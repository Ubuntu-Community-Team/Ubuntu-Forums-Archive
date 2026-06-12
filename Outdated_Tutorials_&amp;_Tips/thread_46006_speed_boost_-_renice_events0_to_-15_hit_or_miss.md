---
title: "speed boost - renice events/0 to -15 ?hit or miss?"
date: 2005-07-02
forum: Outdated Tutorials &amp; Tips
---

### Post by virgule on 2005-07-02
I have watched **top** running for a few minutes. I think its fun watching processes running and trying to guess how they stack to each others... I have a few question tho.. 

1- Several processes wear a **-10** nice value (ie: events/0, khelper, kblockd, aio...) I know negative nice mean higher priorities (huh!?!?)... I asked to myself what would happen if I raise priotity even more.. I decided events/0 would be my test dummy. So I hit 'r' key and renice PID #3 to -15 and immediately noticed a performance gain as the computer react quicker. I'd like to know I am not just imagining things...

2- Is this dangerous? Im only asking because playing with nice is the only thing I have done so far that completetly frooze my Linux installation (absolute priority on XFree86..so dont do that ) I stood away from nice since then now i am back on it but I want improvement and no crash ;)

3- How does one make nice values permanent?

---

### Post by picpak on 2005-07-02
Wow, I was just playing with the priorities a little while ago.

I didn't check for a speed boost, but I saved my session to see if it'd keep the priorities. Unfortunately, it didn't. Any ideas?

---

### Post by virgule on 2005-07-03
silly me.. I just realized this is not the proper section for such thread. :(

..not much ideas. Maybe put some lines in init.d or something..

---

### Post by Lunde on 2005-07-04
[QUOTE=virgule]silly me.. I just realized this is not the proper section for such thread. :(

..not much ideas. Maybe put some lines in init.d or something..[/QUOTE]
 You could allways change it into an experimental Howto :-)

---

