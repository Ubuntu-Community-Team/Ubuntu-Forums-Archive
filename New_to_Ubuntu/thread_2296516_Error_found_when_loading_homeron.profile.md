---
title: "Error found when loading /home/ron/.profile"
date: 2015-09-26
forum: New to Ubuntu
---

### Post by mr.Ron on 2015-09-26
Last night I searched for ways to upgrade node and npm.  I copied and pasted some suggestions and upgraded to their stable versions.
I also installed NVM as a forum-user suggested to do.

But this morning when I started ubuntu, I received the following pop up message:

[I]"Error found when loading /home/ron/.profile

/home/ron/.profile line 24: export /home/ron/.npm/bin not a vaild identifier

As a result the session will not be configured correctly.
You should fix the problem as soon as feasible."[/I]

I also noticed my second monitor is not being recognized by Ubuntu on System Setiings.

I am an absolute beginner and started using Ubuntu just a couple of months ago.
I have no clue where to start to fix this issue-Thanks so much for sharing your wisdom.

mr.Ron

---

### Post by matt_symes on 2015-09-27
Hi

The export on line 24 of your .profile file is invalid. 

I expect you were trying to append the new path to your PATH environmental variable but without knowing what tutorial you followed it's difficult to know exactly what you have done.

I expect line 24 in your profile file should look more like

```
PATH=$PATH:/new/path/in/your/home/folder
```

Post a link to the tutorial you followed and we can take a look for you.

Kind regards

---

