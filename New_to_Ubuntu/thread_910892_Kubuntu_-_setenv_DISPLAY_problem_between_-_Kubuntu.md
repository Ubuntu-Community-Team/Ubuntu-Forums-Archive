---
title: "Kubuntu - setenv DISPLAY problem between - Kubuntu and Ubuntu Machines"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by crsmds on 2008-09-05
Hi,

**_[U]1st Query_[/U]**

I am using kubuntu 8.04 Hardy version and when i try to open any of files from root login (through terminal), i am getting an error message, for example:

When I try to open /etc/ssh/ssh_config 

No protocol specified
Display :0.0 unavailable, simulating -nw

Can anybody suggest me what could be the problem? and how to resolve.

**II Query**

My second query is, I have a ubuntu 7.10 desktop next to me, to which i would like to have a "xhost" ssh connection from my kubuntu PC. Here also, i am not able to "setenv DISPLAY my_pc_ip_address:0.0 and see the xsession of ubuntu in my machine.

Anybody can give me a solution for the above two in a step by step manner, Thanks a lot in advance, i am totally new to this OS.

Rgds,
CRS.

---

### Post by Presto123 on 2008-09-05
I can maybe help on the 1st question...

Try typing in:
```
sudo kate /etc/ssh/ssh_config
```

2nd question...I don't know.

---

### Post by crsmds on 2008-09-09
Hi,

1st Query

I am using kubuntu 8.04 Hardy version and when i try to open any of files from root login (through terminal), i am getting an error message, for example:

When I try to open /etc/ssh/ssh_config

No protocol specified
Display :0.0 unavailable, simulating -nw

Can anybody suggest me what could be the problem? and how to resolve.

II Query

My second query is, I have a ubuntu 7.10 desktop next to me, to which i would like to have a "xhost" ssh connection from my kubuntu PC. Here also, i am not able to "setenv DISPLAY my_pc_ip_address:0.0 and see the xsession of ubuntu in my machine.

Anybody can give me a solution for the above two in a step by step manner, Thanks a lot in advance, i am totally new to this OS.

Rgds,
CRS.
crsmds is online now   	Reply With Quote

---

