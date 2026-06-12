---
title: "xubuntu server setup"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by Grimspark on 2012-03-02
Hi everyone, 
Im very new to ubuntu and setting up my own network so I was hoping that I could get pointed towards some good resources for tutorials or tips re: setting up and maintaining a server.

I have installed xubuntu and hope to achieve the following:
1. A secure setup.
2. It needs to communicate with multiple windows boxes on my home network.
3. I hope to do some web publishing too.

I know the info is out there but theres so much to sort through, thanks in advance folks!

---

### Post by seawolf167 on 2012-03-02
A starting point would be to check out the [Ubuntu Server Guide ]("https://help.ubuntu.com/11.04/serverguide/C/index.html")and see if that helps.

EDIT: Here is a link for [Webmin]("http://webmin.com/"), a good web-based interface for server administration.

---

### Post by jailbait on 2012-03-02
> **Grimspark said:**
> Hi everyone, 
Im very new to ubuntu and setting up my own network so I was hoping that I could get pointed towards some good resources for tutorials or tips re: setting up and maintaining a server.

I have installed xubuntu and hope to achieve the following:
1. A secure setup.
2. It needs to communicate with multiple windows boxes on my home network.
3. I hope to do some web publishing too.

I know the info is out there but theres so much to sort through, thanks in advance folks!
1. [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
2. If communicate you mean by sharing files, you can use [SAMBA.]("https://help.ubuntu.com/community/Samba/SambaServerGuide")
3. What language are you using? Perl? Ruby? PHP? HTML?

If your lazy, and just want to setup Ubuntu without going through the commandline, check out Zentyal.

---

### Post by Grimspark on 2012-03-02
Thanks folks, this'll be great to get me sarted.

> **jailbait said:**
> 
3. What language are you using? Perl? Ruby? PHP? HTML?


I'm starting with html, but may move on to other stuff later.

---

### Post by jailbait on 2012-03-04
> **Grimspark said:**
> Thanks folks, this'll be great to get me sarted.



I'm starting with html, but may move on to other stuff later.
Then use nginx instead of apache2.

---

