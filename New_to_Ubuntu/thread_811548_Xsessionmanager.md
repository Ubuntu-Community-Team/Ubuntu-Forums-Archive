---
title: "Xsessionmanager"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by msidhard on 2008-05-29
My Gui Crashed. And It Says Xsessionmanager Is Not Installed

---

### Post by y-lee on 2008-05-29
I am assuming you have a command prompt and are using ubuntu and hence gnome. have you tried reinstalling gnome session manager?

```
sudo apt-get install gnome-session
```

Edit: I am assuming you have tried rebooting? And it would help to know exactly what you did if anything to cause this.

---

### Post by msidhard on 2008-05-31
actually i done it but that thing goes to internet. but i am connecting internet through mobile which needs a separate terminal kept open for it. but in root@terminal it cannot be successful hence if  i connect to net i cannot type commands till i close the connection. co how i try sudo apt-get install x-session-manager

---

### Post by y-lee on 2008-06-01
I'm not sure I exactly understand your situation. but

If you can somehow [download the package]("http://packages.ubuntu.com/hardy/i386/gnome-session/download") maybe on another computer (or perhaps find it on the live CD) one could use dpkg to install it.

For example to download (assuming you are using hardy):

```
 wget http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-session/gnome-session_2.22.1.1-0ubuntu2_i386.deb
```

And to install as normal user:

```
sudo dpkg -i gnome-session_2.22.1.1-0ubuntu2_i386.deb
```

---

