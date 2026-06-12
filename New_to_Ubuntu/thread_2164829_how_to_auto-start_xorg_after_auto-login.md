---
title: "how to auto-start xorg after auto-login"
date: 2013-08-02
forum: New to Ubuntu
---

### Post by ffvote on 2013-08-02
[COLOR=#333333][FONT=UbuntuRegular]im using this command to auto login my account on my server.
[/FONT][/COLOR]
i[COLOR=#333333][FONT=UbuntuRegular]n [/FONT][/COLOR]**/etc/init/tty1.conf**
**exec /bin/login -f username< /dev/tty1 > /dev/tty1 2>&1**

[COLOR=#333333][FONT=UbuntuRegular]so my question now is, is there a way that i can auto start xorg after this command login my account, so i dont have to type **startx**. thanks.[/FONT][/COLOR]

---

### Post by GwL3eNC on 2013-08-02
Hi,

i cant answer your question but i would like to know why you
dont let the system boot directly to  X and then use the kde autologin.

In that meaning you can read something about how to change
the runlevel in ubuntu.

---

### Post by ian-weisser on 2013-08-02
Autologin on a server seems unwise.
Starting X from a client seems uneccessary, especially if you are accessing through a terminal.

Generally, most people connecting to a remote X server use ssh.
Quite a bit of good information about how to do it at [http://askubuntu.com/questions/175902/remote-x-server-with-ssh-x](http://askubuntu.com/questions/175902/remote-x-server-with-ssh-x)

---

