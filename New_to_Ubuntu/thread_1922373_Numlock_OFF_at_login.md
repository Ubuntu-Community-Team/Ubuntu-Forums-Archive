---
title: "Numlock OFF at login"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by mikegsmith on 2012-02-08
I'm using Ubuntu 11.10, dual boot with Win7, GRUB2 as boot manager. BIOS set to turn Numlock ON, which it does. But then just prior to GRUB menu screen, Numlock goes off so key pad is not available at login.

I've been working through a few of the suggestions at [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock). Specifically, the following:

Option 1, regarding System Settings > Keyboard Layout > Options > Miscellaneous compatibility options. This works but not until after the log in screen. I need to be able to use the numeric keypad for my password.

Option 2. Install numlockx. I've done this and confirmed that it is correctly installed by issuing numlockx on/off commands from the terminal.

Option 3, regarding sudo sed -i command, which I guess is making changes to the /etc/rc.local file. This suggestion is so bewildering that I've avoided it.

Instead, I've edited the /etc/rc.local file by adding the line:  "user/bin/numlockx on". It didn't work.

If Option 3 is indeed my solution, will someone please explain it to me?

Option 4, re Enabling NumLock from startx. I added the  "user/bin/numlockx on" line to the /etc/X11/xinit/xinitrc file. It didn't work.

It appears to me that the remaining options  are not relevant.

I'm a newbie patiently crawling up the learning curve. Unfortunately, the learning curve has flat-lined for me on this issue.

Thanks to those who are so generous of their time in helping us beginners.

---

### Post by Krytarik on 2012-02-08
> **mikegsmith said:**
> Option 3, regarding sudo sed -i command, which I guess is making changes to the /etc/rc.local file. This suggestion is so bewildering that I've avoided it.

Instead, I've edited the /etc/rc.local file by adding the line:  "user/bin/numlockx on". It didn't work.

If Option 3 is indeed my solution, will someone please explain it to me?
It just sets "/etc/rc.local" like shown below, which you've supposedly done yourself manually, only without the prior check if "numlockx" is installed.

Either just copy & paste the content from below, or at least make sure you have both set the path right (as you've stated it incorrectly twice in your post) and placed the command above the "exit 0" line.

"/etc/rc.local":
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Numlock enable
[ -x /usr/bin/numlockx ] && numlockx on

exit 0
```Regards.

---

### Post by Gremlinzzz on 2012-02-08
Menu -> System -> Administration -> Keyboard & Mouse -> Keyboard ->"turn on Numlock on Startup"

:popcorn:

---

### Post by mikegsmith on 2012-02-08
> **Krytarik said:**
> It just sets "/etc/rc.local" like shown below, which you've supposedly done yourself manually, only without the prior check if "numlockx" is installed.

Either just copy & paste the content from below, or at least make sure you have both set the path right (as you've stated it incorrectly twice in your post) and placed the command above the "exit 0" line.

"/etc/rc.local":
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Numlock enable
[ -x /usr/bin/numlockx ] && numlockx on

exit 0
```Regards.

Krytarik: Thanks for your quick response. I edited the rc.local file and used cut/paste to plug in the command line exactly as you suggested. Unfortunately, to no avail. My Num Lock setting still turns off just before the GRUB menu appears. Three questions:

1) Is it possible that GRUB is causing this?
2) The rc.local comments talk about "changing the execution bits." Could this be pertinent?
3) Any other trouble-shooting suggestions?

Again, thanks for your help.

---

### Post by mikegsmith on 2012-02-08
> **Gremlinzzz said:**
> Menu -> System -> Administration -> Keyboard & Mouse -> Keyboard ->"turn on Numlock on Startup"

:popcorn:

Gremlinzzz: Thanks for your suggestion. Is it possible that your suggestion applies to a version of Ubuntu prior to ver. 11.10? In 11.10 I don't find any settings path that leads to the option: "turn on Numlock on Startup."

---

### Post by Gremlinzzz on 2012-02-08
your suggestion applies to a version of Ubuntu prior to ver. 11.10?
wasn't thinking your mostly right i looked it up on the guide 
[http://ubuntuguide.org/wiki/Ubuntu:Oneiric](http://ubuntuguide.org/wiki/Ubuntu:Oneiric)
probably old advice

---

### Post by Krytarik on 2012-02-08
> **mikegsmith said:**
> My Num Lock setting still turns off just before the GRUB menu appears.Actually, even if the "numlockx" thing works, NumLock will still be disabled until "rc.local" is eventually run, which is one of the last things in the boot process.

> **mikegsmith said:**
> 1) Is it possible that GRUB is causing this?
Apparently; didn't think of that too much till now, but yes, it seems so.

> **mikegsmith said:**
> 2) The rc.local comments talk about "changing the execution bits." Could this be pertinent?
That's just referring to changing the permissions of that file so that it may not be executed; by default it's enabled, of course, but you can check that via "Properties -> Permissions" in Nautilus.

We are still talking about that NumLock shall be enabled at the login screen, that is, LightDM, right, not already at the Grub menu? Or have you password protected your Grub?

---

### Post by Krytarik on 2012-02-08
> **Krytarik said:**
> We are still talking about that NumLock shall be enabled at the login screen, that is, LightDM, right ... ?
Thinking of which, provided that we are still up for that, invoking "numlockx" from LightDM might work better than running it via "rc.local":

[https://answers.launchpad.net/lightdm/+question/173666](https://answers.launchpad.net/lightdm/+question/173666)

---

### Post by mikegsmith on 2012-02-08
> **Krytarik said:**
> Thinking of which, provided that we are still up to that, invoking "numlockx" from LightDM might work better than running it via "rc.local":

[https://answers.launchpad.net/lightdm/+question/173666](https://answers.launchpad.net/lightdm/+question/173666)

Bingo, Krytarik!! You got it. I knew that GDM didn't handle the login function any more because I had tried, without success, the old numlockx solutions that worked under GDM. But I didn't have a clue as to what replaced GDM in current Ubuntu releases.

Your link to the lightdm issue provided the answer. Studentz at that link offered the following:

> This work for me

sudo gedit /etc/lightdm/lightdm.conf

add the next line at he end

greeter-setup-script=/usr/bin/numlockx on

I edited the lightdm.conf file as recommended, and my problem is solved. Thanks for all your help. Now if I can only figure out how to mark this question Resolved.

---

