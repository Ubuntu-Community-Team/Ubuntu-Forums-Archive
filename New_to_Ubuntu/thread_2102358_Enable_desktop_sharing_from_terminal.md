---
title: "Enable desktop sharing from terminal?"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by g0nz0uk on 2013-01-07
Hello,

I have a remote Ubuntu PC that I need desktop sharing enabled on and on from the logon screen, can this be done from SSH as I can access it this way?

Thanks

---

### Post by slickymaster on 2013-01-07
There are several ways to access a remote machine. You can choose from a command-line remote access, using [OpenSSH]("https://help.ubuntu.com/community/SSH") on the server and use ssh command on the client, or you can have a graphical remote access using software like [Team Viewer]("http://www.teamviewer.com/en/index.aspx?cdsplit=C").

Take a look at this [post]("http://askubuntu.com/questions/25189/remote-login-with-graphical-display-manager-gdm-lightdm/25192#25192") for secure ssh transmission viewing the login screen.

---

### Post by Rocklobster690 on 2013-01-07
Take a look at NX - [http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by SlugSlug on 2013-01-07
I do this via

```
ssh -R 5901:localhost:5900 my.server.com
```

then on my.server.com

```
sudo apt-get install x11vnc
x11vnc
```


then from client machine open remote desktop and VNC to localhost

---

