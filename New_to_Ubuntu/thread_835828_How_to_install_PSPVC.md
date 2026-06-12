---
title: "How to install PSPVC?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Famicommander on 2008-06-20
Can someone give me a simple, step-by-step guide for how to install PSPVC in Xubuntu 8.04 32 bit?

Thanks in advance.

---

### Post by Famicommander on 2008-06-20
So then I'm the only Ubuntu user in the world with a PSP?

I somehow find that hard to believe.

---

### Post by cariboo on 2008-06-21
Sometimes it takes a while for someone to read the post. Which version are up trying to install the Windows version or the Linux version.

Jim

---

### Post by azurepancake on 2008-06-21
Okay, go to this following website [http://sourceforge.net/project/downloading.php?group_id=158921&use_mirror=internap&filename=pspvc-install-0.3.tar.gz&8764884/](http://sourceforge.net/project/downloading.php?group_id=158921&use_mirror=internap&filename=pspvc-install-0.3.tar.gz&8764884/) to download the tar.gz file.

If the file downloads to your desktop, move it to your '/home/user' directory (replacing "user" with your username of course). Open up a terminal session, check that your in your home directory and type..

```
tar zxfv pspvc-install-0.3.tar.gz
```

This will decompress and create the directory "pspvc-install-0.3" in your users home directory. According to the README inside the directory, the program relies on the following dependencies..

- nasm
- libfaac
- liba52
- libxvidcore
- gtk+2.0 

So then copy & paste the following command into the terminal to download and install them..

```
sudo apt-get install nasm liba52-0.7.4 libfaac0 libfaac-dev libxvidcore4 libxvidcore4-dev libgtk2.0-dev
```

Then navigate to the pspvc-install-0.3 directory.. (replace "user" with your username)

```
cd /home/user/pspvc-install-0.3
```

and type.. 

```
sudo sh install.sh
```

It should then begin the install process. The install took between 3-5 minutes. The installation output is ugly, don't worry too much about it unless the program does not start. Once it is complete type.. 

```
pspvc
``` 

..into the terminal and it should open. 

Good luck, let me know how it goes!

---

### Post by lingenfr on 2008-11-02
Very helpful. I couldn't figure out how to do the thanks thing, but thanks.

---

### Post by XaversPSP on 2009-11-04
I can't open the application someone please help!!

---

### Post by Hey Gary on 2010-02-20
I was able to follow the above instructions and get PSPVC loaded and running on my 9.10 Ubuntu install.  It converted my test case very well and I played it on the PSP.   I used to use 3GP_converter, which sometimes would mess up the sync between video and voice.  The test case was a success where 3GP was not.

I first opened a terminal window and ran the tool, there are warnings but it works (just like warnings during the build).  The command is "pspvc".  I then did a system -> preferences -> Main Menu and created a new menu item to launch from the menu instead of the command line.

Later I noticed the installer (or something) created the menu item for me in Sound & Video menu.

Thanks for the help in getting this to work.

---

### Post by Paul T. on 2010-07-20
I tried to install pspvc in Ubuntu 10.04 using the above instructions, however I was getting an error when trying to install the dependencies;

"E: Couldn't find package libxvidcore4-dev"

I found out that it should be libxvidcore-dev NOT libxvidcore4-dev.
Don't know if this is specific to 10.04 but it works! :p

---

