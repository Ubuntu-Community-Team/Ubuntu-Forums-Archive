---
title: "HOWTO: Firestarter Firewall"
date: 2004-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by word_virus on 2004-12-11
A guide to getting Firestarter firewall up and running on ubuntu linux 4.10-warty

Since ubuntu ships with no world-facing services, a firewall is not absolutely necessary, but since you may choose to enable a service later on (or by accident) I wrote this.

First, enable Universe in Synaptic:
Computer -> System Config -> Synaptic

Settings -> Repositories
Should be two options greyed out that say `universe', go ahead and select them then click `Ok'

Search -> `firestarter'
Double-click to select the package (ver. 0.9.3-4 as of this writing - although 1.0 has just been released), then `Apply'

Firestarter adds itself to Applications -> System Tools as `Firestarter Firewall Tool' but requires a little tweaking to use.


Open a root terminal and type `visudo'.  This will open the config file for sudo.
Find the line that says:

username     ALL=(ALL) ALL

and below it add:

username ALL=NOPASSWD: /usr/sbin/firestarter

where `username' is your log-in name.  Then, [Esc]:wq to save the file.

This will let you start firestarter when your system starts without it prompting you for your root password. Keep in mind that this is a physical security to convenience  trade-off.

Like to add firestarter to the Gnome system tray?

Computer -> Desktop Preferences -> Sessions
Select Startup Programs tab
Add
For `Command' enter: sudo firestarter --start-hidden
Ok

