---
title: "Problem with a specific site"
date: 2022-06-19
forum: New to Ubuntu
---

### Post by gale85 on 2022-06-19
As of yesterday, somewhere before 3 pm, I cannot access my site, for which I am the administrator and editor. I also tried it via a mobile phone that connects wirelessly to the router. It means that most likely my IP address was blacklisted, but my friend checked that my IP address was not blacklisted, and also since we use wordpress for the site, so we activated the wordfence security plugin, my IP address was not found there either. Could this happen due to some process on Ubuntu do you have any idea how to solve this except VPN, proxychains and shut down the router at 48h or 24h I don't know exactly how it was. By the way, to emphasize Ubuntu is 22.04

---

### Post by TheFu on 2022-06-19
If I couldn't access my website that was running on a hosting provider, I'd first ssh into the system. If that doesn't work, then I'd use the hosting provider's "panel" controller to access the system. If that doesn't work, I'd assume the system was hacked, contact the provider, and have them reset the system to a fresh OS, then I'd restore my backups to it.

If I didn't have backups, well, that's a completely different issue.

Regardless, I'd be more cautious with the next install to ensure that all patching and security best practices were followed, in hope of avoiding cracks again.

---

### Post by mIk3_08 on 2022-06-20
> **gale85 said:**
> I cannot access my site, for which I am the administrator and editor. I also tried it via a mobile phone that connects wirelessly to the router. It means that most likely my IP address was blacklisted, but my friend checked that my IP address was not blacklisted, and also since we use wordpress for the site, so we activated the wordfence security plugin, my IP address was not found there either. 
Is your ISP provided you a static IP? Because the ISP here in Philippines just giving up a dynamic IP. Every time I wasn't able to access some website I just restart my local router and my IP change when I do that. Then I can now access the website or use vpn to access the website.
I also agree with the TheFu
> **TheFu said:**
> II'd first ssh into the system. 
Using ssh is one way of using your private secured tunnel to access the hosting server. Regards and cheers.

---

### Post by #&amp;thj^% on 2022-06-20
> **TheFu said:**
> If I couldn't access my website that was running on a hosting provider, I'd first ssh into the system. If that doesn't work, then I'd use the hosting provider's "panel" controller to access the system. If that doesn't work,** I'd assume the system was hacked,** _contact the provider_, and have them reset the system to a fresh OS, then I'd restore my backups to it.

If I didn't have backups, well, that's a completely different issue.

[B]_Regardless, I'd be more cautious with the next install to ensure that all patching and security best practices were followed, in hope of avoiding cracks again.[_[/B[

+1
I was afraid of that, the OP has been running wordpress as root for a few days now, as far as I can tell.
By default, any user that logs in with administrative permissions can access the WordPress plugin and theme editors, and change any theme or plugin file on your site in real-time. 

What Files Can Be Edited?

The following file types (if writable) can be edited in the plugin editor that is built into the WordPress administrative panel:
[list]                       

   [*] HTML
   [*] **_PHP_**
   [*] CSS
   [*] TXT (and related text-like files such as RTF)[/list]

