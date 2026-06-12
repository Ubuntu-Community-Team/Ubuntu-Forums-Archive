---
title: "Stucked in a Ubuntu login screen loop"
date: 2015-11-21
forum: New to Ubuntu
---

### Post by kvanoff on 2015-11-21
Hi all, i write because just like the title said my Ubuntu 14.04 who used to work well enough doesnt allow me to access to the system. Ive got a personal computer with a dual boot and two different hard drives. When i boot from the Hd with Ubuntu (where all my files are) and tap my user pass for the admin account all i can have its the login screen again and again. I cant pass the login screen because ubuntu keeps asking me user and pass after a moment of blank screen every time. I tried to add an user: no way. Guest session: noway. Tried to reconfigure xauthority and xorg: nothing. Tried to reconfigure lightdm: nothing. Tried to remove .Xauthority qnd nothing. To update and upgrade, nothing. What can i do sirs? Thanks in advance.

---

### Post by Bashing-om on 2015-11-21
kvanoff; Hi !

Goodness ... you have done so many things, it will be a challenge to determine what is at fault.
We start this process of discovery from a terminal.
At the login screen can you activate a console interface; key combo ctl+alt+F1 ?

From here IF you have this access we can start looking for faults.

Else, well we try and boot to a terminal via grub's boot menu .

[INDENT][INDENT]depending on what is
[INDENT][INDENT][INDENT]is what we do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by james_hunt10 on 2015-11-21
I am having same login on new 14.04.3 server.  I completed the Contro-Alt-F-1 from login consol and took me to trminal asking for login

---

### Post by james_hunt10 on 2015-11-21
login on terminal with no problems

---

### Post by kvanoff on 2015-11-21
Hi Bashing, and thanks,
Yes the answer is yes, i m able to see and interact with the console. I even can do the login and enter on the system there.

---

### Post by Bashing-om on 2015-11-21
kvanoff; Ho Kay ;

As a jumping off place we need to know that 'YOU" have authority to access your desktop:
what returns from terminal commands:
```

ls -al /home/
ls -al /home/<username>

```
where <username> is your actual system ID ,

And while on my mind what graphics are at play here ?
Intel, AMD, Nvidia ?
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```
will provide a lot of info quickly.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by don62 on 2015-11-22
I am also stuck in this LogIn loop.
Have a Compaq Presario CQ61 Notebook.
Problem seems to have started after I updated 14.04.3 today.
Never been asked for password before on startup but now it does.
I enter my password but it just loops round & round.
Have tried ctl+alt+F1, but still asks for user name & password
& then keeps looping. Its as if it is not accepting my password.
Any advice will be greatly appreciated.

---

### Post by Bashing-om on 2015-11-22
don62; Hello;

Same same advise applies as given to kvanoff . Before we can say we need to know IF "you" have authority, and next the hardware and IF a driver is installed.
Proved the requested outputs and we can proceed .

As ctl+alt+F1 is not available, try to boot to "recovery mode" from grub's boot menu .
[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by don62 on 2015-11-22
Thanks Bashing-om. But I can't get past the user name & password after ctl-alt-F1.
It keeps looping.
Sorry if I am thick.

---

### Post by don62 on 2015-11-22
When I say it keeps looping, I get the message "login incorrect" & round we go again.

---

### Post by Bashing-om on 2015-11-22
don62; Well ...

As amended - my last - can you boot the "recovery" console ?

Else we boot to terminal from grub .

[INDENT][INDENT]we will find a way
[/INDENT][/INDENT]

---

### Post by don62 on 2015-11-22
Sorry Bashing-om, just re-read your response.
OK, but how do I get to [COLOR=#000000]"recovery mode" from grub's boot menu"[/COLOR]

---

### Post by Bashing-om on 2015-11-22
don62; K;

I take it that ubuntu is the sole operating system installed ( as you do not get a grub menu when booting) .
If this is a bios based system; as soon as the bios screen clears depress and hold a shift key -> grub boot menu -> advanced options -> recovery kernel -> root terminal . Here the system is booted in a read only mode . Good enough for our present purposes . If required at a later time we can then remount the system to also permit writing to it .

IF UEFI ( newer hardware ) it is the escape key that grub will recognize . depress and release the escape key .

[INDENT][INDENT]the process too
[INDENT][INDENT]of learning
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by don62 on 2015-11-22
Yes Bashing-om, ubuntu IS the sole OS.I have blundered through the unfamiliar GRUB menu & somehow, gotto what I think is where you want me to be. 
At
[EMAIL="root@don-Compaq-Presario-CQ61-Notebook-PC"]root@don-Compaq-Presario-CQ61-Notebook-PC[/EMAIL]~#ls -al /home/    returns
total 28
drwxr-xr-x  3 root root 4096 Mar 6 2014.
drwxr-xr-x  24 root root 4096 Nov 1319:42 ..
drwxr-xr-x  don  don   20480  Nov 22 20:15


but
[EMAIL="root@don-Compaq-Presario-CQ61-Notebook-PC"]root@don-Compaq-Presario-CQ61-Notebook-PC[/EMAIL]~#ls -al /home/Don Xxxx
returns
ls: cannot access /home/Don:  No suchfile or directory
the (space) surname isn't shown, presumably doesn't like (space)


Another fine mess I've got myself in.
Any hope for me.
Thanks.

---

### Post by Bashing-om on 2015-11-22
don62; Scary thought ...

You don't have no home directory ???

Check once more 
```

