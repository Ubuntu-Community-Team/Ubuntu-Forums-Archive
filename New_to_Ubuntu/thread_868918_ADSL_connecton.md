---
title: "ADSL connecton"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by stmartin on 2008-07-24
Hello! :)

I have ADSL modem, and I just made ADSL connection. I used the command: sudo pppoeconf, and I sucessfully created connection. I start it with pon dsl-provider and stop with poff. The problem is that the connection, breaks every time I start new page, and it doesn't start again. Also when I download something, or while some page is opening the "computers" in the right upper angle aren't blinking.

Thank you.

Regards.

---

### Post by caljohnsmith on 2008-07-24
So do you have your ADSL modem set in "bridged mode" or something? If there is no router involved, then at least for the ADSL modems I've used, the easiest way to use them is let them establish the PPPoE connection by using "PPP is on the modem" mode (you provide the username, password in the modem configuration), and then just connect to your ADSL modem with the standard ethernet connection from your computer. For most people it will simply "work out of the box" this way. 

Any special reason why you would want to use your computer to establish the PPPoE connection rather than your modem?

---

### Post by stmartin on 2008-07-24
Thanks for the reply. Can you please tell me how to use "PPP is on the modem" mode? How will I connect to my ADSL modem connection?

Can you please explain? Thank you.

---

### Post by caljohnsmith on 2008-07-24
You'll need to modify your ADSL modem's configuration, which you can access from your web browser. If you look on the bottom of the modem it often has the address, most often "http://192.168.0.1". Or did it come with any documentation? That should give it too. Also note you will need the access code to modify your modem's setup, and that code is usually on the bottom of the modem too.

In the modem's setup, via the web configuration, there should be place to use "PPP on the modem" (vs. "bridged mode" and "PPPoE on the computer"); for me it's under "Advanced" and then "PPP", but I have not idea about your modem. Be sure to also enter your user name and password in the appropriate areas of the modem configuration, and also select PPPoE (vs. PPPoA). 

If you need more help let me know, but I may be limited since I don't know your exact modem.

---

### Post by stmartin on 2008-07-24
Hello!

Thanks for the reply.

It was already set up at bridge. I connect at it with 192.168.1.1.
Before my fresh installation and update of Ubuntu 8.04 everything was alright, but still the computers in the upper right level weren't blinking. Now, it has problem with the internet connection. I set up it with sudo pppoeconf and everything is alright, but still don't know what is the problem.

Thank you.

Here is screenshot.

---

### Post by caljohnsmith on 2008-07-24
So I'm a bit confused by what you said; based on the screen shot you posted, your modem is set for "bridged" mode and still is? And then you say: > I set up it with sudo pppoeconf and everything is alright, but still don't know what is the problem.
So is everything working OK using bridged mode on the modem with pppoeconf from your computer, or is it still intermittent like you said in your original post?

If you want to have your modem establish the PPPoE connection (and not your computer) like I mentioned in my previous post, just click that "bridge" pull-down menu and choose whatever choice most closely resembles the concept of PPPoE on the modem.

---

### Post by stmartin on 2008-07-24
I have dual boot windows xp/ ubuntu 8.04. On my windows xp I work with bridged, and it works perfectly. It doesn't work with PPPoe. I started pppoeconf and it is configured like this:

```
noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so eth0
user "username@mt.net.mk"
usepeerdns
```

I still can't figure out what is the problem.

---

### Post by caljohnsmith on 2008-07-24
OK, I think I understand your situation better now. Your ADSL modem does not connect to your local neighborhood DSL gateway with PPPoE, because you are able to successfully use it in bridged mode. You say that Windows does not work with PPPoE, and that makes sense with how you have your modem set up right now. But that also means that Ubuntu should not need to use PPPoE either. :)

Just configure your network connection as a standard ethernet connection (use System > Admin > Network) and it should be fine. Have you all ready tried that by chance?

---

### Post by stmartin on 2008-07-24
I tried that. It didn't work. I tried even to change to PPPoE, and try sudo pppoeconf, and it didn't recognize the device. So it only works for Bridge. In the 6.06 ubuntu distribution I didn't experienced this problems, but I have never seen the computers blinking in the upper right corner.

---

