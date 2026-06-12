---
title: "Ubuntu 12.04 Loading Screen Resolution"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by serbforce on 2012-06-18
[FONT=Tahoma]Hello,
I would like to know if its possible to change the loading screen resolution to the native resolution of the monitor, in my case 1920x1080.

[http://imageshack.us/photo/my-images/204/p1010402ya.jpg/](http://imageshack.us/photo/my-images/204/p1010402ya.jpg/)


[]("http://imageshack.us/photo/my-images/204/p1010402ya.jpg/")Thanks in advance for any help.

[/FONT]

---

### Post by bogan on 2012-06-19
Hi!, **serbforce,**

If you have Grub Customizer installed, it has a gui method of setting the grub screen resolution.

Otherwise, from a terminal, edit the grub file by removing the '#' symbol and altering the 'GRUB_GFXMODE' to suit. 

Note: highlight the grub menu item, press 'c' to get a grub prompt, then enter 'vbeinfo', to get a list of the resolutions available to Grub, which may not include the one you want. Edit: In my case,although it is not listed by 'vbeinfo,' I set it to="1280x1024x24" and vbeinfo listed that as 'Preferred Mode' and it works OK.```
gksu gedit /etc/default/grub
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="1920x1080x24"
```Save and enter:
```
sudo update-grub
```Chao!, **bogan**.

---

### Post by serbforce on 2012-06-19
Thanks for the reply, but that did not work. Loading screen resolution is still less then that of my monitor.

---

### Post by duracella on 2012-06-20
Which driver are you using? And what graphic card do you have?

Could be a problem with the driver for your graphic card...

---

### Post by serbforce on 2012-06-20
> **duracella said:**
> Which driver are you using? And what graphic card do you have?

Could be a problem with the driver for your graphic card...

GeForce 9600 GT - 295.40 Driver (default nvidia-current in precise)

---

### Post by serbforce on 2012-06-24
Bump :<

---

### Post by bogan on 2012-06-24
Hi!. **serbforce**,

Did you try with Grub Customer?

Is it only the 'loading' screen resolution you want to change?

Can you log-in, and is the resolution then what you want?

I presume you have tried using 'nvidia X server settings' or ' nvidia-config', if it is the latter.

The 295.40 driver is the notorious bugged version, though for some people it apparently works with 9xxx series cards.

I suggest you use one of the later ones or download the NVidia .run file and install from that.

Chao!, **bogan.**

---

### Post by serbforce on 2012-08-22
Bump

---

### Post by bogan on 2012-08-22
Hi!, [B]serbforce,
[/B]
You did not say if you had tried changing the grub background in Grub Customizer, nor do you say if you have tried a later nvidia-current or nvidia .run file. The latest in both is 304.37.

There is not much point in 'Bumping,' if you yourself do not respond to requests for Info, nor to report the results of suggested solutions.

There is a limit on the capabilities of Grub's graphics display at that stage of the Boot-up procedure, but in my case there is no difficulty in displaying 1920x1080x32. Naturally, you have to supply the image to display, in the correct format.

Chao!,** bogan.**

---

