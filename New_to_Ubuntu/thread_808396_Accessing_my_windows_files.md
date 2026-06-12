---
title: "Accessing my windows files"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by CrossS on 2008-05-26
Probably a stupid question but I'm asking anyway.

I have just installed Ubuntu and this is the first time I try Linux, ever.
I installed Ubuntu on my c: so I can choose whether I want to start Ubuntu or Windows XP. In Windows I have all my music and videos in My documents. 

Is it possible to access those files from Ubuntu?

---

### Post by TeoBigusGeekus on 2008-05-26
Of course. Go to places, find your windows partition and open it. Well, that's it - as simple as that.

---

### Post by CrossS on 2008-05-26
I'm probably stupid but it doesn't look that easy to me :/ 
I didn't make a dedicated Ubuntu partition, so Ubuntu and Windows are both installed on c: Ubuntu is installed on c:/Ubuntu and Windows is installed in c:/windows

---

### Post by TeoBigusGeekus on 2008-05-26
Oops! Are we talking about wubi? Cause I've got no idea about it...

---

### Post by inportb on 2008-05-26
Ah, so you've used Wubi. I haven't any experience with Wubi, but I'd tend to think that it would be difficult or impossible to do what you are asking. Perhaps you might consider installing Ubuntu normally on a partition...

---

### Post by CrossS on 2008-05-26
And I have no idea what wubi is? :/

---

### Post by TeoBigusGeekus on 2008-05-26
How exactly did you install Ubuntu?

---

### Post by AndrewTheArt on 2008-05-26
Wubi is the Ubuntu installer for Windows. Looks like you used that.

>              **Can I access my Windows files from a Wubi installation?**

             Yes, the Windows partitions will be available within the directories /host and /media.
         
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

So go to the Places menu, and you should see some some icons there that will lead you to your C drive basically. Or click on "Computer" on that list and look around in there. Finally, if all else fails, type in /host or /media in the "Location" textbox. 

Good luck!

---

### Post by CrossS on 2008-05-26
What do you mean, installing Ubuntu normally? I thought I did. Was I suppose to create a separate partition for Ubuntu? :S

---

### Post by CrossS on 2008-05-26
Thanks AndrewTheArt. I found them :D

---

### Post by TeoBigusGeekus on 2008-05-26
Did you boot up with a live cd of Ubuntu and installed with it, or did you install Ubuntu through window$?

---

### Post by CrossS on 2008-05-26
I downloaded the Ubuntu 8.04 and burned it to a cd, booted from it and chose install Ubuntu.

---

### Post by TeoBigusGeekus on 2008-05-26
Righto!
So, when you go to Places->Computer, what do you see?

---

### Post by CrossS on 2008-05-26
Home Folder
Desktop
Documents
Music
Pictures
Videos
Computer
CD/DVD creator
Network
Connect to server
Search
Recent Documents


But I found the files within the directories /host and /media. As AndrewTheArt said :)

---

### Post by TeoBigusGeekus on 2008-05-26
> **CrossS said:**
> Home Folder
Desktop
Documents
Music
Pictures
Videos
Computer
CD/DVD creator
Network
Connect to server
Search
Recent Documents


But I found the files within the directories /host and /media. As AndrewTheArt said :)
Glad to read that!

---

