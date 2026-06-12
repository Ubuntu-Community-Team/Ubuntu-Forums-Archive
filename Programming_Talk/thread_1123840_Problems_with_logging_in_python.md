---
title: "Problems with logging in python"
date: 2009-04-12
forum: Programming Talk
---

### Post by mnemonik on 2009-04-12
Hello,

I am running a script, and I want to log messages in to a log file of my choosing so I have this code below, pretty much copied from [http://docs.python.org/library/logging.html](http://docs.python.org/library/logging.html)

[PHP]import logging
LOG_FILENAME = r'/home/fitzgen/western_jobs/dev_job_scraper.log'                                                                                             
logging.basicConfig(filename=LOG_FILENAME,level=logging.DEBUG,)
[/PHP]

And the script runs fine, but none of the messages are logged in the filename I specified. It doesn't even create the log file...

Please help, thanks!

---

### Post by ghostdog74 on 2009-04-12
read the docs carefully. there is one extra step you need to do.

---

