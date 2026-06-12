---
title: "skype chat window doesn't pop up"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by grainbarcelona on 2013-09-20
Hi,

I've this annoying problem: when someone starts a skype chat with me, it doesn't open a window in front of me. It just puts a little triangle in the skype launcher - so most of the time I don't notice that people want to chat with me. I would like a chat window to pop up as soon as someone starts a chat with me.

In the skype settings, I activated 'open chat window in front of me' to no avail. I suspect that it has to do with Ubuntu windows behaviour, as I also have this problem sometimes with other programs (eg if I click on a pdf file, it doesnt open Acrobat. It just activates the program in the launchbar & I've to click on it to see it.)

I've tried fiddling with compiz setting, ubuntu tweak, etc., but nothing works. 

Anyone can help with this? Thanks

I'm on Ubuntu 13.04

---

### Post by amjjawad on 2013-09-20
> **grainbarcelona said:**
> Hi,

I've this annoying problem: when someone starts a skype chat with me, it doesn't open a window in front of me. It just puts a little triangle in the skype launcher - so most of the time I don't notice that people want to chat with me. I would like a chat window to pop up as soon as someone starts a chat with me.

In the skype settings, I activated 'open chat window in front of me' to no avail. I suspect that it has to do with Ubuntu windows behaviour, as I also have this problem sometimes with other programs (eg if I click on a pdf file, it doesnt open Acrobat. It just activates the program in the launchbar & I've to click on it to see it.)

I've tried fiddling with compiz setting, ubuntu tweak, etc., but nothing works. 

Anyone can help with this? Thanks

I'm on Ubuntu 13.04

Hi,

What is your Skype version?

---

### Post by grainbarcelona on 2013-09-20
4.2.0.11

---

### Post by kostkon on 2013-09-21
Check out [skype-wrapper]("https://launchpad.net/~skype-wrapper/+archive/ppa"); the messaging menu envelope will turn blue every time there is a new message in Skype, plus you'll get an Ubuntu pop-up notification.

---

### Post by grainbarcelona on 2013-09-21
Thanks.
But I would like skype to directly open the chat window in front of me when someone starts chatting, like it did before I upgraded. 
And I would also like application windows to open directly, when I click .doc, .pdf, etc. files, rather than having to click again on the application icon on Ubuntu's launcher bar.
Is that possible?
Thanks

---

### Post by Jonathan Precise on 2013-09-21
Try the program wmctrl. (See the manual pages for how to run)

---

### Post by grainbarcelona on 2013-09-22
According to the comments on the wmctrl installation page, wmctrl is not (yet) compatible with ubuntu 13.04. 
I also tried the solutions offered in this post: [http://www.tuxgarage.com/2011/08/auto-raise-chat-and-other-windows.html](http://www.tuxgarage.com/2011/08/auto-raise-chat-and-other-windows.html)
But it doesn't get me there either.
Any other suggestions? Is it that much I'm asking? To have a chat window pop up when someone starts chatting with me?

---

### Post by Jonathan Precise on 2013-09-23
> **grainbarcelona said:**
> According to the comments on the wmctrl installation page, wmctrl is not (yet) compatible with ubuntu 13.04. 
I also tried the solutions offered in this post: [http://www.tuxgarage.com/2011/08/auto-raise-chat-and-other-windows.html](http://www.tuxgarage.com/2011/08/auto-raise-chat-and-other-windows.html)
But it doesn't get me there either.
Any other suggestions? Is it that much I'm asking? To have a chat window pop up when someone starts chatting with me?

```
sudo apt-get install wmctrl
```

---

