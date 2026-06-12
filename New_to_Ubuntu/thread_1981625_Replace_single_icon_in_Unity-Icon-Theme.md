---
title: "Replace single icon in Unity-Icon-Theme"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by devrat43 on 2012-05-17
I use the **Unity-Icon-Theme** but the icon for increasing/decreasing the sound is really bad. I like the simple black and white one in the default **Gnome** icon theme. 

Is there a way I can change the Volume Increase/Decrease icon in Unity-Icon-Theme with the one in the **Gnome** icon theme?

We have four files in the following address :
[B]/usr/share/icons/gnome/scalable/status
[/B]
Namely,
1.audio-volume-high-symbolic.svg
2.audio-volume-med-symbolic.svg
3.audio-volume-low-symbolic.svg
4.audio-volume-muted-symbolic.svg

I wish to use these in the Unity-Icon-Theme.

---

### Post by devrat43 on 2012-05-17
Solved it. :D
Make a folder in the "Unity-Icon-Theme" and put the desired files there. Edit the index.theme file and add the directory and a few more lines to it.

---

