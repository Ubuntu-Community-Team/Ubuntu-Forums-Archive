---
title: "How to access installation Directory"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by jayrjay on 2012-01-29
Hi all I am still struggling with tags and playlists in ubuntu 11.10. I have downloaded a program called "entagged" but when I click on help it says the read me file is located in your installation directory. I have no idea where this is or how I get to it.
Can anybody help?

Thanks:p

---

### Post by cortman on 2012-02-01
> **jayrjay said:**
> Hi all I am still struggling with tags and playlists in ubuntu 11.10. I have downloaded a program called "entagged" but when I click on help it says the read me file is located in your installation directory. I have no idea where this is or how I get to it.
Can anybody help?

Thanks:p

So I assume you downloaded this from Sourceforge.
The binaries (think .exe file in Windows) are usually stored in /usr/bin, although some programs will install stuff all over the place.
This is a Java program, however, so it could be stored anywhere.
Probably your best bet is to search for "entagged" in the root filesystem.

---

### Post by jayrjay on 2012-02-02
Hi Cortman thanks for looking at the thread unfortunately like a lot of times recently what you replied was well over my head no idea what you mean. Do you think it's time I scuttled back to windows with my tail between my legs it does seem to me you need to be computer savvy to run ubuntu successfully.
Thank you for all your help

---

### Post by Lars Noodén on 2012-02-02
Check in the software repositories using Synaptic or the Ubuntu Software Center.  There is a Java Audio File Tagger called [entagged](http://packages.ubuntu.com/search?keywords=entagged&searchon=names&suite=oneiric&section=all) there.  Is that the package you were looking for?  If so, it is worlds easier to use the package manager.

---

### Post by LinuXofArabiA on 2012-02-02
Alright, since I am novice user just like yourself, I will attempt to answer with my limited knowledge, maybe the answer could be as simple as my mind goes. Usually, when you download a program for installation in Ubuntu, you would first download a whole package of files (in a .tar.gz format - similar to .zip or .rar), which contains all the files necessary for you to actually start the installation (called program building in Ubuntu). With all that being said, did you simply check the /Home/Downloads folder? That is where anything you download is stored, and you would take it from there.

P.S. Feel free to yell (type) in anger if the description above is completely irrelevant to what you are asking. Again, I am a novice Ubuntu*er*. However, I would definitely discourage you from switching back to windows, and absolutely recommend that you stick with this problem of yours until you know how to do it. The satisfaction felt after spending two or three days, pouring over tens of online help pages, and finally figuring out is unmatched, and elating.

Good luck!

---

### Post by jayrjay on 2012-02-02
Thanks:)

---

### Post by bogan on 2012-02-02
Hi!** jayrjay**,
Edit: Sorry Lars, got the wrong name
To do what **cortman** suggests:

Open the Home folder;  if you are logged in to Ubuntu, that is usually the third Icon down the list on the left Click on the Icon.
If you are logged in to Gnome Classic it will be the first entry in the Places Menu list, put the cursor on it and release the Mouse button on that.

A Window will open, probably called ' < Home', but may be < home Username.
Click on the '<' and it will change to a square symbol and home Home. 
If it does not, and  give you a screen showing bin, boot, dev, cdrom, etc, etc. then click on it again until it does. 

That is what is called your Root Folder and is shown in the top global menu bar as ' /--File Browser'.
 '/' is the symbol for 'Root'

Top right there will be two arrow symbols, Back and Forward, a Magnifying glass and the word 'Search'. Click on the glass symbol and enter the name of the file you want to find, in the Search Text box that opens.
Then click on the glass at the end of the box. Now you wait, and it may be a long wait.

Eventually it will either show no matches found, or Icons for all the instances it has found.

Right-Clickon the one you want and select 'Properties' in  the drop down menu,
 That will give you the details and where it is to be found ie Its Path. 

eg I searched for "nvidia-config" and it showed: "Location: /home/alan/Downloads/nvidia-270/...

Chao!, **bogan**.  It is not as difficult as it seems, but alcohol is likely to make it look easier than it actually is.

---

### Post by cortman on 2012-02-02
> **jayrjay said:**
> Hi Cortman thanks for looking at the thread unfortunately like a lot of times recently what you replied was well over my head no idea what you mean. Do you think it's time I scuttled back to windows with my tail between my legs it does seem to me you need to be computer savvy to run ubuntu successfully.
Thank you for all your help

Whoa! Sorry for speaking over your head. It can be a little tough to judge a person's skill level sometimes. Proficiency in Ubuntu and Linux in general can be a challenging but very rewarding pursuit (I'm lightyears from guru-hood myself). Keep trying!
Bogan explains kind of what I suggested. Open the file browser and select "file system" in the list of bookmarks on the left. That's the "root" filesystem- the equivalent of C:\ in Windows. Type "entagged" in the search box, and see where that takes you.
Again, apologies for being obtuse! Post back if you have any more questions!

---

