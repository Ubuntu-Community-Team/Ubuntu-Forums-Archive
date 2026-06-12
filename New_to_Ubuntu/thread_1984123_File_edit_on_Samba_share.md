---
title: "File edit on Samba share"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by andperry on 2012-05-21
I'm trying to edit a file on my Ubuntu 12.04 server from a Windows workstation via a Samba share. It's an intelligent text editor inasmuch as it dynamically detects updates to the file from outside sources.

I keep getting prompts to say that the file has been modified by another application (e.g. when trying to save the file or when returning focus to the editor within Windows). The only logical explanation I can think of is that the Samba service itself is doing something by way of a background activity.

Has anyone any idea what is happening and if it can be stopped? It is only mildly annoying with just one file, but being a tabbed editor that can open lots of files, the problem could potentially become very annoying!

Thanks.

---

### Post by zeroseven0183 on 2012-05-21
1. Do other users in your network experience the same problem?
2. Do you encounter the same issue when opening the file with other text editor?

I don't want to assume but you're probably using Notepad++. Sounds like.

---

