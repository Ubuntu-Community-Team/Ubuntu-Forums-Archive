---
title: "Firewall recommendations"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by docJ on 2013-04-13
Hi everyone,
I have done some research about installing a firewall on my Ubuntu 12.04 64bit desktop.
Considering I am really new to anything else than WIndows, I would _strongly_ favor a GUI, as I am not yet comfortable with CLI.

Would you recommend Firestarter, or something else? Again, the easiest to setup/use the better.
I figure its preferable to have a "second best" security app I can use than the absolute best I can't use.

---

### Post by sammiev on 2013-04-13
This [thread]("http://ubuntuforums.org/showthread.php?t=1876124") really helped me.

---

### Post by Frogs Hair on 2013-04-13
I would reccomennd GUFW over Firestarter which has been development stagnent for some time.

---

### Post by fantab on 2013-04-13
**[COLOR=#000000]sammiev [/COLOR]**[COLOR=#000000]has given an excellent Link. Do go through it thoroughly. 
[/COLOR]
Ufw (Uncomplicated Fire Wall) is an excellent and simple firewall. And it comes as a default in Ubuntu. It can be configured very easily, even if you are a noob, with CLI. I strongly recommend it. Just follow these **[instructions]("http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/")**. If you need anymore help then you are most welcome to ask.

The GUI for Ufw is [GUFW]("https://help.ubuntu.com/community/Gufw"). You can install it from ubuntu software center.

---

### Post by docJ on 2013-04-13
Thanks, it convinced me to use gufw.
The tutorial seems a little outdated (ref to 10.04). It also lacks pictures (worth a thousand words...;o) 
As soon as I tried to add rules, I froze as I could not "match" the instructions to what I tried to do.
Are there updated, illustrated setup instructions out there? 

Also, I might need help to determine what rules I need to add, which depend on my use of the system. 
In the link, they were adding Transmission rule; I have no need for that.
Basically my Ubuntu is a media file repository, so I need the SMB shared drives accessible from my home network pc's. 
Apart, from that, I will use Firefox now & then, when I need help like now. I guess I need a rule for the software update.
No email, chat, so its pretty basic need in fact.

Thanks for helping me.

---

### Post by docJ on 2013-04-13
I think I found a (good for hopeless noob like me) gufw tutorial here:[HTML]https://help.ubuntu.com/community/Gufw[/HTML]

---

### Post by docJ on 2013-04-13
The tutorial [**[COLOR=#000000]sammiev[/COLOR]**]("http://ubuntuforums.org/member.php?u=628319") offered me was suggesting to immediatly deny all outgoing traffic, as by default is is enabled, and then add rules
The  tutorial  I linked just above, as well as this one (listed at the end of the former) [HTML]http://www.techotopia.com/index.php/Using_gufw_and_ufw_to_Configure_an_Ubuntu_11.04_Firewall[/HTML] seem to suggest to leave outgoing to allow.

Any advice?

---

### Post by fantab on 2013-04-13
So you didn't check my GUFW link then... :-o

You should allow only selected and deny the rest.

---

### Post by docJ on 2013-04-13
Ooops, no, sorry
 I missed it :redface:
I only looked at the first and realize it was mostly CLI-related
Give me a moment and please forgive me.

I just realized its the same great one that I "found" in post 6

---

### Post by coffeecat on 2013-04-13
@docj, just a bit of advice about using the forum software. When you post a link and want it to be a hyperlink, don't do this:

> **docJ said:**
> I think I found a (good for hopeless noob like me) gufw tutorial here:[HTML]https://help.ubuntu.com/community/Gufw[/HTML]

> **docJ said:**
> [HTML]http://www.techotopia.com/index.php/Using_gufw_and_ufw_to_Configure_an_Ubuntu_11.04_Firewall[/HTML]

HTML BBCode tags are for posting html code. If you want a hyperlink, simply post the URL in your post and the forum software will do the rest for you. If you want to make a hyperlink of some text, simply highlight the text, click on the link button in the toolbar in the advanced editor and again the forum software will do the rest.

Good luck!

---

### Post by sammiev on 2013-04-13
I deny all in and all out. Then I allow out the 8 or so in the first post. I use a VPN as well so I also had to add that. A lot of good reading so take your time.

---

### Post by docJ on 2013-04-13
Sorry about using HTML code.
Back to the great tutorial ([https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)), once mine is unlocked and turned "on", it shows incoming: deny and outgoing: allow, similar to pics on tutorial.

Before I go into rules, I just tried to access my Ubuntu pc data shared drives from a windows 7 computer and I was expecting to be blocked, as I have not created any rules/exceptions yet for Ubuntu incoming traffic.
Surprinsingly enough, I was let in. Do I need to reboot?

Something else, if I go to the dash and open the gufw from there, it shows to be off (but prompts me for user p/w), once I enter p/w, it shows to be on, is this normal?

---

### Post by docJ on 2013-04-13
With incoming and outgoing both set to deny, I can no longer browse my home network from Ubuntu (result of outgoing denied with no exceptions; This is normal for now.
But again, why am I able to browse Ubuntu pc from my Windows pc

---

### Post by docJ on 2013-04-13
OK, I rebooted windows and it now shows all Ubuntu shared drives as unavailable, which makes sense considering...

I must be blind and a little thick, but I can't seem to find instructions about creating rules while in graphical GUFW; I am pointed on UFW's side for more on rules, but then the instructions are for CLI

Sorry for being such a (fill in the blank)

---

### Post by docJ on 2013-04-13
I have gufw set to on, both incoming and outgoing set to deny
I created 2 rules so far, both under Preconfigured tab;
Allow-in-service-Samba
 Allow-out-service-samba
As soon as I close the Firewall: Add Rule window, I am able to access Ubuntu from/to Windows =D>

However, if I add:
Allow-out-service-http
Firefox is (still) unable to display webpage :(

---

### Post by maglinu on 2013-04-13
Add simple rule - allow out, tcp - now find the port you want - 80 for http

---

### Post by docJ on 2013-04-13
I did just that, Firefox still unable to display webpage...

---

### Post by docJ on 2013-04-13
Looking at the list of rules, I notice the absence of both dns and dhcp rules. I beleive those 2 to be essentials.
I am looking at all 3 tabs, Preconfigured, Simple and Advanced and see no trace of DNS/DHCP I can allow...

---

### Post by maglinu on 2013-04-13
Have another look at the guide - you need port 53 tcp/udp for DNS. You may also need 67 and 68 udp for dchp.

---

### Post by docJ on 2013-04-13
I just added all of these: 
DHCP Access - Port 67 and 68 UDP
Web Access - Ports 80 and 443 Protocol TCP
DNS Access - Port 53 Protocol TCP and UDP

Navigation is OK, thanks, I don't thing I need anything else.
 I am wondering about the automated software updates I have received from Ubuntu Software Center (2 or 3 times in the last week);
 Are those being let in?

Refering to the guide, I have not added these:
Email Access - Ports 25 and 110 , 143 Protocol TCP
Bittorrent Access Through Transmission

I have no plan whatsoever to use any email client or p2p on this machine.

Thanks again to all for your patience

---

