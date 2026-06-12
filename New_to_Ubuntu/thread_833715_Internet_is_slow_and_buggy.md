---
title: "Internet is slow and buggy"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by BottleOfAle on 2008-06-18
I just installed Ubuntu today, and I'm absolutely new to it. For a while the internet wouldn't work, but it works now just very VERY slowly. I have a linksys wireless connection at my house. Whenever I try to use Pidgin, my buddy list for AIM will show, but I can't recieve IMs, and IRC can't connect to the host. Anyone know what the problem is? Thank you for the help!

---Ale

---

### Post by marshal_mellow on 2008-06-18
can you copy and paste the output of 'lspci' in this thread?

---

### Post by brdokoky on 2008-06-19
Have you tried to disable IPv6 ? Some time it may help.

---

### Post by adobrakic on 2008-06-19
You guys may need to be more specific, since he's new to it.

---

### Post by superprash2003 on 2008-06-19
It could be a DNS issue.try changing your DNS Servers to opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by hyper_ch on 2008-06-19
I'd say it's an IPv6 issue

---

### Post by Harpoon on 2008-06-19
A "slow" internet connection may, in fact, be an ipv6 issue.  The "fix" is simple:

gksu gedit /etc/hosts

after you enter your password, the file will appear in your text editor.  Now comment out (place a # at the beginning) the lines that deal with ipv6, like so:


# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

then simply save the file. No need to reboot.

That may speed some things up, but I have no experience using AIM, and I have doubts that this will solve that issue.  It's an easy fix, and won't break anything, so give it a try.

Good luck

---

