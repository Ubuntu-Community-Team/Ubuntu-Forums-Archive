---
title: "Code::Blocks"
date: 2008-03-02
forum: Programming Talk
---

### Post by Jason2gs on 2008-03-02
I everyone :)

So I was here:

[http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu)

I got down to the part where it wanted me to go to the Nightly Build forum and download the current release.

I went there, clicked on the thread for the right release, followed the link for my processor and distribution of Linux, but I couldn't find the right download link.

I went here:

[http://www.codeblocks.org/](http://www.codeblocks.org/)

Went down to Downloads, then Binaries, and downloaded **codeblocks_8.02-0ubuntu1.deb.tar.gz** from Sourceforge.

So far, so good.

I unzipped the tar file, and in it I found seven .deb files.

As the first page said, I ran *sudo dpkg -i *.deb* to install it.

Yay! It installed :D

But, then I tried to install another package. The package wouldn't install, and apt-get threw me:

> You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
libcodeblocks0: Depends: libwxgtk2.8-0 (>= 2.8.7) but 2.8.4.0-0ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Running "sudo apt-get -f install" tells me:

> The following packages will be REMOVED:
codeblocks codeblocks-contrib codeblocks-dbg codeblocks-dev libcodeblocks0 libwxsmithlib0 libwxsmithlib0-dev
0 upgraded, 0 newly installed, 7 to remove and 58 not upgraded.
7 not fully installed or removed.

And running "sudo apt-get install libwxgtk2.8-0" only says that libwxgtk2.8-0 is already at it's newest version.

And now I'm here. Asking for help on one of two things:

1) Force apt-get to ignore any unmet dependencies.

2) Make whatever piece of software that isn't recognizing libwxgtk2.8-0, recognize it.

If someone lend their cybernetic hand, I would be very please :)

Thanks for reading,

-Mike

---

### Post by Quikee on 2008-03-02
If you look closely you see that libcodeblocks0 depends on libwxgtk2.8-0 version greater of equal to 2.8.7, but you have 2.8.4.0-0ubuntu3. 

Anyway.. you can try code::blocks from ths repository:

```
deb http://lgp203.free.fr/ubuntu/ gutsy universe
```

To add the repository go to synaptic > settings > repositories > third-party software > add.. and paste the above line

---

### Post by Jason2gs on 2008-03-02
Well, I saw that, but I had no way to fix it, either. I couldn't find the 2.8.4.0-0ubuntu3 package.

I added that to the repository, but I don't know which package(s) to install. I try to mark codeblocks for installation but it gives me the same error message about libwxgtk2.8-0.

---

### Post by Jason2gs on 2008-03-02
Bump.

---

### Post by dynamethod on 2008-03-02
No, you need the dev packages of libwxgtk2.8-0, so try sudo apt-get install libwxgtk2.8-0-dev or just use synaptic to search for it, but if you get any problems usually its because you dont have the dev packages for whatever

And why not make it easier on yourself, use this link to get the .deb packages: [http://downloads.sourceforge.net/codeblocks/codeblocks_8.02-0ubuntu1.deb.tar.gz](http://downloads.sourceforge.net/codeblocks/codeblocks_8.02-0ubuntu1.deb.tar.gz)
untar, then install the .deb packages, if it whines that you need a dependency it will be one of the debs in that tar (dont be a hero, just use the gui.. double click those debs..)

NOTE 2: The Ubuntu packages have been linked against wxGTK-2.8.7, which is not available in the default Ubuntu repositories.To successfully install these packages, you have to add the wxWidgets repository for Ubuntu in your /etc/apt/sources.list (e.g. deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main).

so do wget -q [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) -O- | sudo apt-key add -

sudo apt-get update
sudo apt-get upgrade

---

### Post by Jason2gs on 2008-03-02
Thank you :)

Unfortunately, there's no libwxgtk2.8-0-dev package.

There's a libwxgtk2.8-dev package, but it's already installed.

What I need to do is force a different version of libwxgtk2.8-0 to install. It's just that, in Synaptic, "Package -> Force Version" is grayed out. Why is this?

---

### Post by dynamethod on 2008-03-02
> **Jason2gs said:**
> Thank you :)

Unfortunately, there's no libwxgtk2.8-0-dev package.

There's a libwxgtk2.8-dev package, but it's already installed.

What I need to do is force a different version of libwxgtk2.8-0 to install. It's just that, in Synaptic, "Package -> Force Version" is grayed out. Why is this?

look at my post above closely here:

NOTE 2: The Ubuntu packages have been linked against wxGTK-2.8.7, which is not available in the default Ubuntu repositories.To successfully install these packages, you have to add the wxWidgets repository for Ubuntu in your /etc/apt/sources.list (e.g. deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main).

so do wget -q [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) -O- | sudo apt-key add -

sudo apt-get update
sudo apt-get upgrade

---

### Post by Jason2gs on 2008-03-02
Thank you :)

