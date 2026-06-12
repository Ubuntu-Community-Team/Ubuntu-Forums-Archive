---
title: "No write permissions on home dir in Ocelot"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by mebigfatguy on 2011-11-17
I upgraded to 11.10, and now when i do 

gedit /home/dave/foo.txt, or 
javac

or whatever on a file in my home directory it fails with permission errors. If i do 

sudo gedit
sudo javac

it works fine.

i tried

sudo chown dave:dave /home/dave/

but that did nothing


ideas?

---

### Post by gordintoronto on 2011-11-17
I don't think you got the format of the chown command right. Try CD to your home folder, then
sudo chown -R dave dave

where the first dave is your username, and the second dave is the folder name. The -R (recursive) tells it change everything under the folder dave.

---

### Post by mebigfatguy on 2011-11-18
thanks, that fixed it.

---

