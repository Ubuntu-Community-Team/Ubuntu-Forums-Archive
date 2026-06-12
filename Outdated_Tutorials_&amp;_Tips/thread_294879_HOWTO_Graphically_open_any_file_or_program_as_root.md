---
title: "HOWTO: Graphically open any file or program as root"
date: 2006-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by zds on 2006-11-07
Ubuntu uses gksudo to launch graphical programs as root. 

When you select a menu item that invokes gksudo (i.e., a system utility like Synaptic), Ubuntu will prompt you for the password and then cache this password for a short period of time. 

We can use this to our advantage to open programs or files as root via a graphical menu item.

First, open the Menu Editor (in Xubuntu it's: Applications - Settings - Menu Editor). Create a new menu entry with an appropriate name. For the command simply preface your desired action with *gksudo*.

That's it!

Here's an example that creates a link to run the file manager *thunar* as root in Xubuntu.

**Note:** I chose this example for a reson. A root file manager allows me to edit any configuration file and run any binary from within the graphical interface without invoking the terminal. I just navigate to what I want and go.

**Note:** Different versions of Ubuntu-desktop have different file managers. See in step 2 where the existing file manager item's command is displayed (*thunar* - directly above the *Add menu entry* dialog box)? Substitute your different command as needed.

First I open menu editor:
[IMG]http://img401.imageshack.us/img401/357/1ul7.jpg[/IMG]

Then I create a new menu item, name it "Root File Manager," and enter the command "gksudo thunar":
[IMG]http://img401.imageshack.us/img401/2105/3ab7.jpg[/IMG]

I adjust the new item's position in the menu to where I want it and hit save:
[IMG]http://img172.imageshack.us/img172/6013/4qh1.jpg[/IMG]

And I'm done!
[IMG]http://img292.imageshack.us/img292/5195/5rh1.jpg[/IMG]

---

