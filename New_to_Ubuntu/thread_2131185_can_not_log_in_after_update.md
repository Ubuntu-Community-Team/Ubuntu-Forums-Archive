---
title: "can not log in after update"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by rocka on 2013-04-01
Hi
I am typing this on my phone because I upgraded earlier today after being prompted to and now I cannot login.

only 1 of my monitors is working and the background is low resolution, with a large login prompt in the middle. 
It will not accept my password and I'm sure I'm typing it correctly because it's a very simple one.

When i type in the password it flashes and flickers a bit and then goes back to the same place again.

Please help, I have work to do later tonight and I really don't know what I'm doing or what to do next...

---

### Post by carl4926 on 2013-04-01
At the grub menu
Select the Advanced options, then select the previous kernel option
Does it boot?

---

### Post by black veils on 2013-04-01
if possible can you hold the shift key while booting the computer until grub menu shows, then select previous kernel number and press enter key to boot.

if its back to normal, install grub customizer from ppa, and choose that kernel for your bootable system.

if you cant get it to work, and have ubuntu or another 'live' linux cd/dvd/usb stick, boot that to do your work and get files from hard drive for now.

---

### Post by rocka on 2013-04-01
OK, 
Thanks for the replies so far. 

I've got it to boot into recovery mode, and it will accept my normal password and gets me a command prompt.
I've tried several of the other options (from the grub menu) but none of the non-recovery ones will let me log in.

How do I get from the command prompt to the normal graphical interface again?
When I had trouble in the past after upgrading I had to do something with the nvidia setup, but in this case I can't even get in...

---

