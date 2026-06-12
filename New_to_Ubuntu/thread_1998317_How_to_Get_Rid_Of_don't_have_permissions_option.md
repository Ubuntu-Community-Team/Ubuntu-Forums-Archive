---
title: "How to Get Rid Of don't have permissions option"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by MrBledi on 2012-06-06
i wanna copy paste this theme called  bridge with folder to the usr/share/themes, that  included themes inside but it says to me that i don't have permissions,  so i thought to go into themes folders to properties to change the  chmode to 666 or something, but it says that i'm not the owner, what to  do?? THANKS!

---

### Post by idoitprone on 2012-06-06
> **MrBledi said:**
> i wanna copy paste this theme called  bridge with folder to the usr/share/themes, that  included themes inside but it says to me that i don't have permissions,  so i thought to go into themes folders to properties to change the  chmode to 666 or something, but it says that i'm not the owner, what to  do?? THANKS!

```
gksudo nautilus
```

now move your files around

permission are there for a reason. There is no reason to change it

---

### Post by deadflowr on 2012-06-06
It is highly recommended that you do not change the permissions for a systems folder, such as /usr/share/themes.
Instead, use sudo to move your files into the folder.
You can do this, really, two ways:
option one, open up a terminal and type :
```
sudo mv /home/yourusername/thefolderyourfileisin/thefile /usr/share/themes
```

option two, open a terminal and type:
```
gksudo nautilus
```

option two will open the nautilus file manager as root and will allow you to manipulate your files at will.

When I use option two, I simply open up a second pane, navigate to the various folders and files I want to move and right click copy to or move to and select other pane.

Be careful when in root as absolute power, corrupts absolutely.
And it is easy to get careless, and start changing things willy-nilly. Which can cause system-wide breakages.

---

### Post by MrBledi on 2012-06-06
thank you very much!

---

### Post by deadflowr on 2012-06-06
Oops, I should have posted that the first option will move the file, to simply copy it change the mv command to cp.
I hope everything turns out okay. One thing I sorta dislike about gnome3 is the difficulty in adding new themes.Gnome2.xx was much easier.

---

### Post by idoitprone on 2012-06-06
> **deadflowr said:**
> Oops, I should have posted that the first option will move the file, to simply copy it change the mv command to cp.
I hope everything turns out okay. One thing I sorta dislike about gnome3 is the difficulty in adding new themes.Gnome2.xx was much easier.

blame gnome team and steve jobs' distortion field. apparently gnome people where "inspired" by apple

---

### Post by MrBledi on 2012-06-06
You're right , i don't know about gnome2 but now i'm having some difficulties, i hope that i will get everything sort, from yours support! :D

---