### Post by stmartin on 2008-07-24
It sometimes stays longer, and only works for google.com. I tried with changing "ipv6" to "off" in /etc/modprobe.d/aliases, and still it is dropping after 2 min. Please help! Thank you. Here are also logs and additional screenshot (why I have so much ppp0, ppp1, ppp2....) ??
```
Jul 25 00:08:54 stefan-desktop pppd[8992]: Connect: ppp4 <--> eth0
Jul 25 00:08:57 stefan-desktop pppd[8992]: CHAP authentication failed: Access Denied
Jul 25 00:08:57 stefan-desktop pppd[8992]: Connection terminated.
Jul 25 00:09:03 stefan-desktop pppd[11794]: PPP session is 9547
Jul 25 00:09:03 stefan-desktop pppd[11794]: Using interface ppp4
Jul 25 00:09:03 stefan-desktop pppd[11794]: Connect: ppp4 <--> eth0
Jul 25 00:09:05 stefan-desktop pppd[11794]: CHAP authentication failed: Access Denied
Jul 25 00:09:05 stefan-desktop pppd[11794]: Connection terminated.
Jul 25 00:09:15 stefan-desktop pppd[12784]: PPP session is 9553
Jul 25 00:09:15 stefan-desktop pppd[12784]: Using interface ppp4
Jul 25 00:09:15 stefan-desktop pppd[12784]: Connect: ppp4 <--> eth0
Jul 25 00:09:17 stefan-desktop pppd[12784]: CHAP authentication failed: Access Denied
Jul 25 00:09:17 stefan-desktop pppd[12784]: Connection terminated.
Jul 25 00:09:28 stefan-desktop pppd[8992]: PPP session is 9559
Jul 25 00:09:28 stefan-desktop pppd[8992]: Using interface ppp4
Jul 25 00:09:28 stefan-desktop pppd[8992]: Connect: ppp4 <--> eth0
Jul 25 00:09:31 stefan-desktop pppd[8992]: CHAP authentication failed: Access Denied
Jul 25 00:09:31 stefan-desktop pppd[8992]: Connection terminated.
Jul 25 00:09:31 stefan-desktop pppd[8992]: Exit.
Jul 25 00:09:35 stefan-desktop pppd[11794]: PPP session is 9563
Jul 25 00:09:35 stefan-desktop pppd[11794]: Using interface ppp4
Jul 25 00:09:35 stefan-desktop pppd[11794]: Connect: ppp4 <--> eth0
Jul 25 00:09:37 stefan-desktop pppd[11794]: CHAP authentication failed: Access Denied
Jul 25 00:09:37 stefan-desktop pppd[11794]: Connection terminated.
Jul 25 00:09:37 stefan-desktop pppd[11794]: Exit.
```

---

### Post by caljohnsmith on 2008-07-24
OK, just to clarify, in that Network settings dialog box you posted, did you try just checking the "Wired Connection", unchecking all the others, and see if that works? (Of course hit the "unlock" button first). You may also have to mess with some of the options under "properties" when you have the "Wired Connections" highlighted, but I don't remember since I use wireless. And try a reboot just in case. Based on what you've said so far, I don't think you should be using a PPPoE connection from your computer to your modem; standard ethernet is fine.

---

### Post by stmartin on 2008-07-25
I have ADSL modem, connected to switch and in my PC. I use two computers. So how will I use internet on ubuntu if not with PPPoE?

---

### Post by caljohnsmith on 2008-07-25
> **stmartin said:**
> I have ADSL modem, connected to switch and in my PC. I use two computers. So how will I use internet on ubuntu if not with PPPoE?
OK, you didn't mention anything about a "switch" and two computers before; I assumed your computer was hooked up directly to your modem. ;) So again, please clarify--is your "switch" acting as a router so you have access to the internet on both computers simultaneously, or is the switch more like a mechanical switch that merely lets you choose one computer at a time to use with your modem? Or does one computer connect to the other computer in some sort of Ad Hoc network configuration? (i.e. is one computer set up to do network address translation?) Also, how is your *other* computer using the modem (is it configured for PPPoE or simple ethernet) and what operating system(s) does it have?

---

### Post by stmartin on 2008-07-25
Other PC have windows xp. The swich is letting me to connect on my computers separately, I don't use shared connection or anything like that. I am pretty mad, since on ubuntu 6.06 LTS I was using my connection without any problem, with sudo pppoeconf.

---

### Post by stmartin on 2008-07-25
I think I solved the problem. The problem was that I shouldn't disable ipv6. But I still can't see the computers blinking. Trying with PPPoE from Administrator --> Settings --> Network, and configuring the PPPoE configuration, doesn't work.

---