In the theme editor, only writable PHP and CSS files can be edited.
Source: [https://wordpress.org/support/article/editing-files/](https://wordpress.org/support/article/editing-files/)

---

### Post by gale85 on 2022-06-20
People, let me clarify some things first. I just want to access my site that we rented from the hosting provider, it has nothing to do with my home computer and I do not access it as a root user. All information for access to the site Control Panel and other things we received from the hosting provider. When I called my ISP he told me to check on the site that my IP address was not blacklisted. The friends checked everything on the Yoast plugin, on the .htaccess file and in the Control Panel. My IP address from my ISP is not recorded anywhere.

---

### Post by TheFu on 2022-06-20
> **gale85 said:**
> People, let me clarify some things first. I just want to access my site that we rented from the hosting provider, it has nothing to do with my home computer and I do not access it as a root user. All information for access to the site Control Panel and other things we received from the hosting provider. When I called my ISP he told me to check on the site that my IP address was not blacklisted. The friends checked everything on the Yoast plugin, on the .htaccess file and in the Control Panel. My IP address from my ISP is not recorded anywhere.

Your original post didn't say where the website was hosts. Many Linux people will host websites on their home machines, which is partially why  mIk3_08 mentioned that, I would guess.  He also mentioned some hosting provider stuff too.  I don't think your ISP has anything to do with  this, but some people do try to run websites from their homes, so coming at it from that angle made sense when we didn't know more.

I assumed you were using a hosting provider, hence my first guesses. I made this assumption based on wordpress and wordfense mentions, but some people might run those from their houses.  I've never run wordpress through a point-n-click interface.  I've always set it up through an ssh connection.

We were all guessing because it wasn't clear.  Thanks for clarifying. That part is helpful.

> All information for access to the site Control Panel and other things we received from the hosting provider.
Ok, but it doesn't actually tell us anything.  Is the website up or not?  Assume we are dumb and only know exactly what you tell us.  
Can you not ssh into the server that is running your website and check everything?  Do you know what ssh is?  What do the webserver logs show?  Which webserver is being used?

Did you try the other provided advice or not? Please be extremely clear.

---

### Post by gale85 on 2022-06-20
We have SSH access about the rest, we reviewed everything, my ip address was not found anywhere on the site, it is forbidden. What exactly should you look for when logging in to SSH without the .htaccess file

---

### Post by TheFu on 2022-06-20
> **gale85 said:**
> We have SSH access about the rest, we reviewed everything, my ip address was not found anywhere on the site, it is forbidden. What exactly should you look for when logging in to SSH without the .htaccess file

You said the website isn't working.  
Is that for everyone or just you?  And if just you, for every computer or just 1?   Have you tried [https://downforeveryoneorjustme.com/](https://downforeveryoneorjustme.com/) ?
If it is down for you only, but regardless of the computer/browser used, then it is server-side.  Try using your backup login.
If it is down for everyone, then the issue is different.

You've jumped so far ahead, but haven't provided any relevant background as to why any .htaccess would be involved at all.  I don't use .htaccess files on my sites. I control everything in the main web-server config file for the website.  If I need basic authentication, I'll build that into the webapp or at the reverse proxy, not at the web-server layer.

But with wordpress, it is most likely that someone took over your website completely and is using to for email phishing attacks around the world.  There are usually 2M websites hacked in this way on any day AND most of them run wordpress using at least 1 addon/theme.

---

### Post by gale85 on 2022-06-20
Only I can't access that website through my computer and all those who connect wirelessly to the router from my ISP. Friends who have their own internet can easily access the site

---

### Post by TheFu on 2022-06-20
> **gale85 said:**
> We have SSH access about the rest, we reviewed everything, my ip address was not found anywhere on the site, it is forbidden. What exactly should you look for when logging in to SSH without the .htaccess file

The system logs.
The web server logs.
The firewall logs.
From your LAN, can you ping the server?  
Can you ssh it or is it just https that's blocked?

---

### Post by gale85 on 2022-06-22
We checked all the logs and there is nothing. I can't ping the site via LAN. We will also check with the hosting company that my IP address is not booked on their server

---

### Post by TheFu on 2022-06-22
> **gale85 said:**
> We checked all the logs and there is nothing. I can't ping the site via LAN. We will also check with the hosting company that my IP address is not booked on their server

Rather than saying what does and doesn't work, can you please show us?  I feel like a dentist digging for a root canal using someone else's description, rather than just sending a video/photo of the issues.

Please run the ping and copy/paste the exact command and results back here.  Please use forum code tags too.

I doubt the issue is with the hosting. It is probably a network issue/DNS issue on your LAN.

---

### Post by #&amp;thj^% on 2022-06-23
Some providers don't allow ping, **along with what TheFu has asked**
Maybe give us a "dig" of the site or "just google":
```
dig google.com

; <<>> DiG 9.18.4 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 54560
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		119	IN	A	142.250.72.46

;; Query time: 14 msec
;; SERVER: 103.86.96.100#53(103.86.96.100) (UDP)
;; WHEN: Thu Jun 23 08:44:34 MDT 2022
;; MSG SIZE  rcvd: 55



```
My site:
```
dig 10.5.0.2

; <<>> DiG 9.18.4 <<>> 10.5.0.2
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 25595
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;10.5.0.2.			IN	A

;; AUTHORITY SECTION:
.			3244	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2022062300 1800 900 604800 86400

;; Query time: 45 msec
;; SERVER: 103.86.96.100#53(103.86.96.100) (UDP)
;; WHEN: Thu Jun 23 09:06:29 MDT 2022
;; MSG SIZE  rcvd: 112


```

---

### Post by gale85 on 2022-06-23
Just to add that I set up a VPN plugin for Chrome and now it opens the site normally with that plugin and a friend said he would contact the hosting company and see with their server that my IP address was not blocked there

---

### Post by TheFu on 2022-06-23
> **gale85 said:**
> Just to add that I set up a VPN plugin for Chrome and now it opens the site normally with that plugin and a friend said he would contact the hosting company and see with their server that my IP address was not blocked there

Just to be clear, you won't be posting the requested information.
Good luck., Hope you find a resolution.

---

### Post by web-user on 2022-06-25
It doesn't sound like a problem specific to Ubuntu. Maybe your browser settings are incorrect or Wordfence blocked your IP or whatever.

---

### Post by gale85 on 2022-06-26
@[COLOR=#000000]web-user [/COLOR]Wordfence didn't do it. We checked it out

@1fallen How do I check this if I just type "dig site.com" into google

---

### Post by #&amp;thj^% on 2022-06-26
> **gale85 said:**
> 
@1fallen How do I check this if I just type "dig site.com" into google
Open your terminal and run:
```
dig <your-site-ip>
```

Replace <your-site-ip> with your real sites ip

---

### Post by gale85 on 2022-06-26
dig ip adress
```


; <<>> DiG 9.18.1-1ubuntu1.1-Ubuntu <<>> ip adress
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 22061
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;ip adress.			IN	A


;; AUTHORITY SECTION:
.			86363	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2022062601 1800 900 604800 86400


;; Query time: 31 msec
;; SERVER: 8.8.8.8#53(8.8.8.8) (UDP)
;; WHEN: Sun Jun 26 21:11:27 CEST 2022
;; MSG SIZE  rcvd: 118

```

---

### Post by #&amp;thj^% on 2022-06-26
Something is messed up, on your end you show:
```
 SERVER: 8.8.8.8#53(8.8.8.8) (UDP)
```
That's a DNS Server's address.
When I run a dig for your shown address, I get this:
```
dig 9.18.1-1ubuntu1.1-Ubuntu

; <<>> DiG 9.18.4 <<>> 9.18.1-1ubuntu1.1-Ubuntu
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 48780
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
;; QUESTION SECTION:
;9.18.1-1ubuntu1.1-Ubuntu.	IN	A

;; AUTHORITY SECTION:
.			3391	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2022062601 1800 900 604800 86400

;; Query time: 50 msec
;; SERVER: **[COLOR="#FF0000"]103.86.96.100#53(103.86.96.100) (UDP)[/COLOR]**
;; WHEN: Sun Jun 26 13:20:37 MDT 2022
;; MSG SIZE  rcvd: 128


```
Here is a good reply back from;
```
dig canonical.com

; <<>> DiG 9.18.4 <<>> canonical.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18831
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
;; QUESTION SECTION:
;canonical.com.			IN	A

;; ANSWER SECTION:
canonical.com.		60	IN	A	185.125.190.20
canonical.com.		60	IN	A	185.125.190.21
canonical.com.		60	IN	A	185.125.190.29

;; Query time: 129 msec
;; SERVER: 103.86.96.100#53(103.86.96.100) (UDP)
;; WHEN: Sun Jun 26 13:46:13 MDT 2022
;; MSG SIZE  rcvd: 90



```
EDIT3: Did you by chance dig the forums IE:
```
dig @8.8.8.8 ubuntuforums.org

; <<>> DiG 9.18.4 <<>> @8.8.8.8 ubuntuforums.org
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 31289
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
;; QUESTION SECTION:
;ubuntuforums.org.		IN	A

;; ANSWER SECTION:
ubuntuforums.org.	600	IN	A	185.125.188.16
ubuntuforums.org.	600	IN	A	185.125.188.17

;; Query time: 159 msec
;; SERVER: 8.8.8.8#53(8.8.8.8) (UDP)
;; WHEN: Sun Jun 26 13:49:38 MDT 2022
;; MSG SIZE  rcvd: 77



```
My time is short again for today on the forums.

---

### Post by gale85 on 2022-06-26
dig ip adress
```

; <<>> DiG 9.18.1-1ubuntu1.1-Ubuntu <<>> ip adress
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 7287
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;ip adress.			IN	A


;; AUTHORITY SECTION:
.			10800	IN	SOA	a.root-servers.net. nstld.verisign-grs.com. 2022062601 1800 900 604800 86400


;; Query time: 27 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Sun Jun 26 21:56:06 CEST 2022
;; MSG SIZE  rcvd: 118

```
Is everything ok now? I remembered which files I opened and set up. I opened the /etc/resolv.conf files
and /etc/resolvconf/resolv.conf.d/head If necessary, I will post their content

---

### Post by #&amp;thj^% on 2022-06-26
No time today for that, but I'm very curious>>>is this the site in question=  "9.18.1-1ubuntu1.1-Ubuntu" is this the real address???

---

### Post by gale85 on 2022-06-26
I don't know why it throws it out, I hid the real IP address for security. Everywhere it says ip address, I have the right ip address, and when you ask me, I don't know what it is.
If necessary, I will post exactly which site is in question

---

### Post by #&amp;thj^% on 2022-06-26
> **gale85 said:**
> 
If necessary, I will post exactly which site is in question
No need then if you say you "dig" the right .com address or ip numbers, then that's what I'll have to believe.
But Houston we a have a problem.:o

---

### Post by gale85 on 2022-07-15
Hello people, I'm sorry I haven't contacted you in a while, but I have a lot of commitments so I haven't had time to get in touch. I am very happy to say that from today I can freely open my site through my home IP address. Everything is working now, but ok, if you need some more information to determine the cause of the problem, write to me

---

