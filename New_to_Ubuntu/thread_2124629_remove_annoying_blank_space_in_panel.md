---
title: "remove annoying blank space in panel"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by Mr. ViC on 2013-03-11
Could anyone please tell me how do I remove that annoying blank space there? In the top panel?

It's not a "spacer" applet. And I can't find a way to remove it.

[IMG]http://img831.imageshack.us/img831/3069/screenshotfrom201303111.png[/IMG]

---

### Post by carl4926 on 2013-03-11
Could be LXDE bug
From suspend I get a ever increasing space with each suspend/resume

---

### Post by Mr. ViC on 2013-03-11
It seems a bug of some sort. Here's the look right now:

[IMG]http://img713.imageshack.us/img713/9296/74433807.png[/IMG]

 It's just that my low-end laptop is really damn fast right now. Just wanted to fix that annoying little thing.

---

### Post by ajgreeny on 2013-03-11
Here's a couple of possible related launchpad posts with perhaps fixes to the LXPanel system tray expansion problem: 
[https://bugs.launchpad.net/ubuntu/+s...el/+bug/990619]("https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/990619")
[URL="https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/846878"]https://bugs.launchpad.net/ubuntu/+s...el/+bug/846878

[/URL][COLOR=#000000]I run Lubuntu 12.04 fully updated on two machines and do not see the problem any more, though it was present when I first installed on both.  I am not aware of doing anything to stop it showing apart from updates as they are available.

There is also a workaround here [/COLOR]http://ubuntuforums.org/showthread.php?p=11690707#post11690707 which simply restarts the panel[COLOR=#000000], which is what I used when I had the problem.
[/COLOR]

---

### Post by CaptainMark on 2013-03-11
I have seen this before on lubuntu, basically its a specific amount of white space that attaches itself to (I believe) the system-tray applet or notification-tray applet (I forget its exact name now sorry, it been a while since I used lubuntu) try removing the sys-tray (or similar) applet and adding it again.
When I noticed it, it only affected one user, me, so I moved my data files to a backup deleted my user, made a new one from scratch with a fresh home folder and then restored my data files from the back up, long winded but it worked

Edit: from the post before mine, I believe its bug #846878 which I've added myself to, also notice that there are some other workarounds on there which would be easier than mine

---

### Post by Rex Bouwense on 2013-03-11
Right click on the lxpanel, and choose Add/Remove.  Make sure that the box next to Task Bar (Window List) is checked.  That will stretch them.  That should be the only box checked.  At least that fixed it for me.

edit:  Hey Mark.  The way you did it works as well.  When I had the problem, it effected one person as well (me).

---

