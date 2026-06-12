---
title: "How do you view an mms file"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by bahsarie on 2008-05-25
Hi, i Just installed 8.04 on a desktop and I am trying to play a mms file but it does not seem to work any ideas? I downloaded the codecs to play it in gstreamer. It asks me what program to open it with but I can not find gstreamer to open it with. any help would be great thanks.

---

### Post by sayakb on 2008-05-25
Assuming it's a 3gp or an avi file, play it in VLC player:
```
sudo apt-get install vlc
```

---

### Post by bahsarie on 2008-05-25
i already installed vlc, i added an icon to the desktop and tried using that to open the file but did not work.

---

### Post by sayakb on 2008-05-25
Copy the file to your desktop. Lets assume its called video00.3gp
Then open a terminal and:
```
vlc ~/Desktop/video00.3gp
```
And post the output here.

---

### Post by bahsarie on 2008-05-25
is there anything simpler? because it is for my dad and he is not tech savy at all.

---

### Post by sayakb on 2008-05-25
Did I recommend anything yet ?? ;) ;)
Did the above command play the video?

---

### Post by bahsarie on 2008-05-25
it does not give me the option to save the file. just an open with option and i can not find vlc as an option yes i installed it. and yes i downloaded the proper codecs.

---

