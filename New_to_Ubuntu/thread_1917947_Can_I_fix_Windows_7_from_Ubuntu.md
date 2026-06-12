---
title: "Can I fix Windows 7 from Ubuntu"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by abhishek.purkayastha on 2012-01-31
Hi 
I have a hp g72 250us laptop which came with an in built windows 7 home 64 bit. 
Since last few days I have not been able to boot my Windows at all. The normal mode won't boot and will flash a blue screen momentarily with error codes and then my machine restarts itself. The safe mode,safe mode with command prompt and safe mode with networking hangs at**classpnp.sys** and then my machine restarts itself. The last know good configuration also does the same thing.
 
If I use the startup repair option then it goes beyond the loading files into a blue screen(the one for logon) but thats it and nothing happens(I have kept it at that stage for 8 hours still nothing). So today I wanted to load it from a recovery disk. I went into my BIOS setup and changed the boot option to boot from CD, but even when I boot from the recovery CD , I face the same issues as I had faced with booting from hard drive. i tried using the CD on a separate laptop which i have and there the CD works fine and gives me the startup repair option and does everything it should.
 
I am runnung Ubuntu 11.10 via a Wubi installation on the same machine and Ubuntu is in the same C drive as Windows. I can login and work fine in Ubuntu. So I was wondering if there is any way by which I could run a chkdsk or anything for that matter which can help me at least boot into Windows so that i can run a recovery or something. Now since Windows came in built I do not have a installation disk with me and buying a new one is shelling quite a sum of money.
 
Any suggestions?

---

### Post by HappyLinux on 2012-01-31
I did a quick search for "classpnp.sys" and it came up with many results. Apparently, you're not alone with this problem.

Here, have a good read at these 2 threads.

