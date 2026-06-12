---
title: "PCManFM-Qt How to interpret icons?"
date: 2019-06-21
forum: New to Ubuntu
---

### Post by GhX6GZMB on 2019-06-21
Newbie with a successfully installed 19.04 running fast and perfectly.

Using PCManFM, I'm wondering how to interpret the icons.

Folder: blue with tab, no problem
Program: grey with tab and two blue squares, no problem
???: grey with tab and blue orange in the middle?
???: black with #! and a folded corner?
???: black gear wheel?

And what does the white arrow in a white circle on the icons mean?

I've searched the web, but apparently my search terms were off target.

Thanks.

---

### Post by TheFu on 2019-06-21
I haven't a clue, but perhaps there is a relationship to the icons and the file permissions, ownership, group and ACLs?

```
ls -al {files or directories}
``` could be helpful.

Also, Unix systems have a command, **file**, which tries to figure out what a file might contain.
```
$ file /etc/hosts
/etc/hosts: ASCII text
```
So, the icon could change based on the result of that command on each file/directory.
Perhaps a gear is a config file?
Perhaps the #! is a script file?

I can't see the other things you wrote from the Adv Editor, so I can't guess about the others. Sorry.

---

### Post by Dennis N on 2019-06-21
Icon appearance will vary by icon theme. You can browse the available icons for your theme in /usr/share/icons/ - look inside the folders of your icon theme. In there, their function is labeled.

---

### Post by guiverc on 2019-06-22
A look at my own $HOME (user folder) in pcmanfm-qt shows a shell script of mine having a #! top left in the grey page icon with folded corner.
I had to go to /bin to find a black-gear-icon (/bin/busybox) which is a ELF executable.

I didn't find your other one ([COLOR=#000000]*grey with tab and blue orange in the middle*) but I'd follow @TheFu's advice and `ls` or `file` to query the system on what type file it is) though Dennis' alternative is another option (fyi: LXQt's themes can be found in [/COLOR]/usr/share/lxqt/themes/)

---

### Post by GhX6GZMB on 2019-06-22
Thanks, I'll try what you suggested. This is an out-of-the-box install of Lubuntu 19.04, so I thought there might be a "standard" for the icons.
And that the arrow on certain icons has a meaning.

---

