---
title: "Running the OLPC XO Image Under Qemu"
date: 2006-11-21
forum: Outdated Tutorials &amp; Tips
---

### Post by spyke01 on 2006-11-21
[SIZE="6"][COLOR="Red"]**_Emulating the OLPC XO On Ubuntu_**[/COLOR][/SIZE]
This guide is to emulate the OLPC XO operating system on Ubuntu Dapper Drake, it should convert to Edgy and beyond easily, although you may run into a few problems.

**_Programs Needed:_**

Qemu v0.8.1 or greater
GCC 3 or greater

**_Installing The Programs:_**

The easiest way to get the newest version of Qemu is to download the binary distribution from [http://fabrice.bellard.free.fr/qemu/download.html](http://fabrice.bellard.free.fr/qemu/download.html)

Save the file into the root director and open a terminal and issue the following commands:
```

cd /
tar xzvf qemu-0.8.2-i386.tar.gz

```

This will extract the files into their neccessary directories and thats it!

**_Downloading the OLPC XO Image:_**
Open a web browser and navigate to [http://wiki.laptop.org/go/OS_images](http://wiki.laptop.org/go/OS_images), under the section entitled " Latest Stable Build" there will be a link to the latest stable version. Follow the link and navigate into the ext3 folder. Iniside there will be severl files, the one we want to download is the one ending in img.bz2. Once you download the file, extract the image to anywhere you want, and then go back to your terminal.

In our example we extracted our image to the desktop, so we need to issue the following commands:
```

cd ~/Desktop
qemu -hda olpc-redhat-stream-development-build-182-20061114_2135-devel_ext3.img

```

Depending on which version of the image you get, you will need to change the image name. After you issue the command, a black window will pop-up and the boot process will begin.

**_Using the Desktop:_**
*Excerpt and photos from: [http://www.osnews.com/permalink.php?news_id=16487&comment_id=182482](http://www.osnews.com/permalink.php?news_id=16487&comment_id=182482)*
Here is a screenshot from QEMU image interface:
[img]http://blog.fasttracksites.com/images/uploads/olpc-desktop-interface_original.png[/img]
Top left screen:
- Virtual mode mode, group mode, individual mode and recent ccess

Top right:
- Shutdown button, wireless status and window switcher

Bottom left:
- Etoys: educational programming language that is part of the Squeak Smalltalk language.
- Chat: a simple chat interface
- Browser: gecko based using xulrunner
[img]http://blog.fasttracksites.com/images/uploads/olpc-browser_original.png[/img]
- Memory games
- Penguin TV: to view multimedia
- Abiword: 
[img]http://blog.fasttracksites.com/images/uploads/olpc-abiword-panel_original.png[/img]
- Tam-Tam: a music synthesis tool 
[img]http://blog.fasttracksites.com/images/uploads/olpc-tamtam_original.png[/img]

**_Notes and Thoughts:_**
The build used in this tutorial is Build 182, later builds may appear different. From what I've seen so far, i believe a regular linux desktop would be more effective than what is shown here. By looking at the mockups on the OLPC wiki page, theres great things in the future. However from the current setup, they have a long way to go.

---

### Post by artik on 2006-11-26
More tip - if you want internet... on load in grub press "a" and add "2" at the end and you'll boot to init 2 mode.
Then run command dhclient
Test if there is internet by ping [www.google.com](www.google.com)

Then you can go to init 5 as work as usual.

---

