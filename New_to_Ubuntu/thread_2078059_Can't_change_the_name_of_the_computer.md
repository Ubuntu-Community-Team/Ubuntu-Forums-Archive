---
title: "Can't change the name of the computer"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by mumma on 2012-10-30
I have ubuntu installed on three old laptops and have some experience with it. I just installed ubuntu on a 'new' old laptop and, during installation, I named the computer something I don't want. This is the name the computer will use when talking to other computers.

I searched the forums and did the /etc/hostname and /etc/host changes in the terminal but that didn't work. Instead of changing the name of the computer it simply added the new name to the end of the old name with @ in between.

I don't want to have to reinstall - can someone help me with this?

---

### Post by Cheesemill on 2012-10-30
Can you post your /etc/hostname and /etc/hosts files please.
You must have an error in them as these are the only places your computer name is stored.

---

### Post by dannyboy79 on 2012-10-30
are you sure you're talking about the computer name or the user name?  example at a terminal is
```
daniel@core2duo
```
when you stated, "it simply added the new name to the end of the old name with @ in between." that leads me to believe you want to change the username, no?
post the output of the 2 files as already requested and we'll get ya straightened out.

---

### Post by mumma on 2012-10-30
OK - thanks for the replies.

At the terminal what appears is
mummaohana@mumma

the info from sudo gedit /etc/hosts
127.0.0.1    localhost
127.0.1.1    mumma

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

the info from sudo gedit /etc/hostname 
mumma


initially my computer name was mummaohana - this is what I selected when I installeld. I tried to change it to mumma but instead got the new longer mummaohana@mumma

I'd like it to just be mumma

---

### Post by deadflowr on 2012-10-30
The longer name is the user plus the computer name. The name you gave it, mumma, is in fact the computer name.
In the terminal it lists the user and the computer being used.
What it says is this user is at this computer. mummaohana@mumma.
If you create another user for your system, and login to that user, while using the terminal, that username will show added to the name, such as newuser@machinename.

---

### Post by dannyboy79 on 2012-10-30
just as I suspected, everything looks correct. if you want it to be
mummao@mumma
you need to create a new user with that name as deadflowr said.

---

### Post by mumma on 2012-10-30
Ahh - I think I understand.

Thank you for the replies.

---

