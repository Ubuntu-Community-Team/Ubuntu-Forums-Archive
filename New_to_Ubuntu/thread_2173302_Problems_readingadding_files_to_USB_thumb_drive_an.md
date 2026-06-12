---
title: "Problems reading/adding files to USB thumb drive and phone"
date: 2013-09-09
forum: New to Ubuntu
---

### Post by jay28 on 2013-09-09
Hi, I have looked everywhere for this post since I am pretty sure it is out there but I can't find it if it is. Having read 70 or so unrelated posts I have noticed a theme and I would like to appoligize in advance if you know where the answer to this question is and it annoys you that I can't find it. Yes, I am a noob and yes, I'm probably in over my head using linux and maybe I should just go back to Windows. I am posting because I have exhausted all other options.
THE PROBLEM
I tried to change the boot order of GRUB using "GRUB customizer". That created many problems and I had to reinstall GRUB through Windows to fix the problems. When I reinstalled GRUB, I lost the autoprompt in Ubuntu 12.04 that I used to get when I plugged in a phone or flash drive into any USB port.  I went to  System tools>System settings>Details>Removable Media and set everything to "Ask what to do." When I go to the "media" folder and open "USB" I can see a flash drive. If I try to add a file to the flash drive I get the message " 'INSERT RANDOM FOLDER NAME HERE' cannot be copied because you do not have permissions to create it in the destination". It will let me take files OFF of the flash drive. My phone doesn't show up at all. I would like to restore the autoprompt where it would ask me what to do upon plugging the flash drive in but if its easier to just get it under the USB folder thats fine with me. Again, I admit that I am a noob. Feel free to explain this to me like I am 4 years old. I have been using Windows my entire life and I am not a programmer. Thank you so much in advnace to anyone who may offer any help.

---

### Post by PopsTheSailor on 2013-09-10
I don't have a complete solution but this might put you in the right direction. Go to a terminal prompt and type sudo nautilus. This will open nautilus with rood / admin privileges. See if you get the same problems. That might at least tell you if it is an issue with access rights.

---

### Post by jay28 on 2013-09-11
Pops2, 
Thank you for your suggestion. I really do appreciate the help. Terminal displayed the following message after I opened nautilus: 

george@george-desktop:~$ sudo nautilus
[sudo] password for george: 
Initializing nautilus-dropbox 0.7.1
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

This message was displayed after I closed nautilus.

** (nautilus:2385): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist
Shutting down nautilus-gdu extension

I searched the forum for the first error message and found a [SOLVED] thread that advised me to install/enabled sharing on samba (and something called smbpasswd I think?) but this had no effect. When I opened nautilus I was able to move some important files onto my thumb drive (thanks again) but I don't want to enter root everytime for obvious reasons. Any idea on how to solve this? Thanks again in advance to anyone who offers any advice

---

### Post by PopsTheSailor on 2013-09-11
Funny, I get the same first error as you when I start nautilus. I never really paid attention to it though because I don't do this very often. I'm no expert on this stuff by any means. Is the dump drive encrypted by any chance? I did that for a while with one of my jump drives and that's what led me to find that using sudo nautilus would let me copy files. 

Oh, another thing. Is it only that one jump drive? Do you have another one to try? I know you mentioned you have issues with your phone too but let's stay with the jump drive. If it's just that one drive, you could try drastic measures like reformatting it and see if it clears some type of flag. Sorry I can't be more help. I'm not like some of these folks that are super techie. I've reached the limit of my expertise.

---

