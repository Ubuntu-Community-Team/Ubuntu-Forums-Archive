---
title: "PC doesn't boot"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Settler on 2008-10-03
Hi all,

i have just installed ubuntu on other pc and as restart now button was clicked and cd was ejected, system rebooted...
Pc then stops at...

Checking Up CMOS OK!

and then nothing...

any advice?..

---

### Post by Vendettaseve on 2008-10-03
Not really sure mate. Mine had a similar problem (ALtho I could not install at all)
Have you checked your ram? It turned out that mine had burnt out for whatever reason and I was running on something like 40mb of ram lol, that will deffinitly toss a wrench into the loading gears.

---

### Post by Sub101 on 2008-10-03
Check that you are booting from your hard drive and not still looking for the CD. 

If thats not it I would suggest a problem with GRUB which may be solved with the Grub disc.

---

### Post by Settler on 2008-10-03
Ram is ok and HDD is the first boot device...
should I be considering to run a new installation?..

---

### Post by Sub101 on 2008-10-03
It might be however lets get some more information first.

How far into boot do we get? Does it enter anything beyond Bios?

---

### Post by inxygnuu on 2008-10-03
It is probably a BIOS or other hardware error. I'm no expert, but I would say that Ubuntu either changed something in the BIOS (or CMOS) and that is causing it to freeze. How far do you get? maybe I can help...:D

---

### Post by Settler on 2008-10-03
no...it enters bios...it passes the disk detection screen...but then....

after checking CMOS and writes OK!

it seems the pc stucks there...

---

### Post by Settler on 2008-10-03
another thing is that I created only 3 partitions (don't know if that helps)

1. / (15GB) - ext3
2. swap (1GB)
3. /home (rest GB)

---

### Post by Sub101 on 2008-10-03
I believe during installation it asks what bootloader you want to use (or something similar). Do you remember what you said here?

---

### Post by Settler on 2008-10-03
of course I remember. I left it as it is...didn't touch it.

---

### Post by handydan918 on 2008-10-03
> **inxygnuu said:**
> It is probably a BIOS or other hardware error. I'm no expert, but I would say that Ubuntu either changed something in the BIOS (or CMOS) and that is causing it to freeze. How far do you get? maybe I can help...:D

Seriously?
The O/S is not going to write to the bios or the cmos...

---

### Post by Sub101 on 2008-10-03
Oh. Well often people don't even read the screen just next next next. But you did which is a help. 

I'm going to assume you only have one hard drive and we aren't trying to use the wrong one so... I would try booting into the Live CD, just to see if it works really. If it works I would again say there is a problem with the Grub and so it is this which needs rectifying.

---

### Post by Settler on 2008-10-03
downloaded again iso. burned another cd and now re installing...I have only one drive which is new so even ton formatted. Hope that linux does it. or not?

---

### Post by inxygnuu on 2008-10-03
Have you installed any new hardware lately, If so, the CMOS records all of your hardware ,and that may be the interference.

If you have not, you can be EXTREMELY CAREFUL and take your computer apart to check for any corruption.

---

### Post by Sub101 on 2008-10-03
> **handydan918 said:**
> Seriously?
The O/S is not going to write to the bios or the cmos...

I thought that was the case however im not sure anymore. After using the OpenSolaris live cd my keyboard stopped and didn't work till I reset the CMOS. I'm not sure if this is due to the OS or purely coincidental but it made me doubt my belief. Or is it just a coincidence?

---

### Post by inxygnuu on 2008-10-03
> **handydan918 said:**
> Seriously?
The O/S is not going to write to the bios or the cmos...
you never know... although I do agree.:guitar:

---

### Post by Urvish on 2008-10-03
Can your PC have dual os ????

If you formatted the other os without linux than also this type of problem comes means your GRUB will be deleted when U format the second OS

---

### Post by Settler on 2008-10-03
> **Urvish said:**
> Can your PC have dual os ????

If you formatted the other os without linux than also this type of problem comes means your GRUB will be deleted when U format the second OS


you think I should try format with windows and then retry it?

---

### Post by inxygnuu on 2008-10-03
> **Urvish said:**
> Can your PC have dual os ????

If you formatted the other os without linux than also this type of problem comes means your GRUB will be deleted when U format the second OS

all (most) computers have dual boot compatibility. And that is true, but I don't think it is his problem.

---

### Post by inxygnuu on 2008-10-03
> **Settler said:**
> you think I should try format with windows and then retry it?

wait, what can you access? I have been dealing with a lot of this lately.](*,)](*,)

---

### Post by Settler on 2008-10-03
i can watch the full install ....then on the first restart is says 

checking CMOS and then nothing

what you want me to access?

---

### Post by Settler on 2008-10-03
i'm trying the guided partitioning...hope it's not that or else directions taken from here are no good :(

---

### Post by Sub101 on 2008-10-03
You said it was a new hard drive? Could it be that your Bios is not recognizing it?

---

### Post by Settler on 2008-10-03
bios does recognize it. the exact model. but every new disk come unformatted may that be the problem?

---

### Post by Sub101 on 2008-10-03
Im not certain but i thought it would be formatted during installation? I might be wrong on that though.

Otherwise you can use Gparted to reformat the drive.

---

### Post by inxygnuu on 2008-10-03
If you can, go to the "command prompt" there, you can uninstall Ubuntu, and then reinstall it, unless you were experiencing these problems before you installed Ubuntu...:-k:-k

Another recommendation would be to press different button combinations to see if you can continue.

---

### Post by Settler on 2008-10-03
how can I go to "command prompt"?..

---

### Post by inxygnuu on 2008-10-03
Nevermind... did the key thing work?

---

### Post by Settler on 2008-10-03
no...jus the control alt delete key combo :P

---

### Post by Settler on 2008-10-03
i'm going to have a new installation and report back soon

---

### Post by inxygnuu on 2008-10-03
how did it go???

---

### Post by Settler on 2008-10-03
with guided partitioning everything works....so the probs are maybe the partitions.

any help?

i want a different partition for "/" and another for "/home"

---

### Post by inxygnuu on 2008-10-03
wait...  can you get onto Ubuntu?

---

### Post by Settler on 2008-10-03
yes i'm now in. everything is ok. apart from my /home directory is under / partition

---

### Post by inxygnuu on 2008-10-03
that is Ubuntu's partition:popcorn:. (Boy do I wish they would just name it C:\:()
What do you want to Change now?

---

### Post by inxygnuu on 2008-10-03
Oh! and was I of any help to you? (I'm still in middle school and i would like to see if anyone older than 18 finds me useful, I am going to be engineering for a career.)

---

### Post by Settler on 2008-10-03
well help is always help...and I'm always thankfull...

now I want to get rid of /home inside / and create a different partition and have it /home

---

### Post by inxygnuu on 2008-10-03
/home is your user file and "/" is the whole C:\ drive (out of what I know of)

---

### Post by Settler on 2008-10-03
i know that. but I want it separate

---

### Post by inxygnuu on 2008-10-03
do you want it on a USB drive or a external hard drive?

---

### Post by Settler on 2008-10-03
if you mean the /home partition i want it on my HDD. I want the / partition to be 15GB

---

