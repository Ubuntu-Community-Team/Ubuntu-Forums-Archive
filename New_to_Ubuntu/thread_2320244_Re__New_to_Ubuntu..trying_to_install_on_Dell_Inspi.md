---
title: "Re:  New to Ubuntu..trying to install on Dell Inspiron 3520"
date: 2016-04-12
forum: New to Ubuntu
---

### Post by edward41 on 2016-04-12
I recently lost my hard drive on my Del Inspiron 3520, i3-2370M CPU @ 2.40 GHz x4..  Now running Ubuntu 12.10

It came with windows 8 pro 64 bit installed but when I went to reinstall I realized that I had no windows 8 install disk or a windows 8 code to use to activate it anyways.  I have just gone through all of this with one of my sons computers, a Gateway with windows 8.1 core, his hard drive died about a year ago and I bought a new one and then realized it also did not come with a windows code or windows software, this is making me a bit angry, I am long past tired of the money grubbing tricks Microsoft and computer manufacturers are using to try and squeeze every cent they can out of people.  I have been considering moving away from Windows to Ubuntu for years now and finally here I am...

It just so happens that I downloaded Ubuntu a couple months back on my old desktop pc to try and mess around with it in virtual pc, I was never able to get it to actually do anything and gave up on it.  When I got my new hard drive for my Dell laptop computer today I burned the Ubuntu iso onto a dvd and installed it.

I spent a while exploring the icons and what not seeing where everything is, then went to trying to setup and test things out... I noticed a number of things unable to function normally or at all on the laptop, I thought it likely to be driver issues and so attempted to pull drivers off of my driver cd, I apparently cannot even read the cd, not that it would likely do me any good anyways.

Okay, so here goes with a list of things that I have to try to figure out...

1.)  Is it even possible to run this laptop effectively with Ubuntu?

2.)  Wireless, I have no wireless capability with Ubuntu, is there anyway to deal with this?

3.)  CDROM/DVD drivers, I seem to have basic function but no more than that at the moment.

4.)  Sound, my sound does not appear to work, at least as far as I can test as yet, I am unable to play any kind of media at all so it is hard to tell exactly.


Some other questions that I seem to be having some trouble with...

1.)  How do I get to a command or DOS type prompt?

2.)  How do I find network settings, IP settings etc...  I have a network folder but it gives no options or settings..

3.)  Why am I unable to set computer date and time or change the location?

I have a dozen other computers that I could try Ubuntu on, am I better off going back to windows on this computer and trying on another machine?   Currently it seems very unlikely that I will be able to get this computer to run effectively on Ubuntu, but I am willing to give it a shot if anyone who has more experience can give me some guidance as to where to start and where to go...  other than He double hockey sticks anyways... lol...

OK, I found this having to do with my wireless, apparently I am not the only one with this computer that had this experience with the wireless problems..

(First thing you need to do is download the driver. Do a google search for 'broadcom bcm43142 driver linux download deb' Download the appropriate .deb file. Then assuming you downloaded to ~/Downloads open a terminal and:  )

sudo apt-get install dkms
cd ~/Downloads
dpkg -i wire*.deb   


Now the three lines above are confusing me a bit, this appears to be command line or dos, forgive my lingo I have been using windows for more than 20 years.  Pretty much everything I have looked up regarding Ubuntu shows that dos type code being entered.  I do not see any type of dos or command line functionality within Ubuntu, am I missing something?....   I could just install my python 3.5  and just use that I suppose..

---

### Post by mörgæs on 2016-04-12
Hi, welcome to the fora.

Ubuntu 12.10 is out of support. I suggest that you do a fresh install of one of the supported releases using a wired internet connection, wiping the old installation in the process. When that works and you are able to get online we take a look at the next steps. 

> **edward41 said:**
> 
I have a dozen other computers that I could try Ubuntu on

If any of these are old you might find some inspiration in the link in my signature.

---

### Post by mastablasta on 2016-04-12
CLI interface is called terminal.

