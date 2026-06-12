---
title: "VMware for MySQL &amp; C#"
date: 2007-03-06
forum: Programming Talk
---

### Post by HighD on 2007-03-06
Ok so here's my situation:

I am currently an IT student. I'm  designing a basic database model, soon to be implemented in MySQL 5.1(beta) on a linux platform  (Ubuntu of course). I have various language options for the GUI, one of them being C#, which is the one I really want to use together with MySQL.

What I want to do is use a virtual machine (vmware) so I can use Visual C# , design the GUI and other things and connect through ADO.NET to my linux MySQL database. Is this possible?

If it is, is there any special configuration I need on my virtual machine so I can connect directly Visual C# and the linux MySQL database?

Please ask as much as you want if you have any doubts.

Thanks in advance for your answers!

---

### Post by lnostdal on 2007-03-06
of course you can do that .. but have you considered using mono instead? when you compile something using mono (mcs) the binary will run on both linux (Mono-runtime) and windows (.Net-runtime)

for GUI you can use gtk-sharp and glade (version 3.x is recommended) .. (here are some screenshots: [http://www.mono-project.com/Screenshots](http://www.mono-project.com/Screenshots) )

to answer your second question every virtual machine gets its own ip on a private subnet so your vm's can communicate with your host, between themselves and also with other machines and the internet .. no special configuration is needed

---

### Post by HighD on 2007-03-06
> **lnostdal said:**
> of course you can do that .. but have you considered using mono instead? when you compile something using mono (mcs) the binary will run on both linux (Mono-runtime) and windows (.Net-runtime)

No doubt Mono is a great implementation of the .NET platform for linux, it will become stronger as time passes but currently it's just not an option for me. I may try it soon!.

> 
to answer your second question every virtual machine gets its own ip on a private subnet so your vm's can communicate with your host, between themselves and also with other machines and the internet .. no special configuration is needed


Thanks! So no special config is needed! I was just creating a VM and saw a couple of questions regarding the network connection, to choose from bridge-networking, use NAT, or host-only networking. So none of these choices affect my capability to connect MySQL with C#?

---

