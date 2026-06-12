---
title: "How 2 Run Application as Root without Sudo?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by GregA on 2008-05-15
Am wanting to Install "SeaMonkey" per the following instructions from Mozilla.Org:  note step 1 re running as root to enable proper multi-user setup, but not using "sudo" . . . I can't picture how to do this in Ubuntu . . advice appreciated.

************************************************************************

To install SeaMonkey by downloading the SeaMonkey installer, follow these steps:

1. Create a directory named seamonkey (mkdir seamonkey) and change to that directory (cd seamonkey).
Note: If you install in the default directory (which is usually /usr/local/seamonkey), or any other directory where only the root user normally has write-access, you must start SeaMonkey first as root before other users can start the program. Doing so generates a set of files required for later use by other users.  However, do not use sudo to run the installer as root because that can damage your profile.
	
2. Click the link on the site you're downloading SeaMonkey from to download the installer file (called seamonkey-x.xx.en-US.linux-i686.installer.tar.gz or similar) to your machine.

3. Change to the seamonkey directory (cd seamonkey) and decompress the archive with the following command:

  tar zxvf sea*.tar.gz

The installer is now located in a subdirectory of seamonkey named seamonkey-installer.

4. Change to the seamonkey-installer directory (cd seamonkey-installer) and run the installer with the ./seamonkey-installer command.

5. Follow the instructions in the install wizard for installing SeaMonkey.

---

### Post by kestrel1 on 2008-05-15
Ignore me. wrong post

---

### Post by rlsharpton on 2008-05-15
in termianl window type

sudo passwd root

enter a password

then type su

you should notice that your prompt will change from a $ to a #
however, enabling the root account is a security risk, that may not be a big deal or a huge deal depending on what you are using your ubuntu box for...
however with all that said if you sudo ./seamonkey... then it will work as well as if you su and run as root, hope this helps

---

### Post by GregA on 2008-05-15
If - for installation purposes, I temporarily disable sudo, and assign a persistent password to root, how do I re-enable sudo?   From the way I read Mozilla's instructions, yes, SeaMonkey will run fine using sudo ./seamonkey, but the multi-user files are not written.  Is this true?  yes/no . . . . anyone, anyone?

---

### Post by rlsharpton on 2008-05-15
here is a good article on the whole issue:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

you would disable su after enabling by typing this in a terminal window:
sudo passwd -l root

---

### Post by mbarak on 2008-05-15
> **rlsharpton said:**
> in termianl window type

sudo passwd root

enter a password

then type su

you should notice that your prompt will change from a $ to a #
however, enabling the root account is a security risk, that may not be a big deal or a huge deal depending on what you are using your ubuntu box for...
however with all that said if you sudo ./seamonkey... then it will work as well as if you su and run as root, hope this helps

You do not need to enable the root account to use a root terminal
just enter:
```
sudo -i
```
This will give you a root console without disabling sudo at all
I think that's what you should do, although I don't see why running seamonkey with sudo should affect the installation?

---

### Post by philinux on 2008-05-15
Have you checked in synaptic, it's in the universe repo.

---

### Post by GregA on 2008-05-15
Thanks everyone, I needed to make sure multiple users could run the latest secure SeaMonkey (1.19), with all plugins enabled, and dynamic profile manager working.   Running as root terminal sounds the way to go.

PS - - just checked in Synaptic, and Ubuntu (Hardy) is up-to-date with offering SeaMonkey 1.19 (I'll check Synaptic first in the future, Ubuntu is more up to date than Mepis/etch) - - thanks for the info PhiLinux.

---

### Post by bodhi.zazen on 2008-05-15
You can set the SUID :

[http://www.homepage.montana.edu/~unixuser/051602/SUID.html](http://www.homepage.montana.edu/~unixuser/051602/SUID.html)

[http://www.samag.com/documents/s=1149/sam0106a/0106a.htm](http://www.samag.com/documents/s=1149/sam0106a/0106a.htm)

Or set sudo to run the script w/o a password, then set an alias or launcher.

Or you can use expect.

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

    [http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

Last you can feed the password from a file or on the command line.

All of these options have some risk associated with them.

---

### Post by ubuntu-freak on 2008-05-15
Would "gksudo" not be safe? Hmm...

Nathan

---

