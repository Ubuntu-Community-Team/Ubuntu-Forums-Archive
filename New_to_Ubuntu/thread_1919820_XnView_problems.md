---
title: "XnView problems"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by Curtis6767 on 2012-02-03
I found this [thread ]("http://ubuntuforums.org/showthread.php?t=1874561&highlight=xnview")and followed the directions. 

I got as far as looking for "Bin" sub-folder, but could not find it.

Also, I created the folder XnView and when I click on it hoping to find "Bin", etc, I go to another folder called XnViewMP. I clicked on that folder expecting to find "Bin", but no such luck.

Can anyone help me get past this so I can use  XnView.

Also, I looked in the read README file, where it says I need to change the path name in XnView.desktop but I am not allowed to open that file because it is not trusted.

---

### Post by rojaasensei on 2012-02-03
The easy way to install the latest version of XNView is through this PPA:

sudo add-apt-repository ppa:dhor/myway
sudo apt-get update
sudo apt-get install xnview


This PPA has some other fine graphics packages you can explore. :-)

---

### Post by Curtis6767 on 2012-02-03
I'll try it.

First, should I delete the XnView that I've downloaded but can't run?

---

### Post by rojaasensei on 2012-02-03
That sounds like a good idea

---

### Post by dcsoldschool53 on 2012-02-04
[B]Click on the link to download the file, and untar it.
 [/B][http://newsgroup.xnview.com/viewtopic.php?f=60&t=24056](http://newsgroup.xnview.com/viewtopic.php?f=60&t=24056)
** Then, in a terminal```
cd
``` in to the xnview folderand type ```
ls -l
``` at the prompt. You will be looking for a file called.xnview.sh. Now, in the terminal type```
./xnview.sh
```I hope this helps.**

---

### Post by Curtis6767 on 2012-02-04
I was able to install XnView using the PPA

Seems to be working fine.

Thanks.

If I could figure out how to change [ubuntu] into [solved], I would do that.

---

### Post by dcsoldschool53 on 2012-02-04
> **Curtis6767 said:**
> I was able to install XnView using the PPA

Seems to be working fine.

Thanks.

If I could figure out how to change [ubuntu] into [solved], I would do that.

Click on Thread tools - Mark Thread as Solved.

---

