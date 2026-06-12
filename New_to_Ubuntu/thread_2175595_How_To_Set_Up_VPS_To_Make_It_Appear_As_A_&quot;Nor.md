---
title: "How To Set Up VPS To Make It Appear As A &quot;Normal&quot; Computer And Not A Server ?"
date: 2013-09-19
forum: New to Ubuntu
---

### Post by Omnipresence on 2013-09-19
Hello Ubuntu Community !

Noob in need of some advice. ( Please tell me if this is the wrong section and where I should post this )

I know little about VPS and Ubuntu so a "computer guy" will set it up for me. I would like to get some advice about the stealth side of things.

I want to get a couple of fixed IP VPS's running Ubuntu and use them only to access a couple of websites stealthily and I have been told that a VPS running Ubuntu would be best way to do this.

What is the best way to set up a VPS to make it appear to the outside world that it is a "normal" computer and not a server ?

I also want to be able to gain access to the VPS from my laptop via a dial up connection at times, I know it will be slow but I don't need to spend much time it - Could I access it with dial up ?

I have been told to use CentOS 5 and install GNOME along with FireFox and RealVNC server for remote access. Are there any other options for remote access ?

Is there a specific desktop environment that would be the better choice for stealth?

Do I need to do something about the ports that are open or used to disguise the fact that its a server ?

Can anyone advise what else I should do to disguise the fact that its a server ?

Any help would be greatly appreciated ! - Thanks!

---

### Post by kanikilu on 2013-09-20
I have no idea what "access a couple of websites stealthily" means. How do you intend to access these sites? If you are just simply visiting a website in a browser and not doing anything illicit or against the ToS, first of all, I kind of doubt that they would care if you are running a server. Second, if you just want to hide that fact for some reason, install the User Agent Switcher add-on in Firefox and choose one of the pre-defined/generic Windows desktop user agents.

As far as "disguising" your server from the internet at large, obviously don't run services you don't have to (and change common ports of the services you must run), and of course, use a firewall.

Look into the various methods to "harden" Ubuntu (I don't know CentOS - this is an Ubuntu-centric forum, afterall...). [https://www.google.com/search?q=harden+ubuntu+server](https://www.google.com/search?q=harden+ubuntu+server)

VNC over the internet, and on dial-up? Good luck with that...I think that'll be painfully slow, and also insecure unless you tunnel VNC through SSH.

---

### Post by Omnipresence on 2013-09-20
Thanks[COLOR=#000000] Kanikilu

I want to go thru the VPS to access a website. It is nothing illicit, I was a user on the website but was removed through no fault of my own and would like to regain access.
 
The website implements many security features like browser finger printing and the use of Java to determine if you are a previous user. They have IP ranges for popular VPN's and can see proxy servers and mac addresses etc. 

If I can get it to look like a computer. [/COLOR]VPS would be the best option as[COLOR=#000000] it would be fixed IP, the cookies will remain in place plus I can also access from anywhere as I travel a lot.
[/COLOR][COLOR=#000000]
Did you mean [/COLOR]install the User Agent Switcher add-on in Firefox on the VPS ?

Thanks again

---

### Post by mastablasta on 2013-09-20
why not talk with website owner then?

if you just want anonimity on access use Liberte linux or Tails OS

---

### Post by Toz on 2013-09-20
I have removed your other duplicate thread on the same issue. Please do not create duplicate threads as it dilutes community effort.

---

### Post by Omnipresence on 2013-09-20
> **Toz said:**
> I have removed your other duplicate thread on the same issue. Please do not create duplicate threads as it dilutes community effort.

Apologies, I was unsure which section to post the question - Is this the correct section?

---

### Post by Omnipresence on 2013-09-20
> **mastablasta said:**
> why not talk with website owner then?

if you just want anonimity on access use Liberte linux or Tails OS

If I needed anonymity I could use TOR or a VPN. If I tried to access the website with TOR, VPN or anything other than what appeared a normal computer, access would be blocked.
I want to set up a VPS to appear as a normal computer and not a server, showing IP cookies etc, All the things a standard computer would show. 

Thanks

---

### Post by Omnipresence on 2013-09-26
Anybody have any thoughts of a solution to this problem ?

Thanks

---

### Post by 1clue on 2013-09-26
I think the best approach to solving your dilemma is to approach the site admin for the web site you're talking about and maybe they will remove you from the black list.

The thing is, if I understand your request correctly (I'm pretty sure I do) then what you're asking would help mask your identity during illicit activities.

While setting this sort of thing up for your stated purpose might not violate THIS site's ToS (terms of service), it probably will violate the other's, and as soon as somebody figures it out you'll be banned there again.

Helping set that sort of thing up for the type of illicit activity that comes to mind when I read your posts WOULD violate this site's ToS.  I seriously doubt you're going to get much help here.

---

### Post by Omnipresence on 2013-09-27
I have approached the site admin but they do not allow access from certain countries. I will be travelling and needing access from these countries.

You misunderstand, I do not need to mask my identity, I need to mask the fact that I am accessing the website from a country that they don't approve of because somebody decided that an embargo would be good thing ...

A similar thing can also be achieved by VPN but I would rather go the VPS route.

Can anyone offer a constructive opinion ?

Thanks

---

### Post by 1clue on 2013-09-27
You could get a remote session to a box in a non-embargoed country, then run your browser from there.

Clearly a forum moderator has already looked at this thread and that person doesn't seem to think your post is unethical, but I'm just not going to cooperate in any sort of identity masking. Even if your intent is ethical, this thread could be viewed by some unknown party with different goals.

---

### Post by 1clue on 2013-09-27
There's really not that much difference between Ubuntu Server and Ubuntu Desktop.  It's the same core software but just no GUI.  If you have an Ubuntu desktop box which can connect to the remote site, then chances are you can get an Ubuntu-based server to go too, all you need to do is add a browser.

---

### Post by sandyd on 2013-09-27
If your looking for an easy solution, try NoMachine NX - does a resumable session over SSH.

Unless your really careful though, you _will_ need more than 1G ram. You may be able to squish that below 1G if you dont use firefox, and are running a stripped down version of Ubuntu Server. Perhaps something like opera.

Perhaps OpenBox + opera/chrome + openjre will get you what you want.

You mention java in the site. With java, I think it will go over 1GB ram because java is heavy.

Something like
```
sudo apt-get purge apache2* bind9
```
Will get rid of the stuff thats installed on the VPS by default (the rest are probably needed)

---

### Post by CharlesA on 2013-09-27
No mention of what site it is either. I really wouldn't run a GUI on a VPS, but if I needed one, I would run NX, like sandyd suggests. You will also probably run into memory issues unless you get a high memory VPS and those can get quite.. pricy.

---

### Post by Elfy on 2013-09-28
>  I need to mask the fact that I am accessing the website from a country that they don't approve of because somebody decided that an embargo would be good thing ...
I'm afraid this is not the place to come to evade other countries/companies/peoples policies at all.

Closed.

---

