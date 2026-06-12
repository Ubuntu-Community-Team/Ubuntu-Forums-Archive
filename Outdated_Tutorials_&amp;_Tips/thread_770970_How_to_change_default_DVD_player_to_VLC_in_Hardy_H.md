---
title: "How to change default DVD player to VLC in Hardy Heron"
date: 2008-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Afkpuz on 2008-04-27
*****EDIT***** Please note that this method is for hardy heron.  Once vlc is installed in intrepid IBEX, vlc can be selected via the popup menu that comes up whenever a dvd is inserted.

I know that many people have been trying to find the place to change your default dvd player.  I personally have been looking for a while to change vlc to my default player.  Well, I found it and want to share with the rest of you.


After you've installed VLC, paste this into the command line
```
sudo gedit /etc/gnome/defaults.list
```


Press ctrl-f and search for "x-content/video"

Replace the word "totem" with "vlc" in all 5 instances

Save and quit

Open any nautilus file browser window.  For ease of use, goto Places>Home Folder

Now, click "Edit" on the menu bar at the top.

Select Preferences

Then select Media

Under "DVD Video" select VLC


Thats it.  If you want to change the custom command that is used to open VLC, thats found by right clicking on "Application" and selecting "Edit Menus"

Then, select sound and video on the left and right click on VLC.  Here is where you can change the command to your hearts content.  



Special thanks goes to mc4man for pointing me to the answer and to reassuringlyoffensive for his original post

---

### Post by fede on 2008-04-29
Thanks!

---

### Post by fwilliams on 2008-04-30
Thanks.

---

### Post by MelancholyStoo on 2008-04-30
awesome, that saves me a lot of faffing around closing totem every time :D

---

### Post by SonicSteve on 2008-05-04
I'll give it a try also,

I was wondering though if anyone knew of a way to do it in gconf-editor. If you don't know what it is press alt-F2 and type gconf-editor. Careful what you do in there though, its the Gnome defaults database editor.

---

### Post by ubuntu-freak on 2008-05-05
Just incase anyone has missed it, this is from my sticky thread in the Multimedia & Video section (see sig). Give the alternative commands a try if you want automatic fullscreen playback upon DVD insert.
 
Nathan

---

### Post by Ghuloomo on 2008-05-10
Thank you very much

---

### Post by westyonfire on 2008-05-15
Hey,
thanks, I've been looking everywhere for this. I have run into a little problem though. When I insert a dvd, Vlc pops up but nothing happens and then the vlc window goes dark and freezes. Anybody know how to fix this?

---

