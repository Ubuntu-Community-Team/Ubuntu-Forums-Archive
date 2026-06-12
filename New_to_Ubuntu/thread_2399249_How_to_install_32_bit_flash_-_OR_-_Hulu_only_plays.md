---
title: "How to install 32 bit flash? - OR - Hulu only plays commercials not programs"
date: 2018-08-23
forum: New to Ubuntu
---

### Post by lionrhod on 2018-08-23
Just installed Ubuntu on my computer and I can't make Hulu work in Firefox. It will only play the commercials but when the program SHOULD come on, it loads a gray-black screen and does nothing.

(My now deceased Win 8 laptop had the same problem, which I fixed by going back to a previous save. Can't do that here since my comp is a new build.)

This post, describing the same exact problem: [https://ubuntuforums.org/showthread.php?t=1490837](https://ubuntuforums.org/showthread.php?t=1490837) says I need to uninstall Flash 64 bit and then install Flash 32 bit. Problem is, it doesn't say 
HOW to do that, and the only info I could find on how-to was a video in German.

Thanks much for your help!

---

### Post by Holger_Gehrke on 2018-08-23
Not a Hulu subscriber, but their FAQ lists two options for viewing in a browser, hulu.com and new.hulu.com. The latter isn't supposed to use flash at all, according the FAQ.

Holger

---

### Post by monkeybrain20122 on 2018-08-23
> **lionrhod said:**
> Just installed Ubuntu on my computer and I can't make Hulu work in Firefox. It will only play the commercials but when the program SHOULD come on, it loads a gray-black screen and does nothing.

(My now deceased Win 8 laptop had the same problem, which I fixed by going back to a previous save. Can't do that here since my comp is a new build.)

This post, describing the same exact problem: [https://ubuntuforums.org/showthread.php?t=1490837](https://ubuntuforums.org/showthread.php?t=1490837) says I need to uninstall Flash 64 bit and then install Flash 32 bit. Problem is, it doesn't say 
HOW to do that, and the only info I could find on how-to was a video in German.

Thanks much for your help!

Most likely because  flash for Linux desktop doesn't play drmed content rather than needing 32 bit. That link you provided is very old and the info is likely outdated. See post 17 and 18 of this[ thread]("https://ubuntuforums.org/showthread.php?t=2363550&page=2").

Edited: Just saw the post above, if you can access without flash this would be the best, flash is dying a long agonizing death these days. I wouldn't even install it unless you use some legacy sites.

---

### Post by oldos2er on 2018-08-24
Did you enable DRM content in Preferences? Which version of firefox and Ubuntu are you using? Is ubuntu-restricted-extras installed?

---

### Post by lionrhod on 2018-08-29
with new.hulu.com, I can't watch commercial, and the program itself shows as an "Error 5003" which seems to be an error code related to Apple TV and Playstation. Thanks for the idea, though!

---

### Post by lionrhod on 2018-08-29
I tried following posts 17 and 18, but got lost in miliseconds. What is pepperflash? How do I install chrome?  What are the commands I need to do any of this, and where do I find the programs? Almost anything I find references windows, not unbuntu.

Apologies, but I'm so new to linux/unbuntu that I am clueless.

---

### Post by lionrhod on 2018-08-29
I enabled DRM content in preferences.

I am using Firefox 61.0.1 64 bit. Ubuntu 18.04.1 LTS. I tried figuring out how to install the "restricted extras" and I got some sort of message about fonts. I have absolutely no idea what that is or how to find out if it's installed already.

Also, I installed Chromium and that wants me to install flash all over again, even though it's been installed at least 3 or 4 times.

Of course I've also contacted Hulu support. Their folks doen't even know what Linux IS.

Thanks everyone!

---

### Post by oldos2er on 2018-08-29
The ubuntu-restricted-extras package includes ttf-mscorefonts-installer, its EULA appears in a terminal and you must agree to it before the package can be successfully installed. Run ```
sudo dpkg --configure -a
```, watch for the terminal, then press Tab to select "OK" and Enter to agree. Once that's done, restart Firefox, and try hulu again.

I just watched the opening bit of 'Castle Rock' on hulu, and it works. I'm using Xubuntu 18.04 and Firefox 61.0.1, same as you.

---

### Post by lionrhod on 2018-09-08
Tried this and got the following:

kent@kent-MS-7641:~$ sudo dpkg --configure -a
[sudo] password for kent: 
Sorry, try again.
[sudo] password for kent: 
Setting up libmspack0:amd64 (0.6-3ubuntu0.1) ...
Setting up cabextract (1.6-1.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up chromium-codecs-ffmpeg-extra (68.0.3440.106-0ubuntu0.18.04.1) ...
Setting up libopencore-amrnb0:amd64 (0.1.3-2.1) ...
Processing triggers for man-db (2.8.3-2) ...
Setting up libopencore-amrwb0:amd64 (0.1.3-2.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
kent@kent-MS-7641:~$ 


Nothing came up where I could tab to an "Okay"

Restarted Firefox but no improvement.

Thanks!

---

### Post by jimmy-frydkaer on 2018-09-08
```
sudo apt install ubuntu-restricted-extras
``` 

In a terminal will give you what you need to install restricted extras

---

