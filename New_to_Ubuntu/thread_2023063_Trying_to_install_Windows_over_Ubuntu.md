---
title: "Trying to install Windows over Ubuntu"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by HippoCrit on 2012-07-11
I'm a bit of a newbie when it comes to Linux and Ubuntu but a while ago I installed Ubuntu onto my laptop, removing Windows and making it the only Operating System on the computer. It's working fine but I now I want to re-install Windows 7 onto my laptop. Whenever I try to install Windows off the disk onto the computer, all I get is a black screen with a line (Like this _ ). When I remove the disk it then goes straight to Ubuntu. I have used GParted to create a NTFS partition for Windows. I preferably want to keep Ubuntu on the laptop and also have Windows, but if that's not going to be able to be done I will do whatever I have to do to get Windows back onto it.

EDIT: I just realized my Thread's title is a bit messed up. I meant to say: Trying to install Windows over Ubuntu.

---

### Post by Shadius on 2012-07-11
Have you set the BIOS to boot from CD-ROM first?

---

### Post by HippoCrit on 2012-07-11
In my BIOS it boots in this priority:

1. CD/DVD
2. Hard Drive
3. Removable Device

---

### Post by Shadius on 2012-07-11
That's correct, and it still loads with a blank screen and the underscore?

---

### Post by HippoCrit on 2012-07-11
Yeah, it boots up the blank screen with the underscore. After I remove the disk it boots normally, straight into Ubuntu. I know it's not the disk drive, that's how I got my partition (GParted LiveCD)

---

### Post by Shadius on 2012-07-11
Have you checked the CD to make sure nothing is wrong with it? You could try to see if there is anything on it by using Ubuntu.

---

### Post by HippoCrit on 2012-07-11
Now that I'm looking at the disk, it seems to have a few minor scratches. I checked the disk on my other computer (already running Windows 7) and it shows that it's a Windows Install disk, then when I try to install on the laptop it comes up with the blank screen. Do you think that the scratches could causing the problem? Because they are quite small.

---

### Post by Shadius on 2012-07-11
> **HippoCrit said:**
> Now that I'm looking at the disk, it seems to have a few minor scratches. I checked the disk on my other computer (already running Windows 7) and it shows that it's a Windows Install disk, then when I try to install on the laptop it comes up with the blank screen. Do you think that the scratches could causing the problem? Because they are quite small.

If it can be read on the other computer, I don't think the scratches matter. Are you able to boot into an Ubuntu LiveCD?

---

### Post by HippoCrit on 2012-07-11
I haven't booted into a Ubuntu LiveCD but as I said before, I did a GParted LiveCD so I could organize my partitions (And GParted LiveCD seems to be a basic form of Debian). So, should I boot into a Ubuntu LiveCD or is that just a DVD Drive test?

---

### Post by lisati on 2012-07-11
Based on my reading of the first post: are you trying to install Windows over Ubuntu?

---

### Post by HippoCrit on 2012-07-11
> **lisati said:**
> Based on my reading of the first post: are you trying to install Windows over Ubuntu?
Yes, I am trying to install Windows over Ubuntu. I just accidentally stuffed up the title when I was posting this thread, and it won't let me change the title :/

---

### Post by Shadius on 2012-07-11
> **HippoCrit said:**
> I haven't booted into a Ubuntu LiveCD but as I said before, I did a GParted LiveCD so I could organize my partitions (And GParted LiveCD seems to be a basic form of Debian). So, should I boot into a Ubuntu LiveCD or is that just a DVD Drive test?

Yeah, it was just a CD/DVD drive test. Since you were able to boot into GParted LiveCD, there's no need to boot into an Ubuntu LiveCD. It seems your CD/DVD drive is working fine, but I can't come up with any reason why your Windows installation CD isn't booting up properly. ](*,)

---

### Post by lisati on 2012-07-11
> **HippoCrit said:**
> Yes, I am trying to install Windows over Ubuntu. I just accidentally stuffed up the title when I was posting this thread, and it won't let me change the title :/

I've edited the thread title for you.

---

### Post by HippoCrit on 2012-07-11
I've been reading other threads on other forums, and it somewhere it said that they should remove the boot flag from the NTFS partition. I'm not sure if mine has the boot flag, should I found out if it does, and if it does should I remove it?

---

### Post by HippoCrit on 2012-07-11
> **lisati said:**
> I've edited the thread title for you.
Thanks :D

---

### Post by Shadius on 2012-07-11
> **HippoCrit said:**
> I've been reading other threads on other forums, and it somewhere it said that they should remove the boot flag from the NTFS partition. I'm not sure if mine has the boot flag, should I found out if it does, and if it does should I remove it?

You could probably remove it if it was set because installing the Windows will probably put it back when the MBR is installed. I'm not sure if you can check it by using GParted.

---

