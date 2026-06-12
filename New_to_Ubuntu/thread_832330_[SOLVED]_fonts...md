---
title: "[SOLVED] fonts.."
date: 2008-06-17
forum: New to Ubuntu
---

### Post by bob_hilton on 2008-06-17
I've just installed ubuntu and it's the first linux distro i've tried.. meaning i'm used to windows!:-P

I want to import all my old fonts from windows which are in .ttf format. is this possible?

i also read somwhere that linux file extentions need to be in lowercase. if this is true is there an easy (read: near idiot-proof) way to convert thoses i have with uppercase extentions?

thanks in advance guys:D

---

### Post by markekeller on 2008-06-17
Ubuntu can handle the TrueType (ttf) format, so you can just copy your fonts from Windows!  Fonts in Linux are stored under the folder /usr/share/fonts, with truetype ones in the subfolder called 'truetype'.  Or, easier yet, you can install the Windows fonts from the Ubuntu repositories.  Just run

> sudo apt-get install msttcorefonts

in a terminal, and all the default Windows fonts will be installed.  Any other fonts that you got with software you installed, though, will still need to be copied manually.

Also, Linux is case-sensitive (meaning that file.txt and File.TXT are two different files), but file extensions don't usually matter.  Linux does magic-number detection, meaning that it looks at the contents of a file to see what sort of file it is, not by looking at its extension.  So you probably won't have to rename all your fonts.  If you still want to, though, let me know (it's kind of complex, so I'll not put it in this post unless you need it)

---

### Post by kerry_s on 2008-06-17
> **bob_hilton said:**
> I've just installed ubuntu and it's the first linux distro i've tried.. meaning i'm used to windows!:-P

I want to import all my old fonts from windows which are in .ttf format. is this possible?

i also read somwhere that linux file extentions need to be in lowercase. if this is true is there an easy (read: near idiot-proof) way to convert thoses i have with uppercase extentions?

thanks in advance guys:D

make a font folder:
mkdir ~/.fonts

drop all the fonts you want in there and your good to go.

---

### Post by billgoldberg on 2008-06-17
This might be a guide time to point to my new uber ubuntu post about customizing, which also addresses fonts.

[http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)

---

### Post by bob_hilton on 2008-06-17
> **markekeller said:**
> ..you probably won't have to rename all your fonts.  If you still want to, though, let me know (it's kind of complex, so I'll not put it in this post unless you need it)

In that case i'll avoid that method for the moment! 

I ran the command in the terminal and all went well but i've got a pretty bloated font folder i want to install too. when i try to darg and drop them into the fonts/truetype folder i get an error:

Error opening file '/usr/share/fonts/truetype/ACQUAINTANCE.TTF': Permission denied

how do i gain permission? 

(sorry but im a total noob! tonight i'm popping my linux cherry!)

---

### Post by billgoldberg on 2008-06-17
> **bob_hilton said:**
> In that case i'll avoid that method for the moment! 

I ran the command in the terminal and all went well but i've got a pretty bloated font folder i want to install too. when i try to darg and drop them into the fonts/truetype folder i get an error:

Error opening file '/usr/share/fonts/truetype/ACQUAINTANCE.TTF': Permission denied

how do i gain permission? 

(sorry but im a total noob! tonight i'm popping my linux cherry!)

press "alt+f2" and enter "gksudo nautilus" 

now you can drag and drop again from within the window that opened.

Because you are still learning, I'll explain some of the basics real quick.

You don't have administrator rights (in linux that is called "root") by default, because this poses a serious security risk.

So some actions aren't allowed. 

This is where the sudo (or gksudo) commands comes in. This command gives you temporary root access. 

Nautilus is the name of the file manager. So the command "gksudo nautilus" means

-> open the file manager as root (thus you can do everything you want).

(sudo is used only for terminal actions, gksudo is used when you use a gui).

---

### Post by bob_hilton on 2008-06-18
Thanks for the help guys!

---