(NOTE: The above step is only necessary if you're running a version of Firestarter < 1.0 OR you would like to see the Firestarter GUI on start-up.  See rest of thread for details.)

Select Applications -> System Tools and RIGHT-CLICK on 'Firestarter Firewall Tool'
Select `Properties'
and replace the `Command:' field with:
gksudo /usr/sbin/firestarter

Or the firewall will complain about an `invalid root password' when you launch it from here (because of no "root" user, maybe?).

Now, go ahead and launch the firewall.  It should bring up the Firewall Wizard, which will walk you through basic firewall setup (for an over-view of this process point your browser at: [http://www.fs-security.com/docs/wizard.php](http://www.fs-security.com/docs/wizard.php));  if you're on an unnetworked computer with a single network card and an always-on internet connection configured via DHCP, just hit `OK' for the next few screens.

With the firewall running select Edit->Preferences -> General and click `System Tray Operation Mode' if you want the firewall to run Minimized by default.

Finally, the most important thing, keeping bittorrent from running slow as hell :-) :
You'll need to open up the ports bittorrent binds to, namely 6881-6999.  If you're not behind a router, do this by selecting the firestarter Rules tab and double-clicking Open Ports.  This will open a dialog box asking for the port to open, enter `6881-6999'.  

(Keep in mind that Bit Torrent will bind to ports in this range sequentially, so it's really only necessary to open as many ports as you'll have simultaneous running bittorrent sessions, about five before I start to notice a significant slowdown on my DSL connection.)

If you're behind a router you'll need to Forward those ports to your IP.  
Firestarter 1.0 provides some default policy settings to do this automatically.  Check out:

[http://btfaq.com/serve/cache/25.html](http://btfaq.com/serve/cache/25.html)

for some more thoughts on how to do this manually.

and 

[http://www.fs-security.com/docs/](http://www.fs-security.com/docs/)

for the firestarter documentation.

---

### Post by Lukano on 2004-12-12
Looks great- I had to do this manually today before I found this tutorial, but the one thing I notice is now that I've updated to Hoary, I can no longer click on the applinks in the applications->preferences menu.

Any other way to set "gksudo" in lieu of "gksu" to avoid those annoying root error msgs?

---

### Post by Ozitraveller on 2004-12-12
Yes I had the same problem, Hoary is different! I uninstalled firestarter. Nautilus just doesn't work the same in Hoary.

---

### Post by Lukano on 2004-12-13
[QUOTE=Ozitraveller]Yes I had the same problem, Hoary is different! I uninstalled firestarter. Nautilus just doesn't work the same in Hoary.[/QUOTE]

Well don't let it prevent you from using Firestarter.  I'm running Hoary with Firestarter doing NAT and firewalling for three internal machines (although dhcp was a little broken and I had to set that up manually and not let firestarter touch it).  It also starts on login in tray, just needs the gksudo adjustment to get rid of the error msg.

Also, I don't think the original poster mention the need to create the secondary eth devices (applications -> system settings -> networking) if firestarter errors (only one eth set up by default).  I also had to do that to get it working right.

---

### Post by Ozitraveller on 2004-12-13
Thanks. Iconnect to the internet through a router, so I don't need NAT, si I'll probably re-install it and ClamAV too.

---

### Post by ayam on 2004-12-23
Thanks for the useful reply but I can't get Firestarter to be hidden when I start Gnome. Firestarter appears on the system tray and also as a window on the desktop

---

### Post by UJM on 2004-12-24
regarding BT port ranges ... although they recently closed down this information from torrentbits.org is still pertinent,  ...nice guide by the way.

"It's common practice for ISPs to throttle ports associated with p2p protocols. you should avoid using  these ports when setting up your BT client". 
 
BitTorrent 6881 - 6889

---

### Post by Ozitraveller on 2004-12-27
> **word_virus]A guide to getting Firestarter firewall up and running on ubuntu linux 4.10-warty

Since ubuntu ships with no world-facing services, a firewall is not absolutely necessary, but since you may choose to enable a service later on (or by accident) I wrote this.

First, enable Universe in Synaptic:
Computer -> System Config -> Synaptic

Settings -> Repositories
Should be two options greyed out that say `universe', go ahead and select them then click `Ok'

Search -> `firestarter'
Double-click to select the package (ver. 0.9.3-4 as of this writing - although 1.0 has just been released), then `Apply'

Firestarter adds itself to Applications -> System Tools as `Firestarter Firewall Tool' but requires a little tweaking to use.


Open a root terminal and type `visudo'.  This will open the config file for sudo.
Find the line that says:

username     ALL=(ALL) ALL

and below it add:

username ALL=NOPASSWD: /usr/sbin/firestarter

where `username' is your log-in name.  Then, [Esc]:wq to save the file.

This will let you start firestarter when your system starts without it prompting you for your root password. Keep in mind that this is a physical security to convenience  trade-off.

Like to add firestarter to the Gnome system tray?

Computer -> Desktop Preferences -> Sessions
Select Startup Programs tab
Add
For `Command' enter: sudo firestarter --start-hidden
Ok

Select Applications -> System Tools and RIGHT-CLICK on 'Firestarter Firewall Tool'
Select `Properties'
and replace the `Command:' field with:
gksudo /usr/sbin/firestarter

Or the firewall will complain about an `invalid root password' when you launch it from here (because of no "root" user, maybe?).

Now, go ahead and launch the firewall.  It should bring up the Firewall Wizard, which will walk you through basic firewall setup (for an over-view of this process point your browser at: [http://www.fs-security.com/docs/wizard.php](http://www.fs-security.com/docs/wizard.php)) said:**
> http://btfaq.com/serve/cache/25.html[/url]

for some more thoughts on how to do this manually.

and 

[http://www.fs-security.com/docs/](http://www.fs-security.com/docs/)

for the firestarter documentation.


I also found this helpful.

[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

---

### Post by mark on 2005-01-04
[QUOTE=ayam]Thanks for the useful reply but I can't get Firestarter to be hidden when I start Gnome. Firestarter appears on the system tray and also as a window on the desktop[/QUOTE]
I'm also having this problem, minor though it may be.  I've followed this (very good!) HOWTO a couple of times, checked out the Debian FAQ at the Firestarter site, and I still get the Firestarter main window after login.

However, I'll continue to use it, minor glitch & all - it allowed me to discover and close a couple of "holes" in my Internet connection.

---

### Post by jdong on 2005-01-04
Someone.. wait, no, TWO people didn't read the Firestarter FAQ! GASP

firestarter --start-hidden




You guys know I was kidding about the first part right? Don't come yelling at me.... like at certain other forums...  :evil:

---

### Post by mark on 2005-01-04
[QUOTE=jdong]Someone.. wait, no, TWO people didn't read the Firestarter FAQ! GASP

firestarter --start-hidden




You guys know I was kidding about the first part right? Don't come yelling at me.... like at certain other forums...  :evil:[/QUOTE] No yelling - I'm nursing a sore throat at the moment<g>.  However, I most assuredly did read the FAQ, even printed it out.  Quoting from said document: > Open up your GNOME menu, select Preferences followed by Sessions. Switch to the Startup programs tab, pictured right.

Click Add and enter
sudo firestarter --start-hidden
as the startup command. Click OK and you're done. So I followed the instructions...and what do I find as the only entry in *Startup Programs*?  You guessed it: ```
sudo firestarter --start-hidden
``` So...how did I screw this one up? <g>

---

### Post by wallijonn on 2005-01-04
Mark,

When you log in you should find that the Firestarter program is already running. Adding it to the Panel is superfluous after the initial setup. Thereafter you can change firewall parameters from the Root Terminal.

Firewall test site: [https://grc.com/x/ne.dll?bh0bkyd2](https://grc.com/x/ne.dll?bh0bkyd2)

To start it with "root" privileges, start a root terminal ```
firestarter
```

---

### Post by mark on 2005-01-05
In re: the "Starting minimized" question, I dropped an email to Tomas Junnonen, Firestarter's "Main developer, Maintainer & Dictator for Life".  His prompt and courteous reply: > No, unfortunately this option was introduced in Firestarter 1.0, it won't work on Ubuntu's version. I think you're going to have to wait for Ubuntu to catch up a bit if you don't want to mess with the repositories.

Regards,
TomasNOTE: I mentioned in my email that I had found the 1.0.1 version in the Sarge and Sid Debian repositories but that I was hesitant to mix Ubuntu and Debian repos.

Yesterday, **wallijonn** wrote (in part): > Mark,

When you log in you should find that the Firestarter program is already running. Adding it to the Panel is superfluous after the initial setup. Thereafter you can change firewall parameters from the Root Terminal. <snip> Thanks...I want to make sure I understand - by adding the *Startup Programs* command, I'm just starting the GUI front-end for Firestarter?

---

### Post by wallijonn on 2005-01-05
[QUOTE=mark]I want to make sure I understand - by adding the *Startup Programs* command, I'm just starting the GUI front-end for Firestarter?[/QUOTE]

Yes.

Don't put it in the panel.

Start a Root terminal.

```
firestarter status
```
It should say that it is running. 

It is running because a Firestarter script is in rc0.d, rc1.d, rc2.d, rc3.d, rc4.d, rc6.d, rcS.d 

Therefore a Firestarter script will be started by all the Daemons upon any system startup level.

If you hit the panel it will fail and say something about not having root priviledges or the root password is wrong. To get around that, start a Root Terminal then issue "firestarter".

---

### Post by jdong on 2005-01-05
Oh, I knew that start hidden is a 1.0 option. Thought you guys were using 1.0.

I do have 1.0 in backports.

---

### Post by wallijonn on 2005-01-05
jdong,

I'd like to give Firestarter another shot. I find that when I start in safe mode that Shorewall 'hangs'. What rc.d is safe mode? I would think that it is rc1.d. I would therefore have to remove shorewall from rcS.d, right?, and just put it in rc2.d.

---

### Post by alainhenry on 2005-01-06
I set up firestarter with Warty and tested my system with the two websites proposed by the FS website:
[https://grc.com/x/ne.dll?bh0bkyd2](https://grc.com/x/ne.dll?bh0bkyd2)
and
[http://scan.sygatetech.com/](http://scan.sygatetech.com/)
In the first case, I have a number of positive results (i.e. good protection), such as : 
- Internet port 139 does not appear to exist! 
- Unable to connect with NetBIOS to your computer.
Some ports are stealthed (such as 80).  However, a large number of ports are closed, which this site says is not good.  
I have all services disabled in firestarter, and connect through eth0, a small router and ADSL.  Is there any way to improve this ?
Thanks
Alain

---

### Post by wallijonn on 2005-01-06
Just becasue I also hang out at abxzone.com :

[http://www.abxzone.com/forums/showthread.php?t=52074&highlight=grc.com](http://www.abxzone.com/forums/showthread.php?t=52074&highlight=grc.com)
[http://www.abxzone.com/forums/showthread.php?t=70545&highlight=grc.com](http://www.abxzone.com/forums/showthread.php?t=70545&highlight=grc.com)
[http://www.abxzone.com/forums/showthread.php?t=81149&highlight=stealth](http://www.abxzone.com/forums/showthread.php?t=81149&highlight=stealth)
[http://www.abxzone.com/forums/showthread.php?t=70241&highlight=stealth](http://www.abxzone.com/forums/showthread.php?t=70241&highlight=stealth)
[http://www.abxzone.com/forums/showthread.php?t=81209&page=1&pp=15&highlight=stealth](http://www.abxzone.com/forums/showthread.php?t=81209&page=1&pp=15&highlight=stealth)

---

