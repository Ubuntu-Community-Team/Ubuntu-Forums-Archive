---
title: "How to log in to Ubuntu desktop"
date: 2017-02-10
forum: New to Ubuntu
---

### Post by ipoppy on 2017-02-10
Hi There,
I wonder if someone could point me in the right direction with following problem. Please do understand that I have no absolutely knowledge about Linux and I am taking this as a starting point, so I do apologize for daft question and lack of basics.
I have bought VPS service and I choose OpenVz package with Ubuntu. What I want to do is eventually open Ubuntu desktop, run Wine environment and install MT4. However it seems quite difficult to achieve it for me.
So far I managed to open terminal through Putty and I have logged in with login and password. Then I could run few commands but to be honest I am not sure if I am doing right thing to even try it to run any commands incase if I will enable something which I should not. I have seen few videos to enable desktop in Ubuntu but does not apply to what I am doing. I was even trying to log to desktop through VNC Viewer but of course I have failed.
So is there anyone out there to give me pointers of how to configure OpenVz to run Ubuntu latest version and access finally Ubuntu desktop.
Apart from installing MT4 for obvious reasons I want to learn Ubuntu as I am fed up Windows environment.
Thanks in advance.

---

### Post by HermanAB on 2017-02-10
Well, you won't run a desktop on a remote Linux/UNIX server - it doesn't have a screen, keyboard or rodent attached to it as there is nobody there to use it.  A desktop is for the local machine, then you can connect to the server over ssh or a web server interface, not VNC.

---

