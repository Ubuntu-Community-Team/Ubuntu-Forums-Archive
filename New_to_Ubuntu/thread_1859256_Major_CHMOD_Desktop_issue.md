---
title: "Major CHMOD Desktop issue"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by NeoX12 on 2011-10-13
I got all these things on my desktop
Then how come when i do the following, i get nothing?


[IMG]http://k.minus.com/jLplsGOWEbgp1.png[/IMG]


I am the only admin on my pc.
No other users
If this helps.

[IMG]http://i.minus.com/iTOTZSAhXvHMH.png[/IMG]

Please, i need this fixed asap

After messing around a little bit, i got this:

[img]http://i.minus.com/ibAdXBUk6ijHv.png[/img]

Tell me what i have to do. Much appreciated

---

### Post by kolinab on 2011-10-13
Hi Neox12,

I'm not sure what you're trying to do. Are you trying to change file permissions? 

What do you mean by 'I get nothing' ?

There's some great guides on changing file permissions out there, so let us know if that's what's not working for you and we'll try to help you out.

Welcome to the forums!

Kolin

---

### Post by carranty on 2011-10-13
> **kolinab said:**
> 
What do you mean by 'I get nothing' ?


He means that when he lists files in the terminal (the ls -g command) no files are listed.  I'm not sure why this is though.

---

### Post by carranty on 2011-10-13
Ok, so to summarise the problem.  You have some files and folders in your Desktop directory (which we can clearly see from the screenshot) but when you try to list them in the terminal it doesn't detect them.  Then when you say you've messed around a bit you mean that you have created two new files (wtf.png and wtf2.png) in your desktop folder, and the terminal command does list those.  Is that correct?

Firstly, can you view the files in nautilus?  have you tried opening a file from the terminal, say

eog screenshot-1.png

How did you go about creating wtf and wtf2?

I'm honestly not sure what's going on.  The fact your Desktop folder is highlighted in green is likely something to do with it, I'm not sure what this means but I'm thinking it may mean the folder is owned by another user.  Try doing 

ls -l

in the Desktop folder, that will list the owner of the folder.

---

### Post by anewguy on 2011-10-14
Try the following and post back the outputs:

sudo ls -al ~/Desktop

*IF* I remember correctly that will show owner, all permissions, etc., for the Desktop folder itself, and I believe it's recursive through the files/subfolders in the Desktop folder.

Dave ;)

---

### Post by CaptainMark on 2011-10-14
@ carranty - the highlight shows the permissions of the directory, its coloured like this because the op has set the Desktop r,w&x permissions for everyone 

@ anewguy - the recursive flag for ls is -R 

this is a weird error ive never seen before, try listing the desktop with these flags -lahR

---

### Post by anewguy on 2011-10-16
Hum......I've *never* needed a recursive "flag" on a list - it has always walked the list.

Want the output of this so we can see ownership and permissions on the folder and anything subordinate to it.

Dave ;)

---

