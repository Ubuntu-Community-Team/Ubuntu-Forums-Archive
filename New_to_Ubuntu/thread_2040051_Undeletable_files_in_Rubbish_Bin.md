---
title: "Undeletable files in Rubbish Bin"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by jezzagreen on 2012-08-10
Hi,

Relatively unsophisticated user of both Ubuntu and Forums here, so please forgive me if I've posted this wrongly!

I've got a lot of items in my Rubbish Bin that I didn't put there (most of them are empty folders). If I try to empty the rubbish bin it says 'preparing' for a long time in a 'file operations' window, but nothing happens. If I try to delete individual items or folders individually it just fails. Have just upgraded to 12.04 in the hope that this would make it go away, but it didn't.

Suggestions gratefully received, but please give full details - not very comfortable with Terminal!

Thanks!

---

### Post by albandy on 2012-08-10
In fact, with the terminal, these operations are easier.

To completely delete your Trash folder:

Option 1. By command line:

sudo rm -rf $HOME/.local/share/Trash

Option 2. By Graphical Interface (see the video):

[http://www.youtube.com/watch?v=c2aENdVahOU](http://www.youtube.com/watch?v=c2aENdVahOU)

---

### Post by NikTh on 2012-08-10
Hi , 
it would be helpful if you say with what message fails to delete individual files ? 

and post the results of this command in terminal (ctrl+alt+t)
```
ls /home/**username**/.local/share/Trash/files/
```
replace **username** with your actual username. 
Thanks

---

