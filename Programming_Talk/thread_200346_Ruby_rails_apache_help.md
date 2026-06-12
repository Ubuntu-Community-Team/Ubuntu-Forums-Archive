---
title: "Ruby rails apache help"
date: 2006-06-20
forum: Programming Talk
---

### Post by mattb1982 on 2006-06-20
I've installed ruby and rails using the debian packages.  When I go to [http://myapp](http://myapp) I can see the default welcome page rails creates when it is installed saying "your riding the rails".  However, when I try to view any pages I've created I just see the following text:

#!/usr/bin/ruby1.8

#!/usr/local/bin/ruby
#
# You may specify the path to the FastCGI crash log (a log of unhandled
# exceptions which forced the FastCGI instance to exit, great for debugging)
# and the number of requests to process before running garbage collection.
#
# By default, the FastCGI crash log is RAILS_ROOT/log/fastcgi.crash.log
# and the GC period is nil (turned off).  A reasonable number of requests
# could range from 10-100 depending on the memory footprint of your app.
#
# Example:
#   # Default log path, normal GC behavior.
#   RailsFCGIHandler.process!
#
#   # Default log path, 50 requests between GC.
#   RailsFCGIHandler.process! nil, 50
#
#   # Custom log path, normal GC behavior.
#   RailsFCGIHandler.process! '/var/log/myapp_fcgi_crash.log'
#
require File.dirname(__FILE__) + "/../config/environment"
require 'fcgi_handler'

RailsFCGIHandler.process!

---

### Post by Corvillus on 2006-06-20
It looks to me like you probably don't have FastCGI configured properly, since dispatch.fcgi is just being displayed as text and not being executed.

---

