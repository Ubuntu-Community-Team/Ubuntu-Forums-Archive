---
title: "Maintaining Deactivated Mouse Acceleration"
date: 2015-09-30
forum: New to Ubuntu
---

### Post by eddiefiggie on 2015-09-30
So, I found this source that creates the mouse behavior that I like, but cant seem to make this persistent between boots:

[http://www.techytalk.info/turn-mouse-acceleration-off-on-ubuntu-linux/comment-page-1/](http://www.techytalk.info/turn-mouse-acceleration-off-on-ubuntu-linux/comment-page-1/)

```
#!/bin/bash 
xinput set-prop 'Logitech USB Optical Mouse' 'Device Accel Profile' -1
xinput set-prop 'Logitech USB Optical Mouse' 'Device Accel Constant Deceleration' 2 
```

Based on the last segment of this guide which sates:

> The best approach is to save this script as something like mouseacc.sh inside ~/bin directory because this directory is inside your PATH environment variable and you can call scripts from this directory from anywhere in your file system. You can just hit Alt+F2 and enter mouseacc.sh to turn mouse acceleration off for selected device. Don't forget to set executable bit for your script because without this your script will refuse to do its work. This is how you can achieve this:

```
chmod +x ~/bin/mouseacc.sh

```

That's it my friends. Wish you all good gaming on your Linux PC.  

I get a little confused here.  A few questions:

1) Which /bin directory?  Not clear what the "~" means before the path.  ~/bin    I realize one is for all users, one is for the current user, etc...  How many /bin directories are there?

2) I can't move the file to the /bin directory.  Seems to be a rights issue.  How do I address this?

3) I assume, once in the /bin directory has this new .sh file, from the terminal I can just run the script assuming it has "x" rights.

4) Isn't there a way to always run this script on a boot up and auto-magically or by sorcery make these settings occur?    [COLOR=#ff0000]**<--- Hence the subject line!!**[/COLOR]

---

### Post by ajgreeny on 2015-09-30
The ~ (tilde) is a shortcut for the user's home, so ~/bin folder is in /home/<yourusername>/bin, which probably does not exist if you have not made it already.

That folder, if it is in existence, is one of the folders in the normal default pathway required for a shell script, or any other executable, to work if simply pointed to by its name, ie, in your case, mouseacc.sh.

The script would work fine if you copied it to /bin in the root filesystem (note: not ~/bin, just /bin), but that would not be needed for your user.

Run command ```
echo $PATH
``` in terminal to see the default folders in the system pathway for this activity.  If the bin folder was in your home at boot time it will be shown in the list that is shown in the output; if it was not present in your home it will not be listed, of course.

---

### Post by Geoffrey_Arndt on 2015-09-30
To build on AJ's post regarding moving the file to any directory or folder outside your home folder, you would need to run the "mv" command prefixed with sudo.

Here's a brief howto from "askUbuntu" . . . many more examples of the mv (which is move and also rename).   Also can use the copy command "cp" . . . but orig. file will still be in place (which in not a bad idea as it can be like a backup).

[http://askubuntu.com/questions/465877/how-to-move-one-file-to-a-folder-using-terminal](http://askubuntu.com/questions/465877/how-to-move-one-file-to-a-folder-using-terminal)

Note . . . there is also a graphical way to do this . . 

>   install gksu from Ubuntu Software Center
>   run "gksu nautilus" . . . then use the file manager to accomplish the copy or move (but be especially careful as you can hose your system) (note1, you will be prompted for your password) (note2, the file tree will not be displayed from the same vantage point).

All this security is one of the main reasons Linux is more impervious to malware than some other OS's . .

---

### Post by eddiefiggie on 2015-10-01
Worked like a charm!

You guys are great.

---

### Post by ajgreeny on 2015-10-01
Great!

Can you please mark this thread as SOLVED  from the "Thread Tools" menu at the top.

---

