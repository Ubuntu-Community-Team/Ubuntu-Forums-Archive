---
title: "Hoary Screen Resolution:answers"
date: 2005-04-01
forum: Outdated Tutorials &amp; Tips
---

### Post by robert crowther on 2005-04-01
Several users have reported that 'Hoary Hedgehog' will not allow them to alter their screen resolutions. Such changes may be prefereable. For example 'Hoary' locked my screen to;
 
85Hz Refresh Rate.
640x480 Screen resolution

At this resolution, OpenOffice is unusable. Plainly, I should be able to lower the refresh rate to gain resolution, but 'Hoary' won't let me.

I have several solutions, culled from forums and 'man' pages. I'm offering solution 5 as the one. Keep the keep post size down...



5 Add HorizSync and VertRefresh commands to the Display block of xorg.config. For my monitor, not yours, the commands look like this;

HorizSync 30-50
VertRefresh 50-185

Note: Several reports put a space in 'Vert Refresh', or miss off capitals. I can confirm that, on my install, the extra space will crash X. See 'man xorg.conf' for the official definitions.

You must get your monitor specification from the web.

This solution fixed my display, and involves minimal tinkering. If anyone is interested, i can post other sections of the document, or if they feel its appropriate, I could put the lot onto the wiki.


Good luck everyone, because it seems like 'Hoary' is an excellent operating system.
 


Robert

---

