---
title: "Booting error"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by fractalman on 2011-10-23
my install of 11.04 suddenly stopped loading, it gets to the ubuntu logo with the flashing red dots but once they stop flashing it just hangs and won't let me do anything.  I had this problem on a previous natty iso so i downloaded a new one and burnt another iso , i made sure i burnt it at a slower speed but now after installing i have the same problem it was working ok for about a week, installed fine, no major problems and now just wont boot  the only thing i can do is ctrl-alt-del and restart,  i have been able to boot into other o/s on my ext hard drive, just the pc one seems to be having a problem at start up

---

### Post by ajgreeny on 2011-10-23
Has there been a new kernel released?

Even if not, I suggest you try an earlier kernel from the grub menu.  Hold shift a boot time if no grub menu normally appears, and choose the next lower kernel in the list, but not the recovery mode, to see if that will boot OK.

---

### Post by fractalman on 2011-10-23
Cheers,  there's only one install on the drive so normally i don't see the grub menu but i shall try that next time it happens.

---

### Post by fractalman on 2011-10-24
well it just happened again, i held shift and got the grub menu, there's only one kernel on there which should be the latest natty one.  i can boot into recovery mode ok and log in and access and run stuff from the terminal.  i can also boot into failsafe graphics mode but the screen res is awful.   should i try a different graphics driver? i'm using the nvidia current and it was working ok with no probs  please post any commands if you need outputs, thanks

---

### Post by Jaybyrrd on 2011-10-24
When the boot fails does it give you a screen from which you can see where the boot hung at.
 
For example I recently upped to Oneiric and my boot was hanging and would instantly go to a black screen with all of the processes that the OS was running and where it was hung.
 
I was hung at:
 
```

Starting Userspace Bootsplash
Stopping Userspace Bootsplash
```
 
Did some detective work and discovered that it was a Graphics Card Issue dealing with my drivers. Can you get info on where Ubuntu is hanging at?
 
 
Also it would not hurt to go ahead and do:
 
```
 lspci | grep 
```
 
That will give more info on your graphics card.
 
Next you should be able to access terminal without booting into recovery mode by hitting ctrl+alt+F2, which may save you time from rebooting just to get into recovery, and switching back.
 
And finally 11.04 should be usinig gdm, you may want to change your default and see if you can achieve a successful boot so try:
 
```
 sudo dpkg-reconfigure gdm 
```
 
(If you are runing something other than gdm, like lightdm or kdm, just replace gdm with what you are using)

---

### Post by sandyd on 2011-10-24
> **fractalman said:**
> well it just happened again, i held shift and got the grub menu, there's only one kernel on there which should be the latest natty one.  i can boot into recovery mode ok and log in and access and run stuff from the terminal.  i can also boot into failsafe graphics mode but the screen res is awful.   should i try a different graphics driver? i'm using the nvidia current and it was working ok with no probs  please post any commands if you need outputs, thanks
When you get to grub, go to the first menu item, and press 'e'

Remove "quiet splash" from the linux line.

---

### Post by fractalman on 2011-10-24
Jaybyrrd, 

 it just hangs at the ubuntu logo, the dots flash across then all go red and it stops.  the only thing i can do from there is ctrl-alt-del.

I tried installing a different nvidia driver and it booted ok but some of the windows were glitching when i opened them and it said the driver wasn't actually in use so i went back to nvidia current and got the same problem

i tried

```
sudo dpkg-reconfigure gdm
```

made no difference,

  i'm not sure which grep commands i need to run,  i tried grep help but nothing screamed graphics hardware at me
```
lspci | grep
```
returns
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.

Sandyd,  

i tried pressing 'e' on grub menu and removing 'quiet splash' and it booted ok,  is there a config file i need to edit or will that change be permanent from now on?

Thanks,

---

### Post by Jaybyrrd on 2011-10-24
Oops I feel like an idiot now

```
lspci | grep VGA
```

But problem solved at this point, and way more easily done the other way. Are you're windows still glitchy?

---

### Post by ajgreeny on 2011-10-24
Use the command ```
gksudo gedit /etc/default/grub
``` to open that file with root permissions and delete the quiet splash from the line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```leaving the "" marks empty.  That will make the change permanent.  What you did is only for that single boot.

---

### Post by fractalman on 2011-10-24
ok i got this result

 phi@crust1:~$ lspci | grep VGA 02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)


 ajgreeny,  Shall edit that file, thanks

---

### Post by fractalman on 2011-10-25
ok so i edited the file but now when i log in have to manually adjust the screen resolution everytime, how do i permanently adjust the screen res because the nvidia settings panel doesn't seem to save any configuration?

---

### Post by fractalman on 2011-10-25
ok, had a quick google.  if i change the settings in the nvidia control panel it doesn't save them but i opened system>preferences>monitors   and clicked 'make default'  and it seems to have worked, i just rebooted and logged back in and the resolution has been saved.  thanks for the replies,  much appreciated :-)

---