### Post by cortman on 2012-02-02
To get a feel for the OS and how it operates, I would recommend the pdf I started with- Introduction to Linux, free download [here]("http://tldp.org/LDP/intro-linux/intro-linux.pdf"). It'll explain the filesystem, a little on how the shell works, etc.

---

### Post by bogan on 2012-02-02
Hi!, **cortman**,

Trusting that I am not trying to teach my Grandmother to suck eggs, what you Posted: > Open the file browser and select "file system" in the list of bookmarks on the left.  worked before 11.10, but now "filesystem" is no longer listed in the File Browser Sidebar. ED: For 'listed', read 'visible'.

EDIT: You were right!! [COLOR=RoyalBlue]Appologies!  [/COLOR]My trust was misplaced.

I had read somewhere that the above was the case, but in fact **it ****IS** listed, but under Devices at the bottom of the list, immediately above Trash, so I never scrolled down enough t see it.

Edit2: Correction: This also applies, [COLOR=Red]as in jayrjay's case[/COLOR], when booted from a LiveCD/USB; but if there is a copy of Ubuntu installed it will show in  the Sidebar as: for instance: "77 GB Filesy...", with a Symbol if it has been Clicked-on, ie 'Mounted'.

Edit3: Ignore:
[HTML]Whether the File Browser is opened by Clicking the Home Folder Launcher Icon,
 or by Dash>Files, and then - if necessary, selecting 'ViewMenu>Sidebar>Show SideBar' -
 as far as I knew then, the only way, to display the Root Folder was the rather long-
 winded  way I described.[/HTML]In my own File Browser SideBar there is an entry:>  " 77GB FileSystem", but that is because I have 10.04 installed, as well as 11.10.

  In 11.04, I made a Launcher to open the Browser in the root folder, but have not been able to in 11.10.
 Edit: I just found how to do it!!

 The only other way I know, would hardly be apt for this Thread, ie:```
 gksu nautilus /   # root
```. Please correct me if you know another way. 

Suitably self-chastised,
Chao!, **bogan**.         :redface:

---

### Post by Paqman on 2012-02-02
> **LinuXofArabiA said:**
> Alright, since I am novice user just like yourself, I will attempt to answer with my limited knowledge, maybe the answer could be as simple as my mind goes. Usually, when you download a program for installation in Ubuntu, you would first download a whole package of files (in a .tar.gz format - similar to .zip or .rar), which contains all the files necessary for you to actually start the installation (called program building in Ubuntu).

Actually, you should avoid doing it this way if at all possible. I haven't compiled anything in years, because it's horrible.

On Linux the first place you should look for software is your distribution's repositories. On Ubuntu you use Ubuntu Software Centre to access them. If a package isn't in the repos the next place to look is for a PPA or a .deb file to download. If something only offers a tarball I tend to run a mile. If they can't even be bothered to supply a .deb and a .rpm then I'd question how well-written or current the software is.

---

### Post by jayrjay on 2012-02-03
> **bogan said:**
> Hi!** Lars**,

To do what **cortman** suggests:

Open the Home folder;  if you are logged in to Ubuntu, that is usually the third Icon down the list on the left Click on the Icon.
If you are logged in to Gnome Classic it will be the first entry in the Places Menu list, put the cursor on it and release the Mouse button on that.

A Window will open, probably called ' < Home', but may be < home Username.
Click on the '<' and it will change to a square symbol and home Home. 
If it does not, and  give you a screen showing bin, boot, dev, cdrom, etc, etc. then click on it again until it does. 

That is what is called your Root Folder and is shown in the top global menu bar as ' /--File Browser'.
 '/' is the symbol for 'Root'

Top right there will be two arrow symbols, Back and Forward, a Magnifying glass and the word 'Search'. Click on the glass symbol and enter the name of the file you want to find, in the Search Text box that opens.
Then click on the glass at the end of the box. Now you wait, and it may be a long wait.

Eventually it will either show no matches found, or Icons for all the instances it has found.

Right-Clickon the one you want and select 'Properties' in  the drop down menu,
 That will give you the details and where it is to be found ie Its Path. 

eg I searched for "nvidia-config" and it showed: "Location: /home/alan/Downloads/nvidia-270/...

Chao!, **bogan**.  It is not as difficult as it seems, but alcohol is likely to make it look easier than it actually is.


Thanks bogan found it, easy when you know :P Once again many thanks

---

### Post by jayrjay on 2012-02-03
> **cortman said:**
> Whoa! Sorry for speaking over your head. It can be a little tough to judge a person's skill level sometimes. Proficiency in Ubuntu and Linux in general can be a challenging but very rewarding pursuit (I'm lightyears from guru-hood myself). Keep trying!
Bogan explains kind of what I suggested. Open the file browser and select "file system" in the list of bookmarks on the left. That's the "root" filesystem- the equivalent of C:\ in Windows. Type "entagged" in the search box, and see where that takes you.
Again, apologies for being obtuse! Post back if you have any more questions!

It is so easy to speak over my head anybody can do it! Please I thank you for all your help and I have got this problem sorted now. Just got to sort my broken updater now:(

---

