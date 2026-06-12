---
title: "[SOLVED] How can I block a single IP?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by carloslosgrande on 2008-08-10
I've got a site that keeps popping up. It came in through Stumbleupon in Firefox and then managed to find its way to Opera.
I blocked it from Opera but don't know how to do the same in Firefox.
Firestarter only has options to allow...... as it blocks by default, right?
This site is InternetExplorer in chinese, 221.231.148.194/5
Any ideas on how I can do this?
Thanks.

---

### Post by 505 on 2008-08-10
The easiest way is to add the address of that site to your /etc/host file. In there, redirect the web address to 127.0.0.1 (your local computer).

---

### Post by Malta paul on 2008-08-10
Try 'Adblock plus' a Firefox add on. It works for me :)

---

### Post by carloslosgrande on 2008-08-10
[FONT="Comic Sans MS"]505, I don't know how to redirect. However I did see there is 'hosts.deny'
So I put the ip in there. Didn't know those files existed, Thanks!
Paul, I'm not sure its an ad, but I've installed adblock anyway. I'll see how things go. Thanks.[/FONT]

---

### Post by hyper_ch on 2008-08-10
make an entry in hosts.deny like:
```

ALL: www.xxx.yyy.zzz

```

---

### Post by caljohnsmith on 2008-08-10
Hyper_ch, I have a few websites that I would like to block too, so as a test I put the following in my /etc/hosts.deny file:
```
ALL: .xkcd.com
ALL: www.xkcd.com, .xkcd.com
```
I know the above is a bit redundant, but it doesn't seem to work anyway: I saved the changes, and I could still access [www.xkcd.com](www.xkcd.com) with Firefox. I hit Ctrl-Reload in Firefox to make sure it wasn't just pulling up a cached version of the page either. Also, if I "ping www.xkcd.com", the website responded fine, so it's not a problem with a cached page in Firefox. So just to make sure, I rebooted, and still I could access [www.xkcd.com](www.xkcd.com). 

So is my syntax incorrect, or is there some sort of local DNS cache in Ubuntu that I need to flush to get this to work? Thanks for any help.

---

### Post by Malta paul on 2008-08-10
Just for info. reference above, the 'Host.deny' is a text file located at:
/etc/host.deny

You could use Alt>F2 the gksudo nautilus to put you in root (Caution you are in permanent root now) go to places and page to /etc.

Good luck:)

---

### Post by bpowell2005 on 2008-08-10
> **Malta paul said:**
> Just for info. reference above, the 'Host.deny' is a text file located at:
/etc/host.deny

You could use Alt>F2 the gksudo nautilus to put you in root (Caution you are in permanent root now) go to places and page to /etc.

Good luck:)

On my machine, it's plural.../etc/hosts.deny (not /etc/host.deny)...

A subtle, but significant difference!

---

### Post by carloslosgrande on 2008-08-10
Last night I put this ALL: 221.231.148.194 
in /etc/hosts.deny
This morning restart and firefox loads thas same site again.
I had added the china list to adblock now I've added that particular ip address.
Like caljohnsmith I'm wondering if there's another step to make hosts.deny take effect?
I read the man page and it seems my entry is correct but to no effect.

---

### Post by caljohnsmith on 2008-08-10
Carloslosgrande, I think I found the answer to our question: the /etc/hosts.deny file is for *incoming* connections to services on your computer, not for outgoing connections like accessing a website for example. I think we might have to use iptables to block the outgoing requests, and there are probably other solutions as well. I'll keep you posted when I find a good solution.

---

### Post by carloslosgrande on 2008-08-10
[FONT="Comic Sans MS"]Well I'm confused - nothing new there - I thought that a site appearing on my screen was an incoming service.
I await your researches, while I have a look myself.
Thanks caljohnsmith. [/FONT]

---

### Post by carloslosgrande on 2008-08-11
[FONT="Comic Sans MS"]I found this command ;
		> iptables -A INPUT -s 221.231.148.194 -j DROP
at this site;
		[COLOR="Blue"]http://www.cyberciti.biz/faq/how-do-i-block-an-ip-on-my-linux-server/[/COLOR]
that says this;
		> In order to block an IP on your Linux server you need to use iptables firewall. First you need to log into shell as root user. To block IP address you need to type iptables command as follows:
iptables -A INPUT -s IP-ADDRESS -j DROP

and this one;	 > iptables -I INPUT -s IP_ADDRESS_HERE -j DROP					at this site;		[COLOR="#0000ff"]http://forums.serverbeach.com/showthread.php?t=2241[/COLOR]
However I've noticed that site still come up.
All the sites I found basically gave the 1st command (using -A) but no mention of any other steps.
I checked > /sbin/iptables -L and the drop is in there but not working?
[/FONT]

---

### Post by ahmatti on 2008-08-11
You could also use "Firestarter" to configure your firewall to block unwanted sites. It is an easy to use graphical tool and is in the repos. Ubuntu Hardy also has UFW [https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall) that is easier to use than iptables.

---

