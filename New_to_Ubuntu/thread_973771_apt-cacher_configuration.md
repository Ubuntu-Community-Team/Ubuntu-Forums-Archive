---
title: "apt-cacher configuration"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by everest on 2008-11-07
Hi everyone out there,
We are a small office of 3 pcs and we wanted to setup a central repository to limit our download from the internet. So we decided to install apt-cacher, so to start I have installed apt-cacher on my pc which is running ubuntu hardy and apt-cacher is up and running, this is no problem. When I did ran sudo apt-get update in the shell on my collegue's pc in our office it shows "w: failed to fetch, 500 configuration error. Could it be some settings on the client side that has to be made? To my feeling I followed the instructions given in the website but its giving me this error message, anyone out there who can help me solve this problem, I would greatly appreciate your input. Nandri

---

### Post by mapes12 on 2008-11-07
Not a perfect solution but if you can't get apt-cacher to work then try System>Administration> Synaptic Package Manger and search for aptoncd

The home page is here: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

You could setup one client exactly how you want it then use a CD to load the packages to the other 2 client machines. Clearly, you would only acess the internet once for your packages but the downside is that you would be using a CD, not your network. But if you only have 3 PC's it shouldn't take too long to deploy.

---

