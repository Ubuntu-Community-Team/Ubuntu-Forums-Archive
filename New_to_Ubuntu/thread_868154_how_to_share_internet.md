---
title: "how to share internet"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by winsane on 2008-07-23
I need to share my windows internet connection with my linux computer because I don't have a working GUI on my linux box and can't get updates until I am on the internet.  My firewall requires a login but never prompts for a login when I try to ftp or access the internet, so I want to use a windoze PC for my netwqork connection.  How can I share my windows internet connection with linux?

---

### Post by LowSky on 2008-07-23
What kind of internet connection DSL, Cable, Dial-up

A cheap router could be a better solution but try this if you dont want to do that

try these instructions form the Windows PC

[http://www.annoyances.org/exec/show/ics_xp](http://www.annoyances.org/exec/show/ics_xp)

---

### Post by winsane on 2008-07-23
Ok..That seems like a big pain and I can't get a router because it is not my network.  Is there a way to get a list of all the packages I need to get gnome up and running and somehow copy them from an existing linux computer down to a dvd?  If I can get a gui up and running, th4en I can use a browser.  Once I can browse, the firewall can prompt me for a user and password.  Then I can get authenticated to use the internet.  In any case, I need to get a list of the needed packages for gnome or kde and burn them to dvd. Where can I find this info?

---

### Post by iaculallad on 2008-07-23
> **winsane said:**
> Ok..That seems like a big pain and I can't get a router because it is not my network.  Is there a way to get a list of all the packages I need to get gnome up and running and somehow copy them from an existing linux computer down to a dvd?  If I can get a gui up and running, th4en I can use a browser.  Once I can browse, the firewall can prompt me for a user and password.  Then I can get authenticated to use the internet.  In any case, I need to get a list of the needed packages for gnome or kde and burn them to dvd. Where can I find this info?

I'd say you try the [AptOnCD]("http://aptoncd.sourceforge.net/") utility. It's available in the repo:

```
sudo apt-get install aptoncd
```

---

### Post by Ptero-4 on 2008-07-23
Would w3m work fine for that (it's a console browser that doesn't need X11).

---

### Post by iaculallad on 2008-07-23
> **Ptero-4 said:**
> Would w3m work fine for that (it's a console browser that doesn't need X11).

My mistake, I misread your first post (***"because I don't have a working GUI on my linux box"***). Actually aptoncd works in GUI mode.
And that does not support your situation.

---

### Post by hariprs on 2008-07-23
1. Just enable internet connection sharing in windows 
2. Connect your windows & Ubuntu using a cross over ethernet cable. 
3. Assign IP address for windows & Ubuntu in same subnet.
4. Enjoy the internet from your Ubuntu.

---

### Post by winsane on 2008-07-24
Is there a way to transfer the packages that are already installed on one linux PC and send via the crossover cable to the other linux pc?

---

### Post by Ptero-4 on 2008-07-24
On the working linux PC clean your apt cache. Then type
```
sudo aptitude reinstall -d *gnome-core firefox*
```, this will download all the stuff you need for your GUI and firefox without actually installing anything. After it is done downloading copy the contents of /var/cache/apt/archives to the linux box that doesn't have internet (it needs to be put into /var/cache/apt/archives).

---