### Post by caljohnsmith on 2008-08-11
OK, carloslosgrande, I found out how to use iptables to block an IP address. The main problem with what you tried was using the "INPUT" table instead of the "OUTPUT" IP table. In other words, when you type in a website into Firefox, that is an *outgoing request* from your computer to get a web page from that website, which is why it should be defined in the OUTPUT IP table if you want to block it. Here's an example:
```
sudo iptables -A OUTPUT -d 208.122.19.56 -j REJECT
```
Any outgoing request from your computer to address 208.122.19.56 will be blocked. Now if you list the current iptables:
```
sudo iptables -L
```
Then you will see your rule for 208.122.19.56 under the OUTPUT category. If you decide you want to delete it, and if it is the first entry under the OUTPUT category (for example), you could delete it with:
```
sudo iptables -D OUTPUT 1
```
Or replace the "1" above with whichever entry it is. Another way of deleting it is to fully specify it:
```
sudo iptables -D OUTPUT -d 208.122.19.56 -j REJECT
```

Now the problem is that iptables only deals with IP addresses; the IP addresses of domains can change if they get a new hosting company for example, or in the case of heavily-used domains like google.com, they have more than one IP address. Thus if you want to block a specific website and not just an IP address (like me), then I would use previous poster 505's method and just add the website to the /etc/hosts file and link it to 127.0.0.1.

Anyway, hope that helps carloslosgrande.

---

### Post by carloslosgrande on 2008-08-11
[FONT="Comic Sans MS"]Hi Ahmatti, actually I tried firestarter and there isn't any option to block - it blocks by default - the options are to allow. At least thats how I understand it.
The new ufw system looks even more complex, but perhaps the gui will be simpler? Not sure if its ready yet.
Thanks.[/FONT]

---

### Post by carloslosgrande on 2008-08-11
[FONT="Comic Sans MS"]Hi caljohnsmith, thanks for that. Counterintuitive until you explained how it works.
I've now set it as per your instructions and I'm testing it now.
A whole day testing and no show of the offending IP - that worked a charm[/FONT]

---

### Post by carloslosgrande on 2008-09-18
[FONT="Comic Sans MS"]The solution from caljohnsmith worked fine except it doesn't stick. A few days ago the offending sites reappeared. I checked iptables and the line rejecting the ip address was missing.
So I ran the command again - worked, until next restart.

How can I make this permanent?

I thought a command like that would be permanent?[/FONT]

---

### Post by caljohnsmith on 2008-09-18
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]The solution from caljohnsmith worked fine except it doesn't stick. A few days ago the offending sites reappeared. I checked iptables and the line rejecting the ip address was missing.
So I ran the command again - worked, until next restart.

How can I make this permanent?

I thought a command like that would be permanent?[/FONT]
You could put the iptables command in your /etc/rc.local file, and then it will run the iptables command every time on start up. Any command in the rc.local file is run as root, so no need to put a "sudo" in front of it. And although I've never used it, you might want to check out "firestarter", which is basically a nice GUI for iptables; it will keep your changes between reboots. Good luck and let me know how it goes, or if you need any more info.

---

### Post by starcannon on 2008-09-18
If you have a router in your configuration (most broadband modems have router functions as well) you can block it at the router, keeping it from ever making it as far as your computer.

On a linksys router for instance, you can block by website under "Access Restrictions" tab.
It will be something similar on most consumer grade routers.

I never played with iptables much, I generally blacklist sites using my router.

GL

---

### Post by crjackson on 2008-09-18
Well the easist way was already disclosed in post number 2.  Redirecting using the "**hosts**" file.  **/etc/hosts** not /etc/hosts.deny

edit that file and you will see examples of how to use it properly.  It's a great tool.  I use it all the time to block certain sites from the kids computers.

---

### Post by carloslosgrande on 2008-09-19
[FONT="Comic Sans MS"]crjackson - I looked into that last time and I can't see any examples of how to redirect. I'm a bit simple.

starcannon - Yes I've got a router and I'll check that, but meantime I've just done as caljohnsmith has suggested.

Thanks caljohnsmith and everyone.


just set blocks in the router too. Silly not to think of that before really.[/FONT]

---

### Post by crjackson on 2008-09-19
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]crjackson - I looked into that last time and I can't see any examples of how to redirect. I'm a bit simple.

starcannon - Yes I've got a router and I'll check that, but meantime I've just done as caljohnsmith has suggested.

Thanks caljohnsmith and everyone.


just set blocks in the router too. Silly not to think of that before really.[/FONT]

**127.0.0.1 [www.whatever.com](www.whatever.com)**

Will block **[www.whatever.com](www.whatever.com)**

Example - the following entry 
[B]
127.0.0.1 ad.doubleclick.net[/B] 

blocks all files supplied by that DoubleClick Server to the web page you are viewing. This also prevents the server from tracking your movements.

---

### Post by carloslosgrande on 2008-09-20
[FONT="Comic Sans MS"]Thanks crjackson, that was what I wanted to know. Simple really.[/FONT]

---

