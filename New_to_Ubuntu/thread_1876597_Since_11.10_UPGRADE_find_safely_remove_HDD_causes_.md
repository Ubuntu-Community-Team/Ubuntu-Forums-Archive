---
title: "Since 11.10 UPGRADE find safely remove HDD causes freeze"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by Filthy Stockings on 2011-11-06
Hello

Since 11.10 UPGRADE have found that when try to SAFELY REMOVE external HDD, WD ELEMENTS that PC freezes and have to force reboot.

I have searched here and find problem affected others but cannot understand the solution properly.

eg

  	 	 	 	 	 	  [SIZE=3]*[http://osdir.com/ml/ubuntu-bugs/2011-07/msg37483.html](http://osdir.com/ml/ubuntu-bugs/2011-07/msg37483.html)*[/SIZE]
 

 

 [SIZE=3]*Subject: Re: [Bug 811745] Re: Whole system freeze after*[/SIZE]
 [SIZE=3]*safely remove external usb drive - msg#37483*[/SIZE]
 [SIZE=3]*List: ubuntu-bugs*[/SIZE]
 

 [SIZE=3]*Mail Archive Navigation:*[/SIZE]
 [SIZE=3]*by Date: Prev Next Date Index by Thread: Prev Next Thread Index*[/SIZE]
 

 [SIZE=3]*To Uditha Wijethilaka Bandara:*[/SIZE]
 [SIZE=3]*1) Unistall official 2.6.32-33 load with Synaptic (both*[/SIZE]
 [SIZE=3]*"linux-headers-2.6.32-33-generic" and "linux-image-2.6.32-33-generic"*[/SIZE]
 [SIZE=3]*2) Restart the computer*[/SIZE]
 [SIZE=3]*3) Command "uname -r" in a terminal to check the version (should be*[/SIZE]
 [SIZE=3]*2.6.32-32)*[/SIZE]
 [SIZE=3]*4) Check if you can remove your NTFS drive without any problem*[/SIZE]
 [SIZE=3]*5) Download the 2 .deb files from Herton link (take the version*[/SIZE]
 [SIZE=3]*belonging to your system, i386 or AMD) :*[/SIZE]
 [SIZE=3]*linux-headers-2.6.32-33-generic_2.6.32-33.71~lp811745r1_<system*[/SIZE]
 [SIZE=3]*version>.deb*[/SIZE]
 [SIZE=3]*linux-image-2.6.32-33-generic_2.6.32-33.71~lp811745r1_<system*[/SIZE]
 [SIZE=3]*version>.deb*[/SIZE]
 [SIZE=3]*6) Double click on the first downloaded file and follow instructions (it*[/SIZE]
 [SIZE=3]*should say a most recent official file exists: skip this)*[/SIZE]
 [SIZE=3]*7) Same thing with second file*[/SIZE]
 [SIZE=3]*8) Restart the computer*[/SIZE]
 [SIZE=3]*9) Check the version (see step 4)*[/SIZE]
 [SIZE=3]*10) Check the NTFS drive removal again*[/SIZE]


[SIZE=3]Can anyone help to explain the [/SIZE][SIZE=3]UNINSTALL/INSTALL [/SIZE][SIZE=3]steps, [/SIZE][SIZE=3]please?[/SIZE]
[SIZE=3]
If a link could be posted to where I go and then download this "rollback" [does that mean I will not be using 11.10 thereafter?][/SIZE][SIZE=3] I think I might be able to sort out this problem.

Thanks in advance.

SA
[/SIZE] 
[I]

[/I]**


[SIZE=3][/SIZE]

---

### Post by beew on 2011-11-06
This is for some old versions of Ubuntu. 11.10 uses kernel 3.x.

