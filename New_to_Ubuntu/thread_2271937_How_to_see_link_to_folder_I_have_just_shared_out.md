---
title: "How to see link to folder I have just shared out"
date: 2015-04-02
forum: New to Ubuntu
---

### Post by saurabh13 on 2015-04-02
Hello, new to Ubuntu: 

I wanted to share out a folder(directory) with my teammates who are on the same network. I did the following 'Right Click -> Sharing Options -> Share' and see that the folder is now shared. 

What is the link I should send my teammates so they can look at this? 

Fox example, if I shared a folder on Windows, I would do the following
1. net share "foldername"  (or Right Click -> Share) 
2. I would send out a link like so \\machinename\sharename 

And if I wanted to send the link to a file in the share, I would send 

\\machinename\sharename\filename.html 

What is the Linux equivalent of "\\machinename\sharename" . I will really appreciate an answer.

---

### Post by Holger_Gehrke on 2015-04-03
If you're using standard Ubuntu and it's standard file manager (nautilus), then you're doing your sharing through samba. samba is written to behave just like windows sharing, so the link would be just the same as it is in windows, '\\machinename\sharename".

---

