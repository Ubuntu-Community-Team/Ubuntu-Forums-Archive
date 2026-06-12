---
title: "5 Major Freak-outs with Ubuntu conversion"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by afrodeity on 2008-07-24
1. I have now lost sight of my Window's XP desktop.
Ubuntu allows me to access my XP system which is now in a seperate partition thanks to the Ubuntu installer, but all those icons and stuff I leave on my desktop during XP sessions, well, what happened? Surely recognition should be automatic? Isn't there any way to swing my XP desktop folder onto a Gnome desktop? All I want to do is keep track of where I leave work, and this freaks me out.

2. Ubuntu Icon issues.
Ubuntu is not recognising html,xml, mhtml icons. They all look like system files which I don't usually touch, and I get lost when I am not concentrating, don't have time to focus, and can't read. I freaked out just showing a friend what my system looked like, because I couldn't recognise what I was seeing. Also, html 

3. HTML not coming up.
A lot of files I chuck onto my desk from a stick are simple html files. They come up gibberish, or in bad machine text, is this human?

4. Curve to greatness? Do I want to be insanely great?
One day my computer will be connected to the internet. Right now I have to do manual installations of software. I can't spend an insane amount of time getting to grips with debian. Why won't .deb files install automatically? Is it because somebody is building an enterprise version of ubuntu, and debian is the enterprise?

5.Boot issues.
Somebody please direct me to an insanely great application that will run off a boot disk, and give me disk geometry and advice on what to do about a 200gib harddrive. What if I want three partitions? A second harddrive? Grub is getting lost, innit?

---

### Post by lisati on 2008-07-24
1) Ubuntu and XP use separate areas for their desktops - remember that Ubuntu isn't Windows. Many (most) of the shortcuts that you find in XP have their equivalents in Ubuntu - it is possible to set up icons & the like on Ubuntu. (Google is your friend: look for "customizing your ubuntu desktop")

2) Try starting firefox and then setting it as the default browser. This might help set the associations properly. (An icon for firefox is on the menu panel at the top of the screen. You can also find it on the Applications->Internet menu)

3) Doing #2 might help here too.

4) The "add/remove programs" menu on the applications menu is your friend. Be aware, however, that for some of the programs you are likely to need a working connection to the internet.

5) Check the Add/Remove programs list of programs, there is likely to be something useful there.

---

### Post by cpetercarter on 2008-07-24
I am sure that others will try to help on these issues. Can I just say something about your html files? These are, I guess, files with an html or hml termination. You might expect that, if you try to open these in Firefox, they would display a web page, but in most cases this won't happen. Why? Because the web browser needs a whole load more information before it can display a complete web page - it will need style information, which is probably in a separate css file; it will need images; it may need javascript files, flash objects and other things which the html references but does not contain. Normally, the browser grabs this information automatically over the internet, but you say that you do not have an internet connection yet, so this can't happen. 

I don't understand what you mean by "bad machine text". If you open one of your html files in gedit, you will see the html in which the web page is written. If it is truly "bad machine text" then the file has got corrupted before you put it on your machine. But perhaps you mean that you do not understand what the html code is doing, which is fair enough but please don't blame your computer or the operating system.

---

### Post by The Cog on 2008-07-24
1)
I don't know where Windows hides your desktop files. They change the hiding place with every version. Once you find them, you can link to that location with a folder link on your desktop. Drag the windows desktop folder from the nautilus file explorer window to your Ubuntu desktop using the **middle** (wheel) button, and choose Link rather than Copy or Move in the pop-up menu.

2) Right-click an HTML file, choose Properties. You can click the icon (just left of the name) and choose your own icon for that file type.

3) While fixing 2), you can click the Opens With tab and choose Firefox as your default program for that type of file.

4) Don't understand your problem. .deb files install for me as long as the dependencies (other libraries it needs) are met. Can you explain furthre?

5) gparted will show you what disks/partitions there are, and allow you to change partitions. It won't give you advice though, and doesn't do anything with GRUB. It might be best to raise any GUB issues in a separate post.

---

