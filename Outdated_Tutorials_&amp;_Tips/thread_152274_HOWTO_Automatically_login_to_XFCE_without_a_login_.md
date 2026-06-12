---
title: "HOWTO: Automatically login to XFCE without a login manager"
date: 2006-03-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Haegin on 2006-03-29
I based this post of one made in the Hoary section by "peekpt" with some updates for breezy and later versions of ubuntu.

Are you tired off typing logins? Don't want to load heavy login managers?

This guide let's you have autologin and autostart for your XFCE:

Let's open a console and then create the file autologin.c

```
sudo nano autologin.c
```

and paste this code inside (middle mouse button will paste the text you select):
```

int main() { execlp( "login", "login", "-f", "your_user_here", 0); }
```

replace the string: your_user_here with the user you want to autologin. (ctrl+O to save and Ctrl + X to quit)

Let's compile.. you will need to have gcc-3.4 installed so if you dont you need to 
```

sudo apt-get install gcc-3.4

```
first. (If you are unsure just try and install it anyway).

```
sudo gcc-3.4 -o autologin autologin.c
```

copy the compiled autologin file into /usr/local/sbin

```
sudo cp autologin /usr/local/sbin
```

now we need to edit the file /etc/inittab

```
sudo nano /etc/inittab
```

search for this:

```
1:2345:respawn:/sbin/getty 38400 tty1
```

put a # to comment this line and add this new line:

```
1:2345:respawn:/sbin/getty -n -l /usr/local/sbin/autologin 38400 tty1
```

it will look like this:

```
#1:2345:respawn:/sbin/getty 38400 tty1
1:2345:respawn:/sbin/getty -n -l /usr/local/sbin/autologin 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
```

this will make the autologin stuff...

let's make the autostart:

Code:
```

nano .bash_profile
```

put this code on the bottom and save it

```

if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
       startxfce4
fi
```

then you just have to remove your login manager :
```

sudo apt-get remove gdm xdm kdm

```

Reboot your machine (to try it out)

I used this page as guide:
[http://www.dicas-l.unicamp.br/dicas-l/20030129.shtml](http://www.dicas-l.unicamp.br/dicas-l/20030129.shtml)

**Notes**
If you don't use xfce you can also run startx at startup using
```

if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
       startx
fi
```
in your .bash_profile file instead.

To undo the changes you have made just edit the inittab file and uncomment the line you commented and comment out the line you added.
```
sudo nano /etc/inittab
```

---

### Post by rado_london on 2006-03-30
Nice howto. Just to mention that boot loader is GRUB. This refers to programs like GDM or KDM  which are login managers.

---

### Post by Tobitas on 2006-03-30
Thank you, worked well on my installation of breezy with xfce.

---

### Post by Haegin on 2006-03-30
Darn! If somebody can edit this or knows how I can then please do so/tell me...

---

### Post by Tobitas on 2006-03-30
could you maybe also supply a script for automated shut down, so I dont have to type "sudo halt"?
thanks

---

### Post by smack on 2006-03-31
[http://www.cs.rit.edu/~css8044/?q=autologin](http://www.cs.rit.edu/~css8044/?q=autologin)

Mingetty has a auto login option also.

---

### Post by blair on 2006-05-18
The default XFCE behavior is to make you type in your password in order to shut down. To fix this so that xfce simply shuts down without prompting you for a password, add the following line to the /etc/sudoers file as root:

ALL ALL = NOPASSWD: /usr/sbin/xfsm-shutdown-helper 

I picked this up on another forum. I added this as the last line in the file and it works like a charm.

---

### Post by blair on 2006-05-19
I ran the sudo gcc-3.4 -o autologin autologin.c command as described above and received the following error:

sudo: gcc-3.4: command not found. 

I did a whereis gcc in a shell and found it in the /usr/bin directory. Scanning this directory I found gcc and also found a gcc-4.0. 

Re-running the compile with gcc threw an error message I did not understand. I continued through the instructions, and the automated login process still worked, so whatever the compile error was, it was not a showstopper. I repeated the experiment using gcc-4.0 and same results: compile error, but the auto login process still worked.

---

### Post by benplaut on 2006-05-19
this will work for any wm... just replace the appropriate executable...

---

### Post by nanotube on 2006-05-22
So, it seems to me that since we are changing inittab, a very common and basic system file, that this guide should work for Dapper as well. I do not run Dapper at the moment, so I cannot check - so could anyone please let me know if it does/should work on Dapper just as well as Breezy?
thanks :)

---

### Post by brady618 on 2006-05-25
It doesn't appear to be working on Dapper, at least for me.  Here's what I get:

mike@Home:~$ sudo gcc-3.4 -o autologin autologin.c
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

And I also tried this:

mike@Home:~$ sudo gcc-4.0 -o autologin autologin.c
autologin.c: In function &#8216;main&#8217;:
autologin.c:2: warning: incompatible implicit declaration of built-in function &#8216;execlp&#8217;
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

Any ideas??

---

### Post by nanotube on 2006-05-25
hmm, that's the last thing i would have expected to fail. the autoconf.c is a very simple c file...
have you tried compiling any other c programs to see if that works? maybe you are missing some packages...?

---

### Post by Haegin on 2006-05-27
[QUOTE=brady618]It doesn't appear to be working on Dapper, at least for me.  Here's what I get:

mike@Home:~$ sudo gcc-3.4 -o autologin autologin.c
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

And I also tried this:

mike@Home:~$ sudo gcc-4.0 -o autologin autologin.c
autologin.c: In function ‘main’:
autologin.c:2: warning: incompatible implicit declaration of built-in function ‘execlp’
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

Any ideas??[/QUOTE]

Ok, you need to use gcc-3.4 (not gcc-4.0) so first run:
```

sudo apt-get install gcc-3.4

```
then recompile it using:
```

sudo gcc-3.4 -o autologin autologin.c

```

That should work fine - if not come back for more help.
I have successfully compiled it on dapper so I know its possible.

---

### Post by skimitar on 2006-05-27
You need to 

> sudo apt-get install build-essential

to get the program to compile rather than just installing gcc-3.4 as this also includes the required development libraries.

At least the program it managed to compile for me after I did this. It does install a few other things not strictly necessary for this but which will come in handy eventually (e.g. kernel headers, g++).

EDIT: but you still need gcc-3.4

---

### Post by nanotube on 2006-05-28
ehrm, actually, you dont need gcc3.4, it compiles just fine with gcc4.0 as well. only difference is that it throws out a [harmless] warning when you compile with 4.0, but it compiles just the same. ;)