ls -al /home/don/

```

Should be similar to my output:
```

sysop@1404mini:~$ ls -al /home/sysop/
total 5140
drwxr-xr-x 29 sysop sysop    4096 Nov 22 12:04 .
drwxr-xr-x  4 root  root     4096 May 19  2013 ..
drwx------  2 sysop sysop    4096 Sep 13  2014 #133454 • Fedora Project Pastebin_files
-rw-r-----  1 sysop sysop   11389 Sep 13  2014 #133454 • Fedora Project Pastebin.html
drwx------  2 sysop sysop    4096 May  7  2014 .aptitude
-rw-------  1 sysop sysop   35392 Nov 22 13:44 .bash_history
-rw-r--r--  1 sysop sysop     309 Jul  8  2013 .bash_logout
-rw-r--r--  1 sysop sysop     220 May 19  2013 .bash_logout~
-rw-r--r--  1 sysop sysop     220 Jul  8  2013 .bash_logout-orig
-rw-rw-r--  1 sysop sysop    3393 Sep 17 22:11 bash-n
-rw-rw-r--  1 sysop sysop    3390 Sep 17 22:11 bash-n~
-rw-rw-r--  1 sysop sysop    2154 Mar 20  2015 bash'n~
-rw-r--r--  1 sysop sysop    3835 Jun  7 19:41 .bashrc
-rw-r--r--  1 sysop sysop    3749 Aug  4  2014 .bashrc~
-rw-rw-r--  1 sysop sysop    7195 Oct 24 23:33 Bible
-rw-rw-r--  1 sysop sysop    7115 Oct 21 21:06 Bible~
drwxrwxr-x  2 sysop sysop    4096 Jan 22  2015 bin
-rw-rw-r--  1 sysop sysop    3890 Apr 22  2014 booting_issue~
drwx------ 22 sysop sysop    4096 Feb  3  2015 .cache
-rwxr-xr-x  1 sysop sysop    2297 May 21  2014 chglog~
-rw-rw-r--  1 sysop sysop     561 May 26 16:31 chroot-routine
-rw-rw-r--  1 sysop sysop     544 Nov 17  2014 chroot-routine~
-rwxr-xr-x  1 sysop sysop   19043 Jul 13 20:40 cli_cmds
-rwxr-xr-x  1 sysop sysop   18991 Jun 28 14:31 cli_cmds~
drwxrwxr-x 17 sysop sysop    4096 Feb  3  2015 .config
-rw-rw-r--  1 sysop sysop    5242 Aug  3  2013 cron-rotatelogs~
drwx------  3 sysop sysop    4096 May 19  2013 .dbus
-rw-r--r--  1 root  root   142763 May 27  2013 DejaVuSansMono.pf2
drwxr-xr-x  2 sysop sysop    4096 May 19  2015 Desktop
drwxr-xr-x  2 sysop sysop    4096 Jun 14 19:28 Documents
drwxr-xr-x  2 sysop sysop    4096 Oct 30 20:16 Downloads
-rw-rw-r--  1 sysop sysop   47892 Aug 25  2014 drivers
-rw-rw-r--  1 sysop sysop   47892 Aug 25  2014 drivers~
-rw-rw-r--  1 sysop sysop    6767 Nov 22 14:56 errors-boot.txt
drwx------  4 sysop sysop    4096 Nov 22 11:31 .gconf
-rw-r-----  1 sysop sysop       0 Apr  5  2015 .gksu.lock
drwx------  3 sysop sysop    4096 Jun 26  2014 .gnome
drwx------  3 sysop sysop    4096 May 19  2013 .gnome2
drwx------  2 sysop sysop    4096 Oct 27 09:14 .gnupg
drwxrwxr-x  2 sysop sysop    4096 Feb  9  2015 grubing
-rw-rw-r--  1 sysop sysop    2833 Apr  3  2014 grub-txt~
drwx------  2 sysop sysop    4096 May 19  2013 .gvfs
-rw-rw-r--  1 sysop sysop     997 Sep 29 13:16 Hanjonah-txt
-rw-rw-r--  1 sysop sysop     254 Feb 26  2015 host-txt~
-rw-rw-r--  1 sysop sysop  345119 Jan  6  2014 hwinfo.txt
-rw-------  1 sysop sysop    1304 Nov 22 11:30 .ICEauthority
-rw-r--r--  1 root  root  2477387 Mar 31  2014 initrd.img-3.2.0-29-generic
drwx------  3 sysop sysop    4096 Mar 22  2014 .irssi
drwxrwxr-x  2 sysop sysop    4096 Mar 22  2014 irssi-bac
-rw-rw-r--  1 sysop sysop   12024 Nov  3 13:45 irssi-txt
-rw-rw-r--  1 sysop sysop   11991 Oct 15 21:12 irssi-txt~
-rw-rw-r--  1 sysop sysop    1998 Dec 11  2014 kboard-txt
-rw-rw-r--  1 sysop sysop    1998 Dec 11  2014 kboard-txt~
-rw-rw----  1 sysop sysop    8644 Mar  3  2015 layout
-rw-------  1 sysop sysop     124 Sep 10 15:21 .lesshst
drwxrwxr-x  2 sysop sysop    4096 Nov 14 13:25 less-used
-rw-rw-r--  1 sysop sysop   28396 Oct 11  2012 libudev0_175-0ubuntu13_amd64.deb
drwxrwxr-x  3 sysop sysop    4096 May 19  2013 .local
-rw-rw-r--  1 sysop sysop    1089 Nov 15  2014 makson-txt
drwxr-xr-x  2 sysop sysop    4096 May 19  2013 Music
-rw-rw-r--  1 sysop sysop     544 Nov  3  2014 pastie.txt~
drwxr-xr-x  2 sysop sysop    4096 May 19  2013 Pictures
drwx------  3 sysop sysop    4096 May 19  2013 .pki
-rw-r--r--  1 sysop sysop     675 May 19  2013 .profile
drwxr-xr-x  2 sysop sysop    4096 May 19  2013 Public
-rw-rw-r--  1 sysop sysop   11442 Oct 20 17:09 quotes
-rw-rw-r--  1 sysop sysop   11432 Oct 20 16:17 quotes~
-rw-rw-r--  1 sysop sysop     701 Dec  8  2014 radeon.txt
-rw-r-----  1 sysop sysop   11311 Sep 13  2014 reinstall-packages-txt.html
-rw-rw-r--  1 sysop sysop    6027 Jan 24  2014 resume-wiki~
-rw-rw-r--  1 sysop sysop      66 Feb 15  2014 .selected_editor
-rw-rw-r--  1 sysop sysop   13603 Oct 29 14:57 stat.txt
-rw-rw-r--  1 sysop sysop   13267 Aug 19 09:18 stat.txt~
-rw-rw-r--  1 sysop sysop    5252 Sep  2 19:58 stuff-txt~
-rwxr-xr-x  1 sysop sysop   12471 Oct  5 23:12 sys-info
-rwxr-xr-x  1 sysop sysop   12474 Oct  5 23:09 sys-info~
-rw-rw-r--  1 sysop sysop     858 Oct 17 16:00 systemd-txt
-rw-r--r--  1 sysop sysop   21145 Nov 22 12:04 system-processes
-rw-r--r--  1 sysop sysop   20182 Oct 20 17:29 system-processes~
drwxr-xr-x  2 sysop sysop    4096 May 19  2013 Templates
-rw-rw-r--  1 sysop sysop     286 May 29 11:15 testing
-rw-rw-r--  1 sysop sysop     117 May 29 11:12 testing~
drwxrwxr-x  4 sysop sysop    4096 Jul 14  2014 .thumbnails
drwxr-xr-x  2 sysop sysop    4096 May 19  2013 Videos
drwxrwxr-x  2 sysop sysop    4096 Jan 23  2015 weather
-rw-rw-r--  1 sysop sysop     463 Jul 29  2013 www-explore
-rw-rw-r--  1 sysop sysop     462 Jul 28  2013 www-explore~
-rwxr-xr-x  1 sysop sysop   10768 Oct 14 12:05 wwwoftused
-rwxr-xr-x  1 sysop sysop   10642 Jun 29 12:05 wwwoftused~
-rw-------  1 sysop sysop     209 Feb  4  2015 .Xauthority
-rw-rw-r--  1 sysop sysop       0 May 20  2013 .Xauthority-old
-rw-rw-r--  1 sysop sysop    2074 May 23  2013 Xauthority.sh
-rw-rw-r--  1 sysop sysop    1587 May 23  2013 Xauthority.sh~
-rw-rw-r--  1 sysop sysop    4661 May 24  2013 xauth_stuff
-rw-rw-r--  1 sysop sysop    4661 May 23  2013 xauth_stuff~
-rw-r--r--  1 sysop sysop  374614 Nov 21 21:50 xcopy
-rw-r--r--  1 sysop sysop  374436 Nov 15 22:31 xcopy~
-rw-r--r--  1 sysop sysop  360968 Sep 11 11:49 xcopy~~
-rw-r--r--  1 sysop sysop  182163 Oct  3  2013 xcopy-safe
-rw-rw-r--  1 sysop sysop   28281 Oct 17 11:46 xfce4_cli
-rw-rw-r--  1 sysop sysop   28240 Aug 18 18:17 xfce4_cli~
-rw-rw-r--  1 sysop sysop   22139 May 19  2014 xfce4_cli~~
-rw-rw-r--  1 sysop sysop   67767 Nov 21 19:48 xfer.txt
-rw-rw-r--  1 sysop sysop   67746 Nov 21 18:53 xfer.txt~
-rwxrwxr-x  1 sysop sysop     222 May 22  2015 .xinitrc
-rwxrwxr-x  1 sysop sysop     221 Jul  6  2013 .xinitrc~
-rwxrwxr-x  1 sysop sysop     140 May 24  2013 .xinitrc-bac
-rwxrwxr-x  1 sysop sysop     186 Jul  6  2013 .xinitrc-good
-rw-rw-r--  1 sysop sysop    7659 Oct 28 14:28 .xscreensaver
-rw-------  1 sysop sysop     537 May 22  2013 .xsession-errors
sysop@1404mini:~$ 

