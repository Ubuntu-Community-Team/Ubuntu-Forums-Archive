---
title: "Software upgrades using Synaptic"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by lescarlin on 2008-05-19
This one's a real headache.  I like backgammon, and i saw synaptic has version 0.15 in its package list.  But thats no good since the latest version is 0.16, and a much better deal.  However i cannot find a way to install the latest version.  Here's what i've tried so far:

1. used the reload function in Synaptic to get it to check the repositories
2. Downloaded the latest .tar version of gNu Backgammon, unzipped this, but my system wont recognise this - ie does not appear in Synaptic as an alternative to version 0.15
3.  used terminal and issued: 'sudo aptitude install gnub'.  It does this, but just reinstalls version 0.15
4. used the 'Complete Removal' option in Synaptic PM.  Doesnt work - the old version remains listed as uninstalled, so any attempt to install 0.16 results in 0.15 version being retrieved and installed.
5.  The 'mark for upgrade' is greyed out in synaptic, so no version available in the repository i guess
6. the synaptic file menu has a 'Add downloaded packages' item.  That lets me browse to where i've unzipped the d/l of 0.16, however i've no idea which file synaptic needs from the d/l to recognise the new version.

Thats about it.  Any help appreciated.

Les

---

### Post by 0faber on 2008-05-19
First, check to see if there's a .deb file instead of a .tar file available from the developers. (A .deb file is intented ofr installation in Ubuntu and other Debian-based Linux distributions.) That'll make your life a lot easier. 

If not, come back here and ask for help with the .tar file.

---

### Post by philinux on 2008-05-19
Have you read this.

[http://www.gnu.org/software/gnubg/#downloading](http://www.gnu.org/software/gnubg/#downloading)

---

### Post by Maestro23 on 2008-05-19
Just to add:

Compiling Software: [https://help.ubuntu.com/community/CompilingSoftware?highlight=(compiling](https://help.ubuntu.com/community/CompilingSoftware?highlight=(compiling))

---

### Post by drs305 on 2008-05-19
Synaptic will install apps/libs etc from the repositories or from a CD. The versions on the repositories are not always the latest for a variety of reasons. 

If you cannot find a .deb version of the version you desire, there may be an .rpm version available. If so, that would be the easiest to work with, as it can easily be converted to a .deb file with the 'alien' app.

If you can download an .rpm version, download it and then:
```
sudo aptitude install alien
```

Then:
```
sudo alien location/filename.rpm
```
If the .rpm was downloaded to your Desktop, the command would be:
```

cd ~/
sudo alien filename.rpm
```

This will create a .deb file. Then all you have to do is click on it to install it.

---

### Post by lescarlin on 2008-05-19
> **philinux said:**
> Have you read this.

[http://www.gnu.org/software/gnubg/#downloading](http://www.gnu.org/software/gnubg/#downloading)

Thanks, but that site only refers to version 0.15, which is the one i want rid of.

---

### Post by lescarlin on 2008-05-19
Thanks for the suggestions.  There doesnt seem to be a .deb version around.  However there is an .rpm version i saw, so i'll try to convert that via alien (thx to drs305), failing which maybe some help with my existing .tar file.  Lemme try and i'll get back later.

Les

---

### Post by lescarlin on 2008-05-19
While i'm on the topic - 

where can i can get a listing and usage explanation for terminal commands?  That seems a much better way of getting stuck into what Ubuntu can offer me.  Reminds me of DOS commands... yes i'm that old.:)

---

### Post by philinux on 2008-05-19
> **lescarlin said:**
> Thanks, but that site only refers to version 0.15, which is the one i want rid of.

Specifically this bit about 0.16. Do not expect this code to be stable; it will generally include both more features and more bugs than the main pre-release version.
It calls 0.15 the pre-release version

---

### Post by lescarlin on 2008-05-19
> **philinux said:**
> Specifically this bit about 0.16. Do not expect this code to be stable; it will generally include both more features and more bugs than the main pre-release version.
It calls 0.15 the pre-release version

I'm aware of this.  Actually i have been running gnubg 0.16 for many months on my PC under Win XP with no problems, and i think its streets better than 0.15.  (My Ubuntu OS is on my laptop).  It's possibly more stable with me as i dont use all the gnubg features.

Les

---

### Post by lescarlin on 2008-05-19
Turns out i'm wrong about 0.16 - its only available as .tar.  The rpm's are all previous versions, so i will after all need advice on how how to deal with .tar.  I got as far as unzipping the package in to a new directory, but cannot see further where to go with this.

thx
les

---

### Post by drs305 on 2008-05-19
> **lescarlin said:**
> Turns out i'm wrong about 0.16 - its only available as .tar.  The rpm's are all previous versions, so i will after all need advice on how how to deal with .tar.  I got as far as unzipping the package in to a new directory, but cannot see further where to go with this.

thx
les

I think while I was investigating your problem the extracted folder had an install.sh file in it. Clicking on that will probably install the package.

---

### Post by lescarlin on 2008-05-19
> **drs305 said:**
> I think while I was investigating your problem the extracted folder had an install.sh file in it. Clicking on that will probably install the package.

The only install file i found was a text file giving a lot of very unclear instructions.  Perhaps u could take a look at that.  I didnt see any install.sh there, or in any subdirs.

les

---

### Post by drs305 on 2008-05-19
> **lescarlin said:**
> The only install file i found was a text file giving a lot of very unclear instructions.  Perhaps u could take a look at that.  I didnt see any install.sh there, or in any subdirs.

les

I had looked earlier in the day at one of the daily builds (I think). I would just use the file you downloaded. To compile the app, here are some how to links:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

Added: On any compiling, I would recommend replacing the 'make install' command with 'sudo checkinstall', which will allow you remove the program more easily if you decide to do so later. You would probably have to install the 'checkinstall' app to do this.

---

### Post by lescarlin on 2008-05-20
> **drs305 said:**
> I had looked earlier in the day at one of the daily builds (I think). I would just use the file you downloaded. To compile the app, here are some how to links:

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

Added: On any compiling, I would recommend replacing the 'make install' command with 'sudo checkinstall', which will allow you remove the program more easily if you decide to do so later. You would probably have to install the 'checkinstall' app to do this.

Those 2 urls u supplied are frankly hairy places to be for an ubuntu newbie like me.  At monkeyblog i followed the advice  under the 'source package' heading (mainly as this listed .tar as one of the sources).  It said to use ./configure and was also advised that if that failed it may report missing packages that i would need to install via synaptic.  So it proved - ./configure asked for glib2, so i looked in synaptic, and it wasnt there.  A web search found it, but it turns out to be a .tar file.  Which i cant install cos i cant get past ./configure.  So i have my head well & truly up the rear end now.:confused:

Suggestions?

thx, les

---

### Post by drs305 on 2008-05-20
I beleive the libglib2.0-0 synaptic package contains what you need for the dependencies.

---

