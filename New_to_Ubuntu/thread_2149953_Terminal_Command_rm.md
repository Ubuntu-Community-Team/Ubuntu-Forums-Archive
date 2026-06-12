---
title: "Terminal: Command rm"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by FZag on 2013-05-30
Hello everyone,

This is my first post at the Ubuntu Forums. I am new to the OS and also new to Linux, so I am trying to learn everything from the basics and at the same time enjoying what Ubuntu's high-end functionalities have to offer.

I've spent the last couple of days studying the shell commands and how to use them. So today I was testing a few operations and I found out that after deleting a text file named "**Test**" using the command "***rm *Test**", I would still see a file named "**Test~**" after using the listing ("***ls***") command. Why does that happen? Shouldn't the first operation have deleted the file completely withouth leaving any trace of it? I was able to delete the "**Test~**" file afterwards, but that felt like I had to do the same thing twice.

Thank you for your attention, guys!
FZag

---

### Post by sudodus on 2013-05-30
Welcome to the Ubuntu Forums :-)

The files ending with tilde '~' are backup files that are created automatically by some programs. It is possible to change the settings or 'preferences' of those programs, so that they do not create such backup files. Did you create**[FONT=courier new] Test~[/FONT]** with ***gedit***?

---

### Post by FZag on 2013-05-30
Hello sudodus! Thank you for the welcoming message!

I understand. Yes, I did create "**Test**" with *gedit*! So I believe it is a backup created by that program, right? I will try to look into the setting to change that then.

Thanks a lot for your reply! ;)

Best,
FZag

---

### Post by sudodus on 2013-05-30
Have a look at this link and links that it is linking to :-)[URL="https://help.ubuntu.com/community/CommandLineResources"]

https://help.ubuntu.com/community/CommandLineResources[/URL]

---

### Post by ShadowVegan on 2013-05-30
The files 'test' and test~' are separate files so deleting one--through any method--will not delete the other. Test~ is a backup file. Backup files are normally hidden files. In a file browser, you can use ctrl+H to enable/disable viewing hidden files.

Gedit by default creates backup files before saving. I don't have gedit currently installed (I use Leafpad) so I don't know the exact steps, but it's something like edit->preferences where you can disable gedit creating backup files.

For more information on rm, see [here](http://manpages.ubuntu.com/manpages/raring/en/man1/rm.1.html).

---

### Post by Impavidus on 2013-05-31
In gedit, click "edit" > "preferences", select tab "editor", uncheck "create backup before saving".

---