### Post by oldos2er on 2008-07-24
Linux is built from the ground up to be a networking operating system; this is partly why .deb files expect a net connection to resolve any dependency issues when they install.

 Boot from the Ubuntu live cd, and run the partition editor from there, this will give you disk geometry. How to partition the disk is completely up to you.

 If you're switching back and forth from Windows to Ubuntu, that doesn't really sound like a "conversion." I don't think there's any way to morph a Win* desktop into a Gnome one--at least I've never heard of it (also I'm totally clueless about how Win* creates its desktop environment). Rhetorical question: Shouldn't you be working with files on a disk as opposed to icons on a desktop?

---

### Post by thecircusb0y on 2008-07-24
My advice may not be the best, but I'm having trouble understanding your grammar and english. Sorry if this doesn't help. 

1.) Ubuntu and XP are seperate OS's. Ubuntu's desktop is in your home directory. /home/<user>/desktop/
In my experience, I try to keep all my organization off the desktop, and use the desktop as a buffer, or temp folder of downloads and quick work, but clean it up regularly. 

2.) Try using advanced view by detail. Don't worry about the Icon's, if you know what the name of the file you need is, sort by file type and find the file. 

3.)Open them with firefox. 

4.)The Install/Remove programs application works great, and technically your going to want an internet connection to check for up to date programs. its in the settings-> administration menu I think. 
Debian is the base Linux distro that Ubuntu uses as a foundation. There is no conflict of enterprise vs desktop. 

5.) there is a good partitioning utility, I think its called GPartition. It has a gui interface. But I've never ran into a program that tells you how to partition your drive, except during a linux installation, and thats just basically calculating out how much ram you have, to how much of a swap you need, and then creating a main partition and a swap partition. A quick google of "How should I partition my new harddrive" should yield good results.

---

### Post by Paqman on 2008-07-24
> **thecircusb0y said:**
> 
5.) there is a good partitioning utility, I think its called GPartition.

Gparted (Gnome Partition Editor)

It's already on the Ubuntu LiveCD. It's best to run it from a LiveCD because you can't change a partition that mounted. By default, the LiveCD doesn't mount anything.

It's under System > Admin > Partition Editor.

---

### Post by afrodeity on 2008-07-25
I guess this is 2 out of 4. I know that I can go home and set the properties of my html files, which will hopefully open up in firefox. 

I know that I can map my desktop folder on xp to a folder in my ubuntu session, but this is iffy. Firstly there's the problem of mounting and unmounting my partition. I guess I should break the bad news, my windows xp partition is now totally not accessible. Can't mount it in my windows session either.

What I really want is insane - a goblinx application that will switch desktops, not just the flyovers, but the undercarriage. If only this software existed. 

How do I fix the mount problem with my xp? Is this a sign of conversion? I guess I should switch over comp-letely, but you have to understand the amount of time i spent turning my XP environment into something kool. Now I have all my data in the XP partition (not accessible), and bad disk geometry. Gparted isn't what one could call comprehensive. At least an application that will give me options if I want to move over to 1tb drive additions.

This is what I meant. Short of formatting my drive, what can I do to rectify a bad sitution, where it seems as if my drive has one partition, and a linux swap folder and that is it!!!!

Can't believe I actually did this, about five years of work which is not backed up in one place, finally reconcilled on my harddrive, only to have the ubuntu gremlin cast its spell.

As for debian install issues. I did a .deb install, and the applet ended up in an etc folder somewhere lost to only those who dare to look under the bonnet. I want a firewall!!! and the option of choosing what goes up inside my tool bar! Help, I want another coffee, but can't get over the addiction.

---

### Post by oldos2er on 2008-07-25
It sounds as though your Windows was not shut down cleanly. Perhaps another Win* user can help you rectify that.

 Ubuntu comes with a firewall, called iptables. Hardy also has ufw: [https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by Titan8990 on 2008-07-25
So you installed an OS that you don't know how to use without backing up your data and you blame Ubunutu?

What is the output of fdisk -l? In the terminal type this:

sudo fdisk -l

and post the output.

---

### Post by cariboo on 2008-07-25
As far as installing .deb files, just double click the file and gdebi will open up and tell you if it is installable or what other files you need to install it. You seem to have an internet connection now why can't you just temporarily connect to download and install the files you want to install?

Jim

---

