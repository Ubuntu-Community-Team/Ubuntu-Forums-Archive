---
title: "lost graphic logon"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by wombat123 on 2012-10-18
Using ubuntu latest stable release.  I tried to start a second xterm  [  startup -- :2  ]

This hung.

So I hit the big red button but found when I tried to logon, having entered a valid user/password at the prompt it went away for a second or two and returned to the login.  I tried invalid credentials and these it recognised as invalid instantly.

I arrived at the char interface Ctrl-Alt-F1.  I could log on.

Can anyone help with how I can recover?  Do I need to reload the graphical desktop?

Any thoughts and help very much appreciated :)

---

### Post by 2F4U on 2012-10-18
I assume that the desktop environment is crashing and placing you back to the login screen. Since you are able to login to a console, you can look for a file named .xsession-errors in your home folder. It has errors releated to the X window system in it and may help in diagnosing why the DE is crashing.

---

### Post by buckyaustin on 2012-10-18
What was the last thing you intsalled? This sounds like a problem I had when I tried to customise the logon screen. I had accidently installed two logon managers. LightDm and LDM. You will have to reconfigure this if this is the problem. What I did was un-install LDM & LightDm then reinstalled. That was it solved for me.

---

### Post by wombat123 on 2012-10-18
Many tx for responding guys.

I've looked at .session-errors and there is a critical error but I can make no sense of it.  And sadly I can't post it here at the moment.

I didn't instal anything.  What I want to do is test a VDI system using a script driver cnee.  I installed it , captured a script, and ran it.  It connected via vmware-viewer and was fine.  However to run more users (concurrent) I needed more xterm sessions.  So I executed
startup -- :1

This indeed started a second xterm.  Sadly once in it (looking at the screen) I couldn't escape.  So I thought the issue was the running of a second xterm.  But clearly that corrupted something.

I think I will reload Ubuntu from scratch (on a windows m/c) and try again.

As always any input very welcome and greatly appreciated.  I'll learn on the job but sometimes a little input can save sooooo much time.

Cheers :)

---

### Post by Bashing-om on 2012-10-18
Just a suggestion; You should check and see if access rights and permissions have changed in .ICEauthority and .Xauthority in your home directory.

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by Frogs Hair on 2012-10-18
If you were able to login to tty with Ctrl + Alt + F1 then Ctrl + Alt + F7 will return you to the graphical desktop if it is working.

---

### Post by rburkartjo on 2012-10-19
i have had luck deleting the .Xauthority file and just rebooting. worked for me anyway

---

