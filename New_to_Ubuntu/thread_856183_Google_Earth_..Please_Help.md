---
title: "Google Earth ..Please Help"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by harecanada on 2008-07-11
I have been trying to resolve this problem of GE not working on my system for over a month and a half!!! GE worked fine on Kubuntu Feisty. When I upgraded to Kubuntu Hardy it refused to work. I've tried everything. Over 60 posts on at least three Linux Forums. Finally I decided my system was corrupt. So I added a second hard drive and loaded a fresh install of Ubuntu Hardy 8.04.1 to give it a try. Much to my frustration Google Earth still won't work. I loaded it from Synaptic.. didn't work. I loaded it from Googles website as a bin file ...didn't work. 
What I would like is someone to help me completly uninstall GE and start step by step and get it working.  
Graphics Card:
nVidia Corporation NV34[GeForce FX 5200] 
Running Ubuntu Hardy Heron 8.04.1
Hardware Drivers Manager says my nVidia driver is the latest and is enabled and in use. However, on restarting my system I don't get an NVIDIA splash screen.
At present there is a Google Earth icon on my desktop that doesn't work and also a GoogleEarthLinux.bin icon as well.
Would anyone like to help?
harecanada

---

### Post by philinux on 2008-07-11
Run it from the terminal

googleearth %f

and post the errors if any.

---

### Post by harecanada on 2008-07-11
All I get is this:

darrell@darrellsubuntu:~$ googleearth %f
bash: googleearth: command not found

harecanada

---

### Post by hyper_ch on 2008-07-11
install google earth from the medibuntu repos and it just runs

---

