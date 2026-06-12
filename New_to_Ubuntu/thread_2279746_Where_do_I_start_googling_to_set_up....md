---
title: "Where do I start googling to set up..."
date: 2015-05-25
forum: New to Ubuntu
---

### Post by richard-portelli on 2015-05-25
Hello. I'm new to this forum but a little more experienced with Linux. I currently have access to a VPS environment on a public IP. What I want to do is set up a headless server so that I can log into it remotely in a graphical desktop environment such as LXDE. I have SSH access and know how it works. What I don't know is the name of the services to Google that allow  this set up to happen. Any higher lever explanation of how to set this up would be appreciated. Walk troughs are awesome too.

---

### Post by sandyd on 2015-05-25
You want x2go.

Run:```

sudo apt-get install software-properties-common
sudo add-apt-repository ppa:x2go/stable
sudo apt-get update
sudo apt-get install x2goserver x2goserver-xsession

```

Install X2GO bindings for LXDE and lubuntu-desktop
```

sudo apt-get install x2golxdebindings lubuntu-desktop
```

Create a user to log into x2go
```

sudo adduser x2gouser
```
Go to your computer and install the X2GO client, and connect to the server with it's ip address

---

