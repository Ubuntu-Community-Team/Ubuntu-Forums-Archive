---
title: "How to recover an unreadable content folder from a hard drive ubuntu 14.04"
date: 2017-04-10
forum: New to Ubuntu
---

### Post by andrew2622 on 2017-04-10
hello,

I am new to this forum, and could you please help me to fix the hard drive.

I have ubuntu 14.04 installed and is running properly and a few days ago I decided to delete some
files that I considered useless.

I started with the "Home" folder that contains  the "Desktop", "Documents", "Downloads" and some other folders that are created by 
default by the system during the setup like the "Templates" folder.

So I deleted some "unnecessary" folders like "Templates" and others and then I renamed the "Downloads" and "Documents"folders.

Then I tried to open the other "Downloads" folder that appears on the left hand side folder bar under the "Home" and "Documents" folders.

I need to specify that this "Downloads" folder - I tried to open and was listed under the "Home" folder on the folder bar - is different than the other "Downloads"
folder that is located inside the "Home" folder and it has been renamed.


So when I tried to open this "Downloads" folder, a pop up window appeared with this message:"the folder contains unreadable content".

Then I restarted the computer and I noticed that this " Downloads" folder was gone from the folder bar and the free space of the computer
has been increased by the space occupied by the "Downloads" folder. Ubuntu seemed to work fine.

i immediately restored the initial names for the "Documents" and "Downloads" folders, then I started the computer; but the folder is still missing

I took the hard drive out of the computer in order to preserve what iis still left on it and to avoid over writing of the existing data.

I've tried to understand what has happened, and I got to these options:

 - a glitch in software deleted the folder 
 - the specific information required to read the folder's content is missing - it was stored in the folders that I had deleted
 - the renaming process changed some parameters required to identify the pathway to the folders
 - a hard drive physical problem

Could you please help me to recover the lost folder.

Thank you very much ,

Andrew

---

### Post by vasa1 on 2017-04-10
This is probably not a hardware issue. So moving to "New to Ubuntu".

---

### Post by ajgreeny on 2017-04-10
If you have the left hand pane of thunar set to show Bookmarks (Places) and this is where you are experiencing the problem of missing folders, or in reality probably, changed folder pathways, you will need to edit the bookmarks file in ~/.config/gtk-3.0/bookmarks to show this change.  The entries in the left hand Bookmarks pane are not the actual folders but simply shortcuts to them.

It is also possible that I have completely missed the point of your post, and not understood the problem at all; if so enlighten me with a bit more detail of what is going wrong.

EDIT:
Sorry; I though I read originally that you were using Xubuntu with thunar, but I suspect the answer I gave is the same for nautilus (files) in Ubuntu, so have a look at that file in .config/gtk-3.0/bookmarks.

---

