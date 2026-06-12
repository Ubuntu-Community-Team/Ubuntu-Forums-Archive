---
title: "Chrome not working and even some snags with Firefox"
date: 2018-11-20
forum: New to Ubuntu
---

### Post by alex-bingham on 2018-11-20
I've just got a new desktop with Intel processor and Ubuntu 18.04.  Downloaded Chrome from Google and installed it.  When I open it though it goes to the Chrome front page and appears to freeze.  Any ideas?

Also, Firefox occasionally appears to have problems. For instance I try to log into the Cisco Netacad site and whilst it will let me type in my user name, it won't let me type in the password box.  Again, any ideas?

Chrome works fine on my laptop running the same OS.  Or is it the graphics drivers?

Any help much appreciated.

---

### Post by Autodave on 2018-11-20
Not likely a graphics driver issue, but you never know.  How about giving us some specs on the machine especially the graphics card, processor, and memory.

---

### Post by oldrocker99 on 2018-11-20
Try this:
```
sudo apt remove chrome
```

Hopefully, that will deinstall Chrome from your system.

Then, follow the instructions here:[https://www.ubuntuupdates.org/ppa/google_chrome](https://www.ubuntuupdates.org/ppa/google_chrome). Note that terminal commands need to be used.

---

### Post by alex-bingham on 2018-11-20
Thanks for the advice. I tried that but it still doesn't appear to want to work.

---

### Post by alex-bingham on 2018-11-20
I'm running Chrome from the terminal and just noticed I had the following error message:

[30077:30077:1120/220734.691370:ERROR:input_method_base.cc(146)] Not implemented reached in virtual ui::InputMethodKeyboardController *ui::InputMethodBase::GetInputMethodKeyboardController()Using InputMethodKeyboardControllerStub

Is this relevant does anyone think to why Chrome is generally unresponsive?

---

### Post by alex-bingham on 2018-11-20
Here are the details of the machine:

[ATTACH=CONFIG]281713[/ATTACH]

---

