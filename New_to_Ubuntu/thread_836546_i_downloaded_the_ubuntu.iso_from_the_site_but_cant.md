---
title: "i downloaded the ubuntu.iso from the site but cant find the .iso file"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by wattsburns on 2008-06-21
like the title says i downloaded the .iso file from the site and i downloaded InfraRecorder. on the site it says open infrarecorder and click burn image and find the .iso file. but i cant seem to find it. whats wrong?

---

### Post by kk0sse54 on 2008-06-21
If you are using Firefox go into the preferences to see where all downlaods go and that should be where the iso is

---

### Post by diablo75 on 2008-06-21
The default directory (folder) for Firefox downloads is your Desktop, if that helps.

---

### Post by wattsburns on 2008-06-21
well i can see the file i downloaded. i downloaded it with DAP. i extracted it with WinRar but i dont know what file to burn. in infrarecorder when you click burn image the options are .img. iso and.somethin else. i dont see any of thse types of files in the ubuntu folder i downloaded.

---

### Post by drs305 on 2008-06-21
If you didn't use Firefox, or want to use the command line:
```
sudo find /home -type f -iname *.iso
```

If that doesn't find it, run it again with / instead of /home

---

### Post by forger on 2008-06-21
> **wattsburns said:**
> like the title says i downloaded the .iso file from the site and i downloaded InfraRecorder. on the site it says open infrarecorder and click burn image and find the .iso file. but i cant seem to find it. whats wrong?

Are you using windows xp, windows vista, or other operating system?

---

### Post by wattsburns on 2008-06-21
i am using XP.

---

### Post by forger on 2008-06-21
> **wattsburns said:**
> well i can see the file i downloaded. i downloaded it with DAP. i extracted it with WinRar but i dont know what file to burn.

You **don't** extract the .iso file with winrar.
It's a "cd image", you open it with nero cd burner or with any cd burning software.

I use ImgBurn in windows:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
[http://www.imgburn.com/index.php?act=guides](http://www.imgburn.com/index.php?act=guides)

---

### Post by forestpixie on 2008-06-21
Burn the whole iso you downloaded - don't extract it - check the md5sum before you do

This is the md5sum list for 8.04

7d0ac92c56361949d099dd9337c975e7 *ubuntu-8.04-alternate-amd64.iso
166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso
8895167a794c5d8dedcc312fc62f1f1f *ubuntu-8.04-desktop-i386.iso
8a73cf85b04f37d5d91fb436525ea395 *ubuntu-8.04-server-amd64.iso
c3162b21757746c64a0a22cdd060b164 *ubuntu-8.04-server-i386.iso
cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe

How to check md5sum 

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by acelin on 2008-06-21
Dont confuse him. Open Infra Express instead- go to copy, then click the burn iso to cd. It will open a dialog box - find your downloads folder, and select the Ubuntu8.04.iso, click open, then click ok.

---

### Post by wattsburns on 2008-06-21
when i download it. it looks like this:

[IMG]http://i295.photobucket.com/albums/mm153/kyleeevanss/inwuu.jpg[/IMG]

so do i use that?

---

### Post by acelin on 2008-06-21
yes! that is the iso.

---

### Post by wattsburns on 2008-06-21
sorry posted that before i refreshed the page. ill try that and it should work. just waiting for nero to install. ill post back tonight to tell if it worked or if i had another problem.

thanks

---

### Post by forger on 2008-06-21
> **acelin said:**
> Dont confuse him. Open Infra Express instead- go to copy, then click the burn iso to cd. It will open a dialog box - find your downloads folder, and select the Ubuntu8.04.iso, click open, then click ok.

I just recommended to use a trustworthy program, I've personally never heard of infra express. Nero or imgburn should do a good work burning the cd.

**wattsburns**:
If you see any problems in the future while burning CDs, try to burn another cd at lower speed, say 4x or 1x

---

### Post by kk0sse54 on 2008-06-21
I use InfraRecord in Vista and XP all the time and all of my DVD's and CD's have burned fine. You really don't need to install Nero just to burn an Ubuntu iso

---

### Post by acelin on 2008-06-21
Infraexpress comes with infrarecorder! It is by far just as reliable and trustworthy as Nero!

OP! Dont wait on Nero! Its a waste of time and you dont need something so complicated to get this done!

---

### Post by wattsburns on 2008-06-21
ok i put in a blank cd. a LG CD-RW CED-8080B 1.04. it has 700MB of memory. the button isnt open to click:: [IMG]http://i295.photobucket.com/albums/mm153/kyleeevanss/hcggg.jpg[/IMG]

what kind of cd do i need?

---

### Post by mevets on 2008-06-21
You just need a regular CD. I couldnt tell you why exactly it wont let you burn, I'd guess its a bug. Try using imgburn ([http://www.imgburn.com/](http://www.imgburn.com/)) and see if you have the same problem.

---

### Post by damphoud on 2008-06-21
> **wattsburns said:**
> ok i put in a blank cd. a LG CD-RW CED-8080B 1.04. it has 700MB of memory. the button isnt open to click:: [IMG]http://i295.photobucket.com/albums/mm153/kyleeevanss/hcggg.jpg[/IMG]

what kind of cd do i need?

The iso wont burn becuase you dont have a CD-R in your dvd drive. If you where in that menu and if you where to place in a CD-R, your option would be enabled.

---

### Post by wattsburns on 2008-06-22
ok so damphoud was right. i tryed it in the dvd drive and it worked. now i have 1 problem and 1 question. problem: i put in a 2nd hardrive and now my system wont bootup. ive tryed going in and plugging in only 1 drive and its giving me the same error as when i had 2 in. why? and what do i do to run ubuntu from the disk?

---

### Post by forestpixie on 2008-06-22
To get your pc/laptop to run from the cd you need to get into the BIOS and chnage the boot order so that cd is first.

Usually you will see a message as it boots to enter setup.

Then as long as the burn is good and the iso was not damaged it should boot.

There is a check cd for defect option when the cd boots, use it.

If you have changed hdd about and have oproblems booting I would suggest checking what you have done, one needs to be a master and one a slave if they are on the same cable.

---

### Post by wattsburns on 2008-06-22
ok i loaded the disk and i chose install and it did a bunch of stuff then it stopped at ubuntu@ubuntu. it says im admin but idont know what to do from there

---

### Post by LeoSolaris on 2008-06-22
Did you download the Server edition?

---

### Post by wattsburns on 2008-06-22
Loading, please wait...                                                                           Linux ubuntu 2.6.24-16-generic #1 SMP T Apr 10 13:23:42 UTC 2008 i686                                                                                               The programs included wth the Ubuntu system are free software:     the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.                                     Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.                                                                 To access official Ubuntu documentation, please visit: [http://help.ubuntu.com/](http://help.ubuntu.com/)                                                                                   To run a command as adminstrator (user "root"), use "sudo <command>".                                                       
See "man sudo_root" for details.
ubuntu@ubuntu:~$ __

---

### Post by wattsburns on 2008-06-22
what do i do from there??  /\/\/\/\/\

---

