---
title: "Pc Down After Update Desperate For Help Machine Has Been Down For 6 Weeks Now"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by workshop1702 on 2008-04-28
hi i desperatly need help getting one of my pcs running again , i am using ubuntu 7.10 i did an update about 6 weeks ago and this caused a problem and i cannot use the machine at all , despite posting a question on the forum no one has replied .i got so desperate to get it going again i even tried to reload ubuntu from the disc , this also failed as i cannot get it to boot from the disc , i have the first boot set to cdrom 1 so it should do it , but it doesnt.
a problem i had before doing the updates was that after pluging in a usb external dvd burner i could not see the cdrom or my cd burner anymore . i also posted a question on this problem but non of the answers sorted it out , this may be why it wont boot from the cdrom . 
when this machine boots i end up with a command screen no picture . this is what it says 

starting up ...
loading, please wait...
kinit: name-to-dev-t(/dev/disk/by-uuid/c7bo3b93-970a-4fa3-8885-08484515da56) =sda5(8,5)
kinit:trying to resume from /dev/disk/by-uuid/c7b03b93-970a-4fa3-8885-08484515da56
kinit: no resume image,doing normal boot...
ubuntu7.10 compaq-workshop-2 tty1
compaq-workshop-2 login:
i have then loged in but no improvment or any more info
I AM REALY STUCK ON THIS AS I REALY DO NEED TO GET THIS MACHINE RUNNING AGAIN AND AFFRAID I DONT HAVE A CLUE AS TO HOW TO GET IT GOING AGAIN PLEASE PLEASE COULD SOMEONE HELP I REALY WOULD BE VERY GRATFULL FOR ANY HELP:confused:

---

### Post by AndyCooll on 2008-04-28
A couple of things spring to mind. Firstly you could try a fresh install using Ubuntu 8.04 since this is the latest version.

Otherwise if you really want to stick to 7.10, from the basic details you give us, your issue seems to indicate an issue with your graphics card. I'm assuming Ubuntu starts up and eventually drops you to a command line prompt. If so login with your name and password, and try the following command:
```
sudo dpkg-reconfigure xserver-xorg
```
That should take you through a wizard. Accept the defaults until you get to the graphics card section. At that point choose VESA.
VESA is a bog-standard graphics card setting, and not ideal, but it works with just about everything and should at least get you to a gui desktop. You can then do some research to configure your graphics card settings to a better optimum.

:cool:

---

### Post by bobpur on 2008-04-28
If you have graphics / video capability built into the motherboard you could remove the PCI(e) videocard to remove a source of possible conflict. try to boot with only the onboard graphics hooked up to your moniter. if this works, reinstall your PCI(e) videocard remembering to re-enter the BIOS and deactivate the onboard graphics. If you're sure the onboard graphics is already deactivated and that there is no conflict between it and the add-on videocard disregard this and proceed with the reboot.
If you have onboard graphics you could use it anyhow in case you have a bad add-on videocard to get that machine running again.

Good Luck!

---

### Post by lemming465 on 2008-04-28
If you unplug the external DVD burner, can you boot a CD?

---

### Post by workshop1702 on 2008-04-28
have tried this still cannot get it to boot from any cdrom

---

### Post by daimaru on 2008-04-28
> **workshop1702 said:**
> have tried this still cannot get it to boot from any cdrom
don't have a solution for you but maybe someone else can pick it up and help.
If you just want to rescue the files you have on your system prior to a new install, you could maybe try to create a usb-stick ubuntu or other linux distro and boot from usb-stick.
Copy your files and reinstall hardy fresh.

assuming of course that your computer is still able to boot from usb. If not I guess you should look into a hardware related problem.

---

### Post by workshop1702 on 2008-04-28
hi thanks folks for the suggestions affraid i have already tried all of them so far , i have tried using the motherboard graphics , tried running xorg no luck , then tried installing pci graphics card and run xorg again , this also didnt work,i have tried unplugging the dvd burner again no luck,i tried unplugging this before the machine lost picture to see if i could find my cd rom and cd burner again , this also didnt work, as to the trowing it down the stairs i must admit i have been tempted more than once but somhow managed to stop myself,any more suggestions please.

