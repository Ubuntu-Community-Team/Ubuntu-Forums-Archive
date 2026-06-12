---
title: "Unable to open Ubuntu's IP Address in Chrome or FireFox"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by melriz on 2013-05-17
First off I apologize if I'm asking the most basic question or if I'm not very coherent.  I am soo new to Ubuntu, Linux, and developing in general that it's pitiful. I'm am ever so grateful to anyone who takes the time to respond.

**Background**
Our business has a website and has previously developed a test store through Ubuntu and I'm learning how to modify files and test them in Ubuntu before changes are made on the live store. A few days ago, as I was learning the [very] basics, we could type in the [http://192.xxx.xxx.xxx](http://192.xxx.xxx.xxx) and the test website would open or [http://192.xxx.xxx.xxx/foldername/filename.php](http://192.xxx.xxx.xxx/foldername/filename.php) and it would open that file. Now I type in the same things (I've even click from browsing history to verify the url) and I get error messages (Problem loading page) in both Chrome and Firefox.

**What I've Tried**
1. suda nano /etc/network/interfaces to verify the system's IP Address:
iface eh0 inet static
address 192.xxx.xxx.xxx (This is the addess I've used to pull up test store)
netmask 255.255.255.0
network 192.xxx.xxx.xxx
broadcast 192.xxx.xxx.xxx (This one is different than address)
gateway 192.xxx.xxx.xxx 

2.wget -p [http://IPaddress](http://IPaddress)
failed: No route to host

but other sites like google.com worked

3. Other websites are loading in both chrome and Firefox (host and guest). So I don't think it's a problem with our internet connection.


Can someone help?

---

### Post by miegiel on 2013-05-17
> **melriz said:**
> address 192.xxx.xxx.xxx (This is the addess I've used to pull up test store)
That's the ip number you want to use.
> broadcast 192.xxx.xxx.xxx (This one is different than address)
I'll spare you the details but this is a special address for networking purposes. You don't want to use this one.

Make sure the web server on your machine is up and running, it probably doesn't startup automatically when you boot up. It seems the browser is just not finding a web server at your address.

---

### Post by x C0MMAND0 x on 2013-05-17
1 - Is the website data hosted on the machine you are on locally?  If so, you can just browse to the files and access them directly, without having to worry about an IP address.

2 - Because you said you were previously accessing the website via a 192.xxx.xxx.xxx subnet, that tells me it is internal not external.  Is the website hosted on a separate computer?

3 - run ```
ifconfig -a
``` on your computer you are trying to access the website from, and again on the computer the website is hosted on (if it is different) and post the results here.

I don't fully understand everything you said/asked, so these are just some general questions to help clarify and get us in the right direction.

---

### Post by grahammechanical on 2013-05-17
What do you mean by [COLOR=#000000] > developed a test store through Ubuntu[/COLOR]

Are you storing the files on Ubuntu One? Are you trying to use Ubuntu One to host a web site? Are you saying that you cannot access Ubuntu.com?

---

### Post by melriz on 2013-05-17
Thanks for replying miegiel.  I've aleady learned a lot, just trying to answer your question. 


> **miegiel said:**
> 

Make sure the web server on your machine is up and running,
I'm not really sure how to tell if the web server on my machine is up and running. I did find a code that sounded like it would turn the server on if it was off:
```
test@ubuntu:/var/www$ sudo /etc/init.d/apache2 start
[sudo] password for test: 
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using xxx.xxx.xxx.xxx *(Totally different IP than all others metioned)* for ServerName
httpd (pid 914) already running
```

I also tried the following:
```
test@ubuntu:~$ ping -c 4 192.xxx.xxx.xxx (local host IP address)
PING 192.xxx.xxx.xxx (192.xxx.xxx.xxx) 56(84) bytes of data.
From 192.xxx.xxx.yyy icmp_seq=1 Destination Host Unreachable
From 192.xxx.xxx.yyy icmp_seq=2 Destination Host Unreachable
From 192.xxx.xxx.yyy icmp_seq=3 Destination Host Unreachable
From 192.xxx.xxx.yyy icmp_seq=4 Destination Host Unreachable
```

The From 192.xxx.xxx.yyy isn't an address mentioned before .

I don't know if either of those means it's up and running or not.

 Apache is my web server software, but maybe it's not apache2? If this doesn't tell you the web server is up and running, is there a command I can run that would tell you that?

---

### Post by melriz on 2013-05-17
Thanks for responding and asking clarifying questions. I'll do my best to respond.


> **x C0MMAND0 x said:**
> 1 - Is the website data hosted on the machine you are on locally?  If so, you can just browse to the files and access them directly, without having to worry about an IP address.
I believe this is correct. I can have access and can edit files in both the terminal (where I enter commands as test@ubuntu:/var/www$). In order to see the effects of my changes, I entered 192.xxx.xxx.xxx and my website would appear. This is what isn't working now.

> **x C0MMAND0 x said:**
> 
2 - Because you said you were previously accessing the website via a 192.xxx.xxx.xxx subnet, that tells me it is internal not external.  Is the website hosted on a separate computer? I'm sure I should know this, but I don't. How can I tell? I do in essence have "two computers" on my labtop. I have my LAMP setup then I have a regular PC. I have to log out of my Linux machine in order to access Windows on the same computer. I'm not sure if that's useful info or not.
> **x C0MMAND0 x said:**
> 
3 - run ```
ifconfig -a
``` on your computer you are trying to access the website from, and again on the computer the website is hosted on (if it is different) and post the results here.
```
 /var/www$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 08:00:27:cc:16:1b  
          inet addr:192.168.0.226  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fecc:161b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18810 errors:1 dropped:0 overruns:0 frame:0
          TX packets:3446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3656971 (3.6 MB)  TX bytes:705959 (705.9 KB)
          Interrupt:10 Base address:0xd020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22087 (22.0 KB)  TX bytes:22087 (22.0 KB)
```
As I'm not sure if there is another computer that the website is hosted on so I didn't run it again.

> **x C0MMAND0 x said:**
> I don't fully understand everything you said/asked, so these are just some general questions to help clarify and get us in the right direction.  Thanks for being patient with me, I'm learning a whole new language. :)

---

### Post by melriz on 2013-05-17
> **grahammechanical said:**
> What do you mean  
We have an actual store not hosted on ubuntu. We have a mock store that mimics the real one for testing purposes (I'm not sure if it's actually hosted by Ubuntu or another computer). All the code for the mock site is stored on Ubuntu so that we can try out code and see what happens without breaking the real one.

> **grahammechanical said:**
> Are you storing the files on Ubuntu One?  Yes we have all the php file store on the Ubuntu one.

> **grahammechanical said:**
> Are you trying to use Ubuntu One to host a web site?  I think so... When I typed in the IP address of my linux system the mock store did come up (which it isn't doing now).

> **grahammechanical said:**
> Are you saying that you cannot access Ubuntu.com? No. 

Thanks for taking the time to try and understand me. I'm really trying to be as clear as I can with my limited knowledge.

---

### Post by miegiel on 2013-05-18
> **melriz said:**
> ```
test@ubuntu:/var/www$ sudo /etc/init.d/apache2 start
[sudo] password for test: 
[COLOR="#FF0000"] * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using xxx.xxx.xxx.xxx *(Totally different IP than all others metioned)* for ServerName[/COLOR]
[COLOR="#009900"]httpd (pid 914) already running[/COLOR]
```

The [COLOR="#FF0000"]red line[/COLOR] suggests there's something wrong with the way apache is configured.
The [COLOR="#009900"]green line[/COLOR] suggests there already is an instance of apache running.


I'm not really an expert on apache. However, if you want to see if apache is running on your machine do:
```
ps faux | grep apache
```
If you only get the line below, than apache isn't running. The command looks for process running on your machine and filters the result for anything containing *apache*, but it also finds itself looking for *apache* :D
```
user    861  0.0  0.0   3352   748 pts/0    S+   20:24   0:00              \_ grep --color=auto apache
```


BTW
```
sudo /etc/init.d/apache2 [COLOR="#FF0000"]stop[/COLOR]
```
will probably stop apache ;) in case you want to do that.

Also, don't worry about posting IP numbers that start with 192.168.... (or 10..... or 172.16... up to 172.31...) online. They are common local network addresses that can't be accessed from anywhere but your network.

---

