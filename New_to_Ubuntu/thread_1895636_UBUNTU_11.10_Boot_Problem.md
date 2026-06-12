---
title: "UBUNTU 11.10 Boot Problem"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by adithya25 on 2011-12-15
hi guys,
I'm trying to install Ubuntu 11.10 to my pc which has a hardware specification of 2 gb RAM 160 gb hard drive and a graphic card of 256 mb.

The pendrive which I'm using is a Transcend 8 gb.

I'm using UNetbootin to make a bootable flash drive.

I've downloaded this file frm the Ubuntu website, "ubuntu-11.10-desktop-i386.iso."
My pc is a 32 bit desktop computer and I'm selecting the disk image to do the process. After it is completed, it asks to restart, which I do, But the problem is tat its not booting and I've changed my boot settings to boot frm USB too.
So wht mistake am I doing?
Help out guys!

---

### Post by lukeiamyourfather on 2011-12-15
Can you elaborate? Are you trying to install Ubuntu from a USB drive and it doesn't boot from the USB drive, or are you installing Ubuntu to the USB drive to boot from permanently?

---

### Post by adithya25 on 2011-12-15
> **lukeiamyourfather said:**
> Can you elaborate? Are you trying to install Ubuntu from a USB drive and it doesn't boot from the USB drive, or are you installing Ubuntu to the USB drive to boot from permanently?

I'm trying to install Ubuntu from a USB drive to my System and it doesn't boot from the USB drive.

---

### Post by Sigma1 on 2011-12-15
You have to configure the BIOS to boot from a USB drive in the boot options. Older machines might not allow this, though.

---

### Post by lukeiamyourfather on 2011-12-15
> **adithya25 said:**
> I'm trying to install Ubuntu from a USB drive to my System and it doesn't boot from the USB drive.

What Sigma1 said, check your motherboard manual to see if it can boot from USB if you're not sure. If that doesn't work then just burning a CD would probably be the best option.

---

### Post by Mark Phelps on 2011-12-15
Once again, it looks like folks responding to your question aren't bothering to actually read what you wrote ...

> But the problem is tat its not booting and I've changed my boot settings to boot frm USB too.

So, telling you to set your BIOS to boot from USB is kinda pointless ... since you've already done it.

Since you used unetbootin, that is the correct tool.  

You could try booting the USB on some other PC -- just to see if it boots OK.

Also, I read a post a while back where folks said that they could not get Transcend USB sticks to boot -- but that other brands were OK.  Hate to say it, but you might have to fork out money for a different brand USB stick to get this to work.

---

### Post by rng on 2011-12-15
Sometimes, in bios menu, you have to select hard disk and a submenu will appear which will have usb as well as the hard disk to boot from. Choose usb here and it may boot.

---

### Post by niteman on 2011-12-15
To the OP, I can tell you that I'm one of the folks that has had a tough time getting transcend sticks to work, especially larger capacity ones. If you have another usb stick lying around, say 2 gigs or so, try that one. Format the stick to FAT and then use unetbootin to make the bootable stick. This has worked for me in the past. Unetbootin is pretty reliable, it's usually the usb stick. Hope that helps.

---

### Post by Chaz46 on 2011-12-15
Could be a number of reasons as to why it isn't working. It could be that your computer isn't capable of booting from a USB, but you say that you have selected that in your BIOS so that would suggest that it was, how old is the computer?

The other thing to try, as others have suggest, is change the usb stick. Sometimes the manufacturer can have a big effect on it, I used a Kingston and that had no problems.

If still no luck I would recommend pendrivelinux to create the bootable USB.

---

### Post by lukeiamyourfather on 2011-12-16
> **Mark Phelps said:**
> Once again, it looks like folks responding to your question aren't bothering to actually read what you wrote ...

That solves everything. :-({|=

---

### Post by usorted on 2011-12-16
My desktop would not boot from USB also. I eventually found on here somewhere that for some computers the usb stick needs to be formated to FAT 16 first,  NOT FAT32. 

I used the windows facility to format it to FAT16 then ran the process again to make it bootable making sure to not tick the format option because I think the unetbootin formats it to FAT32.

It then booted my machine like lightning. Hope this helps you.

---

### Post by adithya25 on 2011-12-16
> **usorted said:**
> My desktop would not boot from USB also. I eventually found on here somewhere that for some computers the usb stick needs to be formated to FAT 16 first,  NOT FAT32. 

I used the windows facility to format it to FAT16 then ran the process again to make it bootable making sure to not tick the format option because I think the unetbootin formats it to FAT32.

It then booted my machine like lightning. Hope this helps you.

I dont have an option to format it to fat 16.....
how do I do it?

---

### Post by rng on 2011-12-17
Easiest is to use gparted program from linux.

---

### Post by Paddy Landau on 2011-12-17
If your computer is a more modern one, it may have the new UEFI facility. A number of people -- me included -- have found that 11.10 and 12.04 (alpha) handle this poorly, even if the UEFI is disabled.

What happens if you try [version 11.04]("http://releases.ubuntu.com/natty/") instead -- can you boot from the USB?

---

### Post by amjjawad on 2011-12-17
Assuming you have checked MD5SUM for the file you downloaded:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

And assuming you are using [UNetbootin]("http://unetbootin.sourceforge.net/") correctly ... also assuming the problem is NOT with your USB Drive, no harm to check these:

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]


[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]


However, Note That BIOS could be different from one PC/Laptop to another but the concept should be the same.

As Mark suggested, best to try on different machine, at least to make sure there is NOTHING wrong with your USB Drive.

As for how to format your USB, best way is GParted. Not sure whether you have a Linux Machine or Windows Machine? from where you are trying to create that USB? Windows or Linux?

---

### Post by adithya25 on 2011-12-19
> **Paddy Landau said:**
> If your computer is a more modern one, it may have the new UEFI facility. A number of people -- me included -- have found that 11.10 and 12.04 (alpha) handle this poorly, even if the UEFI is disabled.

What happens if you try [version 11.04]("http://releases.ubuntu.com/natty/") instead -- can you boot from the USB?

wel, the last version which I used was 10.04.... I got the cd for free back then and it wasnt much of a prob to install it back then....
this is the 1st time I'm trying to install through USB..... I tried burning 11.10 to cd too.... similar problems.... so I thought USB to b the best option since I've already wasted quite a few cd's burning....

---

### Post by adithya25 on 2011-12-19
> **amjjawad said:**
> Assuming you have checked MD5SUM for the file you downloaded:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

And assuming you are using [UNetbootin]("http://unetbootin.sourceforge.net/") correctly ... also assuming the problem is NOT with your USB Drive, no harm to check these:

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]


