---
title: "Why the installation for games/app for Linux is diff than Windows"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by D.Sync on 2008-06-03
As a Windows, particularly WinXP for quite a long years, I had been get used to their installation sequence, which requires user to double click on the .exe or .msi file and the installation will take place. Just wondering how come the installation for Linux is slightly difficult and difference than Windows user?

Thanks for sharing.

---

### Post by jualin on 2008-06-03
The difference is that Linux is more about permissions and therefore it doesn't let any program to just install itself by a simple double click. Thats the main reason why Linux is so secure because in a Windows machine any program can run freely. Now Windows games don't work on Linux cause the gaming companies dont release their versions for Linux, so Linux users have to come up with creative ways to install the games. 
Now for the apps you have something way better than in Windows called Synaptic Package Manager which is almost like Windows. You just select the package (application) and then just click on install and that's it!. Also now many of the popular applications such as Frostwire (Limewire clone) and Realplayer come in pre-compiled packages for several distributions which enable the user to just double click on it and install it.

---

### Post by Xiong Chiamiov on 2008-06-03
Why is it different?  Because it doesn't suck.

Really, I got used to apt really quickly, and I can't stand all the steps I have to go through to install things on Windows.  You should read [this]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by oedha on 2008-06-03
hi there....
of course they are different.....
but to me...at least i know what things installed during the installation since the linux installation contains some dependencies installation also......and if i need to know.....just list the package....analyze it
on windows.....yes it's simpler...double click - wait - done....but sometimes i dont know what's installed actually.......is there anything else beside the program that i wanted.

---

### Post by hyper_ch on 2008-06-03
windows is simpler? You can't even really batch-install all your favourite software at once on windows...

---

### Post by Xiong Chiamiov on 2008-06-03
> **hyper_ch said:**
> windows is simpler? You can't even really batch-install all your favourite software at once on windows...
Really.  And not only that, you have to like, visit a website to download the installer!  And then you have to install it!  And then you have to repeat for things that it requires!  Oh noes!

I'd prefer even to compile from source over the Windows way.  That's why I never boot into my PC-BSD installation (well, and the hardware support).

---

### Post by hyper_ch on 2008-06-03
and then you even have to be rich to pay for all that software on windows...

---

### Post by adobrakic on 2008-06-03
> **hyper_ch said:**
> and then you even have to be rich to pay for all that software on windows...

or you can steal it. :x

---

### Post by kostkon on 2008-06-03
> **D.Sync said:**
> As a Windows, particularly WinXP for quite a long years, I had been get used to their installation sequence, which requires user to double click on the .exe or .msi file and the installation will take place. Just wondering how come the installation for Linux is slightly difficult and difference than Windows user?

Thanks for sharing.
I think it is easier than *Windows*: one-click installation in *Add/Remove* and *Synaptic* or double-click on a *.deb* file.

---

### Post by akiratheoni on 2008-06-03
> **D.Sync said:**
> As a Windows, particularly WinXP for quite a long years, I had been get used to their installation sequence, which requires user to double click on the .exe or .msi file and the installation will take place. Just wondering how come the installation for Linux is slightly difficult and difference than Windows user?

Thanks for sharing.

Difficult?

Going to Applications-> Accessories-> Terminal and typing in:

sudo apt-get install apache2

