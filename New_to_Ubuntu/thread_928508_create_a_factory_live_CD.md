---
title: "create a factory live CD"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by MattThLinuxNewb on 2008-09-24
Hi,
I've searched google for the answer to this with no success. Here's my question: I upgraded from 7.10 -> 8.04 through the package manager. Is there any way I can generate a proper 8.04 live CD image from my installation (i.e. instead of downloading it)? I don't mean a custom live CD, I mean the standard one you'd get from downloading it straight from [http://www.ubuntu.com/](http://www.ubuntu.com/).
Thanks,
Matt

---

### Post by nowshining on 2008-09-24
more than likely no since u'd have custom installs of everything u've installed plus that and the stuff you removed - the updates would never install anything that was default on hardy if it were removed  even if they were the default on the official discs, etc,,and so forth...u would only get updated ones..

---

### Post by Paqman on 2008-09-24
You can't really create a pristine LiveCD like you'd get from the Ubuntu download servers, but you can create a customised one based on your own setup with [Remastersys](http://www.remastersys.klikit-linux.com/).

I've not actually used it though, maybe someone who has can tell you a bit more about it.

---

### Post by MattThLinuxNewb on 2008-09-24
Thanks for the quick replies. Ok, then I guess I'll have to download an image at some point :(
I was hoping there was some really obvious "Burn an Ubuntu Live CD" feature that I'd overlooked.

---

### Post by I wanted to leave on 2008-09-24
As Paqman said, you can use remastersys. It has options to burn a custom cd (as in identical to your current system), or you can burn a generic cd for further distribution or to install on other computers etc. Works flawlessly the times I've used it

---

### Post by robert shearer on 2008-09-24
Remastersys has two options

1) make a live cd backup of your installation with user data/settings

2) make a live cd distributable cd of your current install without any user info. This can be given to others as an install cd and will be as close to the standard cd as you make it. It will, however have all the apps and tweaks you have applied to your o/s since installing it (presumably those that you were using before you upgraded)

either way it won't work if you have a lot of user data or large apt/cache from downloaded apps.There is a limit to the compressed file and iso used to make the cd/dvd.

See these links for a fuller description...

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

and this from the Remastersys forum...

You can use Remastersys to backup a fully updated system.

  The key is to make sure your /home/(your_username) does not contain a lot of large files, such as MP-3s, videos, pictures, etc.
  Move all such files to a separate data partition, and you will find that your system easily compresses to a file size of less than 4 gigabytes.  Mine generally is just a bit over 1 gig. 
  Before Remastering your system, be sure to unmount any other partitions, except for your / and /home, unmount any mounted network drives, and unplug any USB thumb-drives or hard drives, otherwise, Remastersys will include those in the backup, making the ISO file too large.  

Also look for the following folder:  /var/cache/apt/archives.  That folder is where Klikit, (and presumably Ubuntu and other Ubuntu-based distros}, store the DEB files for all the programs installed on your system.  The DEB files are binary installers, and once the program is installed, they are no longer needed, unless you need to reinstall the program for some reason.  You can copy the entire folder to your storage partition, or use AptonCD to make a backup disk, then you can safely delete the contents of the original folder ( do a "sudo apt-get clean") , which can free up a half a Gigabyte or more.

---

### Post by nowshining on 2008-09-24
u could also order free cds from shipit.ubuntu.com, etc.. for kubuntu shipit.kubuntu.com, etc.. and so forth..

---

