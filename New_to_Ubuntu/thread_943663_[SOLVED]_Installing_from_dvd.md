---
title: "[SOLVED] Installing from dvd"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by crawling_warpig on 2008-10-10
I am new to Ubuntu (and Linux in general) and I was wondering if you guys could help me.

I'm trying to install a program from a dvd. There's an install file and when I open it, it starts up but then I get a message saying that I must be logged on as a super user.

I've had a search through the forum and many people have said about the 
```
sudo dpkg --configure -a
```
I have put this into the terminal and then input my password but I still can't install the program as it still says that I'm not logged in as a superuser.

I guess i must be missing something out....

Thanks

---

### Post by aeiah on 2008-10-10
what kind of file is on the dvd? the dpgk program (as far as i know) only works with .deb files

what is the name of the file you're trying to install, and must you install it from the dvd?

---

### Post by jamesrl on 2008-10-10
sudo being written before a command, runs it as a superuser.  It means Super User DO, that is super user do the following command (and prompts you for your normal password).

So what you probably want to do, is go to the directory with the install file, and 
run
```
sudo ./install.sh
```
or whatever the name of the installation script is.

If you prefer using nautilus (the graphical file browser) to changing directories manually from the terminal, you can run (Alt-F2)
```

gksudo nautilus
```
which will run the graphical file browser as root (gksudo is the same as sudo except with a graphical rather than terminal text prompt) and find the cd-rom, and the install file.

---

### Post by crawling_warpig on 2008-10-10
I'm not sure about either to be honest.

For the file, I'm not sure what type it is. It's just called 'INSTALL' when I go to properties then under MIME type it says text/x-install. Not sure if that'll help or not.

I am used to the windows way of opening the file and then just going through the install that way so I don't really know much about alternate ways to install in Linux

(Thanks for the quick responces by the way!)

---

### Post by aeiah on 2008-10-10
well this method you're describing kinda makes sense.. its not the prettiest way of installing programs but i guess since its on a dvd they've gone down that method because its kinda universal no matter what distribution of linux you're using.

right, you'll need to use the terminal (menu > accessories > terminal )

when it opens, its current location will be your home directory. you'll need to navigate to your dvd directory before you can run the install script that's on it.

```
cd /media/cdrom
```

that will cd (change directory) to your cd rom drive. now if the install script is in the root of this drive (ie, not in a folder) then you can simply type 
```

sudo ./INSTALL

```
the ./ bit basically means "run this program from this specific location im in right now". sudo means "super user do" and basically grants you super user rights for that particular command (once you've typed in your password). if the INSTALL file is in a directory, you'll have to cd to that directory before doing sudo ./INSTALL...
```

cd directory

```


if cd /media/cdrom does work, it'll be because your cdrom is called something else. you can find out what it is by listing the contents of your media folder and finding whichever makes sense:

```

ls /media

```

normally you'd install software through synaptic or by downloading a .deb file. .deb files bear a similarity to installation files in windows. synaptic is better though

---

### Post by crawling_warpig on 2008-10-10
Superb! Thank you o wise one! :D

It all worked and your descriptions were very helpful for a newbie like me.

Thanks again

---

### Post by Zill on 2008-10-10
> **crawling_warpig said:**
> ...I'm trying to install a program from a dvd. There's an install file and when I open it, it starts up but then I get a message saying that I must be logged on as a super user...
Maybe it's time to get back to basics ;-)

If you are a newbie with Linux then you may like to know that installing from a dvd is not the usual method of installing software in Ubuntu.  We try to use a far simpler method than that used by MS Windows :-)

With Ubuntu, software is generally automatically installed as a deb package.  See this link for more info...
[URL="http://www.psychocats.net/ubuntu/installingsoftware"]
http://www.psychocats.net/ubuntu/installingsoftware[/URL]

As aeiah requested earlier, please let us know what application you are trying to install.

---

