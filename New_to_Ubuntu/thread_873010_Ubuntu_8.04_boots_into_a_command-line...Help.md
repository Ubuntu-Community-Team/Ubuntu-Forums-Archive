---
title: "Ubuntu 8.04 boots into a command-line...Help"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by RGARCIA8972 on 2008-07-28
[SIZE="4"]I just installed 8.04 and after the installation it booted into a command-line screen....someone please help.:confused:[/SIZE]

---

### Post by cardinals_fan on 2008-07-28
Could you give some more information please?

---

### Post by finer recliner on 2008-07-28
what happens if you type this command:

```
startx
```

---

### Post by Troll_the_Great on 2008-07-28
Have you installed the desktop edition or the server edition?Because the server edition doesn't have a graphical interface.

---

### Post by RGARCIA8972 on 2008-07-28
Command-line starts like this: "(initramfs)"

---

### Post by RGARCIA8972 on 2008-07-28
> **Troll_the_Great said:**
> Have you installed the desktop edition or the server edition?Because the server edition doesn't have a graphical interface.

Desktop

---

### Post by RGARCIA8972 on 2008-07-28
> **finer recliner said:**
> what happens if you type this command:

```
startx
```

Replys with "Not Found" message

---

### Post by Troll_the_Great on 2008-07-28
Please give us more info.Desktop or server edition?When does this happens?Do you see GRUB menu?Do you see the bar and Ubuntu logo?Do you reach the login screen?It's difficult to know what the problem is with so little info...

---

### Post by RGARCIA8972 on 2008-07-28
> **Troll_the_Great said:**
> Please give us more info.Desktop or server edition?When does this happens?Do you see GRUB menu?Do you see the bar and Ubuntu logo?Do you reach the login screen?It's difficult to know what the problem is with so little info...

Desktop edition,It happens after the Ubuntu load-up bar. I don't know what grub is, so no and there is no login-in screen.

---

### Post by kool_kat_os on 2008-07-28
> **RGARCIA8972 said:**
> Desktop edition,It happens after the Ubuntu load-up bar. I don't know what grub is, so no and there is no login-in screen.

grub is the bootloader ubuntu uses.

and did you do anything that might have made this happen?

---

### Post by RGARCIA8972 on 2008-07-28
> **kool_kat_os said:**
> grub is the bootloader ubuntu uses.

and did you do anything that might have made this happen?
All I did was take out the live CD when the install was completed as I was instructed to by the OS. Then it restarted and this happened.

---

### Post by kool_kat_os on 2008-07-28
Do you have Windows partition? if not...maybe check the cd for defects and reinstall ubuntu and it SHOULD work

---

### Post by Troll_the_Great on 2008-07-28
OK.Log in and type 
```
gdm
``` and see what happens.If is not working try this:
```
sudo apt-get remove gdm
``` then
```
sudo apt-get install gdm
```
Restart with 
```
sudo restart
```
Post back any results.
Cheers!

---

### Post by avtolle on 2008-07-28
One other question that hasn't been asked; did you install Ubuntu on a separate partition or did you install "inside Windows" via Wubi? If the latter, have you done a hard reset or hard power down (pressed the power key) at some point recently (before installing)?

---

### Post by RGARCIA8972 on 2008-07-28
Well I did install it over winXP but that should be fine.

---

### Post by RGARCIA8972 on 2008-07-28
> **avtolle said:**
> One other question that hasn't been asked; did you install Ubuntu on a separate partition or did you install "inside Windows" via Wubi? If the latter, have you done a hard reset or hard power down (pressed the power key) at some point recently (before installing)?

Fresh install via partition.

---

### Post by SilverDragon on 2008-07-28
> **RGARCIA8972 said:**
> Command-line starts like this: "(initramfs)"

I have the same problem on my Dell Inspirion 530(different specs than in my signature). I installed Ubuntu 8.04 and it loads up past GRUB and then takes a while to load up with the orange bar going back and forth for a couple of minutes. Eventually the command line will show with what is quoted above.

The strange thing is sometimes it'll load up right away. My dad noticed that when the Dell keyboard and mouse light up at the same time it'll load up immediately. If the keyboard lights up a second before the mouse (which it usually does) then the orange bar will just go back and forth for a few minutes before the command line shows.

I wiped out the entire hard drive for Ubuntu and I did check the CD for defects. I actually tried the 8.04 Live CD, 8.04.1 alternate CD and 8.04.1 alternate 64 bit cd.

---

### Post by RGARCIA8972 on 2008-07-28
> **Troll_the_Great said:**
> OK.Log in and type 
```
gdm
``` and see what happens.If is not working try this:
```
sudo apt-get remove gdm
``` then
```
sudo apt-get install gdm
```
Restart with 
```
sudo restart
```
Post back any results.
Cheers!

Those cmds are not found....another thing is when the cmd-line starts the top is busybox v1.1.3 with "Enter "help" for a list of built-in commands.

---

### Post by RGARCIA8972 on 2008-07-28
I'm doing this on a Toshiba laptop.

---

### Post by kool_kat_os on 2008-07-28
what? it cant find the sudo command?

---

### Post by RGARCIA8972 on 2008-07-28
> **kool_kat_os said:**
> what? it cant find the sudo command?

that's right message appears like so:

/bin/sh: sudo: not found

---

### Post by kool_kat_os on 2008-07-28
uh....i think something is really not right here.

EDIT: did you put a space before sudo?

---

### Post by SilverDragon on 2008-07-28
Yeah if he's having the same problem as me, you can't even use sudo because you haven't even logged into your account. It goes from the GRUB loading to the orange bar bouncing back and forth, right into the command line. It's not like the terminal(I don't think?) I get weird lines of text after, but that might be unique to my situation.

---

### Post by RGARCIA8972 on 2008-07-28
> **kool_kat_os said:**
> uh....i think something is really not right here.

EDIT: did you put a space before sudo?

yeah tell me about it.....no space just typed as is.

---

### Post by RGARCIA8972 on 2008-07-28
Doing a CD check right now.

---

### Post by kool_kat_os on 2008-07-28
> **RGARCIA8972 said:**
> Doing a CD check right now.

ya...that sounds good

---

### Post by RGARCIA8972 on 2008-07-28
CD Check status: No Errors

---

### Post by kool_kat_os on 2008-07-28
Maybe reinstall ubuntu...and if it give's you the same problem....redownload the cd.

---

### Post by RGARCIA8972 on 2008-07-28
Doing a re-install right now.

---

### Post by RGARCIA8972 on 2008-07-28
New Installed worked.

---

### Post by kool_kat_os on 2008-07-28
> **RGARCIA8972 said:**
> New Installed worked.

Good to hear! :)

---

