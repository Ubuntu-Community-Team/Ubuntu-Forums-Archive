---
title: "creating script for wicd"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Doormat on 2008-05-31
I would like to create a script to run after connect in wicd so that it will automatically connect to vpn. I want to run the following commands but I dont know where to begin to learn how to:

sudo vpnc vpnconfname

I believe I can make it so vpnc doesn't require sudo but I also do not know how to do this. Help is appreciated!

---

### Post by Doormat on 2008-05-31
I have the shell script written now but I can't figure out how to get wicd to run it. It has a space to input a script but i'm not sure what format it wants (./script.sh?). Anyone know how I would do this?

---

### Post by imdano on 2008-06-01
The script text box just runs whatever you type in as if it was running a command from the terminal.  The problem you're probably going to run into is that scripts don't work a lot of the time in version 1.4.2.  You're better off getting the testing-1.5.0 version from our SVN repository, which has a rewritten script system.  In 1.5.0, scripts are always run as root, and actually work correctly.

---

