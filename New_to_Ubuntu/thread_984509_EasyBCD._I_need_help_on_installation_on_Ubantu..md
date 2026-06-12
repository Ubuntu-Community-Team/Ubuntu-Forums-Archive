---
title: "EasyBCD. I need help on installation on Ubantu."
date: 2008-11-16
forum: New to Ubuntu
---

### Post by TheJoke on 2008-11-16
Ok i totally installed Uabntu 8.1 and now i can't log into windows. I already did the /FIX stuff.

I'm trying to use EasyBCD now, how can i install it so i can use it on Ubantu?

Do i have to use the Terminal? If so, can i get the code?


:confused:

---

### Post by CLomax on 2008-11-16
You mean ```
fdisk /mbr
```?

If that doesn't/didn't work then you'll need the Windows compatibility layer, WINE:

```
sudo apt-get update && upgrade
```
```
sudo apt-get install wine
```

Hopefully the .exe should install.

You then have to create a MBR appropriate to your setup and replace the existing MBR on your Windows partition with the one you created in EasyBCD.

I can't remember how to do this but I know it worked for me.

Best of luck to you.

---

### Post by TheJoke on 2008-11-16
i thought the fdisk thing only works on XP.

Do i need a link to WINE?

Or do i just put the code in?

Where should the exe. install?

---

### Post by caljohnsmith on 2008-11-16
Here's a guide to adding Ubuntu to Vista's boot menu via EasyBCD:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

And just curious, but is there some particular reason you don't want to use Grub as your boot loader?

---

### Post by CLomax on 2008-11-16
> **TheJoke said:**
> i thought the fdisk thing only works on XP.

Do i need a link to WINE?

Or do i just put the code in?

I apologise, I should have made it more clear.

I was wondering if the command you tried in Windows was the fdisk /mbr command. Also, what version of Windows? If it's Vista you can boot up on the DVD and fix it easily from there. If it's XP, as far as I know, you'll need to create a new MBR with EasyBCD in WINE. Speaking of which...

The last two commands can be entered into the terminal (Applications -> Accessories -> Terminal : One after another). The first one updates the system in case you haven't done so already, the second one installs the WINE program. No need to find it on the internet :).

---

### Post by CLomax on 2008-11-16
> **caljohnsmith said:**
> Here's a guide to adding Ubuntu to Vista's boot menu via EasyBCD:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

And just curious, but is there some particular reason you don't want to use Grub as your boot loader?

I'd follow that tutorial, it's very good and makes it more clear than I can :p.

Good question. +1 for recommending Grub, the Windows MBR doesn't play nicely with other OSes.

---

### Post by TheJoke on 2008-11-16
I just want to get away from linux. All my files are on Vista.

For some reason Easy won't load on Ubantu.

---

### Post by CLomax on 2008-11-16
> **TheJoke said:**
> I just want to get away from linux. All my files are on Vista.

For some reason Easy won't load on Ubantu.

Ah, I see.

Right click on the .exe file and 'Open with Other Application', click the arrow next to 'Use a custom command' and type 'wine', then 'Open'.

That should do it.

---

### Post by caljohnsmith on 2008-11-16
There's no reason to use EasyBCD in Ubuntu, because EasyBCD needs to run in Vista so that it can modify Vista's boot loader. That's the whole point of the program. :)

---

### Post by TheJoke on 2008-11-16
Well i can't access Vista so what can i do?

---

### Post by CLomax on 2008-11-16
> **caljohnsmith said:**
> There's no reason to use EasyBCD in Ubuntu, because EasyBCD needs to run in Vista so that it can modify Vista's boot loader. That's the whole point of the program. :)

Yup.

But if TheJoke is absolutely sure that he (?) wants to use Windows' MBR instead of Grub, all we can do is recommend it.

---

### Post by caljohnsmith on 2008-11-16
> **TheJoke said:**
> Well i can't access Vista so what can i do?
Do you have a Vista Install CD? If so, you can just go to the command line and run:
```
bootrec /fixmbr
```
If you don't have a Vista Install CD, you could either download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"), or I could give you directions for installing a Windows MBR (Master Boot Record) from the Ubuntu Live CD if you want (that's what the above command does--it installs a Windows MBR).

---

### Post by InfectedWithDrew on 2008-11-16
I have a sneaking suspicion that this user accidentally formatted his entire drive and no longer has Windows Vista.

----------------
Now playing: [Shinedown - 45 (Acoustic)](http://www.foxytunes.com/artist/shinedown/track/45+(acoustic))

---

### Post by CLomax on 2008-11-16
> **TheJoke said:**
> Well i can't access Vista so what can i do?

OK, we could try the following:

```
sudo gedit /boot/grub/menu.lst
```
Scroll to the bottom,
You should see something like:
```
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=b4e57226-d71d-4c10-a23f-175a5c054bf2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet
```
I'm assuming your Windows partition is hd(0,0) so add this...
```
title		Windows
root		(hd0,0)
chainloader      +1
```

Restart, press ESC when you see something counting down and try loading Windows again.

---

### Post by TheJoke on 2008-11-16
Thanks i'll try it.

---

### Post by TheJoke on 2008-11-16
Ok i did the thing and windows showed up but i got a error: 13 " it said invalid executable program"

---

### Post by caljohnsmith on 2008-11-16
How about posting:
```
sudo fdisk -lu
```
So we can see your partitions and make sure you still have a Vista partition.

---

### Post by TheJoke on 2008-11-16
/dev/sda2        12932325   488392064   237729870    5  Extended
/dev/sda5       483106743   488392064     2642661   82  Linux swap / Solaris
/dev/sda6        12932451   477821294   232444422   83  Linux
/dev/sda7       477821358   483106679     2642661   82  Linux swap / Solaris


Is that it. I beleive Extended is windows. It has the 240GB i left it with.

---

### Post by caljohnsmith on 2008-11-16
Unfortunately it looks like InfectedWithDrew was right, you don't have a Vista partition any more. You'll have to reinstall Vista if you want Vista again.

---

### Post by TheJoke on 2008-11-16
Will all my personal stuff still be on Vista beacuse i know i did not format my drive.

---

