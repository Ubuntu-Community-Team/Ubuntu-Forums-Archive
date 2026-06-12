---
title: "Writing Data on an NTFS Drive"
date: 2014-11-21
forum: New to Ubuntu
---

### Post by Ubultron on 2014-11-21
Hi again guys. I know that it's safe to both read and write data on an NTFS partition (or external hard drive, for that matter), but when I was reading about it on a thread a few weeks ago, they mentioned something regarding an incompatibility problem with file name permissions on Windows. My PC has Ubuntu installed now, but I have an NTFS partition, and all of my external hard drives are also NTFS. Does it mean that everything I save on my external HDDs won't be readable once I plug them into a Windows computer? Because if so, that will be a bit of a problem for me, as I do need to share the files with a friend whose computer is Windows-only.

I'm a total n00b when it comes to this stuff, so I apologize if this isn't even the case, haha. Further clarification on the matter would be greatly appreciated, though!

---

### Post by yancek on 2014-11-21
>  Does it mean that everything I save on my external HDDs won't be readable once I plug them into a Windows computer? 

No.  There may be problems with some text files due to differences in line endings.  I think you would need to be more specific about the type of files you will be sharing.  Linux and windows file permissions are different.  You might post a link to the forum or more details for a detailed explanation from someone.

---

### Post by Ubultron on 2014-11-21
> **yancek said:**
> No.  There may be problems with some text files due to differences in line endings.  I think you would need to be more specific about the type of files you will be sharing.  Linux and windows file permissions are different.  You might post a link to the forum or more details for a detailed explanation from someone.
I wanted to post a link to the thread I'm referring to, but I couldn't find it. It was a few weeks ago, and just randomly found it on a google search when I was googling to see if there were no problems with writing data to NTFS partitions. Someone mentioned that other than file name permissions, it was safe. They didn't go into detail about it, though.

Picture, and video files make the bulk of what I need to share with a Windows computer. As far as text files go, I have a couple of .txt and PDF files, and a bunch of LibreOffice documents (since I used LibreOffice even during my Windows days). Videos, pictures, and the PDF documents are all I'm concerned about, really.

---

### Post by bilkay on 2014-11-21
I've never had a problem with putting files on an NTFS partition. Text files can be converted with to DOS format with the unix2dos utility which can convert both ways.

---

### Post by oldfred on 2014-11-21
If you have a permanent mount in fstab, be sure to include the windows_names option.
Most do not use these chars, so not usually an issue.

 For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

And do not hibernate in Windows or you will lose anything you write from Ubuntu as the hibernation restores to to as before you wrote anything.

---

### Post by ajgreeny on 2014-11-21
A final point to bear in mind; if you have files in a folder on a Linux filesystem called file.txt, File.txt, FILE.TXT they will live side by side with no difficulty.
If you transfer them to an ntfs partition you will have big problems as they will all be thought to be the same file; Linux is case sensitive, Windows, and ntfs is not.

---

### Post by Ubultron on 2014-11-21
> **oldfred said:**
> If you have a permanent mount in fstab, be sure to include the windows_names option.
Most do not use these chars, so not usually an issue.

For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

And do not hibernate in Windows or you will lose anything you write from Ubuntu as the hibernation restores to to as before you wrote anything.
Oh, gotcha! So basically, this problem would only arise with file names containing those nine characters, yes? Also, what do you mean a code of less than 0x20? I don't know what that is, haha, so forgive my ignorance. And thanks for the hibernation heads-up; they definitely didn't mention that in the thread I had stumbled upon.

> **ajgreeny said:**
> A final point to bear in mind; if you have files in a folder on a Linux filesystem called file.txt, File.txt, FILE.TXT they will live side by side with no difficulty.
If you transfer them to an ntfs partition you will have big problems as they will all be thought to be the same file; Linux is case sensitive, Windows, and ntfs is not.
Ah, that's a good point. Thank you so much!

---

### Post by ofnuts on 2014-11-21
> **Ubultron said:**
> they mentioned something regarding an incompatibility problem with file name permissions on Windows

AFAIk the main incompatibility regarding file permissions is that Windows has no support for the "execute" flag. AFAIK the NTFS behaves as it it were always set for directories, and has an option to set it by default or not for files. There may be an option to use the Windows archive flag for this, too.

This is mostly something to think about if you keep Linux executables (binaries or scripts) on the NTFS partitions.

---

