---
title: "Dos"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by Marc St Louis on 2012-04-09
Posted about this earlier but it's vanished.

I have a few old Dos programs that I would like to use but don't really want to install an old version of Windows, 98 or 95.  Will Ubuntu work with Dos?

---

### Post by sffvba[e0rt on 2012-04-09
[Dosbox]("http://www.dosbox.com/")

It should be available in the Software Center.



404

---

### Post by Marc St Louis on 2012-04-09
I'm not looking for games.  I just want to know if Ubuntu will work with dos programs

---

### Post by eriktheblu on 2012-04-09
You will have to use an emulator, like DOSbox.

---

### Post by mastablasta on 2012-04-09
> **Marc St Louis said:**
> I'm not looking for games.  I just want to know if Ubuntu will work with dos programs

DosBox work with all dos programmes so far. It' san emulator that is now quite well optimised, so you should see any slowdowsn when running it. though it has an option to slwo things down or increase speed if necessary.

there are also nice GUI interfaces if you don't want to sue dos commands.

can run games, but can also run various dos based programmes. emphasis on DOS not windows. for windows porgrammes there is wine.

---

### Post by santosh83 on 2012-04-09
> **Marc St Louis said:**
> I'm not looking for games.  I just want to know if Ubuntu will work with dos programs

While DOSBox is optimised for games, it should work with most plain DOS applications too. Alternatively consider DOSEmu.

---

### Post by dniMretsaM on 2012-04-09
You could also run [FreeDOS](http://www.freedos.org/) in a virtual machine (instructions for installing on VirtualBox [here](http://sourceforge.net/apps/mediawiki/freedos/index.php?title=VirtualBox)).

---

### Post by anewguy on 2012-04-09
Since linux isn't DOS, no you cannot directly run a DOS program of any type in Linux.  You must first have a "go-between" to interpret the DOS program and it's antiquated machine code and system calls in a way such that Linux code and system calls (which are VERY different) can be used.  So in essence, you have a go-between program that "runs" the DOS application.  This go-between program runs as native Linux.

For DOS, such a go-between is the already mentioned DOSbox.  For Windows applications, the go-between is the already mentioned Wine project.

So, pay no attention to something saying it is opotomized for games, allows you to play games, etc..  The important thing is that it allows you to run DOS programs of any type.

Is this a 100% guarantee it will work?  No.  But it should.

So, try DOSbox as not found recommended.

Dave ;)

---

### Post by na5h on 2012-04-09
> **not found said:**
> [Dosbox]("http://www.dosbox.com/")
It should be available in the Software Center.

+1 For DOSBox.

It's quite easy to set up too:
[http://www.ubuntugeek.com/howto-auto-mount-a-drive-in-dosbox.html]("http://www.ubuntugeek.com/howto-auto-mount-a-drive-in-dosbox.html")

---

### Post by houseworkshy on 2012-04-09
DosBox is excellent, runs every dos thing I've ever had.  One can also alt+return it in and out of full screen mode.  the help section is very good.  I usually bung in a special dos directory in the home directory and configure the thing to open up there, just makes it easy.  
  
Remember that it is a virtual machine so you have to go through the installation bit with the programs and that with dos things that was not always the .exe file,  often a batch file ( .bat ).  After things have been installed dragging the appropriate file onto the Dosbox icon will often ( not for all things  and I don't know why ) open dosbox with the selected programs running.

You can fiddle around with the virtual machine too, it has support for several of the sound cards of the era, soundblaster etc.  So if the program you are running in DosBox  isn't happy with the non-existant hardware it thinks it's running on you can alter it's hallucination to fit.  Another nice feature.  

Have fun

A lot of old dos programs are now abandon ware so available for free.  This is a good one for games     [http://www.abandonia.com](http://www.abandonia.com)  They're very good on copywright so no legal worries with anything you download from here, if the rights get brought up they keep the info on whatever it was but pull the download.  There are also similar sites for app's but I don't know any off hand, I enjoy a bit of occasional retro gameing but retro application using doesn't have the same appeal for me somehow.

Just and addition.  You mentioned windows. There is also a windows emulator called wine which is superb on the older unsupported windows programs and often ok for the newer things.  My experiance of it is that it will run everything from the 3.11 to win98 era, most of the XP stuff, less of the vista stuff.  Don't know about the later ones.  One chooses which version to use each time if you like.  It is a good idea to delete the ability to open anything anywhere ( in it's settings remove the / drive, in the wine settings that is NOT your PC  ) and have it run from it's virtual hard drive which will be a hidden file in /home/yourname.    This is because it is prone to windows malware, and you don't want it to have root privaleges.   I wound't recomend going online with it ( or DosBox ).  When getting .exe files for it just put them on its virtual drive where it can see them.
Wine is also available from the software centre.

---

### Post by underquark on 2012-04-09
Nobody has asked yet - what are the old DOS programs that you want to run? There might be an equivalent or better that will run native in ubuntu.

---

