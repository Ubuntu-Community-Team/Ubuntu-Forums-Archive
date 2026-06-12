---
title: "Help with desktop panel"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by Tazmman on 2012-02-07
Hello, I've been in the Ubuntu help center, Trying to figure out how to get different applet on my panels. Specificity one to disconnect my computer from the it's network.  While we're at. my Update manager has not worked properly form so time now, And I believe it's  compromised my system. Help would greatly be appreciated. If there is a more appropriate place to post this please let me know.  thanks.

---

### Post by jerrrys on 2012-02-08
Open a terminal and enter:

sudo apt-get update

That has a tendency to fix update manager.

---

### Post by Gremlinzzz on 2012-02-08
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo apt-get autoclean
sudo apt-get autoremove

:popcorn:

---

### Post by grahammechanical on 2012-02-08
It helps if you tell us the version of Ubuntu that you are using. Have you tried clicking on the network icon and selecting Disconnect or removing the tick mark against the line Enable Networking by clicking on that line? You will find that there is already an applet on the panel to do what you want. Unless you have somehow removed it.

Regards

---

### Post by Tazmman on 2012-02-13
Thank you for the the updater help

---

### Post by Tazmman on 2012-02-13
Now if I a can revolve the network connection/disconnect issue that would be great. I'm using 10.04

---

### Post by winh8r on 2012-02-13
Go to Synaptic package manager

search for  network-manager-gnome

select for installation 

click apply

network manager icon will appear in panel

---

### Post by Tazmman on 2012-02-25
Thanks for the help problem solved:)

---

