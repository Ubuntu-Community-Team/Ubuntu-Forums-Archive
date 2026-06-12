---
title: "[SOLVED] Folder move results in empty folder"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by meindian523 on 2008-08-21
Ok,here goes.
I did the following,excerpt from my .bash_history file
```

mkdir /home/easwarh/Documents/IEEE
mv /home/easwarh/Documents/Research\ Wing/ /home/easwarh/Documents/IEEE/

```
Now what I have is an empty folder named Research Wing in ~/Documents/IEEE and no folder ~/Documents/Research Wing.
I tried checking the hidden files,in nautilus AND through gksudo nautilus,but the folder and it's contents are not visible.Can someone help?That stuff was really valuable.

---

### Post by meindian523 on 2008-08-21
And I just checke the man page for the mv command,it says nothing I could see that mentioned about moving a directory into a directory.Though,I might have missed it in the stress of losing all that stuff.. :(:oops::cry:

---

### Post by fahadsadah on 2008-08-21
Please can I see the whole .bash_history?

---

### Post by meindian523 on 2008-08-21
```

touch Sahil
vi Sahil
mv Sahil /home/easwarh/Documents/
mkdir /home/easwarh/Documents/IEEE
mv /home/easwarh/Documents/Sahil /home/easwarh/Documents/IEEE/
mv /home/easwarh/Documents/Research\ Wing/ /home/easwarh/Documents/IEEE/
clear
ls /home/easwarh/Documents/IEEE/
ls l
ls -l
ls -l /home/easwarh/Documents/IEEE/
man chmod
apropos permissions directories
apropos permissions for directories
gksudo nautilus
tail .bash_history 
cat .bash_history|less
tail .bash_history 
tail -50 .bash_history 
tail -10 .bash_history 
tail -20 .bash_history 
man mv

```
The commands above these are commands I used to help people out here on Ubuntuforums and as such have nothing do with this case.

The entire experiment I(foolishly) did is put bare here.

---

### Post by Elfy on 2008-08-21
I'm not really sure and I hope I'm wrong but I thought that it should have been

> mv /home/easwarh/Documents/Research\ Wing/[COLOR="Red"]*[/COLOR] /home/easwarh/Documents/IEEE/

I would be inclined to try and use the livecd until you are sure just in the files need to be recovered if possible.

If I've not done anything else I've bumped the thread :(

---

### Post by meindian523 on 2008-08-22
Actually,I looked in my Trash and found the files.They have been recovered.Thanks to all who contributed.I still have a problem though.
Description:
I open nautilus(as admin group user but without root rights,I'm able to see .local and access sub-directories of .local in my home folder (/home/easwarh)
I open nautilus as root via gksudo nautilus,and I navigate to /home/easwarh and I'm unable to see .local for easwarh.
I'm able to access .local via command line(Terminal) in both cases.Isn't that strange?I believe it could be a symptom of a deeper malaise.

---

### Post by Elfy on 2008-08-22
> Actually,I looked in my Trash and found the files.:D

Yes I'd say it was a bit odd, but that's all I could say... not sure why that could be - you could check the permissions 

this mione other than that - ?

drwxr-xr-x   3 kevin kevin     4096 2008-04-17 20:46 .local


Glad you found your files though, tbh - I generally do a cp and rm instead of a mv - but didn't want to say that yesterday ;)

---

### Post by meindian523 on 2008-08-23
The permissions were 700,fixed them to 755,still root can't see .local.Now what?

---

### Post by meindian523 on 2008-08-27
Well,root can now see .local,though how the issue was resolved,I don't know.Thanks to all who helped.

---

### Post by Elfy on 2008-08-27
Afraid I don't know - but it's decidely odd that nautilus doesn't let you see them.

---

### Post by meindian523 on 2008-08-27
Correction.Didn't let me.Now it does.As to how,I'm as clueless as the next person.

---