you should be able to get drivers using additional drivers application (software & updates tool). [http://www.omgubuntu.co.uk/2015/10/10-things-to-do-after-installing-ubuntu-15-10](http://www.omgubuntu.co.uk/2015/10/10-things-to-do-after-installing-ubuntu-15-10)

network is under system settings: [https://wiki.ubuntu.com/SystemSettings](https://wiki.ubuntu.com/SystemSettings)


as for sound we would need to know your hardware. you can display it and then copy it from terminal with this command:

```
sudo lshw -sanitize
```

or use *hardinfo* program (I am not sure if it's pre-installed or not since I use Kubuntu)


CD/DVD - I am not sure what kind of drivers you need. the ones provided by the OS can do everything. what function is missing in your case?

---

### Post by edward41 on 2016-04-12
I have given up on Ubuntu at the moment, way to many things to download from way to many places, if everything could be in one place to download what I need then maybe...  I will spend weeks setting this up to use the programs that I want to use, or I can go back to windows and spend a few hours....

Now to figure out how to reformat the hard drive....  apparently windows cannot reformat to an ntfs format, and apparently the Ubunut does not come with any partitioning software to remove the current format....  man I should never have tried messing with this...

Now I will spend hours downloading another dozen things off the internet until I find something that will reformat the hard drive... arghhh....  Maybe in a few years I will come back and try Ubuntu again...

This is going to be tough....  I have no working Ubuntu computer, no way to access internet or anything, all internet access is through my windows computers....  how exactly do I download the Gparted onto my windows system and then burn a boot cd for the Ubuntu system?...  One would think that Ubuntu would come with a way to remove it in the software you to use install it, this is retarded....

Can anyone point me to a downloadable .iso that I can download and directly burn onto a cd or dvd to boot the Ubuntu machine with that will allow me to remove any partitioning and formatting on the hard disk?  Something like this must exist.... though I cannot find anything...  I have found many instances of other people having this same problem though...

Most answers say to download gparted and create a bootable disc and remove partitions and the directions as to how to do this are for the Ubuntu computer which I cannot use to do this....  all the downloads at gparted are zipped file downloads rather than a .iso file format though...  So how do I create a .iso for an Ubuntu system on a windows computer?

---

### Post by howefield on 2016-04-12
> **edward41 said:**
> ....  all the downloads at gparted are zipped file downloads rather than a .iso file format though...

[https://sourceforge.net/projects/gparted/files/gparted-live-stable/0.25.0-3/](https://sourceforge.net/projects/gparted/files/gparted-live-stable/0.25.0-3/)

---

### Post by edward41 on 2016-04-12
Now I am unable to boot from any kind of cdrom or  dvd rom, my system just bypasses it and goes straight into Ubuntu, this Ubuntu is a freaking nightmare....

*I tried the download link, the Nero burn software is for some reason unable to even see the program, windows can though...   Back on the search for something to delete these Ubuntu partitions...  I may have to break down and invest the three hours to drive to town and have VGH computer erase the hard drive for $20, probably be faster and far more effective than trying to find something on the internet.*

---

### Post by yancek on 2016-04-12
> It came with windows 8 pro 64 bit installed but when I went to reinstall  I realized that I had no windows 8 install disk or a windows 8 code to  use to activate it anyways. 

Most major manufacturers of computers coming with any windows pre-installed do NOT and have not included an installation CD/DVD for about the last 10 years.  This is usually an added cost, $15-$25 depending upon the manufacturer.

You should have the product code on the computer case if it is a Desktop, bottom front or side usually.  A laptop should have it on the bottom

Windows 8 and newer pre-installed almost always come with a newer method called UEFI.  If that is how the windows system is installed then any other system (Linux/Ubuntu) must be installed in UEFI mode or one of the systems won't boot.

> so attempted to pull drivers off of my driver cd

Linux drivers are almost always in the kernel.  Drivers you get with some hardware are almost always ONLY for windows and that is usually stated on the CD.

You could probably run Ubuntu, at least one of the versions on that computer.  One important factor you did not mention is the amount of RAM you have.
Problems with wireless or sound, there is an icon in the left panel and if you mouse over them, one will show System Settings and clicking on that will allow you to change most settings.

What you refer to as a Dos prompt is called a termina/konsole in Linux.  With Ubuntu you can easily access it by clicking the Dash which is the Ubuntu logo in the extreme upper left of the Desktop where you will see a Search entry box.  Type terminal.  Alternatively, simultaneously hold down the Ctrl+Alt+t keys.

> I have given up on Ubuntu at the moment, way to many things to download from way to many places

You should download from the Ubuntu repositories only.  If you us the apt-get install command or the Software Center, that is where the software comes from.  Downloading things from various sites online will lead to nothing but problems.

> Ubunut does not come with any partitioning software to remove the current format

If you have any Ubuntu installation DVD/CD or flash drive, it has GParted on it which is a partition manager.  Just type:  sudo gparted in a terminal to open it.

> how exactly do I download the Gparted onto my windows system and then burn a boot cd 

GParted can be downloaded as an iso file.  You simply burn it as a bootable image to a CD.  Do you not have any software on this windows system capable of burning an iso file?  I'm sure there must be something available in windows even if the default system doesn't include it.  Once you burn the CD, you re-boot the computer with the CD in the drive, set the CD drive to first boot priority and off you go.  But as I said above, GParted is on the Ubuntu install disk so why waste your time?

---

### Post by edward41 on 2016-04-12
I have managed to get the gparted iso file now, but it will not do much...  It boots to the initial selection screen it says to use tab to select but tab or any other key seems to have no effect upon anything, the screen times out giving me number of seconds to make a selection and then tries to boot but it gives me three error messages.....1.) failed to find cp0device mode.... 2.) module dm-raid45 not found in modules.dep......  and  3.)overlayfs: missing 'wokdir'.....  Then I get a blinking cursor....

I have been reading the online manual for the Gpart, but those directions expect that the software choices can be selected upon boot...

I am trying the Ubuntu install disc that I installed from now...  I cannot gparted on it, though I am guessing maybe I do not need to find it...  

1.) I pressed...  ctrl+alt+t and opened (what I assume is) a terminal

