---
title: "O noes my ubuntu i want him back!"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by 0utlaw 0f Pk on 2008-08-06
I am quoting this from the computing section of a game fansite. But it is the same problem I had before... just couldn't abandom my beautiful OS
> 

[color="green"]Hai Rsc,

You may remember me before where I posted I couldn't get into my Ubuntu OS because it just kept coming up with a random black screen with Busybox on it. I uninstalled Ubuntu and went back to my windows. 2 weeks later, I decided I could not live without it, and decided to once more re-install my Linux. I am still having this same problem. When I press enter on 'Normal Installation' it comes up with Busybox, and the start of the command line is:
```
<Initramfs>
```
Or something similar, I have a terrible memory as I had this error before i took the dog out which was an hour again. But it was definate in the busybox. What can I do to destroy this once and for all!

Thanks in advance.
[/color]


---

### Post by tech9 on 2008-08-06
> **0utlaw 0f Pk said:**
> I am quoting this from the computing section of a game fansite. But it is the same problem I had before... just couldn't abandom my beautiful OS


you could always use the unrecommended rm command

---

### Post by 0utlaw 0f Pk on 2008-08-06
> **tech9 said:**
> you could always use the unrecommended rm command

I just type RM into the busybox?

Sorry about the newbiest question I really shouldn't be using Ubuntu at my level of expertise just I really like it despite it's disadvantages.

---

### Post by cgkades on 2008-08-06
> **0utlaw 0f Pk said:**
> I just type RM into the busybox?

Sorry about the newbiest question I really shouldn't be using Ubuntu at my level of expertise just I really like it despite it's disadvantages.

If ubuntu isnt installing, you could have a hardware problem or conflict. I'm sure there is a compatible hardware list somewhere. Did you try a fresh install? what exactly did you do to come up on this problem? Which version are you using? Have you tried to match the MD5 sums on the ISO you burned? have you tried to reburn the CD? have you tried to at least boot the live CD and try installing that way?

---

### Post by 0utlaw 0f Pk on 2008-08-06
NO NO NO NO NO.

I have not used a CD lol. I used Wubi. And Ubuntu installed fine at first, then I shut down and could not get back in. I have tried every option, all i can get is the busybox or the GRUB.

---

### Post by 0utlaw 0f Pk on 2008-08-06
bump

---

### Post by phidia on 2008-08-06
When in busybox have you tried pressing the Ctrl + D keys and seeing if your system will resume booting?

Sometimes you get dropped to busybox because of partition errors or conflicts between your current partitioning and /etc/fstab. Did you eliminate a partition after you installed ubuntu?

---

### Post by steveneddy on 2008-08-06
Try posting in the WUBI forum or **[COLOR="Blue"]install it on your hard drive[/COLOR]**.

All the cool kids are doing it.

---

### Post by Yotobari on 2008-08-06
The way I found to fix it was to run some file I can't remember what it's called but it was like CKD somthing or other, I'm sure someone else will know and I then installed fine, however this didn't happen after a shutdown, I couldn't get in from the download so it might not work but worth a shot.

---

### Post by pi.boy.travis on 2008-08-06
I have had nothing but problems with Wubi.  It never worked on any of my computers or my buddy's computers.  I didn't look into it, because it was just for my own curiosity.  I would recommend a full hard disk install.

---

### Post by LowSky on 2008-08-06
Real Linux users don't use Wubi.

And the Busybox error can be from using a bad IDE cable. People don't realize this but there are two kinds of IDE cables 40 pin (feels rough) and 80 pin (feels smoother). Always use 80 pin.

---