### Post by philinux on 2008-07-11
[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Download the 4.3 beta. It works fine.


Install it via this method.

[http://monkeyblog.org/ubuntu/installing/#installer](http://monkeyblog.org/ubuntu/installing/#installer)

Or use hypers solution.

click the medibuntu link below in my signature.

---

### Post by harecanada on 2008-07-11
Hey hyper_ch,
How do I do that?
Do I uninstall any thing to do with GE first?

---

### Post by hyper_ch on 2008-07-11
add the medibuntu repos... google earth is in those. then you can use synaptic or apt-get to install it... no need to uninstall ge first...

---

### Post by harecanada on 2008-07-11
OK Guys,
So I tried both methods. No Luck.
So if you are telling me that you both are running GE and you used two different methods of installing it, and it is running smooth and no glitches them I'm spinning out here!!
I put in a second hard drive and did a fresh install of Ubuntu Hardy and still no GE!! What the hell can i be doing wrong? 
Right now when I go to Applications>Internet there are two GE icons. I clicked the first and the GE spash screen opens and says it is initializing then it disappears then I try the other icon and the same thing happens. 
I feel like I should throw my system in the fireplace and go get a stone tablet and chisel:lolflag:
Any suggestions?
This is why I like Linux... Lots of challenges and hands on..
What next?

---

### Post by philinux on 2008-07-11
Just try 

gksudo googleearth

---

### Post by deNoobius on 2008-07-11
Here's what I would do (I'm pretty new at this but I do have Google Earth and other installed software running).  Go to System/Administration/Synaptic Package Manager and search for Google Earth.  If the upper window shows that it is installed (the checkbox is filled in), click the checkbox and select "Mark for Complete Removal."  "Apply" so that it is removed, and make sure the data package is removed as well.  

Then reinstall, including the data package (also found in Synaptic if you search on "Google Earth").

---

### Post by hyper_ch on 2008-07-11
and if that still fails then start it from the cli... this will at least produce some (error) output.

---

### Post by harecanada on 2008-07-11
Splash screen comes up. Says initializing. Then disappears.

Crazy eh!!!

---

### Post by philinux on 2008-07-11
post the output of this.

glxinfo | grep rendering

use copy and paste

---

### Post by harecanada on 2008-07-11
darrell@darrellsubuntu:~$ glxinfo | grep rendering
direct rendering: Yes
darrell@darrellsubuntu:~$

---

### Post by hyper_ch on 2008-07-11
now run googelearth from the cli

---

### Post by philinux on 2008-07-11
Well that means graphics card good to go.

Open synaptic package manager.

Click on any app then type googleearth

See what it says you got installed.

---

### Post by harecanada on 2008-07-11
googleearth
googleearth-4.3
googleearth-4.3-data

---

### Post by philinux on 2008-07-11
The one marked just googleearth

right click and select mark for complete removal.

It might be worth a reboot too after. Just to clear the decks.

You dont normally need to do this in linux.

---

### Post by harecanada on 2008-07-11
Ok.
Same thing with the spah screen comes on. Says initializing. Then disappears.

---

### Post by harecanada on 2008-07-11
I meant "splash screen"

---

### Post by philinux on 2008-07-11
Go to your home folder and do ctrl h to show hidden files.

Find the .googleearth folder and delete it then try running it again.

If that does not work use this

[http://ubuntuforums.org/showthread.php?t=520952](http://ubuntuforums.org/showthread.php?t=520952)

Post 8. Download the file to your desktop. Double click it to extract the files and copy them to your .googleearth folder.

---

### Post by harecanada on 2008-07-11
Ok.
I found the GE folder and deleted it.
Clicked on the Google Earth icon and my computer restarted!!!
I went and downloaded those files but I can't copy them to my google earth folder because I deleted it, like you said.

---

### Post by philinux on 2008-07-11
> **harecanada said:**
> Ok.
I found the GE folder and deleted it.
Clicked on the Google Earth icon and my computer restarted!!!
I went and downloaded those files but I can't copy them to my google earth folder because I deleted it, like you said.

Ok so it will be in the recycle bin. You can copy it back hopefully.

On second thoughts no. Use synaptic and mark it for reinstall

---

### Post by harecanada on 2008-07-11
Double clicked on folder.
Highlighted the first file and copied it.
Opened the Googleearth folder.
Won't let me paste to it^!&@^&!^@#&
I can't be this cursed. There must be an Ubuntu chant or something to resolve this.

---

### Post by hyper_ch on 2008-07-11
still no cli start of GE.... well, I tried but I unsubscribe now from this thread.

---

### Post by philinux on 2008-07-11
He did you missed the output.

> Splash screen comes up. Says initializing. Then disappears.

Crazy eh!!!

---

### Post by philinux on 2008-07-11
If you extracted the files to your desktop there should be 2 files.

One called libGL.so.1 and the other file libGL.so.1.2

---

### Post by harecanada on 2008-07-11
Ok.
This is where I put them.
I clicked the GE icon in Applications>Internet.
The splash screen came up and said initializing.
Then my computer restarted!!!
So weird!!
I'll understand if you want to bail out of this thread. I'm starting to think I need an exorsist!!
 I appreciate all the help your giving me.
I should purge my system of Google Earth and start again.
What do you think?

---

### Post by harecanada on 2008-07-11
Forgot to attach the screenshot.

---

### Post by philinux on 2008-07-11
I'd delete that instance running lock file.

open a terminal and type

killall googleearth

Then try running it again.

It's nearly beer o'clock time.

It sounds like it interfering with xorg.

Also have a look in the crashlogs see if anything useful there.

---

### Post by harecanada on 2008-07-11
darrell@darrellsubuntu:~$ killall googleearth
googleearth: no process killed
darrell@darrellsubuntu:~$ 

Tried it again. Restarted my puter.
Nothing in crashlogs.
Your right , Beer time here too (I wish) Got an infection in my foot and not alloud to have beer!! Have one for me..or two

---

### Post by Foster Grant on 2008-07-11
As long as we're talking about Google Earth problems, I have one.

I have Google Earth on my Applications->Internet submenu but when I boot it up, there's no Earth, just empty space. And according to Synaptic, Google Earth is not installed. If I try to install it from Synaptic, I end up with (apparently) two versions of Google Earth; both versions will load, but neither will run properly (neither one has Google Earth data).

Ideally, I'd like to get rid of the version of GE that I have right now and cleanly reinstall the whole package (including data). But first, I have to get rid of that GE version that Synaptic says I don't have. Any ideas?

I'm running Hardy, if it matters.

---

### Post by harecanada on 2008-07-11
Hey Foster Grant,

I'm not really one to give advice on Google Earth but have you looked at this link:
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)
It gives details of uninstalling as well as installing on Ubuntu

---

### Post by Foster Grant on 2008-07-11
Yep, that worked. :)

There's a package in the repositories picked up from Debian that allows a user to roll a .DEB of Google Earth. May have to look into that.

---

### Post by harecanada on 2008-07-12
Hey philinux,

Can you imagine. I helped someone with their Google Earth and still don't have it working on my own system](*,)
Talk to you tomorrow?

---

