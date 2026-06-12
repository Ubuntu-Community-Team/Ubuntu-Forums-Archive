---
title: "Can't get volume-change sound to play"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by creator101 on 2011-11-27
Usually when I change the sound volume with the buttons on my laptop (hardware) I get a nice popping sound telling me how loud the volume is. However, now I only get it when I adjust the volume with the sound settings program, not with the hardware buttons. How do I fix this??? It would be appreciated.

:(:(:(

---

### Post by creator101 on 2011-11-27
Hello?

---

### Post by creator101 on 2011-11-28
bump

---

### Post by sagarkane1989 on 2011-12-13
Start nautilus with root access by opening terminal (Ctrl+Alt+T)

Type "sudo nautilus" (without quotes)

Type in the password. (The characters don't show. Just type it and press enter)

go to /usr/share/sounds/ubuntu/stereo

copy all the files in that folder and paste them at /usr/share/sounds

If you have used dconf editor before to mess with the sound settings in org then return it to default value (freedesktop). If not then skip this step.

Close nautilus. Exit terminal. Lougout and Login again.You will have gotten back the popping sound and also other system sounds if they were missing before. (logon sound, warning sounds, etc.)

P.S. Answer obtained from other site not particularly for this problem; however upon trying it out, it worked. Hope it helps you too.

---

