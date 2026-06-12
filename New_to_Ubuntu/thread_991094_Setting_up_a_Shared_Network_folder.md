---
title: "Setting up a Shared Network folder"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by mudrain911 on 2008-11-23
I have a feeling this is something really easy to do, but before I actually try it I figured I would ask and make sure. Is there a certain way you would set up a shared network folder to go between a windows (xp) machine and a Xubuntu (intrepid) machine? If there is a special way to do this can someone help me out? Thanks alot!

---

### Post by NESFreak on 2008-11-23
rightclick on a directory you'd like to share. There should be something like shareoptions. follow the instructions.
----
lol srry i forgot you're using xubuntu. Shouldn't be to different although i wouldn't know for sure, it has been a while since all my pc's run ubuntu fine.

---

### Post by aktiwers on 2008-11-23
Right click on the folder and pick "Properties".
Then go to the "Share" tab and enable "share this folder". It will then proberbly prompt you to install the needed software. Samba is the name of the software, and when you are done you should find your Windows share under Places => Networks=> Windows Share

---

### Post by mudrain911 on 2008-11-23
ummm...Thunar doesn't have that, or at least I cant find it. (I'm trying to do this on the Xubuntu computer)

---

### Post by mudrain911 on 2008-11-23
Does this Samba program work the same in Xfce? If it does could I just install that and set up the shared folders?

---

### Post by aktiwers on 2008-11-23
Im not that experienced with XFCE, but Samba works with it.
So I guess the answer to your question would be yes :)

Else you can install nautilus and do like I said before.
sudo apt-get install nautilus
and run it from terminal:
nautilus

But I guess there is a "better" way to do this from XFCE. 

But SAMBA is what you are looking for.

---

### Post by mudrain911 on 2008-11-23
ok... to be honest I feel completely stupid now. I went to Applications > System >, and right there on the menu it says 'shared folders'. I'm almost embarrassed lol. Thanks for all your help, I just got it to work (and btw it did need Samba). Thanks again.

---

