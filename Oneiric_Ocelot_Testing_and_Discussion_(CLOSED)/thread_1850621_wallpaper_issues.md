---
title: "wallpaper issues"
date: 2011-09-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by flipper T on 2011-09-26
i know its trivial, but hey! :

1 "change desktop background" eats my cpu

2 if i use the "+" to add a image, image selected works once only. if i change it then try to re select the first image, then "ok" button is greyed out

3 workaround used to be to open image in "image viewer" and set as background from there...this no longer works


any answers ?

---

### Post by rburkartjo on 2011-09-26
works fine on my end

---

### Post by cariboo on 2011-09-26
> **flipper T said:**
> i know its trivial, but hey! :

1 "change desktop background" eats my cpu

2 if i use the "+" to add a image, image selected works once only. if i change it then try to re select the first image, then "ok" button is greyed out

3 workaround used to be to open image in "image viewer" and set as background from there...this no longer works


any answers ?

Point 2, you can't re-add a background, because it should already be in the list of backgrounds available, this was discussed early on in the release.

---

### Post by seeker5528 on 2011-09-28
> **flipper T said:**
> any answers ?

For previously added wallpapers go to 'system settings --> appearance --> pictures folder'.

Later, Seeker

---

### Post by flipper T on 2011-09-28
i think what was causing that problem was that i had the saved wallpapers in home/pictures/wallpapers/

moved them to home/pictures/ & seems to be working ok.

also, latest updates have resolved "eating cpu" issue

---

### Post by seeker5528 on 2011-09-28
> **flipper T said:**
> i think what was causing that problem was that i had the saved wallpapers in home/pictures/wallpapers/

moved them to home/pictures/ & seems to be working ok.

I believe any wallpapers you put in '~/Pictures' should show up without having to add them. 

Wallpapers stored elsewhere that were previously added and not moved to another location in the file system after they were added should show up when you go to select a wallpaper and select 'Pictures Folder'. 

I have 3 images in '~/Pictures', one of them not used for wallpaper, the other two copied there when things were broken, the rest of the wallpapers that show up when I go to 'system settings --> appearance --> pictures folder' were all added by clicking the '+' button, browsing to the location on another partition where I actually store my wallpapers, and selecting one or more wallpapers to add. 

You might want to play it a little conservative on how many you add in a single whack, assuming performance is not much if any better than it was in the Gnome 2 equivalent, adding 100+ wallpapers at once might take an excessive amount of time relative to doing groups of 20 or so.

Later, Seeker

---

### Post by chinchin on 2011-10-01
I had a good few hundred large photographs in my ~/Pictures folder, opening the "Change Desktop Background" settings was taking forever with a lot of disk activity.  Eventually I moved the photos into a new sub-folder inside ~/Pictures and it is now much quicker to open and be usable.

It seems strange that the developers would not account for people having a ~/Pictures folder full of large photographs.  Maybe it would be better to use a sub-folder of ~/Pictures for wallpapers.

---