2.) I then typed in ... sudo gparted... and hit enter...

3.)  I am then asked for my password...  pass word entered...

4.)  I the reenter... sudo gparted...  and hit enter

5.)  I then get on the next line....   sudo: gparted:  command not found

6.)  back to cursor...

There has to be, I hope a step by step instruction somewhere that can walk me through how to get rid of this mess..... So far nothing I have read or downloaded seems to be able to do anything....  This seems crazy to me, it used to be incredibly simple...  you downloaded a simple partitioning tool... burned it to a cd as an iso and then booted from it...  it booted to a few simple lines of choices and you selected what you wanted to do and literally within minutes everything was formatting and or partitioning...  Such a simple thing but I cannot find anything that will do that... I miss the simple days of DOS.....

I would download a more updated version of Ubuntu, but I have no working networking.... you guys say to click on the wireless icon... I have no wireless icon...  I have the power button on the right...  the speaker volume to the left of that....  wired network to the left of that, which might work if I had any wire cables to hook up with ....  to the left of that is blue tooth...... to the left of that is my battery symbol....

My wireless does not even show up in Ubuntu...

It would not make any difference anyways, because I am out of bandwidth now until the 19th, I can still get on the net but all I have is dial up speed now, so no downloading anything except after midnight...

I now have kill disk for linuxbut I think I am missing something on Ubuntu, how in the world are you supposed to install anything on Ubuntu?

I went to the file folder... Killdisk    double clicked on...  KillDisk.exe....  The response is another window opening up labeled "Archive Manager"  then I get an error window that states....  An error occurred while loading the archive...

So far this is the result I have gotten from everything that I have tried to run or install on Ubuntu....  Is there a specific way that things have to be run or installed that I am missing?

