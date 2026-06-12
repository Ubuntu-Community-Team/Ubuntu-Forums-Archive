---
title: "Upgrading Open Office"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Armaniboy on 2008-10-19
I want the new open office, but I don't know how to upgrade it. Can anyone help? I'd prefer to do it in the terminal. I still have issues downloading a deb file from openoffice.org

Armaniboy:KS

---

### Post by fr.theo on 2008-10-19
here try this out.

add this to your repository.

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

update it using sudo apt-get update or use you synaptic package manager and check for new updates.

then upgrade it.

2.4.1 will automatically be upgraded to 3.0, no hassle of deleting previous installations

---

### Post by subaruwrc01 on 2008-10-19
I did that, but I'm not seeing any updates/upgrades for open office.

---

### Post by fr.theo on 2008-10-19
sorry forgot to tell you,

go to terminal then type the following:

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
"always make a backup of any file you modify, just in case"

sudo gedit /etc/apt/sources.list

add the following at the bottom of the file:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

then save now you can goto your synaptic package manager and check for updates or sudo apt-get update in terminal.

Good luck.

---

### Post by fr.theo on 2008-10-19
ok, you can try the following site [http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)


you can download open office 3 from here: [ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/](ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/)

---

### Post by fr.theo on 2008-10-19
just found this site give it a go.

[http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/](http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/)

---

### Post by fr.theo on 2008-10-19
my last post works tried it my self.

---

### Post by toasty_ghosty on 2008-10-19
I just tried adding the software sources to my sources list and it doesn't seem to detect the update. I tried both apt-get update as well as doing it through the GUI. And I'd rather not just install it. Any reason why this isn't working?

---

### Post by fr.theo on 2008-10-19
ok, download the Open office package from this site, remember to download the appropriate architecture if you are using 64 bit Ubuntu then download the 64 bit version or 32 bit then download the 32 bit version of office.

here is the site again: [ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/](ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/)
 
remember to remove the old office. sudo apt-get remove openoffice*.*

Example:
File:OOo_3.0.0_LinuxX86-64_install_en-US.tar.gz ( RPM file)
 
File:OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz (DEB this is easier)

once downloaded do the following:

1 > unpack the tar.gz file to you desktop or anywhere else you want, I put it in my desktop.

2 > in terminal su then type your password this will give you admin rights.

3 > goto your desktop directory "cd /home/(your folder name)/desktop  eg./home/theodore/Desktop

4 > change to the directory in which you unpaked your Open office 3 folder

eg. cd OOO300_m9_native_packed-1_en-US.9358

5 > then goto "cd /DEBS" folder

6 > then type the following    sudo dpkg -i *.deb once it has finished its process then goto step 7

7 > going back to desktop on the top pannel right click and select "add to panel"

8 > then select "custom application launcher"

9 >in the launcher add the following :
 Name it open office or OOO3
 in the command line add the following :/opt/openoffice.org3/program/soffice

10 > now close and run the newly made launch


11> the open office set up should launch, just follow the instructions.

Good luck.

---

### Post by fr.theo on 2008-10-19
to add the launcher in your Applications >> Office 

1 . goto Systems > Preferences > Main Menu

2 . In Main Menu select "Office" in the "Menu" list

3 . then select add an application launcher will start up 

4 . Give it a Name Open Office 3

5 . add the following to the command line: /opt/openoffice.org3/program/soffice

6 . if you want change the Icon.

have fun.

---

### Post by dwasifar on 2008-10-20
> **fr.theo said:**
> to add the launcher in your Applications >> Office...

If you have uninstalled the Ubuntu-delivered Open-Office 2.x, then rather than manually creating launchers, you can install the desktop integration package included with 3.0:

```
cd OOO300_m9_native_packed-1_en-US.9358/DEBS/desktop-integration/
sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb 
```

This creates all the launchers and shortcuts within the menus where you would expect them to be.

---

### Post by Armaniboy on 2008-10-20
Thanks for the help!

---

### Post by metalnate on 2008-10-21
Im following the instructions here, and I have the correct file downloaded when I run:  cd OOO300_m9_native_packed-1_en-US.9358 it says no file or directory.  This is so frustarting I've been trying to install this for days.  The zipped file is on my desktop, i've unpacked it on my desktop.  No commands work.  it's like the file isnt there, i've even deleted it and downloaded it three times.  Why must installing programs be so difficult. I cant even change directories to any folder on my desktop.  

Nvm.  I was in the wrong directory, i did cd / and then the commands worked.

---

### Post by Armaniboy on 2008-10-22
Still lost. I downloaded the file, removed openoffice from my computer, but have Open office 3 sitting on my desktop. What are the command lines I type into the terminal?

The name of my file is:

OOO300_m9_native_packed-1_en-US.9358

Armaniboy:KS

---

### Post by Armaniboy on 2008-10-22
[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)


This worked well for me :):KS

---

