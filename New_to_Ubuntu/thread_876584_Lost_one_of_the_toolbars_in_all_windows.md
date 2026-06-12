---
title: "Lost one of the toolbars in all windows"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by mity on 2008-07-31
i am not sure how to describe the problem, but i have lost the toolbar that has "file, help, etc" in all windows except for firefox ( see attached screenshot for visual) while tinkering with ubuntu. 

Can some one help me out with how to get it back? 

Thanks

---

### Post by deathvalleyjoker on 2008-07-31
this happened to me the other day after an update. someone gave me this code in the terminal:

"metacity --replace"

---

### Post by mity on 2008-08-01
that didnt work

---

### Post by mity on 2008-08-01
*bump*

---

### Post by silkstone on 2008-08-01
Try this...

Open the file browser (Nautilus) and click on Edit > Preferences.

In the Behaviour tab, see if 'Always open in browser windows' is selected. If it isn't, select it. If it is, unselect it, Close, then go back and select it again.

---

### Post by sdowney717 on 2008-08-01
create a new user and login to that new user and see if it is back.
system-admin-users and groups

I have done this if my configuration gets botched up so bad I cant fix it.
You can always transfer your files to this new account

---

### Post by mity on 2008-08-01
> **silkstone said:**
> Try this...

Open the file browser (Nautilus) and click on Edit > Preferences.

In the Behaviour tab, see if 'Always open in browser windows' is selected. If it isn't, select it. If it is, unselect it, Close, then go back and select it again.

the problem is that i dont have "Edit". it's part that is not there.

---

### Post by mity on 2008-08-01
Full Disclosure

This is what in was doing when I lost my buttons. 

[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/)

---

### Post by mity on 2008-08-02
bump

---

### Post by sdowney717 on 2008-08-02
If you cant get any help on this, then try another user login.
The user settings which control menu items, etc... are contained in the user space to which you log into. So when you log into another user, all the default settings should be like they were before. And the menu item should be back. It is a good idea to have another login anyway, since you may someday find yourself unable to login to your user space. It happened to me. And it was easier to fix from the gui than the command line.

Turning you desktop in a Mac, all those settings should also be contained in the user space. In fact, set up a test user space to try out things like this before you mess up your regular user space. Then if it works you can apply it. Linux is very surprising to windows users as to how easy to recover the system.

---

### Post by mity on 2008-08-02
I have setup a new account, but i do not know what i changed to cause the disappearance.

---

### Post by mity on 2008-08-04
No one?

---

### Post by gaspard.leon on 2008-08-04
I went to the site you linked to:

[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23/)

And I found that the step:
> **Change the traffic light window control to the left**

In the terminal, type

```
gconf-editor
```

This will bring up the gconf-editor window. Scroll down to App->Metacity->general. On the right, double click on the button_layout and change the content to ‘close,minimize,maximize:menu’ (without the quote). Click Ok and close the gconf-editor.

This part could screw up your menu.
You should experiment with the button_layout string, as this looks like it could cause your menu to disappear.


Also: This part is really nasty!!

> Next, we are going to install globalmenu so as to display the menubar for each application. In your terminal,

```
cd Mac_files
wget [http://gnome2-globalmenu.googlecode.com/files/gnome-globalmenu-0.4-svn964.tar.gz](http://gnome2-globalmenu.googlecode.com/files/gnome-globalmenu-0.4-svn964.tar.gz)
tar zxvf gnome-globalmenu-0.4-svn964.tar.gz
cd globalmenu
sudo dpkg -i *.deb
```

If you have any errors when installing the package, try

```
sudo dpkg -i –force-overwrite *.deb
```

If you are having some installation problems with the gnome-globalmenu-applet, try

```
sudo apt-get install -f
```

Once finished, right click on the top panel and select ‘Add to panel‘. Scroll down the list and add ‘Global Menu Applet‘.

Forcing deb installs can screw things up...
Best to find a supported version of this "globalmenu" package...

Hope this helps.

---

### Post by mity on 2008-08-05
thanks. 

I have already reversed the metacity layout. 

I am  gonna search for the "Globalmenu" next.

---