I found some directions on how use disc utilities on Ubuntu to remove the format....  where in hell is the disc utilizes on the desktop though?   The directions say to go to disc utilities....  they do not give any kind of path to find this.. disc utilities though...  What folder or icon do I look for and then the next and next etc to get to the disc utilities?

I found these directions on a post of someone else having this trouble with removing Ubuntu.....

Boot into the installation Ubuntu USB that you made for installing Ubuntu.
Instead of installing, go Live by choosing the 'Try Ubuntu' option.
Once you are inside the desktop, go to 'Disk Utilities'.
Select your hard drive on the left.
One of the options in the right will be 'Format Drive'.
.
This seems straight forward, but I have looked through everything I can find and there does not appear to any...  Disk utility... anywhere
.
I have tried a number of searches on location of "disk utility" but all I get is how to use the disk utility ... apparently it must be rather obvious as where it is located...  I thought it was tough to find stuff in windows....

I may have figured it out....  There apparently is no disk utility icon or access from the desktop... kind of retarded but OK...  in Ubuntu 12 you apparently have to open a terminal and then type in..... gnome-disk  .....   this will open the disk utility... from there it is simple, just reformat to ntsf...  I also unmounted a smaller drive... loop?...  not exactly sure what that was, but I wanted to be sure everything is undone that I can get undone and get of this....   The computer is apparently unmounting files before shutting down now... with any luck it is almost over...

---

### Post by Geoffrey_Arndt on 2016-04-12
Edward41

The system you have is _easy to install Linux to_ . . . . provided one has done a bit of homework before.    That way, one doesn't tend to make a whole "series" of incorrect assumptions and get totally off track.    First bad step was not to look at the official Ubuntu website and see just what the "current" supported version of Ubuntu is (it's 15.10 - - wily werewolf).    Just plain out - - the 12.10 version will not install correctly and be workable from the get-go.    The repos are not even accessible to get the wireless broadcom driver.    

Perhaps you should start out by viewing about 1/2 dozen of so videos from Youtube that illustrate the install.

---

### Post by edward41 on 2016-04-12
It took three try's but I have Ubuntu removed and my hard disk is now NTSF....   For anyone else having this trouble, the steps I took are..

1.)  Reinstall Ubuntu......  Select the.... "try Ubuntu" rather than the install....

2.)  When you get into the desktop.....  open a "Terminal"  by pressing  ctrl+Alt+t...

3.)  In the terminal window.... type in....  Gnome-Disks  .......

4.)  This should open your  "disk utilities"...

5.)  In the disk utilities window select one of the hard drives on the left.....  right click and select format.....  then select the format type...  FAT32-NTSF etc...repeat for what all drives you are wanting to change.

6.)  There will be a drive at the bottom, labeled something loop...  I would not mess with that, it did not seem to help in fact I think it messed me up by unmounting it..

7.)  Remove media 

8.)  Shutdown computer

9.)  Restart computer and for me anyways press f12 and select cdrom/dvdrom boot.....  before selecting I opened tray and put in my windows install disk...

10.) Windows still saw the partitions on the hard drive but I was able to delete them and then reformat for windows....

I had to do this twice before it actually worked out, but it definitely worked the second time... windows is nearly finished installing now....

---

### Post by mörgæs on 2016-04-13
> **Geoffrey_Arndt said:**
> Edward41

The system you have is _easy to install Linux to_ . . . . provided one has done a bit of homework before.    That way, one doesn't tend to make a whole "series" of incorrect assumptions and get totally off track.    First bad step was not to look at the official Ubuntu website and see just what the "current" supported version of Ubuntu is (it's 15.10 - - wily werewolf).    Just plain out - - the 12.10 version will not install correctly and be workable from the get-go.    The repos are not even accessible to get the wireless broadcom driver.    

Perhaps you should start out by viewing about 1/2 dozen of so videos from Youtube that illustrate the install.

+1

In case other people find this thread don't take it as an indication that Ubuntu does not work in this hardware.

---