The instruction mentions synaptic, but synaptic is not installed by default in Ubuntu since 11.10. So open a terminal, and while you are at it, you should install gdebi as well, you use it to install .deb files with right click instead of using the software center. gdebi is much faster (choose open with gdebi when you click a .deb file, there is no easy way to choose it as default though in 11.10, there is work around, but let's not digress)

```
sudo apt-get install synaptic gdebi
```For a more up to date work around for your problem , check out post #70.
[http://ubuntuforums.org/showthread.php?t=1859528&page=7](http://ubuntuforums.org/showthread.php?t=1859528&page=7)

---

### Post by Filthy Stockings on 2011-11-07
Thanks for reply and advice and have entered the code you gave for "gdebi".

Apologies for being uninformed but on following your link to the 'solutionpost #70.
[http://ubuntuforums.org/showthread.php?t=1859528&page=7](http://ubuntuforums.org/showthread.php?t=1859528&page=7)' I do not understand how to determine

[SIZE=3]"your architecture (i386 or amd64)"[/SIZE] stated in below

  	 	 	 	 	 	  *[SIZE=3]Fix: Go to [http://people.canonical.com/~ogasawara/lp844957/](http://people.canonical.com/~ogasawara/lp844957/) and into the folder for your architecture (i386 or amd64). Install the 3 .debs located therein, and reboot. You should now be able to successfully remove the drive without issue.[/SIZE]*


[SIZE=1]In 11.10 can you offer a step by step how to find if am on i386 or amd64...[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]thanks in advance anyone who can advise[/SIZE]
[SIZE=2]
[/SIZE]
[I][SIZE=3][SIZE=2]SA[/SIZE]
[/SIZE][/I]

---

### Post by Healey on 2011-11-07
Hi 

Not sure if it has changed in newer versions of Ubuntu
But I am using Lucid Lynx and if you put 

uname -a

In a terminal it will tell you some things about your system

Hope it helps - I am not an expert - Sorry

Healey

---

### Post by waynefoutz on 2011-11-07
I've noticed this bug as well. I simply use the "unmount" option instead.

---

### Post by waynefoutz on 2011-11-07
> **Shia Asininity said:**
> Thanks for reply and advice and have entered the code you gave for "gdebi".

Apologies for being uninformed but on following your link to the 'solutionpost #70.
[http://ubuntuforums.org/showthread.php?t=1859528&page=7](http://ubuntuforums.org/showthread.php?t=1859528&page=7)' I do not understand how to determine

[SIZE=3]"your architecture (i386 or amd64)"[/SIZE] stated in below

  	 	 	 	 	 	  *[SIZE=3]Fix: Go to [http://people.canonical.com/~ogasawara/lp844957/](http://people.canonical.com/~ogasawara/lp844957/) and into the folder for your architecture (i386 or amd64). Install the 3 .debs located therein, and reboot. You should now be able to successfully remove the drive without issue.[/SIZE]*


[SIZE=1]In 11.10 can you offer a step by step how to find if am on i386 or amd64...[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]thanks in advance anyone who can advise[/SIZE]
[SIZE=2]
[/SIZE]
[I][SIZE=3][SIZE=2]SA[/SIZE]
[/SIZE][/I]

Did you install the 32 bit or 64 bit? i386 is the 32 bit, amd64 is the 64 bit.

---

### Post by Filthy Stockings on 2011-11-13
Sorry late THANKS but appreciate the reply and advice re 32 or 64 bits, to help me try and sort the FREEZING SAFELY REMOVE problem.

With 11.10 UBUNTU I found that if I go into L CLICK top R CORNER ICON [7 pointed star; UBUNTU logo?] get SYSTEM SETTINGS and showed me have 64bits.

SO then knew which of the 3 LINUX HEADERS/IMAGE to DL. Then INSTALLED em using the previously advised GDEBI PACKAGE INSTALLER and so, presume, they are now in my system somewhere.

So thanks for that....

BUT should I just go ahead and try to SAFELY REMOVE my WD HDD now to test this out?

Am, as a novice, always fearful when get alert about DEVICE REMOVED WITHOUT DUE PROCESS or whatever AND the two FREEZES that resulted both times tried to SAFELY REMOVE the HDD, following 11.10 UPGRADE as do not want to LOSE any material; tho tried to backup all....

Anyway of testing if the new system will work WITHOUT risking further FREEZES and/or loss of HDD data?

Or am I being too cautious and should just go ahead and trust I followed the advice given correctly?

Thanks to all who helped, anyway.

---

### Post by beew on 2011-11-13
The 3 .debs you installed are Linux kernel 3.0.0-13 and its headers, the one that is having the problem is 3.0.0-12. After installing the .debs you have basically upgraded your kernel. For that to take effect you need to reboot, and then you can test with a usb drive.

When you boot there will be 2 choices to boot into, make sure you choose Linux 3.0.0-13 (the entry Linux 3.0.0-12 will still show up unless you uninstall  the old kernel) If everything works you can delete Linux 3.0.0-12 from Synaptic, there are again 3 packages to delete (remember you have installed 3 .debs for Linux 3.0.0-13) , consisting of Linux image and two headers (generic and "all")

Oh, since 11.10 doesn't come with Synaptic you may want to install it too, it makes managing your software packages a lot more effective and faster than the stupid software center.
```

sudo apt-get install synaptic
```

---

### Post by Filthy Stockings on 2011-12-30
VERY belated thanks for help BEEW

Belated MERRY XMAS and premature HAPPY NEW YEAR!

---