```
where I am "sysop" and I have a LOT of working files in my home directory.

[INDENT][INDENT]is there a snake in this wood pile ?
[/INDENT][/INDENT]

---

### Post by don62 on 2015-11-22
OK, loads of files went flashing past, some of which I recognised. Is this good news?

---

### Post by Bashing-om on 2015-11-22
don62; Yeah ...

Good news .. of interest here is the files:
.Xauthotity and .ICEauthority . Do you own them ?
show :
```

ls -al /home/don/.Xauthority
ls -al /home/don/.ICEauthority

```

Depending on that result .. we look next at the graphics .. as if there are problems in the graphics layer of the system no can start a GUI .

[INDENT][INDENT]load is lightened
[/INDENT][/INDENT]

---

### Post by don62 on 2015-11-22
Sure looks like I've got em, both files returned with -rw------- privileges.
Deep breaths now.

---

### Post by Bashing-om on 2015-11-22
verify please they come back similar:
```

-rw-------  1 sysop sysop     209 Feb  4  2015 .Xauthority

```
where you should see 'don' in place of me as 'sysop' .

If that is true .. next we want to look at graphics - if any .
post back:
```

lspci | grep "VGA\|3D"

```

in this return: - that takes a bit of time to complete - 
```

sudo lshw -C display

