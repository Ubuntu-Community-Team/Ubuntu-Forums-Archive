---
title: "simple xfce trash can / recycle bin"
date: 2006-08-27
forum: Outdated Tutorials &amp; Tips
---

### Post by pyros on 2006-08-27
The new Xfce desktop is rather cool. The latest releases include Thunar, a fast and light (and downright sexy) file manager. But Xfce and Thunar are not exactly perfect. One of the things I do miss is a trash or recycle bin. In the current thunar, when you delete a file, it is gone for good. Here's what I did to work around that.

Step 1:
Create a folder for your trash. This can be anywhere that you have write access. I put mine in my home folder. For the purposes of this tutorial I will call the home folder "mine". You should replace "mine" with the name of your own home folder. So, create a folder called ".trash" in "/home/mine/". Now you should have a "/home/mine/.trash" folder.

Step 2:
Now, in Thunar, click on Edit in the menu bar. Towards the end of the menu, click on "Configure custom actions". The custom actions window will probably have at least one entry, probably the "Open Terminal Here" action. Click on the plus sign on the right-hand side of the window. You will get the create action window. Under name, I typed "Trash". You may want to call it "move to trash" or something similar. For Command, type

```
mv %n /home/mine/.trash/%n
```

If you want an icon, click on the box that says "no icon" and choose an icon. Click on the "appearance Conditions" tab at top. You want an asterisk (*) for File pattern and go ahead and check all of the boxes in the window. Click on Ok in the Create Action window, and Close on the Custom Action window. Now when you right-click on a single file or folder, you should have an entry that says "Trash" and clicking on trash should move the file to "/home/mine/.trash"

Step 3:
Like I said, this will only work on a single file. So for moving multiple files I need another solution. What I did was add an entry to the shortcuts sidebar for the .trash folder. If you have thunar open to your home folder, click on "View" on the menubar. About half way down the menu there should be an entry that says "Show Hidden Files". Click on that and there should be several folders now with names that start with a period. Scroll down until you find the ".trash" folder. Right-click on the .trash folder and left-click on "Add Folder to Shortcuts" on the menu. Now you should be able to select multiple files and folders and drag them to the .trash folder on the sidebar. If you want, you can rename the shortcut on the sidebar. I renamed mine to "trash"

Step 4:
Ok, so now we can send files to the trash, but I've come to expect at least a little more functionality from my trash bin. So, the final step for my weak recycle bin replacement is to add a trash bin link to the task bar. Right-click on the bar and choose "Add New Item". In the "Add Items to the Panel" window, click on "Launcher" and click the "Add" button. Now you should be in the "Properties" window. For "Name" type "Trash", Choose an icon if you want, and for "Command" type

```
thunar /home/mine/.trash
```

This will open thunar to your .trash folder.

Now, Look for the plus icon on the bottom left hand side of the Properties window. Click on that an you should have "New item" in the list above. For "Name" type "Empty Trash", Choose an icon if you want, and for "Command" type

```
rm /home/mine/.trash/*
```

Now check the box that says "Run in terminal" and click on close. You should now have an icon for trash, and an arrow that opens a menu with "Empty Trash". This will delete the contents of the .trash folder, so use it with caution.

Well. that, sadly is it. It is far from a complete solution. Most notably, pressing delete on the keyboard will still permanently delete a file. But without figuring out how to remap the delete key, this is all I've got. Much Love.

---

### Post by sawjew on 2006-08-28
Thanks for this, it all works fine except adding the shortcut in thunar.  I do not get the option to add a shortcut on right click in thunar.  Are you using the standard Xubuntu release of Thunar?

EDIT: I just found out that I need to have the side pane in shortcut view to enable this menu option.  Now it works great, I just wish I could change the icon on the shortcut.  Well we only have to wait for Edgy and it will all be there anyway.

---

### Post by sawjew on 2006-08-28
Just a couple of minor improvements I picked up along the way.

First you need to name the trash folder /home/<username>/.Trash with a capital T.

Then you can use the command ```
del %F
``` for the move to trash command. 

Using this command files and directories can be moved to trash.

Then I found that the Empty Trash command didn't work.  It worked from the command line but not from the menu so I wrote a script which also enabled me to delete hidden files and folders.

first make a directory for the script.

```
mkdir ~/.bash-scripts

```

then create the script

```
mousepad ~/.bash-scripts/remove-from-trash

```

then paste this into it

```
#!/bin/bash
rm -rf /home/stephen/.Trash/* | rm -rf /home/stephen/.Trash/.*
```

then make it executable

```
chmod a+x ~/.bash-scripts/remove-from-trash

```

then for the Empty Trash command use 
```
/home/<username>/.bash-scripts/remove-from-trash
```

Doing it this way enables files and folders, hidden or not, to be moved to Trash and emptied from the Trash can.

---

### Post by pyros on 2006-08-28
> **sawjew said:**
> I just wish I could change the icon on the shortcut.
I just added a trashcan icon into my icon theme's emblems directory, then used that emblem for the trash folder. It doesn't change to show the state of the trash, but it's a nice visual cue.

---

### Post by pyros on 2006-08-28
> **sawjew said:**
> Then I found that the Empty Trash command didn't work.

I'm not sure why that didn't work for you, I must have left something out... but thank you for a far more complete solution. I take it the del %f command works because it is using the partialy implemented trash support in xfce?

---

### Post by sawjew on 2006-08-28
> **pyros said:**
> I'm not sure why that didn't work for you, I must have left something out... but thank you for a far more complete solution. I take it the del %f command works because it is using the partialy implemented trash support in xfce?

I picked that up from another thread and, yes, I think that is what it's doing.

I don't know why the remove from trash didn't work either.  I tried it from the terminal and then pasted it in and it wouldn't work.  But the script deletes directories and hidden files/folders as well.

It will do until the next release of Thunar reaches the repositories, I can't be bothered compiling it from source.

---

### Post by jis on 2006-09-06
I hope there will be an option not to use recycle bin for those who don't need it.

---

### Post by phranx on 2006-09-28
Hi there,
I added some improvements on the "del" script to avoid the un-deletion of files with same name. I put the "del" script into /usr/bin and then 
```
sudo chmod 755 /usr/bin/del
```
This is my "del" script
```

#! /bin/bash

newdir=$(date +%Y%m%d_%H%M%S_%N)
mkdir $newdir
mv "$@" $newdir
mv $newdir $HOME/.Trash

```

In this way, the script puts all the stuff you want to delete in the new directory and then moves the generated directory to the trash-bin.
I hope this can help :)

---

