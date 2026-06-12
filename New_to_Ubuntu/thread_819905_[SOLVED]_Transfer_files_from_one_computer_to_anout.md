---
title: "[SOLVED] Transfer files from one computer to anouther?"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Sabar on 2008-06-05
Hello every one. I am trying to figure out if it is possible to transfer files from one computer running 7.10 to another computer running Hardy over an either net cable?

     Basically I am trying to transfer my music collection from one computer to another and I don't want to have to run 400+ CD's thrue the CD drive.

     Any help would be well appreciated. Oh both computers are connected to different cables on the same DSL Modem. I was actually thinking of just running the either net cable from one computer to another but it would be ok to if they could find one another as is.

Thank you 
Sabar

---

### Post by wpshooter on 2008-06-05
Have you tried installing SAMBA and see if that would allow you to do this.

I know SAMBA will allow you to see the contents of each computer from the other but I am not sure if you can transfer between the two using this method.  It has been a while since I have played around with this, maybe I should go back and try this when I get some time to play around with it.

Maybe someone else can give you a more definitive answer about SAMBA capabilities.  Or maybe you can just google SAMBA and read up on it.

Good luck.

---

### Post by drs305 on 2008-06-05
I just reread your post. I was thinking router but you are talking about a modem. So none of this post may apply but I'll leave it anyway.

I would think you can do this with SSH. You are talking about 2 computers connected to a common router, correct? The programs are actually openssh-client and openssh-server, but you can install them both via synaptic. The package is simply called ssh, or you can do it from the command line:
```
sudo aptitude install ssh
```

Both versions of ubuntu can run this with no problem. Once you have them installed, click on the connect to server icon (Places, Connect to Server), enter the IP address and username of the other computer and (hopefully) they will talk to each other. On first contact, you will receive a security message stating that your computer doesn't recognize the other computer. That is normal.

---

### Post by aeiah on 2008-06-05
no point installing samba, just use NFS, it'll be less hastle. samba is for if you have windows machines in your network. nfs is native.

have a look here:
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

you should set your older pc with your music as the server. when you've finished setting it up and mounted the location you want, just navigate to it and drag them over to their new location.

---

### Post by wpshooter on 2008-06-05
P.S. - SAMBA is found in Synaptic also.

---

### Post by walker9010 on 2008-06-05
depending on the computers, you may need a crossover cable

see [http://en.wikipedia.org/wiki/Ethernet_crossover_cable]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable")

---

### Post by AndyCee on 2008-06-05
I agree with walker9010.

If your modem also functions as a router (it would say explicitly on the box/manual if it does), you may be able to easily set up a network and copy files across. That's what I've got set up at home, but as my notebook dual-boots with Vista I use samba.

If your modem doesn't function as a router, connecting the two with a crossover cable should work as aeiah pointed out. While I have heard of a direct connection working with a normal cable, I've yet to see it happen.

At any point, to check for other locations in your network go to the "Places->Network" menu.

I can't see the benefit of using SSH in this situation, but if anyone knows otherwise feel free to teach me something new.

---

### Post by drs305 on 2008-06-05
> **AndyCee said:**
> I can't see the benefit of using SSH in this situation, but if anyone knows otherwise feel free to teach me something new.

On every install I've done I:
1. Install SSH
2. Go to Network, SSH, enter the IP and other computer's name.
3. Acknowlege the unknown computer message.
4. Enter the other computers password
5. Use nautilus.

It seems as simple as anything else to me, maybe I've forgotten some aggravating steps...

---

### Post by Sabar on 2008-06-05
currently I am using the terminal to download the SSH program.  and I am hoping to follow the instructions given by drs305.  I only wonder about one thing you said > 5. Use nautilus.   What is Nautilus?

Thanks every one hoping to make this work for me
Sabar

---

### Post by DGortze380 on 2008-06-05
I would just set up an ad hoc with a cross-over cable...
After that ssh is probably the easiest.

---

### Post by drs305 on 2008-06-05
> **Sabar said:**
> What is Nautilus?

Thanks every one hoping to make this work for me
Sabar

Nautilus is the ubuntu file manager, like windows explorer. You should be able to use any file manager and the other computer will probably be listed by it's IP number, e.g. 192.168.0.3

---

### Post by Sabar on 2008-06-05
ok I used the terminal to download SSH this is the last few lines in terminal so I think it is done

> Setting up ssh (1:4.7p1-8ubuntu1.2) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done   

ok so where do I find in my computer to open it? under system?

---

### Post by drs305 on 2008-06-05
Let me back up on these instructions. Are both computers connected to a router, which connects to the modem? That is the assumption I am making.  


First, you have to download and install SSH on both machines. Once you have it installed on both, on one of them open SSH. You do this by going to Places, Connect to Server. 
At the top, Server Type: select SSH.
Server: the IP address of the other computer.
To get this, if you don't know it, on the other computer, in a terminal type: 
```
ifconfig | grep "inet"  
```
It should be something like: 192.168.0.3  (it isn't the one that says 127.0.1.1 )
Type that number in the server address.
In the user name, type the username of the other computer.
Then click on the connect button.

If everything goes ok, you will get a warning message saying your computer doesn't recognize the other computer. Just acknowledge or OK or whatever it asks.

Next you will have to enter the password of the other computer.
It should now connect.

Open nautilus or your file browser. In the left pane you should see the other computer.

.

---

### Post by Sabar on 2008-06-05
My modem is an Actiontec 54mbps wireless DSL gateway. It has 4 wired connections and wireless. both computer are connected to this thing I think it also works as a router. IN all this I could be wrong and may want to figure out how to uninstall SSH :( 

I do not know if this information will help on weather I can do this or not.
Sabar

---

### Post by drs305 on 2008-06-05
Do you have IM capability with gmail or yahoo? If so, I sent you a Private Message.

First, let's make sure you don't already have a network connection. Go to Places and click on Network and see if any networks are listed. If there is one with either or your computers name on it double click and see if it opens.

---

### Post by Sabar on 2008-06-05
I think it is working! Thank you everyone who replied to my posts. A Screen popped up of the folders in my other computer I went to the file I wanted and hit copy, then went to the folder in this computer I wanted it in and hit paste looks like things are coping now!

Thank you so much every one

Sabar

---

### Post by Victormd on 2008-06-05
> **Sabar said:**
> My modem is an Actiontec 54mbps wireless DSL gateway. It has 4 wired connections and wireless. both computer are connected to this thing I think it also works as a router.

If they're both connected, you should be able to "see" the computers opening PLACES>NETWORK

To transfer the files, you'll have to setup file sharing but it should be very simple. A way to check if your computers can communicate is opening a terminal and using the ping command
i.e.
```
ping 192.168.0.3
```
assuming 192.168.0.3 is the IP for the other computer... and you should get several lines like this
> 64 bytes from 192.168.0.3: icmp_seq=1 ttl=128 time=0.83 ms
If you get something like this
> From 192.168.0.3 icmp_seq=1 Destination Host Unreachable
then you'll need to do some tweaking...

EDIT: Ok, just saw that you got it... :)

---

### Post by drs305 on 2008-06-05
> **Sabar said:**
> I think it is working! Thank you everyone who replied to my posts. 
Sabar

When you have time from copying, would you please mark this thread solved? At the top right of the original post is a link with "Thread Tools". Click on that and there is an option to 'Mark thread as solved'.

Congratulations!  ;-)

---

