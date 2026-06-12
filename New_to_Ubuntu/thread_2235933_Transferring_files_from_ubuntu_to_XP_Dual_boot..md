---
title: "Transferring files from ubuntu to XP Dual boot."
date: 2014-07-23
forum: New to Ubuntu
---

### Post by Eric_Feder on 2014-07-23
I have Windows XP, Word 2003, and Excel 2003. I am adept with these programs and don't wish to install Windows 7 or 8. I want to partition my hard drive and install Ubuntu so I can safely access the internet and email. I will boot both XP and Ubuntu. I understand that even just using outlook express to access email without even opening an attachment is a security risk.

My question is how files can be transferred from Ubuntu to XP. I saw a post about drag and drop available under the /media/ directory. But will it work for an executable file, or a file with an extension Ubuntu does not recognize? If not, how would I transfer the files?

I read that Ubuntu will recognize Word 2007 files. Can it recognize Word 2003 and Excel 2003?

I assume that there is no problem downloading an saving a file in Ubuntu with file with an extension Ubuntu does not recognize, which can be transferred to XP which will recognize the file. I have a number of programs that create files with their own unique file extensions.

Thank you

---

### Post by whitesmith on 2014-07-23
> **Eric_Feder said:**
> My question is how files can be transferred from Ubuntu to XP. I saw a post about drag and drop available under the /media/ directory. But will it work for an executable file, or a file with an extension Ubuntu does not recognize? If not, how would I transfer the files?I read that Ubuntu will recognize Word 2007 files. Can it recognize Word 2003 and Excel 2003?
Ubuntu can read Windows files irrespective of extension. Windows executables won't run in Ubuntu (or any other Linux) except under something similar to Wine. All Windows files can be read by Ubuntu.

---

### Post by coldcritter64 on 2014-07-23
> **Eric_Feder said:**
> ...
My question is how files can be transferred from Ubuntu to XP. I saw a post about drag and drop available under the /media/ directory. But will it work for an executable file, or a file with an extension Ubuntu does not recognize?
...
The XP partition can be accessed directly as you note mounted in /media. Easy access/mounting is available directly in the Nautilus file manager itself in the sidebar by clicking the XP entry there.

