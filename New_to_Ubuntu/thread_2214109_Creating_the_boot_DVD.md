---
title: "Creating the boot DVD"
date: 2014-03-30
forum: New to Ubuntu
---

### Post by RussellXPD on 2014-03-30
I've persuaded my son to switch to Ubuntu 12.04, same as me. I'm doing well with it. (I can't recommend anything else because it's my only experience of a successful OS.)

I created my own first bootable DVD two months ago and now I've created another, using Win 7's standard disc burning facility.  Trouble is, this one doesn't work. 

The good one has 740,032,512 bytes (705 Mb)
The copy on the HDD was 739,313,063
The new, dud, one has 800,030,720 (792 Mb)

I realise this is a generalised issue but perhaps someone may have experienced this glitch already.
Any thoughts please?

Russell

---

### Post by pqwoerituytrueiwoq on 2014-03-30
burning a .iso file to a disk is not the same as burning a image
windows 7 does have a image burner but is not not that efficient, i always use infrarecorder to do it on windows
[http://infrarecorder.org/?page_id=5](http://infrarecorder.org/?page_id=5) - full install of infrarecorder
[http://portableapps.com/apps/utilities/infrarecorder_portable](http://portableapps.com/apps/utilities/infrarecorder_portable) - portable version of infrarecorder
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) - make a bootable usb flash drive (use a 1gb flash drive or larger)
you may want to consider 14.04 beta and save on upgrade times as it will replace 12.04 in about 2 weeks as the new LTS

---

### Post by sudodus on 2014-03-30
Did you start from the same or a new iso file?

If a new iso file, check with ***md5sum*** that the download was successful. See this link

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Did you burn in the same way - burn an ISO file to a DVD? You should see a lot of files and directories, when you mount the DVD disk into the drive. If you see one file (the iso file) you have created a data-DVD, which is wrong, the computer will not boot from it.

You can also try to burn a new DVD, this time with the lowest possible burning speed.

-o-

By the way, if the computers are not too old (less than 10 years old), you can probably make a USB boot drive and boot your son's computer from it. I think it is simpler and also more reliable to boot from USB drives nowadays. It is usually easy to use ***Unetbootin*** to create a USB boot drive from the iso file.

[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

You can also use the shellscript ***mkusb***

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

Get more details from this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by RussellXPD on 2014-03-30
Thanks pqw

I'll follow those suggestions tomorrow am. I thought I was doing it right, and the same way. I'll have to assume I didn't. 

The original computer told me I'd burned the DVD and showed its new name, but on my return it said it still had an iso file waiting.
Another computer told me the burned disc was raw and didn't show the name.
 

I know there's a strong pressure to switch to 14.04 but surely the most important thing for a newbie is to get started and build up their confidence?
Also I'll check out if he has a boot from USB option. 

Thanks also Sudodus

**md5sum** is first call. I'd forgotten its name.  **unetbootin** worked for me first time so I'll check that out too. And my son's computer probably can boot from USB.
I'll try all the options and let you know how it went.
Thanks to both.

---

### Post by monkeybrain20122 on 2014-03-30
Forget about burning dvds if you computer can boot from usb. DVDs are so last century. :) Use something like unetbootin to make a live usb, it is much faster than the dvd and easy to make.

---

### Post by pqwoerituytrueiwoq on 2014-03-30
> **monkeybrain20122 said:**
> Forget about burning dvds if you computer can boot from usb. DVDs are so last century. :) Use something like unetbootin to make a live usb, it is much faster than the dvd and easy to make.
i don't think dvds existed 100 years ago, you mean decade

---

### Post by RussellXPD on 2014-03-31
Okay ... I've had a bad day. Approx 6 hours wasted with Win7's Disk Burning utility and an old Nero program. You get them sometimes.

So I've downloaded InfraRecorder. Could I have a bit of help? (I'm in XP for this.)  It's a case of understanding the terms, doing things in the right sequence.

