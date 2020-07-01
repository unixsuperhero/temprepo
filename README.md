
# Setting up a server

- install rbenv
  - do what it says in the `$> rbenv init` output
    ```# add to ~/.bashrc

      export PATH="$HOME/.rbenv/bin:$PATH"
      eval "$(rbenv init -)"
    ```
- install ruby-build
  - clone github repo into `~/.rbenv/plugins/ruby-build/`
  - run the following:
    - `rbenv install 2.7.1`
    - `rbenv global 2.7.1`
- setup postgres
  - sudo apt install postgresql libpq-dev
  - sudo -u createuser `some_root_user_name` -s
  - setup a role
    - `sudo -u postgres psql` or `sudo -u postgres psql postgres`
    - `create role RAILS_DB_USERNAME with createdb login password 'RAILS_DB_PASSWORD';`
- setup rails
  - `gem install rails -v 6.0.0.rc1`
  - `rails new www --database=postgresql`
  - `rbenv rehash`
  - configure `config/database.yml`
  - `rake db:setup`
  - `rake db:migrate`
- setup devise
  - `echo >>Gemfile`
  - `echo '# Gems added post-rails new' >>Gemfile`
  - `gem 'devise'`
  - `git add --all; git commit -m 'add devise to Gemfile'`
  - `bundle install`
  - `rbenv rehash`
  - `rails g devise:install`
  - `rails g devise User`
  - `rake db:migrate`


# Generate Models



rails g scaffold Customer
  user:belongs_to
  dbase_customer_id:string
  name:string
  address_1:string
  address_2:string
  city:string
  state:string
  zip:integer
  zip4:integer
  phone:string
  active_status:string
  business_category:string





rails g scaffold Contact
  user:belongs_to
  customer:belongs_to
  name:string
  phone:string





rails g scaffold TimelineItem





# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
