---
title: "logging into ubuntu(unity) 12.10"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-10-20
when i try all i get is desktop background no icons or toolbars. worked fine in the rc. xubuntu,xfce,gnome3,classic, and classic no effect all work great though.

---

### Post by robtygart on 2012-10-20
Did this happen after installing a graphic driver? 

Last night I had Ubuntu 12.10 installed, after installing (any) Nvidia driver, after loging in I had only a background with right click. 

I went to Kubuntu 12.10, and it works fine now.. (Thats what I was going for but I goofed up and downloaded ubuntu :oops:)

---

### Post by rburkartjo on 2012-10-20
rob no it just happened in the updates after the rc. at a loss dont like unity but still would like to be able to use if i want.

---

### Post by robtygart on 2012-10-20
Ok, thought it might have been linked, I did not give it a chance.

---

### Post by Frogs Hair on 2012-10-20
Try  Ctrl + Alt + T```
 setsid unity
```

No Terminal

Login to Ubuntu use Ctrl + Alt + F1 to enter TTY. Next enter user name, password, and run the following command.```
setsid unity
```

Wait until the process is complete and your user name appears again. Use Ctrl + Alt + F7 to renter the desktop environment.

If there is error reporting wait until finished. If Unity doesn't appear within a minute or two restart and login to Ubuntu.

---

### Post by rburkartjo on 2012-10-20
frog should i first log into unity and then run the commands from tt1 note i have gnome-do so i can still load any program i want. so i can access this thread when in unity. you have helped me before tks

---

### Post by cagilla on 2012-10-20
If this does not work for you - check out this thread:  <snip> it worked for me.

---

### Post by Frogs Hair on 2012-10-20
> **rburkartjo said:**
> frog should i first log into unity and then run the commands from tt1 note i have gnome-do so i can still load any program i want. so i can access this thread when in unity. you have helped me before tks

Run the command from the Gnome terminal if you have access . It is just the new unity reset command.

---

### Post by rburkartjo on 2012-10-21
tks frog give it a try

---

### Post by rburkartjo on 2012-10-21
frog fyi if i run the unity reset command from the terminal while in xubuntu it will switch me to a unity session. if i log into a unity session i still get just the desktop until i open a terminal and use the reset command. i googled this problem before i started this thread and i wasnt the only having this problem. a nice work around until a fix is found. note i get a ton of error from the terminal after i run the reset command but at least unity loads./tks

---

### Post by Frogs Hair on 2012-10-21
I am only using the XFCE session as a shell added to my Ubuntu installation which is quite different from running Xubutnu and I know  commands vary . I'm glad you found a way yo use Unity if you want.

---

### Post by rburkartjo on 2012-10-21
sure hope this problem is solved with some further updates. note it is do to ubuntu 12.10 unity fall back settings for old unity 2-d users not working correctly.

---

