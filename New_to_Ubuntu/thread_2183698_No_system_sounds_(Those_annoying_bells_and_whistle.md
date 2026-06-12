---
title: "No system sounds (Those annoying bells and whistles)"
date: 2013-10-25
forum: New to Ubuntu
---

### Post by amhndu on 2013-10-25
Hello,
I installed Ubuntu 12.04 several months ago,everything works fine , I watch movies , shows etc. the sound works for everything else but for any system sounds.
It didn't worked on Unity , lxde (lubuntu-core package) , xfce except the drum sound at login prompt.
It isn't very useful although but this makes me feel something is wrong with my installation , so how can i get them.

FYI , I don't have unity now.
Thanks in advance

---

### Post by fantab on 2013-10-26
There is nothing wrong with your installation. Its just fine.
Ubuntu, for some reason has the sounds disabled by default. You have to enable them if you like.

To get your desktop login-
Open 'Startup Applications' or from terminal
```
gnome-session-properties
```

Create a new Startup for Login sound, use ADD button.

Name = GNOMELogin Sound
Command = /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login" *(copy and paste this in the Command box)*
Comment = Plays Ubuntu login sound.

Save it. Reboot.

For all the other system sounds-
Open 'System Settings' -> Sound -> Sound Effects
Increase the 'Alert volume' slider to the full. Make sure its 'ON'.

Thats it.

---

### Post by amhndu on 2013-10-27
Thanks for replying , does your solution work if i'm on lxde.

---

### Post by fantab on 2013-10-27
It should.

---