[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7191[/IMG]


However, Note That BIOS could be different from one PC/Laptop to another but the concept should be the same.

As Mark suggested, best to try on different machine, at least to make sure there is NOTHING wrong with your USB Drive.

As for how to format your USB, best way is GParted. Not sure whether you have a Linux Machine or Windows Machine? from where you are trying to create that USB? Windows or Linux?

wel, the download file and unetbootin part r all ok.... no problems in those....
I'll check the boot settings again since u asked me to... and GParted and the checking part in another machine, I'll try and get back to u as soon as I can..... Lets c....

---

### Post by adithya25 on 2011-12-19
I'm formatting it through windows..... and till now I haven used Gparted.... so I guess Gparted and FAT16 r my last options...... lets c.....

---

### Post by MartijnNL on 2011-12-19
I have formatted USB sticks for unetbootin using this windows tool, tends to work fine:
[http://download.cnet.com/HP-USB-Disk-Storage-Format-Tool/3000-2094_4-10974082.html](http://download.cnet.com/HP-USB-Disk-Storage-Format-Tool/3000-2094_4-10974082.html)

---

### Post by amjjawad on 2011-12-21
> **adithya25 said:**
> I'm formatting it through windows..... and till now I haven used Gparted.... so I guess Gparted and FAT16 r my last options...... lets c.....

When formatting in Windows, make sure to use FAT not NTFS.

Waiting for your update :)

---

### Post by Paddy Landau on 2011-12-21
> **amjjawad said:**
> When formatting in Windows, make sure to use FAT not NTFS.
Good point. I have also read that FAT16 on a USB works more reliably than FAT32.

---

### Post by adithya25 on 2011-12-23
Every1.... Thank u for ur help.....

PROBLEM SOLVED!!!!!

wht I did......

I used to format my USB through windows xp.... but it dint work..... so as "[MartijnNL]("http://ubuntuforums.org/member.php?u=466404")" suggested, I used
this tool to format my USB..... [http://download.cnet.com/HP-USB-Disk...-10974082.html]("http://download.cnet.com/HP-USB-Disk-Storage-Format-Tool/3000-2094_4-10974082.html") 

after tat used UNetbootin for creating a bootable device.....

next steps r pretty normal.... jus finished installing.......

THANK U EVERY! FOR THE HELP!

ITS WORKING and its COOOOOOL!!

---

### Post by adithya25 on 2011-12-23
oh and I dint use FAT16 or Gparted...... it wasnt necessary...... but I'll remember all these things....... thnx for all the other suggestions..... 

and as "[amjjawad]("http://ubuntuforums.org/member.php?u=941822")" suggested, for ppl who'll look into this post in the future, re-look into the boot menu too........

---

### Post by amjjawad on 2011-12-23
Well done :)
Glad you managed to install ... ENJOY :D

Thanks for marking this thread as SOLVED.

Nothing is better than learning this way because you will never forget that ;)

---

### Post by rng on 2011-12-23
@adithya25:
> oh and I dint use FAT16
What format did you use for formatting- FAT32 or NTFS?

---

### Post by adithya25 on 2011-12-23
> **rng said:**
> @adithya25:

What format did you use for formatting- fat32 or ntfs?

fat32

---

### Post by adithya25 on 2011-12-23
> **amjjawad said:**
> Well done :)
Glad you managed to install ... ENJOY :D

Thanks for marking this thread as SOLVED.

Nothing is better than learning this way because you will never forget that ;)

Yaaa.... definitely I wont forget.....

oh and if u've any boot prob in the future, u can contact me..... hehe....
(jus kidding.....)

thnx for the help.!

---

### Post by amjjawad on 2011-12-24
> **adithya25 said:**
> oh and if u've any boot prob in the future, u can contact me..... hehe....
(jus kidding.....)
You'll be there in no time if you want that and it's not really hard to achieve that. Most of us have started here with no real experience and the more problems we come across, the more experience we learn, not to mention if you are that type of users who do tests and like to try new stuff, etc ... that will add even more experience. This is how I learned Linux. I was active here + I do lots of tests.

If you need anything, feel free to contact me. Oh, check my signature, you may find some useful information over there :) 

> thnx for the help.!
I did nothing special but you most welcome :)

---

