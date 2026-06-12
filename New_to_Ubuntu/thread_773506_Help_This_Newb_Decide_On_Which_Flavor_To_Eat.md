---
title: "Help This Newb Decide On Which Flavor To Eat"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by leotemp on 2008-04-28
Okay, i've had the worst week ever thanks to both Mac Os and XP/Vista. I'm so pissed off right now I hope the devs at both those companies choke to death on bees and that includes people I know over there.

At any rate, i need advice on which flavor of ubuntu to install, i see there are different options and of course this confounds my primitive brain. I am a designer and im mainly looking for a platform that looks equally impressive shell wise as vista or macOS as at my work they show case us like animals in a zoo. I also play a lot of games. Photoshop is a must but i figure i can use wine like on other nix.

Can anyone out there point to a specific flavor and say, "thats the one for the user thats used to windows but wants eye candy and games" I know ill probably have to do some manual stuff to get directx going and everything else and thats fine as long as it rocks when I'm done.

I also have the following more technical questions (technical for me anyways)

1] I dont have any other partitions on my drive as it stands and im wondering if its common to lose data when creating a new partition in the install of ubuntu

2] If say i decide to go with kubuntu then do i need to just download kubuntu or do i need the ubuntu install and the kubuntu install?

Many thanks in advance.

---

### Post by thisiam on 2008-04-28
Ubuntu is a good one to install, you can download kubuntu and install it without having Ubuntu.
never used it but from what i have read photoshop with wine doesn't work so well, check out the gimp.
you can partition your hard drive from the Ubuntu live CD install

---

### Post by mrdosa on 2008-04-28
I think Ubuntu is good. You dont need Ubuntu for installing Kubuntu. Kubuntu has K Desktop Environment instead of Ubuntu's Gnome Desktop.
Remember that there is a learning curve to Ubuntu. And you will need some patience, but once you do learn it well, you will get the freedom you always needed!! Really powerful!!
Ubuntu with beryl and other window decorators will give you a great eye candy!! It rocks!!

---

### Post by sheilnaik on 2008-04-28
+1 for Ubuntu from me too.  Kubuntu is fine, I'm sure, but I think Gnome is much more sexier than KDE.  As far as looking cool, you can enable visual effects like wobbly windows straight from the appearance menu item after you install Ubuntu.  It's literally as easy as checking a box.  More in-depth options for visual effects are also available after installing a simple package (again, just checking another box).

There are two things you should remember when you install Ubuntu:
1. Hardy Heron lets you install the whole Ubuntu OS right inside Windows, so you can get an experience much closer to the real thing (in terms of speed) than just a Live CD right from XP.  Definitely take advantage of that.

2. You can install VirtualBox, and then install Windows XP right inside Ubuntu.  That means that even if you think GIMP isn't a good equivalent for Photoshop, you can still run CS3 right inside VirtualBox.  I use it all the time for Office 2007 stuff, since some advanced PowerPoint 2007 slides don't load perfectly in OpenOffice as of now.

---

### Post by leotemp on 2008-04-28
Thanks for the reply guys, Im not worried about working hard to get it going as i spend about 10 hours a week fighting MacOs and XP to work the way i paid them too so that is fine.

Anyone know about my risks losing data doing the partition during install?

---

### Post by mrdosa on 2008-04-28
If you use the "Guided - resize the partition and use the freed space" option during installation, i dont think you will lose any data. You will need to run a good defrag before on your windows or mac before you start off with this option as it uses contiguous free space. 
When you choose to make a new partition, [as far as I know] you need available free space, so you may have to delete some partition.

---

### Post by spacefreak86 on 2008-04-28
I'm running Kubuntu, but I've heard that Kubuntu / Ubuntu is just a matter of desktop preference, as most aps can run on both. 

As for games, linux does have some games, but they run on OpenGL, not DirectX, as DirectX is one of the very few things that Microsoft actually did right, but as such, it only runs on Windows. Luckily, there is a program called "wine" that runs many windows applications that you might need. Sadly, Halo isn't one of them :(  But hey, if you're a developer and want to work on OpenGL or wine to get them to have equivalent technologies to DirectX, please, go for it!


I believe many people have gotten Photoshop to work under wine, although there is GIMP, which can be used on Windows and *nix. Give it a try under windows to get used to the interface and see if it works for your needs. Otherwise, try installing Photoshop under wine.

Partitions depend on how you set things up. Linux uses a swap partition, whereas Windows uses a pagefile.sys. Each works as the virtual memory, ontop of your RAM. I don't know anything about Macs, but I would assume they have some equivalent thereof. Since in Linux it is an actual partition, you have to make one yourself. If you have plenty of RAM on your system ( > 1 GB), you shouldn't need a swap partition more than 1/3rd to 1/2 of your RAM total. 

