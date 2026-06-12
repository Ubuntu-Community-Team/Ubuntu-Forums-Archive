---
title: "Can't launch application from desktop"
date: 2010-05-01
forum: Programming Talk
---

### Post by Tottish on 2010-05-01
I was told to post here instead of in the beginner talk. Here is my post:
*****
Hello! I'm running Karmic Koala and have problems launching a certain app from anywhere except it's original location.

So I've made this application called "Visual" in C++/Qt and it runs fine if I just locate it in it's folder and double-click it.
BUT I can't seem to make a working link or a launcher to/for it.
If I create a link it works fine until I place the link on my desktop then the program immediately crashes when launched. Same thing when using a launcher.
I also tried putting it among the "autostart"-applications with the same result, it runs for maybe 1/10th of a second then crashes.

I really want this app on autostart and I'm sure there is an easy solution so could someone please light the way for a Linux noob?

Thanks!
/Tottish

---

### Post by Tottish on 2010-05-05
Could someone please help me on tis one or just steer steer a n00b in the right direction?

I mean, this can't be very hard to do? Worst case could be like a macro that runs the mouse and double-clicks on a folder-link on the desktop and then on an icon in that folder.
Or like a program that launches this app of mine in it's right location...

Thanks for listening!
/Tottish

---

### Post by Milliways on 2010-05-05
> **Tottish said:**
> I was told to post here instead of in the beginner talk. Here is my post:
*****
Hello! I'm running Karmic Koala and have problems launching a certain app from anywhere except it's original location.

So I've made this application called "Visual" in C++/Qt and it runs fine if I just locate it in it's folder and double-click it.
BUT I can't seem to make a working link or a launcher to/for it.
If I create a link it works fine until I place the link on my desktop then the program immediately crashes when launched. Same thing when using a launcher.
I also tried putting it among the "autostart"-applications with the same result, it runs for maybe 1/10th of a second then crashes.

I really want this app on autostart and I'm sure there is an easy solution so could someone please light the way for a Linux noob?

Thanks!
/Tottish

If you want help, you need to provide more information.
You don't even specify which folder it is in.

If you have made an executable which works, you should be able to execute it from anywhere, provided the permissions are correct, and it is not dependent on the path.

If you really want to run an app you should install in a directory on the path, usually /usr/local/bin

---

### Post by Tottish on 2010-05-06
Thank you for your response!
I'm sorry if I don't give the information you need. I'm not sure what's important but here are the answers to your comments:

"You don't even specify which folder it is in."
It's a few folders into the tree from my home-folder. Is the full path necessary for you to help me? I don't have access to the computer right now so that will have to wait.

"If you have made an executable which works, you should be able to execute it from anywhere, provided the permissions are correct, and it is not dependent on the path."
OK, I'm not sure what to make of that, all I can tell you that it works perfectly when I double-click the icon with a blue square standing on edge in the folder for my project, while it crashes if I make a link to the same file and place the link on my desktop or any other folder. The crash also occurs if I execute the program from autostart and the same if I use a launcher. Although the program only runs for a few tenths of a second there is no doubt that it is the same program that opens.

"If you really want to run an app you should install in a directory on the path, usually /usr/local/bin"
OK, that's useful. As I said I've created this program/project using Qt Creator so I haven't really installed it at all. Maybe I could copy the folder to the path you mention or move the project there and rebuild it right there?

If I'm not telling you the right answers, then please just ask.

Have a wonderful day, people!
/Tottish

---

### Post by Zugzwang on 2010-05-06
Ok, let's try the following.

Try to start your application from a different path in the terminal. For example, assuming that your application has the executable "/home/tittish/coolapp/visual", try to execute the following lines in the terminal:

```

cd /tmp
/home/tittish/coolapp/visual

```

This way, you can check if your application is dependent of being started from a particular directory.

---

### Post by Tottish on 2010-05-06
Thanks a lot Zugzwang! It'll be a couple of days before I get access to the computer in question again but I'll try it out as soon as I can and post back!
/Tottish

---