### Post by Shadius on 2012-07-11
I just checked the [GParted Manual]("http://gparted.sourceforge.net/display-doc.php?name=help-manual") and learned that you can manage boot flags. I don't know if that'll solve the issue, but I suppose it's worth a try.

---

### Post by HippoCrit on 2012-07-11
Alright, I opened GParted (Not LiveCD though) and it says that my NTFS partition did have the boot flag. I just removed it then, do you think that'd be enough to get the Windows Install Disk working?

---

### Post by Shadius on 2012-07-11
> **HippoCrit said:**
> Alright, I opened GParted (Not LiveCD though) and it says that my NTFS partition did have the boot flag. I just removed it then, do you think that'd be enough to get the Windows Install Disk working?

Try booting into the Windows install disk now.

---

### Post by oldfred on 2012-07-12
Is the NTFS partition a primary partition? or sda1 thru sda4? 

And you need the boot flag on the NTFS primary partition as Windows sees that as the active partition so it knows that is the one to use to boot, or install into.

Also is CD a full XP install and not one of the upgrade CDs?

---

### Post by HippoCrit on 2012-07-12
> **oldfred said:**
> Is the NTFS partition a primary partition? or sda1 thru sda4? 

And you need the boot flag on the NTFS primary partition as Windows sees that as the active partition so it knows that is the one to use to boot, or install into.

Also is CD a full XP install and not one of the upgrade CDs?
How do I find out if it's a primary partition? Also, it's a full install Windows 7 disk, not an upgrade one.

EDIT: It's sda3

---

### Post by HippoCrit on 2012-07-12
Alright, so it's sda 3. What am I supposed to do now?

---

### Post by oldfred on 2012-07-12
You should be able to format to NTFS and set boot flag. Some with Windows 7 said they had to use the Windows to reformat again to NTFS.

There is a difference in NTFS formats. The partition boot sector (PBR) specifies which boot loader to use. So boot flag will tell the Windows boot loader to look for ntldr for XP in the PBR or for bootmgr if Vista or 7. So that may be why you have to reformat from 7?

---

### Post by HippoCrit on 2012-09-03
God it's been a while since I've been trying to this, because I basically gave up.

Anyhow, I thought maybe I could try installing Mint, so I downloaded it and tried burning it to a disk on my Laptop. When I went to burn it to the disk, after Brasero finished doing it's 'checksum' came up with this error.

"**Error While Burning**.
SCSI error on write(0,16): [3 73 03] Power calibration area error"

Also, I tried installing Windows again recently, it didn't work (Same Problem as before) but when I loaded Ubuntu, I could hear the DVD drive trying to read the Disk but nothing would appear.

Finally, I think it may be of some relevance, my Laptop's built-in monitor broke a while ago so I have been using an external one (Including during my previous install attempts). 

Do you think any of this could have anything to do with my errors with installing Windows?

---

### Post by Bartender on 2012-09-03
Hippo, I'm surprised nobody mentioned this.  A Windows install CD won't know what to do with a drive that's not NTFS.  You just want to get the lappy back to Windows, right?  Not a dual-boot?

Pop that GParted CD back in and delete all partitions.  One odd thing you'll run into with the GParted CD - you can delete data partitions by right-clicking on the "map" near the top of the window.  If you have an extended partition, right-click on the text in the lower half of the window that describes the extended partition (sda5 or what have you) to delete it.

Don't forget to Apply at each step!! It's a mistake to keep adding tasks to GParted, then Apply all at once.

When you've wiped every partition and have one big block of unallocated, right-click on the map and create one primary partition ***formatted as ntfs***.

Apply that task, then get out of GParted and pop that Windows disc in.  If you still can't make any progress, then there's some sort of hardware problem.  The optical drive, a bad Windows disc, etc.

EDIT: I've installed Ubuntu (or Mint) to dozens of old PC's and have run into a couple of optical drives that just don't seem to work reliably with Brasero.  I could swap the optical drive out for another one and Brasero would seem to work much better.  I've also had Brasero report odd errors such as you describe, but the disc seemed to work OK.  If you don't have access to a few different computers and/or optical drives, it can be hard to figure out the root cause.

EDIT II: No, I can't imagine any way that using an external monitor would affect the described problems.

---

### Post by SeijiSensei on 2012-09-03
Another alternative you might consider is installing [VirtualBox]("http://www.virtualbox.org/") within Ubuntu.  It gives you the ability to create "virtual machines" into which you can then install another operating system.  I run Win7 inside a VirtualBox VM for those few occasions when I need Windows.  

VB has nice features for sharing the display among machines.  You can run Windows within a window on the Ubuntu desktop, run it full-screen, or have it share the desktop with Linux.  It's far and away a better solution than dual-booting unless you want to play PC games.  They usually need to write directly to the graphics hardware and have trouble with the emulated graphics hardware that the virtual machine supplies.

---

