---
title: "changing Ubuntu login screen"
date: 2015-12-30
forum: New to Ubuntu
---

### Post by rob154 on 2015-12-30
Hello, I'm having trouble with customizing my login screen for Ubuntu 14.04. I just want to change the background wallpaper and the login icon where you input your login password. I've tried going to other forums, downloading Ubuntu tweak, and even using "dsconf-editor" through the terminal. Nothing seems to change the login screen.

---

### Post by deadflowr on 2015-12-30
Do you want to use the same image as what you have when you login?
Or do you want to set a separate image for the login screen entirely?

Also, the icon for the Ubuntu login box is in the folder /usr/share/unity-greeter.
The icon should be something like ubuntu-badge.png.
Or any of the other icons seen on screen should also be in that folder.
(note that you will need sudo/root to make changes to that folder)

---

### Post by rob154 on 2015-12-30
Thank you for the help, I've figured it out. Apparently the image permission needed to be change to read only. Which I do not understand why that would make difference. I'm trying to find the site where I found my solution, but I'm having a difficult time tracking it down. If I find it I'll post it up. Till then I'll tag this as solved.

---