I already said in the first post that I had downloaded the .deb files.

I followed what the tutorial said and installed them using sudo dpkg -i *.deb

Also, when I open them in the GUI, there's not one of them that doesn't have an unmet dependency.

I'm running sudo apt-get upgrade right now. Let's hope it works! Restarting now.

---

### Post by dynamethod on 2008-03-02
edit nvm

---

### Post by Jason2gs on 2008-03-02
Restarted.

*Sigh*

libwxgtk2.8-0 is still 4.8.4.0-0ubuntu3 :(

Even after sudo apt-get install libwxgtk2.8-0.

---

### Post by dynamethod on 2008-03-02
Can you please confirm for me that you added:

deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main

to your sources list AND wget the key

thanks

---

### Post by Jason2gs on 2008-03-02
I copied-and-pasted the command you gave me.

How can I make sure it took effect?

And thank you for helping me :)

---

### Post by dynamethod on 2008-03-02
ok open up terminal then type this in:

**gksu gedit /etc/apt/sources.list**

gedit will then open up and you will have some text inside, scroll to the bottom of the text file and type this in (or copy and paste it):

**deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main**

then click on "save"

now close gedit,

now in terminal type this in (or copy and paste it in):

**wget -q [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) -O- | sudo apt-key add -**

it should say something like "done" or "Ok" or "key added" something like that anyway

THEN do this:

**sudo apt-get update**
**sudo apt-get upgrade**

---

### Post by Jason2gs on 2008-03-02
Oh thank God!

> mike@Juankubariz:/$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

See that? No errors :) All thanks to you!

---

### Post by dynamethod on 2008-03-02
Glad to help, enjoy

I noticed the 9 not upgraded, can you please open up terminal and type this in:

**sudo apt-get upgrade**

thanks

---

### Post by Jason2gs on 2008-03-02
Kay.

> The following packages have been kept back:
kaffeine libxine1 libxine1-console libxine1-ffmpeg libxine1-gnome
libxine1-misc-plugins libxine1-plugins libxine1-x ntfs-3g
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

---

### Post by dynamethod on 2008-03-02
Ah well, no biggie, as long as it works :popcorn:

---

### Post by Jason2gs on 2008-03-02
Exactly ;)

---

### Post by melopsittacus on 2008-03-03
Hi, I installed Code::Blocks with the above mentioned process. I noticed however that it said the Code::Blocks packages could not be authenticated (although I did add the signatures file as described). Anyone else noticed this?

---

### Post by dynamethod on 2008-03-03
Hi there,

Can you please post step by step exactly what you have done to try to install codeblocks, such as where you got and what you got for the packages, did you get the source or the binary?, step by step, if you could also post output from the terminal within code tags that would help to.

---

### Post by intel on 2008-03-04
there's no reason not to use a full featureD iDE like
eclipse CDT instead.

---

### Post by Jason2gs on 2008-03-04
> **intel said:**
> there's no reason not to use a full featureD iDE like
eclipse CDT instead.

Code::Blocks is a full featured IDE?

---

### Post by dynamethod on 2008-03-04
yes codeblocks has alot of features, probably more than you'll ever need to use, you can try eclipse if you like, but i think it comes down to more personal preference.

---

### Post by Jeisson on 2008-03-04
> **Jason2gs said:**
> Code::Blocks is a full featured IDE?

Code::Blocks is developed using the cross-platform [wxWidgets]("http://www.wxwidgets.org/") library, so it is cross-platform also, and it is one of the best IDE for developing applications for several architectures in C++ with the quoted library, because you use real wx controls while you are programming. Of course, there are lots of advantages more to talk about this IDE.

An easy way to install the lastest CVS version is taking advantage of the [Jens nighty builds]("http://jens.lody.name/debian/")...

Best regards ;)

---

### Post by luke.is.very.handsome on 2008-04-10
So i did this


```
wget -q [http://apt.wxwidgets.org/key.asc](http://apt.wxwidgets.org/key.asc) -O- | sudo apt-key add -
```

then i went in to synaptic and added

```
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main
```

then i ran the <Reload> button on the spm and then clicked <Mark All Upgrades>.

Amazingly, it listed the stuff that code::blocks still needed, aside from me having the repository for codeblocks in my synaptic as well ( some french written site has it, google search for it ), i installed it all through synaptic and those two repository keys you have to run before the repository will work.

Thanks for the help out on this.

---

### Post by drdos2006 on 2008-04-11
Here is how I did it.

[http://ubuntuforums.org/showthread.php?t=750323](http://ubuntuforums.org/showthread.php?t=750323)

regards

---

### Post by pasgui on 2008-04-22
hi,

try this command:
```
sudo update-alternatives --config wx-config
```

regards, pasgui

---

### Post by Ferrat on 2008-04-26
As of Hardy (at least 64bit) code::blocks installs just fine from what I can see?

---

