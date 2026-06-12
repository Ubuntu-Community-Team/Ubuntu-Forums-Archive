---
title: "Problems with boot"
date: 2016-05-28
forum: New to Ubuntu
---

### Post by tallyson2 on 2016-05-28
Hi guys,

I'm new in Linux World (it's a importind thing I supposed)

This is my problem: In a wonderful night, I was working in my projects (PHP Projects) and as always, I saved my files in "/home/user/Projects/Project1".
I use PhpStorm as my IDE (uhuu!) and, so I can edit my files I had to set the "Project1" folder to 777 privileges using chmod. Until here everything is perfect.

When I restart the machine, I receive the message error like this: "Your home folder is set 777 privileges, fix this you looser...". Fine! Search in google, found it something like this: "Set your home to 455 privileges..." so... bad idea... The system doesn't work anymore, the recovery mode so to, and the Emergency Terminal (ctrl+shift+f1), take a guess: "DOESN'T WORK TO".... I try everything... Pliz someone, rescue me...

Thanks guys!

PS.: Recovery mode doesn't work

---

### Post by wildmanne39 on 2016-05-28
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by ajgreeny on 2016-05-28
Assuming everything in your home really does belong to you at the moment you should be able to run ```
chmod -R /home/*username* 755
```from recovery mode.  Change *username* to your own user of course.

You will need to run command ```
mount -o rw,remount /
```first to make the filesystem read/write as recovery mode makes it read only by default, which is probably why you say recovery mode does not work.

I am not sure where you saw the info to change your /home to 455 (a link please) but that would be a disaster as it means that everything, including all folders, are read only; folders **must** be executable to work which is why you can no longer login as your user.

---