```
what have we for hardware and is a driver installed:
for reference my output:
> 
description: VGA compatible controller
       product: RV515 [Radeon X1300/X1550]

configuration: driver=radeon latency=0


[INDENT][INDENT]progress,
[INDENT][INDENT][INDENT][INDENT]1 step at a time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by don62 on 2015-11-22
[COLOR=#000000][FONT=Liberation Serif, serif]Both files return similar to yours.[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]lspci | grep "VGA\|3D" returns[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]00:02.0 [COLOR=#ff0000]VGA [/COLOR]compatible controller:  Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (Rev 07)[/FONT][/COLOR]

[COLOR=#000000][FONT=Liberation Serif, serif]Then[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]sudo lshw -C display[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]returned more than a page of info which scrolled off the screen (I don't know how to pause it), neither can I copy & paste it.  There appear to be 2 groups of Info, the second group headed, [/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]*-display:1 UNCLAIMED. [/FONT][/COLOR]
[COLOR=#000000]        [FONT=Liberation Serif, serif]description: Display Controller[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Liberation Serif, serif]product:   Mobile 4 Series Chipset Integrated Graphics Controller[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Liberation Serif, serif]vendor: Intel Corporation[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Liberation Serif, serif]physical id: 2.1[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Liberation Serif, serif]configuration: latency=0[/FONT][/COLOR]

[COLOR=#000000][FONT=Liberation Serif, serif]I don't know the heading for the first group because it scrolled off but the rest of the info is[/FONT][/COLOR]
[COLOR=#000000]         [FONT=Liberation Serif, serif]description: VGA compatible controller[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Liberation Serif, serif]product:   Mobile 4 Series Chipset Integrated Graphics Controller[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Liberation Serif, serif]vendor: Intel Corporation[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Liberation Serif, serif]physical id: 2[/FONT][/COLOR]
[COLOR=#000000]        [FONT=Liberation Serif, serif]configuration: latency=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Liberation Serif, serif]Any other pertinent bits I can give you?[/FONT][/COLOR]

---

### Post by Bashing-om on 2015-11-22
don62; Welp;

The good news is that we have identified the problem:
> 
*-display:1 UNCLAIMED


configuration: latency=0

No display driver ( module) is loaded .

The Bad thing here - in your case - is that it is Intel, and Intel "just works" . Intel supports us very well, and their graphic's driver is incorporated into the kernel.

I have no experience with Intel graphics. Gimme some time, see what I can come up with for a means to get us the graphic's module (driver) loaded .

[INDENT][INDENT]If I knew everything
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by don62 on 2015-11-22
Hey , you have been great to assist a silly old duffer like me. Seems a good time to 
break off as it is 23:27 in little ole UK. Will catch up with you tomorrow.
Sleep tight in the Ozarks & don't worry about my probs. G'night y'all.

---

### Post by Bashing-om on 2015-11-22
don62; Hey !

I got us a way forward.
Boot back into recovery -> root shell ,
Here we are going to remount the operating system to enable writing :
```

