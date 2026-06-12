---
title: "[SOLVED] gui screen on startup really confused!"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by hasp on 2008-11-23
hi
i just installed ubuntu 8.04 using unetbootin
I turn on my computer and select ubuntu on grup ( i am dual booting linux and windows)
I get too a terminal like screen like cmd on windows
I login but I can't get to my desktop
startx doesn't work 
Im a total noob so I have no idea what im doing really
any help would be appreciated
thanks

---

### Post by DGortze380 on 2008-11-23
> **hasp said:**
> hi
i just installed ubuntu 8.04 using unetbootin
I turn on my computer and select ubuntu on grup ( i am dual booting linux and windows)
I get too a terminal like screen like cmd on windows
I login but I can't get to my desktop
startx doesn't work 
Im a total noob so I have no idea what im doing really
any help would be appreciated
thanks

post the output of 
cat /etc/X11/xorg.conf

What kind of computer are you using?
Did the live CD work ok?

Try these two in order:

sudo pkill gdm
sudo gdm

---

### Post by hasp on 2008-11-23
> **DGortze380 said:**
> post the output of 
cat /etc/X11/xorg.conf

What kind of computer are you using?
Did the live CD work ok?

Try these two in order:

sudo pkill gdm
sudo gdm

 will do but what do you mean by did the live cd work ok
i used netbootin so isn't that a usb start?
sorry if its a really newbie question

---

### Post by hasp on 2008-11-23
cat /etc/x11/xorg.conf 
i get no such file or directory

sudo pkill gdm
I have to enter my password
after nothing comes up on the screen
then i enter sudo gdm and i get command not found

thanks for all your help so far

---

### Post by hasp on 2008-11-23
also if i type in startx i get
 [B][I]fatal server error
No valid fontpath could be found
giving up
xinit connection reset by peer (errorno 104)unable to connect to xserver
xinit no such process (errno3) server error
xauth: error in locking authorityfile /home /user /.xauthority[/I][/B]
i hope this helps
thanks in advance

---

### Post by DGortze380 on 2008-11-23
> **hasp said:**
> 
cat /etc/x11/xorg.conf 
i get no such file or directory


it's:
cat /etc/X11/xorg.conf

not x11

> 
sudo pkill gdm
I have to enter my password
after nothing comes up on the screen


normal

> 
then i enter sudo gdm and i get command not found


That's odd. Try, in order (fist command will take a while and needs an internet connection):

sudo apt-get install ubuntu-desktop

sudo gdm



post any output

---

### Post by hasp on 2008-11-24
> **DGortze380 said:**
> 

That's odd. Try, in order (fist command will take a while and needs an internet connection):

sudo apt-get install ubuntu-desktop

sudo gdm

post any output

Done and it works 
Thanks a lot I was getting really desperate!!:):)

still need me to post reply to cat /etc/X11/xorg.conf?

---

### Post by DGortze380 on 2008-11-24
> **hasp said:**
> Done and it works 
Thanks a lot I was getting really desperate!!:):)

still need me to post reply to cat /etc/X11/xorg.conf?

nope, not if everything's working.

Happy Ubuntu-ing

---