### Post by d0006 on 2013-04-01
From: [http://askubuntu.com/questions/31849/how-do-i-restart-unity](http://askubuntu.com/questions/31849/how-do-i-restart-unity)
(this assumes the update is to 12.04 or higher)
First choice
```
unity 
```
Second choice
```
unity --replace &
```
Third choice:
```
killall -u USR1 -r -g unity*
```

---

### Post by rocka on 2013-04-01
Hi,
Didn't get too far with those unfortunately.

First
WARNING: no DISPLAY variable set, setting it to :0
unity-panel-service: no process found
compiz (core) - Fatal: Couldn't open display :0


Second
Warn: Unknown option '-'

Third
Cannot find user USR1

There's other bits, but this is painful typing it all out on my phone. I think I've given the jist of it.

---

### Post by black veils on 2013-04-01
i didn't realise this was an upgrade of versions.

what are the basic computer specs? processor and ram. maybe it can't cope with the new system.

if you had proprietary graphics driver inatalled, i think its meant to be removed before an upgrade.

you have a setup of more than one monitor, which pobably complicated things.

you could try:

sudo apt-get install ubuntu-desktop

or

sudo apt-get install lxde

from recovery mode. choose network option in recovery menu, then drop to shell option.

---

### Post by d0006 on 2013-04-01
I think[**[COLOR=#000000] black veils[/COLOR]**]("http://ubuntuforums.org/member.php?u=1646668") idea is best if you are in a hurry
 
Install this desktop and do whatever you need to do:
```
sudo apt-get install lxde

```
You can fix the rest later.

---

### Post by rocka on 2013-04-01
No, I didn't realise it was a version upgrade either.

There's nothing  special about the computer, it's about 4 years old or so. Quad core, 4G ram, geforce gtx450 video card.

There was no message about removing anything, it was just the usual "updates available" that pops up every now and then.


I've tried that install ubuntu-desktop - it did a bunch of stuff but did not throw up any errors.
After rebooting, still the same unfortunately.

---

### Post by rocka on 2013-04-01
Ok, have tried the lxde one too now, still the same can not log in.

Logging in on the command line with exactly the same username and password works. 
<shrug>
???

---

### Post by d0006 on 2013-04-01
After you login at the command line , try typing 
```
startx lxde
```

---

### Post by black veils on 2013-04-01
so at the ubuntu purple screen you can Ctrl + Alt + F1 and login?

looks like you need a reset of xserver or the nvidia driver. good info in here [http://askubuntu.com/questions/21309/how-to-restore-xserver](http://askubuntu.com/questions/21309/how-to-restore-xserver)

" sudo apt-get remove --purge nvidia-*

Then reinstalled nvidia driver
through Ubuntu setup."

---

### Post by rocka on 2013-04-01
Well I was getting the purple login screen (though not the right resolution etc) and I could get to a terminal with ctrl-alt-F1, but now it just boots directly to the command line.

Now when I try startx lxde it throws up "error in locking authority file" and "unable to connect to X server: no such file or directory

---

### Post by carl4926 on 2013-04-01
Login command line
And do

```
mv .Xauthority .Xauthority-old
```
reboot

---

### Post by rocka on 2013-04-01
Ok I did that and it didn't seem to do anything. No errors at least :)

But still, after rebooting it's straight back to the command line again.

---

### Post by carl4926 on 2013-04-01
You could try with the .ICEauthority

```
mv .ICEauthority .ICEauthority-old
```

---

### Post by rocka on 2013-04-01
Same again.
No errors, but no change either.

---

### Post by black veils on 2013-04-01
have you tried reinstalling nvidia drivers or resetting xserver like my post said?

---

### Post by rocka on 2013-04-01
Do you mean "reinstall nvideo driver through ubuntu setup"? 

If so then no, I haven't had a chance yet. It's just booting to a command line - is there a way to get to ubuntu setup from there?

---

### Post by rocka on 2013-04-01
OK
I'm going around in circles on this one. I've removed and reinstalled the nvidia-current and also nvidia-updates and I've googled quite a bit but I'm still no better off. 

When i reboot or start it from cold it just goes straight to a command line prompt. If I try startx I get
"X: /tmp/.X11-unix has suspicious mode"


I'm thinking I should be going back to basics.
If it was an engine I would be checking the basics - fuel air and spark.
In the Ubuntu world, what is required for the desktop to start? 
What are the basic required files or settings?
How do I go about checking them?

---

### Post by black veils on 2013-04-01
this is why i said about xserver.

you were getting the GUI to an extent, you had the login screen (at wrong resolution).

now you dont get the login screen. perhaps try messing about with lightdm, which is the display manager (brings login screen and GUI). but i doubt that will get you anywhere.

is there no way to reinstall your system? i just figure it might be quicker. if you dont have a 12.04/12.10 installer disc/usb, then you could download the installer and create a disc using another person's computer? if you want to use small amount of their internet bandwidth, you can use the mini.iso which is a small command-line installer, requiring wired internet connection. [http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html)

sorry this is the entent of my being able to help i think. someone with better knowledge and understanding of this area will help.

---

### Post by rocka on 2013-04-01
Well thanks man
I appreciate people on here are helping out of the goodness of their hearts :)

I'm going to go sleep on it, I've got to work in the morning.

See you back here tomorrow...

---

### Post by schragge on 2013-04-01
Please, log in on the text console, install pastebinit and publish the output from */var/log/dpkg.log*
```

sudo apt-get install pastebinit
awk '$3=="upgrade"' /var/log/dpkg.log|pastebinit

``` Then post here the link it will give you.

---

### Post by rocka on 2013-04-01
[http://paste.ubuntu.com/5668653/](http://paste.ubuntu.com/5668653/)

---

### Post by d0006 on 2013-04-01
> **schragge said:**
> Please, log in on the text console, install pastebinit and publish the output from */var/log/dpkg.log*
```

sudo apt-get install pastebinit
awk '$3=="upgrade"' /var/log/dpkg.log|pastebinit

``` 
What are you looking for?  I assume the kernel version and video drivers.  Anything else?
Thanks

---

### Post by rocka on 2013-04-02
Hi
I'm back from work now, so back to have another go. I've posted the pastebin link above as requested earlier.

Can anyone help me with a different tack in the meantime? There are a couple of files on there that I really need to get to. Is there a way to somehow get them to my phone (android) so I could email them to my work?

(or should I start a new thread, and leave this one to the video problems?)

---

### Post by black veils on 2013-04-02
if you do not have a live cd/dvd/usb system you can use, then you will have to do it the command way, should go something like this:
go to the line starting "Connect your usb drive and run"
[http://ubuntuforums.org/showthread.php?t=1458025&p=9145004&viewfull=1#post9145004](http://ubuntuforums.org/showthread.php?t=1458025&p=9145004&viewfull=1#post9145004)

using cd, ls, mount etc

```
sudo fdisk -l
``` or ```
sudo parted -l
``` will show you your drives/partitions


Edit:
finally understand how you would check files are on the destination device after copy command.
```

cd /media
ls
cd myusbdevice/home_backup
ls  [COLOR=#ff0000]**or  **[/COLOR]ls -R  [COLOR=#ff0000]**or  **[/COLOR]ls -alR

```

it is case-sensitive.

---

### Post by jackclarck on 2013-04-02
I was also faced a same problem, and my issue is not resolved by using all these methods is their any other way to resolve it?

---

### Post by rocka on 2013-04-02
Hi,
I tried "ls /dev" but it completely fills the screen with 6 columns of stuff, and I suspect the bit I need has scrolled off. I don't see sdb1 or anything    like it.

How can I make it not overflow the screen?

---

### Post by black veils on 2013-04-02
yes that command gives unreadable results to me, try ```
sudo fdisk -l | less
``` instead to view your devices and determine which it is you want for the destination

to navigate (if needed) press **Ctrl + F** to move forward and **Ctrl + B** to move backward.

---

### Post by d0006 on 2013-04-02
> **rocka said:**
> Hi,
I tried "ls /dev" but it completely fills the screen with 6 columns of stuff, and I suspect the bit I need has scrolled off. I don't see sdb1 or anything    like it.

On a live session the USB drive will be in /media.  On my system it actually shows the model of the USB drive, for example, "CRUZER".

---

