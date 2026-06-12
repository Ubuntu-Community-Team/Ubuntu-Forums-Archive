---
title: "How Do I Share a Folder With a Windows PC With No Password Prompt?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-10-18
I have Ubuntu 8.04 on my PC. My wife has Windows 2000 on her PC. When I was using XP, she could shoot a file to my desktop from her PC in two seconds. Now she's prompted for a username and password (which is my Ubuntu login name and password). It's a pain. I want this to work like it used to - with the Windows user able to access my Ubuntu desktop without providing any password or username. How is that done? When I click on the "Help" menu in Samba, the window simply closes. Other stuff I've read online covers just about everything I don't need to know, and nothing I've seen covers this. Can someone provide a step-by-step or a link? Thanks.

---

### Post by quinnten83 on 2008-10-18
try this:
rightclick the folder you want to grant access to
go to properties> share
click the option to grant access for users without a user account.
Might help I dunno.
Also I believe windows is supposed to remember the password so you won't have to add it everytime.
Check on your wifes pc to be sure.
either that or create an account for your wife on your ubuntu machine and add her to the group who can access the folder. She should have to enter her password once.
What you can also try is to make the share accessible to everyone in the smb.config file. This youtube video will show you how.
[http://www.youtube.com/watch?v=Ad17kma8rNM&feature=related]("http://www.youtube.com/watch?v=Ad17kma8rNM&feature=related")

---

### Post by bobsmith2 on 2008-10-19
> **quinnten83 said:**
> 

try this:
rightclick the folder you want to grant access to
go to properties> share
click the option to grant access for users without a user account.


Thanks quinnten83. I think you may have hit on the problem, because the option to "grant access for users without a user account" is greyed out. How do I get that option enabled? Thanks!

---

### Post by superprash2003 on 2008-10-19
hope this helps [http://prash-babu.blogspot.com/2008/07/samba-share-folders-or-files-without.html](http://prash-babu.blogspot.com/2008/07/samba-share-folders-or-files-without.html)

---

