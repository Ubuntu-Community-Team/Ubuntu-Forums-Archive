---
title: "Browse Localhost  with no connection"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by JKHinton CPBD on 2008-10-30
Hello,

I am new to ubuntu hardy server. I am trying to change my working web pages from a Windows XP Apache server to Ubuntu LAMP.  Why can I browse with firefox my webpages that are not on the internet using localhost without a network connection sometime and sometimes I can't?  When I have a network connection, I have no trouble browsing the internet or browsing my web pages under localhost.  It seems like if my web pages are on my hard drive, I should be able to browse them with or without a connection I know I can using the XP/Apache server. Any pointers will be appreciated.

James in GA,USA

---

### Post by JKHinton CPBD on 2008-10-30
Ok, I found this in Ubuuntu server documentation

 The Listen directive specifies the port, and optionally the IP address, Apache2 should listen on. If the IP address is not specified, Apache2 will listen on all IP addresses assigned to the machine it runs on. The default value for the Listen directive is 80. Change this to 127.0.0.1:80 to cause Apache2 to listen only on your loopback interface so that it will not be available to the Internet, to (for example) 81 to change the port that it listens on, or leave it as is for normal operation. This directive can be found and changed in its own file, /etc/apache2/ports.conf 

I edited the ports.conf from listen 80 to 127.0.0.1:80 and then restarted Apache and I still am not able to browse my own web pages on the local hard drive through localhost with no internet connection. Isn't this what loopback interface should do? or am I barking up the wrong tree?

James in GA, USA

---

### Post by Sarmacid on 2008-10-30
I don't think this is it, but it might be the firewall. You can check out the rules set on iptables with ```
iptables -L
```

---

### Post by Mindzai on 2008-10-30
What does your /etc/hosts file contain?

---

### Post by JKHinton CPBD on 2008-10-30
Thanks Mindzai and Sarmacid for your responses,

I'll check the firewall.

The etc/hosts file contains the following
"

127.0.0.1 localhost
127.0.1.1 xubuntubox (name of my laptop)

# The following lines are desirable for IPv6 capable hosts
::1     ip6.localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

"
Thats whats in the etc/host file.

Just wondering if I change 127.0.0.1:80 to 127.0.0.6:80 let me use my browser to view my web files on my harddrive thru localhost when offline.  127.0.0.6 is what my address is when on my home network connected to the DSL


This is interesting.

---

### Post by JKHinton CPBD on 2008-10-31
Well I'm still wondering but not about this in particular.
I changed my default value for the Listen directive is 81. Changed this to 127.0.0.1:80 and also tried 81 to cause Apache2 to listen only on your loopback interface so that it will not be available to the Internet. I then tried 127.0.0.6:80 and 81.

I have figured out that the times I can view my web pages off line in the browser is when they are in cache, so I will not be able to work offline changing them and then check in my browser.  There should be a way to point the browser to the directory on the harddrive and not the cache any ideas out there????   All help will be appreciated.

James in GA,USA

---

### Post by Pconfig on 2008-10-31
File ==> Work offline should be off ;)

---

### Post by JKHinton CPBD on 2008-10-31
Sorry Pconfig I'm a newbie, Where would I find this directive?  I searched File ==> in the Apache2.conf file with no hits.

---

### Post by Pconfig on 2008-10-31
Woops, in firefox that is ;)

---

### Post by coldcoffee on 2008-10-31
I am not answering you question, but I do know that the 127.0.0.1:80 in the ports.conf file is to make only your localhost be able to access your Apache server. It is so you can be online and other people on the Internet cannot access your web server, only so your computer can.

Example, the default is Listen 80. This allows anyone on the Internet to access the server if you are online. Changing it to 127.0.0.1:80 gives only you access to it, even if you are online. 80 is the port it is assigned to listen for requests on which is the default for web servers. I am guessing pretty much all the web servers on the Internet  listen on port 80. Either way, I don't see how this would keep you from using it. Either option will allow you access. The problem is somewhere else.

Which is a good option if you are just testing. Especially if you are new to Apache and just learning it and on the off chance there is some settings in it that would be big vulnerability to hackers.

I know this is an obvious question. But are you sure Apache is running. You can check to see if it is in system > asministration > system monitor > processes. If  you do not see apache in there the command to run it if you are using Apache2 from your terminal would be sudo /etc/init.d/apache2 start

Also, are you by any chance running a proxy server? If you are and it is not running and your browser is configured to use the proxy, it will not allow you access.

---

### Post by JKHinton CPBD on 2008-10-31
pconfig, that did the trick, I was looking for a complicated problem and had not dreamed it was right there on the main menu in Firefox.  Thank you for the solution.

Coldcoffee,  you did not answer my question but Thank you for your response, your explanation of this has help me better understand what is happening.  

Thank you all

---

### Post by coldcoffee on 2008-10-31
You are very welcome. I am glad you did find that useful. Got me to thinking, if you were to change the default port of 80 to anything else and you wanted  other people to be able to access your server, you would have to let them know or they could not access it.

Example: Lets just say your ip is 74.553.22.01 and you changed it to port 8080. You would have to let them know this. They would have to type this into the url bar on the browser to access it. 74.553.22.02:8080. If they didn't and just typed in the ip address without the :8080, they would not be able to access your site. 80 is the default port all browser are gonna hit up when they are directed to a website.

I have no idea what that ip is for, purely made up. If someone types it in, I hope it isn't something crazy!

Edit: nevermind, that isn't a real ip anyway, the 533 is out of range if I am correct.

---

