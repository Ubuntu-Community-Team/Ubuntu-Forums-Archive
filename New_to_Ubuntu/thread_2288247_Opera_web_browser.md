---
title: "Opera web browser"
date: 2015-07-25
forum: New to Ubuntu
---

### Post by openation1 on 2015-07-25
Hello everyone: I download opera from the WEB. and then i ran the program from Ubuntu Software Center and it said that i have to run it from the terminal.......... I don't know how to do it please advice me what I have to do........ thank you so much.

---

### Post by openation1 on 2015-07-25
Hello everyone:   I download Opera from the WEB, and then ran the program from Ubuntu Software Center......... It said that it was installed but it had to be run from a terminal and I don't know how to do it................. please help me on this matter and I would appreciate it very much. thank you so much...........

---

### Post by Frogs Hair on 2015-07-25
I' am an opera user and you shouldn't have to start it from the terminal . It should start from the icon. If something has gone wrong the command varies depending on version.

Version 12.16 (old)```
 opera
``` The latest version would use the following ```
opera-stable
```

---

### Post by ajgreeny on 2015-07-25
I've never used opera.  What is the filetype of your download?

If it is a .deb package the easiest way is to use either ```
sudo dpkg -i /path/to/opera.deb
```in terminal or use gdebi, which you will have to install first.

See all the info at [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

EDIT:
I was just about to merge this post but PaulW2U beat me to it.

@ openation1, just in case you knew you had posted twice, please do not do so in future, and if it happens accidentally please use the "Report post" button at the bottom of one and ask that it be deleted.

---

### Post by PaulW2U on 2015-07-25
Threads merged, probably a forum glitch.

---

### Post by deadflowr on 2015-07-25
With Ubuntu if the icon doesn't show up in the left side launcher panel(where icons from newly installed apps from the software center normally go)
I'd either click on the top most icon, called the dash, and use the dash search feature to find opera (simply type opera and it should show up in the listing)

Or from a terminal, run the above suggestion, *opera*.
Once any graphical app starts running, an icon will appear in the launcher panel. Just right click on that icon and you will see a few options select the option lock to launcher.
And now when you close Opera, the icon should remain, locked to the launcher.

You can then drag the icon anywhere in the launcher panel except the top and bottom (those launcher icons are locked; the dash and the trash)

Hope it helps.

---

