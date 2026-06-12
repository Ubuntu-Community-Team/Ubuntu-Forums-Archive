---
title: "copy past not working vncviewer"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by fachhoch on 2012-10-16
I a  connection to ubunut from windows using realvnc viewer.

Copy paste from windows to ubunut is not working .
To trouble shoot I tried commands on ubunutu

vncconfig

I get 
No VNC extension on display :0

Please advice what needs to be fixed on vncserver.

---

### Post by daslinkard on 2012-10-17
Open the VNC Viewer **Properties** dialog and, on the **Inputs tab**, turn on **Share clipboard with VNC Server**.

Or you can try to connect using **vncviewer** and run **vncconfig** within the remote window, check the options regarding the clipboard and then try to paste.

 [IMG]http://i.stack.imgur.com/a0HJn.jpg[/IMG]

---

