---
title: "Installing Restricted Codecs on an offline Ubuntu machine"
date: 2009-02-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Taemojitsu on 2009-02-22
I didn't see a good guide for this so I am creating one myself.

It's relatively easy to update your system if your Ubuntu computer has an Internet connection, no matter how slow. You can update the packages list, generate a file showing all the packages and dependencies you need for what you want, and download them on a different computer. It's more difficult tho if you have no Internet connection at all on your Ubuntu computer, and the only online computers you have access to run Windows.


For many users, being able to play media files is a main computer function, even if it's offline. So the restricted codecs are one of the most important parts of an installation and something that many users get immediately after a fresh install. This explains how to do that using only a Windows computer connected to the Internet.

1) Go to [help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and read it
2) Go to [help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and read it
* 3) [update] Go to [help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal) and read it
4) Go to [medibuntu.org](http://www.medibuntu.org/) and download every package listed for your distribution, except Acrobat if you don't like and some of the other minor programs. Starting with Intrepid, I think the ffmpeg packages aren't included in medibuntu because the unstripped versions are available from Multiverse in the official repositories. Save all these packages to a single folder on your flash USB drive.
5) Go to [google.com](http://www.google.com) and search for 'ubuntu-restricted-extras intrepid', where intrepid is the adjective for your Ubuntu version such as dapper or hardy. One of the results should be at [packages.ubuntu.com](http://packages.ubuntu.com), with your adjective somewhere in the URL. Go to this page and make sure it's the correct version of the package.
6) Download every package required by this version of ubuntu-restricted-extras. If any dependencies of a package have a similar name ('vlc' vs 'libvlc2'), you will also need to download them. If any dependencies are in Multiverse or Universe, you will need to download them. Make sure to get the 'unstripped' versions of packages that offer it. You won't get every dependency for every package on the first try.
7) Download any media or audio players/editors you like, such as VLC, Mplayer, [Cinelerra](http://cinelerra.org/getting_cinelerra.php) and Audacity, and any obvious Multiverse or Universe dependencies.
8&#8203;) If you need to, download the Nvidia drivers for your card. The latest as of time of writing was nvidia-glx-180 for intrepid, the kernel source for 180 and the nvidia settings manager. You might also want to get the Compiz config settings manager so you can alter transparencies and so on.
9) Use the package search to find dpkg-multicd. Download this too and save it to the same folder.

Don't download any packages for a different distribution because you want a 'more advanced' codec. This can and will break your installation!! Unless you know it's safe.

Now you should have the first round of packages, all saved to the same folder on your flash USB drive, and the dpkg-multicd package. Transfer this folder to your home directory on your Ubuntu computer, and open the dpkg-multicd package in Gnome. This lets you install it using gdebi, which only works for installing one package at a time. This doesn't work if you need to install multiple packages which depend on each other! Install dpkg-multicd, which will let you create the Packages.gz needed to load your packages into Synaptic.

Go to the command line, such as by going to Applications / Accessories / Terminal. Type 'cd <directory>', where <directory> is where your packages are saved to. (NOTE: '~' is a shortcut symbol for your home.) 

```
misaki@dawn:~$ cd install/intrepid64-codecs/
```

dpkg-scanpackages is a program provided by dpkg-multicd. It creates complicated repositories but we only need to do simple stuff. You can type 'man dpkg-scanpackages' to read the manual. Create the packages list:

```
misaki@dawn:~/install/intrepid64-codecs$ dpkg-scanpackages .  /dev/null |gzip -9c > Packages.gz

```

This says: scan the current directory (the period means current directory), using a blank file (/dev/null) as the Override file, forward the output to gzip (the | means forward), and use it to create a 9c compressed file in the current directory named Packages.gz (the > means create).