mount -o remount,rw /  ##(Note there is no space after the comma.)##

```

And now to install the graphic's driver:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade # nope, only upgrades installed packages that 'update' will not deal with .. NOT a distribution relation ##
sudo apt-get install xserver-xorg-video-intel

```

reboot:
```

sudo shutdown -r now

```

[INDENT][INDENT]now tell me
[INDENT][INDENT][INDENT]all finer than a frog's hair ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kenb2 on 2015-11-22
I have this problem with Ubuntu 14.04.3 also, even though I selected automatic login on installation.  I was told to try new version 15.10, which I did.  No login problem with 15.10 and I also chose automatic login during installation.  But 15.10 is not fully compatible with my machine, screen goes into a fast sideways roll, often and over and over.

So I re installed 14.04.3 because it works perfectly with my machine when I can login.  The problem is that I have to keep trying to login over and over 1 to 10 times before it catches, and logs me in, then everything works wonderfully.

---

### Post by Hodevah on 2015-11-22
Have you thought about the fact that it might be a permissions issue?

in your tty, you could try 
> sudo chown -R yourusernamehere: users/home/yourusernamehere
to get out of the loop during the login.

---

### Post by kenb2 on 2015-11-22
Tried that here is what I got. (where are those code tags?)
ruth@ruth-desktop:~$ sudo chown -R ruth: users/home/ruth
[sudo] password for ruth: 
chown: cannot access ‘users/home/ruth’: No such file or directory
ruth@ruth-desktop:~$

