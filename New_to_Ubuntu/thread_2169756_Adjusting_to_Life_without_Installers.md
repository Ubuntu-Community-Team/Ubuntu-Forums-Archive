---
title: "Adjusting to Life without Installers"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by RangerK on 2013-08-23
So, if I go to download some software, here ([http://www.sublimetext.com/2](http://www.sublimetext.com/2)), for example.  

I download a folder full of files.  There's an executable that works as a stand-alone.

Is there a standard place in the Ubuntu file structure where I should put this folder?  What are some best practices?

Thanks!

---

### Post by tgalati4 on 2013-08-23
Put it in /tmp or make a directory in your home folder called Installs.  It doesn't matter, because the package management system will put the files in the correct place.  You can delete the installer file when you are done.

---

### Post by zealibib slaughter on 2013-08-23
I just unpack to my home directory then make a symbolic link to whichever  file that starts the program in /usr/local/bin/

example
```
sudo ln -s /home/user/myprogram/myprogram.sh /usr/local/bin
```

---

### Post by r_avital on 2013-08-23
RangerK,

Not sure what you mean by "folder full of files" but I went to the site you linked, found the Linux 64Bit version of the software available on that site, and clicked on it, and it gave me a download of a *.tar.bz archive.

Some best practices state you should unpack the archive in the /opt directory, then make a symbolic link to the executable, and the link should be in /usr/bin/ -- all this will require root privileges.  However, technically, you could unpack it anywhere you want, including a directory under your own home directory, and run the executable directly from there, it should function just as well.  You unpack it using the utility "archive manager" (the executable is file-roller from the terminal).

In any case, the package management system will be completely oblivious to it, since it's not technically-speaking a "package" (it's not a .deb file).  This only means that the package management system won't configure it or remove it for you, should you ever decide to remove it.

[Interesting tool, this Sublime Text, by the way, I might try it]

---

### Post by oldos2er on 2013-08-23
> **RangerK said:**
> So, if I go to download some software, here ([http://www.sublimetext.com/2](http://www.sublimetext.com/2)), for example.  

I download a folder full of files.  There's an executable that works as a stand-alone.

Is there a standard place in the Ubuntu file structure where I should put this folder?  What are some best practices?


webupd8.org maintains a PPA for Sublime Text: [http://www.webupd8.org/2013/07/sublime-text-3-ubuntu-ppa-now-available.html](http://www.webupd8.org/2013/07/sublime-text-3-ubuntu-ppa-now-available.html)

---

### Post by tgalati4 on 2013-08-23
My mistake.  I saw 32-bit and 64-bit and I just assumed *.deb files  or *.rpm files for linux.  So *r_avital* is correct, put the files in a consistent location.  /opt (for optional software) is often a place for such manually-installed programs.  But if a PPA is available, I would use that.

---

### Post by r_avital on 2013-08-23
> **oldos2er said:**
> webupd8.org maintains a PPA for Sublime Text: [http://www.webupd8.org/2013/07/sublime-text-3-ubuntu-ppa-now-available.html](http://www.webupd8.org/2013/07/sublime-text-3-ubuntu-ppa-now-available.html)

Well, that's good news, I was about to just unpack the tar.gz archive, but yes, a PPA is always preferable.

Just to clarify for the OP's benefit -- Ranger, either method is fine, but adding the PPA to your software sources (easily done in Synaptic) and installing from there, means that the Synaptic package manager will in fact install in directories determined by the software author, and provide info on updates when available.  That's one reason why it's the preferred method.

---

### Post by RangerK on 2013-08-24
Great advice.  Thank you!

I installed the PPA using the advice from here: [http://www.webupd8.org/2013/07/sublime-text-3-ubuntu-ppa-now-available.html](http://www.webupd8.org/2013/07/sublime-text-3-ubuntu-ppa-now-available.html)

Namely: 
> sudo add-apt-repository ppa:webupd8team/sublime-text-3
sudo apt-get update
sudo apt-get install sublime-text-installer

Then I found the executable file using

> 

sudo updatedb
locate sublime



Then I made a symbolic link using Zealibib's advice:

> 
sudo ln -s /opt/sublime_text/sublime_text /usr/local/bin


Am I correct in drawing a couple conclusions:

1. Instead of downloading and unpacking tar.bz files, look for a ppa when you want new software.  It makes more of the process, including future updates, automatic.

2. Making symbolic links in /usr/local/bin is a standard part of installing new software.

If anyone can recommend a simple tutorial that covers these issues, I'd love to go through it.

---

### Post by akoskm on 2013-08-24
I prefer the
```

/home/username/Applications/

```
structure when I have to install something that doesn't come with installer.

---

### Post by agillator on 2013-08-24
For what it may be (or may not be) worth, here is an explanation of the 'standard' file system hierarchy for Linux: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard). Is it followed? Wellllllllll . . . . . . , sometimes by some people. From what I have seen very few use /opt and /etc/opt, although some do. All the advice you received here is good, but I thought you might like to see the standard. In actual fact you can put a file anywhere. The only problem with putting it somewhere unusual is finding it later when you forget where you put it although there are several utilities that do a pretty good job of that. Also, as you discovered, packages for Linux tend to be pretty specific: 32 bit, 64 bit, etc. So when you look at an 'installation' directy somewhere you need to get the file for you, not all of them.

---

### Post by 3rdalbum on 2013-08-24
> **RangerK said:**
> 
Am I correct in drawing a couple conclusions:

1. Instead of downloading and unpacking tar.bz files, look for a ppa when you want new software.  It makes more of the process, including future updates, automatic.

Correct, a PPA or a third-party repository (basically the same thing) is the best thing to look for.

> 2. Making symbolic links in /usr/local/bin is a standard part of installing new software.

No, that's not standard at all. Usually, the program will elect to be installed into /usr/bin and will add a menu item to the Dash automatically. This does depend on whether the person who has packaged the program actually included the functions for this to happen, but usually they would. Adding a symbolic link to /usr/local/bin is very unusual for a program installed via PPA.

---

### Post by Zill on 2013-08-24
> **RangerK said:**
> Am I correct in drawing a couple conclusions:

1. Instead of downloading and unpacking tar.bz files, look for a ppa when you want new software.  It makes more of the process, including future updates, automatic.

2. Making symbolic links in /usr/local/bin is a standard part of installing new software.

If anyone can recommend a simple tutorial that covers these issues, I'd love to go through it.
Just in case you haven't already discovered that things are different with Linux, I suggest you read this:
[LIST][Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")[/LIST]

---

### Post by r_avital on 2013-08-24
> **RangerK said:**
> 
Am I correct in drawing a couple conclusions:

1. Instead of downloading and unpacking tar.bz files, look for a ppa when you want new software.  It makes more of the process, including future updates, automatic.

2. Making symbolic links in /usr/local/bin is a standard part of installing new software.
First, #2 above -- when you install a *.deb package, you dont' need to worry about making links.  My empirical observation is that more often than not, the installation process will put the actual executable in /usr/bin, which is a location that by default, is on the path for all users, so invoking it will always work.  In some cases, the installation will place a symbolic link in there for you, but the user doesn't need to worry about it.

For #1 above, that's is the preferred approach.  If you know what you're doing and have preferences, you may occasionally prefer the .tar.gz archive, and go with the manual process (unpack wherever you want, make a symbolic link in /usr/bin/).  For instance, I use the eclipse Java development environment.  There is a .*deb eclipse package provided by Ubuntu, you can install it right from Synaptic, no need to add a PPA, as it is a standard component of the Ubuntu distribution.  But it doesn't get updated as often as the publisher provides new versions, and I trust the publisher on the basis of working with their software for years now, so I prefer downloading a stable release from them, and going with the manual method.

Bear in mind, the other (great) advantage of sticking with the Synaptic method, is that since it's an approved repository, it greatly reduces the chances of malware infections.

---

