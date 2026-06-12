---
title: "Move files from many subdirectories"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by Eniliad on 2012-02-27
I copied my Videos folder over from my iTunes Backups onto my Xubuntu partition. Trouble is, they're all in their own subdirectory. So basically, I have 60 or so subdirectories, each of which has one file, either .mp4 or .m4v. I'd like to rip them all out of their subdirectories and put them all in /Videos/ so I can sort them a bit better myself. However, I don't really want to go into 60+ folders, highlight the file, hit Ctrl-X, go up a folder, Ctrl-V, and repeat ad nauseum. I could also use the command "mv * .." but that still requires going into every directory.

Is there a simple command or bash script that would accomplish this easily?

---

### Post by yetiman64 on 2012-02-27
If the files all have the same extension (you have 2) I would use the search function in nautilus (check for Thunar if this matches) on the parent folder for the extension and when the results put all the files from the search in the one window, highlight them all and cut and paste to a holding single folder.

This works in nautilus (11.10), I'm not entirely sure it will work in Thunar, you will need to compare the method with your install.

Edit: this is more a graphical method to do the same, just noted the script reference in your post.

---

### Post by Eniliad on 2012-02-27
Hey there,

I appreciate the help. However, funny story - I was about to come back and edit my post to say I found a Terminal command to do exactly what I wanted. Had to run it for both extensions but it worked:

find -iname "*.mp4" -exec cp {} /home/eniliad/Videos/ \;
find -iname "*.m4v" -exec cp {} /home/eniliad/Videos/ \;

---

