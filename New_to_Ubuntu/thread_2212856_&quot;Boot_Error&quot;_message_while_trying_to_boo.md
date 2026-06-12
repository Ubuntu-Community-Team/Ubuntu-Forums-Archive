---
title: "&quot;Boot Error&quot; message while trying to boot from USB!"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by meathdeath on 2014-03-23
Ubuntu Forum,

I for the life of me cannot figure out why in the world the USB image I have created of Ubuntu 12.04 LTS is refusing to become bootable from my computer. I have tried using the Universal USB Installer from [http://pendrivelinux.com/](http://pendrivelinux.com/) and tried both going with and without a persistence file on the flash drive. With both I had no luck. I keep getting the same message. I'm using a Lexar 4GB flash drive, but have also tried this with an 8GB SanDisk flash drive. Initially I tried doing this with Ubuntu 13.10, but then tried Ubuntu 12.04 LTS seeing as it wasn't working. I have also tried using an Acer laptop to try to do this process without luck as well as the computer I am currently using and trying to get it on. (Sony VPCEB32FM) When I try to boot it up on my Acer it gives me some weird text that I'm assuming amounts to simply the copyright. (Or something) I waited on that and nothing happened after hours. I am using XP on my Vaio and Windows 7 on my Acer laptop. I even tried to redownload and use 3 different versions of the Universal USB Installer program. I HAVE changed my bios to boot from USB and tried several different combinations on my bios. I have tried every possible combination it appears I have at my disposal. I would simply just burn a DVD and go off of that only the optical drive is nonfunctional. (EVEN IN THE BIOS after installing windows XP) So if you are reading this and have ANY useful tips or ideas on how to get this thing going on Ubuntu I would VERY MUCH appreciate your help. 

Thanks,

Meathdeath

---

### Post by Rex Bouwense on 2014-03-23
Sounds like you are frustrated.  Sit back and have a cup of coffee.  First, did you check the MD5Sum after you downloaded the image?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If that checked out OK, then the next problem area is the burning.  I personally use UNetbootin but other applications work just as well.  
Next, some computers, and I cannot give you a list, recognize a flash drive as an additional hard drive.  Go to your BIOS and navigate to Boot.  If there is a + sign by the hard drive, that may be the problem.  Click on hard drive and if you see your flash drive, move it to the top of that catagory.  Save, exit, and continue with the boot sequence.

---

### Post by meathdeath on 2014-03-23
I am. Thank you for recognizing that man. As for checking the MD5Sum I have not. Let me do that real quick. I did try and use UNetbootin for the first attempt. (Believe I failed to mention that in my post) I have booted from flash drives in the past. It just recently started acting up after I installed Windows XP. (On my Vaio) Thanks for the reply man.

---

### Post by meathdeath on 2014-03-23
MD5Sum confirmed that the hashes are the same. I assume that means that the checksum is "OK" correct?

---

### Post by meathdeath on 2014-03-23
I still cannot boot from the USB though. It doesn't change anything. I just retried using unetbootin and it acted in the exact same way.

---

### Post by meathdeath on 2014-03-23
Note: Both times Checksums were "OK"

---

### Post by slooksterpsv on 2014-03-23
Is it formatted as FAT32 the Lexar or SanDisk? If so, if you have the ISO accessible, format it again, but use Unetbootin to put it on the USB drive.
Otherwise if it's not FAT32 it won't boot properly or at all.

---

### Post by meathdeath on 2014-03-23
Yes. I formatted it as FAT32 with Universal... Let me try and format FAT32 using unetbootin since that seems to be a forum favorite. Share with you the results as soon as they're available.

EDIT: IT'S ALREADY FORMATTED AS FAT32. JUST CHECKED THE PROPERTIES IN WINDOWS XP. (SAVING MYSELF TIME AND ENERGY)

---

### Post by meathdeath on 2014-03-23
I also have formatted and reformatted so many times that it would be impossible that it is anything other than FAT32 unless I'm just a blithering idiot. (Which in all likelihood 
could very well be the case)

