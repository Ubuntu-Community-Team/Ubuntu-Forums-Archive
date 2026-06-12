---
title: "How to change Ubuntu welcome message?"
date: 2012-10-21
forum: Programming Talk
---

### Post by Onefreshfish on 2012-10-21
Recently I decided that I wanted to change my default Ubuntu login message to a more personalised ASCII art message.
I did some research and found that the message can be found by editing the **motd** file:
```
user@ubuntu$ nano /etc/motd
```Although I couldn't edit due to file permission, so I logged into root using:
```
user@ubuntu$ sudo -i
[sudo] password for user:
root@server#
```I then navigated to the same file, however when I edit it doesn't work. **It saves, but on login the message is still the old message.**
Is there anything I am missing? I apologise if this thread is in the wrong area.

[IMG]http://www.gamepursuit.com.au/server9.bmp[/IMG]

---

### Post by Pinoy Tux on 2012-10-23
How about the /etc/issue file?

---

