---
title: "HOW TO: Make Amarok my *default* music player????"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by swimm3r137@gmail.com on 2008-04-27
I uninstalled rythombox, cuz it sucks and replaced it with Amarok. (which rocks btw).  BUT, when I insert a cd for instance, Sound Juicer opens it and attempts to play it.  I don't want this.  How do I make Amarok my default music player(where I can just insert a cd, and amarok will open), so other random programs will stop opening it.

appreciate any and all help

---

### Post by macogw on 2008-04-27
In a file browser, go to Edit -> Preferences.  Go to the Media tab.  Choose amarok on the Audio CD line.

By the way, check out Exaile.  It's very similar to Amarok, but it matches your GNOME environment instead of looking all out of place like Amarok does.

---

### Post by macogw on 2008-04-27
In a file browser, go to Edit -> Preferences.  Go to the Media tab.  Choose amarok on the Audio CD line.

By the way, check out Exaile.  It's very similar to Amarok, but it matches your GNOME environment instead of looking all out of place like Amarok does.

---

### Post by lamalex on 2008-04-27
Try System > Preferences > Preferred Applications > Multimedia Tab

---

### Post by swimm3r137@gmail.com on 2008-04-27
> **macogw said:**
> In a file browser, go to Edit -> Preferences.  Go to the Media tab.  Choose amarok on the Audio CD line.

By the way, check out Exaile.  It's very similar to Amarok, but it matches your GNOME environment instead of looking all out of place like Amarok does.

thankyou.  Exaile, I sort of checked it out.  It looks and sounds like the same thing as amarok.  Does it perform better than amarok.  Persuade me to switch :)

---

### Post by mc4man on 2008-04-27
> How do I make Amarok my default music player(where I can just insert a cd, and amarok will open)

to get amarok to auto open, load playlist and start playing cd in gutsy, feisty, use this line in removable drives and media....
```
amarok -cdplay %d
``` not sure if cdplay needs to be installed separately -  if so part of cdtool package
edit: it will take 15-20 secs for playlist to load

---

### Post by aigelonic on 2008-04-27
I checked out Exaile, but it seems just not as well developed as Amarok yet. I can't for example seem to find how you connect other devices like a mp3-player (I've checked the plugins, and I only found a plugin for iPod). But otherwise this seems like a good player. I'll be checking in regulary to see how the development goes... :)

---

### Post by steve_4802 on 2008-04-27
On the same topic - except I want to make amorak default for when I plug in my ipod.

I can stop Rhythmbox from starting by going to a file browser, go to Edit -> Preferences. Go to the Media tab. Then for 'music player' set it to 'Do nothing'. However, if I want to start it in Amarok, how do I get amarok to appear in that list?

Cheers

---

### Post by steve_4802 on 2008-04-27
On the same topic - except I want to make amorak default for when I plug in my ipod.

I can stop Rhythmbox from starting by going to a file browser, go to Edit -> Preferences. Go to the Media tab. Then for 'music player' set it to 'Do nothing'. However, if I want to start it in Amarok, how do I get amarok to appear in that list?

Cheers

---

### Post by nofrendo on 2008-04-27
Yeah just no let you know, Amarok does not only look out of place in the Gnome environment, but it depends on a lot of KDE packages, check out the install size and all the extra packages that it also installs.

---

### Post by spectrevk on 2008-04-27
I have a similar problem, but with video players. I want to use VLC instead of the default that comes with Ubuntu, but there's no way to set it as default. Preferred Applications doesn't have VLC in the drop-down list, andi in the past when I've tried to use the Custom option, it didn't work out so well (though it's possible that I was just doing it wrong).

---

### Post by mc4man on 2008-04-27
> I want to use VLC instead 
I haven't found a 'global' that worked with vlc but for 1 drive follow procedure in my prior post but insert ```
vlc cdda:///dev/scd0 
``` where scd0 is drive on your setup
> 
Amarok does not only look out of place in the Gnome environment for the most part it runs minimized. as far as installing kde stuff it's not normally an issue

---

### Post by spectrevk on 2008-04-27
I was thinking more about local files. I'd like to be able to double-click on a media file and have it open up with VLC.

---

### Post by mc4man on 2008-04-27
> I was thinking more about local files.
try r.clicking on a type of file>properties>open with, if vlc is in list click the little circle
if not choose add,  ...ect.

---

### Post by terabyte1 on 2008-04-27
Yup! Yup! Exaile is a bute with Gnome Good on yer girl - lets boogie...:guitar:

terabye1:lolflag:

---

### Post by spectrevk on 2008-04-27
I can get them to open by right clicking, but it never sticks, so I always have to right click and choose it from the menu.

---

### Post by mc4man on 2008-04-27
> I can get them to open by right clicking
What you want to do is right _click_ > _properties_..........ect.

edit :you only need to do this once per _file type_ you want to set

---

### Post by marko_4454 on 2008-04-27
> **steve_4802 said:**
> On the same topic - except I want to make amorak default for when I plug in my ipod.

I can stop Rhythmbox from starting by going to a file browser, go to Edit -> Preferences. Go to the Media tab. Then for 'music player' set it to 'Do nothing'. However, if I want to start it in Amarok, how do I get amarok to appear in that list?

Cheers

I want exactly the same thing. And I have exactly the same problem, how can you add a custom application to that option list or how can I get my ipod to get detected by amarok automatically? 
I dont really know why they changed the interface from 7.10, since it worked well and gave you more options. Can anyone help us out? 
Thanks

---

### Post by spectrevk on 2008-04-28
> **mc4man said:**
> What you want to do is right _click_ > _properties_..........ect.

edit :you only need to do this once per _file type_ you want to set

Thanks. I can't believe I didn't think of that before.

---

