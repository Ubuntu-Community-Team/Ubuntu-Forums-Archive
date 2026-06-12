---
title: "User Permissions"
date: 2015-08-25
forum: New to Ubuntu
---

### Post by trislong on 2015-08-25
Why is it, every time I try to use the gui to extract a .zip it tells me I do not have the permissions? I am wondering how to give myself the permissions when I am the only user on this pc and it says I am the administrator. I know I can do it through terminal using sudo. But sometimes it is just more beneficial to use the gui.

---

### Post by TheFu on 2015-08-26
> **trislong said:**
> Why is it, every time I try to use the gui to extract a .zip it tells me I do not have the permissions? I am wondering how to give myself the permissions when I am the only user on this pc and it says I am the administrator. I know I can do it through terminal using sudo. But sometimes it is just more beneficial to use the gui.

At the center, Unix (and Linux) are multi-user operating systems. Different processes run as different userids as part of the security model. You are NOT the only user of the system, even if you are only person using it. There are probably 10-30 other user accounts, each used for different reasons.

A clear understanding is needed to avoid reoccurring issues with file permissions. Abusing sudo is a short-term solution and sometimes causes more problems than it solves. For example, using *sudo gedit* can cause terrible issues - use **sudoedit** instead. I've had to help a few nice people who used sudo too much fix a login problem.

Understanding file and directory permissions is also central to using a Unix system.  Different userids have different privileges to different directories.  It is NOT safe for a normal userid to write anything to / (or many other locations), but they should be able to write almost anything to their HOME - also called ~/.  If, however, these userids have been using sudo too much, it is possible that parts of their HOME have been taken over by the root userid (the normal account that running sudo invokes).

So that explanation doesn't help you solve the problem. Hopefully it explains why file permissions are so important to understand. We need specifics to help you  solve it. 
What file?  
Which directory is the file in?  
What userid?
Which program(s) are being used?

Ubuntu does have a file and directory permissions tutorial:
  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
Or if you learn better by watching a video: 
  [https://www.youtube.com/watch?v=Yx9ipORQp5g](https://www.youtube.com/watch?v=Yx9ipORQp5g)

Practice of this knowledge is needed.  Please create a few extra accounts, a few groups, then mix and match these with your account, open a few terminals, login to a different userid in each, then create some files, directories with different userids, different groupids and different permissions. See what works and what doesn't for each userid to still keep access and to prevent it. 

GUI or CLI/shell - doesn't matter.

The Unix permissions model is really elegant, once understood.  That knowledge is forever.

---

### Post by howefield on 2015-08-26
Is this question connected to your other question re themes ?

In which case, you can probably extract to a .themes folder inside /home.

As TheFu states above, you will need elevated permissions to extract anywhere that is outside of your /home folder.

---

### Post by trislong on 2015-08-26
Well I really appreciate the explanations. Thanks a lot for that. I understand a lot better now. :)

---

