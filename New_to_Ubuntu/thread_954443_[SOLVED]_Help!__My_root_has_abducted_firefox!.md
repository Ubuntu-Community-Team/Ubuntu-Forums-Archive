---
title: "[SOLVED] Help!  My root has abducted firefox!"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Zorgoth on 2008-10-21
More or less, the title says it all.  I had a problem earlier with a drive that was only accessible by root and I saved something in it with "sudo firefox," and after I closed it, opening firefox the normal way stopped working; I had no history, no home page, and couldn't, for example, press "back" to see previous pages, and only sudo firefox had these features.

For now, I changed my launcher to sudo so I still get a nice firefox when I press the button, but I would like a more elegant fix...  I assume it has something to do with file permissions or something of that nature...

---

### Post by Zorgoth on 2008-10-21
gksudo firefoc actually

---

### Post by Thelasko on 2008-10-21
> **Zorgoth said:**
> For now, I changed my launcher to sudo so I still get a nice firefox when I press the button, but I would like a more elegant fix...  I assume it has something to do with file permissions or something of that nature...

Yikes! Don't do that!
What did you save?
If you open the terminal and type "firefox" what does it say?

---

### Post by cek on 2008-10-21
Root has likely assumed ownership of your user's .mozilla (?) directory.  I don't have a linux machine in front of me, so I don't know if the files are still in .mozilla or if they've been moved to a .firefox or similar.  Have a look at the hidden directories to see potential places for the firefox user files.

You should be able to change the permissions/ownership of this directory and reclaim firefox for yourself.

From your user's home directory:
sudo chown -R ./.mozilla

and see if that makes a difference.

---

### Post by Thelasko on 2008-10-21
> **cek said:**
> Root has likely assumed ownership of your user's .mozilla (?) directory.  I don't have a linux machine in front of me, so I don't know if the files are still in .mozilla or if they've been moved to a .firefox or similar.  Have a look at the hidden directories to see potential places for the firefox user files.

You should be able to change the permissions/ownership of this directory and reclaim firefox for yourself.

From your user's home directory:
sudo chown -R ./.mozilla

and see if that makes a difference.
I figured a .mozilla folder would simply be created in the /root folder.  If what you are saying is true the directory should be "/home/*username*/.mozilla/firefox".  Where *username* is of course the user's username and .mozilla is a hidden file viewable in nautilus by pressing ctrl+h.

---

### Post by cek on 2008-10-21
> **Thelasko said:**
> I figured a .mozilla folder would simply be created in the /root folder.  If what you are saying is true the directory should be "/home/*username*/.mozilla/firefox".  Where *username* is of course the user's username and .mozilla is a hidden file viewable in nautilus by pressing ctrl+h.

Correct.  If you log in as root (or simply su to root/another user) I believe you are correct in that a new .mozilla folder would be created in the home directory of the new user (be it root or otherwise).

However, I think the sudo command works slightly differently -- it just changes the user that executes the target command without updating to the target user's profile.  I've had similar issues with files like .bash_history after executing a sudo xterm (to perform some lengthy tasks in a terminal as a root user).

---

### Post by bodhi.zazen on 2008-10-21
The issue is environmental variables, ie $HOME.

When you use sudo to obtain a root shell, you should use

```
sudo -i
```

the -i flag = a log in shell = root's environmental variables.

If you just sudo or sudo -s you use your users environmental variables, and as in this case root can over write files and directories in your user's home and cause breakage (although the fix in this case is easy).

For graphical applications use gksu (kdesu in Kubuntu). In addition to using root's environmental variables, gksu also give sane access to X.

See also this post :

[http://ubuntuforums.org/showpost.php?p=4636376&postcount=16](http://ubuntuforums.org/showpost.php?p=4636376&postcount=16)

If you do not understand environmental variables, just try this:

```
sudo -s #Enter password
echo $HOME # Show $HOME
exit #Exit the root shell

sudo su
echo $HOME
exit

sudo -i
echo $HOME
exit

gksu gnome-terminal
#Now in the new terminal
echo $HOME
exit
```

FYI, this thread is an example of why, as a mod, I keep "harping" on root logins and sudo -i

---

### Post by Zorgoth on 2008-10-21
Thanks, the .mozilla directory was the one that it took over.  I'm no longer using gksudo (I should have been using gksu?  What's the difference?).

---

### Post by Thelasko on 2008-10-21
> **Zorgoth said:**
> Thanks, the .mozilla directory was the one that it took over.  I'm no longer using gksudo (I should have been using gksu?  What's the difference?).

I can't think of any reason to run Firefox under sudo.  EVER!

---

### Post by bodhi.zazen on 2008-10-21
> **Zorgoth said:**
> Thanks, the .mozilla directory was the one that it took over.  I'm no longer using gksudo (I should have been using gksu?  What's the difference?).

gksu is a symbolic link to gksudo, so they are almost the same, gksu is for the lazy types.

---

