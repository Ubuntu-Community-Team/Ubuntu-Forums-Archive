---
title: "cannot install Firefox 3"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by yatgirl on 2008-07-14
running gutsy: because of picture editing software that doesn't run on hardy. I'm pretty happy with gutsy anyway but there is no install option in aptitude like in later versions of kubuntu...which leads me to:

firefox-3.0
I got the tar, extracted it and it even says it is installed in terminal.

However it is nowhere to be found. I tried to update firefox 2 to 3 but that didn't work so I just uninstalled the whole firefox program and tried to cleanly install firefox 3 from scratch, in terminal.

hope someone can help,
chela :)

---

### Post by Vadi on 2008-07-14
Click here ([click]("apt:firefox-3.0")) to install ff3 from the repository. After that, do alt+f2 and type "firefox", and select the 3 one.

---

### Post by sbassett on 2008-07-14
Yat -

It looks like you will have to download the tar and install again. You will have to take notice as to where it installs, if it installs at all. I could very well just create a single folder with the binary located inside (called simply "firefox"), in which case, you could create a desktop shortcut to the file (in Gnome, middle click the file and drag to the desktop) or create a menu entry manually pointing to that location within the extracted firefox folder.


Vadi -

I don't believe firefox 3 has been released for gutsy, has it?

---

### Post by Vadi on 2008-07-14
[Of course it was]("http://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=gutsy&section=all"). packages.ubuntu.com is your friend :)

---

### Post by sbassett on 2008-07-14
Looks like it only made it to Alpha 8, however.

---

### Post by Vadi on 2008-07-14
Hm I believe that means it was introduced in alpha 8, it should still be there

---

### Post by avtolle on 2008-07-14
Here is something that might help you out: [http://psychocats.net/ubuntu/firefox](http://psychocats.net/ubuntu/firefox)

---

### Post by avtolle on 2008-07-14
> **Vadi said:**
> Hm I believe that means it was introduced in alpha 8, it should still be there
I think that it means that the version is FF3, alpha 8, not the final....

---

### Post by yatgirl on 2008-07-14
> **avtolle said:**
> Here is something that might help you out: [http://psychocats.net/ubuntu/firefox](http://psychocats.net/ubuntu/firefox)

YES!!! Thank you!!! I used to have that link and when I first got started with Kubuntu it was pretty much where I learned all I knew. Lost it a while back when I tried to update to Hardy before I realized I couldn't use Hardy...I somehow messed around and lost the link! Psychocats pages are trusted & kitchen tested! :D

Thanks everyone for pointing me in the right direction. Thanks again for that link,
oxoxoxo
Chela

p.s. for the guys who are pm'ing me that they think I'm cute & want more pix...well here ya go!

---

### Post by Sweet Spot on 2008-07-17
Helpful thread, but I seem to be experiencing some problems installing FF 3 via the methods shown on the psychocats page. I'm in my Home/username/ directory and opened the terminal from there, ran the first command and was told:

> cp: cannot stat `/home/*******/.mozilla': No such file or directory

So I guess I can't get very far at this point. Anybody know why this might pop up ?

doug

---

### Post by Bachstelze on 2008-07-17
> **yatgirl said:**
> 
p.s. for the guys who are pm'ing me that they think I'm cute & want more pix...well here ya go!

You can also report them to the staff instead of posting silly pictures in support threads. Thanks.

---

### Post by moody_mark on 2008-07-17
Hi, it worked for me, here's the command I used;

/usr/local/bin/ubuntuzilla.py

Unless the /usr/local/bin is in your path then it wont find the script. (im sorry if you tried this already and im stating the obvious here) :-)

---

