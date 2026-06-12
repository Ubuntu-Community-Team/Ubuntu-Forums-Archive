---
title: "ubuntu 11.10 b1 hangs on normal user..."
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by buntu63 on 2011-09-15
hi there! 
black screen,but if i enter on recovery mode leads me to **recovery menu** then resume then resume normal boot then login then i've to $ startx to launch gnomo3!

how can i fix it[if it is possible]? thx in advance...

---

### Post by buntu63 on 2011-09-16
well...folks i need some answer(s) or sadly i'm going to quit this great distro...at this situation nobody can work like this:

cannot read win partition(unable to mount filesystem -not authorized-)
too much to get working the desktop
...

aint impacient...just need to know if is there a solution...

---

### Post by dino99 on 2011-09-16
> **buntu63 said:**
> well...folks i need some answer(s) or sadly i'm going to quit this great distro...at this situation nobody can work like this:

cannot read win partition(unable to mount filesystem -not authorized-)
too much to get working the desktop
...

aint impacient...just need to know if is there a solution...


YES FOR SURE :) POST ON THE DEDICATED SUBFORUM ;)

but you seems too unskilled to test a beta ;(

---

### Post by sisco311 on 2011-09-16
Moved to Ubuntu +1 (Oneiric Ocelot).

---

### Post by cariboo on 2011-09-16
> **buntu63 said:**
> well...folks i need some answer(s) or sadly i'm going to quit this great distro...at this situation nobody can work like this:

cannot read win partition(unable to mount filesystem -not authorized-)
too much to get working the desktop
...

aint impacient...just need to know if is there a solution...

Threatening, to leave isn't the way to get answers to your questions, you could just as well hold your breath until you turn blue.

To answer your question, we need a lot more details, such as what graphics device and driver you are using. If you are totally up to date. What you have done to solve the problem.

Can you start lightdm from the prompt?

```
sudo service lightdm start
```

---

### Post by buntu63 on 2011-09-16
> **cariboo907 said:**
> Threatening, to leave isn't the way to get answers to your questions, you could just as well hold your breath until you turn blue.

Oky docky pal...sorry...

To answer your question, we need a lot more details, such as what graphics device and driver you are using. If you are totally up to date. What you have done to solve the problem.

Intel 915G Express chipset with Integrated Intel Graphics Media Accelerator            900
according to 'synaptic' i have **vesa **and **intel**

Can you start lightdm from the prompt?

after an upgrade not have to write login name neither ```
 $ startx
``````
sudo service lightdm start
```
but... i wanna start normal -i mean to hit the first option- no recovery mode,less the 'sub'menu: **recovery menu** then resume then resume normal boot then **prompt** then startx...

---

### Post by cariboo on 2011-09-17
We have to determine the problem, before we can suggest a way to fix it, does lightdm start when you use the command I gave you?

---

### Post by buntu63 on 2011-09-17
```
sudo service lightdm start
``````
start: Job is already running: lightdm
```

---

### Post by Harry33 on 2011-09-17
Start with recovery mode, then start lightdm.

---

### Post by buntu63 on 2011-09-17
> **cariboo907 said:**
> 

Can you start lightdm from the prompt?

```
sudo service lightdm start
```

> **Harry33 said:**
> Start with recovery mode, then start lightdm.

i think you people do not follow me...when u start u box u first get   **grub 2  **then automatically charges,in my case [COLOR=Red][U][B]the system hangs forever with a black screen...

[/B][/U][/COLOR] that's why i got to choose **'recovery mode' **to get operative...

---

### Post by cariboo on 2011-09-17
We know you get a black screen when you boot normally

Can you tell us if the i915 is loaded, use the following commands to determine if it is:

```
sudo lshw -C display > display.txt 
```

the above command will create a file called display.txt, could you include it in your next post.

---

### Post by buntu63 on 2011-09-17
appreciate u help dude...

---

### Post by buntu63 on 2011-09-17
well...at least now i do not get this annoying step:

**recovery menu** then resume then resume normal boot then **prompt** then startx

hope with 'new' 'magicals' updates could resolve!

btw i do not if installing xfce4 gave me  a [COLOR=Magenta]**debian's  **[/COLOR][COLOR=Black] style grub[/COLOR]?!

---

### Post by cariboo on 2011-09-17
Do you mean grub or gdm? they are two different things. Grub doesn't have anything to do with the problem you are having, from the looks of your output, the graphics chipset isn't being detected properly, and the correct driver isn't being loaded.

---

### Post by buntu63 on 2011-09-17
> **cariboo907 said:**
> Do you mean grub or gdm? they are two different things. Grub doesn't have anything to do with the problem you are having,
 
from the looks of your output, the graphics chipset isn't being detected properly, and the correct driver isn't being loaded.

grub\ i don't have gdm installed...neither gnome-shell  it serves the info...

friend...it is possible to fix it(chipset/driver)? and how?

---

### Post by buntu63 on 2011-09-19
r u people deflated with my case? :P do i uninstall  intel driver or vesa driver?
Btw...is this a bug? need to press cancel twice to  get rid!

---

### Post by buntu63 on 2011-09-19
```
menuentry 'Ubuntu, with Linux 3.0.0-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos3)'
        search --no-floppy --fs-uuid --set=root 0dc8e243-9c84-4cd0-abfc-bcc20d974865
        linux   /boot/vmlinuz-3.0.0-11-generic root=UUID=0dc8e243-9c84-4cd0-abfc-bcc20d974865 ro   quiet splash $
        initrd  /boot/initrd.img-3.0.0-11-generic

```
```
menuentry 'Ubuntu, with Linux 3.0.0-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --c$
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos3)'
        search --no-floppy --fs-uuid --set=root 0dc8e243-9c84-4cd0-abfc-bcc20d974865
        echo    'Loading Linux 3.0.0-11-generic ...'
        linux   /boot/vmlinuz-3.0.0-11-generic root=UUID=0dc8e243-9c84-4cd0-abfc-bcc20d974865 ro recovery nomode$
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.0.0-11-generic

```

grub entry's(if helps on some)

---

### Post by buntu63 on 2011-09-20
bump...

may some Adm/Mod see this post? 

thx...

---

### Post by cariboo on 2011-09-20
Your problem has nothing to do with grub, your graphics adapter isn't being detected properly, and the correct driver isn't being loaded. You could try removing the vesa driver and install the i915 driver to see what happens. The first thing you have to do is determine if the vesa driver is actually loaded, to check in a terminal type:

```
lsmod | grep vesa
```

it will echo back if the driver is installed. To remove it type:

```
sudo rmmod vesa
```

if the command is successful, you won't see any output. To install the i915 module in the terminal type:

```
sudo modprobe i915
```

again if the command runs successfully, there will be no output. You will need to restart X to see if things worked the way they should. If you are starting X from a command prompt, just log out and then run:

```
startx
```

If things work the way they should, once you are at the desktop, click the power button in the top right corner, select shutdown, then click restart. Hopefully that should bring you to a gui login prompt.

---

### Post by buntu63 on 2011-09-20
```
~$ lsmod | grep vesa
vesafb                 13489  1 
:~$ sudo rmmod vesa
[sudo] password for diablo: 
ERROR: Module vesa does not exist in /proc/modules

```

---

### Post by cariboo on 2011-09-20
Didn't you try:

```
sudo rmmod vesafb 
```

like the output of you grep command told you?

---

