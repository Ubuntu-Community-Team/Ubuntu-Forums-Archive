---
title: "sudoers problem -- can't use sudo"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by JohnDillinger43 on 2013-04-07
Recently I noticed a problem with my daily rsync backup -- it didn't have permission to open my /etc files to back them up.  I (perhaps stupidly) assumed this was a file permissions problem, and (as far as I remember) all I did was give my group read permissions to those files.  Well, apparently I did something horribly wrong with the file permissions (I don't know what I thought it was a good idea to mess with file permissions on system files in the first place), because now I can't do anything.  The login screen after startup doesn't display my login name, and though I can put in my name and password now (after adjusting permissions on /etc/sudoers from the recovery console) I can't get to the graphical interface no matter what I do.

If someone can explain to me what I did and how to fix it I will be eternally grateful, because otherwise I think I'm just going to have to reinstall Ubuntu.

For reference, the error message I'm getting says that file permissions are 0444 and should be 0440.  I can't post the text verbatim if helpful.

---

### Post by Impavidus on 2013-04-07
I don't know what you did exactly, but it sound like you changed groups and permissions on files in /etc. This breaks your system and there is no undo. If you remember exactly which files you changed and there are only a few of them, you can fix it by changing them back one by one. If you changed them recursively on entire directories the only realistic option is to make backups of your files and reinstall.

---

### Post by schragge on 2013-04-07
[size=-1]*Deleted. Sorry, wrongly posted.*[/size]

---

### Post by JohnDillinger43 on 2013-04-08
Well, I reinstalled Ubuntu without formatting anything and everything seems to be running fine now, with no loss of data.  The only problem is that my wifi is horrifically slow (worsening of a problem that already existed); I'm going to go post in the networking section about that.

---

