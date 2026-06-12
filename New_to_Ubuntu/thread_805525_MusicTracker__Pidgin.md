---
title: "MusicTracker / Pidgin"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by rage-against-windows on 2008-05-24
Banshee 0.13.2 / Pidgin 2.4.2 / MusicTracker 0.4.1

Absoluteley nothing changes in the status menu.
In the debug window I get this error "core-musictracker: Disabled flag on!"
Ive tried using rhythumbox and pidgin 2.4.1, and get teh same errors. Everything else works fine like its ment to just the musictracker plugin is not working. Anyone have any ideas? Ive searched the forums, and messed around most of the day, and I come up with nothing.

---

### Post by itix on 2008-05-24
Switch to Emesene :P
Much better than pidgin. I have no solution to your current situation, I'm afraid, but if you only use MSN on pidgin, I'd suggest you switch to emesene ;)

---

### Post by Maestro23 on 2008-05-24
Emesene is in the repositories.

---

### Post by itix on 2008-05-24
And in my signature :p

---

### Post by Maestro23 on 2008-05-24
> **itix said:**
> And in my signature :p

Didn't see that. :smile:

---

### Post by jjgomera on 2008-05-24
with banshee i have no idea, but with amarok pidgin work ok 

In pidgin go to Tools/Addons, search musictracker and look at the options

---

### Post by rage-against-windows on 2008-05-24
No I use MSN, Yahoo, ICQ, and sometimes AIM.
I also like Banshee quite a bit, and I don't think its the player thats causing the problems.
Im thinking somethings not set right somewhere. I installed musictracker VIA the repository, and got the updated pidgin from there website. Thanks for the replys though.

---

### Post by alexandremrj on 2008-05-24
Perhpas this will be the stupidest idea:

with me it happens that i have to run pidgin before exaile, or else the plugin doesn't work (of course exaile is a different multimedia player). Can you try loading them in different order to see if it changes anything?

---

### Post by itix on 2008-05-24
Banshee is a wonderful player. It should according to me be the default on any gnome system.
I think the best option is to install musictracker FROM pidgin to make sure that it's the right version. Try to completely uninstall it from the packagemanager and installing it from pidgin from addons.

---

### Post by rage-against-windows on 2008-05-24
I tried both of those, and still no change.
core-musictracker: Disabled flag on! - Still pops up in the debug window. Im stumped.

---

### Post by ikebowen on 2008-11-14
So I'm a little late to the party, but you can go in and change that setting manually in ~/.purple/prefs.xml - look for the musictracker section and change ```
<pref name='bool_disabled' type='bool' value='1'/>
``` to ```
<pref name='bool_disabled' type='bool' value='0'/>
```

Still having issues here with xmpp, but at least it's no longer angry about the disabled flag...

---

### Post by khizar on 2008-11-15
can u plz help n tell me how exactly u do tht
coz i have the xml file open n i tried to edit it but no good. itried to edit its source but still no success...so plzzzz will u elaborate a bit

---

### Post by khizar on 2008-11-15
well sorry for being hasty..i did get to edit the file by opening it in a text editor but as soon as pidgin starts it again goes back to the previous settings...

---

### Post by ikebowen on 2008-11-15
Exit pidgin, then try running the following in a terminal:

```

sed "s/<pref name='bool_disabled' type='bool' value='1'\/>/<pref name='bool_disabled' type='bool' value='0'\/>/" ~/.purple/prefs.xml > ~/.purple/prefs.xml

```

---

### Post by khizar on 2008-11-16
thanks man tht did it...
but thr still is one prob....
my debug window shows tht the status is set to the song tht i m listening and my frndz on my list can also see it...but nothin has happened to status msg on my messenger...its still available or whatevr was set before.. i tried to quit pidgin and tried again but, no good...

---

### Post by ikebowen on 2008-11-16
Yeah, the plugin doesn't change the status box on the player interface. Undocumented feature. ;)

One option is to add yourself as a buddy to keep tabs on how your status actually appears.

---

### Post by khizar on 2008-11-17
ok thanx man

---

### Post by delicio on 2009-04-06
> **ikebowen said:**
> Exit pidgin, then try running the following in a terminal:

```

sed "s/<pref name='bool_disabled' type='bool' value='1'\/>/<pref name='bool_disabled' type='bool' value='0'\/>/" ~/.purple/prefs.xml > ~/.purple/prefs.xml

```

Hey ikebowen, thanks a lot man!! I was trying to fix this for a long time! \o/


Celso

---