---

### Post by nickless on 2006-07-11
When I do apt-get remove gdm, it wants to remove xubuntu-desktop, too... so I guess I better don't do this. Anyways nice How-To!

---

### Post by Haegin on 2006-07-11
You don't need the xubuntu-desktop package - it's just used to easily install everything required for xubuntu and once everything is installed can safely be removed from the system.

---

### Post by nickless on 2006-07-11
Ah ok, thanks :D If I don't remove gdm it will always get started.. :)

---

### Post by nanotube on 2006-07-11
> **nickless said:**
> Ah ok, thanks :D If I don't remove gdm it will always get started.. :)

you dont have to uninstall gdm to stop it from starting. just remove it from /etc/rc2.d/
(or use the handy tool called "sysv-rc-conf" to edit your runlevel config. then you can just simply uncheck gdm from runlevel 2 (which is the default ubuntu runlevel) )

---

### Post by tsagas on 2006-07-29
How can I get rid off the X11 usual ugly grey background? Gdm used to take care of that by replacing it with a nicer color...

---

### Post by K.Mandla on 2006-09-07
Thanks for this. I had been looking for a way to lighten the load on a 750Mhz laptop, and the first thing I wanted to dump was gdm. I needed the autologin though.

This worked perfectly under an extremely lightweight Xubuntu 6.06.1 system after installing build-essential. It's very nice to be able to automatically log in without the desktop manager.

Thanks again!

EDIT: I should mention I didn't have the same luck on an Edgy installation, but I blame that mostly on all the weird tweaks and modifications I've done since I installed it. I'll try some other time on a fresh build and see if it works ... maybe once Edgy is fully stable.

---

### Post by danpre on 2006-09-18
I just would like to tell that it works on Debian Sarge too.

Great.

Thx.

DANIeL

---

### Post by K.Mandla on 2006-10-02
> **K.Mandla said:**
> I'll try some other time on a fresh build and see if it works ... maybe once Edgy is fully stable.
If you've tried this autologin under Edgy and had no luck, here's the reason.

The upstart boot sequence, as I understand it, abandons inittab, and instead uses a series of files under /etc/event.d/ to spawn tty consoles.

That means each console has a separate tty file inside /etc/event.d/ ... edit tty1 in the same way you would for inittab, to get the autologin working. In other words. ...

```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on runlevel-2
start on runlevel-3
start on runlevel-4
start on runlevel-5

stop on shutdown

respawn /sbin/getty -n -l /usr/local/sbin/autologin 38400 tty1
```
That should do the trick for you. Cheers! 8) 

P.S.: I should mention that this is only the case for Edgy post-Knot 2, which means if you install from Knot 1 or 2, and don't find those files, you should either use the old system for Dapper, or *dist-upgrade* to the new bootup system. There is some related information [here]("https://launchpad.net/distros/ubuntu/+source/upstart/+bug/61539").