---

### Post by Bashing-om on 2015-11-22
kenb2; Hello:

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

As to " chown: cannot access ‘users/home/ruth’: No such file or directory ": We best take a look:
post back the results of terminal commands:
```

ls -al /home/
ls -al /home/ruth/

```
Where 'ruth' is your system ID .

Let's see what tale
[INDENT][INDENT]gets told
[/INDENT][/INDENT]

---

### Post by kenb2 on 2015-11-22
Hi Bashing-om, I do appreciate your help.  I actually thought you had solved it a while ago.  I had restarted the machine after I replied to you before, and 4 times it logged in and did not ask me for a password at all.  But on the 5th try it took me 12 tries to login, and it asked for the password every time, then finally I'm back logged in.  Weird.  Anyway here is the results.

```
ruth@ruth-desktop:~$ ls -al /home/
total 12
drwxr-xr-x  3 root root 4096 Nov 22 15:52 .
drwxr-xr-x 22 root root 4096 Nov 22 16:31 ..
drwxr-xr-x 22 ruth ruth 4096 Nov 22 22:48 ruth
ruth@ruth-desktop:~$ 

```

```
ruth@ruth-desktop:~$ ls -al /home/ruth/
total 232
drwxr-xr-x 22 ruth ruth  4096 Nov 22 22:48 .
drwxr-xr-x  3 root root  4096 Nov 22 15:52 ..
drwx------  3 ruth ruth  4096 Nov 22 17:17 .adobe
-rw-rw-r--  1 ruth ruth 74857 Nov 22 19:35 AuntRuth.odt
-rw-------  1 ruth ruth   167 Nov 22 22:15 .bash_history
-rw-r--r--  1 ruth ruth   220 Nov 22 15:52 .bash_logout
-rw-r--r--  1 ruth ruth  3637 Nov 22 15:52 .bashrc
drwx------ 26 ruth ruth  4096 Nov 22 21:52 .cache
drwx------  3 ruth ruth  4096 Nov 22 17:09 .compiz
drwx------ 22 ruth ruth  4096 Nov 22 22:23 .config
drwx------  3 ruth ruth  4096 Nov 22 18:02 .dbus
drwxr-xr-x  2 ruth ruth  4096 Nov 22 16:11 Desktop
-rw-r--r--  1 ruth ruth    25 Nov 22 16:12 .dmrc
drwxr-xr-x  2 ruth ruth  4096 Nov 22 16:11 Documents
drwxr-xr-x  2 ruth ruth  4096 Nov 22 16:11 Downloads
-rw-r--r--  1 ruth ruth  8980 Nov 22 15:52 examples.desktop
drwx------  3 ruth ruth  4096 Nov 22 22:48 .gconf
drwx------  3 ruth ruth  4096 Nov 22 18:58 .gnome
drwx------  2 ruth ruth  4096 Nov 22 16:29 .gvfs
-rw-------  1 ruth ruth 16102 Nov 22 22:48 .ICEauthority
drwx------  3 ruth ruth  4096 Nov 22 16:11 .local
drwx------  3 ruth ruth  4096 Nov 22 17:17 .macromedia
drwx------  4 ruth ruth  4096 Nov 22 17:11 .mozilla
drwxr-xr-x  2 ruth ruth  4096 Nov 22 16:11 Music
drwxr-xr-x  2 ruth ruth  4096 Nov 22 16:11 Pictures
drwx------  3 ruth ruth  4096 Nov 22 18:58 .pki
-rw-r--r--  1 ruth ruth   675 Nov 22 15:52 .profile
drwxr-xr-x  2 ruth ruth  4096 Nov 22 16:11 Public
drwxr-xr-x  2 ruth ruth  4096 Nov 22 16:11 Templates
-rw-r--r--  1 ruth ruth     6 Nov 22 16:30 upstart-dbus-bridge.17995.pid
-rw-r--r--  1 ruth ruth     6 Nov 22 16:30 upstart-file-bridge.17995.pid
drwxr-xr-x  2 ruth ruth  4096 Nov 22 16:11 Videos
-rw-------  1 ruth ruth    57 Nov 22 22:48 .Xauthority
-rw-------  1 ruth ruth   711 Nov 22 22:48 .xsession-errors
-rw-------  1 ruth ruth  1287 Nov 22 22:45 .xsession-errors.old
ruth@ruth-desktop:~$ 
```

