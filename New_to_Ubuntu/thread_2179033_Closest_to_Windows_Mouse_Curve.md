---
title: "Closest to Windows Mouse Curve"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by Danny_Michel on 2013-10-06
Was wondering if some of us could share our mouse settings here if you believe yours is the closest possible configuration to the Windows mouse curve.

---

### Post by ibjsb4 on 2013-10-06
When you say "Windows mouse curve" all I can think of is ..

[ATTACH=CONFIG]246780[/ATTACH]

---

### Post by Danny_Michel on 2013-10-06
I can try it explain it like this...
The pointer is fast, but it stops when you stop - no slipping around. It needs actual blatant movement to go anywhere(more natural), but if you move the mouse softly, it moves slowly rather than slipping around.

---

### Post by heir4c on 2013-10-06
Here nothing changed, just the default configuration:
(moving my mouse 2,5cm = on screen 35cm)

[IMG]http://i.imgur.com/B7eUEgU.png[/IMG]

---

### Post by Danny_Michel on 2013-10-06
thanks, but the above is what I would consider extremely 'slippery'.
xset m 1 1 seems decent, but still a bit slippery and not as fast as windows.

---

### Post by heir4c on 2013-10-06
You want it faster? Or...?
When I set it totally to 'fast' (in Dutch 'snel') than that is real fast, to fast for me.
Then I move my mouse just 1 cm for the same 35cm and when I set it on slow than I have to move my mouse 5cm for the 35cm.

---

### Post by ibjsb4 on 2013-10-06
Have you tried to adjust setting in System Settings>Mouse?  If you don't get the desired settings, maybe try a different configuration package.  I don't use the package in the link, it just sounds like you want.

[https://apps.ubuntu.com/cat/applications/precise/gpointing-device-settings/](https://apps.ubuntu.com/cat/applications/precise/gpointing-device-settings/)

---

### Post by Danny_Michel on 2013-10-06
I've tried it, but it doesnt give me options.
[ATTACH=CONFIG]246782[/ATTACH]
no scrolling tab - no speed tab - nothing,

---

### Post by ibjsb4 on 2013-10-06
Ok, try manually editing some dconf settings.  You first need to install dconf-tools.

In terminal:
```
sudo apt-get install dconf-tools
```

No restart required.  Navigate to mouse settings.

[ATTACH=CONFIG]246784[/ATTACH]

---

### Post by Danny_Michel on 2013-10-06
Awesome! looks like motion-acceleration - -1.0 and motion-threshold - 20 is pretty close to windows

---

### Post by ibjsb4 on 2013-10-06
Bingo

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums :)

---