### Post by ubuntu-freak on 2008-05-15
> **westyonfire said:**
> Hey,
thanks, I've been looking everywhere for this. I have run into a little problem though. When I insert a dvd, Vlc pops up but nothing happens and then the vlc window goes dark and freezes. Anybody know how to fix this?

 
Have you followed Part 1 and 4 of my [how-to](http://ubuntuforums.org/showthread.php?t=766683)? 
 
Nathan

---

### Post by westyonfire on 2008-05-15
Hi,
I added the resources from the beginning of step one but my flash is working fine so I skipped the rest of step 1. I also skipped steps 2 and 3 as I dont really do any converting. But I followed step 4 word for word. I also got this warning when doing step 4: "dpkg - warning: downgrading libdvdcss2 from 1.2.9-2medibuntu4 to 1.2.5-1."...how do i get the latest version back again?
But VLC player still crashes when I insert a dvd even though it plays dvds fine when i open a dvd up through vlc player.

---

### Post by ubuntu-freak on 2008-05-15
> **westyonfire said:**
> Hi,
I added the resources from the beginning of step one but my flash is working fine so I skipped the rest of step 1. I also skipped steps 2 and 3 as I dont really do any converting. But I followed step 4 word for word. I also got this warning when doing step 4: "dpkg - warning: downgrading libdvdcss2 from 1.2.9-2medibuntu4 to 1.2.5-1."...how do i get the latest version back again?
But VLC player still crashes when I insert a dvd even though it plays dvds fine when i open a dvd up through vlc player.

 
I'd rather you reply in the thread you're talking about, but anyway. The libdvdcss2 file will be re-upgraded by Update Manager automatically, it probably already has been. Did you try changing the VLC launch command? As mentioned in the how-to. 
 
Nathan

---

### Post by westyonfire on 2008-05-15
> **reassuringlyoffensive said:**
> Did you try changing the VLC launch command?

That worked! I didn't do it before because i didn't mind the half volume thing or it not opening into full screen. I changed it from 'vlc %u' to 'vlc --volume 512 %m'. I guess the '%u' was somehow stuffing it up. 

Thanks Heaps!

p.s. I would've replied in your other thread but seeing as you just solved it i thought there wasn't much point.

,thanks again

---

### Post by dondad on 2008-05-15
> **Afkpuz said:**
> I know that many people have been trying to find the place to change your default dvd player.  I personally have been looking for a while to change vlc to my default player.  Well, I found it and want to share with the rest of you.


After you've installed VLC, paste this into the command line
```
sudo gedit /etc/gnome/defaults.list
```


Press ctrl-f and search for "x-content/video"

Replace the word "totem" with "vlc" in all 5 instances

Save and quit

Open any nautilus file browser window.  For ease of use, goto Places>Home Folder

Now, click "Edit" on the menu bar at the top.

Select Preferences

Then select Media

Under "DVD Video" select VLC


Thats it.  If you want to change the custom command that is used to open VLC, thats found by right clicking on "Application" and selecting "Edit Menus"

Then, select sound and video on the left and right click on VLC.  Here is where you can change the command to your hearts content.  



Special thanks goes to mc4man for pointing me to the answer and to reassuringlyoffensive for his original post

Thanks for that. One thing, you should use gksudo with a graphical app. Using sudo can sometimes cause lots of problems. DAMHIKT

---

### Post by Gourgi on 2008-05-16
> **westyonfire said:**
> That worked! I didn't do it before because i didn't mind the half volume thing or it not opening into full screen. I changed it from 'vlc %u' to 'vlc --volume 512 %m'. I guess the '%u' was somehow stuffing it up. 

Thanks Heaps!

p.s. I would've replied in your other thread but seeing as you just solved it i thought there wasn't much point.

,thanks again
my vlc freezed also until i edited the gnome-menu launcher
changed it from 'vlc %u' to 'vlc --volume 512 %m'.
thanks for your post :popcorn:

---

### Post by peakpc on 2008-05-16
Thanks for the tip, I really like vlc... I wish it were the default player used by ubuntu as it is on my laptop. In fact I used Replace to change all "totem" to "vlc" and I haven't come across any behavior that I don't like.  I also used the 'vlc --volume 512 %m' a nice tweak for full volume.

---

### Post by robolange on 2008-05-20
Suppose, for the sake of argument, that I do not have root/sudo on a machine. (vlc is installed.)  How do I set vlc as the default player for my account only?

Of course, I do have root, but I adamantly oppose the editing of global system files to change user preferences.  That is the Windows 95 mentality, which frankly has no place in a GNU/Linux environment.  (This is not a dig against the commenter who found this workaround, but against the circumstances that force us to use a root-level kludge to change a simple user preference.)

--Robert Lange

<snip>
> **Afkpuz said:**
> I know that many people have been trying to find the place to change your default dvd player.  I personally have been looking for a while to change vlc to my default player.  Well, I found it and want to share with the rest of you.


After you've installed VLC, paste this into the command line
```
sudo gedit /etc/gnome/defaults.list
```


Press ctrl-f and search for "x-content/video"

Replace the word "totem" with "vlc" in all 5 instances

Save and quit

</snip>

---

### Post by Afkpuz on 2008-05-20
From what I understand, there was some bug within the code of hardy which had to change the way the default dvd player is selected.  In gutsy, it was a simple field that you could paste in any command you wanted.  Granted, you had to figure out the command syntax for your favorite player, but I agree that this method is ridiculous.  We should all bug the devs to try to fix this.  so head to brainstorm and let em know!  I went ahead and made an entry at brainstorm.  Please vote to help this


[[IMG]http://brainstorm.ubuntu.com/idea/8846/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/8846/)

---

### Post by schaumkeks on 2008-05-25
This has been intentionally changed as discussed here:
[http://bugzilla.gnome.org/show_bug.cgi?id=532474](http://bugzilla.gnome.org/show_bug.cgi?id=532474)

I have written some steps to work around this problem system wide or per user without changing existing files:
[http://ubuntuforums.org/showpost.php?p=4941152&postcount=23](http://ubuntuforums.org/showpost.php?p=4941152&postcount=23)

Bye, schaumkeks

---

### Post by Afkpuz on 2008-05-25
Ok, I kind of understand why they took out the feature, but they still need to allow for some way to change the default dvd player without all the run around that seems necessary for hardy.  I wouldn't mind if after installing vlc, that became a choice automatically in the nautilus>edit>preferences>media.  But right now, we have no choice but to alter config files which may not be hard for me, but it's still annoying.  Some of those posts said that there were problems caused by having a command line box that could be customized.  What kind of problems were they referring to?

---

### Post by wandalalakers on 2008-12-06
Thx!  XOXO.
You made me a very happy girl.
I'm making a ubuntu image using remastersys and now my image is perfect.
I an now autoplay DVDs using VLC!

---

