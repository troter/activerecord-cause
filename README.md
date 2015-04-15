# Activerecord::Cause
[![Build Status](https://travis-ci.org/joker1007/activerecord-cause.svg?branch=master)](https://travis-ci.org/joker1007/activerecord-cause)

This gem logs where ActiveRecord actually loads record

ex.
```
D, [2015-04-15T22:13:46.928908 #66812] DEBUG -- :   User Load (0.1ms)  SELECT "users".* FROM "users"
D, [2015-04-15T22:13:46.929038 #66812] DEBUG -- :   ActiveRecord::Cause  SELECT "users".* FROM "users" caused by /Users/joker/srcs/activerecord-cause/spec/activerecord/cause_spec.rb:16:in `block (3 levels) in <top (required)>'
```

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'activerecord-cause'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install activerecord-cause

## Usage

```ruby
ActiveRecord::Cause.match_paths = [
  /spec\/spec_helper/,
]
```
```ruby
# spec/spec_helper.rb
User.all

# output to log file.
# D, [2015-04-15T22:13:46.928908 #66812] DEBUG -- :   User Load (0.1ms)  SELECT "users".* FROM "users"
# D, [2015-04-15T22:13:46.929038 #66812] DEBUG -- :   ActiveRecord::Cause  SELECT "users".* FROM "users" caused by /Users/joker/srcs/activerecord-cause/spec/activerecord/cause_spec.rb:16:in `block (3 levels) in <top (required)>'
```


## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release` to create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

1. Fork it ( https://github.com/joker1007/activerecord-cause/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
