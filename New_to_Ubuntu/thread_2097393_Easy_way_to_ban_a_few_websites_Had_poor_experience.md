---
title: "Easy way to ban a few websites? Had poor experience with dansguardian."
date: 2012-12-23
forum: New to Ubuntu
---

### Post by polaatx on 2012-12-23
Hello, 

I need to stop people using my laptop running Ubuntu 12.10 from going to just a handful of domains. 

I installed dansguardian using the instructions here [http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008)

However, it was a disaster. It filtered most of the websites I use - like Bank of America or Amazon.com - but not any of the Google sites. I never figured out why. Posting to the dansguardian mailinglist and waiting 3 days was not helpful. Didn't get a single reply. So I uninstalled using instruction here: [http://ubuntuforums.org/archive/index.php/t-311089.html](http://ubuntuforums.org/archive/index.php/t-311089.html).

**My question: is there a easy way to ban a few domains? **

The router built into my wifi hotspot does not have website filtering capability. I am not an experienced linux user. Please kindly write out the code if your solution involves the terminal.

---

### Post by 3v3rgr33n on 2012-12-23
Suppose you do ban a website say "www.example.com", will they not be able to access it via a web-based anonymous proxy service like anonymouse.org ?

---

### Post by polaatx on 2012-12-23
> **3v3rgr33n said:**
> Suppose you do ban a website say "www.example.com", will they not be able to access it via a web-based anonymous proxy service like anonymouse.org ?

The people I am dealing with are not that knowledgeable.

---

### Post by NikTh on 2012-12-23
Hi , 
you can add some websites in /etc/hosts file .. and block them. Be aware , the full web address is needed. 
Open the file with this command ```
gksudo gedit /etc/hosts
```and add 
example format 
```
127.0.0.1        www.google.com
```Save the file and close and open the browser again .. and you will see a message like "Unable to connect" , when you visit [www.google.com]("http://www.google.com") 

This method can be bypassed from an experienced user. 

Thanks

---

### Post by fantab on 2012-12-23
polaatx, /etc/hosts is IMO a good way to restrict some "known" bad domains. You can download a 'hosts' file from [**here**]("http://www.hosts-file.net/"), offcourse there are other providers if you care to search. You can edit this hosts file to add or subtract domains. 
After downloading the hosts file (You may have to extract it and rename it to hosts).

```
$ sudo nautilus
```Delete the /etc/hosts file or back it up and replace it with the hosts file you've downloaded. That is all.

To edit it:

```
$ sudo gedit /etc/hosts
```Also some sort of Browser Protection with addons like ADBLOCK, NoScripts, Ghostery, etc you can keep the 'bad' elements from any website at bay.

Just my two cents...

EDIT: enable UFW (Uncomplicated Fire Wall) follow steps [**here**]("http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/").

Good Luck

---

### Post by agillator on 2012-12-23
Adding to what fantab wrote, the easiest way to block some site is at the firewall. First, you will probably need the ip addresses of the sites - whois can help there, ping can help, etc. Then activate your firewall. Ubuntu provides ufw as mentioned which would probably be the easiest way. In the firewall, you will want to deny both incoming and outgoing packets to the ip addresses you found. DROP, don't REJECT them. You may or may not want to omit logging of them, too. See the man page (man ufw) for specific instructions.

When dealing with a firewall it is best to spend a few minutes learning how to do it rather than blindly following some script you see somewhere. It really isn't as confusing or as difficult as it may seem at the start. And be sure ufw automatically loads and activates at boot time.

---

### Post by spynappels on 2012-12-23
I believe that the /etc/hosts way is a better way than the firewall, because it will stop the request going out in the first place and does not depend on having the correct IP address in the firewall config. Don't forget that many domains may operate across a range of IPs and blocking one of them is not enough, while adding all possible IPs is tedious.

---

### Post by Zill on 2012-12-23
> **polaatx said:**
> ...I need to stop people using my laptop running Ubuntu 12.10 from going to just a handful of domains...
Why not just stop other people using your laptop or give them their own accounts?

You could logout when you are not using it *or* hit Ctrl + Alt + L to lock the screen while remaining logged in.

---

### Post by agillator on 2012-12-23
/etc/hosts will work for OUTGOING packets, not incoming. Blocking a range of ips with iptables is not at all difficult. As a matter of fact, you don't really need the ip(s) for iptables. The network/site name will suffice, although that is not recommended. 

I prefer doing the work to stop packets at the firewall since I can foresee, in my case, the hosts file growing to an unmanageable size and actually slowing everything down. Since the firewall packet inspection is actually done by the kernel it seems to be faster. Long and complicated firewall setups can slow things down, of course, but I usually don't see much problem with that.

Obviously if I couldn't catch everything at the firewall then I would resort to the hosts file, but personally that would be my third choice. My first choice would be to keep people off my laptop, second choice firewall, third choice hosts file. But, different strokes as they say. I think the OP has enough info to see the pros and cons of each and make a fitting decision.

---

