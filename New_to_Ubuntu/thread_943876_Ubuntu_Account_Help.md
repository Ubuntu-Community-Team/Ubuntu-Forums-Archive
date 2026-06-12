---
title: "Ubuntu Account Help"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by nm1 on 2008-10-10
Hi all.  I'm very new to xubuntu; just installed it this afternoon.  I'm needing some help with the user accounts.  The user account that I created during the installation process is not working when I try and log in on the log in screen.  It simply defaults to the account that it logs into when it times out (if you don't type anything for 30 seconds) (I believe it is called ubuntu).  I let it time out and went into this account and used the "terminal" to create a new user with the same name and password that I input during installation.  That account is working, but it doesn't have Administrative priviliges so I can't go in and change the users to my satisfaction.  And the "ubuntu" account that is the default doesn't seem to have administrative priviliges either.

That's the background.  Here's my questions:

1) I know that there was supposed to be an account set up when I installed and I'm not sure why it didn't do it.  Why not?

2) How do I fix it?  I'm assuming that I need administrative priviliges to go in and get rid of the default (ubuntu) account (because I'm never going to use it) and make the account that I set up, able to access settings....  How would I go about doing this?

3) One more minor problem with the account that I created.  The top and bottom bar seem to have disappeared.  I'm not sure how to get them back.

Thanks to anyone who can help, and all who do!  I'm liking ubuntu except for the problems I'm experiencing.  But those are to be expected I suppose when you take a windows user and show him a new operating system :)

---

### Post by sumguy231 on 2008-10-10
1.) I've never heard of a default "ubuntu" account. Are you using the new beta or perhaps did an OEM install?
2.) You'll need to boot into recovery mode first. Do this by hitting escape when the bootloader counts backwards from 3. Select the "(recovery mode)" option. Once you're in, you'll need to enter the following command to add yourself to the admin group:
```
adduser username admin
```
**Replace username with your username**. Reboot and everything should work.
3.) I'm using GNOME right now so I can't tell you, but I'll look it up on my Xubuntu box real quick and get back to you.

---

### Post by sumguy231 on 2008-10-10
Okay, number 3:
It sounds like the desktop may not be sucessfully starting. Right-click on the desktop and see if you get a context menu.

---

### Post by nm1 on 2008-10-10
Well, my problems may be solved.  I shut down my computer after posting and when I came back and started the computer up just a moment ago, it told me to insert something to boot from, etc... (it had ejected the disc before shutdown).  So, I inserted the xubuntu disc (although I was confused as to why it needed it and the computer did not boot from the hard drive) and the computer started up.  Then, it did not go to the login screen, instead it loaded the desk top of what was apparently the root account; because it let me go into the user screen and make a new user with the information that I wanted and it showed that the only other user was "root".  So, I'm thinking whatever was wrong before the shutdown has been magically solved, (as things sometimes are with computers) and my new problems are simply:

1) Why is it still asking me to insert the CD when I've already installed xubuntu?


Thanks very much for helping with the earlier problem that now seems to have disappeared!!! :)

---

### Post by lisati on 2008-10-10
> **sumguy231 said:**
> 1.) I've never heard of a default "ubuntu" account. Are you using the new beta or perhaps did an OEM install?

I once encountered the "ubuntu" account after a botched install, I can't remember which version, but think it was after 7.04

> **nm1 said:**
> Well, my problems may be solved.  I shut down my computer after posting and when I came back and started the computer up just a moment ago, it told me to insert something to boot from, etc... (it had ejected the disc before shutdown).  So, I inserted the xubuntu disc (although I was confused as to why it needed it and the computer did not boot from the hard drive) and the computer started up.  Then, it did not go to the login screen, instead it loaded the desk top of what was apparently the root account; because it let me go into the user screen and make a new user with the information that I wanted and it showed that the only other user was "root".  So, I'm thinking whatever was wrong before the shutdown has been magically solved, (as things sometimes are with computers) and my new problems are simply:

1) Why is it still asking me to insert the CD when I've already installed xubuntu?


Thanks very much for helping with the earlier problem that now seems to have disappeared!!! :)

I'm not quite sure what's happening. It is possible that something was missing from the installation on your machine, and it ended up running the LiveCD, which doesn't usually ask for a username/password.

---

### Post by nm1 on 2008-10-11
> **lisati said:**
> I once encountered the "ubuntu" account after a botched install, I can't remember which version, but think it was after 7.04 

I think it would be safe to assume that this was a "botched" install.  And yes, this version is after 7.04 (I think it might be 8.04?) How can I fix it and make it run properly?

Just some further information.  This morning, I started the computer up and it once again asked me to insert the CD so that it could boot.  And when I did and it loaded, it had apparently erased all of the user stuff I created yesterday when the same thing happened and it loaded the desktop of the root account.  So, it's not remembering any of the changes that I make which makes me agree and think that it's just running from the CD even though I installed.  So, back to the question, what do I do to fix it and make it run properly?!

Thanks for all the help I've gotten so far!!

---

### Post by sumguy231 on 2008-10-11
Just try doing the install again from the LiveCD. If you can obtaina fresh copy, do so because it may increase your chances of success.

---

### Post by nm1 on 2008-10-12
Alrighty, I'll try that.  How do you suggest I wipe whatever information was installed?  I don't have anything stored on this computer so I don't have a problem wiping everything, but how would I do it?  This way, I will know that I'm starting fresh.

---

### Post by sumguy231 on 2008-10-12
You don't have to do anything special, assuming you installed with the 'use entire disk' or 'guided' options, just do the same again.

---

