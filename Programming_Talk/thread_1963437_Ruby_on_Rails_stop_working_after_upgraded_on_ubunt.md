---
title: "Ruby on Rails stop working after upgraded on ubuntu 11.10 ?"
date: 2012-04-22
forum: Programming Talk
---

### Post by hoboy on 2012-04-22
Sorry if this mail is boublet. I
I have upgraded my ruby on ubuntu 11.10 since that
whenever I try to create a project in eclipse, aptane I get the
following error.
when I also write rails I get the same errors:
-----------------------------------------------------------------
Satellite-A300D:~$ rails
Usage:
  rails new APP_PATH [options]

Options:
  -r, [--ruby=PATH]              # Path to the Ruby binary of your choice
                                 # Default: /home/luc/.rvm/rubies/ruby-1.9.3-p194/bin/ruby
  -b, [--builder=BUILDER]        # Path to a application builder (can be a filesystem path or URL)
  -m, [--template=TEMPLATE]      # Path to an application template (can be a filesystem path or URL)
      [--skip-gemfile]           # Don't create a Gemfile
      [--skip-bundle]            # Don't run bundle install
  -G, [--skip-git]               # Skip Git ignores and keeps
  -O, [--skip-active-record]     # Skip Active Record files
  -S, [--skip-sprockets]         # Skip Sprockets files
  -d, [--database=DATABASE]      # Preconfigure for selected database (options: mysql/oracle/postgresql/sqlite3/frontbase/ibm_db
/sqlserver/jdbcmysql/jdbcsqlite3/jdbcpostgresql/jdbc)
                                 # Default: sqlite3
  -j, [--javascript=JAVASCRIPT]  # Preconfigure for selected JavaScript library
                                 # Default: jquery
  -J, [--skip-javascript]        # Skip JavaScript files
      [--dev]                    # Setup the application with Gemfile pointing to your Rails checkout
      [--edge]                   # Setup the application with Gemfile pointing to Rails repository
  -T, [--skip-test-unit]         # Skip Test::Unit files
      [--old-style-hash]         # Force using old style hash (:foo => 'bar') on Ruby >= 1.9

Runtime options:
  -f, [--force]    # Overwrite files that already exist
  -p, [--pretend]  # Run but do not make any changes
  -q, [--quiet]    # Supress status output
  -s, [--skip]     # Skip files that already exist

Rails options:
  -h, [--help]     # Show this help message and quit
  -v, [--version]  # Show Rails version number and quit

Description:
    The 'rails new' command creates a new Rails application with a default
    directory structure and configuration at the path you specify.

    You can specify extra command-line arguments to be used every time
    'rails new' runs in the .railsrc configuration file in your home directory.

    Note that the arguments specified in the .railsrc file don't affect the
    defaults values shown above in this help message.

Example:
    rails new ~/Code/Ruby/weblog

    This generates a skeletal Rails installation in ~/Code/Ruby/weblog.
    See the README in the newly created application to get going.

---

