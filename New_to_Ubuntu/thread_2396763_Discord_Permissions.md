---
title: "Discord Permissions"
date: 2018-07-20
forum: New to Ubuntu
---

### Post by mason4290 on 2018-07-20
I have a wireless headset which I use to talk to people and listen to music. It is working properly in my system settings, but when I attempt to use discord it does not work. I can't hear or talk to people. 

I went to the "Ubuntu Software" application and went to discords permissions. I enable bluetooth but when I hit close it does not save. Youtube and other audio relaying apps work just fine. Why can't I save my permissions? I do believe it needs bluetooth permissions as that is what my wireless mic uses.

Thanks in advanced to anyone that helps me, I just made the switch to Ubuntu and I am really hoping to use it as a full time OS. Thanks guys!

---

### Post by deadflowr on 2018-07-20
You probably want to give discord the bluez interface access.
since this from the Software store, it's probably the snap version of discord.
I don't see an apt version...

Try something like
```
sudo snap connect discord:bluez
```
it'll tell you if it works.

More on snap references here:
[https://docs.snapcraft.io/reference/]("https://docs.snapcraft.io/reference/")
including interfaces and confinement levels of snaps.

---

