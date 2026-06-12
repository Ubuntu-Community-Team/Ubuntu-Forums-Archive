---
title: "Installing and Configuring Polipo"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by mrgoodfox on 2011-10-16
I want to install and configure Polipo. I've already installed it but from what I understand [URL="http://hack2live.blogspot.com/2009/12/how-to-configure-polipo-proxy-on-ubuntu.html"]there is still another step to configure it.
[/URL]
When I browse to open the /etc/polipo/config file, it opens as a read only file. I cant edit it at all.

What am i doing wrong?

---

### Post by Lisiano on 2011-10-16
It is read-only because it's a system file. Open a terminal (Ctrl+Alt+T) and type this
```
gksudo gedit /etc/polipo/config
```A box will popup, give it your password. Now you can edit the file

Edit: Darn phone auto-correct!

---

### Post by mrgoodfox on 2011-10-16
Thanks. That allowed me to edit it. 

I installed Polipo for use with Tor. But Tor still doesn't work (even though Polipo is installed). The option to "Use Polipo" doesnt even come available anymore (Ive restarted firefox few times too)

---

### Post by bodhi.zazen on 2011-10-16
See if this helps : [http://bodhizazen.net/Tutorials/TOR](http://bodhizazen.net/Tutorials/TOR)

---

### Post by mrgoodfox on 2011-10-16
I feel like Im lost. Too much info , lol

**Update:**

How do i do this

> Make sure Universe and Multiverse Repositories are enabled.

---

### Post by Lisiano on 2011-10-17
Open a terminal (Ctrl+Alt+T) and just type
```
software-properties-gtk
```
Now just make sure (universe) and (multiverse) have a tick in their checkbox.

---

### Post by mrgoodfox on 2011-10-17
> **Lisiano said:**
> Open a terminal (Ctrl+Alt+T) and just type
```
software-properties-gtk
```
Now just make sure (universe) and (multiverse) have a tick in their checkbox.

When i type that , it says "You need to be root to run this application"

---

### Post by Lisiano on 2011-10-17
This is unusual, just prepend gksudo to it like you did before with gedit

---

### Post by mrgoodfox on 2011-10-17
That worked. But (universe) and (multiverse) were already checked so the reason Polipo wasnt working wasn't this.

---

### Post by bodhi.zazen on 2011-10-17
> **mrgoodfox said:**
> That worked. But (universe) and (multiverse) were already checked so the reason Polipo wasnt working wasn't this.

You said polipo was already installed, so that was not the problem.

Did you look at the link I gave you ? It has detailed instructions for TOR and polipo.

---

### Post by mrgoodfox on 2011-10-17
I did follow that document (i think to the T , but obviously I did something wrong).

Even though it seems like i have polipo installed and configured, when I go to the Tor Button settings in Firefox I dont have the Polipo checkbox active like it is shown  in this link: [http://bodhizazen.net/img/Torbutton_defaults.gif](http://bodhizazen.net/img/Torbutton_defaults.gif)

---

### Post by bodhi.zazen on 2011-10-17
What port are you running polipo on ?

Is it running ?

Manually enter your poliop.

IP address is 127.0.0.1 and port is the port you are running polipo on, lol.

---

### Post by mrgoodfox on 2011-10-17
I added this code to the config file of Polipo (per instruction on the link you sent)

```
proxyAddress = "127.0.0.1"
proxyPort = 8123
allowedClients = 127.0.0.1
allowedPorts = 1-65535
proxyName = "localhost"
disableLocalInterface = true
disableConfiguration = true
dnsUseGethostbyname = yes
disableVia = true
censoredHeaders = from,accept-language,x-pad,link
censorReferer = maybe
maxConnectionAge = 5m
maxConnectionRequests = 120
serverMaxSlots = 8
serverSlots = 2
tunnelAllowedPorts = 1-65535
chunkHighMark = 67108864

localDocumentRoot = ""
disableLocalInterface = true
disableConfiguration = true

#use socks4a for TOR
socksParentProxy = "localhost:9050"
socksProxyType = socks4a

# Alternately use socks5
# See : here
# socksProxyType = socks4a
```

So I'm assuming it's on port 8123. right? 

When I check my global IP address online its not the 127.0.0.1 though.

---

### Post by bodhi.zazen on 2011-10-17
localhost is 127.0.0.1 

[http://en.wikipedia.org/wiki/Localhost](http://en.wikipedia.org/wiki/Localhost)

You defined the port here:

> proxyPort = 8123

for the tor buttons to work you need to change that to 8118 (as I indicated on my web page).

You will then need to restart polipo and TOR (after editing the config files) ;)

---

### Post by mrgoodfox on 2011-10-17
Ok. I made that change and then went to restart Polipo and got this error:

> 
Restarting polipo: Couldn't open config file /etc/polipo/config: 2.
 

I think it's because in the tutorial it was the config file was moved to config.orig. Right?
```

sudo mv /etc/polipo/config /etc/polipo/config.orig

```

Should i uninstall Polipo and do it from scratch?

---

### Post by bodhi.zazen on 2011-10-17
> **mrgoodfox said:**
> Should i uninstall Polipo and do it from scratch?

Reinstalling polipo is not going to help you.

You really need to stop for a minute and read the documentation.

On the web link I gave you is a link to the recommended configuration file for polipo. You can download that , or you can make modifications.

The web page I gave you also goes through the default ports and when to use which port, as well as some modifications I use.

You save, or modify, the config file of your choice at /etc/polipo/config

and then restart polipo.

---

### Post by mrgoodfox on 2011-10-17
Ok. I'll go through the whole document line by line.

First problem: where [it says]("http://bodhizazen.net/Tutorials/TOR") > Using any method, edit your repositories and add the Tor repository :

I go to Edit Software Sources ([as instructed here]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Repositories%20in%20Ubuntu")). My password is not opening the edit area though!

I had the same password problem with [another issue]("http://ubuntuforums.org/showthread.php?t=1863012&page=2") i'm trying to fix. **gandaran** told me in that thread to use 'sudo' instead of 'gksu' in terminal and it would work.  and it did work (using sudo on command line and my password worked).

so first question, what's the deal with the whole password thing? why do some times it's accepted and others not?

---

### Post by bodhi.zazen on 2011-10-17
> **mrgoodfox said:**
> so first question, what's the deal with the whole password thing? why do some times it's accepted and others not?

One would presume a typo.

---

### Post by mrgoodfox on 2011-10-17
I figured it might be that but i've entered the psasword 100 times by now and it just doesn't work half the time. If I use the terminal to open something, the password works though. (how can i open the Edit Software Center page with terminal?)

Also, when I try to run the following line, I get the error that follows it:

> gpg --keyserver keys.gnupg.net --recv 886DDD89

> 
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpgkeys: key 886DDD89 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0



---

### Post by bodhi.zazen on 2011-10-17
> **mrgoodfox said:**
> I figured it might be that but i've entered the psasword 100 times by now and it just doesn't work half the time. If I use the terminal to open something, the password works though. (how can i open the Edit Software Center page with terminal?)

Also, when I try to run the following line, I get the error that follows it:

You are sort of chasing your tail, spinning your wheels.

You already have installed TOR and polipo. Adding repositories, gpg keys, reinstalling, etc is not going to help you one bit.

You need to edit a few configuration files.

---

### Post by mrgoodfox on 2011-10-17
So, i feel like an idiot.

All this time I wasn't turning Tor, ON, on firefox because the Polipo checkbox in the screen shot here ([http://bodhizazen.net/img/Torbutton_defaults.gif](http://bodhizazen.net/img/Torbutton_defaults.gif)) wasn't active for me (It still is not).

But when I switched Tor ON and went to a TOR checked site, it looks like its working. 

I still dont know why my Polipo checkbox isnt active. Does it matter at this time?

---

### Post by bodhi.zazen on 2011-10-17
> **mrgoodfox said:**
> I still dont know why my Polipo checkbox isnt active. Does it matter at this time?

As long as TOR shows you are using a tor exit node, you are good to go.

---

### Post by mrgoodfox on 2011-10-17
ok. Thanks for the help. I'll figure out why Polipo is playing hard to get after I've spent a little more time on Linux.

---

