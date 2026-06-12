---
title: "HOWTO: Ruby, Rails, Capistrano"
date: 2009-02-20
forum: Outdated Tutorials &amp; Tips
---

### Post by clcollins on 2009-02-20
So, I spent about 30 minutes working out how to get Ruby, Rails and Capistrano installed on my desktop.  Granted, I'm a relative n00b, so you may be more efficient at it.  However, for those newbies out there like me, I wrote a simple bash script to take care of all the dependencies and get it all setup.  

Currently it sets up everything with a SQLite database.  As I have time I will add sections for MySQL and PostgreSQL.

This has been tested and works in my 8.10 Desktop environment (relatively basic install).  Please feel free to test on other versions and let me know how it worked.

Any comments or criticism or corrections are welcome!

```

#!/bin/bash
#
# Written by clcollins
# Comments, criticism welcome.

# Take database option from command line argument
# Currently valid: sqlite or <BLANK>
# Others will error politely
# Support for MySQL, PostgreSQL
DB=$1

## If no database specified in the
#  command line, then default to
#  SQLite

if [ "$DB" = "" ] ; then
  DB="sqlite"
  echo "sqlite"
fi

if [ "$DB" = "sqlite" ] ; then
  # Install necessary aptitude packages
  aptitude -y install build-essential \
                        ruby rubygems ruby1.8-dev \
                        libsqlite3-dev

  # Gems 1.3.1 needed for rake
  # Updating here
  gem install rubygems-update
  # Need to run actual update seperately
  /var/lib/gems/1.8/bin/update_rubygems

  # Install rake, capistrano, sqlite and rails
  gem install rake capistrano sqlite3-ruby
  gem install -v=2.2.2 rails
  exit 0

else
  # Fill this out with support for MySQL and PostgreSQL
  echo ""
  echo "NOTE: That DB support not setup yet...exiting."
  echo ""
  exit 1
fi

```

---

