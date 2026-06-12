---
title: "Menu"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by jotnarta on 2008-06-18
Hi All

I can't find my start menu, and the task bar, any help please?

Jotnarta

---

### Post by jotnarta on 2008-06-18
any help please

---

### Post by MasterSander on 2008-06-18
Did you remove them? or didn't they show when you installed?

---

### Post by jotnarta on 2008-06-18
I restarted my computer and log on again, they were disappeared :s

---

### Post by MasterSander on 2008-06-18
That shouldn't happen. You should be able to make a new toolbar and add things to the panel, including the apps menu etc.

---

### Post by jotnarta on 2008-06-18
Would you please to tell me how? I am a newbie

---

### Post by MasterSander on 2008-06-18
The problem is I'm in Vista atm, cause I have to use a program that can't be run in ubuntu, so I don't know exactly. Try right-clicking on your desktop. 

[https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/3179](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/3179)
here they suggest deleting the gnome folder, but you're using the de desktop so it should be kde for you (don't know what versian though)

---

### Post by MasterSander on 2008-06-18
[http://ubuntuforums.org/showthread.php?t=800364](http://ubuntuforums.org/showthread.php?t=800364)

Also handy, if you still got a panel left.

---

### Post by MasterSander on 2008-06-18
[https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/7759](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/7759)

Or this...

---

### Post by MasterSander on 2008-06-18
[http://ubuntuforums.org/showthread.php?t=724882](http://ubuntuforums.org/showthread.php?t=724882)

If not solved read this as well.

---

### Post by jotnarta on 2008-06-18
Thank You buddy, but I have no panel to click on it and add new panel.
Even my firefox page, when I minimize it, I use Alt+F5 to restore it.

---

### Post by MasterSander on 2008-06-18
Did you read the first post about removing the kde folder in your home directory?

---

### Post by jotnarta on 2008-06-18
Yes I did, But acutally, I didn't know how to remove it. I used the command : rm kde, but it didn't work, it gave me: no such directory kde

---

### Post by jotnarta on 2008-06-18
I am standing here on my termainl:
/home/zabin, but no such an entry called kde???

---

### Post by aquavitae on 2008-06-18
I've sometimes had similar problems for no apparent reason which clear up when I log out.

---

### Post by jotnarta on 2008-06-18
I tried to remove kde folder, but actually, I think that I couldn't. I am a newbie, and I don't know how to reach for a specific folder or file.

Besides, I didn't find any folder kde???

---

### Post by aquavitae on 2008-06-18
Try ~/.kde

---

### Post by jotnarta on 2008-06-18
Yes, I found it, but I tried this command to remove:
rm ~/.kde and I got the following : cannot remove '/root/kde': is a direcotyr

---

### Post by aquavitae on 2008-06-18
Did you use "rm ~/.kde" or "sudo rm ~/.kde"? You shouldn't use sudo here as it is not a system folder. You could also delete it by navigating to you home folder, clicking on "Show hidden files" in the nautilus menu, and finding the folder called .kde.

---

### Post by jotnarta on 2008-06-18
I used both of them

---

