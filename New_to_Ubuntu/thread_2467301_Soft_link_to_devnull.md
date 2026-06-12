---
title: "Soft link to /dev/null?"
date: 2021-09-22
forum: New to Ubuntu
---

### Post by briand-idaho on 2021-09-22
Not a Linux expert, still pretty new ... I have a program that dumps log info into a local (.blah/app-name/logs/log.log) log file ... but I wish the log file to never store anything at all unless I allow it.  How about a soft link named log.log that points at the /dev/null bit bucket ... would that work?  Any reasons to NOT do this?

thanks

---

### Post by scorp123 on 2021-09-22
I did something similar once...  it should work. The log's contents should basically go into Nirvana but not get stored on the disk.

Just be extra careful with the syntax, you don't want to link the wrong thing to /dev/null ...

---

### Post by TheFu on 2021-09-22
> **briand-idaho said:**
> Not a Linux expert, still pretty new ... I have a program that dumps log info into a local (.blah/app-name/logs/log.log) log file ... but I wish the log file to never store anything at all unless I allow it.  How about a soft link named log.log that points at the /dev/null bit bucket ... would that work?  Any reasons to NOT do this?

thanks

Best not to hard code log files.  Then you could just set the log file in the settings to /dev/null.  Wouldn't that be easier?

BTW, log files belong in /var/log/ somewhere or you can use the syslog facility to write to the logs. There are plenty of examples online for almost any language. Then the admin can choose which file and which level of logging to have - Critical, Errors, Warnings, Informational or Debugging - and send each level to a different file or /dev/null, if they prefer. 

I've written log routines in at least 5 different languages. They all come back to letting the person/admin running the program to choose where the logs go and how much logging to have.  There is an expected hierarchy for settings, so when it comes to handling any program settings, it is best to process in the reverse order, so the expected override locations always overrule any defaults in a config file.
[LIST]
[*]Default coded into the program.
[*]Default Config file - /etc/{program-name}/program.conf
[*]Local override Config file -  /etc/{program-name}/program.local
[*]Per-user override Config file -  $HOME/.config/{program-name}/program.conf
[*]Command Line override Config file - passed in with -c option - as in  /path/to/program -c $HOME/.config/filename-whatever.conf
[*]Environment Variable Config File - export APPNAME-CONF=/some/wacky/location/filename
[/LIST]
That's the expected priority for Unix programs to seek out options. Woe to those who ignore it. You shall be hated by all users. ;)

Any setting in the configfile specified by the environment variable would override all the others.  If a setting isn't specified anywhere, the default coded into the program should be used.

It is also good if changes to the configs are recognized while the program is running and re-read.  I've had a number of client love that they didn't have to restart the program for config changes to be picked up.  It is great when they are helping you find an issue that can't be reproduced on your local system.  Have logging set to Critical, then the user gets to the step just before they can recreate the issue and changes the log level to Debug in the config file. They cause the issue, the logs are full of information, then they can reset the log level back to Critical again.  You get the logs that has the most important stuff you want and they don't have to send 500MB of logs just to reproduce an issue caused by 1 button click.

---

### Post by briand-idaho on 2021-09-23
Thank you, TheFu...

I'm a developer, but the program in discussion is not mine.  It doesn't log to the /var/log path like other programs do.  BUT, since I'm also a developer, I did copy your post into a text doc that I can reference when I write my own logging code (thx).

---

