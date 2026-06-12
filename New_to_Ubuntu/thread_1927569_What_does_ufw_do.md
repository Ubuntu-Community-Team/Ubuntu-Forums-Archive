---
title: "What does ufw do?"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by ubume2 on 2012-02-18
I am a newbie when it comes to firewalls. I fiddled with firewalls when I was into XP, but have ignored them on Linux.  I understand the basics of a firewall[maybe?]. 

For the past couple of years I have done nothing with the firewall, but this week, I have set up my ubuntu installs
by $sudo ufw enable.  I do nothing else.

I have either wired connections and wireless connections on all of my desktops.

In the above situation, am I doing ANYTHING by enabling ufw?  If yes, what am I doing?

Just curious.  In the past week or so I had been losing my wired connection frequently.  I was at wits end trying to figure out the problem.  In desperation, I tried ufw enable.  And the problem now seems to be solved.  Coincidence?

---

### Post by mike555 on 2012-02-18
If you want a GUI , install gufw

---

### Post by haqking on 2012-02-18
> **ubume2 said:**
> I am a newbie when it comes to firewalls. I fiddled with firewalls when I was into XP, but have ignored them on Linux.  I understand the basics of a firewall[maybe?]. 

For the past couple of years I have done nothing with the firewall, but this week, I have set up my ubuntu installs
by $sudo ufw enable.  I do nothing else.

I have either wired connections and wireless connections on all of my desktops.

In the above situation, am I doing ANYTHING by enabling ufw?  If yes, what am I doing?

Just curious.  In the past week or so I had been losing my wired connection frequently.  I was at wits end trying to figure out the problem.  In desperation, I tried ufw enable.  And the problem now seems to be solved.  Coincidence?

