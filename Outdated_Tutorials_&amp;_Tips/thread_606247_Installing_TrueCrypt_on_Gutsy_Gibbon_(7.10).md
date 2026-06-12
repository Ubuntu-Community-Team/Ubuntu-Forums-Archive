---
title: "Installing TrueCrypt on Gutsy Gibbon (7.10)"
date: 2007-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by flickerfly on 2007-11-07
[COLOR="Red"]**WARNING:**[/COLOR] It appears that these directions don't work for the Kubuntu. It isn't clear why, but the kernel module doesn't seem to load properly. This may require the compilation of a custom kernel. If you figure it out, please post below how you did it.

I found the information on the forums a bit scattered and/or outdated so I was encouraged to write up a quick post to inform others who might be searching for the same information I was how to do so quickly.

If you would like to get TrueCrypt install on Gutsy, the good folks over at the TrueCrypt website have made it pretty easy. If it was in the repositories it would be even easier, but this is about as close as it gets. No totally anonymous packages or fresh compiles against kernel source...

Simply visit [http://www.truecrypt.org/downloads.php]("http://www.truecrypt.org/downloads.php") and select the appropriate 7.10 package from the dropdown box and run it. It will open in a package manager you may or may not be familiar with. In this it is as simple as clicking Install and following the directions. You'll probably have to put you password in, then it may need to install some dependencies, but the beauty of apt is that it will handle that for you.

That's it.
:guitar:

---

### Post by grkravi on 2007-11-12
This is not working for me. Truecrypt is installing but trying to mount the encrypted volume in kubuntu gutsy is throwing this error:

insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.22.ko': -1 Unknown symbol in module
FATAL: Error inserting truecrypt (/lib/modules/2.6.22-14-386/extra/truecrypt.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Failed to load TrueCrypt kernel module

---

### Post by flickerfly on 2007-11-12
Does Kubuntu use the same kernel as Ubuntu? Looks like trouble loading the kernel module.

---

### Post by NIT006.5 on 2007-11-15
Yep, solved the problem for me and saved me a lot of time.

Thanks very much :)

---

### Post by flickerfly on 2007-11-15
> **NIT006.5 said:**
> Yep, solved the problem for me and saved me a lot of time.

Thanks very much :)

Glad I could help.

---

### Post by Shai Hulud on 2007-11-16
insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.22.ko': -1 Invalid module format
FATAL: Module truecrypt not found.
Failed to load TrueCrypt kernel module

This is on my Ubuntu with KDE machine :/

Could you please write, how did you've solved the problem?

This update gave me so much headaches :(

---

### Post by flickerfly on 2007-11-16
The only thing I can think of to try is compiling your own kernel. Does Kubuntu have a different kernel than Ubuntu?

---

### Post by Shai Hulud on 2007-11-16
I don't think so...

Hmmm... I will register on the TC forum later to see if there is a solution there.

Thanks :)

---

### Post by Haywood on 2007-11-16
Does this only run in the command line version or is there a GUI as in the (forgive me) Windows version?

---

### Post by MaSJaNz on 2007-11-17
for me ( Kubuntu 7.10 ) it works perfectly! I have downloaded and installed .deb-package from TC-website and it works...

---

### Post by flickerfly on 2007-11-17
> **Haywood said:**
> Does this only run in the command line version or is there a GUI as in the (forgive me) Windows version?

There are some separately developed GUI s available. I've not used them, but search the forums for EasyCrypt and I think you'll find the one that looks simplest.

---

### Post by Shai Hulud on 2007-11-18
> **MaSJaNz said:**
> for me ( Kubuntu 7.10 ) it works perfectly! I have downloaded and installed .deb-package from TC-website and it works...

I think you got lucky :P

---

### Post by zybrid on 2007-11-18
Works fine, very easy.

Though i miss a GUI and a truecrypt icon on the application menu. :/

---

### Post by Shai Hulud on 2007-11-19
Well... i've made myself a file with

```
truecrypt -u /path/to/truecrypt/volume /path/to/mount
```

and it's nothing more than "sh mnt" in the console (yakuake ftw). After that you just type the passwords, and voila :)

Edit:

After reading a thread in the TC forums, i think that the .deb package for 7.10 works only on freshly installed Gutsy, but not on upgraded one. If you have upgraded to Gutsy, you should compile TC for yourself.

This is a very nice guide: [http://www.howtogeek.com/howto/ubuntu/install-truecrypt-on-ubuntu-edgy/](http://www.howtogeek.com/howto/ubuntu/install-truecrypt-on-ubuntu-edgy/)

---

### Post by Palmyra on 2007-12-16
> **grkravi said:**
> 
FATAL: Error inserting truecrypt (/lib/modules/2.6.22-14-386/extra/truecrypt.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Failed to load TrueCrypt kernel module

I had this same error, but on Gnome.  I went to the Truecrypt website as directed, and downloaded the Gutsy file.  The .deb file told me it was already installed, so I selected "reinstall."  That error is now gone, but Truecrypt via the terminal gave me an error (a different error).  Forcefield worked as it should.

---

### Post by Francewhoa on 2008-12-27
Another how-to install TrueCrypt [guide here]("http://www.randyjensenonline.com/blog/installing-truecrypt-51a-on-ubuntu-804"). Great for absolute beginners. It worked with Ubuntu Desktop 8.04.1 and TrueCrypt version 5.1a or 6.1a.

---

