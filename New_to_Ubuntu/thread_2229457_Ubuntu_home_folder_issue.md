---
title: "Ubuntu /home folder issue"
date: 2014-06-13
forum: New to Ubuntu
---

### Post by jason98 on 2014-06-13
[COLOR=#333333][FONT=Helvetica Neue]I am quite a newbie to Ubuntu and Linux world. I dual booted windows 8.1 and Ubuntu 14.04. I followed a tutorial and mounted a 38GB partition at /home. Now that my /home folder is almost full (2MB remaining), but when I select "properties" in the drop down menu from home folder, it says it's totalling at 100 and so GB. I want to know why is that and if it's possible to extend my home folder as my root directory still has quite some space. Any ideas would be much appreciated, thanks![/FONT][/COLOR]

---

### Post by Impavidus on 2014-06-13
Let's have a look at the details. Can you post the output of these commands?```
df -h
sudo parted -l
```
That -l is a "minus ell". I case you didn't know yet, the sudo command will ask for your password. When you type it, nothing will appear in your terminal. Just type it and hit enter. And yes, there is also a point-and-click way of doing this, but that's a bit difficult to communicate over a forum.

---

