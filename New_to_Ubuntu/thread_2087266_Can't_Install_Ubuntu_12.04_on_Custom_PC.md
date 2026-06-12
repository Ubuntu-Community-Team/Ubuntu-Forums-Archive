---
title: "Can't Install Ubuntu 12.04 on Custom PC"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by linuxn00bface on 2012-11-23
So I bought a custom PC in Hong Kong about a year ago, and it works great with Windows 7. I created an install CD using Brasero on my laptop, on which I've got Ubuntu 12.04. I run the exe on the CD to have it restart automatically.

It takes me to a black screen with white text:

“Completing the Ubuntu installation.
For more installation boot options, press 'ESC' now...
0
_”

The 0 was originally a countdown, and it's stuck at 0, with the underscore blinking, and the whole screen flashing white once every 10 seconds or so.

Gahhhh, I have nothing important on Windows, I don't mind doing a clean erase... Help, please!

---

### Post by NikTh on 2012-11-23
> **linuxn00bface said:**
>  **I run the exe on the CD** to have it restart automatically.

Hi , 
well , I assume you try to install Ubuntu via wubi installer. You have to know that wubi is just for testing Ubuntu. It is virtual installation and not recommended for long time. 

The regular way to install Ubuntu(without erase Windows) is to make-create a dual boot. 

You have to download the iso image of Ubuntu , 12.04 can be found [here]("http://releases.ubuntu.com/precise/") and burn the iso to CD/DVD or USB (for USB you have to use a program like [Unetbootin]("http://unetbootin.sourceforge.net/")). 

Finally, boot from this CD/DVD or USB and Install Ubuntu AlongSide Windows. 

For further - analytic info read here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Thanks

---

### Post by linuxn00bface on 2012-11-23
> **NikTh said:**
> Hi , 
well , I assume you try to install Ubuntu via wubi installer. You have to know that wubi is just for testing Ubuntu. It is virtual installation and not recommended for long time. 

The regular way to install Ubuntu(without erase Windows) is to make-create a dual boot. 

You have to download the iso image of Ubuntu , 12.04 can be found [here]("http://releases.ubuntu.com/precise/") and burn the iso to CD/DVD or USB (for USB you have to use a program like [Unetbootin]("http://unetbootin.sourceforge.net/")). 

Finally, boot from this CD/DVD or USB and Install Ubuntu AlongSide Windows. 

For further - analytic info read here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Thanks

Thanks for the response. Actually, I don't want Windows at all... just Ubuntu. Also, yes I did wubi, however when I boot from CD it just gives me the purple Ubuntu screen with the keyboard and guy in the middle, then goes to a blank screen with a blinking dash.

Help, please?

---

### Post by NikTh on 2012-11-23
Try to use USB (Unetbootin program) or 
[check the MD5](https://help.ubuntu.com/community/HowToMD5SUM) or
burn the CD again at the slower speed. 

Thanks

---

### Post by mastablasta on 2012-11-23
aside form checkign the md5sum as suggested....

what is the configuration of computer? you might need to use boot options (for exampel nomodeset): [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

