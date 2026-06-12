---
title: "swfdec in firefox not working"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by orwellus on 2008-06-19
Here I am again, third time this week.

I am trying to get the swfdec flash player to work in firefox. In synaptic, I uninstalled the adobe flash player, and then installed swfdec. But, when I go to site like YouTube or Hulu I get a message that says I need to install the flash player. Anyone know how to get the swfdec working in firefox. I have Gutsy installed on my system

Thanks.

---

### Post by Dynaflow on 2008-06-19
Do you have Java installed and working?

Also, are you using swfdec instead of the Adobe Flash player for ideological reasons, or for some technical reason?  If the latter, you might be better off reinstalling the Flash player and its accouterments using this guide:  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by orwellus on 2008-06-19
I have iced-tea java plug installed and it's working. I am trying a different player, because, when I watch a video on hulu with adobe flash the video is jumpy, and doesn't stream correctly. I heard good things about swfdec on another ubuntu thread (which I can't seem to find right now) so I thought I would give it a try. It looks like that guide you pointed my to is for hardy, I have gutsy. When I first installed adobe flash, I opened firefox, and then went to youtube where it asked me to install the missing plugin, so I installed the adobe plugin. (I have since uninstalled adobe flash).

---

### Post by Dynaflow on 2008-06-19
> **orwellus said:**
> I have iced-tea java plug installed and it's working. I am trying a different player, because, when I watch a video on hulu with adobe flash the video is jumpy, and doesn't stream correctly. I heard good things about swfdec on another ubuntu thread (which I can't seem to find right now) so I thought I would give it a try. It looks like that guide you pointed my to is for hardy, I have gutsy. When I first installed adobe flash, I opened firefox, and then went to youtube where it asked me to install the missing plugin, so I installed the adobe plugin. (I have since uninstalled adobe flash).

The guide also has parallel sections for pre-Hardy versions.  If you haven't already added the Medibuntu repository some other way, follow the instructions under "Preparation."  Then, skip the first section of "Installation" that says "UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY," and go to the section under the heading "PRE-UBUNTU FAMILY 8.04 HARDY HERON USERS ONLY."  I would remove the IcedTea plugin before you begin, though.

If still no joy, there is a troubleshooting section at the bottom of that first post, with subsections on how to coerce Java and Flash into doing your bidding.

---

