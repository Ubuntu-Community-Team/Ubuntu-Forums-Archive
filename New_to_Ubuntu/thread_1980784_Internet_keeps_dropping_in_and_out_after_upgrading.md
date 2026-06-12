---
title: "Internet keeps dropping in and out after upgrading to 12.04"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by Deinonysus on 2012-05-15
Hi,

I recently installed Ubuntu on my computer; I dual-boot with Windows 7 using GRUB 2.  Ever since upgrading to 12.04, I have had trouble with my internet connection dropping.  I'll have a connection intermittently, but it usually only lasts a minute or so.  I usually use Chromium as my browser, but I am also experiencing this problem with Firefox.  This problem is only appearing in Ubuntu.  My internet connection has been fine in Windows.

I would greatly appreciate any help you could give me on this.  I'm not sure which info would be the most helpful for me to provide on this, so let me know what you need.

Thank you very much!

---

### Post by DingusFett on 2012-05-15
Do you have a static IP set in Ubuntu? I had a similar problem which I still need to look into further, but as soon as I set it back to using DHCP instead of Static, everything works fine.

When it drops out, does it come back straight away? When it drops, you could try pinging your router to make sure the connection is fine to there.

---

### Post by Deinonysus on 2012-05-15
> **DingusFett said:**
> Do you have a static IP set in Ubuntu? I had a  similar problem which I still need to look into further, but as soon as  I set it back to using DHCP instead of Static, everything works fine.

When it drops out, does it come back straight away? When it drops, you  could try pinging your router to make sure the connection is fine to  there.
Thanks!  My IPv4 settings are set to Automatic (DHCP).  I've been fiddling with them a bit but nothing has worked.

When it drops out it doesn't come back right away.  It could be back  again in a minute or it could be ten minutes.  It doesn't seem to follow  any rhyme or reason.

I tried pinging my router (had to look up how to do that) and it seems to work fine every time.  A typical result will be:

ping -c 3 -w 10 XXXX

PING XXXX (XXXX) 56(84) bytes of data.
64 bytes from XXXX: icmp_req=1 ttl=64 time=0.056 ms
64 bytes from XXXX: icmp_req=2 ttl=64 time=0.047 ms
64 bytes from XXXX: icmp_req=3 ttl=64 time=0.053 ms
[FONT=Ubuntu]
Where XXXX is my router's IP address.

But when I ask it to ping a website it says:
ping -c 3 -w 10 [http://www.google.com](http://www.google.com)
ping: unknown host [http://www.google.com](http://www.google.com)

I'm not sure if I formatted that correctly.[/FONT]

---

### Post by Deinonysus on 2012-05-16
This fell off the front page.  Trying again today, thank you!

---

### Post by Face-Ache on 2012-05-16
That looks like you're getting connection to your router, but the router is not connecting to the Internet.

Are you able to ping the IP address of a website? You might need to do an 'nslookup' in a Terminal; open a Terminal with Ctrl-Alt-T, type in 'nslookup' and then [www.google.com]("http://www.google.com")

Hit Ctrl-C to exit nslookup

Then 'ping 74.125.237.147' (or 'ping whatever-address-is-listed-in-your-window').

That will at least tell you whether it's a DNS, Domain Name Server issue or not (DNS changes the [www.google.com]("http://www.google.com") that you type into a browser address bar to a 74.125.237.147 IP address, so you don't have to remember IP addresses to access websites).

Seems a bit strange that Windows is fine, but Ubuntu not, when they are both connecting to the Internet via the same router.

---

### Post by Deinonysus on 2012-05-16
> **Face-Ache said:**
> That looks like you're getting connection to  your router, but the router is not connecting to the Internet.

Are you able to ping the IP address of a website? You might need to do  an 'nslookup' in a Terminal; open a Terminal with Ctrl-Alt-T, type in  'nslookup' and then [www.google.com]("http://www.google.com")

Hit Ctrl-C to exit nslookup

Then 'ping 74.125.237.147' (or 'ping whatever-address-is-listed-in-your-window').

That will at least tell you whether it's a DNS, Domain Name Server issue or not (DNS changes the [www.google.com]("http://www.google.com")  that you type into a browser address bar to a 74.125.237.147 IP  address, so you don't have to remember IP addresses to access websites).

Seems a bit strange that Windows is fine, but Ubuntu not, when they are  both connecting to the Internet via the same router.

Thank you!  I think it's a DNS problem.  I can get to Google using an IP  address when I'm having my problem, but I can't get there using the  URL.  Is there something in the network settings that might be able to  fix this?

---

### Post by Face-Ache on 2012-05-16
Okay, there's a couple of options;
_**1**_ - You could boot to Windows, open up a Command Prompt and type in 'ipconfig /flushdns'
This flushes, or clears out the DNS cache on your router - don't worry, it recreates these DNS entries whenever you visit those websites again.

**_2_** - in Ubuntu, open a Terminal and type
```
sudo aptitude install nscd
```

Then

```
sudo /etc/init.d/nscd restart
```

I understand that Ubuntu doesn't cache DNS entries by default, so you need to install and then restart the Ubuntu DNS daemon, nscd.

I admit, i'm not 100% sure that this Ubuntu option will definitely work, so the Windows option might be your best bet. Could an Ubuntu Guru provide any further advice on this please?

---

### Post by Deinonysus on 2012-05-16
Thank you for your suggestion!  Unfortunately the windows option did not solve the problem, and when I try the terminal command in Ubuntu it says "sudo: aptitude command not found."

---

### Post by Face-Ache on 2012-05-16
Hmmmm, okay. 

Sorry, try;
```
sudo apt-get install nscd
```Alternatively, it's available in the Software Centre - just search for nscd, and Name Service Cache Daemon will show up. Install it from there.

Once installed, run the second command;
```
sudo /etc/init.d/nscd restart
```

---

### Post by Face-Ache on 2012-05-16
Did a little bit more research on this, and found this;
[http://ubuntuforums.org/showpost.php?p=11377464&postcount=7](http://ubuntuforums.org/showpost.php?p=11377464&postcount=7)

So trying those commands might help.

---

### Post by Deinonysus on 2012-05-17
Thank you very much for your help!  Unfortunately, I have tried all of these things and I'm still havig the same problem.

---

### Post by Face-Ache on 2012-05-17
Hmmm, i'm sorry mate, i have to admit, i'm at a bit of a loss from here.

My suggestion, since we have now narrowed it down to a DNS issue, would be to mark this thread as SOLVED, and then start another thread with a title like "12.04 - DNS not resolving!" - or something to that effect.

That way, one of the Ubuntu Networking Guru's from around here will be able to see at a glance that this is a DNS issue, and are more likely to help you out.

In your post, i'd also provide a link to this thread, so that whoever provides advice is aware of the history.

Again, sorry i can't help any further - good luck!

---

### Post by Deinonysus on 2012-05-17
Thank you very much!  I will do that. Your help is much appreciated!

---

### Post by Face-Ache on 2012-05-17
You are most welcome, my friend :)

---

