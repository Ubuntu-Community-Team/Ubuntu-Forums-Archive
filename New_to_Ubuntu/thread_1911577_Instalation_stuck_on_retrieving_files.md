---
title: "Instalation stuck on retrieving files"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by kaloasd on 2012-01-19
As I was installing Ubuntu 11.10 it got stuck on retrieving files 55 of 117 so I decided to pull the internet cable to see if anything would happen. The instalation continued and it seems to work fine for now.

Can anyone tell me how bad I've messed up and how to fix whatever is wrong

---

### Post by jerrrys on 2012-01-20
Open a terminal and enter:

sudo apt-get update

followed by:

sudo apt-get upgrade

Get any errors?  If not, you lucked out.

Also if it offers you a partial upgrade; don't do it.  That can turn into a can of worms.

---