---

### Post by beauring on 2006-11-23
I get the following error message any ideas what's up?

autologin.c: In function ‘main’:
autologin.c:1: warning: incompatible implicit declaration of built-in function ‘execlp’
autologin.c:1:62: warning: no newline at end of file
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

---

### Post by moore.bryan on 2007-02-17
[I]silly me, i just started a new thread on a problem i had with this... my openbox startup script is written to start gnome-volume-manager, but when doing the autologin sequence, it doesn't seem to load.  and then, when i try to write files to my manually mounted external drives, i find them "unwritable."  ideas?

more specifics are @ my thread ([http://ubuntuforums.org/showthread.php?t=363713](http://ubuntuforums.org/showthread.php?t=363713))

[/I]==============================================================
[I]EDIT:

nevermind... i just dumped gnome-volume-manager and went with ivman... works; not sure why, but it does.
[/I]

---

### Post by linuks on 2007-04-06
Hi,

To the author - please update the guide and tell ppl. to install build-essentials in order to successfully compile the program? Thanks for the guide btw!

linuks

---

### Post by wrrr on 2007-09-30
> **Tobitas said:**
> could you maybe also supply a script for automated shut down, so I dont have to type "sudo halt"?
thanks

hello. try this. add this line to **/etc/sudoers**
```
%users    localhost=NOPASSWD:/sbin/reboot, /sbin/poweroff
```
this makes possible to any user from the *users* group to invoke **sudo reboot** or **sudo poweroff** without the need of typing in root password.
lastly, make a change in **~/.bash_profile** as such:
```
if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
       startx; [color=red]**sudo poweroff**[/color];
fi
```

for me it works like a charm. btw. I don't use any of the xDMs (have GDM in my Debian/Etch installed but disabled), just  terminal login with the autologin feature created according to the how-to found in this topic.
the effect is: when I invoke "log off" from gnome menu, the xserver shuts down and the **sudo poweroff** command is executed automaticlly (no need to give root password).

btw. anyone could tell me what are the drawbacks of my solution?

one quiet annoying thing I found is that when you want to resetart xorg (by ctrl+alt+backspace) the computer goes off, because the **power off** command is invoked always after the xserver shutdown. a good thing would be to swap this command with the call of some kind of script which could offer choosing, if the user wants to restart or halt the system or just log off (back to text login prompt). I'm not the best in bash programming so if anyone can help,  I'd be thankful. the use of ncurser would be nice.

---

### Post by kerry_s on 2007-09-30
> **wrrr said:**
> hello. try this. add this line to **/etc/sudoers**
```
%users    localhost=NOPASSWD:/sbin/reboot, /sbin/poweroff
```
this makes possible to any user from the *users* group to invoke **sudo reboot** or **sudo poweroff** without the need of typing in root password.
lastly, make a change in **~/.bash_profile** as such:
```
if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
       startx; [color=red]**sudo poweroff**[/color];
fi
```

for me it works like a charm. btw. I don't use any of the xDMs (have GDM in my Debian/Etch installed but disabled), just  terminal login with the autologin feature created according to the how-to found in this topic.
the effect is: when I invoke "log off" from gnome menu, the xserver shuts down and the **sudo poweroff** command is executed automaticlly (no need to give root password).

btw. anyone could tell me what are the drawbacks of my solution?

looks okay to me, i do mine a little different(using debian+xfce4).no compiling needed, i apt-get mingetty. "user" is my login name.

```
my sudoers line:
%nopasswd ALL=(root) NOPASSWD: /usr/bin/conky, /sbin/halt, /sbin/reboot, /sbin/shutdown, /usr/sbin/xfsm-shutdown-helper, /usr/bin/thunar, /usr/bin/mousepad, /usr/sbin/synaptic
```

```
my login line(/etc/inittab):
1:2345:respawn:/sbin/mingetty tty1 --autologin user
```

```
bash_profile:
if [ `tty` = "/dev/tty1" ]; then
startx
fi
```

---

### Post by popey on 2008-01-01
Please can this be updated to remove "sudo" from the first nano line and from the gcc line, as it is not required.

---

### Post by johnraff on 2010-03-18
Credit to ["shallow thoughts"](http://shallowsky.com/blog/linux/install/autologin-karmic.html) for this.

First the bad news:
The login files changed again in Karmic. The file to edit is now /etc/init/tty1.conf but the line is the same.

The good news:
You don't need to compile an "autologin" binary - a script containing ```
#! /bin/sh
/bin/login -f yourusername

```is enough. :)

---

