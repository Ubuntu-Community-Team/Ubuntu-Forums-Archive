---
title: "[SOLVED] icon delete under wine menu"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by a.subramanian on 2008-08-08
hi am very fresh user of ubuntu, some how i learned and solved allot problem in ubuntu, now i a need of help that i installed adobe reader 8 under wine, i delete all its folder in c:\Programfiles\adobe\, then for wine unistaller icon i use for regedit.exe, but in the main menu of ubuntu i can hide adobe reader icon but can't able delete on right click go delete option, can any one help me to delete the icon,
:([B]Thanks allot in advace
[/B]

---

### Post by lordhaworth on 2008-08-08
I too have found this with some icons in the wine menu so would be interested to hear the solution - * bump *

---

### Post by zipperback on 2008-08-08
I don't use Wine because I don't run Windows applications, but if you really need to have Adobe Acrobat Reader 8 for your system, you can install the Linux version of it.

It is available from the medibuntu repository.

Add the appropriate repository for your version of Ubuntu as indicated on the following web page.

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")


Once you have added the repository to your system, enter the following line of text into your terminal window.

```

sudo apt-get update && sudo apt-get install acroread

```

That will install Adobe Acrobat Reader 8 for you.

- zipperback
- :popcorn:

---

### Post by a.subramanian on 2008-08-11
Thank you zipperback for your reply,
I install the adobe reader 8 of .deb package.
but now i in need of delete the icon of adobe reader under wine menu,
have to find some solution for the case of deleting.

---

### Post by Mister.Vash on 2008-08-11
In the top left corner of your screen, you should see the ubuntu logo next to Applications
Right Click on the ubuntu logo and select "Edit Menus"

In the dialog that appears, scroll down to the wine menu section and uncheck the items that you want to remove

---

### Post by a.subramanian on 2008-08-11
i do uncheck its wright, but in i can right click it in and find delete button, by clicking delete i cant delete, thanks in advance

---

### Post by Rhubarb on 2008-08-11
In the attached screenshot, I right clicked on the 7-Zip folder (in the wine menu, in the menu editor), there you can select delete.

---

### Post by a.subramanian on 2008-08-11
for me not working particularly on that icon adobe reader only, all other icon can delete, fine working. pls help

---

### Post by a.subramanian on 2008-08-11
or me not working particularly on that icon adobe reader only, all other icon can delete, fine working. pls help

---

### Post by Rhubarb on 2008-08-11
Go to:
Places --> Home Folder
View --> Show Hidden Files (or press ctrl + h)
Go into .local/share/applications (~/.local/share/applications)
You will find the Adobe Reader 8 icon in there, just click on this icon and delete it.

---

### Post by a.subramanian on 2008-08-11
thank you so much Rhubard it worked for me fine,
thank's allot, i take you as my master.:)

---

### Post by lordhaworth on 2008-08-11
Thats Great Cheers

---

