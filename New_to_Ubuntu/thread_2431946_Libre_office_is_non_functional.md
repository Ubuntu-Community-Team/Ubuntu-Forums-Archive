---
title: "Libre office is non functional"
date: 2019-11-24
forum: New to Ubuntu
---

### Post by thunderchild2 on 2019-11-24
I have installed libre office through Ubuntu software but it is incabable of opening open document files or MS office files. As such it's completely useless and quite the headache. I can't figure out how to just install a downloaded copy from their site so i am a sitting duck. I get told that the files are corrupt and urecoverable when they work fine in libre office on windows.

---

### Post by Impavidus on 2019-11-24
So LibreOffice actually opens the file, but fails to display it? As opposed to complaining it cannot find the file or has no permission to open it. That's weird.

Can you tell us which version of LibreOffice and which version of Ubuntu you use? And how do you transfer the file from Windows to Ubuntu? Can LibreOffice on Windows still open the file after you transfer the file back to Windows? Which version of LibreOffice do you use on Windows?

---

### Post by thunderchild2 on 2019-11-24
I'm confused, now libre office seems to not be installed at all.

---

### Post by thunderchild2 on 2019-11-24
Libre office 6 is installed via ubuntu software apparently with an open format file it crashes but then the generic libre office opens but not the program that would actually open the file. If i try am MS file it says it is corrupt.

---

### Post by thunderchild2 on 2019-11-24
On windows I use 6.3.0.4

---

### Post by thunderchild2 on 2019-11-24
The files are on a portable hard drive.

---

### Post by thunderchild2 on 2019-11-24
If i open from libre office it works but libre office cannot see my external hard drive.

---

### Post by thunderchild2 on 2019-11-24
so if i open my spreadsheet with calc it works. But if i just send it to libre office it does not work.

---

### Post by CatKiller on 2019-11-24
Do you think you've installed the snap version? They are limited in where they can read or write compared to a traditional package.

---

### Post by Impavidus on 2019-11-25
There are multiple types of packaging of software for Ubuntu. There are the traditional deb packages and the newer snap packages, which I avoid. The snap packages get sandboxed for security and cannot access your external hard drive. It will tell you it cannot find the file or has no permission to open it, but not that it's corrupt. If you use the snap version, you can use the file manager to first copy the file from your external drive to your Documents folder.

If you use the traditional deb packages and don't use a PPA to get the latest version of LibreOffice, the version of LibreOffice you get depends on the version of Ubuntu you run. For the currently supported versions of Ubuntu, that could be 5.1.6, 6.0.7, 6.2.8 or 6.3.2. When you open a file from a newer version of LibreOffice in an older version, it may not understand the file format and get confused, but I expect that to be more like some unsupported features than like no functionality at all.

When you unplug the external hard drive from the computer, do you first safely remove it? If you don't, the file may not have fully transferred to (or from) the external drive. Don't rely on progress indicators during the file copy. They tell you when the file manager has copied the file, not when the operating system has flushed all buffers.

Look at the file using the file managers on Ubuntu and Windows. Are the files the exact same size in bytes? You can also check the md5sum. [This guide](https://help.ubuntu.com/community/HowToMD5SUM) tells how to check the md5sum of Ubuntu live images, but it works the same for any file.

I want to know if there's a problem with LibreOffice on Ubuntu, a problem with your understanding of Ubuntu or the files really get corrupted.

---

### Post by speartip on 2019-11-25
Just going back to your original post, you say "[COLOR=#000000]I have installed libre office through Ubuntu software" and yet LibreOffice is already install by default on all Ubuntu Distros. Probably best if you give more information on your installation.

[/COLOR]

---

### Post by uRock on 2019-11-25
If you search LibreOffice as one word, then you'll see it listed twice. Open each one and look at the Source. One is Listed as Snap Store, do not use this version as it is NOT fully functional. The one listed as ubuntu-bionic-updates-main is the one that is fully functional and usually installed by default. If you're on a newer 19.04 or 19.10, then it will have that release name, instead of "bionic" in it.

---

### Post by uRock on 2019-11-25
If you search Libre Office as two words, then you will ONLY see the Snap package.

---

### Post by deadflowr on 2019-11-25
> **speartip said:**
> Just going back to your original post, you say "[COLOR=#000000]I have installed libre office through Ubuntu software" and yet LibreOffice is already install by default on all Ubuntu Distros. Probably best if you give more information on your installation.

[/COLOR]

Not sure it's installed if the install is the minimal option.
That option is available (on the Desktop edition installer, btw) during installation and it cuts out a whole bunch of stuff.

---

### Post by uRock on 2019-11-25
I just booted 19.10 and the Snap is not available in the Software Store. I think the devs noticed the handicaps of the Snap version.

---

### Post by rbmorse on 2019-11-25
> **deadflowr said:**
> Not sure it's installed if the install is the minimal option.
That option is available (on the Desktop edition installer, btw) during installation and it cuts out a whole bunch of stuff.

I can confirm that libreoffice is not installed with the minimal option.

---

