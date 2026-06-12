---
title: "change rhythmbox to amarok (hardy)"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by biji on 2008-09-17
Hi,
i've followed instruction here to change rhythmbox to amarok:
[http://sofabedz.co.uk/linux/iPod.html#Open%20Amarok%20by%20default](http://sofabedz.co.uk/linux/iPod.html#Open%20Amarok%20by%20default)

it works but... all my song in ipod queued to amarok how to avoid this... thanks :guitar:

---

### Post by mc4man on 2008-09-17
there are 2 issues
First to get amarok to auto connect to ipod and then not to load all the tracks in a big playlist.
While it may be possible to use a copy .desktop method with a different launch command i think this works best.
Based on using an existing choice to autorun on ipod insertion to run a script with a proper launch comm. ( amarok -m %d)

[http://ubuntuforums.org/showthread.php?p=5562637#post5562637](http://ubuntuforums.org/showthread.php?p=5562637#post5562637)
scroll up for more info

It may be possible to adapt this method below for music player use (ipod), but I think the above linked method is better, and easily reverted if desired 

[http://ubuntuforums.org/showthread.php?p=5459412#post5459412](http://ubuntuforums.org/showthread.php?p=5459412#post5459412)
(alternate method

Edit: Because you have already created a .desktop in /usr ... I'd use script method. You may want to clean up what you've done. You could experiment with the launch comm. I'm suggesting, but I'd be **careful**

---

