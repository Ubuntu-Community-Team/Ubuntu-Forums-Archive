---
title: "adding swap partition after install"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by beelzebufo on 2014-02-19
I made a mistake and didn't add a swap partition when I installed.  When I do it from a live cd, is there anything else that I will need to do to get ubuntu to know that it has a swap to use?  or will it just autodetect?

thanks for the help
beelzebufo

---

### Post by SuperFreak on 2014-02-19
You can create a Swap partition in GParted . You need to specify the file type when use use the format  command as linux-swap

[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by Bucky Ball on 2014-02-19
It is actually as easy as creating a /swap partition with Gparted (or using the Live install media) and then adding it to your /etc/fstab. 

1/ Create the partition, right click it and 'swapon' so it is active;

2/ Open a terminal and:

```
sudo blkid
```

There, you should see an entry something like this, probably last line. The important part is it ends with "swap"

```
/dev/zram0: UUID="**e197b72d-b267-4572-82f2-1c259f4ab79c**" TYPE="swap"
```

Take note of the UUID number (in bold above, yours will be different). Now, open the /etc/fstab file:
```

sudo nano /etc/fstab
```

... and add this at the very end:

```
UUID=**e197b72d-b267-4572-82f2-1c259f4ab79c**       none    swap    sw      0       0
```

... replacing the UUID with the UUID number you found for "swap" in the 'sudo blkid' command. But the number ONLY. Don't included the " at either end like 'sudo blkid' output does.

Reboot and you have a swap partition. 2Gb /swap is fine or same as your installed RAM if you hibernate. Good luck.

---

### Post by monkeybrain20122 on 2014-02-19
Aside from fstab there is another file you should check.
```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```
It may be empty or in it there is a single line like "RESUME=UUID=XXXXXXXX"
make sure the xxxxxx matches the uuid for swap in fstab and blkid, if it already has something but doesn't match the uuid in fstab swap will not be on after reboot.

---

### Post by beelzebufo on 2014-02-20
great, thank you all so much, getting the project started right now, hopefully all will end well, although I am prepared for a long, arduous journey.

---

### Post by Bucky Ball on 2014-02-20
I did this not less that a week ago (moved the /swap to another drive entirely, actually) and didn't take long at all. Follow those instructions I gave and shouldn't take you too long either. ;)

PS: Before tweaking your /etc/fstab file, might be an idea to back it up:

```
sudo cp /etc/fstab /etc/fstab.backup
```

To copy back the original if things go pear-shaped:

```
sudo mv /etc/fstab.backup /etc/fstab
```

Should have mentioned that earlier, sorry.

---

### Post by beelzebufo on 2014-02-20
thank you so much bucky ball and monkybrain, however, I did what both of you said, and after a reboot, my open system monitor is saying 0.0 kb swap, not sure what went wrong, but I followed both of your statements to a tee, using my own output from "sudo blkid" I don't have much load on my system as I test now, but it seems like my swap should have some load on it even as it sits idle... The reason I am so concerned is that I know that linux needs swap to function properly, I have run into this problem before.  Anyway, any new ideas would be greatly appreciated.  

thanks again
beelze

---

### Post by sudodus on 2014-02-20
Please post the output of the command

```
swapon -s
```

---

### Post by beelzebufo on 2014-02-20
here ya go, looks like it recognizes the swap, but it's not being used, maybe I am just being paranoid.

```
wreckingball@wreckingball-pc:~$ swapon -s Filename                Type        Size    Used    Priority
/dev/mapper/cryptswap1                  partition    8103932    0    -1



```

the code didn't go right, but you can see that the partition is 810k and used is 0.. not sure what's a happinin.

---

### Post by sudodus on 2014-02-20
You have 8 GB cryptswap but don't use any of it (yet)
:-)

---

### Post by beelzebufo on 2014-02-20
ok, so it's just not in use is all?  wow, super noob here lol

edit: how can I test that? I mean sort of stress test my swap.. if that's even possible.

---

### Post by sudodus on 2014-02-20
```

Filename                               Type              Size        Used    Priority
/dev/mapper/cryptswap1                 partition         8103932     0       -1

```
You have 8 GB cryptswap but don't use any of it (yet)
:-)

Edit: fixed the columns to make the swapon output easier to read

---

### Post by beelzebufo on 2014-02-20
do I need to change that priority level? being that it's -1 I feel like it will only be used as a last resort..  I know nothing about swap space if you couldn't tell.

---

### Post by sudodus on 2014-02-20
> **beelzebufo said:**
> ok, so it's just not in use is all?  wow, super noob here lol

edit: how can I test that? I mean sort of stress test my swap.. if that's even possible.

Edit some really huge picture (or create a huge picture from a smaller one) with ***gimp***.

---

### Post by sudodus on 2014-02-20
> **beelzebufo said:**
> do I need to change that priority level? being that it's -1 I feel like it will only be used as a last resort..  I know nothing about swap space if you couldn't tell.

It is OK. Swapping *is* the last resort, when RAM is not big enough. Swapping makes things slow, and is nothing you want, unless necessary.

---

### Post by sudodus on 2014-02-20
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

This link will give you more information about swapping

---

### Post by beelzebufo on 2014-02-20
Thank you all so much, I will mark this solved as of now, great thread, much obliged.

---

### Post by sudodus on 2014-02-20
You are welcome :-)

---

### Post by Bucky Ball on 2014-02-20
Great news, glad it worked. 

One really easy way of checking if the new swap partition is recognised is, immediately after booting, open Gparted and right click on the /swap partition. If the option is 'swapoff', then swap is on and recognised and working at boot! If the option is 'swapon', then it is off and not recognised at boot. ;)

Enjoy, glad we could be of help and glad it all worked out in the end. ;)

---

### Post by beelzebufo on 2014-02-20
uh oh, it appears all is not well.  I just opened gparted for a different project and the swap partition I just created last night isn't formatted anymore... according to gparted it is unknown with a big red exclamation mark.  I will poke around a bit and try to figure out whats' going on.

---

### Post by beelzebufo on 2014-02-20
yeah, it won't stay formatted for some reason. I must have done my /etc/fstab wrong.  After reboot from the live cd the swap was there, but not in use (swapon option was on it in gparted)  So I went and edited the fstab file, then rebooted again, and came back to a blank (unformatted) swap space.. strange.  

I still get this though... 


```
wreckingball@wreckingball-pc:~$ swapon -s
Filename				Type		Size	Used	Priority
/dev/mapper/cryptswap1                  partition	8103932	0	-1



```

---

### Post by sudodus on 2014-02-20
You have encrypted home, and then you get encrypted swap automatically. It is not recognized by gparted, but *swapon seems happy*, and I think it is OK.

---

### Post by beelzebufo on 2014-02-20
ok, thank you very much sudodus.  I will just leave it alone then, remarking solved, thanks again.

---

### Post by Bucky Ball on 2014-02-20
But hang on ... if it is saying 'swapon' then it is off. That is not good. You want it to say 'swapoff' ...

---

