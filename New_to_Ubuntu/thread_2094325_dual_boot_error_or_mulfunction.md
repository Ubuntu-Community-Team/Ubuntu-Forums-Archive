---
title: "dual boot error or mulfunction"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by Marthewicked on 2012-12-13
Hello,

Im trying to help a friend and here is what is going, i tried to install ubuntu with computer already had windows 7 installed, the cd did not work after i chose instal ubuntu along with windows.
But the cd had error so i went to get my flash dr and installed 12.04 from stick.
Now when i went back to install there were the option of 
1- reinstall ubuntu and delete the incomplete ubuntu
2- wipe ubuntu and windows and install ubuntu
3- and something else

I chose the 1st option and installed but it will not dual boot, it just boots ubuntu.

I have tried to install again just to see if windows got wiped out and it is not. The computer stil has windows and ubuntu. The back up is not working so the hard drive is my only option to retrieve.

I want to know if i can delete ubuntu and have windows to work and do another back up and test it (i did not test it ugh before going to installation ehh)
Or if i can try to use the option something else and reinstall ubuntu where i can have windows to boot.

Thank you.

And the computer is machines i dont know model yet.

Thanks in advance.

---

### Post by TheFu on 2012-12-13
> **Marthewicked said:**
> I want to know if i can delete ubuntu and have windows to work and do another back up and test it (i did not test it ugh before going to installation ehh)

I'm sorry that the boot got messed up somehow.  Removing Ubuntu probably will not correct the issue, but it might.  Did you install Ubuntu to a different partition or under the C: drive somewhere using a WUBI install?

With all the recent changes to HDDs and UEFI recently, it is hard to suggest much without more data about the system, drives and partitioning.  There is a script that will grab all the necessary data ... I need to look for it to find the link.  

Here's a how-to: [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) 

Boot into rescue mode using the USB flash drive, downloaded the script, run it for the **RESULTS.txt**  output to be saved.  Then paste that output here.

---

### Post by Marthewicked on 2012-12-13
Different partition. Like, i chose the option along side windows where i can move the slider left or right.
Right being ubuntu sda2 and sda1 on windows 7. 

I will try that rescue mission whatever that is i have never done that.

Oh, if i put usb stick as if im to install again and i choose "something else" and partition the ubuntu which i delete again, shouldnt that let me have windows to boot?

---

### Post by TheFu on 2012-12-13
> **Marthewicked said:**
> Different partition. Like, i chose the option along side windows where i can move the slider left or right.
Right being ubuntu sda2 and sda1 on windows 7. 

I will try that rescue mission whatever that is i have never done that.

Oh, if i put usb stick as if im to install again and i choose "something else" and partition the ubuntu which i delete again, shouldnt that let me have windows to boot?

It is unlikely that removing the Ubuntu partition will alter the boot back to  Windows.  It all depends on where the boot manager was written.  Do you  remember where you told the installer to write the boot manager/grub  during your install attempt?  I would guess there were 3 choices presented
* /dev/sda
* /dev/sda1
* /dev/sda2

There is a **How-To** somewhere for this exact issue [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) . In theory, it will fix Ubuntu AND Windows boot issues.  I've never used it, but it is worth a try.

If the boot-repair how-to doesn't work, please run that script and post the output here.

Good luck.

---

### Post by Marthewicked on 2012-12-13
> **TheFu said:**
> It is unlikely that removing the Ubuntu partition will alter the boot back to  Windows.  It all depends on where the boot manager was written.  Do you  remember where you told the installer to write the boot manager/grub  during your install attempt?  I would guess there were 3 choices presented
* /dev/sda
* /dev/sda1
* /dev/sda2

There is a **How-To** somewhere for this exact issue [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) . In theory, it will fix Ubuntu AND Windows boot issues.  I've never used it, but it is worth a try.

If the boot-repair how-to doesn't work, please run that script and post the output here.

Good luck.

Thank you.

I wrote on the dev sda 2 i will post it give me few

---

### Post by Marthewicked on 2012-12-13
julio@julio-ET1330:~$ sudo bash ~/Desktop/boot_info_script*.sh
[sudo] password for julio: 
bash: /home/julio/Desktop/boot_info_script*.sh: No such file or directory
julio@julio-ET1330:~$ 
julio@julio-ET1330:~$ sudo bash ~/Downloads/boot_info_script*.sh
bash: /home/julio/Downloads/boot_info_script*.sh: No such file or directory
julio@julio-ET1330:~$ 

No such file, or am i being clumsy here?

---

### Post by Marthewicked on 2012-12-13
it might be sda 1 because windows was on dev/sda and dev sd2 was still blank.