[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

Both threads will answer your questions and how to use it or somethng else effectively.

Cheers

---

### Post by kevdog on 2012-02-18
I believe a coincidence because turning on ufw by default does nothing.

---

### Post by mcduck on 2012-02-18
If you haven't installed any server application that would listen for incoming network connections, then enabling UFW won't do anything for you. There is no use for a firewall if there's no connections for it to block...

...and even if you had installed some server, you'd only need a firewall if you wanted to limit it's connectivity beyond what the server's own configuration options allow you to do.

Anyway, UFW just configures rules for the built-in firewall of Linux kernel, and makes sure the rules are loaded on every boot.

---

### Post by ubume2 on 2012-02-18
Thank you all for your replies. & haqking thanks for the urls.  (They didn't show up in my google search)

---

### Post by haqking on 2012-02-18
> **mcduck said:**
> If you haven't installed any server application that would listen for incoming network connections, then enabling UFW won't do anything for you. There is no use for a firewall if there's no connections for it to block...

...and even if you had installed some server, you'd only need a firewall if you wanted to limit it's connectivity beyond what the server's own configuration options allow you to do.

Anyway, UFW just configures rules for the built-in firewall of Linux kernel, and makes sure the rules are loaded on every boot.

I have reread that a few times and not sure if you are saying what i think you are or not...LOL

Anyways to clarify for the OP, a firewall is about more than blocking incoming connections or controlling services that may be associated with a port.

Firewalls also control outgoing connections, regardless of if you have services listening on a given port, you want to control outbound traffic to prevent reverse connections or exploited applications that may configure there own arbitrary port.

The whole thing about not needing a firewall if you have no services listening or because Ubuntu/Linux has no default ports open by default is not a good philosophy in terms of general security best practice

Cheers

---

### Post by wildmanne39 on 2012-02-18
+1 haqking> The whole thing about not needing a firewall if you have no services listening or because Ubuntu/Linux has no default ports open by default is not a good philosophy in terms of general security best practice
as stated in the first link of hakings post.

---

### Post by mcduck on 2012-02-18
> **haqking said:**
> I have reread that a few times and not sure if you are saying what i think you are or not...LOL


Hard to say which way it is since you didn't say what you thought I were saying... ;)

My point is that you shouldn't need a firewall for any normal use case. Especially not on a desktop machine. You only need one if you run a server application and are not able to configure the server itself to limit connectivity the way you'd want to.

So, on a desktop system there's no need for a firewall because there's nothing listening for incoming connections, and thus nothing for the firewall to block. And on system running, for example, Apache server, there shouldn't be any need for a firewall since either you want the web server to be accessible from the Internet, or you only want to limit it to local network or localhost, which can both be done directly through Apache's configuration.

So the most common reason why you'd really need a firewall is that you are running a server application that you wan to limit to localhost or certain addresses only, but that server itself doesn't have such option. And of course there are some more advanced firewall tasks like protecting against DoS attacks and such.

---

### Post by Ms. Daisy on 2012-02-18
> **mcduck said:**
> Hard to say which way it is since you didn't say what you thought I were saying... ;)

My point is that you shouldn't need a firewall for any normal use case. Especially not on a desktop machine. You only need one if you run a server application and are not able to configure the server itself to limit connectivity the way you'd want to.

So, on a desktop system there's no need for a firewall because there's nothing listening for incoming connections, and thus nothing for the firewall to block. And on system running, for example, Apache server, there shouldn't be any need for a firewall since either you want the web server to be accessible from the Internet, or you only want to limit it to local network or localhost, which can both be done directly through Apache's configuration.

So the most common reason why you'd really need a firewall is that you are running a server application that you wan to limit to localhost or certain addresses only, but that server itself doesn't have such option. And of course there are some more advanced firewall tasks like protecting against DoS attacks and such.
I don't understand what you're saying.  A desktop doesn't listen for incoming connections?  Here's the output on my desktop. Can you explain why these ports have "listen" after them?
```
ms.daisy@ms.daisy-machine:~$ sudo lsof -i -P -n
COMMAND    PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
smbd       969  root   24u  IPv6   8449      0t0  TCP *:445 (LISTEN)
smbd       969  root   25u  IPv6   8451      0t0  TCP *:139 (LISTEN)
cupsd     1091  root    9u  IPv6  26182      0t0  TCP [::1]:631 (LISTEN)
cupsd     1091  root   10u  IPv4  26183      0t0  TCP 127.0.0.1:631 (LISTEN)
vmware-au 1299  root    8u  IPv4   8644      0t0  TCP *:902 (LISTEN)
firefox   6731 ms.daisy   52u  IPv4 104023      0t0  TCP 192.186.10.69:46335->74.125.93.138:80 (ESTABLISHED)

```

---

### Post by haqking on 2012-02-18
> **mcduck said:**
> Hard to say which way it is since you didn't say what you thought I were saying... ;)

My point is that you shouldn't need a firewall for any normal use case. Especially not on a desktop machine. You only need one if you run a server application and are not able to configure the server itself to limit connectivity the way you'd want to.

So, on a desktop system there's no need for a firewall because there's nothing listening for incoming connections, and thus nothing for the firewall to block. And on system running, for example, Apache server, there shouldn't be any need for a firewall since either you want the web server to be accessible from the Internet, or you only want to limit it to local network or localhost, which can both be done directly through Apache's configuration.

So the most common reason why you'd really need a firewall is that you are running a server application that you wan to limit to localhost or certain addresses only, but that server itself doesn't have such option. And of course there are some more advanced firewall tasks like protecting against DoS attacks and such.

OK you were saying what i thought.

In which case i disagree as i discussed in my post.

Firewalls are not just for incoming traffic.

reverse connects, code exploitation.

A desktop user should have tight outbound rules for the same reasons you should use other methods to aid in security such as NOScript, Apparmor and the such.

Firewalls are not all about incoming and having listening services.

Cheers

---

### Post by mcduck on 2012-02-19
> **haqking said:**
> OK you were saying what i thought.

In which case i disagree as i discussed in my post.

Firewalls are not just for incoming traffic.

reverse connects, code exploitation.

A desktop user should have tight outbound rules for the same reasons you should use other methods to aid in security such as NOScript, Apparmor and the such.

Firewalls are not all about incoming and having listening services.

Cheers
Well, outgoing traffic is best controlled by making sure you don't install applications you can't trust (as such applications could cause many other issues than just things that require a network connection).

So if you really want to play it safe, and stick to applications that you know to be safe, & avoid using untrusted software sources, the firewall once again becomes pointless for most use cases. :)

---

