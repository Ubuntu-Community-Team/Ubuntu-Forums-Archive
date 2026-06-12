---
title: "Desktop not loading for main user"
date: 2014-02-15
forum: New to Ubuntu
---

### Post by Light Knight 22 on 2014-02-15
Hi there. 

So before 13.10 I was playing around with kde and "broke" my desktop. It would simply not load when I logged in. After updating to 13.10 and unistalling kubuntu, I STILL cannot access my desktop, but I can just fine from the guest account. 

What I see is simply the background default image and nothing else. I can crt+alt+del and ctrl+alt+F1 and get a response... but that's it, nothing else loads or seems to work. 

I am using ubuntu on a partition alongside windows 7, and just can't seem to fix this problem, please help.

---

### Post by deadflowr on 2014-02-15
Is this default ubuntu with unity desktop not loading?
Then you'll probably need to reset it.
If you can gain access to a terminal by run
ctrl+alt+T
then see if doing the command here help
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

It's a complete assumption on my part, but a totally blank screen with nothing but the background image in typical of unity being disabled. resetting it should bring in back, though you'll have to re-tweak whatever you might have done before.Since reset puts it back to the default settings.(Which includes the default workspaces, which for 13.10 is only one)

---

### Post by Light Knight 22 on 2014-02-16
Hello and thank you!

Yes, it was the default unity not loading. After trying the second method in that post (dconf-tools) my desktop returned, though I havn't tryed loging out again to see if it happens again. 

However, there was a message that stalled the first method, and did show up again when using dconf-tools, here it is: [https://www.dropbox.com/s/0qlnrie1pfoqsh6/20140216_090457.jpg](https://www.dropbox.com/s/0qlnrie1pfoqsh6/20140216_090457.jpg) . 

Is this something I should try to fix?

---

### Post by deadflowr on 2014-02-16
Unity should persist now.

As for that error you can look up that particular setting in dconf-tools.
It'll list the default value you can set it as.
(It usually is set as the defaults, or is a non-usable function)

Personally, I think it's probably not overly important.

Edit: dconf-tools installs a program called dconf editor, that's what I mean by checking the setting in dconf-tools.

---

### Post by Light Knight 22 on 2014-02-16
Thanks!

---

