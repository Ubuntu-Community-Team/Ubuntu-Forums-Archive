---
title: "How to Install e-Sword via Wine"
date: 2007-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by shane2peru on 2007-01-06
**EDIT:  NOTE: ** Ok, if you want an easier way, just grab the deb from [this post here]("http://www.ubuntuforums.org/showpost.php?p=2224828&postcount=1")  Jereme has done an excellent job getting this into a deb, and a super easy installation process as well as installing modules.  Unless you like rolling your sleaves up and getting into the workings of Linux, just grab the deb from the link above and run with it!
March 31, 2007.

**EDIT: NOTE:**  You don't want to use wine version .9.38 with e-Sword.  It has problems.  You can [follow this thread]("http://ubuntuforums.org/showthread.php?t=462097") and fix the wine installation.



Ok, my first real how to so be patient.  We are going to install E-Sword (located at [www.e-sword.net](www.e-sword.net))  Go there and download the latest full version at the time of this writing it is 7.8.5 located here:  [http://www.e-sword.net/downloads.html](http://www.e-sword.net/downloads.html)  Select the Application Installation it is around 18 MB file.  Save it to your home directory.  This has been tested on Edgy, and works fine.  I'm about 99% sure it will be the same on Dapper.  I will try and help if you have any problems just post your questions here.  I'm not a Guru by any stretch, just trying to help out the community that has helped me out so much!

**Install Wine:**
First of all we need to install wine open a terminal **Applications -> Accessories -> Terminal**  Keep this open because we will do most of our work here.  Wine has greatly improved, it is still not a miracle working program, but it has greatly improved.  In the terminal we are going to install wine ```
sudo apt-get install wine
```  you should get the latest greatest version in the repos with this.  (You may need to enable Multiverse or Universe repositories to get wine. I really don't remember now.)  Ok, wine should be all installed now we need to configure it.

**Configure Wine**
In the Terminal that is still open we are going to type/paste ```
winecfg
```  When the window pops up, we are going to click on the Library tab.  We are going to type in the little box riched20 and then click on the add button.  Now we can close that box, everything should be fine now.  

**Install e-Sword**
Ok, remember the file we downloaded into our home directory.  We are still in the terminal, when we open it, it automatically opens in our home directory, (if you aren't there you will need to switch to there.)  Next type/paste ```
wine setup785.exe 
```  and click your way through the installation process that Windows is known for.  You are all set!  There should be an icon on your desktop just double click and enjoy.  We will need to configure one thing to prevent crashing.  (At least you used to have to. If anyone wants to verify that it won't crash that would be great.)  After you Open E-Sword you will need to close the tip box, be-careful not to let your mouse go over any of the Strong's numbers as that is what crashes the program.  You need to go to Options and unselect the display Strongs # tool tips.  Now you are all set to run e-Sword!  If not you can run it by running in the terminal ```
wine ~/.wine/drive_c/Program\ Files/e-Sword/e-Sword.exe 
```

**Advanced configuration**  (This step is not necessary unless you want to use the Strong's # tool tip)

We are going to take one of the msls31.dll files and paste it into our wine configuration.  If you have a mount point for your windows partition you can skip this step.  90% of the people dual booting one a single hard drive are going to find there windows partition located at hda1 - if that is not where your windows partition is located then you will need to plug in the correct setting here.  In the terminal we are going to paste/type ```
sudo mkdir /mnt/temp 
```  Ok now in the terminal ```
sudo mount /dev/hda1 /mnt/temp 
```  Now ```
cd /mnt/temp
```  if you get an error you may need to run **sudo** before that command.  Now we are in our windows directory so be careful here!  Don't be deleting things or you could mess up your windows installation.  Next ```
cd windows/system32/
``` I'm quite sure that is the right directory.  Now in the terminal ```
ls msls31*
```  If it is there Great, now we are just going to copy it with ```
cp msls31.dll /home/**username**/.wine/drive_c/windows/system32/
```  you may need to run that command with a sudo in front of it.  Now lets change the permissions type ```
cd ~/.wine/drive_c/windows/system32/
```  Now we are back in the wine directory and type ```
sudo chown **username** msls31.dll 
``` and ```
sudo chgrp **username** msls31.dll
``` and one more ```
chmod 644 msls31.dll
```  Now you can close the terminal you are done.  Open E-Sword an you can enable your Strong's # tool tip and they should work great!  You are done!  

**Installing more modules**

Just as a tip, someone else told me, if you have trouble installing more modules, and want to install them, you may need to put them in your e-Sword directory under .wine (it is a hidden file so enable view hidden files in Nautilus ctrl-H)  Go to your drive_c, Program Files, e-Sword directory and paste it there.  Now to install it you will need to right click on the .exe file and select open with wine and it should install.  

Please feel free to post any questions!
Enjoy E-Sword!

Shane

---

### Post by Scott A on 2007-01-13
What if Dansgardian won't let us download e-sword?

---

### Post by Scott A on 2007-01-13
Hi, 
I downloaded E-sword to my desktop, but the directions for installing it give me the error message:

> saurand@saurand-desktop:~$ wine setup785.exe
wine: could not load L"c:\\windows\\system32\\setup785.exe": Module not found
saurand@saurand-desktop:~$ 

What did you mean about the home directory when you said > Install e-Sword
Ok, remember the file we downloaded into our home directory. We are still in the terminal, when we open it, it automatically opens in our home directory, (if you aren't there you will need to switch to there.) Next type/paste

I am new to ubuntu and to linux, so sometimes I don't get the simplest things.

---

### Post by stalefries on 2007-01-13
Or, you could just install BibleTime (KDE) or GnomeSword (Gnome).

---

### Post by shane2peru on 2007-01-13
> **stalefries said:**
> Or, you could just install BibleTime (KDE) or GnomeSword (Gnome).
Stalefries,

E-Sword has far more resources than the Sword project, and many Windows users are extremely use to using e-Sword.  It is also nicer in my opinion than using GnomeSword, or BibleTime.  Also E-Sword allows users to make modules, and there are tools out there that allow you to make your own modules rather easily (original content, not copy righted material).   

> **Scott A said:**
> What did you mean about the home directory when you said
Quote:
Install e-Sword
Ok, remember the file we downloaded into our home directory. We are still in the terminal, when we open it, it automatically opens in our home directory, (if you aren't there you will need to switch to there.) Next type/paste
I am new to ubuntu and to linux, so sometimes I don't get the simplest things.

Ok, Scott, I thought that may be a problem for a new Linux user.  You will need to run this command in the terminal before running the setup***.exe.  ```
cd Desktop
```  Then you will be able to run ```
wine setup785.exe
```  Of course the numbers have to match the version that you downloaded.  If you have any more questions feel free to ask.  The Home directory is under your user name it is kind of like the "My Documents" of windows.  It is located at /home/username/  and your Desktop is located at /home/username/Desktop .  I hope that helps a little.


Shane

---

### Post by stureharry on 2007-06-05
I took away the new Wine and put in the old Wine, but this with downloading e-sword stops when I get the non-finding sentence above. Is it possible to get a *.deb-file with E-sword? I am quite satisfied with Bibletime, but Gnomesword for Ubuntu is not functioning. By the way, Gnomesword 2,2,3 for Fedora 6, is working. Perhaps downloading a rpm-file and then alien can make it.

---

### Post by shane2peru on 2007-06-05
> **stureharry said:**
> I took away the new Wine and put in the old Wine, but this with downloading e-sword stops when I get the non-finding sentence above. Is it possible to get a *.deb-file with E-sword? I am quite satisfied with Bibletime, but Gnomesword for Ubuntu is not functioning. By the way, Gnomesword 2,2,3 for Fedora 6, is working. Perhaps downloading a rpm-file and then alien can make it.

If you look at the **NOTE** in the very first post, it has the location of the deb file that you can download and run.  Just make sure you don't have wine .9.38 installed, as we have seen many problems with e-Sword and that version of wine.  You want the version .9.37 for now.  Check the forums as there has been much discussion about that under the **3rd party -> Ubuntu Christian Edition** forums.  If you need anything else just post back.

Shane

---

### Post by jesse100 on 2008-05-22
I have a problem installing the modules. 

"Just as a tip, someone else told me, if you have trouble installing more modules, and want to install them, you may need to put them in your e-Sword directory under .wine (it is a hidden file so enable view hidden files in Nautilus ctrl-H) Go to your drive_c, Program Files, e-Sword directory and paste it there. Now to install it you will need to right click on the .exe file and select open with wine and it should install."

I tried this but it will not work. The setup wizard freezes. What could it be?

Jesse

---

### Post by shane2peru on 2008-05-22
> **jesse100 said:**
> I have a problem installing the modules. 

"Just as a tip, someone else told me, if you have trouble installing more modules, and want to install them, you may need to put them in your e-Sword directory under .wine (it is a hidden file so enable view hidden files in Nautilus ctrl-H) Go to your drive_c, Program Files, e-Sword directory and paste it there. Now to install it you will need to right click on the .exe file and select open with wine and it should install."

I tried this but it will not work. The setup wizard freezes. What could it be?

Jesse
Jesse,

How did you install e-Sword, via the deb, or by yourself?  This thread is quite old, and wine has dramatically changed since the time of this thread, Ubuntu has too. :)  What you can try is this, save the file to your desktop, and open the terminal **Applications -> Accessories -> Terminal**  In the terminal type ```
cd Desktop
```  (cd stands for change directory)  Desktop is the location we are moving too.  Now type in the terminal ```
wine modulename.exe
``` of course you will need to replace modulename with the name of the module you want to install, then post the errors that show up in the terminal after it locks up on ya.  We will go from there.

Shane

---

### Post by tarant8l on 2008-06-12
greetings from Venice Italy
you are closer to Taiwan perhaps you know

i tried to install e-sword on 
asus eeepc 
running default xandros linux

but the text does not show
the search produces text so the install is ok bnut the
bible and commentaries don't show
perhaps i need a windows program to show text> 
here i was dumb folded
just at the moment when i wanted to uninstall the second time
i found your thread
perhaps help

[email]klaudio_zic@yahoo.com[/email]

---

### Post by pantherse on 2008-06-30
Hi,

Has anyone installed esword 7.9.8 on Ubuntu 8.04? Basically the only things displaying something are the tree on the left that shows the bible books, and the chapters that you can click on, part of Strong's, the one that has H1, H2, etc.

Any help would be appreciated.

Thanks

---

### Post by jerrallan on 2008-07-07
I have 8.04. I have installed E-sword twice.  The last time after Ubuntu crashed.

I followed this howto:
[HTML]http://ubuntuforums.org/showthread.php?t=404042[/HTML]

---

### Post by combro2k on 2008-07-21
pantherse did you do the trick winecfg?

winecfg go to libraries,
type in msls31 press add,
type in riched20 press add.

And some people say that you need to add oleaut32 also for faster
responds in e-sword... I don't know if that is true... I am checking that out now...

Good luck,

bless,
Martijn

---

### Post by uboer on 2011-03-03
For new installations also see
[http://art.ubuntuforums.org/showthread.php?p=10516525#post10516525](http://art.ubuntuforums.org/showthread.php?p=10516525#post10516525)

---

