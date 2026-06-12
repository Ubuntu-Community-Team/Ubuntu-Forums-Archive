---
title: "Catalyst 11.9 out today. Thought I would take it for a spin"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by alphacrucis2 on 2011-09-28
Well I saw AMD released catalyst 11.9 so I thought I would take it for a spin with Oneiric. Installed via usual buildpkg method. Well it was displaying weird artifacts on boot up and sort of hung. Oddly I was able to the get to the lightDM screen by removing the laptop from the dock. It then seems to be causing more weird stuff after logging in. I found it also hung the laptop on shutdown. Back to 11.8 from the repo for me.

---

### Post by sumski on 2011-09-29
I got 4 xserver segfaults in one hour of usage , so i also downgraded to 11.8 (but didn't have artifacts)

---

### Post by xgt001 on 2011-09-30
i have 3 kernels 3.0.0.11 2.6.37.6 and 2.6.35.30.... apparently 11.9 catalyst hates em all :( :P its not even booting here:lolflag:

EDIT: now its working perfectly in Gnome 3.1.92 Shell...only moving windows is bit glitchy and some rare articrafts (occurs rarely)... awesome shell :D

---

### Post by gururise on 2011-09-30
Tried 11.9 in Gnome Shell.... well, its almost there, but still got some wierd rainbow colors, and graphical glitches.

Enabling "tear free" desktop in the amd control center almost fixes it, but still some issues remain.  Too bad, I was really hoping to use Catalyst in Gnome Shell!

---

### Post by ratcheer on 2011-09-30
I assume Version: 2:8.881-0ubuntu3 is it, it updated today. No problems here with Unity DE.

Tim

---

### Post by kaldor on 2011-09-30
Can anyone report what it's like when using Unity 2d or GNOME fallback?

---

### Post by sumski on 2011-10-01
> **ratcheer said:**
> I assume Version: 2:8.881-0ubuntu3 is it, it updated today. No problems here with Unity DE.

Tim

> fglrx-installer (2:8.881-0ubuntu1) oneiric; urgency=low    * New upstream release 8.881 (11-8).We still have 11.8 in repos (thankfully)

---

### Post by Dangertux on 2011-10-01
Yeah...I wouldn't recommend these I tried them on an HD6300 under Ubuntu 11.04 Natty (2.6.38-8) couldn't even start X server. They didn't do much better in Backtrack 5 R1 or Fedora 15 Lovelock. I switched back to 11.8 almost instantly.

---

### Post by lefuuuu on 2011-10-01
It's working for me, no artifacts or crashes, but it's a bit rough dragging windows. Overall it's perfectly usable but I'd prefer it being smoother.

---

### Post by MAFoElffen on 2011-10-02
> **lefuuuu said:**
> It's working for me, no artifacts or crashes, but it's a bit rough dragging windows. Overall it's perfectly usable but I'd prefer it being smoother.
Users on the Installation & Upgrades Forums still having lots of issues with this driver.  My recommendation to them is 11.8... But waiting to hear when ATI gets this new one "fixed."

---

### Post by TuxIsAwesome on 2011-10-02
Have any of you had issues suspending/hibernating with 11.9?

I cannot get either of these to work properly for the life of me. They suspend and hibernate yes, but they never resume. My backlight effectively seems to be shut off, but pressing the key combo does nothing.

---

### Post by xgt001 on 2011-10-03
> **TuxIsAwesome said:**
> Have any of you had issues suspending/hibernating with 11.9?

I cannot get either of these to work properly for the life of me. They suspend and hibernate yes, but they never resume. My backlight effectively seems to be shut off, but pressing the key combo does nothing.

awesome. same here. it worked perfectly in 11.8

i am using it only for the sake of gnome-shell. The gnome shell from ricotz-ppa has better performance than repo's ppa afaik

---

### Post by TuxIsAwesome on 2011-10-03
> **xgt001 said:**
> awesome. same here. it worked perfectly in 11.8

i am using it only for the sake of gnome-shell. The gnome shell from ricotz-ppa has better performance than repo's ppa afaik

Edit: Pardon my language here, but hot damn people, I thinks I may have fixed it on my own

Apparently both fglrx and radeon were loading on boot, so the two were  for a lack of better terms and to a more apparent guess, fighting over  my system.

Try changing this line in /etc/default/grub

From this
GRUB_CMDLINE_LINUX=""

To this
GRUB_CMDLINE_LINUX="nohz=off highres=off radeon.modeset=0 nomodeset"

It totally seems to have fixed it. I have mine booting in verbose-only mode so the splash screen is irrelevant.

I am concerned about the output of lsmod which still showed radeon as being modprobed, but it either wasn't actually active/probed, or it may have just been shown because something else called it. Either way suspend works on my system now. Have not tested hibernate

---

### Post by pulpo69 on 2011-10-04
when the new fglrx-driver will be in the repos?

---

### Post by alphacrucis2 on 2011-10-04
> **pulpo69 said:**
> when the new fglrx-driver will be in the repos?

Hopefully never.

---

### Post by TuxIsAwesome on 2011-10-05
> **alphacrucis2 said:**
> Hopefully never.

Eh you're probably better off doing what I did in a post above and rather than using the one in the repos, use the .run installer from ATI.

Make sure you remove the open source drivers first, or things will bork.

---

### Post by ratcheer on 2011-10-11
I installed the latest version (2:8.881-0ubuntu4) from the Ubuntu repository, this morning. I don't notice any difference. Still no fix for the gnome-shell problem.

Tim

---

### Post by TunaCanTommy on 2011-10-11
+1

---

### Post by P-I H on 2011-10-11
I think 2:8.881-0ubuntu4 stands for the version Catalyst 11.8. I have installed Catalyst 11.9 and the version number in Synaptic is 2:8.892-0ubuntu1.  With this driver the Gnome panel looks OK.

---

### Post by ratcheer on 2011-10-11
> **P-I H said:**
> I think 2:8.881-0ubuntu4 stands for the version Catalyst 11.8. I have installed Catalyst 11.9 and the version number in Synaptic is 2:8.892-0ubuntu1.  With this driver the Gnome panel looks OK.

Cool. Some day, it will make it to the repos.

Tim

---

### Post by 4Orbs on 2011-10-12
Manually installing the 11.9 driver fixed the Gnome Shell display problem for me also. In order to install the .debs successfully, I had to use the force-overwrite option described on the wiki page for the Natty instructions. Other than the fix for gshell, the new driver seemed to be no different in behavior than the 11.8 from the repo; so if you're not using Gnome Shell there is no advantage (that I can see) in installing the new driver manually. Regardless, Gnome Shell causes videos to play poorly on my machine, compared to the other desktop environments.

---

### Post by pompidoi on 2011-10-12
:( Dang, I thought it'll be fixed already. But I'm using Gnome Shell now in Oneiric Beta 2 and it's smooth. (Gallium 0.4 on AMD CEDAR) I hope the next Catalyst version will be better.

---

### Post by 4Orbs on 2011-10-12
The open source Gallium works nicely for me too, much better than it worked last year, except for a few things that are graphics intensive. I could be happy with it as long as I opt to boot into Windows for those other things (HD mkv, certain games, a few others). Maybe in a year or so we'll never need to mess with proprietary stuff anymore. That would be fantastic.

---

