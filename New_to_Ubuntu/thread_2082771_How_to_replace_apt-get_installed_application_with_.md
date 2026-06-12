---
title: "How to replace apt-get installed application with one compiled from source?"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by BeniaminK on 2012-11-10
I installed some packaged (in my case: medit and goldendict) from apt-get. I found some bugs in those application, that are currently fixed in a developer's page, but not yet in repositories.
Thus I compiled those applications from source (they are currently on ~/Desktop/xxx folder altogether with the source code in the same folder).
So my question:
1. How can I replace apt-get installed application with the one compiled from source? Where to copy files and should only binary file be copied, or everything else as well?
2. How might have I compiled applications, so that it can be distinguished, which files are necessary for compiling (source codes etc.) and which are config files? Because now they are messed up in one folder.

My guesses:
Ad. 1
a)check where are medit and goldendict installed (dpkg -L maybe? )
b) apt-get remove {medit,goldendict}
c) copy all folder to the places found above (source with binary and all the rest)

Ad 2.
No idea :)

---

### Post by evilsoup on 2012-11-10
Before you try all that, are you sure that there isn't a PPA with the latest version?

Another option might be to [create your own PPA](https://help.launchpad.net/Packaging/PPA). This will have the advantages of staying within the standard way of doing things, and allow you to transfer the software to other computers and new installs, *and* it could be useful to other people. The disadvantage is that you'll have to upload the source code to Canonical's servers and then apt-get them again.

---

### Post by BeniaminK on 2012-11-10
Well, in fact, I didn't change PPA for any packages. I just use the pre-installed one, mostly, beacause I what actions should have I proceeded.
[Launchpad webpage]("https://launchpad.net/ubuntu/+source/goldendict") shows, that recently has been an update in goldendict, but I don't know whether I am using this PPA or not.

How may I check, if I am using this one PPA?

---

### Post by evilsoup on 2012-11-10
PPAs are Personal Package Archives; they're listed on that page at the very bottom, under [Other versions of 'goldendict' in untrusted         archives.]("https://launchpad.net/ubuntu/+source/goldendict/+index#") PPAs can be uploaded by anyone, and in theory can contain anything (though the source code is freely available to view), so you should only use PPAs belonging to people you are pretty sure you can trust. The paranoid amongst us refuse to use them entirely, but I and many others find them an invaluable tool.

[This]("https://launchpad.net/~createsc/+archive/3beol") PPA is the only one listed there with the latest version of goldendict. If it was me, I'd probably be willing to trust the PPA's owner, since they've been a member since 2010 and is a member of the Ubuntu Korean team - but obviously that's up to you. If you want to use that PPA,
```
sudo add-apt-repository [B]ppa:createsc/3beol
[/B]sudo apt-get update
sudo apt-get upgrade
```
in a terminal will add it. This will make your system use *all* the software in the PPA instead of the repository versions.

The 'Raring Ringtail' thing on the page you linked indicates that a newer version of your program is available in the 13.04 development version. You can see if that has been 'backported' to your version of Ubuntu by using 
```
sudo apt-get install goldendict/raring-backports
```

If this works, it will install the version from the Raring Ringtail repositories (see [here]("https://help.ubuntu.com/community/UbuntuBackports") for a bit more information). This is as safe as using the regular repositories, so far as I know. If it doesn't work, that probably means that your program hasn't been backported. You can request it to be [backported]("https://wiki.ubuntu.com/UbuntuBackports"), but that can be quite an involved process - probably nothing you can't handle if you can compile code, but it might be more effort than its worth, for you, and so going the PPA route could be easier.
[]("https://launchpad.net/ubuntu/+source/goldendict/+index#")

---

### Post by monkeybrain2012 on 2012-11-10
Assuming the compiling involves the following steps:

```
./configure

make

sudo make install
```

There are two things you can do.

1) If you want to replace the repository version, it is nice to create a .deb from your compiled version and install that, so you can delete it from synaptic or use sudo apt-get remove if you decide you don't need it later.

Install checkinstall from the repository.

```
sudo apt-get install checkinstall
```

Then in the last step of compiling, instead of "sudo make install" do "sudo checkinstall" that will create and install a .deb package.


2) use your compiled version side by side with the repo version.

In that case instead of just "./configure" during compiling do something like "./configure --prefix=$HOME", that will install the software in your home directory (instead of "sudo make install" in the last step, just "make install" is fine) and the binary should be in /home/yourusername/bin (you may have to create the folder bin first if it didn't exist) You can use it by clicking the binary or create a launcher for it by making a desktop file and place it in the hidden folder /home/yourusername/.local/share/applications.

Google to see how to make a .desktop file, or open one with gedit in /usr/share/applications (with names like smplayer.desktop) and copy the template.

---

