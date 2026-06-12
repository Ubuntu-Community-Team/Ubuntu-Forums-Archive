---
title: "Samba config tool and Installing x server"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Technofear on 2008-10-09
Hi

I am trying to run the Samba config tool, and am getting this error in the .xsessions-error file. 

system-config-samba requires a currently running X server.

I have tried to install x server using 'apt-get install x-window-system-core' but I get an error telling me this is a virtual package.

My question's are...
Do I need x server to run the samba config tool?
If so, how do I ascertain the status of x server? 
If it's not  there, how do I install it?

---

### Post by hyper_ch on 2008-10-09
you could use SWAT install, that will require a webbrowser to be installed and root to be enabled. Btw, xserver should be installed with
```

sudo apt-get install xserver-xorg

```

---

### Post by Technofear on 2008-10-09
tried to install x-server and package says it's already up to date. So will look at SWAT route

Thanks

---