---

### Post by slooksterpsv on 2014-03-23
It's all good, sometimes it's better to reformat just to make sure something didn't go wrong, than to not do so at all. Question, are you running Antivirus on the system? If so what one?

---

### Post by meathdeath on 2014-03-24
I am not what so ever. Even if I had I clearly mentioned in the description of the thread that I have attempted to make this flash drive bootable from my Acer laptop. I just NOW installed Windows Security Essentials before logging on, but that was only 30 minutes ago before reading your post. Any other ideas?:/ This is quite frustrating for me.

---

### Post by slooksterpsv on 2014-03-24
Calm down there - I never implied you were an idiot or that. The issue you're facing seems like it is a growing issue. You're not the only one experiencing this issue.

1 - First of all, have you tried another USB port? 
2 - Are you able to get what the Boot Error says or does it just flip back and restart? This may give us more of a clue.
3 - One last option would be to go into BIOS, and reset BIOS, load the defaults back (should be on the last page). After that try to boot from the USB.

The error that it gives would be the most helpful.

This one is a real thinker. Something's not right.

---

### Post by meathdeath on 2014-03-24
I never said that. I just get upset because I have emotional problems. (Swear on my life - my bad)

1- I tried all of them
2- It only says "Boot Error" in white text on a back blackground. (If I press enter it goes to Windows, but the BIOS may just be sending it to the next available bootable device)
3- I tried resetting all of the options to default, and even changing something about C3/C6 CPU support. (Not sure what it was, but dead end)

I agree. All it says is "Boot Error" though. It's VERY not right. I swear.

---

### Post by slooksterpsv on 2014-03-24
I've been doing a lot of research on this laptop trying to figure out what the heck is going on. Hmm...

[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

Let's try this app - it will work with Windows XP on up and works on the low-level spectrum of the programs we have been using.

---

### Post by slooksterpsv on 2014-03-26
Holy crap since I posted a lot of my content in the wrong thread I'll post an update to the correct one (this one) on what's been going on.

Using a TeamViewer session we chkdsk'ed the drives, we checked the partitions in diskmgmt and everything is fine, but Linux will not pick up on the partitions already created. In gparted it's showing that the whole drive is unused - free space is 298GB of a 320GB hard drive (max size after translating is 298GB). We're trying a live cd boot and I'm going to run some items in Linux over Team Viewer to see if that helps.

Otherwise the only way to go from here is either Ubuntu or Windows - no other choice.

---

### Post by JoshuaXD on 2014-09-05
For the benefit of anyone (like me) who found this thread when googling the unhelpful "Boot Error" message, I want to suggest something simple -

**Try a different USB stick. Try a different USB port.**

I am reviving a beat up old Windows laptop for a friend - a Toshiba T215 - and after installing the latest Ubuntu as dual boot, I decided to start over with a clean install of Lubuntu, no dual boot. The Ubuntu install had gone flawlessly. The Lubuntu install kept having this "Boot Error" message, going to a blank black screen with a purple border, then booting back to Ubuntu. The ISO passed an md5 check, I reformatted the thumb drive, etc, with no results.

After reading [this]("https://help.ubuntu.com/community/Installation/FromUSBStick"):

> [COLOR=#333333][FONT=Ubuntu]Most but not all USB pendrives are reliable for booting ... [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Some computer hardware and some operating systems have issues with certain ports. And some USB pendrives just have issues also. Some of them cannot be used for booting. ... Some USB pendrives and computers 'do not like each other'. The pendrive might boot another computer, and the computer might boot from another pendrive (everything else being the same).[/FONT][/COLOR]

I tried using the laptop's other USB port. No luck. I tried a different USB stick. No luck. I tried the different USB stick in the other port... SUCCESS.

[COLOR=#333333][FONT=Ubuntu]> Some USB pendrives and computers 'do not like each other'.[/FONT][/COLOR]

---

