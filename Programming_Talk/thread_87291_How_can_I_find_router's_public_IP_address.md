---
title: "How can I find router's public IP address?"
date: 2005-11-07
forum: Programming Talk
---

### Post by mfyahya on 2005-11-07
I have a NAT router set up at home with private IPs for the home computers. My ISP gives me only one IP address that gets assigned to the router. Is there a way to find what this is? I normally go to whatismyip.com but I'm looking for some kind of command line tool that I can use in scripts and stuff.

---

### Post by adwait on 2005-11-07
I doubt it, because the router exists as a completely different device from the computer and the OS has no knowledge about it. You would probably have to telnet to the router or something........

---

### Post by souki on 2005-11-07
you can use a free dynamic dns provider
I don't know which one is the best but I often use [http://www.dyndns.com/](http://www.dyndns.com/)

you will have to open an account and choose a host name for your dynamic ip.
then you can use ddclient from the universe repository to update the ip-address (it's not difficult to configure)

then you can use your-choosen-name.dyndns.org in your script

---

### Post by nemik on 2005-11-08
primitive but works for me:

#!/bin/bash

STR=`lynx -dump http://www.cc.com.au/ip.php`
echo $STR

---

### Post by mfyahya on 2005-11-09
thanks nemik. that worked. I had to filter out some whitespace though

---

### Post by 80aless on 2009-02-08
How can I make that script work? it shows all my files of the ~/ directory 
and   then [5]Lists Page not found when there's no plan b - plan cc [6][osiamember.png] References Visible links 1. [http://cc.com.au/](http://cc.com.au/) 2. [http://cc.com.au/oss](http://cc.com.au/oss) 3. [http://cc.com.au/hosting](http://cc.com.au/hosting) 4. [https://mail.cc.com.au/](https://mail.cc.com.au/) 5. [http://lists.cc.com.au/](http://lists.cc.com.au/) 6. [http://www.osia.net.au/](http://www.osia.net.au/) Hidden links: 7. [http://cc.com.au/](http://cc.com.au/)

---

### Post by geirha on 2009-02-08
All you need is a page that prints the ip address you connect to the page with. Don't know about that australian one, but portforward.com shows your ip.
```
lynx -dump http://portforward.com | grep 'Your external IP address is'
```

---

### Post by 80aless on 2009-02-08
ok thank you!

---

### Post by tomchuk on 2009-02-08
If you view source at whatismyip.com you get:

```

<!--Please set your code to scrape your IP from www.whatismyip.com/automation/n09230945.asp Please set your code to hit this page at a REASONABLE pace.  For more info, please see our "What's New" page.-->

```

```

IP=`wget -q -O - http://www.whatismyip.com/automation/n09230945.asp`
echo \"$IP\"

```
IP address, no whitespace.

---

