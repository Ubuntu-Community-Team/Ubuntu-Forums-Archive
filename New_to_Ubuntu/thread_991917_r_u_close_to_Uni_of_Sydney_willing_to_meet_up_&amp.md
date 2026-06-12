---
title: "r u close to Uni of Sydney? willing to meet up &amp; help install a software??"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by oziekhan on 2008-11-24
Hi

I am a student at Uni of Sydney Australia. I have just switched over to ubuntu. I need to install a small educational software on my system....it is called cmap (concept map)..it is a free software for creating a pictorial representation of ideas and concepts (available at cmap.ihmc.us)... it is an .exe file and the download site says that it is for linux.. but I cant install it.

Is there anyone out there in Sydney who can help me with that.... if you want I can come over to your place.

please PM me.

Thanks

Amer Khan
PhD Student
Uni of Sydney

---

### Post by eldragon on 2008-11-24
did you follow this link? [http://cmap.ihmc.us/download/installs/CmapTools/Linux/LinuxCmapTools_v4.18_06-09-08.zip](http://cmap.ihmc.us/download/installs/CmapTools/Linux/LinuxCmapTools_v4.18_06-09-08.zip)

its clearly a zip file, im downloading it right now to see whats inside.. and maybe give some instructions to follow..

---

### Post by oziekhan on 2008-11-24
> **eldragon said:**
> did you follow this link? [http://cmap.ihmc.us/download/installs/CmapTools/Linux/LinuxCmapTools_v4.18_06-09-08.zip](http://cmap.ihmc.us/download/installs/CmapTools/Linux/LinuxCmapTools_v4.18_06-09-08.zip)

its clearly a zip file, im downloading it right now to see whats inside.. and maybe give some instructions to follow..

Thanks eldragon for your help. yes it is a zip file and it is just sitting there on my desktop refusing to budge!!! I tried to open it using the synoptic manager etc. but it refuses to acknowledge the file!!

Cheers

---

### Post by Sef on 2008-11-24
Check out [How to Install Anything in Ubuntu]("http://amitech.50webs.com/installing/index.php.html").

---

### Post by eldragon on 2008-11-24
unpack the zip

you will see a .bin file.

right click and select properties.

check the permissions tab, and check the allow executing this file checkbox.

its probably an installer.

good luck

---

### Post by arochester on 2008-11-24
Being a glutton for punishment I downloaded this, extracted it, saw a .bin file, changed permissions ...and it doesn't work for me. According to [http://cmap.ihmc.us/download/index.php?myPlat=Linux](http://cmap.ihmc.us/download/index.php?myPlat=Linux) the system requirements list "RedHat 8.0 or higher version" Looks as though it might not work on Ubuntu?

---

### Post by hyper_ch on 2008-11-24
you could also try to find out where your local linux user group is and contact them :)

---

### Post by mc4man on 2008-11-24
Whether it works right or not i don't know, but to install extract the zip to your home dir.and make executable as described.

Then in terminal ./[COLOR="Red"]name[/COLOR].bin (change red to match extracted name.

Or to make life easier rename the extracted .bin to something easier like test1.bin. then you'd go in terminal ./test1.bin


Edit;  Read below post first. (eldragon

I checked it out, installs fine, here's a more exact from the top with no renaming of the .bin (though it makes life easy

Right click on your zip file -> 'open with archive manager'

Click  the extract button and in left side box (places) highlight your home folder (user name and click extract.

when it's done open a terminal (Applications -> accessories -> terminal

copy and paste this into the terminal and press enter on keyboard (will make the bin executable
Edit anything in red if different from the exact name of your .bin

```
chmod +x [COLOR="Red"]LinuxCmapTools_v4.18_06-09-08[/COLOR].bin
```

You should be returned to a prompt with no error message, if so then copy and paste this (again adjust red if needed

```
./[COLOR="Red"]LinuxCmapTools_v4.18_06-09-08[/COLOR].bin
```

the installer should start

You should choose 'create a link', browse or set to desktop, see screen

good luck (I opened it after install - not a clue as to what it does

---

### Post by eldragon on 2008-11-24
exactly, after replying to this thread, i tried double clicking the .bin and it would not run.

opening the terminal and running with /path/to/filename.bin fixes it.

id advise you to run this program as root, so that it gets installed in a system directory and all links end up in the proper place.

---

### Post by oziekhan on 2008-11-25
I DID IT!!!!WOW!! I did some actual coding.... after many many years (since the days of 'GW Basic')....

Honestly, I was about to give up on this linux thing and fall back on Windows.... But given the excellent guidance given by dedicated linux users like you guys..i will stick around...

Guys... THANKS A LOT!!! 

Best Regards

Amer

---

### Post by oziekhan on 2008-11-25
hey guys, now I have another problem......... installation all done but when I open the files open all blank screens!!! please help again!

---

### Post by oziekhan on 2008-11-25
I have got Ubuntu 8.04  Hardy Heron

---

### Post by oziekhan on 2008-11-25
may be I need to run it in root... how can i do that?

---

### Post by mc4man on 2008-11-25
Hopefully somebody can help you out ( that's what i meant by 'didn't have a clue what to do..

i uninstalled it and reinstalled as root - no change (grey windows
plus it was much harder to find (vs. /home

Maybe eldragon can help you there

Did find this (possible solution at bottom

[https://answers.launchpad.net/ubuntu/+question/18055](https://answers.launchpad.net/ubuntu/+question/18055)

Faq (probably not that helpful
[http://cmap.ihmc.us/Support/FAQs.php](http://cmap.ihmc.us/Support/FAQs.php)

---

### Post by eldragon on 2008-11-25
i dont know where your install resides, you will have to find that for yourself.

the solution proposed is the following:

rename the jre folder located in the install location IHMC_CmapTools/ to something else eg. mv jre jre.bak (you need to be on the IHMC_CmapTools/ directory for this to work)


which messes up with the local jre which should alredy be installed in your system.


a second less destructive solution proposed is to disable compiz temorarily when running the software.

just hit: alt-f2 and run "metacity --replace" without the quotes. this will kill all eyecandy..

to get eyecandy running again, (once you finnished using your software) hit: alt-f2 and type "compiz --replace"

---

### Post by mc4man on 2008-11-25
The compiz solution works quite well whether installed as root or to home dir.
The desktop link isn't created when installing as root, though easy to create one if you go that route.

---

### Post by oziekhan on 2008-11-26
eldragon, 

your solution worked!! Thanks again. 

regards

---

### Post by oziekhan on 2008-11-26
by the way... what is 'eye candy'..... what happens when I run 'metacity replace' and back? besides getting me my software interface......??..and what is 'eyecandy'... sorry for the stupid questions as i am a complete novice...


cheers

---

### Post by mc4man on 2008-11-26
'eye candy' refers to 'desktop effects' or 'advanced desktop effects'
By default compiz is installed with some minimal effects.

To enable the advanced settings, effects you'd need to install compizconfig settings manager.

```
sudo apt-get install compizconfig-settings-manager
```

Then in System -> preferences you'll see in hardy - 'Advanced Desktop Effects Settings', in intrepid - ' CompizConfig Settings Manager'

The ability to use or to have effects work properly is dependent on your video adapter and video driver installed.

I find for my desktop the 'desktop cube' and 'rotate cube' very handy. You can have up to 16 cube sides and rotate them with the mouse scroll wheel. (having 4 sides is typical

There's a separate forum section just for 'effects'
[http://ubuntuforums.org/forumdisplay.php?f=330](http://ubuntuforums.org/forumdisplay.php?f=330)

screen shows some of the possible effects

---

### Post by eldragon on 2008-11-26
to be more specific, there are different ways to draw your screen.

when refering to eye candy, we usually mean the desktop is 3d redered and thus you get those nice effects when you minimize, maximize, and move windows. you can have more advanced effects that usuually clutter more than help.

the program in charge of doing this is called a windows manager. 

metacity and compiz are both window managers, compiz being the one running all the fancy 3d stuff, while metacity is the default gnome windows manager.

when running metacity --replace, you are telling it to replace whatever windows manager there is running with metacity. (thats why there is a slight windows dissappearance).

some programs dont interact well with compiz, yours is one of them.

---