then your password too difficult for you? Or would you rather go to Google, search 'apache', go to [http://www.apache.org](http://www.apache.org), go to the HTTP Server link, click 'from a mirror!' under Downloads, click on the correct download, wait for it to download, then verify the integrity of the download, then scan it for viruses just in case, then double click the exe, then go through the wizard? And possibly reboot your computer?

I'd say the Linux way is easier. Different, but easier.

---

### Post by adobrakic on 2008-06-03
> **akiratheoni said:**
> Difficult?

Going to Applications-> Accessories-> Terminal and typing in:

sudo apt-get install apache2

then your password too difficult for you? Or would you rather go to Google, search 'apache', go to [http://www.apache.org](http://www.apache.org), go to the HTTP Server link, click 'from a mirror!' under Downloads, click on the correct download, wait for it to download, then verify the integrity of the download, then scan it for viruses just in case, then double click the exe, then go through the wizard? And possibly reboot your computer?

I'd say the Linux way is easier. Different, but easier.

Lol, wow, why are you catching feelings? If he just started, downloading things on linux IS difficult. And the way your explaining Windows downloads is completely over-exaggerating it. It's more like go to the website, click on download, and install. Same as going to the terminal and installing that way. And you don't need to be afraid of viruses if you know where to go. Also, i rarely had to restart my computer after installing things. 
Fan boys are annoying, btw.

---

### Post by mix. on 2008-06-03
First off, the biggest thing for any Linux newcomer would be adjusting to the fact that the equivalent of the *.exe files you're so used to in Windows are hidden from plain view (unless you're talking desktop shortcuts).

Also, almost every installation that I know of puts files in different places on the filesystem as opposed to putting them in a single folder under Program Files. You might want to read [this]("http://tldp.org/LDP/intro-linux/html/chap_03.html") to learn more about it.

Reason for all this is, again, security. By putting strict permission settings and spreading files across the filesystem Linux is effectively telling outside threats (viruses and such) that it would take an administrator password to get anywhere, unlike in Windows where once you log in as an administrator, backdoor programs get to go anywhere and get to use all the resources they want.

Now as for the perceived difficulty, it's all a matter of being in a completely different environment from the one you were used to. That doesn't mean it's difficult - I think most people confuse "unable to run Windows programs" with "difficult." You're going to have to accept the fact that many of the programs you're used to using won't work straight out of the box on Ubuntu. Most of these programs have their equivalents though, if you look hard enough. A majority of the software people use can be installed via the install option on the menu, or through Synaptic or apt. 

Bottom line is, it's just a different way of doing things.

---

### Post by D.Sync on 2008-06-03
Wow, that's a nice feedbacks from all you guys there~

I'll try to get used to it. :)

---

### Post by D.Sync on 2008-06-03
I find [this]("http://monkeyblog.org/ubuntu/installing/")link very useful. Really solve the questions I had on my mind.

---

### Post by SunnyRabbiera on 2008-06-03
For me I never found software installation hard in a debian based system, its just doing something different.
Synaptic, apt, aptitude and add/remove are all good tools in their own way.
For me getting software and keeping it maintained in linux is much simpler then in windows...
I mean after using synaptic the windows way seems more drug out:
Double click .exe
next
next
go through a long drawn out EULA and if I agree to the terms and willing to sell my mortal soul, house, car, husband, wife, kids, dog, cat, hamster, guinea pig, etc to Bill gates
next
enter 900 character long software code
next
next
next
close

Comapre that with:
go to system> administration> synaptic package manager
search for package
mark package
mark dependancies
click apply
then apply again
wait for stuff to install
done

---

### Post by hyper_ch on 2008-06-03
btw, if you ever going to reinstall, you can easily install everything at once... that's the power you really get here.

(0) Make a notice with all the applications you "must" have...

(1) Add all the repos that you had before (this can also be done through a script but I skip that part now)

(2) Make a little script with that you can install all those applications that are a must (see above 0).

```

sudo apt-get install -y apache2 php php-cli skype amsn kopete konversation kontact googleearth ........

```

A few applications do require user input and I'd split it up into different chunks:

```

#!/bin/bash

################ RESTORE SOURCES.LIST ###############

cp -f backup_files/sources.list /etc/apt/sources.list
cp -f backup_files/secring.gpg /etc/apt/secring.gpg
cp -f backup_files/trustdb.gpg /etc/apt/trustdb.gpg
cp -f backup_files/trusted.gpg /etc/apt/trusted.gpg

#####################################################

apt-get update
apt-get -y upgrade

# Stuff with user feedback
apt-get -y install skype sun-java6-jre sun-java5-jre postfix

# Networking
apt-get -y install amsn irssi openssh-server kazehakase opera flashplugin-nonfree samba mc ntp ntpdate whois phpmyadmin mysql-server mysql-client libmysqlclient15-dev googleearth traceroute libjack0.100.0-dev

# Security
apt-get -y install seahorse file-roller chkrootkit

# Codecs & Media
apt-get -y install kubuntu-restricted-extra libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui w32codecs mplayer vlc imagemagick gnump3d python-glade-1.2 python-gtk-1.2

# Other stuff
apt-get -y install gnomebaker htop linux-headers-`uname -r` build-essential xinetd unrar gparted openoffice.org openoffice.org-gtk msttcorefonts numlockx

```

With that I have 95% of my want-to-have programs again installed...

---

### Post by akiratheoni on 2008-06-03
> **adobrakic said:**
> Lol, wow, why are you catching feelings? If he just started, downloading things on linux IS difficult. And the way your explaining Windows downloads is completely over-exaggerating it. It's more like go to the website, click on download, and install. Same as going to the terminal and installing that way. And you don't need to be afraid of viruses if you know where to go. Also, i rarely had to restart my computer after installing things. 
Fan boys are annoying, btw.

Okay, yeah, I may have over exaggerated a little bit, but inputting a single command is so much easier. Yes, it's different, and it takes getting used to, but is easier.

Don't call me a fanboy. Like I said, I might have exaggerated a bit but I do like Windows for several things.

EDIT: Wait, you didn't need to restart your computer after installing things? Okay, yeah, you could skip that part, but a lot of times it was recommended after I installed things on Windows...

Also, when I download things even off download.com, I need to go through several screens to finally get to the downloading the executable. And I do need to search for the program on the site first (and just to be fair, you do have to find the right name of the package to install through the command line).

---

### Post by D.Sync on 2008-06-03
> go through a long drawn out EULA and if I agree to the terms and willing to sell my mortal soul, house, car, husband, wife, kids, dog, cat, hamster, guinea pig, etc to Bill gates

This one's real funny~ Cheer up my day with this one LOL.

---

