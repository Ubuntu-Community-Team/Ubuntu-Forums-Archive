---
title: "(NOOB) Changing default handler for file type in Ubuntu"
date: 2010-09-27
forum: Programming Talk
---

### Post by Ripfox on 2010-09-27
First, I don't really know how to program anything, so be forgiving!

I want to understand how a newly installed program takes over file handling tasks. Here is my example: When you click on an .exe file, archive manager opens up. Then, if you install Wine, it will take over "handling" an exe file. How is this accomplished? 

Thanks so much!

---

### Post by Dex73 on 2010-09-27
The starting application goes by extension type e.g.   .png  .exe  .doc  ....and so on. It changes when you write click on a file choose Open with Other Application then select the one you want. The application you pick is the new default. In 10.04, I had to right click on the file and then choose the application I wanted to make it different. This has to be done for each file type in each method, but only once per file type.

---

### Post by Ripfox on 2010-09-27
Thanks for the answer, but I posted this in the coding talk section b/c I am going to attempt to write a program. I need an explanation about how a program actually takes over handling a certain file extension after it is installed...i.e. Wine behavior. I didn't have to "tell" Wine to take over as a default handler for an .exe file. There is something in the code which makes it behave this way.

Thank you for your patience

---

### Post by Ripfox on 2010-09-28
Bump

---

### Post by ssam on 2010-09-28
you can declare in your ,desktop file that your program can read a file type.

[http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-registering.html.en](http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-registering.html.en)

---

### Post by SledgeHammer_999 on 2010-09-28
Also take a look into the "install scripts" of the wine deb file. These scripts do the appropriate thing, not wine itself. 
I think GNOME and KDE handle *"the default application for each type"* in a different way. So your best bet is to also look into the GNOME tutorials.

Furthermore, I would like to learn it myself so if you find your answer please share it with us.

---

### Post by Ripfox on 2010-09-28
I think looking through the Wine install script may be what I need. I want to create a .deb file that when installed, takes over handling a certain file type in Ubuntu Linux.

---

### Post by Ripfox on 2010-09-28
> **ssam said:**
> you can declare in your ,desktop file that your program can read a file type.

[http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-registering.html.en](http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-registering.html.en)

This would not help as the user would have to change the file manually if I understand correctly. I want the program to "take over" the file type when installed.

---

### Post by Tony Flury on 2010-09-28
> **Ripfox said:**
> This would not help as the user would have to change the file manually if I understand correctly. I want the program to "take over" the file type when installed.

Basically your install script will change the defaults.list file as part of the install.

Just about anything that a user can do "manually" i.e. from the command line or from an editor, an install script can do automatically as it runs - especially if it is something simple like adding a new line to a file.

---

