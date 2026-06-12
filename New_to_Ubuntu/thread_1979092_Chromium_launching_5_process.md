---
title: "Chromium launching 5 process?"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by d4m1r on 2012-05-12
Hey guys, I have 2 seperate problems as demonstrated below;

1) Chromium launches 5 processes (I don't like this...it should only be launching 1. Even Firefox is annoying because it launches 2).

2) Chromium is using over 357MB RAM just to run 1 instance of it....Given, in incognito mode, and 3 tabs, but that still seems like way too much.

[IMG]http://i.imgur.com/P2vDwl.png[/IMG]

---

### Post by d4m1r on 2012-05-12
Slight update, but it seems to launch 3 processes right off the bat for incognito mode, and then launches a separate process for each tab I open....Excuse my French, but that is just dumb ](*,) Anyone have any suggestions on how to fix/change this or is it even possible?

---

### Post by Enigmapond on 2012-05-12
Each tab in Chrome is a separate process...this is a good thing and where is differs from FF. If one tab freezes or get buggered by a web site, the others will still work...in all other browsers if one goes, they all go. But that is a bit high...my Chrome opens tabs at about 40-90MB each of Memory.

---

### Post by MonkeyPaw on 2012-05-12
It's all a part of Chrome/Chromium sandboxing. It's totally a good thing, as it keeps rogue sites from reaching beyond their dedicated process, thus keeping your tabs fully separate. Multiple processes are not the enemy in today's multi-core CPU world.

As for RAM usage, I'm sure it just takes what is available and caches your content. It also probably caches your entire browsing session, which in turn gets reloaded from the cached RAM as Ubuntu manages it. Again, this is a good thing, as it reduces load times at the expense of cheap RAM. Personally, I want things to make use of my RAM. Just looking at your setup, FF is taking almost 1GB.

---

### Post by d4m1r on 2012-05-12
> **MonkeyPaw said:**
> It's all a part of Chrome/Chromium sandboxing. It's totally a good thing, as it keeps rogue sites from reaching beyond their dedicated process, thus keeping your tabs fully separate. Multiple processes are not the enemy in today's multi-core CPU world.

As for RAM usage, I'm sure it just takes what is available and caches your content. It also probably caches your entire browsing session, which in turn gets reloaded from the cached RAM as Ubuntu manages it. Again, this is a good thing, as it reduces load times at the expense of cheap RAM. Personally, I want things to make use of my RAM. Just looking at your setup, FF is taking almost 1GB.

Thanks for the comments guys but:

1) I consider multiple proccesses bad as if it freezes/crashes/etc, now I have to worry about killing the right process....Yes, managing multiple tabs within a single process is hard, but if done right, it means if the application freezes/crashes/etc, I can just kill the entire program by killing a single process.

2) Yes in my screenshot Firefox is using 1GB but it has 15-20 tabs open.....350+ MB of RAM for 3 tabs is far from good :???:

---

### Post by Utkarsh Ray on 2012-05-12
> **MonkeyPaw said:**
> It's all a part of Chrome/Chromium sandboxing. It's totally a good thing, as it keeps rogue sites from reaching beyond their dedicated process, thus keeping your tabs fully separate. Multiple processes are not the enemy in today's multi-core CPU world.

As for RAM usage, I'm sure it just takes what is available and caches your content. It also probably caches your entire browsing session, which in turn gets reloaded from the cached RAM as Ubuntu manages it. Again, this is a good thing, as it reduces load times at the expense of cheap RAM. Personally, I want things to make use of my RAM. Just looking at your setup, FF is taking almost 1GB.

True.
The source of this annoyance/convenience is Chrome. This is what we pay for speed and security.
I was astonished at first to see that my friend's notebook had its memory gobbled by Chrome but later found that it is easier browsing experience when we kill only the ill-mannered webpages and let others run fine.
Such high memory consumption is in Windows version also.

---