Linux recognises files by their mimetype not by the extension like windows does. You can drag and drop any file onto the Ubuntu filesystem irrespective of extension and return them to XP later for use (but only from Ubuntu, Windows doesn't recognise Linux filesystems). 

Any that are recognised (by their mimetype not extension) can then be opened in Ubuntu. Windows executables won't run under Ubuntu unless run in Wine, a code compatibility layer.

---

### Post by Mark Phelps on 2014-07-23
If your plan, which I'm guessing from your comments, is to use Linux to do the downloads (therby avoiding the malware problems of Windows) and then transferring everything you download to Windows, a way to make that easier is to use a dual-pane file manager.  I strongly recommend Gnome-Commander.

If you install this, then mount the Windows partition you want to receive the files, you can have the Linux directory in the left pane, the Windows directory in the right pane and just drag and drop files from the left to the right.

Don't worry about the file extensions -- Linux doesn't actually use them.

---

### Post by Bucky Ball on 2014-07-23
Something to remember is just because Ubuntu won't get infected by a virus or trojan designed for XP, if it downloads a file containing one then passes it on to the Windows side, all is lost anyway. You still need to be careful about what you download and dump to Windows. It is a sitting duck. An infected email attachment downloaded on Ubuntu then dumped to a Windows partition is still an infected email attachment, regardless of whether you downloaded it in Windows or Ubuntu. ;)

---

### Post by Eric_Feder on 2014-07-23
That is exactly what I want to do. Thank for the suggestion to use Gnome-Commander. It sounds simple and easy to use.

---

### Post by Eric_Feder on 2014-07-23
Yes, I am aware of that. I try not to open an unknown download, but in the past I had a horrible infection from Advanced Care Systems, supposedly an advanced hueristic antivirus program. The Bleeping Computer folks bailed me out. I assume I can right click a downloaded file I transferred to XP and check scan it with Norton 360 to check for viruses before opening. But perhaps there are files that execute automatically without even opening them.

Thank you.

---

### Post by coldcritter64 on 2014-07-23
> **Eric_Feder said:**
> Yes, I am aware of that. I try not to open an unknown download, but in the past I had a horrible infection from Advanced Care Systems, supposedly an advanced hueristic antivirus program. The Bleeping Computer folks bailed me out. I assume I can right click a downloaded file I transferred to XP and check scan it with Norton 360 to check for viruses before opening. But perhaps there are files that execute automatically without even opening them.

Thank you.

I would suggest rather than transferring the file to XP then scanning with Norton to actually install an "on demand" scanner like Avast for Linux (IN LINUX) and manually scan BEFORE transferring the files to XP. 

If you keep XP offline you won't be able to update Norton and your Windows antivirus scanner will be way out of date for definitions leaving you wide open to infection from newer nasties.

Keep Avast (or a similar AV for Linux) updated in Linux, manually scan any files to be passed to XP before using them, note antivirus programs in Linux generally don't have a "resident shield" like you would normally expect in Windows they are mostly "on demand" scanners for manual scanning for Windows viruses. Although there are some viruses for Linux, NO viruses exist "in the wild" for Linux hence a resident shield is pretty much a waste of resources and is not needed.

Good luck.

---

### Post by bigmonmulgrew on 2014-07-24
As far as opening file types goes the way Windows and Linux works out what to do with the file is different. Windows reads the file extension eg .exe which tells it what to do with the file. Linux ignores the file extension and reads the properties inside the file to determine what to do with it. You could name a word file my-letter.exe and Ubuntu would still open it in a text editor. Windows would just give you an error that there's something wrong with the exe.

As far as sharing files is concerned heres how I used to do it

I had 3 partitions  (could also be seperate drives)
Partition 1 Windows XP
Partition 2 Ubuntu
Partition 3 Storage

In Windows right click your my documents folder and you can change the location to a folder in the storage drive.
The in Ubuntu you do the same thing, moving your files to the same folder in the storage drive.

This will mean anything you place in your ubuntu documents folder will automatically appear in your windows documents folder. Anything you place in your windows My Documents will automatically be in your ubuntu documents.

All you are doing here is moving the Windows "My Documents" and Linux "Home" directories to point to the same folder on a drive they can both access rather than using the default locations.

Back when I first did this you had to install something to get Ubuntu to read NTFS drives but I think its included these days. I was on ubuntu 7.04 back then. I don't use the desktop variant of Ubuntu these days so sorry I can't be more specific with instructions. I'm sure one of the up to date guys on here could give you a step by step if this is what you want to do.

---

### Post by mastablasta on 2014-07-24
do not use outlook express. use thunderbird instead.

Word 2003, Excel 2003 work well in wine (have a look at playonlinux) eventhough they have silver rating. Word, Excel and Powerpoint 2007 also work almost perfectly in wine (some minor issue with function that are not present in 2003 version). 
default Ubuntu's Libre office can read word 2003 and excel 2003 files well. it also has similar look and feel to office 2003 but is way more advanced underneath.
there is also Caligra Office new and under development. But made to be easy with basic functions users mostly need.
There is also WPS office (Kingsoft office). A Chinese made office compatible with MS office.

So many alternatives available for your need. So are you sure you actually need windows XP. 

Also windows XP is still getting malware removal tool updates until 2017. it might be good to keep it updated afterall. Comodo (or Zonealarm) free firewall and some good antivirus scanner might also help protect it a bit.

---

### Post by Eric_Feder on 2014-07-24
I thank everyone for your help. I think I am all set. Now if I can keep from blowing up XP and all the programs that are installed when I add a partition and install Ubuntu ... (I found some good tutorials)

---

