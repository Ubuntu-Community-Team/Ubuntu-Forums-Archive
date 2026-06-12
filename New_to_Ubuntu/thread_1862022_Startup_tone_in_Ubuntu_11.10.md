---
title: "Startup tone in Ubuntu 11.10"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by vicke4 on 2011-10-16
Hi all I'm new to Ubuntu i installed 11.10 yesterday.today i can't hear startup tone i don't know how is disabled.can anyone tell me how to enable start up tone?

---

### Post by verymadpip on 2011-10-16
Check in sound preferences  Click the speaker icon, preferences is at the bottom of the drop down (I think).
Sometimes it's muted by default in a fresh install.

---

### Post by vicke4 on 2011-10-16
No it's not the reason.i checked the settings it is okay.i heard startup tone yesterday.now i can't.i installed some softwares and restricted codecs.so i need different remedies.

---

### Post by sadaruwan12 on 2011-10-16
Does any other sound plays like a song and can you hear it.

---

### Post by fractalman on 2011-10-16
Do you mean the sound on the log in screen?

this code lets you disable the sound and then you can select in the start up apps and check the box if you want it on or not

```
gksudo gedit /usr/share/gnome/autostart/libcanberra-login-sound.desktop
```

input that in the terminal and when the text document opens change the line that reads  'NoDisplay=' to false then save and exit

---

### Post by vicke4 on 2011-10-17
I've already searched solutions in Google and i did it correctly(true to false and make a tick in Gnome login sound).though i can't hear login sound.other audio video sounds are good.i installed Gnome shell yesterday.could it cause the problem?

---

### Post by kiki298 on 2011-10-21
I'm pretty sure that's what the problem is. I think the entire sound scheme has been changed when you install gnome-shell, so I'm trying to figure out a way to get it all back. If you figure out a way please post here!

---

### Post by kiki298 on 2011-10-22
Here's how to fix it :)

Download dconf editor if you haven't already. Then click in this order org -> gnome -> desktop -> sound. Once in sound, click on the theme name there (it says freedesktop if I'm not mistaken) and change it to ubuntu (lowercase!) and exit. Log out and log back in to hear the glorious drums :)

---

### Post by vicke4 on 2011-10-23
Thank you kiki298 marvelous stuff.It's working.how you discover this solution?

---

### Post by kiki298 on 2011-10-23
Just a bit of deductive work :) if you don't mind marking the thread as solved so other people will know we found a solution, that would be great :)

---

### Post by vicke4 on 2011-10-23
hmm i added the solved tag.Our thread will become popular.:lolflag:

---

### Post by Tuhinbhatt on 2011-12-15
> **kiki298 said:**
> Here's how to fix it :)

Download dconf editor if you haven't already. Then click in this order org -> gnome -> desktop -> sound. Once in sound, click on the theme name there (it says freedesktop if I'm not mistaken) and change it to ubuntu (lowercase!) and exit. Log out and log back in to hear the glorious drums :)

Cant change the value to ubuntu as soon as i exit the dconf the value defaults to freedesktop(Any help buddies)

---

### Post by Tuhinbhatt on 2011-12-15
Its working now.. Awesome... kiki298 thanks so much buddy you are a lifesaver.. i was searching for hours to solution for this problem.

---

### Post by gilthethrill on 2011-12-23
Worked like a charm.

Thx.

---

### Post by EvanF on 2011-12-24
kiki298, you the man!!!  Thanks for the directions.

EvanF

---

### Post by hillmelvin73@gmail.com on 2012-02-04
I'm having a problem with the login sound at start-up only with Ubnutu 11.10. The thing is it's been working  for months and now I have no login sound. The sound works on everything else but the login. When I login as guest the login sound plays as usually. I have become aware of this in the last week. I have tried a number of solutions but still no login music. This is not a new upgrade or install. The system has been very stable and I have not had any problems in the past with it. I know it is probably something minor. Please help. 

Thanks, Melvin

---

### Post by MoebusNet on 2012-02-05
This is the solution offered in post # 8 of this thread:

> Here's how to fix it

Download dconf editor if you haven't already. Then click in this order org -> gnome -> desktop -> sound. Once in sound, click on the theme name there (it says freedesktop if I'm not mistaken) and change it to ubuntu (lowercase!) and exit. Log out and log back in to hear the glorious drums

If that doesn't work try the code in post #5.

---

### Post by sardhwk on 2012-02-14
> **fractalman said:**
> Do you mean the sound on the log in screen?

this code lets you disable the sound and then you can select in the start up apps and check the box if you want it on or not

```
gksudo gedit /usr/share/gnome/autostart/libcanberra-login-sound.desktop
```

input that in the terminal and when the text document opens change the line that reads  'NoDisplay=' to false then save and exit
My script does not show "No Display=". I use Edubuntu 11.10 on an Acer Aspire One D255. I lost login sound after update and PAVcontrol install. The script is intact (when I click at its location the sound works). Also startup application Gnome login is selected and correctly referred. Gedit does not allow me to edit the script. But it also openend an untitled document?? What must I do to get the login sound back?

---

### Post by sardhwk on 2012-02-14
> **kiki298 said:**
> Here's how to fix it :)

Download dconf editor if you haven't already. Then click in this order org -> gnome -> desktop -> sound. Once in sound, click on the theme name there (it says freedesktop if I'm not mistaken) and change it to ubuntu (lowercase!) and exit. Log out and log back in to hear the glorious drums :)
I am sorry to say but this solution did not solve my problem. The settings you suggested were correct!

---

### Post by sardhwk on 2012-02-16
Still _not_ solved! Can somebody plse explain how i can edit libcanberra? I got this message when trying>gksudo gedit /usr/share/gnome/autostart/libcanberra-login-sound.desktop

(gedit:2314): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.G8BF9V': No such file or directory

(gedit:2314): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

But the file is there and when I click it the drums play!

---

### Post by wilsonB on 2012-03-04
I think specificly the problem people are having is the system sounds don't play. I can play sounds when going into ;
System Settings\sound\
sound effect tab
This plays sounds and I can listen to music, youtube.. etc.
There are no options here to select sound themes or anything like that.

but I hear no Desktop system sound effects. 
log on/off , or minimizing windows, etc..

I successfully installed a new sound theme and gone back to default ubuntu theme. Still no sound played for system sounds.

Ubuntu 11.10 build
I might have reinstalled Debian shell.. I have done so much since install to get things working nicely. 

Lost system theme sounds. Don't know how to get it back. 
Anyone?

Thanks so much

---

### Post by critin on 2012-03-04
wilsonB, hillmelvin, and sardhwk,

Hey Guys,  You're posting on an "old" SOLVED thread and not getting any answers.  I suggest you each start you own separate threads for quicker help.  If the solution here didn't work for you, you have a different issue.

---

