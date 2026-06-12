---
title: "Various questions"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by joum on 2008-06-28
Hi everyone!

I've been messing around with xubuntu on my laptop and I'm loving it so far!

I've got everything pretty much sorted out and configured right except for a few things, and I was hoping to find soome help here.

This is what's been going wrong:

- everytime I boot, the "Compiz Fusion Icon" app doesn't load right, wich results in no borders to my windows. Compiz doesn't work either till I load the Compiz Fusion Icon. Maybe I can set it as session definition ore something like that. Any thought on this?

- I tampered a bit with the native calender application "Orage" and now it always loads on boot, which is bad, because I don't want to use it at all.

- I can't seem to add new launcher icons in the top panel, next to the orginal Firefox one. It was very easy to do this in Ubuntu, by right-clicking in the Applications menu and clicking "Add to Panel". Should this work in Xubuntu too? Can't figure it out...

Anyway, if anyone has any idea on how to fix these little questions, please let me know. Thanks!

---

### Post by defrex on 2008-06-28
I would highly recommend using xfce's built in light weight composition manager rather then Compiz Fusion.

I only used xubuntu briefly, so I might be wrong, but I think you can just drag an icon that on the main menu onto the panel.

---

### Post by hyper_ch on 2008-06-28
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by joum on 2008-06-28
I actually have figured out how to make the Compiz Fusion Icon auto load on boot, so that's taken care of! :D It actually performs very well and hasn't crashed yet on any ocasion, even when I had a bunch of RAM chuggers running at the same time.

To do this, you can go to "Applications > Settings > Settings Manager", you then have a "Auto Started Apps" Icon, if you click on it, you can see some of the apps that are loaded on your system during boot. You can then add any app you want on load. In the Compiz Fusion Icon case, the command line is: ```
fusion-icon
```

Regarding the icons and the calendar problems, I'm still trying figure it out! :)

---

### Post by joum on 2008-06-28
> **hyper_ch said:**
> it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.


You're right! I now see that it was kind of lame to do it this way... I'll keep that in mind from now on...

---

### Post by aimpau on 2008-06-28
For orage:
Don't just hit the 'x' mark. Go to file and exit it properly using the "QUIT" not the "CLOSE".

For the launcher panel buttons:
Right click on a panel >> Add new Item >> Launcher

tip: You can add a lot of panel items that make xubuntu an eyecandy as well as being fast.

---