---

### Post by workshop1702 on 2008-04-28
hi again a couple of you have suggested that i could do a fresh install , i dont know how to do this as i cannot get it to boot from a cd , how would i solve this please

---

### Post by daimaru on 2008-04-28
> **workshop1702 said:**
> hi again a couple of you have suggested that i could do a fresh install , i dont know how to do this as i cannot get it to boot from a cd , how would i solve this please
please try booting from a usb stick.

---

### Post by ByteJuggler on 2008-04-28
> **workshop1702 said:**
> hi again a couple of you have suggested that i could do a fresh install , i dont know how to do this as i cannot get it to boot from a cd , how would i solve this please

I would do the following:

1) Go into the BIOS, load "failsafe defaults" or whatever it's called. Reboot.
2) Go into the BIOS, find the "boot order", make *sure* the CDROM is listed first. Reboot.
3) Go to another PC, download Hardy 8.04 (32 bit), burn to CD.
4) On that same other PC, go into the BIOS, change the boot order, and confirm you can boot the CD to the boot menu.  Perform a CD verification.  
5) Assuming the CD passes, go back to the laptop, insert into CDROM and boot from it.  Verify you get to the boot menu.  Do another CD verification,to prove the CDROM on the laptop can read the CD properly.
6.) Boot into the Ubuntu LiveCD.
7.) Mount the old installation, if it's still there, and copy your data off onto an external disk or USB key.
8.) Start the installation process, and reinstall.

Comment: It is possible your laptop's CDROM has developed a fault.  If so, no amount of hacking around will fix it. You need to get that sorted first.  It's also possible your existing CD has developed a fault etc, which is why I'm suggesting burning another and then verifying.

Edit: The booting/installing from USB stick is a good suggestion.

---

### Post by InfinityCircuit on 2008-04-28
Given your description of the problem, I am 99% sure that the solution is much simpler than what everyone here suggests.  If you had a crash during an upgrade in X, dpkg stops configuring packages and you won't be able to use half-configured packages, like hal.

Boot up, login as your normal user, and run:
```

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f
sudo apt-get dist-upgrade
sudo /etc/init.d/gdm start
```

---

### Post by workshop1702 on 2008-04-28
tried infinity circuits suggestions all went well untill the last command , it doest recognise this command , tried a reboot , still get the same as before still no picture

---

### Post by ByteJuggler on 2008-04-29
> **workshop1702 said:**
> tried infinity circuits suggestions all went well untill the last command , it doest recognise this command , tried a reboot , still get the same as before still no picture

OK, perhaps try inserting this before the last command then (see italic/bold line):

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f
sudo apt-get dist-upgrade
***sudo dpkg-reconfigure -phigh xserver-xorg***
sudo /etc/init.d/gdm start

