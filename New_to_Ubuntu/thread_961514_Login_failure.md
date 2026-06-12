---
title: "Login failure"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by NeuB27 on 2008-10-28
I recently downloaded some sound drivers for my motherboard from the ASUS website that were stated as being for Linux, after trying to install them, and their failing, I now cannot log into Ubuntu. Whenever I try to, I am immediately logged out, the error states that linsound.so.2 cannot be found in usr/bin/seahorse-agent. I'm not sure what that means. I tried to start in recovery mode, and none of the options there helped. Is there any way to undo the changes that were made to the system, and get back to a functioning environment? Thanks in advance for any help.

---

### Post by NeuB27 on 2008-10-28
Anyone know how to help? Should I post this elsewhere?

---

### Post by macogw on 2008-10-29
Er, I'm really not sure how you installed the driver that it ended up wanting to interact with your SSH key program...?  If it's a new install, I'd just re-do it.  

And then install XChat, connect to irc.freenode.net, and ask for help in #ubuntu-audio-help to get your sound working.  We're usually in there between 5pm and midnight (sometimes later) Eastern US time (which is like 2100-0400 UTC).  You can catch me (maco) and crimsun in there at other random times as well, though.  Also, please follow the directions on [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) and keep a copy of the link it gives you, so we can look at it.

---

### Post by NeuB27 on 2008-10-29
I found the drivers for linux on the motherboard manufacturer's website and used the install file (./install) to apply the new drivers, then it failed. It stated in the summary that nothing was added, removed or changed and then later I restarted and noticed that I could no longer log in. So what I would like to do is be able to fix that install, it wasn't a new install and I didn't really want to have to make a new install. It seems like since I can access the root prompt through the recovery mode (and thats all) I would be able to fix it, and thought I might find the information on how to do so here. If its just not something I can do, then I guess I'll have to reinstall.

---

### Post by macogw on 2008-10-29
It obviously lied about making no changes if that file exists for it to complain about.  In the recovery console, try this:

```

mkdir /home/temp
adduser --home /home/temp temp

```
I think it should ask you for a password for the temp user.  Then reboot (you can type "reboot" at the prompt) and see if the new user can login.

---

### Post by NeuB27 on 2008-10-29
I just tried that, and it didn't seem to help, I still get the error (found under .xsesson-errors I think, .xsession-something)
right after it establishes the x11 links (one line) it states an error with /usr/bin/seahorse-agent: unable to establish shared object libasound.so.2 : file doesn't exist, or something very similar to that. So is there some way to set up (in the root prompt) the cdrom drive as a source for pkg files, because then I could maybe find some way to rollback that file, or whatever else I might need to, as I have no internet access without wireless access. I'm in my XP boot now, so maybe I could download a file and then mount this drive and cp it over? I'm just not sure what might be a way to fix it. And the ideas I've got I don't know if they will work or how to accomplish them. Thanks for the idea though, I appreciate it.

---

### Post by macogw on 2008-10-29
Did the driver fail to compile, you mean?  

The driver from ASUS's site includes all parts of the ALSA architecture, but they don't all get compiled by default.  libasound2 and alsa-utils, for example, don't get compiled unless you tell it to.  But it still removes the originals.  Depending on how much of it it clobbered...we'll see.

I suggest printing this out so you have something to look at instead of going by memory.

You'll need to burn a copy of the alternate cd. [32bit (i386)]("http://ubuntu.osuosl.org/releases/8.04.1/ubuntu-8.04.1-alternate-i386.iso") or [64bit (amd64)]("http://ubuntu.osuosl.org/releases/8.04.1/ubuntu-8.04.1-alternate-amd64.iso")  If you used amd64 to install, then get the amd64 alternate disk. If you use i386, get the i386 one.  If you're not sure, "uname -m" in the recovery console will say "x86_64" for amd64 and um...something else for i386 (sorry, I run 64bit, so I'm not sure what 32bit says...maybe i686?).

Boot into recovery mode.  Then we need to add the CD as a potential repository so we can reinstall the packages.  
```

mount /dev/cdrom /media/cdrom
apt-cdrom add

```
And disable the online repositories so your lack of network doesn't interfere:
```
nano /etc/apt/sources.list
```
Put # in front of "deb" on every line that starts with "deb" or "deb-src" so it's like this:
> 
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main 
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main

Hit ctrl+O to save then ctrl+X to exit.  Then update the list of what's available like this:
```
apt-get update
```
It'll read what's available on the cd.  And now you have a way to reinstall the necessary software from the cd.

First try this:
```

aptitude reinstall libasound2

```

It'll reinstall libasound2, which is the library it says is missing. Reboot (by typing "reboot" at the command prompt) to see if it worked.  If that doesn't help, try this:
```

find /lib/modules/$(uname -r) -name snd*.ko | xargs rm
aptitude reinstall linux-image-$(uname -r)

```
Then reboot.

That will remove anything that did get installed by the driver you tried to compile, then it'll reinstall your kernel so you get the old drivers back.

Let me know how it goes.  And once you're back to a working system, we'll work on figuring out whatever sound bug you were having, ok?

---

### Post by NeuB27 on 2008-10-29
Great, that worked, I am not back into ubuntu. Thanks a million. The sound all seems to work fine again. I don't know if anything else was affected, but it all seems okay now. When I logged back in though, the screen was all messed up (in relation to its size and position) and I had to change the resolution and change the display drivers back to the restricted nvidia ones. Is there any way to check and see if there are any residual problems that are going on, just not so critical that I can't log in?

---

### Post by macogw on 2008-10-29
It should be fine now then.  The sound stuff's the only stuff that could've been screwed up by that, and a missing sound library was what caused your problem.  You just reverted the sound stuff back to how it was when you installed.

What was the sound issue that made you go looking for that driver?  And you said you can't get online right?

---

