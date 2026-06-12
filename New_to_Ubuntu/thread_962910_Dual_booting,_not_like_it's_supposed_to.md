---
title: "Dual booting, not like it's supposed to?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by daxonsale on 2008-10-29
I've been using Hardy for a month or so now and loving it. However a change in circumstances require me to access Windows occasionally, so dual booting is what I've been trying, however, the tutorials I'm finding aren't matching what I'm getting on screen.

I installed Windows (XP) first, wiping out my Hardy installation (yes, I backed my data up), then I rebooted with Hardy, either the disk or I have it on thumb drive. When I get to the partition manager however, I only get three options. Full guided, which I'm assuming will wipe out the Windows installation, the second one where it will use all available free space other than Windows, and manual.

Obviously if the first wipes out Windows it defeats my purpose. When I choose the second, it tells me that space is too small, which confuses me as it's a 160Gb drive with just a bare bones XP install on there. As for manual, it would be as well written in ancient Greek as far as my understanding goes.

Can anyone offer some advice please?

---

### Post by SuperSonic4 on 2008-10-29
Use the second one then?

First: Wipes XP
Second: Uses what's on the disc **that is not used** by XP
Third: DIY :p

Go into manual and post a screenshot. Did you make a partition for XP or let it use the whole disk?

---

### Post by randy78 on 2008-10-29
1. Pop in a live cd (or usb drive), go to System>Administraton>Partition Editor

2. Resize Windows partiton manually (should say NTFS under filesystem, right click that and select Resize/Move) This might take quite a while, so be patient.
This will leave you with some unformatted space on your drive.
Go ahead and right click the unformatted space, select New, choose EXT3 and then OK and Apply (Primary).

3. Click the Install icon on the Desktop, going through all the steps and choose Manual install.

4. Select the new partition (the windows partition should be sda1, so you should choose sda2), if a dialog comes up about where to install root to, select "/".

5. Since you have already formatted the EXT3 partition, you don't have to check the "Format" box.

6. Click Ok (or forward, I can't remember right now...), and confirm the changes... it will auto-detect your Windows install and ask you if you want to import any shared documents, etc...

7. Finalize the install and reboot, remembering to remove the CD from the drive and enjoy :)

---

### Post by daxonsale on 2008-10-30
Thanks for the advice guys. I followed the step by step guide and it all went well until I got into the partition editor. I saw the Windows partition fine but the editor will only allow me to change the size by a few Mb and I'm not sure why. I made a [screenshot]("http://www.flickr.com/photos/31901716@N02/") to see if that throws any light on things.

---

### Post by hyper_ch on 2008-10-30
can't you set a dfiferent "New Size" in there?

---

### Post by karlsomewhat14 on 2008-10-30
I've never been able to repartition an ntfs filesystem from Ubuntu.
To resize my windows partition this weekend, I ended up having to boot into Windows and installing the EASEUS partition editor for Windows.

Alternately, you could install Ubuntu over Windows, use gParted to resize the Ubuntu partition to where you want it, and install XP in the extra space afterward.

---

### Post by daxonsale on 2008-10-30
Okay, I'm making progress, kind of, sort of, a bit anyways. I downloaded, installed and ran Easeus. At first it said it couldn't complete the process because of my "special condition" in NTFS ????? Anyway, I did the full Windows reinstall again, only this time, I chose the quick reformat option. That went fine. I then reinstalled Easeus and ran it and this time it did what I wanted it to do, Windows on 50 Gb leaving 100 Gb for Ubuntu. So I started that install (Hardy by the way), and that went fine too. After the reboot, there was Grub offering me either OS. I can get into Windows just fine, however, when I chose Ubuntu, I get to the login screen, punch in my ID and password, I get an orange screen for a second or two, then a black screen, then back to the login screen

I know for a fact that I'm punching in the correct details, they're the same ones I've always used with Ubuntu. I even see my name at the bottom of the login screen.

Any thoughts?

---

### Post by hyper_ch on 2008-10-30
username is normally just small letters and the password is case-sensitive

---

### Post by oldos2er on 2008-10-30
"there was Grub offering me either OS. I can get into Windows just fine, however, when I chose Ubuntu, I get to the login screen, punch in my ID and password, I get an orange screen for a second or two, then a black screen, then back to the login screen"

 Could be a video driver problem. Which make/model video card do you have?

---

### Post by randy78 on 2008-10-30
I agree with oldos2er... it sounds like a video issue.

Boot into a live CD, fire up a terminal and type:
lspci

that will give us more info on your hardware

:D

---

