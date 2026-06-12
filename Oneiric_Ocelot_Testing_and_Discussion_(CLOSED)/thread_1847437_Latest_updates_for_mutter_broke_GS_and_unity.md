---
title: "Latest updates for mutter broke GS and unity"
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-09-20
I just ran the latest updates (I think there were 5, one at least was for mutter) and they appear to have borked both gnome-shell and unity here. Fallback is no good either as no functions are available at all :-(

There is an up side though - conky still works ;)

---

### Post by jbicha on 2011-09-20
Please read the warning on Ricotz' PPA. :-)

We'll be getting a new gnome-shell in the official repositories after beta 2 is released. And next week, GNOME 3.2 is released as the new stable version so things should stabilize.

---

### Post by Quackers on 2011-09-20
Warning? Did I miss something?

---

### Post by jbicha on 2011-09-20
Mutter hasn't been updated in Ubuntu in 2 weeks so I presume you used [https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

---

### Post by Quackers on 2011-09-20
DOH! Yes. I didn't see that warning when I went there!
It's been fine for a while, so I guess I got lazy!
Maybe ppa-purge is in for a bashing then :-)
Thanks jbicha.

---

### Post by ronacc on 2011-09-20
for info I am running GS with no ppa's enabled and updating did not have any bad effects on my install .

---

### Post by tista on 2011-09-20
Guys,

Please write the package and/or git version you had at least if you had some problems... :S

Now I'm using 3.1.92+git in both gs/mutter, works well.

cheers.

---

### Post by Quackers on 2011-09-20
Sorry tista, but those packages are gone now. I did a ppa-purge.

---

### Post by ricotz on 2011-09-21
> **Quackers said:**
> I just ran the latest updates (I think there were 5, one at least was for mutter) and they appear to have borked both gnome-shell and unity here. Fallback is no good either as no functions are available at all :-(

There is an up side though - conky still works ;)

 If g-s and unity isn't working after an update of mutter there is a great chance the problem is something else! Like for example with the x-server/x-driver.

---

### Post by Harry33 on 2011-09-21
I have the Gnome-shell testing PPA (Ricotz) enabled.
I can confirm there are no noticeable issues with those packages, they work just fine.
I can see also gnome-shell is going to be updated to the version 3.1.92.

---

### Post by Harry33 on 2011-09-21
> **Quackers said:**
> I just ran the latest updates (I think there were 5, one at least was for mutter) and they appear to have borked both gnome-shell and unity here. Fallback is no good either as no functions are available at all :-(

There is an up side though - conky still works ;)

Hmm, I see you tried to correct the heading (from ppa:ricotz/testing).
It is a pity we members cannot do that.

---

### Post by VinDSL on 2011-09-21
> **Harry33 said:**
> Hmm, I see you tried to correct the heading (from ppa:ricotz/testing).
It is a pity we members cannot do that.
Wow!  You have a keen eye!  I thought I was the only one that noticed things like that...  :D

Anyway, as fate would have it, I got caught flat-footed.  Bad timing, on my part...

I've been running proprietary nVidia drivers, Xserver 1.11, Ricotz/testing PPA, and (you name it).

Truth be told, my biggest problem is, I lost internet connectivity , e.g. web access, on every 11.10 DE that I'm running - Unity 2D /3D, Classic, GS, E17, blah, blah, blah.

If I had web access, I could fix things, but...

It's so much easier to simply boot into Maverick, browse the forums, and wait for someone else to discover the silver bullet.

So, here I sit, under the Cork Tree, smelling the flowers - revisiting UbuMM.

Wake me up, when there's a fix, please.  LoL!

---

### Post by VinDSL on 2011-09-21
Oh, drat!  Got my networking going again... missing file.  Sigh!

Now, I can be lazy and surf the web in Unity 2D or E17, or go fix Unity 3D and GS.

Decisions, decisions...

I think I'll eat a sandwich and maul it over.  :)

---

### Post by VinDSL on 2011-09-21
Okay... working my way back up the ladder, from the pits of hell.  :)

I'm logged into Unity 3D now.  Everything looks fine!

Gonna go try GS...

---

### Post by VinDSL on 2011-09-21
I'm in GS now.  Yeah!

That was fun...  :D

Here's the sequence:

[LIST]
[*]Got home and booted into a Unity 2D session.

[*]Did a normal update via Synaptic.

[*]Restarted and 11.10 et al. was borked.  No panels, no network, all DEs (creds to Canonical)

[*]Booted into 'Old Faithful' (Ubu Maverick 10.10).

[*]Mounted my UbuOO root partition and copied /usr/lib/thunderbird-7.0/libnss3.so to /usr/lib/i386-linux-gnu/ (creds to MacUntu)

[*]Booted into Ubu Oneiric Unity 2D - networking now working.

[*]Purged xorg-edgers PPA - left Ricotz/testing PPA intact (creds Harry33)

[*]Tested all installed 11.10 DEs.  Everything is working, including GS.
[/LIST]

Okay, I'm ready for you, devs!  Bring on the breakage... LoL!

---

### Post by Cloud79 on 2011-09-21
I reinstalled package libnss3 and then my machine started working again

---

### Post by VinDSL on 2011-09-21
> **Cloud79 said:**
> I reinstalled package libnss3 and then my machine started working again
Sweet!  Nice n' simple.

Unfortunately, I couldn't reinstall libnss3.so because my internet connection dissapeared, along with it.  I had to do some dancing on the keyboard.

All's well that ends well, yes?

I'm hungry again.  I think I'll eat another sandwich...

---

### Post by Cloud79 on 2011-09-21
i had to run dhclient <interface> to get an ip adress (if on cable that is)
then aptitude reinstall libnss3


:)

---

### Post by Harry33 on 2011-09-21
> **VinDSL said:**
> I'm in GS now.  Yeah!

That was fun...  :D

Here's the sequence:

[LIST]
[*]Got home and booted into a Unity 2D session.

[*]Did a normal update via Synaptic.

[*]Restarted and 11.10 et al. was borked.  No panels, no network, all DEs (creds to Canonical)

[*]Booted into 'Old Faithful' (Ubu Maverick 10.10).

[*]Mounted my UbuOO root partition and copied /usr/lib/thunderbird-7.0/libnss3.so to /usr/lib/i386-linux-gnu/ (creds to MacUntu)

[*]Booted into Ubu Oneiric Unity 2D - networking now working.

[*]Purged xorg-edgers PPA - left Ricotz/testing PPA intact (creds Harry33)

[*]Tested all installed 11.10 DEs.  Everything is working, including GS.
[/LIST]

Okay, I'm ready for you, devs!  Bring on the breakage... LoL!

Well thanks for those creds, VinDSL ):P.

Yeah, that was one unlucky ca-certificates update.

---

### Post by Quackers on 2011-09-21
Yes, as discussed in the thread which was stickied earlier, it seems to have been the ca-certificates update and not the ricotz ppa updates that borked everything. Sorry ricotz!
Apparently it removed the libnss3.so from /usr/lib/x86_64-linux-gnu directory. This broke internet access and gnome-shell.
As discussed here
[http://ubuntuforums.org/showthread.php?t=1847446](http://ubuntuforums.org/showthread.php?t=1847446)

---

