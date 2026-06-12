---
title: "Workspaces -- How to start app in workspace"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by rccharles on 2013-04-27
Ubuntu 11.10

backgroun:  I am a user of Mac OS X.  It would be nice to group panels to applications.  Would be nice to have windows stay what size and position they were the last time you used the app.  

Question: I'm trying to figure out how to use workspace. I have figure out how to switch between workspaces.  I have not run across a good and easy explanation of how to start an app in a workspace.  How do I move a window from one workspace another?

rants: Would be nice if I could switch to a workspace then start an app from the launcher, but I read where that doesn't work.

         Would be nice if I could just click on a quaderant of the launcher icon to pick workspace.

I've done some searching for this, but what read was a little confusing with complaints like this included.

Robert
PS Thanks

---

### Post by Westonkd on 2013-04-27
> [COLOR=#000000]Question: I'm trying to figure out how to use workspace. I have figure out how to switch between workspaces. I have not run across a good and easy explanation of how to start an app in a workspace. How do I move a window from one workspace another?[/COLOR]

An easy way to move an application to a different workspace is by right clicking the title bar and then selecting "Move to workspace right" or whatever direction you want to move the window. You can also select which workspace you want to move the window to in the same menu. 
   
Another way to easily rearrange a large amount of windows in different workspaces in by clicking on the workspace switcher in the unity menu bar. Once you do you will be able to see all available workspaces. You can then can click and drag the title bars of the windows and move them to the workspace you want them in.

   I have found this system pretty easy to work with after I got used to it, hope this helps!

---

### Post by CatKiller on 2013-04-27
Also, Compiz has a Window Rules plugin that will let you specify where and on which workspace a window with specified properties will open. You can fiddle with Compiz' settings with compizconfig-settings-manager. Be aware that it's not the most new-user-friendly software ever written, but it does let you do neat things.

EDIT: I believe the default keybinding to move windows to another workspace is Ctrl-Alt-Shift-Left and -Right. That's certainly what mine's set as. Again, that's something you can fiddle with in CCSM.

---

### Post by deadflowr on 2013-04-27
First off, I would suggest you prepare your system for an upgrade soon.
11.10 will be hitting end of life on May 9.

Secondly, compizconfig-settings-manager is an awesome of powerful configuration program, use it cautiously.
It has been known to cause trouble for those not used to its fickleness.

Now, I personally like having various programs open up in certain workspaces.
Programs like thunderbird, firefox, gimp, libreoffice-writer, etc,etc.
I do this by opening ccsm and going to 'place windows'. In here I go to the second tab fixed windows placement.
Here I can set on what part of the screen any particular window will open in, and which viewport (workspace)
I want the program/window to open in.

For a basic tip, x and y coordinates start in the top left corner, so x1, y1 is the very peak of the corner. So the first usable space after the launcher/dock and the top panel would be something like x49, y25, otherwise the program would open underneath or on top of the panel or launcher. By default. I think the default launcher is 48 pixels and the panel is 24, not totally sure though.

There are many, many more interesting things you can do with ccsm, which you'll have to explore on your own..
But one I will get to is expanding the workspaces.
To do this, go to the ccsm general options(It's in the top section) and open, then go to desktop size) just change the x,y, but leave the number of desktops part alone, as I don't tjhink it does anything useful anyway. You can expand the number of workspaces ( i say infinite  but probably not; more like just a real lot (I once set it at 300, though I settled for 9.).

Tidbit for shortcuts > hold down the windows key should bring up a listing of the default key shortcuts.

Don''t know if any of this is helpful, or coherent, but hey...

---

### Post by rccharles on 2013-04-27
> **Westonkd said:**
> 
Another way to easily rearrange a large amount of windows in different workspaces in by clicking on the workspace switcher in the unity menu bar. Once you do you will be able to see all available workspaces. You can then can click and drag the title bars of the windows and move them to the workspace you want them in.
Close but no cigar for me. I tried dragging from the middle of the window before posting.

You say i click on the workspace icon, a boxed +,  I did.  I saw four quaderants. One had four little windows in it. I tried to drag the title line to another quarderant window.  Nothing happend. 

When I get more organized, I'll work with configuring the other methods.


Thanks.

Robert

---

### Post by Westonkd on 2013-04-28
> [COLOR=#000000]Close but no cigar for me. I tried dragging from the middle of the window before posting.[/COLOR]

Oops, it worked for me, but I am using 12.10

---

### Post by rccharles on 2013-04-28
I guess I'll have to consider upgrading.  I have an old machine.  It doesn't meet the specs for even 11.10, buts to run ok.

---

