---
title: "If You Are Having Trouble Getting Adobe Flash To Work In Chromium"
date: 2015-05-18
forum: New to Ubuntu
---

### Post by Stephan_H_Smith on 2015-05-18
Hi, all, I installed Chromium web browser because to me, Fire Fox was just running too slow. But when trying to look at videos in Face Book (yeah, I know), most of the videos were erroring out. So, I looked up Adobe Flash in Ubuntu Software Center. Adobe Flash said it was installed, and that it is supposed to work with Chromium. But I saw one of the comments, they said it does not work for Chromium. Instead, we should install Pepper Flash Plugin.

In terminal:

sudo apt-get install pepperflashplugin-nonfree


sudo update-pepperflashplugin-nonfree --install


If Chromium is running when you do this, close it and reopen it.


I did it, and now all videos play just fine. Just thought I would put this out there in case anyone's having this problem.

---

### Post by RobGoss on 2015-05-18
Thanks for post this helpful info.

---

### Post by Stephan_H_Smith on 2015-05-18
You are very welcome!

---

