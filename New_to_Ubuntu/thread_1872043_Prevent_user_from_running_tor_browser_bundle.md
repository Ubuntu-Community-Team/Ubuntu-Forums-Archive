---
title: "Prevent user from running tor browser bundle"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by rsa137 on 2011-10-30
Hi all,

I have a desktop user account set up on 11.04 with limited internet access (firefox is locked down, other browsers can't be used, etc.). The problem is that this user can bypass all of these restrictions simply by running the tor browser bundle, either from a usb drive or locally. I would like to prevent this user from being able to do this, but I'm not quite sure how to proceed. Two options that I've considered:

1. using iptables to prevent tor from connecting. I'm new at iptables, and I've tried to configure it to block what I think are the right range of ports (9001 and anywhere from 30000 to 60500, at least). However, my attempts here haven't been successful. Any idea how I might go about doing this?

2. denying the user the rights to launch tor. Since it can be launched from a usb drive, I don't think that using chmod to deny the user privileges to run it will work (but I may be wrong). Is there a way to prevent a user from running the text file "start-tor-browser" as an executable? I know that you can do this by going into nautilus>preferences>behavior and clicking "View executable text files when they are opened". But this is not a permanent fix, and can easily be undone by the user. 

Any suggestions would be appreciated!

---

### Post by wojox on 2011-10-30
Cut off access to the usb drives.

---

### Post by rsa137 on 2011-10-30
> **wojox said:**
> Cut off access to the usb drives.

Thanks for the reply wojox. I should have mentioned that I had considered doing this as well, but I would really prefer to allow the user to access the usb drives to transfer files and access an external hd. So if I can, I would like to avoid disabling the usb (or cd/dvd) drives.

I'm working under the assumption that the user will be able to find some way to get the tor bundle into (say) their home folder. The challenge is to prevent them from running it once it's there.

---

### Post by Psyael on 2011-10-30
Block ports 9001-9030 at the router/firewall level? It's the ports Tor typically uses for getting it's directory.

That can be changed, so if you're that paranoid you may just consider blocking everything except http, https, dns, smtp, pop3, etc.

I am not old-school enough to know about these things, but it seems to me with a fair amount of chmod commands you can set it so that people can't execute files from the folders they can write to, and can't write to the folders they execute applications from. But again, I am not an expert, so I'd go for the firewall option.

Play around with it, the restricted firewall setting might defeat that. If it does, block outbound port 80 (which you should do as a matter of routine anyway to prevent trojan zombies) because it switches to that.

---

### Post by antoinethewiz on 2011-10-30
You're thinking too close to the user. You don't want to restrict your own use. What do all network requests pass through? The router (the physical layer of the OSI model). So you have to deny access at the router. Simply set up an internal firewall (in the router) that will block the port range used by that application, or block that workstation IP completely. Some routers are intelligent enough to block based on the application used. If so, that would be the way to go.

The user could then bypass you in one of two ways.
(1) Use a different router and assign your ISP connection credentials (PPP?) on that router.
(2) Use a port outside of the normal port range specified.

A few other things you can do: (1) block ALL non-standard ports at the router, (2) block at the application level with a password-protected firewall [somewhat vulnerable, as it's close to the user], (3) make the user sign an Internet usage agreement.

---

### Post by rsa137 on 2011-10-30
> **Psyael said:**
> Block ports 9001-9030 at the router/firewall level? It's the ports Tor typically uses for getting it's directory.

Yes, thanks. My initial strategy was to do something like this, but I was hindered by an unfamiliarity with the iptables commands. However, I just discovered that I can get what I want through the uncomplicated firewall using

sudo ufw deny from 192.168.2.3 to any port 9001

[FONT=Verdana]I had tried this before, but erroneously entered the wrong ip address (oops). In any case, it seems to be preventing tor from establishing a connection!


  > **antoinethewiz said:**
> You're thinking too close to the user. You  don't want to restrict your own use. What do all network requests pass  through? The router (the physical layer of the OSI model). So you have  to deny access at the router. Simply set up an internal firewall (in the  router) that will block the port range used by that application, or  block that workstation IP completely. Some routers are intelligent  enough to block based on the application used. If so, that would be the  way to go.[/FONT]

[FONT=Verdana]Yes I think that you're probably right[/FONT], [FONT=Verdana]in general, that blocking the application at the router is the most efficient approach.[/FONT]  [FONT=Verdana]Unfortunately my router doesn't seem to have that option, so it won't work in my particular case. I also don't want to block the workstation completely, since I want the desktop account to have basic limited internet connection (and the admin account to have unrestricted access, except for tor, which isn't used by this account). [/FONT]

[FONT=Verdana]In any case, it looks like using ufw will work for my purposes, at least for now. It's possible, if not likely, that there may be a way to configure tor to get around this port restriction. I'll have to play around with it a bit to see. 

Thanks to everyone for the help![/FONT]

---

### Post by donkyhotay on 2011-10-30
Be aware that if the person you're trying to limit is really interested in bypassing your security there isn't much you can do so long as they have physical access to whatever you use to lock things down. Always remember that physical access *is* root access for any device. Anything you can do to the computer, like firewalls, can be bypassed with a liveCD, assuming there isn't another option. Most routers just need a paperclip to reset and bypass that way. Personally I consider it much more effective to keep the computer in a public location (rather then a bedroom) and have rules about computer/internet usage.

---