When I did install and run ubuntu 15.10 and Lubuntu 15 something they both logged in everytime, but soon as I ran firefox or a couple of other programs the sceen would just loose stability.  That's why I went back to 14.04, it works perfectly except for this login problem.  Thanks again for you help.

---

### Post by don62 on 2015-11-23
Hi Bashing-om
Oh dear. have tried
remount,rw /
and even inserted space after remount, comma, rw
but each time receive
remount: command not found

Have not proceeded with sudo commands as not sure 
whether doing so would screw things up, even more than
they are at moment.
Await your instructions with bated breath.
Regards
Don

---

### Post by Bashing-om on 2015-11-23
don62; Owweee ...

The bad is on me !

> **don62 said:**
> Hi Bashing-om
Oh dear. have tried
remount,rw /
and even inserted space after remount, comma, rw
but each time receive
remount: command not found

Have not proceeded with sudo commands as not sure 
whether doing so would screw things up, even more than
they are at moment.
Await your instructions with bated breath.
Regards
Don

Tired and did not I guess double check what I directed>
the correct command and syntax is:
```

mount -o remount,rw /

```
I will edit that error out and we can now move forward ...

Sorry bout that .....
[INDENT][INDENT]to err is human
[INDENT][INDENT][INDENT][/INDENT]but I can really foul things up
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-11-23
james_hunt10; Hey ....

> **james_hunt10 said:**
> login on terminal with no problems

I lost you in the shuffle some how ..

For this server, is it headless ? Such that there is no graphics card installed ?

From the terminal, what returns:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
And we see what we are working with .

[INDENT][INDENT][INDENT]hay it could be
[/INDENT][/INDENT][/INDENT]

---

### Post by don62 on 2015-11-23
Hey Bashing-om, you are a Star :KS-nay Superstar:KS:KS -nay SUPER,SUPERSTAR:KS:KS:KS
It all worked, much to my surprise, as there were so many lines whizzing
off the screen, some saying failed this, failed that, missing this, missing that
& I though it hadn't got a snowballs chance in hell of working - BUT IT DID.
All back up & running as before. Hope it lasts. Will give you a big sticky kiss
if ever I am in Arkansas. Can't thank you enough. Wish I understood it all. 
Once again, many, many thanks.
Regards to you & yours.
Don in North Yorkshire, UK ):P

---

### Post by Bashing-om on 2015-11-23
don62; Hey ... like ...

Outstanding ! glad it worked out .. a load off the mind.

This forum also functions as an institute of teaching , We want that you know and understand . ANYthing you want clarification on .. ask.
Here the only dumb question is the one that is not asked .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ron3872 on 2015-11-24
> **Bashing-om said:**
> verify please they come back similar:
```

-rw-------  1 sysop sysop     209 Feb  4  2015 .Xauthority

```
where you should see 'don' in place of me as 'sysop' .

If that is true .. next we want to look at graphics - if any .
post back:
```

lspci | grep "VGA\|3D"

```

in this return: - that takes a bit of time to complete - 
```

sudo lshw -C display

```
what have we for hardware and is a driver installed:
for reference my output:
[INDENT][INDENT]progress,[INDENT][INDENT][INDENT][INDENT]1 step at a time
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Ok I am good up to this point. 
```

 lspci | grep "VGA\|3D"
 
```
This returns nothing for me.

