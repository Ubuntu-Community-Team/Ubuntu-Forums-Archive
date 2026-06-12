---
title: "Saving as admin in gedit when you are not an admin"
date: 2015-03-06
forum: New to Ubuntu
---

### Post by Delco on 2015-03-06
I frequently open text documents and edit them, only to not be able to save them because I am not an admin. So I have to either open nautilus and navigate back to the file to open it as an admin, which is time consuming. Is there a way to save a text file as an admin in gedit (to make it prompt for my password) instead of just shutting me out of saving it? Alternatives to gedit are fine, too.

---

### Post by DuckHook on 2015-03-06
There is no "admin" account in Ubuntu, so I assume you are referring to root.

You should not need to save text files as the root user except system files like configuration files, setup files, etc. If you are saving general text files as root, then please tell us what your use case is so that we can advise you whether there is a better way to do things.

That said, to create and save text files owned as root, with root privileges, you must launch gedit using gksudo:```
gksudo gedit &
```If you then exit the root instance of gedit and try accessing the resulting file from your normal user account, you will be denied access. Is this what you really want? I can't imagine why.

---

### Post by Bucky Ball on 2015-03-06
If it's not letting you save a text file because you don't have permission, that would be about the permissions set on the partition/folder you are attempting to save it to I would think rather than the file. If it was the file, you wouldn't be able to open it in the first place, probably. 

Where are you trying to save the file? To an external drive? A folder on an EXT or NTFS partition?

---

### Post by Delco on 2015-03-08
I am editing various config files in folders in the /etc folder, primarily for a lamp server (apache, php). As I am very new to linux, and it is my first time trying to configure a lamp server, I have to open these files constantly for running tests and often forget to open them as root (I am using "admin" equivalently with "root" here). I am also not sure what files even require admin privileges so it's been somewhat of a guessing game for me.

---

### Post by deadflowr on 2015-03-08
> **Delco said:**
> I am editing various config files in folders in the /etc folder, primarily for a lamp server (apache, php). As I am very new to linux, and it is my first time trying to configure a lamp server, I have to open these files constantly for running tests and often forget to open them as root (I am using "admin" equivalently with "root" here). I am also not sure what files even require admin privileges so it's been somewhat of a guessing game for me.

Most everything outside your personal home folder requires root(sudo) to write/edit.

---

### Post by Yellow Pasque on 2015-03-08
> Is there a way to save a text file as an admin in gedit
I don't think you can magically elevate permissions if you've started gedit as an unprivileged user.

---

### Post by newb85 on 2015-03-08
I've been caught many times editing config files outside /home in gedit and forgetting to use gksudo.  Perhaps the best solution (so as not to lose your work) is to simply File>Save As and stash it to the Desktop.  Then, from the terminal, you can sudo mv the file to it's proper place, overwriting the old one.

---

### Post by danne33 on 2015-03-08
This used to happen to me, when I was a beginner. What I did was just to copy everything (Ctrl+c), then close the document and quickly open it as root and past everything.
Like I told you: this happens when you are new to Linux. Now I "never" (extremly rarely) make that error.

---

### Post by haplorrhine on 2015-03-08
You can add write permissions just long enough to save.
Chmod +0222
Chmod -0222.
It will be the last entry in .bash_history anyway, so just hit up and change + to -.
 -0222 will remove write permissions for all users and groups, but I think this is generally a good security practice anyway.

Vi or Vim will clearly warn you that you are trying to edit a read-only file.

---

### Post by Delco on 2015-03-09
Helpful responses - thank you all.

I took the habit of copying the data, and re-opening as an admin, but I  have such a habit to using ctrl+c/v/p all the time I have mistakenly  overwritten my original file. I then started saving to the desktop.

The temporary chmod is a very clever idea (or at least to me, a linux newbie). Thanks for sharing.

---

