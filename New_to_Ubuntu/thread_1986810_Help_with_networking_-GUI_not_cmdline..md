---
title: "Help with networking -GUI not cmdline."
date: 2012-05-25
forum: New to Ubuntu
---

### Post by Brian_new_to_linux on 2012-05-25
Good evening gentlefolk of the free world!

Although I have been using Ubuntu since 10.10 netbook (the first with my beloved Unity interface) I have never used the command line. This is partly on principle- I consider my self an open source advocate for people kept offline by cost- but also I will admit to being really, really lazy! I now have four machines all running 12.04LTS.  Two basic desktop PCs (1Gb ddr, HDD of 40/80GB, a decrepit Dell laptop (512Mb ddr) and the netbook (Acer aspire One with 1Gb +120HDD) Without using the command line at all - How to I share all resources across all of these machines, including external drive I use for backups and two printers?
Is Samba the answer? if so where do I find a guide based on GUI not sudo commands?

Thank you all muchly, in advance.

BM

---

### Post by nothingspecial on 2012-05-25
Install openssh-server on all of them. From the nautilus menu go file > connect to server

In the server box put the ip address of the other machine, to find this out go to it and right click the wireless icon and look at connection information.

In the type box choose ssh

Choose whatever folder you like, / will be fine

Click connect and type the password in.

Rinse and repeat for the other 2 computers and then on to the next one to do the same for the other 3, and so on and so on

For, printing hit the super key and find the printing app on the machines with the printers. In the menu choose server > settings

check/tick both "show printers shared by other systems" and "publish printers connected to this system"

On the machines with no printers just check/tick "show printers connected to this system"

That's it

---

### Post by Brian_new_to_linux on 2012-05-28
> **nothingspecial said:**
> Install openssh-server on all of them. From the nautilus menu go file > connect to server

In the server box put the ip address of the other machine, to find this out go to it and right click the wireless icon and look at connection information.

In the type box choose ssh

Choose whatever folder you like, / will be fine

Click connect and type the password in.

Rinse and repeat for the other 2 computers and then on to the next one to do the same for the other 3, and so on and so on

For, printing hit the super key and find the printing app on the machines with the printers. In the menu choose server > settings

check/tick both "show printers shared by other systems" and "publish printers connected to this system"

On the machines with no printers just check/tick "show printers connected to this system"

That's it

Thank you 

I am busy with other things at the moment but I will try this very soon.  I am confident it will work - thank you very much, you are a gentleman & a scholar!
Brian

---

### Post by Dave_in_MD on 2012-05-28
> **Brian_new_to_linux said:**
> Good evening gentlefolk of the free world!

  How to I share all resources across all of these machines, including external drive I use for backups and two printers?
Is Samba the answer? if so where do I find a guide based on GUI not sudo commands?

Thank you all muchly, in advance.

BM
Someone else here wrote a very clear step by step While written for 10.10 it works for 12.04 just the screen shots don't match. 
[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by Brian_new_to_linux on 2012-05-30
Thanks for the previous posts.  I have no Windows PC so the guide is not relevant.  I have followed the steps today from "nothingspecial" but I get the connection refused at password- what am I doing wrong?

---

### Post by Brian_new_to_linux on 2012-05-30
.... I have tried the username and password of the machine I am accessing from and the remote one I want to open and every combination of these-is there some other password I should know about?

---

### Post by Brian_new_to_linux on 2012-05-30
Can I just clarify again I do not want to share resources with Windows but to network 4(+) Ubuntu PCs. I am a loss to understand why this is so  difficult to do within a GUI environment.

---

### Post by nothingspecial on 2012-05-30
Did you install openssh-server on all your machines?

---

### Post by Cheesemill on 2012-05-30
You can always just right-click on the folder you wish to share and click on Sharing Options :)

---

### Post by Brian_new_to_linux on 2012-05-30
Yes I did install openssh-server on all 4 machines, but right clicking to share demands that I install SAMBA to share with a Windows network I do not have. 
I am sorry it took me so long to get back to this but I am a full time carer for my wife (Parkinson's) so I only really have Wednesday to myself. 
Is there some other password or application I need to use?  I still cant' see why this is so complicated, as I only want to share the resources of four machines all connected to the same router (three wired, one wireless) and all running the same version of the same OS!

---

### Post by Cheesemill on 2012-05-30
> **Brian_new_to_linux said:**
> Yes I did install openssh-server on all 4 machines, but right clicking to share demands that I install SAMBA to share with a Windows network I do not have. 
You can use Samba to share between Ubuntu machines as well, it's not just for Windows boxes.

---

### Post by Brian_new_to_linux on 2012-05-30
OK I may be helpful if go though what I have done so far and where it all stops. 

I have  installed openssh-server on each of the machines from the software centre. I have found the IP address of each of the machines from the home network page of my routers gateway web page and made sure that each is set to a static IP address. 

Next I returned to the main office desktop and went to File>connect to server, changed the drop down to SSH entered the first IP address  and the username/password of a remote machine to connect to.  Connection is refused.  I have tried all combinations of password/machine name and username without success. 

Is there a default password for SSH? Should I be using the router set up password? 

To be clear I do not want to connect to a Windows network or add Windows PCS to a network, just network four Ubuntu PCS together.

---

### Post by nothingspecial on 2012-05-30
Something is wrong.

I have done this a bazillion times on many many different machines using the steps you describe.

Have you enabled your firewalls?

Can you think of any time you may have altered your ssh configuration for anything? Have you followed any security tutorials for example?

Can you try connecting 2 different computers from the four.

It is also possible that I have overlooked something, but I can't see it.

---

### Post by Brian_new_to_linux on 2012-05-30
Just to be sure- I don't need to install anything else but openssh-server?

---

### Post by Zill on 2012-05-30
> **Brian_new_to_linux said:**
> ...I have found the IP address of each of the machines from the home network page of my routers gateway web page and made sure that each is set to a static IP address...
Can each machine "ping" each other with each IP address?  eg.
```
ping 192.168.0.x
```

---

### Post by nothingspecial on 2012-05-30
> **Brian_new_to_linux said:**
> Just to be sure- I don't need to install anything else but openssh-server?

As long as you haven't removed any of the packages that come with ubuntu. openssh-client is installed by default along with the gvfs stuff that let's you connect with nautilus.

---

### Post by gordintoronto on 2012-05-30
It's possible your router is blocking the connection.

I also suggest installing Samba. Most people just want to have a shared folder and shared printer(s), and you can do that entirely with Samba, in a pure Linux environment. And you can do it all from the GUI.

---