```
 ** Packages in archive but missing from override file: **
  aacgain aacplusenc akirad-keyring-and-mirrors akiradnews alsa-
  firmware alsa-firmware-loaders alsa-tools alsa-tools-gui amrnb amrwb
  app-install-data-medibuntu audacity avidemux avidemux-common
  avidemux-qt blender cinelerracv-smp compiz compiz-core compiz-
  [...]
  zopeinterface python2.5 qdvdauthor qdvdauthor-akirad qt4-qtconfig
  sox transcode ttf-dejavu ttf-dejavu-core ttf-dejavu-extra videolan-
  doc videotrans vlc vlc-data vlc-nox vlc-plugin-arts vlc-plugin-esd
  vlc-plugin-ggi vlc-plugin-jack vlc-plugin-pulse vlc-plugin-sdl vlc-
  plugin-svgalib vorbis-tools w64codecs

 Wrote 239 entries to output Packages file.
misaki@dawn:~/install/intrepid64-codecs$ 
```

This created a list of all the packages in your local repository, and where they are located (all in the same folder). If you add new packages you have to recreate the Packages.gz, but it's fine to have packages in subfolders as long as you don't move them around after creating the packages list. You might be able to skip compressing and just name it 'Packages'.

Now open Synaptic Package Manager, at System / Administration / Synaptic Package Manager. It might ask you for your password again. To add your repository, go to Settings / Repositories, then go to Third-Party Software. Click '+Add...', which will ask you for an APT line, which determines where it looks for the Packages.gz within that repository since most will have many different channels they're hosting at once. We want a normal 'deb' repository with no fancy channels, so enter something like this:

```
deb file:///home/misaki/install/intrepid64-codecs ./
```

The three /'s, and the ./ at the end, are very important!! It means you look in the '/home' directory instead the 'home' directory, which doesn't exist, and for some reason without the final / (if you just put .), it bugs out also. If you mess this up and it doesn't load, press Alt-F2 to Run this or enter at the command line:

```
gksudo gedit /etc/apt/sources.list
```

This says, use gedit as root with no terminal to host it ('gksudo'), to edit the sources file that lists your repositories. Go to the APT line that you entered before and remove any syntax errors. Then go back to Synaptic.

Remove all other sources for now, such as under the Ubuntu Software tab in the repositories, because you can't load them right now anyway. Then press Reload in the main window to read the packages list you created for your repository. It should successfully load with no errors, and all your packages will show up and you can install them.


...or so you wish. Go to Uninstalled packages (under Status) and highlight everything, then Install. It should give a bunch of errors of what dependencies it couldn't find. Highlight everything in the list, save it to a text file on your flash USB drive, and do everything all over again... until it works. ^_^ Hope this helps!!

---

### Post by AXeS on 2009-02-23
i dont know what jitsu taemo is but its strong.

thanks a heck-of-alot Taemojitsu.
i've been searching most the day trying different searches except 'offline install' 
-should of done that search 1st i guess-

Thing is i download my apps and things elsewhere and small updates on windows using my cell-phone to connect to the net.
im new to alota this but getting somewhere with intrepid ibex. anyway my phones sofware is for windows only i guess.

thanx 4 the guide. gona follow it step by step.

-oyes im using my phones browser at the mo, dont have net at home yet, will very soon tho-

---

### Post by EXCiD3 on 2009-02-24
You guys should try out my new app called [Keryx]("http://keryxproject.org"). It is like synaptic that you take with you to get updates for those offline machines. You can add the repositories like medibuntu to Keryx's sources.list for your offline machine and use it just like you would use Synaptic.

---

### Post by hacktolive on 2009-04-03
Hi "created" an easier method to install ubuntu-restricted-extras offline:

[http://hacktolive.org/wiki/Ubuntu-restricted-extras_offline_installer]("http://hacktolive.org/wiki/ureoi")

---

### Post by albinootje on 2009-04-03
> **EXCiD3 said:**
> You guys should try out my new app called [Keryx]("http://keryxproject.org"). 

Looks promising, and a cool website setup!

---

### Post by EXCiD3 on 2009-04-03
> **albinootje said:**
> Looks promising, and a cool website setup!
Thanks, I'm looking forward to rewriting it from scratch over the summer to add more stability and a ton of new features. Give it a try and let me know what you think. :)

---