[http://social.technet.microsoft.com/Forums/en/w7itprogeneral/thread/566cdd43-ce91-4e64-93e0-8d09d8fc1ea0](http://social.technet.microsoft.com/Forums/en/w7itprogeneral/thread/566cdd43-ce91-4e64-93e0-8d09d8fc1ea0)

and

[http://answers.microsoft.com/en-us/windows/forum/windows_7-system/laptop-hangs-up-at-classpnpsys-file/2b7213da-ba91-4228-af9d-2ba6b2d2edc0](http://answers.microsoft.com/en-us/windows/forum/windows_7-system/laptop-hangs-up-at-classpnpsys-file/2b7213da-ba91-4228-af9d-2ba6b2d2edc0)

I hope these help, or at least get you on the right track.

---

### Post by abhishek.purkayastha on 2012-02-07
Hi I do not know if I am asking the question in the right forum but I need help .I am running Ubuntu 11.10 through a Wubi install.I also have Windows 7 running on my machine and both Ubuntu and Windows are in the same disk. This is what happened a few weeks back, my windows simply refused to boot up. None of the options seem to work. So i tried to boot from a repair disk and still the same , no luck. I used to get an error like unmountable disk drive.But all this time I have been able to login into Ubuntu just fine.
So I got myself a windows boot disk and although i manage to boot windows up through the disk but that's it. It gives two options to either repair or install.The repair option doesn't respond and I have left it at that for one night and the install option hangs at setup is starting and doesn't go beyond that(i have kept it at that for 8 hours).
So after reading a lot of posts I think that I need to do something to my bios. basically I am using a Hp g72 250 US laptop 64-bit and its running Insyde H20 bios which doesnt give me any advanced menu options to change my hard disk type etc etc.
So I figured I would flash my bios from Ubuntu and although there are a few posts on it I have really not been able to understand where do I get the image file for Bios etc.
So can somebody please help me,I need to desperately get my windows up and working and I have to do it using my Ubuntu.
Any suggestions (including how to flash bios)welcome!!!!

---

### Post by cariboo on 2012-02-07
Please don't create multiple threads on the same subject. I have merged your two threads.

Forum policy allows you to bump your thread every 24 hours to bring it back to the top of the page, so I'd suggest you do that, instead of creating new threads.

---

### Post by abhishek.purkayastha on 2012-02-07
> **HappyLinux said:**
> I did a quick search for "classpnp.sys" and it came up with many results. Apparently, you're not alone with this problem.

Here, have a good read at these 2 threads.

[http://social.technet.microsoft.com/Forums/en/w7itprogeneral/thread/566cdd43-ce91-4e64-93e0-8d09d8fc1ea0](http://social.technet.microsoft.com/Forums/en/w7itprogeneral/thread/566cdd43-ce91-4e64-93e0-8d09d8fc1ea0)

and

[http://answers.microsoft.com/en-us/windows/forum/windows_7-system/laptop-hangs-up-at-classpnpsys-file/2b7213da-ba91-4228-af9d-2ba6b2d2edc0](http://answers.microsoft.com/en-us/windows/forum/windows_7-system/laptop-hangs-up-at-classpnpsys-file/2b7213da-ba91-4228-af9d-2ba6b2d2edc0)

I hope these help, or at least get you on the right track.

Thanks for replying. basically I tried most of the options in the above threads. I say most because some of the options require to at least go into windows with last known good configuration or something and I can't do that as my machine reboots at all options. 
So I tried to do a new install by getting myself a CD and that too wont help because the install hangs at setup is starting and I cant do anything.Although the same boot CD will go beyond that step when i choose to use it through a VMware installation on Ubuntu.
So I figured the only option left for me was to tinker around with my BIOS ("change the disk mode from AHCI to ID") but my BIOS (INSYDE H20) doesn't have anything which can enable me to do that, i.e no advanced menu/tabs.
So I was wondering if I can update/flash my bios through Ubuntu and hence I asked the second question today (which has been merged to this thread now).
I do not know if flashing my bios would help because if it doesn't I dont know what else I am supposed to do.

---

### Post by ecopccare on 2012-02-07
Ubuntu can do some amazing things for windows, but somethings you really need to use Microsoft's own tools to repair certain issues.  I've seen similar problems like you described originate from rootkits and bad sectors in the filesystem.  Unfortunately i don't know any way to check either of those from within Ubuntu.  There is clamAV which is useful for offline virus scanning, and a few other tools

---

### Post by ecopccare on 2012-02-07
I just had an idea, you can use virtual box, and install a virtual instance of windows, and I think that could run check disk and other tools on your windows partition, just a thought

---

### Post by abhishek.purkayastha on 2012-02-07
> **ecopccare said:**
> I just had an idea, you can use virtual box, and install a virtual instance of windows, and I think that could run check disk and other tools on your windows partition, just a thought

Yes I wanted to do that as well. But I do not know whether I will be able to do it as I am running Ubuntu through a Wubi installer. In fact i started it this morning, and the windows installation goes to a point where it says expanding files. Then the whole system hangs.
I don't know if thats because of lack of sufficient RAM or something. There is a message that comes up saying I may not have allocated sufficient swap space and it needs 1gb swap space whreas 256 mb is allocated. I clearly remember to set RAM to 2gb for the new virtual machine(i have a total of 3gb) in the Vmware settings before starting the windows install. But I don't know if Ubuntu itself has access to all the RAM and Space since its not on a different partition really.
Any idea on what is swap space?

---

### Post by Mark Phelps on 2012-02-07
If you can burn a CD, then you could try using Boot-repair to fix the Windows booting issue:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

But that will only get booting to work again.

You may have to resort to removing the hard drive from your PC and connecting it to another Windows PC -- to run chkdsk on it from there.

Also, NONE of this is going to fix bluescreens.  To do that, you really need to go to a Win7 forum: sevenforums.com.  They have tutorials and can provide diagnostic help.

---

### Post by abhishek.purkayastha on 2012-02-07
> **Mark Phelps said:**
> If you can burn a CD, then you could try using Boot-repair to fix the Windows booting issue:
 
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)
 
But that will only get booting to work again.
 
You may have to resort to removing the hard drive from your PC and connecting it to another Windows PC -- to run chkdsk on it from there.
 
Also, NONE of this is going to fix bluescreens. To do that, you really need to go to a Win7 forum: sevenforums.com. They have tutorials and can provide diagnostic help.
 
I can  burn a CD so I will try this and let you know how it goes. 
Basically if I can just get to point where I can format my entire hard disk with the help of a cd/drive that will do.
At this point I am just thinking of removing everything and re-install everything fresh.

---

### Post by nipunshakya on 2012-02-07
If you want to install fresh, you can download a copy of ubuntu from [FONT=verdana][SIZE=3][Ubuntu's website]("http://www.ubuntu.com/download/ubuntu/download")[/SIZE][/FONT] and then install ubuntu to your whole machine(if you want that). make sure to try ubuntu first in LiveCD mode to make sure it works well with your machine, later you can install the whole of ubuntu to your machine, or have a dual boot as u want..

---

### Post by Mark Phelps on 2012-02-07
> **abhishek.purkayastha said:**
> ...
At this point I am just thinking of removing everything and re-install everything fresh.

Sorry ... didn't know you had the media for doing a fresh install.

That being the case, you may be able to fix Win7 by booting from the Win7 DVD, choosing the option for command mode, and once there, entering "sfc /scannow" (without the quotes).  That will run  a scan looking for missing/corrupted system files and will replace/repair them from the contents of the DVD.

If all your problems are related to missing/damaged system files, that should fix it without requiring a reinstall.

Also, as a second approach, you can use the Win7 DVD to do a "Repair Install".  That will leave your data and apps intact, replacing only the system files.  Instructions for this can be found on the Win7 forum site: sevenforums.com.

---

### Post by abhishek.purkayastha on 2012-02-07
> **Mark Phelps said:**
> Sorry ... didn't know you had the media for doing a fresh install.

That being the case, you may be able to fix Win7 by booting from the Win7 DVD, choosing the option for command mode, and once there, entering "sfc /scannow" (without the quotes).  That will run  a scan looking for missing/corrupted system files and will replace/repair them from the contents of the DVD.

If all your problems are related to missing/damaged system files, that should fix it without requiring a reinstall.

Also, as a second approach, you can use the Win7 DVD to do a "Repair Install".  That will leave your data and apps intact, replacing only the system files.  Instructions for this can be found on the Win7 forum site: sevenforums.com.

Thw win7 dvd is pretty useless now as it will boot and then hang.Repair or install hangs using the dvd.Right now I am trying to use the boot repair and trying to repair the MBR of windows.Thanks to ur links. I am also downloading iso files of Ubuntu Cd's so that I can use them to boot my machine and then probably remove windows totally before doing a clean install.

---

### Post by abhishek.purkayastha on 2012-02-08
hi the bad news is after fixing the MBR I can't login into Ubuntu as well. Basically during the startup when it asks me the option to boot Windows or Ubuntu , in that menu whether I choose Windows or ubuntu it comes up with the same error message
 
"Windows failed to start.A recent hardware or software change might be the cause.
To fix problem 
insert windows installation disk and restart computer blah blah blah"
Info:the boot selection failed because a required device is inaccessible.
 
Well worth mentioning that just before this menu comes up it flashes MBR on my screen for a second or so.
I tried to boot it from a CD where I had burnt the ubuntu CD image but i wont boot or do anything from the CD and keeps coming back with the same options and error page.
So basically now i have lost access to Ubuntu as well!!!

---

### Post by abhishek.purkayastha on 2012-02-09
Someone please help me I have lost access to both my OS now.I am in a big soup now :(

---

### Post by Mark Phelps on 2012-02-09
If you can't boot from Windows -- maybe because the boot loader files are damaged or missing -- switching the MBR to point to Windows by default is NOT suddenly going to get you a working machine.

You need to repair ALL the Windows boot loader stuff -- and you should be able to do that either with the Boot-Repair CD or by inserting the Win7 DVD and running Startup Repair three times, that's right, three times.

If you're unable to read or boot from CDs, you're in major trouble.

---

### Post by abhishek.purkayastha on 2012-02-09
> **Mark Phelps said:**
> If you can't boot from Windows -- maybe because the boot loader files are damaged or missing -- switching the MBR to point to Windows by default is NOT suddenly going to get you a working machine.
 
You need to repair ALL the Windows boot loader stuff -- and you should be able to do that either with the Boot-Repair CD or by inserting the Win7 DVD and running Startup Repair three times, that's right, three times.
 
If you're unable to read or boot from CDs, you're in major trouble.
 
Yeah looks like I am in trouble. But now I can get my machine to boot from Ubuntu for a start!!
 
Here is the current scenario:with my Windows 7 dvd i can boot up and get to the install/repair part.But the install and repair both hang for indefinite periods so I am unable to do anything.
 
Using mY Ubuntu CD I can my machine to boot and since I am new to Ubuntu I dont know many options that i can use. After reading from the CD it comes up with a purple screen where if i press enter it gives me options under F1,F2,F3,F4 etc.. 
I tried one option to check disk for defects and it took me to a black screen with a beeping cursor and then it came up with 9/10 lines saying this;
 
udev[105] :timeout killing 'sbin/blkid -o udev -p -u noraid /dev/sro' [265]
 
and the last line has an added part to the above statement:
 
terminated by signal 9 [killed]
 
And then it takes me to a purple screen with the logo where Its kind of loading Ubuntu(the dots suggest  that), but it remains at that screen for 15-20 minutes and after that I restart my machine.
 
Next time after I restart my machine and choose "try Ubuntu without installing" option, that again takes me to that black screen with beeping cursor and those 9 lines come up and basically a repeat of the 1st step.
 
Now I know there are other options in the first purple screen but I do not know what i should choose, because choosing the above two gets the same kind of result.
 
I know I am being a noob at the moment and sorry for being a pain, but I really need to get my machine formatted or fixed!!!!
is there anyway i can at least format my disks thorugh this Ubuntu CD

---

### Post by nipunshakya on 2012-02-09
> **abhishek.purkayastha said:**
> Yeah looks like I am in trouble. But now I can get my machine to boot from Ubuntu for a start!!
 
Here is the current scenario:with my Windows 7 dvd i can boot up and get to the install/repair part.But the install and repair both hang for indefinite periods so I am unable to do anything.

How long exactly does the indefinite periods refer? because startup repair in mine once took more than 30 minutes...
 
> **abhishek.purkayastha said:**
> Using mY Ubuntu CD I can my machine to boot and since I am new to Ubuntu I dont know many options that i can use. After reading from the CD it comes up with a purple screen where if i press enter it gives me options under F1,F2,F3,F4 etc.. 
I tried one option to check disk for defects and it took me to a black screen with a beeping cursor and then it came up with 9/10 lines saying this;
 
udev[105] :timeout killing 'sbin/blkid -o udev -p -u noraid /dev/sro' [265]
 
and the last line has an added part to the above statement:
 
terminated by signal 9 [killed]
 
And then it takes me to a purple screen with the logo where Its kind of loading Ubuntu(the dots suggest  that), but it remains at that screen for 15-20 minutes and after that I restart my machine.
 
Next time after I restart my machine and choose "try Ubuntu without installing" option, that again takes me to that black screen with beeping cursor and those 9 lines come up and basically a repeat of the 1st step.
 
Now I know there are other options in the first purple screen but I do not know what i should choose, because choosing the above two gets the same kind of result.
 
I know I am being a noob at the moment and sorry for being a pain, but I really need to get my machine formatted or fixed!!!!
is there anyway i can at least format my disks thorugh this Ubuntu CD

I think you should try some other versions of linux in your machine too, or maybe some previous distributions of ubuntu as well....if you are trying to boot ubuntu 11.10, try burning 11.04 and run the livecd first. This is the reason why you should always select 'try ubuntu' option first before going to direct installation.

---

### Post by abhishek.purkayastha on 2012-02-11
Thanks for all ur replies. 
After I found that I could do nothing with my bootable dvds (ubuntu and win 7) except watching blue/purple screens for hours and hours i thought I would better format my drive and go for a fresh install. 
I got this really handy disk format tool(which has a whole lot of other options also), which comes with a bootable cd option from here 
[http://www.partitionwizard.com/download.html](http://www.partitionwizard.com/download.html)
 
I formatted my hard disk with this tool(without needing to boot any OS which is awesome) and did a fresh installation of Windows 7. So my machine is up and running again now.:D
Thanks again for taking the pain to reply to me questions.

---

### Post by Mark Phelps on 2012-02-11
It's great to see that you are up and running again.  Please use the Thread Tools at the top of the thread to mark this thread as SOLVED.  thanks

---

### Post by nipunshakya on 2012-02-11
Good to know that your machine is fine now....Goodluck

Happy linuxing

---

