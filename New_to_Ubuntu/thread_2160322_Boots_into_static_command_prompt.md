---
title: "Boots into static command prompt"
date: 2013-07-06
forum: New to Ubuntu
---

### Post by dystopias on 2013-07-06
Hello all, 

Here's my setup:  Ubuntu 12.04 64bit.  I have it set to automatically boot into my wife's account (may or may not be important).  

Everything seemed fine but all of a sudden when you start the computer it boots into what, as an old windows user, i would call a command prompt - (wife's name@computername:~$)  like you would see if you opened the terminal from her account.  thing is, you can't type in it.  doesn't respond to any keystrokes.  nothing.

If i boot into recovery mood and tell it to "drop to root shell prompt" it will give me a root prompt.  I tried typing "startx".  Eventually that gave me the default purple background screen and a mouse pointer, but nothing else . . .

the only changes I made yesterday were downloading some updates and reinstalling plex media server . . .anyone have any ideas?

thanks,
Mitchell

---

### Post by Bashing-om on 2013-07-06
dystopias; Hi ! Welcome to the forum .

Let's presuppose that in all that process that a proprietary graphics driver got broke.

Try this:
 Boot up ubuntu from cold boot, soon as the bios screen clears, depress the shift key -> grub menu>
Insure a "non recovery" kernel option is highlighted and press the "e"key for edit mode -> boot parameters; arrow down to the line similar to this "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
; arrow across to the term "quiet splash" and insert the term "nomodeset" -without the quotes-; ctl+x to continue the boot process. GUI login -> user name and password -> desktop. Left side of screen is the launcher ->System Settings ->Additional Drivers  [must have 'net connectivity ]//assumes that 3rd party software sources have been enabled// (re-)Install the recommended driver within the Additional Drivers utility.

Reboot
[INDENT][INDENT][INDENT]all good now ?[/INDENT][/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
Okay, I tried following your instructions.  I added nomodeset before the quiet splash, after it, and at the end of the line (wasn't sure where exactly it was supposed to go.)  In any case, none of those positions made it behave any differently.  after ctrl+x, still goes to the "static prompt".

---

### Post by Bashing-om on 2013-07-06
dystopias; Yuk !

Still not enough info to make more than an educated guess...
What results:
Boot up a liveDVD (bios set to DVD -1st boot priority) -purple splash screen; shift key -> language screen; escape key to accept the default;
Boot options menu -> boot from hard drive.

Looking at: that bios is handing off to grub (GRand Unified Bootloader, ubuntu's booting codes) and grub for whatever reason is not responding ...Be aware grub is generally very good at indicating where the problem is ...in this case ..I just do not presently know what is not transpiring. 

The process:
Basically, we want to make sure that the Grub menu boots. 
Then verify that the kernel is booting;
Then that the XServer Session starts and displays.

[INDENT][INDENT]a process, one thing, then another[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
Having a little trouble following your instructions.  I made a boot disc on a thumb drive.  I was able to boot on the live disc.  what do i do after that?

thanks for trying to help me!

---

### Post by Bashing-om on 2013-07-06
dystopias;

Apologize for the delay in getting back with you ,,, distracted with issues on my install, not affecting operations.

But, Hey ... helping is a good thing ... open source and we are all in this together !

As to using a thumb drive, not sure as I have never used one as a liveMedium... but I seem to recall that rather than the shift key as the actuator... use the tab key.

When booting, as soon as the bios screen clears, depress the tab key (??)
What results ?

[INDENT][INDENT]more than happy to help, I learn ![/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
Okay, after using tab key i chose "boot from first hard disc".  then it gave me the ubuntu loading screen and after a long while gave me the "install ubuntu" screen that lets you chose if you want to try it or install it - like it was still booting from the flash drive and not from the hard drive. . . .

---

### Post by Bashing-om on 2013-07-06
dystopias; Well !

That result sets me back a bit... lemme have a bit to consider what I have in mind and I will get back at ya ..

While considering I will be away from the keyboard ... gotta go to town.
While I am considering.. to make sure we know; do in the liveUSB ->try "ubuntu mode" ->terminal code:
```
 sudo fdisk -lu
```

Be back soonest,

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
here's what i got:

[FONT=arial]ubuntu@ubuntu:~$ sudo fdisk -lu[/FONT]

[FONT=arial]Disk /dev/sda: 320.1 GB, 320072933376 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disk identifier: 0x0003a129[/FONT]

[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sda1   *          63   363245714   181622826   83  Linux[/FONT]
[FONT=arial]/dev/sda2       404201470   625141759   110470145    5  Extended[/FONT]
[FONT=arial]/dev/sda3       363245715   404195399    20474842+   7  HPFS/NTFS/exFAT[/FONT]
[FONT=arial]/dev/sda5       602888192   625141759    11126784   82  Linux swap / Solaris[/FONT]
[FONT=arial]/dev/sda6       404201472   594716671    95257600   83  Linux[/FONT]
[FONT=arial]/dev/sda7       594718720   602888191     4084736   82  Linux swap / Solaris[/FONT]

[FONT=arial]Partition table entries are not in disk order[/FONT]

[FONT=arial]Disk /dev/sdb: 3880 MB, 3880452096 bytes[/FONT]
[FONT=arial]110 heads, 46 sectors/track, 1497 cylinders, total 7579008 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disk identifier: 0x00095a1d[/FONT]

[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sdb1   *        8064     7579007     3785472    c  W95 FAT32 (LBA)[/FONT]
[FONT=arial]ubuntu@ubuntu:~$[/FONT]

---

### Post by Bashing-om on 2013-07-06
dystopias; 

Fdisk relates a Windows' partition ... are you dual booting or is that just a shared partition ?
Do not really think you are dual booting so as only the one partition, just to make sure I know where we are going to,
And BY the way ... you show 2 swap partitions... 1 of which is not needed. There is some disk space that can be reclaimed !

[INDENT][INDENT]short steps but we are getting there
[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
i think i tried dual booting a while ago to do something for work that had to be done on windows.  don't think i ever got it to work or if i did, i only used it once.  In any case any windows partitions can be erased.

---

### Post by Bashing-om on 2013-07-06
dystopias; My My ..

We are getting cleaner and cleaner all the time..Looks like ubuntu is going to inherit a data partition.

Ok lets see the condition of the ubuntu's kernel:

Boot the install to the grub menu ...do the edit routine again to get the boot parameters screen ... and this time rather then the "nomodeset" option;
delete "quiet splash and all after ... and insert the term "text" -between the quotes- ... I hope that you boot to a command line terminal (seems I do recall the "text" term may have been superseded by another)[if no get to tty, will verify]... at this text login type the username of an existing account (preferably the 1st account created at the install) followed by the pass word associated with that account; the pass word will have no response to the screen - security reasons ->linux way.

OK, logged in ?
what results from terminal code:
```
sudo service lightdm start
``` and we will see what the Xserver is up to.

[INDENT][INDENT]just prob'n to see what[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
okay, i got logged in.  i used my account as it was the first one created.  when I tried "sudo service lightdm start" it took me back to the static prompt for my wife's account . . .

---

### Post by Bashing-om on 2013-07-06
dystopias;

That tells us 
Bootlader is good
kernel is good
so we are now looking at Xserver:
so what haps:
Boot back up into the install to the text login ... login as that original user (gonna do admin stuff, that user is the only one than can);
terminal code:
```
unity --reset
```
no response back is good -> log out; reboot ->
```
sudo shutdown -r now
```
do you now boot to the GUI login ?

Else -> "unity --reset" results in errors;
post back the errors generated and  try:
```
sudo dpkg-reconfigure xserver-xorg
```
and again post back any errors;
log out and reboot (shutdown command)

Maybe at this point if still no GUI ... run check/repair filesystem utility (??).

[INDENT][INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
> **Bashing-om said:**
> dystopias;

Boot back up into the install to the text login ... login as that original user (gonna do admin stuff, that user is the only one than can);
terminal code:
```
unity --reset
```



okay, here's what unity --reset gave me (sorry if any mistakes, i have to type this out)

unity --reset
WARNING: no DISPLAY variable set, setting it to :0

(process:1998): GConf-WARNING **:  Client failed to connect to the D-BUS daemon:
//bin/dbus-launch terminated abnormally with the following error: Autolaunch error: x11 initialization failed.

WARNING: environment is incorrect: No D-BUS daemon running

Did you just try to reset in a tty?
unity-panel-service: no process found
compiz (core) - Fatal: Couldn't open display :0

---

### Post by Bashing-om on 2013-07-06
dystopias;
Again not what I was expecting ... humm .. maybe I learned something ...
Anyway, not setting unity .. so what haps with resetting what unity is layered onto ?
the terminal command :
```
sudo dpkg-reconfigure xserver-xorg
```
returns what ? ... by the way .. your (re)typing is admirable effort !

[INDENT][INDENT]still try'n[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
"[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg-reconfigure xserver-xorg" 

this gives me nothing, just gives me a new line with prompt.[/FONT][/COLOR]

---

### Post by Bashing-om on 2013-07-06
dystopias;

No output from a command is generally a good thing,, command accepted and system complied ... and system has nothing else to add .. like no errors to report !

ok ... can you now log into the GUI ?

[INDENT][INDENT]sometimes I wonder, other times I just do not know[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
log into gui - like should i restart computer or do a startx?

---

### Post by Bashing-om on 2013-07-06
dystopias;
Reboot ... 
if X is not running the command "startx" results in the system screaming and hollering, the command "service lightdm start" has generally taken the place of "startx"...

Here's hope

---

### Post by dystopias on 2013-07-06
okay, restarted the computer and let it try to startup.  same problem as before.

---

### Post by Bashing-om on 2013-07-06
dystopias;
Ok round and around I go ...
1. Is the underlying system intact ?
```
ls -la /boot/
ls -la ~/

```
edit:The symptoms really do not indicate but won't hurt to check on authority access.
```

ls -la .ICEauthority
ls -la .Xauthority

```
should return similar:
> sysop@1304mini:~$ ls -la .Xauthority
-rw------- 1 sysop sysop 103 May 29 13:58 .Xauthority
sysop@1304mini:~$ ls -la .ICEauthority
-rw------- 1 sysop sysop 15974 Jul  6 15:06 .ICEauthority
sysop@1304mini:~$ 
where here "sysop" is my username.
If the returns are as expected... no post of the output needed. The system is intact.

2. Is lightdm running ?
Is gdm installed ?
by default lets see if an alternate desktop manager is installed:
```
dpkg -l gdm
``` that is a lower case "L".
and lets do it like this:
> 
 If you have no graphics, go to a text terminal using alt-ctrl-F1
    Stop LightDM with sudo stop lightdm
    Start GDM with sudo start gdm
    Run sudo dpkg-reconfigure lightdm to set the default display manager
    Edit /etc/X11/default-display-manager and set it to /usr/sbin/gdm if
       you can't run the above
    Uninstall LightDM and GDM will replace it after a reboot
    If things go really bad, you may need to remote login using SSH
    or by  using grub to enter a recovery mode (It should never get this 
    bad and if it does then blame X). 

If with gdm you have a GUI after login, we know lightdm is at fault, else ->

and it looks like we are starting to blame X.

[INDENT][INDENT][INDENT]that's what I think
[/INDENT][/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
ls -la -/ returns:  
ls: invalid option -- '/'

---

### Post by Iowan on 2013-07-06
> **dystopias said:**
> ls -la -/ returns:  
ls: invalid option -- '/'


> **Bashing-om said:**
> 
1. Is the underlying system intact ?
```
ls -la /boot/
ls -la[COLOR="#FF0000"] ~[/COLOR]/

``` 

That's a tilde (shift and top left key on my keyboard), not a dash...
(shortcut to home directory)

---

### Post by Bashing-om on 2013-07-06
Hi Iowan .. Glad you are looking over my shoulder.

@dystopias; Please see also my edit to my last post.

[INDENT][INDENT]we be stepp'n[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
ah, sorry about that, evidently i need my glasses.  In any case, dpkg -l gdm returns one line which lists gnome.

when i get to the screen to set the default display manager, it lists gdm and lightdm.  I told it to set gdm as default and restarted.

upon restart, the ubuntu loading screen (the purple screen which says Ubuntu on it and has the five progress dots) stayed up for a long time.  it's been a few minutes and it is still there . . .

---

### Post by Bashing-om on 2013-07-06
dystopias; Hey,

looks like X is broke huh ?? Ok before we get drastic... let's try this:
reconfigure xserver with: 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
 the-phigh flag, Using that forces it to autodetect.

AND ... what did the .Xauthority/.ICEauthority commands return --before attempting to (re-)configure xserver.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
[COLOR=#000000]AND ... what did the .Xauthority/.ICEauthority commands return --before attempting to (re-)configure xserver.

they came back similar to your example of what they should look like.

when I type the code you gave me it returns:
dpkg: error: unknown option --reconfigure

[/COLOR]

---

### Post by Bashing-om on 2013-07-06
dystopias; Hey...looks like I did a typo !
try as:
```

sudo service lightdm stop
sudo service gdm stop ##not that either one is running.. but just in case
sudo dpkg-reconfigure -phigh xserver-xorg
sudo shutdown -r now

```space and "-" character removed from the original command directive.

Let her reboot ... maybe now to the GUI ?? ... try both GDM and lightdm and see what haps.

[INDENT][INDENT]see'n what is to be
[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
okay, now that command gives me:
Unknown option: phigh

---

### Post by Bashing-om on 2013-07-06
dystopias;

Lemme go do some homework on that "phigh"; I expected to be valid... but I can be wrong.

I'll be back.

---

### Post by Bashing-om on 2013-07-06
dystopias; I am Guilty.

I was not following proper syntax in the command formation, Properly it should be:
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Only the one "tac" mark before "phigh"

I will go back and fix that in my prior post.


[INDENT][INDENT]press on ?[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
okay, followed those commands and upon restarting it takes me back to the ubuntu loading screen, where it proceeds to stay.

---

### Post by Bashing-om on 2013-07-06
dystopias;

Well... I have one other thing I want to try (mostly for my education) before we get down and drastic.
Reset the configuration for all packages that use debconf with the command:
```
sudo dpkg-reconfigure -phigh -a
``` with lightdm and gdm stopped.
This will restore a large portion of your system, although there will likely be things that are still configured and set.

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-06
okay, running that just gives me a cursor on a new line, but no prompt. . .

i'll let it sit overnight - bedtime for me!

thanks for sticking with me, i really appreciate it.  i'll be at it again in the morning.

---

### Post by dystopias on 2013-07-07
Okay, this morning it had a prompt.  the only message it had was about a program not being installed and that it had no other information.  the program was scrivener, a word processor that I had tried to install a few months ago.

so i restarted and it took me back to the ubuntu loading screen.  but that is where it stays, it never actually loads ubuntu.

thanks,
Mitchell

p.s. also, i just tried switching the default display manager back to lightdm, and this time it didn't get hung up on the ubuntu loading screen, but took me back to the static prompt that I had originally.

---

### Post by Bashing-om on 2013-07-07
dystopias;

I think at this point we should clean up the system. check the condition of installed packages and insure that the package manager is all happy.........
Then go ahead and (re-)install Xorg and Xserver on that solid foundation.
------------
#oldfreds's methology for restoring:
Then try ( all the # are comments do not type anything after a #)
```

sudo -i #elevates to admin privileges - be sure and careful ! Here, ubuntu assumes you know what you are doing and there is no forgiving of mistakes.
#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get autoremove
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
All that does is update it again.
#log-out from super user
exit

```
Any errors at any point, stop and fix the problem before proceeding further.

When all this runs then we will restore the GUI.

[INDENT][INDENT][INDENT]that's my thought
[/INDENT][/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-07
Okay, did all that, no errors.

---

### Post by Bashing-om on 2013-07-07
dystopias; Hey ..

Playing catch up ...

Ok, here goes :
terminate the X using:
    For Gnome (Ubuntu): 
```
sudo service lightdm stop #or gdm as applies
```
Remove existing xorg using the following command
    ```
sudo apt-get remove --purge xserver-xorg
```
(Re-)Install xorg using the following command
    ```
sudo apt-get install xserver-xorg
```
Reconfigure xorg using the following command
    ```
sudo dpkg-reconfigure xserver-xorg
```
Reboot to see effect:
```
sudo shutdown -r now
```

now do you boot to the GUI ?

[INDENT][INDENT]keep on keep'n on[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-07
okay, just did all that.  back to the static prompt.

---

### Post by Bashing-om on 2013-07-07
dystopias; Yikes !

That blows me away... I am about at the end of my current knowledge... time for me to learn more about what is happening "under the hood".

Everything is in place, all parts are functioning and yet no workie !
Who are you in respect to your operating system ?
```

whoami
who
echo $XAUTHORITY

```
should return similar:
> 
sysop@1304mini:~$ whoami
sysop
sysop@1304mini:~$ who
sysop    tty1         2013-07-07 11:30
sysop    pts/0        2013-07-07 11:30 (:0)
sysop@1304mini:~$ echo $XAUTHORITY
/home/sysop/.Xauthority
sysop@1304mini:~$ 
where, again, "sysop" is my username.

As this is a 'X" problem ... let's see what the logs have to say.
```
less /var/log/Xorg.0.log
```
"q' to quit out of "less"
Do you see anything that is real suspicious ???

[INDENT][INDENT]grasping now... but still hanging in there
[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-07
> **Bashing-om said:**
> dystopias; Yikes !

That blows me away... I am about at the end of my current knowledge... time for me to learn more about what is happening "under the hood".

Everything is in place, all parts are functioning and yet no workie !
Who are you in respect to your operating system ?
```

whoami
who
echo $XAUTHORITY

```
should return similar:
where, again, "sysop" is my username.

As this is a 'X" problem ... let's see what the logs have to say.
```
less /var/log/Xorg.0.log
```
"q' to quit out of "less"
Do you see anything that is real suspicious ???
[INDENT][INDENT]grasping now... but still hanging in there
[/INDENT]
[/INDENT]


okay:  

:~$  whoami
:~$  mitchell
:~$  who
:~$  mitchell tty1      2013-07-07 13:18
:~$  echo $XAUTHORITY

:~$

so, it gives me a blank line after the echo line . . .


as for the log, what am I looking for?  just scrolling through it, the only lines that look suspicious are:

[     21.431] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found  (there are a handful of these lines, with only the numbers after pci changing.)

---

### Post by Bashing-om on 2013-07-07
dystopias;
Do not know how I missed your last response.. trying to keep an eye our for ya...
OK ! We are on to something now... As to where and how you have lost XAUTHORITY I can not imagine,,,and the fglrx errors maybe related.

We are poking our heads "under the hood" and others may be able to advise better -. However I am aware of 1 work-a-round to reassign XAUTHORITY.
It is not elegant, but works !

Taking me a bit to find the reference I am looking for ... back in a bit.

[INDENT][INDENT]keep'n on keep'n on[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-07
dystopias;

I presently have 2 avenues we  can pursue .. I prefer if possible this one - to edit;
On your system --I can not recall my 12.04 - do you have this file ?
```
  ls -la ~/.xinitrc
``` remember there is a "tilde" 
("~/" is short cut allways applicable as "/home/<username>/")

Also by the way --- are you aware of the existence of the manual for all commands and most aps that is available on you system ?
do:
```
 man who
man whoami
```to get a gist of what I am referrng to, resorting to the manual assures you that I am not passing malicious code to you and you have a good idea of what is going on and what the output of a command should look like..

[INDENT][INDENT]mean while, back at the ranch
[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-07
ls: cannot access /home/mitchell.xinitrc: No such file or directory

---

### Post by Bashing-om on 2013-07-07
dystopias;

Ok, I have another option. We have I am fairly sure identified the cause but before proceeding I would like a second opinion. Is there a need for speed to fix your system ? The persons I want to consult with are presently not on-line... can this wait ?


We can proceed, but my fix is a hack .. and I would prefer a better solution - if one exist.
edit:
For info: I have in mind to generate a new .Xauthority file, and in .bashrc export XAUTHORITY.


[INDENT][INDENT]safety is no accident[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-07
Not terribly important, other than it is the only computer set up for my wife to use (she's very low vision, so her account was set up with compiz zooming and high contrast and whatnot).

---

### Post by Bashing-om on 2013-07-07
dystopias;
This situation has pushed me to a "learning mode" and I would like to take advantage of it.. The possibility does exist to just move existing files out of the way and copy "working" files into place ..but in all honesty I do not know ... and I want to know, If there is a better option than "hacking" I am all for it .. and prefer a second opinion.

[INDENT][INDENT]inquiring minds want to know
 [/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-07
well, the only thing i know how to do would be to rescue any files I need off the hard drive, wipe it, and reinstall.  but hopefully it won't come down to that.

thanks for your help, and I probably have a couple more days before my wife gets on my case about it. :-)

---

### Post by Bashing-om on 2013-07-07
dystopias;

Good deal ..lemme get ahold of an associate and get his opinion... should be resolved quickly after that.

[INDENT][INDENT]later
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-07-07
Sorry to stick my oar in late but I would think that the XAUTHORITY variable being unset is normal outside of a GUI session (if I switch from a running unity desktop to tty1 using Ctrl-Alt-F1 for example 'echo $XAUTHORITY' comes up empty even though the file ~/.Xauthority obviously exists)

Also AFAIK the X server doesn't need a pre-existing .Xauthority *file* in order to start (it will create one if missing) 

I haven't read the thread from top to bottom but have we checked that the /home/user is owned/writeable by the user and not full up? That's one thing that can stop a user's X session from starting

```

df -h /home

ls -ld /home/*your-wifes-login-name*

```

Are you still getting to a prompt like "wife's name@computername:~$" ? if so that would suggest that the lightdm auto-login is still enabled for your wife (in spite of the dpkg-reconfigure) and that it's working - up to a point (that point being the startup of her chosen desktop session) - if so it might be useful to scan the lightdm / greeter logs e.g.

```
sudo grep -r '*your-wifes-login-name*' /var/log/lightdm/
```

EDIT: if the autologin *is* still enabled, then disabling it for now might be helpful - it would at least let us see if the system can get as far as the lightdm GUI login screen (and may allow us to select an alternative desktop if you have one installed, or at least a 2d session)

You can do that either by editing the /etc/lightdm/lightdm.conf file manually (using 'sudo nano /etc/lightdm/loghtdm.conf) or with the following command

```
sudo sed -i 's/autologin-user=/&#/' /etc/lightdm/lightdm.conf
```

and then restart the lightdm service or reboot

---

### Post by dystopias on 2013-07-07
well, the only thing i know how to do would be to rescue any files I need off the hard drive, wipe it, and reinstall.  but hopefully it won't come down to that.

thanks for your help, and I probably have a couple more days before my wife gets on my case about it. :-)

---

### Post by Bashing-om on 2013-07-07
@steeldriver;

Thanks .. yeah, agree I may be jumping to conclusions//an alternate DM (gdm) can not access the GUI either. I am about out of ideas for what to check. The system is solid, stable and fully updated... just not able to access the GUI. One must have authority to access x-server but I do not know how that mechanism functions.

[INDENT][INDENT]sorta 'tween a rock and a hard place[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-07
> **steeldriver said:**
> Sorry to stick my oar in late but I would think that the XAUTHORITY variable being unset is normal outside of a GUI session (if I switch from a running unity desktop to tty1 using Ctrl-Alt-F1 for example 'echo $XAUTHORITY' comes up empty even though the file ~/.Xauthority obviously exists)

Also AFAIK the X server doesn't need a pre-existing .Xauthority *file* in order to start (it will create one if missing) 

I haven't read the thread from top to bottom but have we checked that the /home/user is owned/writeable by the user and not full up? That's one thing that can stop a user's X session from starting

```

df -h /home

ls -ld /home/*your-wifes-login-name*

```

Are you still getting to a prompt like "wife's name@computername:~$" ? if so that would suggest that the lightdm auto-login is still enabled for your wife (in spite of the dpkg-reconfigure) and that it's working - up to a point (that point being the startup of her chosen desktop session) - if so it might be useful to scan the lightdm / greeter logs e.g.

```
sudo grep -r '*your-wifes-login-name*' /var/log/lightdm/
```

EDIT: if the autologin *is* still enabled, then disabling it for now might be helpful - it would at least let us see if the system can get as far as the lightdm GUI login screen (and may allow us to select an alternative desktop if you have one installed, or at least a 2d session)

You can do that either by editing the /etc/lightdm/lightdm.conf file manually (using 'sudo nano /etc/lightdm/loghtdm.conf) or with the following command

```
sudo sed -i 's/autologin-user=/&#/' /etc/lightdm/lightdm.conf
```

and then restart the lightdm service or reboot

sorry, some how i missed your post.  In any case, here are the results from your suggestions:

df -h /home
/dev/sda6 90g size 69g used 17g avail. 81% used.

ls -ld /home/elizabeth
drwxr-xr-x 40 elizabeth elizabeth 4096 Jul 7 12:46 [COLOR=#0000cd]/home/elizabeth
[/COLOR]
I get the prompt when lightdm is set as the default display manager.  when i set it to GDM it just gets to the ubuntu load screen and hangs there.

sudo grep -r '*your-wifes-login-name*' /var/log/lightdm/

returns a bunch of lines, none of which stand out to novice me as being bad.  they all say DEBUG in them.

for example it will say something like:

/var/log/lightdm/x-2-greeter.log:[+2.22s] DEBUG: unity-greeter.vala:332: Adding/updating user elizabeth (elizabeth)
/var/log/lightdm/x-2-greeter.log:[+2.29s] DEBUG: Starting authentication for user elizabeth . . .
/var/log/lightdm/x-2-greeter.log:[+2.81s] DEBUG: Authentication complete for user elizabeth with return code 0
/var/log/lightdm/x-2-greeter.log:[+29409.01s] DEBUG: user-list.vala:573: Start session for elizabeth

etc.

there are six lines that look a little different:

/var/log/lightdm/lightdm.log:[+0.00s] DEBUG: Starting new display for automatic login as user elizabeth
" DEBUG: automatically logging in user elizabeth
" DEBUG: started session 1582 with service 'lightdm-autologin', username 'elizabeth'
" DEBUG: Autologin user elizabeth authorized
" DEBUG: Writing /home/elizabeth/.dmrc
" DEBUG: Starting session xterm as user elizabeth

(i've used " to indicate more or less same as last line)

i did your code to disable the auto-login, will report back when i restart.

edit: upon restarting, took me to the login screen.  chose my account and it loaded right up.  going to try to restart and then login to wife's account now.  also, when i did get into my account it brought up the "do you want to report problem" option.  I clicked yes and send, but then realized it wasn't going to send me a copy of the report.  it said something about gdm crash.

edit: okay, tried loggin into wife's account.  this time it took me back to the prompt, but the difference is that now it lets me type commands, whereas before it would not. . .

---

### Post by steeldriver on 2013-07-07
OK well for whatever reason it believes your wife wants to start a plain xterm (X terminal) instead of a full desktop session 

```
DEBUG: Starting session xterm as user elizabeth
```

That's likely either because it's finding a .xsession file (or .xinitrc - but I believe Bashing-om had you check for that earlier) or because 'xterm' got set as your wife's saved session

---

### Post by Bashing-om on 2013-07-07
There is now light at the end of the tunnel !

[INDENT][INDENT]step'n out big
[/INDENT][/INDENT]

---

### Post by dystopias on 2013-07-07
okay, so what can i do about that?

---

### Post by steeldriver on 2013-07-07
... when you get to the GUI login screen, press the little circle icon next to your wife's name and see if it gives you the option to select a regular 'ubuntu' session

---

### Post by dystopias on 2013-07-07
okay, i'll try that.  thanks for your help!


any idea what could have caused this?  i'd like to not have to go through this again . . .

---

### Post by steeldriver on 2013-07-07
Too early to guess - it's certainly unusual! I can't say I've heard of it happening before, let's see whether you are able to select a regular session first, then we can do some forensics

---

### Post by dystopias on 2013-07-07
Okay, I changed it to Ubuntu - and it seems to load except for the fact that there is no top bar . . so i don't have access to any menus, etc. . . 

could this be a problem with compiz?  I know that is something i've had trouble with in the past and is something that was enabled on wife's account but not mine . . .

---

### Post by steeldriver on 2013-07-07
Yes that sounds like a compiz settings issue - if you're on 12.04 you can try

```
unity --reset
```

(which I think you tried before - but would not have worked outside of an active unity session) - OTOH if you are on 12.10 or beyond you need another method, I'd recommend the 'dconf' method described here --> 
[http://www.liberiangeek.net/2013/04/how-to-restart-unity-and-compiz-in-ubuntu-13-04-raring-ringtail/](http://www.liberiangeek.net/2013/04/how-to-restart-unity-and-compiz-in-ubuntu-13-04-raring-ringtail/)

---

### Post by dystopias on 2013-07-07
I think i stayed on 12.04 because my wife didn't like unity.  I had it on her account to not use the sidebar thing. . . not sure how i did that.

i did ctrl alt t and reset unity, it brought back both the top bar and the side bar. . . maybe i can get her to use the side bar.

however, while attempting to copy the text so i could post it here, i hit ctrl c (as i always hit that before remembering to do shift ctrl c) and everything went away again . . . then the terminal became unresponsive to the keyboard.  did a hard reset, going to try again.

edit: after restarting it came up fine, with both side and top bars . . .

---

### Post by dystopias on 2013-07-07
Okay, so I think it is working for the moment.  Anything else you guys can think of that I should do to ensure stability?

and thanks again for all your help. I'm slowly learning more about Linux, but experiences like this one are what are keeping me from going back to windows.

---

### Post by Bashing-om on 2013-07-07
dystopias;
Thanks again to steeldriver !
Sorry for delay .. my system crashed and did not come back up clean// all looks good now.

Stability: Well I have encountered several times that "auto login" causing issues.. I think with ubuntu's security model, trying to circumvent these staples is a bad idea ... might consider changing the Wife's password and make it short and simple (on my Wife's her pass word is but 2 letters and 2 numbers- short enough but good enough that the password does not get missread and/or confused when apps access the authentications).

As to why an interrupt (ctl+c) would cause any adverse effects...something is not right ... have the default key mappings been altered ?

Alternate desktop if the Wife does not like unity... gnome shell co-exists nicely.

Our operating system of choice because millions of people - by choice -make it work.

[INDENT][INDENT]and hey all's well that ends well
[/INDENT][/INDENT]

---