---

### Post by oldfred on 2012-12-13
Latest version of bootinfoscript has been renamed.

Best to find file in directory you downloaded into. Usually Downloads but it may be whatever default you have set.

fred@fred-Precise:~$ cd Downloads
fred@fred-Precise:~/Downloads$ ls boo*

Edited my list as I still have a bunch of old copies.

fred@fred-Precise:~/Downloads$ ls bootin*
bootinfoscript-061.tar.gz
bootinfo_results.zip     
bootinfoscript     

fred@fred-Precise:~/Downloads$ sudo bash bootinfoscript
[sudo] password for fred: 

long list of what it is doing 

   Finished. The results are in the file "RESULTS5.txt"
located in "/Downloads/".

Keep track of where and exact name that it saved your results.txt
Mine is results5.txt as it already had 4 other older copies.

---

### Post by Marthewicked on 2012-12-13
it is not under downloads but i will search to see where it was downloaded to.  It was default so i don't know why it is not on downloads folder

---

### Post by Marthewicked on 2012-12-13
julio@julio-ET1330:~$ /Downloads
bash: /Downloads: No such file or directory
julio@julio-ET1330:~$ cd Downloads
julio@julio-ET1330:~/Downloads$ ls boo*
ls: cannot access boo*: No such file or directory
julio@julio-ET1330:~/Downloads$ 

so far but the location under file systems is "/" or just /

---

### Post by oldfred on 2012-12-13
I would look in Desktop or just your home.

fred@fred-Precise:~$ cd /home/fred/Desktop
fred@fred-Precise:~/Desktop$ ls
firefox.desktop         libreoffice-writer.desktop  sol.desktop
gnome-terminal.desktop  Picasa 3.desktop            thunderbird.desktop

I do not have copy in Desktop. But I do have another copy in my /home.

fred@fred-Precise:~$ ls bootin*
bootinfoscript

---

### Post by Marthewicked on 2012-12-13
Thank you soooo much guys,
I knew i had it right and the boot sequence was ok the problem was in an area i was not expecting on....new problem everyday.
The screen monitor was made by acer and "the input is not supported" comes on after i start. 
Here is where you pick which windows to boot. Since i see dark screen with "the input is not supported" square box i might as well be duh-duh. The first option was ubuntu no wonder it just boots to just that alone.
How i figured? I clicked arrow button accidently and it went to recovery. I did it again and same thing. I started and clicked three arrows down and it went to safe mode or the repair mode.
I kept at it till i found windows boot. And windows boots up on the fifth arrow hit.

So, now i told friend how to boot on two windows, start up and five hits on arrow down key and hit enter and windows boots up viola.

It was the weirdest problem ever, booting on to pc blindly.

You guys are always the best though.

Thank you so much.

---

### Post by TheFu on 2012-12-14
> **Marthewicked said:**
> Thank you soooo much guys,
I knew i had it right and the boot sequence was ok the problem was in an area i was not expecting on....new problem everyday.
The screen monitor was made by acer and "the input is not supported" comes on after i start. 
Here is where you pick which windows to boot. Since i see dark screen with "the input is not supported" square box i might as well be duh-duh. The first option was ubuntu no wonder it just boots to just that alone.
How i figured? I clicked arrow button accidently and it went to recovery. I did it again and same thing. I started and clicked three arrows down and it went to safe mode or the repair mode.
I kept at it till i found windows boot. And windows boots up on the fifth arrow hit.

So, now i told friend how to boot on two windows, start up and five hits on arrow down key and hit enter and windows boots up viola.

It was the weirdest problem ever, booting on to pc blindly.

You guys are always the best though.

Thank you so much.


Blank screen boots are tough. As a new user, it is difficult to tell a blank screen issue from a minor grub issue, as you described. 

There are troubleshooting guides just for that. Let me search ... found it **[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)**

I'm glad you figured it out. Might be worth seeing if pressing up-arrow 1 or 2 times will boot Windows easier.  I don't know since I reboot so seldom and when I do, I'm usually not in the same room or building as the machine.
```
$ uptime
 10:07:00 up 63 days, 34 min,
```

---

### Post by Marthewicked on 2012-12-14
Yea,apparently ubuntu is selected automatically if up or down is not clicked. But if arrow down is clicked five times windows boots up. I have not tried up keys as it is possible windows being the last to choose and up arrow could make 1st or 2nd key. I have never seen anything like this before on all computers i have worked on. Thanks for the links though

---

### Post by oldfred on 2012-12-14
Grub now tries to use video from system, but it sometimes just needs to use defaults.

       Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply
       
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    OR: grub-customizer
       Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

