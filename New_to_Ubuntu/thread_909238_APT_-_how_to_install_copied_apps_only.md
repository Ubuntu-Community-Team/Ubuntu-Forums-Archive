---
title: "APT - how to install copied apps only"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by tommaso.ferigo on 2008-09-03
Hi guys, 

new to Ubuntu and to Forums, so please don't blame me (or give link for other similar threads in case) if I did not manage to find a reply to this question yet.

I have burned a DVD with APTonCD to back up some apps I am trying to install on a second PC. 

I have restored the apps, and I read that I have now to install them manually from synaptic, from the terminal or via add/remove.

As far as I understood, so far I have copied the apps somewhere (but where?) and they are ready to be installed.

I opened synaptic package manager and I can see the list of all available packages. By the way I am using a virtual machine on a XP OS now with only 1Gb RAM, so it is not that quick.

************
MY QUESTIONS
************

How can I install ONLY the several applications copied from a APT DVD which are spread and not showed as "copied and ready to be installed even without any internet download" among all the available apps in the synaptic "all" list?

Can I install the copied APT-DVD apps all at once and not by double checking the names of what was on my APT DVD (I had 1Gb apps on the DVD, it would take me forever) with what I see in the "all" list of synaptic? Among the "all" list of synaptic, how should I know which are the apps copied from the APT-DVD and ready to be installed, and which are the ones I would still have to download from the internet before installation? How can I filter the apps copied from APT DVD and ask to install them all at once?

Thank you in advance for yr kind answers. Tommaso

---

### Post by cozmicharlie on 2008-09-03
Welcome to Ubuntu - installing programs (packages) in Ubuntu is one of the most confusing activities for new users (especially those coming from Windows). Synaptic is great because it installs all the dependencies and any package installed through Synaptic should work without any further tweaking.  

As per aptoncd I suggest your read through this [http://aptoncd.sourceforge.net/doc-manual.html](http://aptoncd.sourceforge.net/doc-manual.html)

(I know this explanation of Synaptic is very basic but some reading this may find it helpful)  
You basically have 2 GUI methods for installing packages in Ubuntu - 1. is the add/remove (go to menu/applications/Add/Remove) and 2. Using Synaptic (menu>system>administration>Synaptic).  All the packages in Add/Remove are in Synaptic so all you really need is Synaptic.  To install in Synaptic all you do is:
[LIST=1]
[*]Open Synaptic
[*]Find the package you want to install (search works great)
[*]Click on the box and a dialog comes up that says "mark for installation"
[*]In some cases another dialog will open with a list of other packages that are needed (these are called dependencies) - click OK.
[*]Then you will see a green check in the box.  Click on Apply and it will install the package.
[/LIST]
That is all you have to do.

Of course without internet access it won't work and that is were using aptoncd comes in:

The basic steps using aptoncd are:
[LIST]
[*]Open the media
[*]Select the packages
[*]Copy the files
[*]Install the files
[/LIST]
In detail:
[LIST=1]
[*]The packages are stored on the disk as .iso files (images).
[*]The first step is to put the CD/DVD created by APTonCD in the drive.
[*]When the media is read, it's shows a list with all packages available to restore. By default all packages are checked, but you can just uncheck the packages you don't want to restore.
[*]Copy files.  The packages selected are copied from the APTonCD media to /var/cache/apt/archives/ directory. This way the packages are available and you can install them using apt-get, aptitude or synaptic without need to download them.  Any packages you don't want you just uncheck.
[*]Under the options you want to make sure you also include the dependencies.  Auto-select dependencies.  This option guarantees that all dependencies of the selected packages are also checked to be restored.
[/LIST]
Open Synpaptic and install.  Without internet access you will only be able to install packages on aptoncd.

I am not sure with aptoncd if you need to point Synaptic to the downloaded packages from the aptoncd (I don't believe you do) but just in case all you do is go to the menu>file>add downloaded packages and point it to the /var/cache/apt/archives/ directory.

You can install them all at once using a couple methods:
**Create a Metapackage:**  This goes back to how you created the aptoncd. "With Metapackage option it's possible to create a package whose dependences are all packages included in the APTonCD media. It's useful to restore all packages easily, so you can just install the matepackage instead of install each package by hand."

**Create an aptoncd repository:**  If you already have the aptoncd and don't want to go back and burn another then you can set it up as a repository.  Then in Synaptic on the bottom left you will see a box that says "origin" click that and it lists ll the packages by repository and yours should be there.  Then when you select it in the dialog box only the packages on the aptoncd will show in Synaptic.  It makes it easy to check the ones you want or all.  Their is probably a way to mark "all" in Synaptic if you look through the menus - I don't know how though maybe someone else that does will come along and help. 

That should work for you.
Enjoy

---

### Post by Elfy on 2008-09-03
I'm not sure how you could just install packages that you backed up using aptoncd, how many of the packages you backed up did you actually install yourself? 

The packages should be in /var/cache/apt/archives

If you know what you have installed you could
```
sudo apt-get install package package1 package2 package3 package4
```

---