I've focused on Copy Disc because I've got a working DVD-RW (12.04) that I would like to clone. The Copy Disc window shows D drive as the Source and the Target. Clone disc is ticked.
Write speed is defaulted as Maximum. Two points here: I don't want to wreck the existing disc so why does it pick on write speed, not read speed. and wouldn't it be better to run slower?
 
Am I going to be okay if I press ahead at this point, putting in source then target as directed?

The extra reason I'm asking, I've wrecked two discs already. Thanks Win Disc Utility.

Russell

---

### Post by sudodus on 2014-03-31
I have no experience with InfraRecorder. Let us hope someone who has experience with it will chip in and help you.

But do I understand correctly, that you are running Ubuntu in one computer? In that case you can install ***k3b***, which is an excellent burning program.  I use it and I think many others here at the Ubuntu Forums. So you can get good guidance how to use k3b.

---

### Post by RussellXPD on 2014-03-31
Thanks Sudodus

I hadn't picked up on **k3b**. I'll try that next if InfraRecorder doesn't come good.
(For years I avoided writing CDs and DVDs and lack the experience I could have had.)

---

### Post by RussellXPD on 2014-04-02
Had problems with the other DVD burners.

I've downloaded **k3b** aiming to create a bootable Ubuntu 12.04. I've also downloaded the k3b manual but have two problems;
I'm not sure of the terms, and the manual images don't match the images served by **k3b**.

I've burned the contents of a working 12.04 bootable DVD via the hard drive (working in Ubuntu) onto an empty DVD-RW.

This is what I did: folder named Ubuntu placed on the hard drive with 8 folders (Casper the main size) and 5 files, total 739 Mb.

Start k3b. Burn Image - k3b window shows up. Put bootable source  disc in drive. Double click on image to burn. Ubuntu 12.04 name appears in panel.  It appears to be ready to burn to disc. I don't want this written over so I take it out and replace it with the target disc. It asks to put in the files to burn. I try to put in the 13 directories and files mentioned above but it says these aren't valid. So I put in the parent folder of these called Ubuntu and this works.
The burn process starts.

SERIOUS EDIT OF THE POST
k3b tells me that the files have been put onto the target DVD. That appeared to be right. When I check later, a blank disc is shown with today's date. Didn't work!

The problem as I see it: When I start k3b I can't see the correct sequence when I reach the Burn Image page. I'd be grateful for a push or a shove!

---

### Post by sudodus on 2014-04-02
I think the most straight-forward way is like this:

0. Download an Ubuntu desktop iso file and check the md5sum (or let k3b show it and check it) with the listed value at

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

1. Open a terminal window

2. Change directory to where you have your Ubuntu desktop iso file, for example

```
cd Downloads
```

3. start ***k3b*** with the iso file as parameter. Then it will automatically start in the correct mode (to burn an image instead of making a data DVD)

```
k3b ubuntu-12.04.4-desktop-amd64.iso
```

See the attached file.

4. Insert a DVD disk (because this iso file is oversized for CD)

5. and the Start button with get active.

6. Click on the Speed button and select the slowest speed that is available for your burner.

7. Start burning with the Start button

--

It makes it more complicated to start from another disk, but it is certainly possible. You can probably either clone the disk (copy disk to disk) or first make an iso file, and then use the instruction above to make a boot disk from the iso file.

---

### Post by mike-ransier on 2014-04-09
Hello,

The steps I used for success was I downloaded the .iso and installed Active ISO Burner.  (I did this using XP.) Once the software is installed if you open the download folder and right click on the .iso file you need to burn. Allow me to back up here. If the file is over the 700mb I use a DVD either way I open the cd/dvd/blue ray and place the media in the tray FIRST. Then right click on the file. The selection to burn the .iso file will appear. Choose this method. Once done if your unsure you can check the checksum but this is the easiest and slickest way on any .iso burn I have found.

Good Luck!


(The Greatest Thrill In Life Is The Anticipation Of The WAIT !!! ).

---

### Post by Coolgirl on 2014-04-09
Ive you have a burner, windows seven has a boot disk creation tools from theyre website.. that what I used and it worked like a charm

---

