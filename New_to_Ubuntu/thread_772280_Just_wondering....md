---
title: "Just wondering..."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by drsaamah on 2008-04-28
In an ongoing quest to better understand my operating system...
Under Gutsy the trash can use to be a hidden folder with the absolute path /home/$USERNAME/.Trash
Now, under Hardy the trash can has a path /home/$USERNAME/.local/share/Trash
So I guess its still kind of a hidden folder.
So, I have the following questions regarding totally useless knowledge:
(1) Why the change?  Benefits and/or disadvantages?
(2) Is the "share/" directory shared amongst all the users?  For example, if I moved something to the trash, could another user on my system go to the trash and see this?
Thanks in advance to anyone bored (and knowledgeable!) enough to answer these questions!!

---

### Post by Nano Geek on 2008-04-28
(1.)They might have moved the trash folder because of the new virtual file system. I don't really know though.

(2.) No, I'm sure other users can't see it without you setting it that way.

---

### Post by Hospadar on 2008-04-28
Nothing in your home folder is by default viewable by other users.  You'd have to manually give them access.

---

### Post by TerpInHotLanta on 2008-04-28
(1) Anyone's guess is as good as mine-- probably some guy said "hey let's try and collect more stuff under single directories" (they've been doing that for 15 years now-- such as moving user-installed programs to /usr/local about 10 years ago or so)

(2) You have total power over who can see what through the chmod command. I'm positive that your trash directories are blocked to other users by default.

---

### Post by jken146 on 2008-04-28
The answer to the first question is that they did it to conform with the freedesktop standards.  XFCE and others implemented trash this way before GNOME did.

Also, having a 'files' directory and an 'info' directory enables restoring deleted files to their original locations.

---

### Post by forrestcupp on 2008-04-28
> **jken146 said:**
> The answer to the first question is that they did it to conform with the freedesktop standards.  XFCE and others implemented trash this way before GNOME did.

Also, having a 'files' directory and an 'info' directory enables restoring deleted files to their original locations.

That's some good info.

Now if someone could tell me why they changed the name of the Restricted Drivers Manager to Hardware Drivers.  That messes up a lot of archived support on these forums.  Now we have to tell people a different way to do things.

---

### Post by Joeb454 on 2008-04-28
I think that's just because some people would wonder why their driver "has been restricted" which I think is totally understandable.

In my opinion calling it hardware drivers makes a little bit more sense :)

---

### Post by meindian523 on 2008-04-28
But it doesn't show that they are "restricted" in freedom,does it?I guess it should have still been restricted drivers,people should also know about the philosophy behind GNU/Linux.That's just my Rs. 0.25,BTW.

---

### Post by jken146 on 2008-04-28
Yeah, 'hardware drivers' isn't specific enough, although they have kept the warning in the app istelf.

---

