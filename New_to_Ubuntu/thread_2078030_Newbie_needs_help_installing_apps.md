---
title: "Newbie needs help installing apps"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by Seadevil on 2012-10-30
I am a ubuntu site trying to install apps. the site is appnr.com
and they have "install" buttons by each app.
when i click on the button, a dialogue page pops up and says
"this link needs to be opened with an application. Send to Ubuntu software Center...then Choose an application..."   

What am I missing here?  what am i Looking for?  
any help appreciated...
I am in Ubuntu 12.10  kde.
thanks
Seadevil

---

### Post by TheMTtakeover on 2012-10-30
What is it you are trying to install and can you provide a link?

---

### Post by Seadevil on 2012-10-30
well...here's the link,  I know I can "download"...but the 2nd link
has a bunch of software of which i get the same message no matter which one i click to install on.
[http://appnr.com/package/korganizer](http://appnr.com/package/korganizer)

2nd link:    [http://www.makeuseof.com/dir/appnr-ubuntu-application-installer-directory/](http://www.makeuseof.com/dir/appnr-ubuntu-application-installer-directory/)

---

### Post by monkeybrain2012 on 2012-10-30
korganizer is in the repository (and I suspect all of them are). Just install it with the package manager in Kubuntu. Linux is not like Windows usually one doesn't download programs from random sites.

---

### Post by bra|10n on 2012-10-30
With all respect I ask why you even bother with a website in the first place?
Is it so hard to use Muon Package Manager to install packages or a konsole with "sudo apt-get install <name-of-package>"

---

### Post by houseworkshy on 2012-10-30
The site you are looking at uses the apt;url method of installing.  It should open a package manager which asks for your password and then proceeds with the install.  I'm not fond of this method as one of the things it can do is install repositories too.  The relative safety of linux is partly due to programs being stored in repositores which are checked against malware.  If using repositores from elsewhere one is in the world of random trustworthyness.
The other big deal is that to install them one has the browser open, which includes virtual machines such as java, these can be infected on any machine.  On linux not such a problem as it rarely gets any further into your system.  
However when you enter your password you are activating "sudo", which gives admin powers for 15 minets.....and your browser is open and running.   You'll notice that if you use an apt;url it will ask for your password but if you use another within sudo's default timer period then it won't.  I think that this is potentially dangerous.  
So when using an apt;url don't browse or click anywhere else while sudo is active and after the install is done open a terminal and enter "sudo -k" which will stop the admin powers early. This isn't a bad idea even if the next thing you intend to do is another apt;url install as, along with the password request, you also get to see what actions are going to be taken.  If repository adding is one of those actions, you really do want to know about it and be extra leery of doing it.

---

### Post by NikTh on 2012-10-30
Hi , 
when you want to install an application **first thing** you have to do is to open the Ubuntu Software Center. 
I think Kubuntu has its own software center called [COLOR=Blue]Muon Software Center[/COLOR]. You have to search first there for the application you are interested. 

There are **thousands** of applications you can install with one click and with safety. Just write the name of the application in the search box.

Thanks

---

### Post by whatthefunk on 2012-10-30
Ways to install software in Kubuntu, in order of ease:

1. **Muon Software Center**
From the menu go to System > Muon Software Center.  You can easily search for programs or browse through the various categories to look for programs.  When you find the program you want, click on it and an Install button will appear.  Click on it and enter your password at the prompt.  Once installed, a button will appear in Muon Software Center allowing you to open it from there or you can open it from the menu.

2. **Muon Package Manager**
From the menu, go to System > Muon Package Manager.  Search for your program.  Once you find it, click on it and additional program information will come up on the bottom along with a button saying Mark for: Installation.  Click this, and then click Apply Changes on the top left.  It should ask for your password.  Program can be opened from the menu.

3. **Terminal**
Open a terminal, probably Konsole if you're using KDE.  You can find it by opening a menu and going to System > Konsole.
To search for a program:
```
apt-cache search SEARCH_TERM
```
To install a program:
```
sudo apt-get install PROGRAM_NAME
```

The above methods are the safest, easiest and best ways to install software on your system.  They get packages from Ubuntu repositories which contain software specially made for your system and are malware free.  You can install software that is not found in the repositories as well, but be sure that it is from a trusted source. 

4. **DEB packages**
DEB packages are packages made especially for Linux OSes in the Debian family, like Ubuntu.  All DEB packages end in .deb and can be downloaded from various internet sites.  To install a DEB package, simply double click on it.  An installer will open up and guide you through the installation process.

5. **Tarballs**
Not really recommended for new Linux users.  This usually involves downloading the program components, reading the README file to see if there are any special instructions, building the program, and then installing it.   See [here](http://www.cyberciti.biz/faq/install-tarballs/) for more info.

---

### Post by newb85 on 2012-10-30
That's a great write-up, whatthefunk.

I would add that extra repositories or personal package archives (PPAs) can be added to your system.  When that is done, the packages in those archives become available through the first three methods.  Of course, if an unsafe archive is added to the system, the safety of those three installation methods is compromised, so make sure it's a trusted source before adding it.

---