```

sudo lshw -C display
 
```
This returns my graphic card AMD 6370m. Which my laptop does have AMD 4250/6370m switchable graphics. 
Says my 4250 is *-display unclaimed
              6370m *-display 
               6370M Configuration: driver=fglrx_pci

So do I keep going from this point? or is there another route I need to go?

---

### Post by Bashing-om on 2015-11-24
ron3872; Well ...

We know this is hybrid graphics ? OR SLI ??.. AMD is one of them .
What release are you running ? If 15.10 ; there is a slight hitch . AMD has released the proprietary driver but to this time I do not know that the driver has  made it into our software repository.

As this is AMD .. let's try an alternate 'lspci' command to see what the hardware is:
```

lspci -vnn | grep VGA -A 12

```

And for my peace of mind I would like to see that complete output of 'lshw' :
```

sudo lshw -C display

```
Please use code tags for the outputs:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Find out the hardware
[INDENT][INDENT][INDENT]then see what the options are
[/INDENT][/INDENT][/INDENT]

---

### Post by ron3872 on 2015-11-24
I am using a different PC to post here. I hope this works for the results as I don't know of any other way to show you the results [https://www.dropbox.com/s/f2qyqax439mpxnh/IMG_1111.JPG?dl=0](https://www.dropbox.com/s/f2qyqax439mpxnh/IMG_1111.JPG?dl=0)

EDITED:
using Ubuntu 14.04.3 LTS
It's not SLI so I would say hybrid.

---

### Post by ron3872 on 2015-11-24
ok just found out that because my laptop boots with 4000 series card first the drivers don't work so I need to figure out how to remove the driver to log back in.

---

### Post by Bashing-om on 2015-11-24
ron3872; Well .. 

Running the system on the 2nd graphic's card that does have proprietary driver support . so I guess that is a good thing .

As you can not access the GUI, let us consider (RE-)installing the graphics's driver.
Can you boot to a console ? -> at the login screen key combo ctl+alt+F1 to gain the console.
Login here with your username and password,

I now suggest that you install a tool to relay requested outputs in a text format direct to out pastebin site - may prove difficult to work with/from photographs in our instance :
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install pastebinit

```
And now to tell us what drivers for the chip sets are installed onto the system with these outputs :
```

dpkg -l | grep fglrx | pastebinit

```
and what does the system see for available drivers ?
```

sudo ubuntu-drivers list | pastebinit

```

The result is a URL back in your terminal .. Pass that link back here and we can then access the file(s) and see the requested information .

We will see what results when we (RE-)install a graphics driver.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by ron3872 on 2015-11-24
Sorry if I jumped ahead of you [http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx)
This got me back into my problem. 
```

[COLOR=#000080]hawkman@hawkman-HP-Pavilion-dv7-Notebook-PC:~$ sudo ubuntu-drivers list
[sudo] password for hawkman: 
bcmwl-kernel-source
fglrx-updates
fglrx
hawkman@hawkman-HP-Pavilion-dv7-Notebook-PC:~$ [/COLOR]

```
Hope I did this right but I don't think so lol. I used the above link to remove the fglrx driver for the graphic card. So now I can log into my system that has Ubuntu installed

---

### Post by Bashing-om on 2015-11-24
ron3872; Great .

As you now boot to the GUI:
" Hope I did this right but I don't think so" does not apply.
You did something right or you would not have the GUI.

[INDENT][INDENT]you do good work
[/INDENT][/INDENT]

---

### Post by ron3872 on 2015-11-24
I still have a flickering issue but will sort that out later. Thanks for your help and patience. I am looking at HP's website now. Seems they have updated some bios to use the supported graphic card for the new drivers. Trying to find out if this option is available to my laptop as well. Unless you know of a way to force the computer not to boot with the unsupported graphic card.

---

### Post by Bashing-om on 2015-11-24
ron3872; Welp:

> 
Unless you know of a way to force the computer not to boot with the unsupported graphic card.

That is drifting to far from the subject of this thread . I do suggest ya explore that in another thread.

[INDENT][INDENT]thread are akin to dead men
[INDENT][INDENT][INDENT]one to the box
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

