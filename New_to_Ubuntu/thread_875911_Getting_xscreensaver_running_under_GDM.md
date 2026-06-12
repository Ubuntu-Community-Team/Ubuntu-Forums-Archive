---
title: "Getting xscreensaver running under GDM"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by andersoj on 2008-07-31
OK, I've done the expected rounds of google searches, and also searched some similar topics in the ubuntu forums.

I've got Hardy Heron (server, plus a limited selection of GUI stuff) installed on a new machine.  I want to get xscreensaver running during the GDM time -- where this machine is likely to spend a lot of time.

I have followed the instructions to add xscreensaver -nosplash to the BackgroundProgram directive in gdm.conf.  No luck, and there is no evidence that xscreensaver was ever run (I don't see it in ps; I don't see a logfile anywhere telling me it failed.)

So I try to: 
su to the gdm user
export DISPLAY=:0.0 (the display of the console screen)
xscreensaver -nosplash

And I get:

```
xscreensaver: Can't open display: 0.0
xscreensaver: running as gdm/gdm (111/122)

xscreensaver: Errors at startup are usually authorization problems.
              But you're not logging in as root (good!) so something
              else must be wrong.  Did you read the manual and the FAQ?

              http://www.jwz.org/xscreensaver/faq.html
              http://www.jwz.org/xscreensaver/man.html

```

OK, so this makes sense.  The X server is running as root, and I haven't done anything with xauth/xhost to permit a connection to that xserver.  But it baffles me that there isn't some canned answer to this... where do I do the magic to (with reasonable security) allow the gdm/gdm xscreensaver to connect to that display and put up some pretty pictures?

JA

---

### Post by pauper on 2008-08-01
> **andersoj said:**
> No luck, and there is no evidence that xscreensaver was ever run (I don't see
it in ps; I don't see a logfile anywhere telling me it failed.)

I believe, you supposed to explicitly add xscreensaver to your startup programs.

> **andersoj said:**
> The X server is running as root, and I haven't done anything with xauth/xhost
to permit a connection to that xserver.

You can run xscreensaver as a user.

An extract from xscreensaver manual, lines 514 through 530:

> USING GDM(1)
Using xscreensaver with gdm(1) is easy, because gdm has a configuration tool.
Just fire up gdmconfig(1) and on the Background page, type "xscreensaver -nosplash"
into the Background Program field. That will cause gdm to run xscreensaver while
nobody is logged in, and kill it as soon as someone does log in. (The user will
then be responsible for starting xscreensaver on their own, if they want.)

Another way to accomplish the same thing is to edit the file
/etc/X11/gdm/gdm.conf to include:

 BackgroundProgram=xscreensaver -nosplash
 RunBackgroundProgramAlways=true

[i]In this situation, the xscreensaver process will probably be running as user
gdm instead of root.[/i] You can configure the settings for this nobody-logged-in
state (timeouts, DPMS, etc.) by editing the ~gdm/.xscreensaver file.

To get gdm to run the BackgroundProgram, you may need to switch it from the
"Graphical Greeter" to the "Standard Greeter".



In Gutsy (desktop) I had it running in no time:

```
sudo apt-get install xscreensaver xscreensaver-data-extra xscreensaver-gl xscreensaver-gl-extra
echo "
> BackgroundProgram=xscreensaver -nosplash
> RunBackgroundProgramAlways=true" | sudo tee -a /etc/gdm/gdm.conf
```

Note: Just in case, check that any other occurrences of these two entries are
commented out.

```
gnome-screensaver-preferences
```

Uncheck "Activate screensaver..." box.

```
gnome-session-properties
```

Add new entry:

Name: Xscreensaver
Command: xscreensaver -nosplash

```
xscreensaver-demo
```

Set it up the way you want it.

---

