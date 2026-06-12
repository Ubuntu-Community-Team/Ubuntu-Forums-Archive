---
title: "Having problems with proxy"
date: 2006-02-16
forum: Repositories &amp; Backports
---

### Post by yuneyev on 2006-02-16
Hail.

I'm a begginer at Ubuntu and Linux, needing some help =)

Well, I'm having problems to make updates and install packages from internet, cause here we use a proxy that requires a username and a password...so I receive the message "10:57:14 ERROR 407: Proxy Authentication Required." almost everytime ;/

Can you guys help me?

Thank you =)

---

### Post by public_void on 2006-02-17
I'm behind a proxy as well. Have you editted the file /etc/apt/apt.conf, and add your proxy settings in there. If not heres how in the terminal

cd /etc/apt/ (Changes the directory to /etc/apt/)
cp /etc/apt/apt.conf /etc/apt/apt.conf_backup (Copies the file apt.conf to the same directory be renames it apt.conf_backup. This is incase you make a mistake, you don't have to do that command)
sudo gedit apt.conf (Opens apt.conf in a text editor and allows you to edit it)
Add the lines

```
ACQUIRE { 
http::proxy "http://[Username]:[Password]@[Address]:[Port]/" 
}
```

Once done, change the proxy server in Synaptic to "Direct connection to the internet". I don't know why but it worked for me.

---

