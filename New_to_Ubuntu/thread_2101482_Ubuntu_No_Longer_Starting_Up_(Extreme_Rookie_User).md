---
title: "Ubuntu No Longer Starting Up (Extreme Rookie User)"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by MDRMC on 2013-01-04
Hello all, 

I am new here. Thank you all for taking the time to read through this. It is very much appreciated.  

I am extremely new and have little to no knowledge of Ubuntu/Linux. I originally got Ubuntu over 6 months ago because my Windows crashed and I did not have the install CD. 

_**My Problem: **_

I can no longer boot up Ubuntu. When I do so I get the following screen:

[IMG]http://img.photobucket.com/albums/v319/bizarre52/20130104_130518_zps49e561a0.jpg[/IMG]

_**Computer and system information:**_

Here's the information I was able to obtain. 

-HP G62 Notebook PC
AMD Phenom N850 Triple-Core Proccessor 2200mhz
Memory 4096mb

Video Card:
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]

- I cannot tell you which version of Ubuntu I was running. It was 12.xx and running on Gnome. 

_**More important information:**_

I am able to run Ubuntu via live USB. The only thing I care about is to retrieve certain folders and files. I have been able to get _some_ files using Live USB and accessing the Home folder on the hard drive through Ubuntu. 

_The problem with this is_ when trying to access certain folders I am getting the following message;

" The folder contents could not be displayed. You do not have permissions necessary to view the content of (insert folder name)"

_**What I am hoping can happen with everyone's help:**_

I hope I can repair these issues I am having without having to reinstall and loose any content saved on the hard drive.

With that being said, I am ok with wiping everything out and reinstalling Ubuntu as long as I can get the files off the hard drive first. 

Please do no hesitate to ask me for information I might have forgotten to include.   

Thank you again for your help.

---

### Post by howefield on 2013-01-04
I am pretty sure that you can reinstall without losing your /home folder by reusing the existing partitions and not marking them for formatting.

Have a browse here..

[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

However, I wouldn't recommend it without having gotten everything off the disk that you need on the basis that if something can go wrong it probably will :-).

---

### Post by audiomick on 2013-01-04
If you boot into the live CD and start the file manager with
```
gksudo nautilus
```

you should be able to access everything on the drive. That gives you an instance of the file manager with root privileges. I would suggest using this to back stuff up before you try what howefield suggested. Not that I don't believe that will work, but better safe than sorry.

If you have trouble with gksudo in the live session ( it has been a while, and I can't remember exactly what I had to do) create a new user in the live session, log off (not shutdown, just log off) and log back on as that user. It should then work with the password for that user. The user has to be part of the administrator group, of course.

---

### Post by Impavidus on 2013-01-04
Last time I was in a live session it worked fine. (gk)sudo asked a password, but just hitting enter works.

Reinstalling without losing your home directory only works if you have a separate home partition (I think). I don't think that's the default. It can be handy though, especially if you plan on breaking your system frequently. If you don't have a separate home partition yet, consider creating one while reinstalling.

---

### Post by MDRMC on 2013-01-04
> **howefield said:**
> I am pretty sure that you can reinstall without losing your /home folder by reusing the existing partitions and not marking them for formatting.

Have a browse here..

[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

However, I wouldn't recommend it without having gotten everything off the disk that you need on the basis that if something can go wrong it probably will :-).

Thank you I will try that once I backup everything.

---

### Post by MDRMC on 2013-01-04
> **audiomick said:**
> If you boot into the live CD and start the file manager with
```
gksudo nautilus
```you should be able to access everything on the drive. That gives you an instance of the file manager with root privileges. I would suggest using this to back stuff up before you try what howefield suggested. Not that I don't believe that will work, but better safe than sorry.

If you have trouble with gksudo in the live session ( it has been a while, and I can't remember exactly what I had to do) create a new user in the live session, log off (not shutdown, just log off) and log back on as that user. It should then work with the password for that user. The user has to be part of the administrator group, of course.


Sorry again I am very new at this. I'm not sure how I would do this. 

Would I simply open a terminal once in Ubuntu through live cd and type in the above code?

---

### Post by audiomick on 2013-01-04
> **Impavidus said:**
> Reinstalling without losing your home directory only works if you have a separate home partition (I think)....

That's what I thought, but Howefield's link seems to indicate otherwise.

I am personally a big fan of a separate /home partition, regardless. ;)

---

### Post by MDRMC on 2013-01-04
> **audiomick said:**
> That's what I thought, but Howefield's link seems to indicate otherwise.

I am personally a big fan of a separate /home partition, regardless. ;)

Michael, 

Thank you that code did work and now all my files are available. Your help was greatly appreciated.

---

