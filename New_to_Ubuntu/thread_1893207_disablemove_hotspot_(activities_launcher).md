---
title: "disable/move hotspot (activities launcher)"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by chickenpoxparty on 2011-12-09
Hi all, first post for me, hope this is the right forum.

I switched from unity to gnome last night and im liking it a lot (especially with all the extensions you can get over at [https://extensions.gnome.org/](https://extensions.gnome.org/). 

The only thing i would like to change is the behavior of the hotspot in the top-left corner. Id prefer to disable it completely since using the super key does exactly the same thing and sometimes the activity menu gets activated when i hover my mouse to close to the corner. 

Ofcourse ive already googled for a solution but the only one i found ([http://askubuntu.com/questions/5573/how-do-you-disable-the-automatic-activation-of-gnome-shell-activities-button](http://askubuntu.com/questions/5573/how-do-you-disable-the-automatic-activation-of-gnome-shell-activities-button)) doesnt work for me since my panel.js is different from the one mentioned in the link. 

So, can anyone tell me how i can disable the hotspot functionality in Gnome 3.2? Thanks a lot!

---

### Post by chickenpoxparty on 2011-12-10
Right, found the solution:

1. Backup layout.js:

*sudo cp /usr/share/gnome-shell/js/ui/layout.js /usr/share/gnome-shell/js/ui/layout.bak*

2. Open layout.js:

*gksudo gedit /usr/share/gnome-shell/js/ui/layout.js *

3. In layout.js, look for the line: this._corner = new Clutter.Rectangle

4. 4 lines down (under opacity): 

change reactive: true --> reactive: false

5. Save changes to layout.js

6. Alt-F2 - R

and done.

---

### Post by kwacka on 2012-09-14
many thanks for this tip - been looking everywhere for how to turn off this annoying 'feature'.:mad:

---

