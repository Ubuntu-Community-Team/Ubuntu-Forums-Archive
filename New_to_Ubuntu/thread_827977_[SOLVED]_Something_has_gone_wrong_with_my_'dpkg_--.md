---
title: "[SOLVED] Something has gone wrong with my 'dpkg --configure -a'!!! :("
date: 2008-06-13
forum: New to Ubuntu
---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-13
Hey all, Armageddon here!

Saw on another thread about something of Alt+Ctrl+F1... Didn't know what in the world that was so i tried it out. At the same time however, I had updates going on. Thought nothing of it...However, I was wrong, very very wrong...I didn't know how to get out of that mode however, and I tried a hard reboot.

Turns out, I have messed up something in my system. I wasn't to panicky as it said that all I had to do was type in "dpkg --configure -a" and everything would be dandy and nothing else would happen. This happened on Update Manager. However, when I went and typed it in my terminal, it tells me I need superuser privileges to do that.:mad: (Great, now I have do do another thing for this stupid thing to work) I thought, O.K. fine... I went to Add/Remove programs to download the superuser mode of that program, however, it says my "dpkg..." is messed up! Now what do I do? Is it just "sudo dpkg..." or do I need that program or some other command to go into Superuser mode? :confused:

Serves me right I guess to be messing around with my system ](*,) but I came here to get help, so if anyone could tell me something about whats going on, it would be very appreciated!

P.S. - For some reason, I can still download updates for my Firefox plugins. Hope this helps!

Sincerley,
Armageddon

---

### Post by drs305 on 2008-06-13
All it means is that you run the command with sudo. You need 'superuser' powers to change system files. You gain that temporarily by using the sudo command:
```
sudo dpkg --configure -a
```
It will ask for your password but you won't see it as you type. Just type it and ENTER.

---

