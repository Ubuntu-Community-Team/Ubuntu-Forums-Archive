---
title: "Terminal.....again"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by rebeccabunz on 2011-09-09
I am having a couple of problems. I am trying to get the cube to work on my ubuntu 11.04. I have it working currently but.... to get it working I put "compiz --replace" into the teminal and it wokrs but the temrinal is still running it has stopped at....

~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done
Initializing grid options...done
Initializing imgjpeg options...done
Initializing wobbly options...done
Initializing session options...done
Initializing mousepoll options...done
Initializing opacify options...done
Initializing imgsvg options...done
Initializing animation options...done
Initializing cube options...done
Initializing resize options...done
Initializing move options...done
Initializing expo options...done
Initializing rotate options...done
Initializing ezoom options...done
Starting unity-window-decorator
Setting Update "move_window_match"
Setting Update "multioutput_mode"
Setting Update "top_color"
Setting Update "bottom_color"
Setting Update "skydome"
Setting Update "skydome_image"
Setting Update "skydome_gradient_start_color"
Setting Update "active_opacity"

and will not go further. So when I exit my screen goes back to how it was before I typed this because the terminal isnt finished.  The second thing is last night I was working on this and it worked and the terminal didn't do this but when I shut down my computer and log off it goes back to how it was before I got the cube to work. Anyone have an idea why the terminal isnt working or why my computer is not saving the changes I make?

---

### Post by nothingspecial on 2011-09-09
Press Alt-F2 and type compiz --replace in the box that pops up.

Or, type ```
compiz --replace &
``` in the terminal.

---

### Post by ubudog on 2011-09-09
Try this:
```
compiz --replace &
```

Then, you can press CTL>C, and close the terminal, and the changes will be applied until you shut down.  (the process will keep running in the background)

If you want to have the computer run this command automatically on startup, open a terminal and do the following:

```
gksu gedit /etc/rc.local
```

That will open the text editor.

Now, go to the end of where it says:
# By default this script does nothing.  

And press enter.  On the new line, type:
```
compiz --replace &
```

Now, when you restart, that command will be run automatically.

NOTE: I recommend installing compizconfig-settings-manager to manage Compiz.  That can be done by typing:
```
sudo apt-get -y install compizconfig-settings-manager
```
in the terminal.

Hope that information helps, let us know!  :-)

---

### Post by rebeccabunz on 2011-09-12
Thank-you both for your help but....nothing came up when I pressed alt-F2. So I tried the compix --replace & and it closed when I pressed ctrl c and went back to not having the cube. I already have compizcomfig manager and it wouldnt let me put in the code to get to the start-up command. It wouldnt let me copy and paste it or type, it was like frozen or something. Any other ideas???

---

### Post by ubudog on 2011-09-12
Did you make sure to put the "gksu" in front of the command?

---

### Post by nothingspecial on 2011-09-12
Try putting ```
compiz --replace
``` in your startup applications in the system settings menu (top right).

You put that in the "Command" box. It doesn't matter what ou put in the other 2, something like "Compiz" would be fine

---

### Post by nitstorm on 2011-09-12
//Seems nothingspecial already said it while I was typing, still going to let this be..


1.Click the Menu button(The button on the top-left of the screen). Type Startup Applications and click on the button that says "Startup Applications".

2. Now click Add.

3. In the name section, fill ZZ_compiz

4. In the command section type *compiz --replace&*
Click Add.

5. Now LogOut and LogIn again. 

That should positively solve your issue.

---

