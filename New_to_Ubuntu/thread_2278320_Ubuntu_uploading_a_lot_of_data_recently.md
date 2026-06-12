---
title: "Ubuntu uploading a lot of data recently"
date: 2015-05-15
forum: New to Ubuntu
---

### Post by newbie13 on 2015-05-15
I am on a limited data pack and everyday almost half gb of data is being uploaded. (screenshots attached)

How can I see and control what uses my internet?

---

### Post by howefield on 2015-05-15
Are you transferring files over a local network ?

---

### Post by newbie13 on 2015-05-15
no... I checked everything which might upload files like auto back up or something.. found nothing

---

### Post by Lars Noodén on 2015-05-15
You can see a bit of what is using the net with [netstat](http://manpages.ubuntu.com/manpages/trusty/en/man8/netstat.8.html)

```

netstat -ntup

```

And then [tcpdump](http://manpages.ubuntu.com/manpages/trusty/en/man8/tcpdump.8.html)  will show the live packets.  It can be modified to do all kind of things.  This prints the start and end packets (the SYN and FIN packets) of each TCP connection from eth0:

```

tcpdump -i eth0 'tcp[13] & 3 != 0'

```

If you need a graphical interface to help visualize your data, then [wireshark](https://www.wireshark.org/) is available in the repository via the Software Center or Synaptic.  Below ignores SSH traffic.

```

wireshark -k -i <( sudo tcpdump -lqi eth0 -w - "not port 22" )

```

tcpdump (wireshark) will tell you what ports are causing all the traffic.  netstat will tell you then which program (process) is using that port.

---

### Post by dino99 on 2015-05-15
each browser and music player needs to download/sync/...
some plugins like adblock on browser hardly limit all the sub and redirected links traffic
you can also limit the downloaded packages for ubuntu by deactivated the 'proposed' archive
and check your ports status are 'stealth' and 'closed'  
[http://www.cyberciti.biz/faq/how-do-i-find-out-what-ports-are-listeningopen-on-my-linuxfreebsd-server/](http://www.cyberciti.biz/faq/how-do-i-find-out-what-ports-are-listeningopen-on-my-linuxfreebsd-server/)
[http://askubuntu.com/questions/9368/how-can-i-see-what-ports-are-open-on-my-machine](http://askubuntu.com/questions/9368/how-can-i-see-what-ports-are-open-on-my-machine)

---

### Post by newbie13 on 2015-05-15
@Lars Nooden I tried what you have suggested but couldn't understand what it means.. It does not show what is using the data.

@dino I don't use music player.. Even if I did, look at the difference between download and upload. All I do is surfing on internet for which 100-200 mb shoud be used, which the case indeed. But I don't understand the reason for half gb of upload.


Isn't there any app that shows what used how much data? Like we have data usage in setting in android?

---

### Post by Lars Noodén on 2015-05-15
You can use wireshark+tcpdump or tcpdump by itself to see which ports are sending/receiving the traffic.  Then you can use netstat to see which programs are using that port.  It's a two step lookup, but might be too much info / fun for the occasion.  

The package 'nethogs' gives a lot less information and is thus much clearer.  It will list the programs that are using the network , how much is sent, how much is received, the user, and so on.  So maybe that package is better for your needs.

---

### Post by sandyd on 2015-05-15
```

sudo apt-get install iftop

```

Choose your interface, generally will be either wlan0/eth0/etc depending on how you are connected to the internet. You can show all your interfaces by running
```
ifconfig
```

Once you get your interface name,
```

sudo iftop -i *interface_name_here*
```

It should show you a nice representation of what is transferring data out of your computer.

---

