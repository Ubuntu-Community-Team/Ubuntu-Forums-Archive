---
title: "ssh: connect to host 192.168.110.1 port 22: Connection refused"
date: 2019-04-15
forum: New to Ubuntu
---

### Post by torbentf on 2019-04-15
Hi,
I have lost track of my questions to Ubuntu Forum, so I have to repeat (I think) my question.

I have followed the following:

[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04)
[https://help.ubuntu.com/lts/serverguide/openssh-server.html.en](https://help.ubuntu.com/lts/serverguide/openssh-server.html.en)


In have inactivated fire wall, and done:
sudo apt-get remove openssh-client openssh-server
sudo apt-get install openssh-client openssh-server

but I keep getting:

torben@torben-Aspire-E5-773G:~$ ssh -L 5901:127.0.0.1:5901 -C -N -l torben 192.168.110.1
ssh: connect to host 192.168.110.1 port 22: Connection refused

Can anyone explain?
torben

---

### Post by torbentf on 2019-04-15
Hi,
Should'nt this show channel 22?

```

torben@torben-Aspire-E5-773G:~$ ss -altnp | perl -ne '@_=split;printf"%-20s %s\n",@_[2,4]'
Send-Q               Address:Port
5                    0.0.0.0:*
128                  0.0.0.0:*
5                    0.0.0.0:*
128                  0.0.0.0:*
128                  0.0.0.0:*
128                  0.0.0.0:*
5                    0.0.0.0:*
128                  [::]:*
5                    [::]:*

```
torben

---

