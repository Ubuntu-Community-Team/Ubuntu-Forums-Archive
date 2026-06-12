---
title: "trying to remove/uninstall doodle"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by housekid on 2008-11-07
Help Please. I am using etch 4.0 and KDE.

I have been trying to remove/uninstall doodle.
This is the error I keep getting using synaptic, apt-get and dpkg:

E: doodled: subprocess pre-removal script returned error exit status 1

(Reading database ... 107257 files and directories currently installed.)
Removing doodled ...
Stopping doodle daemon: invoke-rc.d: initscript doodled, action "stop" failed.
dpkg: error processing doodled (--remove):
 subprocess pre-removal script returned error exit status 1
Starting doodle daemon: doodled.
Errors were encountered while processing:
 doodled
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

~~~~~


Then I tried to re-install it and I get this:

E: doodled: subprocess pre-removal script returned error exit status 1

(Reading database ... 107257 files and directories currently installed.)
Removing doodled ...
Stopping doodle daemon: invoke-rc.d: initscript doodled, action "stop" failed.
dpkg: error processing doodled (--remove):
 subprocess pre-removal script returned error exit status 1
Starting doodle daemon: doodled.
dpkg: doodle: dependency problems, but removing anyway as you request:
 doodled depends on doodle (= 0.6.5-5).
Removing doodle ...
Errors were encountered while processing:
 doodled
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

~~~~~


Next I searched all the forums I could find, goggling between
forums and found the only info that looked like it could help
and this is it:

  "Dealing with troublesome package upgrades or removals"
  Posted by Steve on debian-administration
  [http://www.debian-administration.org/articles/251/](http://www.debian-administration.org/articles/251/)

which is the only thing close to my problem I've found.
I did/tried everything that Steve talks about, NO LUCK YET.
Belive me there is not much out there on this problem that.


I commented out the " #  set -e ", that he talks about in the
script files starting one at a time with "prerm" file. Then switching
to apt-get I would do an "apt-get -f install" to straighten it all back
up again.

I then compared doodler's prerm file with many other programs files.
I could not find anything wrong.

Next I did everything that I had already done to the "prerm" file
to the remaining script files and as yet Nothing!

Here is a copy of my "prerm file" with the "set -e" commented out:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
#!/bin/sh
#  set -e
exit 1
# Automatically added by dh_installinit

if [ -x "/etc/init.d/doodled" ]; then
	if [ -x "`which invoke-rc.d 2>/dev/null`" ]; then
		invoke-rc.d doodled stop || exit $?
	else
		/etc/init.d/doodled stop || exit $?
	fi
fi
# End automatically added section
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  Help! I'm posting this now (it's late) and I'll be back this weekend.
  Thank you all for getting to post here.

---