```

---

### Post by workshop1702 on 2008-04-29
still wont have the last line says command not recognised, still no picture

---

### Post by ByteJuggler on 2008-04-29
> **workshop1702 said:**
> still wont have the last line says command not recognised, still no picture

What's the error message?

Try just "startx" then, tell me what happens.

---

### Post by workshop1702 on 2008-04-30
fantastic that last command got it going again i now have the desktop picture back which after 6 weeks is somewhat of a relief thank you very very much for the help . Andrew

---

### Post by workshop1702 on 2008-04-30
hi again seems i got to exited to fast , if i do  a restart the problem is still there i have to type in startx every time to get a picture .it does work when i do this howeverthe resolution is very low and when i try to increase it i cannot acces the resolution settings , i get  x server does not support the xr and r extension . if i could set the resolution it would be great as booth screens are working i can extend the desktop over the two screens and drag pages from one to the other what i cannot do is adjust the screen resolution , some more help would be good and how to get x to start needs sorting . Thanks again Andrew

---

### Post by ByteJuggler on 2008-04-30
> **workshop1702 said:**
> hi again seems i got to exited to fast , if i do  a restart the problem is still there i have to type in startx every time to get a picture .it does work when i do this howeverthe resolution is very low and when i try to increase it i cannot acces the resolution settings , i get  x server does not support the xr and r extension . if i could set the resolution it would be great as booth screens are working i can extend the desktop over the two screens and drag pages from one to the other what i cannot do is adjust the screen resolution , some more help would be good and how to get x to start needs sorting . Thanks again Andrew

Please, you've still not told me what the error message is, that you get after you try "sudo /etc/init.d/gdm start" in the previous posts... I need to know what the actual error with starting gdm is, so I can suggest a way to fix it.

---

### Post by workshop1702 on 2008-04-30
sorry , forgot . it says "command not found"

---

### Post by ByteJuggler on 2008-05-01
> **workshop1702 said:**
> sorry , forgot . it says "command not found"

OK, so gdm is for some reason not installed... OK.    Firstly, try

```
sudo apt-get install gdm
```

Tell us what happens when you do that.  (You might try rebooting and/or try the "sudo /etc/init.d/gdm start" aftwards as well.)

Alternatively, you might try reinstalling the gnome-desktop, which includes gdm, to fix it:
```
sudo apt-get install ubuntu-desktop
```

Tell us what happens when you try these solutions.

---

### Post by workshop1702 on 2008-05-01
hi again thanks very much for the help . i have done what you suggested and the machine starts as it should now , i still am unable to change the screen resolution as as i still get the error message i was getting before if i try system screen resolution .if you can now tell me how i can get round this and set the screen resolution i think that will do it. one other problem i have which i cannot seem to cure is that for some reason after unplging a usb external dvd burner i lost all my cdr and cdrw burner , when i did the update you suggested the machine recognises the cdrom , floppy and the hard drive , it does not see the cd burner , this is an improvment on what i had before , however if i click on any of them it says unable to mount. if you have the time i would be very gratfull of any help sorting this as well. thanks again for the help so far . Andrew

---

### Post by ByteJuggler on 2008-05-01
> **workshop1702 said:**
> hi again thanks very much for the help . i have done what you suggested and the machine starts as it should now , i still am unable to change the screen resolution as as i still get the error message i was getting before if i try system screen resolution .if you can now tell me how i can get round this and set the screen resolution i think that will do it. one other problem i have which i cannot seem to cure is that for some reason after unplging a usb external dvd burner i lost all my cdr and cdrw burner , when i did the update you suggested the machine recognises the cdrom , floppy and the hard drive , it does not see the cd burner , this is an improvment on what i had before , however if i click on any of them it says unable to mount. if you have the time i would be very gratfull of any help sorting this as well. thanks again for the help so far . Andrew

It sounds like the X server is still somehow misconfigured (missing R and XR modules), so can you post the contents of /etc/X11/xorg.conf.  Simplest way to get it is to open it in gedit and copy and paste here. (Press alt-f2, type "gedit /etc/X11/xorg.conf" and press enter and it will open in a text editor.)

I suggest you open a new thread for the CD/DVD burner issue.

---

### Post by bobpur on 2008-05-01
If your machine is running now (after a fashion) I'd get out what I wanted to save and format the drive and do a fresh install. 
But then, I don't have Bytejugglers' expertise. Just a big roll of blank cd/dvd's and a real good burner for when I wear out a cd/dvd. I just burn a new one and fix the problem with a fresh install. :) :)

Good Luck!

---

### Post by ByteJuggler on 2008-05-02
> **bobpur said:**
> If your machine is running now (after a fashion) I'd get out what I wanted to save and format the drive and do a fresh install. 
But then, I don't have Bytejugglers' expertise. Just a big roll of blank cd/dvd's and a real good burner for when I wear out a cd/dvd. I just burn a new one and fix the problem with a fresh install. :) :)

Good Luck!
bobpur:  I'd actually agree with that sentiment to be honest :) , but the original poster was having some issue booting off his CD drive... and as it turned out as one of the other posters intimated it was indeed possible to somewhat recover/rescue the existing system, avoiding a reinstall... hence why we are where we are.    

To the original poster:  Out of interest, are you still having trouble booting off a CD/DVD?  Did you ever try the instructions I gave you in a previous post re going into the BIOS, resetting it, burning a new CD on another PC etc?

---

