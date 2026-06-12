---
title: "HOWTO: Compile Gnomad2-2.8.9 to use with Toshiba Gigabeat"
date: 2007-01-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Nick Rivers on 2007-01-20
I've been waiting to be able to use my Toshiba Gigabeat F40 with Linux for quite some time now and thanks to Gnomad2 that day has finally arrived.  Here is how I compiled Gnomad2-2.8.9 for Ubuntu Edgy to make things happen.

First, let's make sure you have the necessary tools to compile the source code:
```
sudo apt-get install build-essential gcc checkinstall
```

Now let's get Gnomad2 compiled and installed...

Install libmtp2 libmtp-dev libnjb-dev libid3tag0-dev libgnomeui-dev
```
sudo apt-get install libmtp2 libmtp-dev libnjb-dev libid3tag0-dev libgnomeui-dev
```

Download the source for Gnomad2-2.8.9 here: [http://sourceforge.net/project/showfiles.php?group_id=65573&package_id=63060&release_id=449092](http://sourceforge.net/project/showfiles.php?group_id=65573&package_id=63060&release_id=449092)

Extract the source package by right-clicking on it and selecting *Open with "Archive Manager"*

Move into the source directory:
```
cd /path/to/gnomad2-2.8.9
```

Configure the source code and set the install path to /usr instead of /usr/local :
```
./configure --prefix=/usr
```

Make the installation files:
```
make
```

Create the .deb of gnomad2 and install:
```
sudo checkinstall
```

When checkinstall prompts you just hit *Enter*

If everything went well, Gnomad2 is now installed and you can run it from your *Sound & Video* menu.  For some reason when starting/quitting Gnomad2 a dialogue pops up saying a camera has been detected.  If this happens to you just click the *Ignore* button.  Also, be aware that when you quit Gnomad2 it takes several seconds to shut down - the first time I quit the program I thought it had hung, but it apparently needs time to shut down properly.

If you have any questions or tips, please let me know.

---

### Post by trippinnik on 2007-02-23
I've got a Gigabeat and I compiled Gnomad and got the libmta, but the device isn't detected.  libmta doesn't seem to detect it either.  The model I have seems to only be available in Japan.  Which seems to be making it difficult to get a mp3 player that works with linux.  Any ideas how to get it to be detected my libmta? There's a command mta-hotplug that seems to lest a lot of different devices, is there anyway to add my device to that file?

---

