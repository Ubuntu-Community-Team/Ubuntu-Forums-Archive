---
title: "[SOLVED] Firefox 3 installed, but v 2 loads"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by GkProf on 2008-10-07
The Syn Pkg Mgr lists Firefox 3.0.3 installed, but the menu bar icon and apps/Internet/Firefox items still load v 2.0.17.

How do I load v 3?

(Using 8.04.)

---

### Post by Tatty on 2008-10-07
Try uninstalling firefox 2 via synaptic, then re-install firefox 3.

---

### Post by GkProf on 2008-10-07
Synaptic does *not* list v 2 as installed, so can't select uninstall there?!

---

### Post by Tatty on 2008-10-07
how did you install firefox 2?

---

### Post by GkProf on 2008-10-07
I don't remember; I figured out something when I first started experimenting with Ubuntu last year. I've been using 

gksudo firefox &

to keep v 2 updated.

---

### Post by Tatty on 2008-10-07
> **GkProf said:**
> gksudo firefox &

afaik, that command would simply run firefox with superuser rights, it would not update firefox.

Im not sure how to remove Firefox 2 without knowing how it was installed, but perhaps simply re-installing Firefox 3 will overwrite the menu entry for you?

---

### Post by GkProf on 2008-10-07
Sorry; I load Firefox with the gksudo, then I can use Firefox auto update feature.

I've tried installing v 3 several times with Synaptic since it showed up there, but no success.

I'm wondering if I originally installed the Mozilla version outside of Synaptic?

---

### Post by Tatty on 2008-10-07
> **GkProf said:**
> I'm wondering if I originally installed the Mozilla version outside of Synaptic?

That sounds likely.  You would need to know how you installed firefox before you can uninstall it, Im afraid I dont know how to go about finding this out, but hopefully someone else can come along with an answer.

---

### Post by GkProf on 2008-10-07
Bummer. Thanks for getting me started. Anyone know how to resolve this one? I'll check back in the morning... Thanks.

---

### Post by 4nick8or on 2008-10-07
I have the same problem. I found the FF3 launcher on the Debian menu under Applications > Network > Web Browsing. Right click and add the launcher to the Desktop or a panel. Or run pdmenu in a terminal and follow the same paths.


Regards,

---

### Post by GkProf on 2008-10-08
Still unresolved. I'm not proficient at Ubuntu, so these things may be obvious to some, but not me. I have been poking around a bit and as best I can figure out, here's where I've found the pieces. 

Firefox 2 is installed here: /opt/firefox/

If I go to: /usr/bin/
there are shortcuts (or whatever they're called on Ubuntu!) to both "Firefox" (which links to the /opt location and loads v 2) and also one to:
../lib/firefox-3.0.3/firefox.sh

Double clicking the second of these does, indeed, load Firefox 3.

Is that enough more info for someone to explain to a novice how to get rid of v 2 and make v 3 the default?


(If this were Mac, or even XP [!], I'd know how to do this, but I've been gradually trying to learn Ubuntu since Bill Gates thought I should upgrade my XP ;) Things are very different here, however.)

Thanks.

---

### Post by billgoldberg on 2008-10-08
Open up synaptic.

And see if firefox 2 is installed.

Remove it if you find it.

--

Press "alt + f2" and type "firefox".

Does that start firefox 3.03?

It should.

It is easy to change the launcher to start 3.03 instead of 2.xx

Go to "System -> Preferences -> Main Menu".

Find the firefox entry.

Edit it and replace the command with "firefox".

---

### Post by GkProf on 2008-10-08
Thanks. Here's what I find (or don't find):

Synaptic: does *not* list Firefox 2

Alt + f2 does nothing on my system. I seem to remember this problem before, so something is messed up or changed from the default here; is that supposed to open a Run window? If so, and instead I click the Run icon/widget in the task bar at the bottom of the screen, and there I type "firefox," yes, it does load v 3.

In "System -> Preferences -> Main Menu" at the moment it says: "firefox %u"

Not sure what the %u is for. If I change it to just plain "firefox" and close that window, clicking the Firefox icon in the top menu bar still loads v. 2. I also still get v 2 when using the Applications menu and selecting Internet > Firefox Web Browser.

Where to go from here?

Thatnks!

---

### Post by billgoldberg on 2008-10-08
> **GkProf said:**
> Thanks. Here's what I find (or don't find):

Synaptic: does *not* list Firefox 2

Alt + f2 does nothing on my system. I seem to remember this problem before, so something is messed up or changed from the default here; is that supposed to open a Run window? If so, and instead I click the Run icon/widget in the task bar at the bottom of the screen, and there I type "firefox," yes, it does load v 3.

In "System -> Preferences -> Main Menu" at the moment it says: "firefox %u"

Not sure what the %u is for. If I change it to just plain "firefox" and close that window, clicking the Firefox icon in the top menu bar still loads v. 2. I also still get v 2 when using the Applications menu and selecting Internet > Firefox Web Browser.

Where to go from here?

Thatnks!

In synaptic how is firefox 3 lsited?

Using that filename in "Main Menu" to change the launcher should load up firefox 3.

---

### Post by Bölvaður on 2008-10-08
do what bill said, but Im not sure if it is clear enough so here is a little addon to that.

try find out what command you use to execiute firefox3
you know it begins with firefox.... but dont know the rest. so just enter firefox into the terminal and then press tab few times to list all possible endings.

for me it is firefox-3.0

so lets assume you also have firefox-3.0 to run firefox. Then you can either replace or make new luncher.

Click the desktop and create luncher.
enter firefox-3.0 as command and find nice icon for it (you can try find the firefox2 icon somewhere).

or alternativly, you can right click on the menu, find the luncher for firefox2 and change the command for the execution of that program. simple isnt it?

---

### Post by GkProf on 2008-10-08
> In synaptic how is firefox 3 lsited?

v 3 appears in Synaptic both as just "firefox" and as "firefox-3.0" (they are probably different components or something? I assume the one with the 3 suffix is the main lisitng?) whereas v 2 is "firefox-2"

Ahh! Changing the properties to the Toolbar icon to "firefox-3.0" does the trick there. But the Application menu still launches v 2. It's not clear to me where I find ... whoops, just remembered... System > Preferences > Main Menu.

Got it. Thanks. I suppose my only question is, how to remove v. 2. (Though I guess it won't hurt to leave it installed?)

---

### Post by gandaran on 2008-10-08
the firefox in /opt/firefox is a mozillas firefox install, its not listed in synaptic, if you want to remove just delete the /opt/firefox folder, delete the /usr/bin link too and check if there's a firefox 2 launcher in /usr/share/applications, delete this launcher too.
then reinstall firefox 3

---

