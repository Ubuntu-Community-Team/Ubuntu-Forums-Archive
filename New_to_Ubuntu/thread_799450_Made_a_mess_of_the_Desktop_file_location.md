---
title: "Made a mess of the Desktop file location"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by tropdoug on 2008-05-19
Okay, I was trying to be smart and putting all home files onto a separate partition, in the process, I deleted the original Desktop folder that was in /home/kim/Desktop all seemed to be okay until I realised that  when I tried to delete something (a launcher I had made) from the desktop, it talked about the file already being in the Garbage bin. I was Confused!

Then I though hmmm, opened the Garbage Bin, and there was the original Desktop folder with all the newly created launchers  sitting inside it. So I realised that this folder must have to remain from whence it came, and copied it back to its original location, and it wont stick it comes back to /home/kim/.Trash/ automatically. what a horror!!!

So I used a terminal and sudo to try to move it back, but the resulting folder did not have that little icon sitting on top of the folder. and a new launcher simply reappeared in .Trash again. 

Question, how can i restore the desktop to its rightful place?

---

### Post by N.N. on 2008-05-19
This problem has been discussed on the forums before, see [http://ubuntuforums.org/showthread.php?t=581498](http://ubuntuforums.org/showthread.php?t=581498). Haven't had the problem myself, so I'll just paraphrase the fix from that thread: [LIST=1]
[*]Open a terminal and use the following command to force the desktop folder to be moved back to your home directory: ```
sudo mv ~/.Trash/Desktop ~/
```
[*]Log out and then log in again.
[*]Ubuntu should now use your home directory, /home/kim/, as the desktop folder, which means that the contents of this directory should be displayed on the desktop. To remedy this enter the following command in a terminal: ```
sudo gedit ~/.config/user-dirs.dirs
``` and edit the XDG_DESKTOP_DIR entry so that it becomes XDG_DESKTOP_DIR="$HOME/Desktop".
[*]Finally, log out and then log in again to solve the problem.
[/LIST]
If nautilus crashes when you log in, go to "System" > "Administration" > "System Monitor" and stop nautilus from the processes tab. If it isn't running, open a terminal and type the following command to make it run: ```
nautilus
```, and then stop it. Finally, run nautilus from the terminal again, and the problem should be solved.

---

### Post by tropdoug on 2008-05-19
Man you saved my bacon! thanks a mill. 1 Question, I keep on trying to find threads that may answer the varied and many questions I come up with, but almost invariably when I try to do a search I get either nothing returned or a heap of threads that don't come close, is there some trick to finding what you are looking for?

Again many many thanks for the assistance.

---

### Post by N.N. on 2008-05-19
> **tropdoug said:**
> Man you saved my bacon! thanks a mill. 1 Question, I keep on trying to find threads that may answer the varied and many questions I come up with, but almost invariably when I try to do a search I get either nothing returned or a heap of threads that don't come close, is there some trick to finding what you are looking for?

Again many many thanks for the assistance.

You're welcome.

No trick can guarantee that you'll find what you're looking for. Sometimes, however, a google search can be more helpful than a regular forum search, as it will find forum posts as well as posts on blogs and so on. In general I find that it also discovers relevant forum posts more readily than the forum search engine. To find the solution for the problem you were facing, for instance, I searched for "Ubuntu restore desktop folder" on google (without the quotes). Using the same string with the forum search engine yields completely different results.

Anyway, don't be afraid to ask. The forums are here to help you solve problems and learn from the process. :)

---

