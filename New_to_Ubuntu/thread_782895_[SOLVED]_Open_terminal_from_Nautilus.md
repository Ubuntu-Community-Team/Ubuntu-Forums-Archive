---
title: "[SOLVED] Open terminal from Nautilus?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-05-05
Is there a way to open a terminal session from Nautilus with the current directory being viewed in Nautilus as the CWD of of the terminal session?

---

### Post by Suzan on 2008-05-05
Yes, just install the package

nautilus-open-terminal

Not sure if a restart is required after installation or not.

---

### Post by Liv3dN8as on 2008-05-05
I'm curious what the advantage of this would be? 
I know you can open Nautilus and start in any directory you specify with the command:
sudo nautilus /directory

---

### Post by Suzan on 2008-05-05
It's simply because you don't have to type in the directory path.

If you work more "graphical" like me, search files in Nautilus it is a nice feature.

---

### Post by graben3 on 2008-05-05
[http://www.gnome-look.org/content/show.php/Terminal+Here?content=73250](http://www.gnome-look.org/content/show.php/Terminal+Here?content=73250)

Download this nautilus script and put in your home directory at :
/home/graben/.gnome2/nautilus-scripts

replace graben by your current user name.

Then when you browse directories, just right click in nautilus and you'll see a menu item named Scripts and choose Open Terminal here

---

### Post by Liv3dN8as on 2008-05-05
makes sense.

---

### Post by H.Callahan on 2008-05-05
> **Suzan said:**
> Yes, just install the package

nautilus-open-terminal

Not sure if a restart is required after installation or not.

Great!  Thanks!

> **Liv3dN8as said:**
> I'm curious what the advantage of this would be? 
I know you can open Nautilus and start in any directory you specify with the command:
sudo nautilus /directory
That's not what I want.  Here is the scenerio:  Suppose I am deep in a directory structure and see a .rar file that I want to uncompress.  I have 7-Zip installed which is a CLI.  If I open a terminal session, it puts me into my /home/*username* directory.  Then I have to manually navigate to where ever I was when I saw the .rar file that I want to uncompress.

What I would like to do is have an option in Nautilus to open a terminal session with whatever subdirectory I am looking at in Nautilus to automatically be the working directory of the terminal session.

---

### Post by Liv3dN8as on 2008-05-05
that would be nice. will have to get that script too.

---

### Post by H.Callahan on 2008-05-05
> **Suzan said:**
> Yes, just install the package

nautilus-open-terminal

Not sure if a restart is required after installation or not.
Ok, I am an idiot.  I installed the package, but I can not find where the option to open the terminal is.

---

### Post by H.Callahan on 2008-05-05
> **graben3 said:**
> [http://www.gnome-look.org/content/show.php/Terminal+Here?content=73250](http://www.gnome-look.org/content/show.php/Terminal+Here?content=73250)

Download this nautilus script and put in your home directory at :
/home/graben/.gnome2/nautilus-scripts

replace graben by your current user name.

Then when you browse directories, just right click in nautilus and you'll see a menu item named Scripts and choose Open Terminal here

...and the same problem with this one.  Where do you invoke it from.  Right clicking in a blank area does not bring anything that says "script" or "open terminal".

---

### Post by Monicker on 2008-05-05
Just right click on a folder from the file browser.  Works fine when I try it.

---

### Post by Liv3dN8as on 2008-05-05
I just installed the script. Very nice. I like it.

---

### Post by noynac on 2008-05-05
> **H.Callahan said:**
> Is there a way to open a terminal session from Nautilus with the current directory being viewed in Nautilus as the CWD of of the terminal session?

Another option to consider is Nautilus Actions, which is a Nautilus extension. It's in the repo's, and the following page references various Nautilus Actions configurations including:

* Open in terminal

* Open in root terminal

* Open terminal on files

* Open terminal on folders

[http://www.grumz.net/index.php?q=node/8](http://www.grumz.net/index.php?q=node/8)

Once installed, all Nautilus Actions are accessed by right-clicking on a folder or file/files from within Nautilus. 

BTW, I'm not sure what CWD refers to, so Nautilus Actions may not be able to do this.

---

### Post by sayakb on 2008-05-05
> **H.Callahan said:**
> ...and the same problem with this one.  Where do you invoke it from.  Right clicking in a blank area does not bring anything that says "script" or "open terminal".
Placing the script in the ~/.gnome2/nautilus-scripts folder should create a Scripts sub-menu in the nautilus context menus.

---

### Post by graben3 on 2008-05-05
> **H.Callahan said:**
> ...and the same problem with this one.  Where do you invoke it from.  Right clicking in a blank area does not bring anything that says "script" or "open terminal".

This works for me... did you reboot... normally it works as soon as you put the script file in the directory I said... I used it with ubuntu 7.10 and 8.04 and it works.

You must have done something wrong...

---

### Post by DirtDawg on 2008-05-05
> **H.Callahan said:**
> Ok, I am an idiot.  I installed the package, but I can not find where the option to open the terminal is.

Look in Nautilus's File menu. File>Open_In_Terminal. This is a must have feature for me.

---

### Post by Monicker on 2008-05-05
> **graben3 said:**
> This works for me... did you reboot... normally it works as soon as you put the script file in the directory I said... I used it with ubuntu 7.10 and 8.04 and it works.

You must have done something wrong...

Now that I think about it, I had to log out and log back in after installing nautilus-open-terminal.

There should be no need to reboot.

---

### Post by linfidel on 2008-05-05
> **H.Callahan said:**
> ...and the same problem with this one.  Where do you invoke it from.  Right clicking in a blank area does not bring anything that says "script" or "open terminal".I seem to remember that you have to click on a folder on a certain side if you have a split window, but I forget exactly where - seems like it was the right-side only, not the tree.  But it could be the opposite.

I'm at work now, not on a linux system. :(

---

### Post by Oldsoldier2003 on 2008-05-05
> **Monicker said:**
> Now that I think about it, I had to log out and log back in after installing nautilus-open-terminal.

There should be no need to reboot.

no need to logout either
```
killall nautilus
``` will kill allopen nautilus windows and restart nautilus, the newly installed extensions will now work.

---

### Post by H.Callahan on 2008-05-05
Ok, rebooting did it for the nautilus-open-terminal.  I now find "Open Terminal" both under the File menu and also on the right-click context menu.

I still don't see a "Scripts" option anywhere...  But my problem is solved.  Thanks all!

Harry

---

