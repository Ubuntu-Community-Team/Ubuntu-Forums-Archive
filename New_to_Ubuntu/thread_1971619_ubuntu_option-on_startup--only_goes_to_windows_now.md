---
title: "ubuntu option-on startup--only goes to windows now."
date: 2012-05-02
forum: New to Ubuntu
---

### Post by dale1 on 2012-05-02
[FONT=Arial Black]Unable to get Ubuntu on startup any more- arrow to it--and it goes to window. I opened a previous down loaded Wubi--then it ask me "do i want to uninstall Ubuntu?" I dont have any desktop icons of Ubuntu and seemly no ubuntu system any more..could this be possible or likely? NEED [/FONT]Wifes Social security downloads,files,programs,ect. that i am working on! QUESTION ?? IF THIS CANT BE FIXED.. IS ANY OF THE STILL THERE? (I HAVE BEEN LATELEY SAVING PROGRAMS TO uBUNT CLOUD--I HOPE THAT HELPS)    ALSO,TRIED TO INSTALL NEW UBUNTU ALONG WTH MY WINDOWS    AND NO SUCCESS.   THANKING YOU IN ADVANCE, DALE OLIVER....               .......... USER DALE1.............

---

### Post by Zukaro on 2012-05-02
Try burning a LiveCD or making a LiveUSB to boot from, then from there you should be able to access the filesystem (Windows wont be able to access a Linux partition; it will detect it (in the computer management thing under disk management) but your only option in Windows will be to format it, so you'll have to use a LiveCD/USB to see if anythings still there).

Once you've boot up the LiveCD/USB find your Linux partition and open it up, then go to /home and look in there for your files (I'm assuming they're in your documents, in which case the filepath is /home/username/Documents).  If it's still there just copy it over to your Windows partition.

After you've done that try opening a terminal (hotkey is Ctrl Alt T) and then type "sudo update-grub".  I'm not sure if that will work, but it's worth a shot.  If that doesn't work then try BootRepair.



Here's the tutorial for BootRepair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The reason I suggest backing up your files first is in case something goes wrong and causes something bad to happen (although I doubt anything like that will happen, it's better to be safe than sorry).  You don't absolutely need to back them up first though, as the things I've mentioned wont mess with the partitions or anything (they only do stuff to grub).

---

### Post by dale1 on 2012-05-03
Thanks Zukzro- good info. I  am holding off on your advice because i recalled what may be important info.---i did do and earlier restore point--but that point was before i installed a ubuntu system!!!  Is this a consideration in you past or future advice?????      Secondly--i have been trying (to no avail- yet.) to install a new ubuntu online widow down load!  so---if i do this- 1.) will it negate or adversly affect your advice.??            2.) WOULD new ubuntu install-l  with this method --hurt or be helpful with your plan???!!!       THANKS  ---your reply gave me some hope and a direction!!!  "MOST APPRECIATED" DALE OLIVER

---

### Post by Zukaro on 2012-05-03
I don't think the restore point would do anything when it comes to Ubuntu (as the restore point is a Windows thing, and as far as I know, only backs up the Windows settings (it also shouldn't interfere with anything, regardless of the time of creation)).

As for using the Windows installer for Ubuntu to get back in, I don't think that would work very well (I'm not 100% sure, but I think using the Windows installer for Ubuntu formats the drive before you've even gotten into Ubuntu).  What you should do would be use the LiveCD/USB to try and retrieve your data/fix grub.

So basically; if you can, just use a LiveCD/USB (for USB you'll need at least a 2GB USB stick (an SD card or MS card likely wont work as I don't think BIOS supports booting off those; however, most modern day BIOS's support booting from USB)).

If you want to just reinstall Ubuntu then I still suggest using the LiveCD/USB then backing up your data (make sure to choose "try Ubuntu" when you boot up the LiveCD/USB (there will be an install option on the desktop so you wont have to reboot after backing up your files)).

If you're unable to backup your files due to encryption (as you can choose to encrypt your home folder during installation) try Fix-Boot or typing "sudo update-grub" into the terminal.


If you don't know how to create a LiveUSB here's a guide:
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

Here's one for a LiveCD:
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
(not sure if you need these or not but I figure I might as well link them)

---

### Post by jerome1232 on 2012-05-03
Did you initially install using Wubi? Wubi is the windows installer you refered to, if that is the case then it's an entirly different troubleshooting process.

Try a few things listed here if you did in fact install using Wubi.

[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

---

