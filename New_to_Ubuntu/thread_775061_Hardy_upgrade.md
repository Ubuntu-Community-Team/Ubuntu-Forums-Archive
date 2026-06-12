---
title: "Hardy upgrade"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by kokomonjo on 2008-04-29
Hi all, I am fairly new to Ubuntu and Linux. I did my first instal back in December. I have a dual-boot on my box. Vista for school and Ubuntu for everything else. Anyway I just upgraded from Gutsy to Hardy, and i had my compiz fusion going when i did this as well as awn for my menu (i like eye candy). Anyway after installing the new version of ubuntu my awn toolbar is gone. and none of my drop down menus are visible. This makes using the OS next to impossible. Does anyone know how i can correct this? for when i say nothing is visible i mean for instance when my mouse goes over the time on my toolbar it flames up as if it is going to display the time then nothing. if i go and click on my menu button it then again flames up like its going to open and nothing. no visible menus.

---

### Post by sowelie on 2008-04-29
I would first try and disable desktop effects.  System -> preferences -> appearance, go to visual effects tab and go to none.  See if your menus come back.  If that works, make sure you have the compizconfig-settings-manager package installed and go to system -> preferences -> advanced desktop effects and go to window rules to make sure nothing is hidden.  As far as awn goes, does it come up if you go to applications -> accessories -> avant window navigator?

---

### Post by kokomonjo on 2008-04-29
Hi Thanky ou for your quick response. The problem with that is nothing is visible. I would disable the effects but i can not navigate to it. nothing is visible when i click the start menu. i can scroll down the where the menu would and you can see the flame from the cascade but then there again you can see nothing.

---

### Post by akiratheoni on 2008-04-29
Hit CTRL+ALT+F1 to get into a terminal. Then log in and type:

> metacity --replace

That should replace Compiz Fusion and/or emerald temporarily and then hit CTRL+ALT+F7 to go back to the desktop.

---

### Post by kokomonjo on 2008-04-29
Ok, So i was able to blindly find the advanced desktop settings (the size of the flame helped me to judge the location in the menus) then i disabled the animations and was able to see the drop down from the start menu. i thought everything is great. i went and restarted my computer. and to my horror was not able to see the drop down menu. this time with no flame to tell me it was even open. so i blindly navigated to the add/remove programs and totally removed compiz-fusion. no luck. still no drop down. i just tried the CTRL+ALT+F1 thing typed in "metacity --replace" and it said "unable to open X display". I am at wits end here. All i want is to be able to use the new version of Ubuntu. oh btw when i boot there is an additional ubuntu boot but it is in the graphics safe mode when i upgraded did ubuntu install twice on my partition?

---

