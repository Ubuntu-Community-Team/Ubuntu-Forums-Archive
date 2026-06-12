---
title: "Synaptic through a proxy"
date: 2006-01-31
forum: Repositories &amp; Backports
---

### Post by mgroat on 2006-01-31
I am on a network that goes through the proxy: 10.5.100.13

The proxy requires a username and password; I tried putting [http://username:password@10.5.100.13:8080](http://username:password@10.5.100.13:8080) for the proxy address, but it still dows not connect.  What am I doing wrong?

---

### Post by ralfsmith on 2006-02-05
Oh its very interesting. Could you provide me more information ?

[email]johntvery@operamail.com[/email]

[email]johntvery@hotmail.com[/email]

---

### Post by public_void on 2006-02-06
I'm behind a proxy as well. Have you editted the file /etc/apt/apt.conf, and added your proxy settings in there. If not heres how in the terminal

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

### Post by new2lnx on 2006-02-08
I would like to also follow your direction.  It's just that I don't have /etc/apt/apt.conf.  The command "locate apt.conf" simply shows the following files/directories under /etc on my system:

/etc/apt/apt.conf.d
/etc/apt/apt.conf.d/70debconf
/etc/apt/apt.conf.d/20archive
/etc/apt/apt.conf.d/05aptitude
/etc/apt/apt.conf.d/10periodic
/etc/apt/apt.conf.d/99update-notifier

Now which one should I edit?

---------------------------

Problem solved, partially.  Now I can apt-get, but proxy still does not allow synaptic to get packages.
This came after I added the following to .bashrc (that which appears within nautilus running as root, not the one we see as regular user):

export http_proxy=http://user:password@my.proxy.server:port/
export ftp_proxy=http://user:password@my.proxy.server:port/

Now, can we solve the synaptic problem?  Pleeeease.

---

### Post by public_void on 2006-02-08
Locate should being up apt.conf as the next one in the list. Have you looked for the file in /etc/apt via Nautalius. It maybe that you have to create it, I can't remember because I found those steps on this forum.

EDIT: After looking around the forum I found this other method [here](https://wiki.ubuntu.com/AptGetHowto). Go down to the "Setting up apt-get to use a http-proxy" section, it is different to what I said does work aswell.

---