Some linux users, especially gamers or those who require specialty software that is not 100% compatible with Linux have the option of dual-booting. On my own system, I have XP Pro on one side for the specialty software (Origin, Halo, and a few other things), then have my swap partition, then Kubuntu on a third partition. It will be useful to know that Linux is able to see the NSFS and FAT32 drives under Windows, but Windows doesn't natively see the ext3 (or other file system) that Linux may be running over. I have heard there is a plug-in for Windows somewhere, but I just keep all of my documents and files and such under the Windows partition in case I need to load them through dual-booting.

As far as downloading Ubuntu / Kubuntu: if you have in mind which desktop system you want, download that version. You can always download the packages for GNOME or KDE later on and switch them out, but it takes time and bandwidth to do so.

Hope this helps and good luck!

---

### Post by schauerlich on 2008-04-28
> **leotemp said:**
> Anyone know about my risks losing data doing the partition during install?

Any time you mess with partitions, there's the risk of losing data. Make a back up if at all possible. You might be 99% sure your data will be safe, but with a backup, you'll be 100% sure.

---

### Post by leotemp on 2008-04-28
I was under the impression that one could if they were in fact insane get directx 9 to run on linux, is that wrong?

Also, i notice when i put the iso in my drive it says i can install it in windows (MAGIC!) and that seems pretty damn easy, is it better to boot to it and install it from the drive or does it not matter?

---

### Post by Xiong Chiamiov on 2008-04-29
Just want to give a +1 for Kubuntu.  Eye-candy wise, it's a matter of preference.  KDE 4 is supposedly sexy (it looks like Vista), but I very much like [my KDE 3 setup]("http://picasaweb.google.com/xiong.chiamiov/ScreenshotsDesktop").  It's nothing super fancy, but it's super-customizable.

---

### Post by acelin on 2008-04-29
Booting it for a clean install.

What you have there is Wubi, which allows you to install it into its own folder/partition within windows and boot into that.

---

### Post by Kinst on 2008-04-29
Wine-doors can autoinstall Photoshop CS2 which works near perfectly.

---

### Post by alienexplorers on 2008-04-29
Ubuntu is pretty clean compared to kubuntu.  If you want the eye candy go with kubuntu.  If you are looking for a nice operating system with a straight forward look go with Ubuntu.  Ubuntu can be dressed up with compiz if you want it to be a bit fancier.

---

### Post by FredB on 2008-04-29
What about downloading live of each flavour and see which one you will install ?

I prefer Ubuntu because I didn't like at all KDE (and this, since its 0.12 days).

So, just look at Ubuntu (gnome), Kubuntu (KDE) and Xubuntu (Xfce) live cd.

Test them, you only will know what you prefer after all.

---

### Post by Sef on 2008-04-29
Most people here run Ubuntu, so it is better to start off with that.  After you get used to GNU/Linux, you can switch to Kubuntu and check it out.

---

### Post by zaivala on 2008-04-29
OK, so a newbie (like me) picks a flavor, and then finds the flavor not to his liking...  I wubi'd KDE4buntu... am finding out that it is not a finished desktop and would like to go back to 3.5x.  Do I have to uninstall my _buntu and reinstall?

---

### Post by muteXe on 2008-04-29
I believe you can switch from kbuntu to ubuntu from the command line (can't remember the command, i'm a noob too sorry).  Or I think you can change the kind of session you're in on the log-in page (kde, gnome or xfce i think).

Linux Mint looks pretty nice as well, although i've not played around a lot with this distro.

mute

---

### Post by davidgypsy on 2008-04-29
Plain Ubuntu recieves the most development and attention and just simply works. Stick with that and you won't go wrong!

Of course you could try them all out on live discs before you make a final decision... ;-)

---

### Post by zaivala on 2008-05-03
You're absolutely right about Ubuntu.  I found that K4 was not ready for prime time, and uninstalled, re-installing (Gnome) Ubuntu.  Other than not liking the orange desktop (I fixed that, I'm not THAT stoopid), this is by far the best Linux experience I've ever had, and the first one that exceeded my Windows experience.  One more item and I can leave Windows forever...

---

### Post by Paqman on 2008-05-03
> **leotemp said:**
>  i see there are different options and of course this confounds my primitive brain.

The difference is largely cosmetic. Besides, you can install any of the other versions after you install, so which actual disk you use to start off is immaterial. After installing off a Kubuntu disk you could then install Gnome and XFCE, and take your pick at login. It's all the same system underneath, it's just dressed in different clothes.

You can also use the aps from one desktop environment in any other environment. There's nothing stopping you using Brasero in KDE and K3B in Gnome, for example.

---

### Post by the8thstar on 2008-05-03
One man's KDE is another's Gnome. ;)

---

### Post by days_of_ruin on 2008-05-03
As for games, enemy territories quake wars has a linux installer:)

---

