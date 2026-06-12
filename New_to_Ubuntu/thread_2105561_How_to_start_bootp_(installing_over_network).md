---
title: "How to start bootp (installing over network)"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by zcacogp on 2013-01-16
Hello, 

I'm trying to install mint Linux across a network, to an old laptop which will boot from the network card. I have a machine running Ubuntu 12.10 to use as the server. 

There are various guides around, all of which are a little bit different, but I am using this one: 

[https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)

I am confused by the line "Start bootp: Here is a wrapper to start and stop bootpd from the command line" - this is followed by a number of lines of code. 

If bootp is a service, why can't it be started with "sudo service bootp restart"? (It can't - I've tried). And I don't understand what the significance of the code is - it looks like it should be saved into a file somewhere, but that's all I can understand. 

Another question concerns the use of a DHCP server. I understand a DHCP server as being something that hands out IP addresses on a network, and my broadband router does this for me. Some of the network installation guides give instructions to set up a DHCP server on your computer. Why would you need to do this, particualrly given that haing two such servers on a network will cause confusion? 

All help welcomed - thanks in advance. 


Oli

---

### Post by Sakrecoer on 2013-09-02
Hi!

Now, i'm not an expert in this, but i have been looking arround alot probably for a similar reason to yours.

Hopefully by now you know your answer, however for futur searchers, this is how i used the "wrapper".

I created i file called bootp in the init.d directory
```
sudo editor /etc/initi.d/bootp
```

in this file i pasted the "wrapper" code. 

then i gave it the proper persmissions:

```
sudo chmod 755 /etc/init.d/bootp
```

now, if i type 

```
sudo /etc/init.d/bootp restart
```

it restarts. 

Hope this helps someone.

---

