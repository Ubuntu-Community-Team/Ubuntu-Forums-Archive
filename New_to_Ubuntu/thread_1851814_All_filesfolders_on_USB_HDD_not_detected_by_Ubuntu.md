---
title: "All files/folders on USB HDD not detected by Ubuntu"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by FreebirdMike on 2011-09-29
While attempting to do a clean install of Windows, I created a 11.04 live CD to transfer a bunch of files from my Windows partition to a external HDD. Long story short, Vista wouldn't reinstall properly and I decided to permanently install Ubuntu (was very impressed with the features while playing with the live CD). Install went extremely well, with just a few hiccups.
 
One of the hiccups is the external HDD (Seagate Free Agent Flexgo USB). After the install, I mounted the drive with no problems, but Ubuntu can only recognize/detect about 20% of the files and folders (which were all saved to the HDD by Ubuntu). I can unmount the drive and attach it to my Windows laptop and see all the files and folders. I have tried reloading, resetting the view to defaults and showing hidden files in "View" with no change. When I select "Properties", it says 57.5 GB used but Contents only totalling 27.6 GB (bought the drive for this tranfer so was obviously empty with exception of the bits Seagate puts on it, <1GB).
 
All the file san dfolders on my other 2 internal HDDs, which were present before my conversion, are recognized/detected in Ubuntu.
 
Looking for any advice or direction.
 
Thx in advance.

---

### Post by tomski on 2011-09-29
Hi there FreebirdMike.

ok if i am correct Seagate  usb drive come pre-formatted to NTFS & i think this is your problem, that being the ubuntu install appears to be having issue's with it's ntfs driver.
So i suggest as you have a laptop move the files on the usb hdd to that (for now) then re-format the usb drive to FAT32

this way the only issue you (might) face is that files bigger than 4Gb will need to be split into chunks no bigger than 4Gb (use 7zip to archive the bigger files into multi volume archives)

to re-format to FAT32 from vista you should be able to use the right click menu within My Computer after you have copied the files to your laptop then when it is fat32 copy the files back & re-connect to desktop pc.

obviously once you have your files where you want them i would then begin to look at why the ntfs failed for which I'd recommend a few google searches & perhaps a new thread in this forum, also consider re-installing the fuse driver

good luck


**EDIT**

i have just looked at the drive specifications:
 the freeagent goflex drive appear to have encryption features

ARE THE FILES ENCRYPTED?

if so just unencrypt them using the right click >properties menu

---

### Post by FreebirdMike on 2011-09-29
tomski,

Will swap the files this weekend and see how that will go.

[QUOTE=tomski]if so just unencrypt them using the right click >properties menu[/QUOTE]

I don't see anything in Properties indicating encryption, would it be obvious?

---

### Post by mikechant on 2011-09-30
Is there any pattern in which folders/files are displayed?
Can you list the 'missing' items in the terminal with 'ls -al' or 'sudo ls -al'?

---

### Post by FreebirdMike on 2011-10-04
Mikechant,

Yes, the missing files are displayed running "ls -al" in the disk's directory.  So why aren't they showing in the file viewer?  Do I need to reformat or not?

BTW, I did copy the contents to my son's laptop (running Win7) and was going to reformat the removable HDD.  The disk manager system in Win7 would only allow me to select either NTFS or exFAT as a format.  From my little bit of research, it doesn't appear that Ubuntu and exFAT don't play well with each other, correct?  If I have to reformat, what do I go with?

---

### Post by mikechant on 2011-10-05
> Yes, the missing files are displayed running "ls -al" in the disk's directory. So why aren't they showing in the file viewer? Do I need to reformat or not?

I'd say no need to reformat. If the files show up with 'ls -al' then there's nothing wrong with them, it's just a Nautilus (file manager) display issue.
What I think you might have done is set 'show hidden files' for the current folder only (whatever this was). To set it for all files/folders you need to use edit>preferences as per steps 2/3/4 in this article:
[http://linux.about.com/od/ubuntu_doc/a/ubudg10t7.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg10t7.htm)

As for which filesystem is best for you, I'd say if you want to be able to use the drive from Windows and Linux, use NTFS (formatted in Windows); if you're sure you only want to use it in Linux, ext4 is probably best (can only be formatted from Linux), but only if a reformat is convenient.

---

### Post by FreebirdMike on 2011-10-06
> **mikechant said:**
> What I think you might have done is set 'show hidden files' for the current folder only (whatever this was). To set it for all files/folders you need to use edit>preferences as per steps 2/3/4 in this article:
[http://linux.about.com/od/ubuntu_doc/a/ubudg10t7.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg10t7.htm)

Did so and didn't change anything, anything else I can try?

---

### Post by FreebirdMike on 2011-10-13
Anyone have some advice? (*bump*)

---

### Post by Fedupera on 2011-12-20
I am having the same problem.

I am using a 1TB Freecom USB disk attached to a Lubuntu computer. This is not a USB disc problem. It is formatted with Fat16 I think and can be read by other versions of linux. Previously, I had no problems reading it with lubuntu either. However, now the file manager cannot get beyond about 2 or 3 levels of sub-folders. Lx terminal shows all sub folders without a problem.

I have tried disconnecting the USB cable and reconnecting, re-booting, standing on my head etc but nothing seems to work. Very occasionally, disconnecting and re-connecting the power to the USB disc does work but most of the time it does not.

I suspect it may be a bug in the File manager relating to memory useage:confused:

---

### Post by Fedupera on 2011-12-20
Further to my previous post, I checked the folder permissions in the terminal and discovered that only the owner (i.e. root) had access to the folders. I do not know how this has happened.

So, by opening the folder as root with a right click, the missing folders appeared. The permissions can be changed on in lxterminal using chmod if the disc has a linux file-system.

This is a useful article:
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

This is different from the default behaviour in Windows where you would be able to see folders but not open them.

---

