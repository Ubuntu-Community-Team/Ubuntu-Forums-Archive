---
title: "HOWTO: USB tethering with iPhone 3G 3.2.1 and Ubuntu 9.10 (Karmic Koala)"
date: 2009-12-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Mandor_ on 2009-12-25
There are quite a few ways to accomplish tethering with an iPhone but unfortunately most of them imply paying for proprietary software (see [PdaNet]("http://www.junefabrics.com/iphone/index.php")), overriding the carrier settings (see [IPCC files]("http://www.google.fr/search?hl=en&safe=off&client=firefox-a&rls=org.mozilla%3Afr%3Aofficial&hs=nTU&q=iphone+IPCC&btnG=Search&aq=f&oq=")) or a [WiFi ad-hoc connection]("http://www.mydigitallife.info/2008/07/27/how-to-tether-and-connect-iphone-1g-2g-and-3g-as-modem-for-internet-gateaway/"). The method I'm going to describe only requires the iPhone to be jailbroken and have OpenSSH installed which is probably a good idea anyway if you want to make the best of it. Plus since you'll be using the USB cable, battery life won't be an issue! Also, there's no compiling required so it should be pretty straighforward. In fact I'll be explaining this using as little CLI as possible!

[COLOR=red]**I tested this with an iPhone 3G 3.2.1 and Ubuntu 9.10 but it should work for any other iPhone device and distro.**[/COLOR]

[INDENT][SIZE=3]**1. Configuring the iPhone**[/SIZE][/INDENT]

This is a little outside of the HOWTO's scope, but for the sake of comprehensiveness I'm going to quickly explain how to get OpenSSH installed on the device.

[LIST]
[*][COLOR=red]**Backup your iPhone using iTunes or whatever it is you usually use!**[/COLOR]
[*]First you'll want to jailbreak your iPhone with ***[blackra1n]("http://blackra1n")***. It's completely automated and takes like 5 seconds. Your iPhone will reboot.
[*]After the iPhone comes back up, click on the blackra1n icon which should have appeared on the desktop and install ***Cydia***. When first launching Cydia it will do its thing and ask to upgrade "essential packages", let it do so.
[*]Once Cydia is done with its internal stuff, go to its search tab and install ***OpenSSH***.
[/LIST]

That's it, you're done with the iPhone's configuration. If, like me, you like to keep it as clean as possible, you can even remove the blackra1n and Cydia applications. If anything goes wrong during these steps, you can always just restore your iPhone!

[INDENT][SIZE=3]**2. Installing required packages**[/SIZE][/INDENT]

Since Apple uses some kind of weird proprietary USB protocol, connecting an iPhone to an USB port won't work right out of the box. Fortunely, some smart people reverse-engineered it and released open source software that we'll need to install.

[LIST]
[*]Launch the ***Synaptic Package Manager*** (found under *System* > *Administration*), then go to the *Settings* > *Repositories* > *Other software* menu and add the following source:
> ppa:pmcenery/ppa
Note: if you're not sporting the Koala, there are other [repos/.deb/.rpm/sources available](http://matt.colyer.name/projects/iphone-linux/index.php?title=Main_Page).
[*]Install [***usbmuxd***](http://marcansoft.com/blog/iphonelinux/usbmuxd/). This is the daemon that will enable your box to connect with the device.
[*]**[color=red]Optional[/color]**: it's not required for this particular HOWTO but you'll probably want to also install [***iFuse***](http://matt.colyer.name/projects/iphone-linux/index.php?title=Main_Page) from the same repo. It will make your iPhone be auto-mounted when your connect it to the box and a nifty icon with the iPhone's name that lets your browse its filesystem will automagically appear on your desktop. More about this in the "[ipod touch 3G/iphone sync over USB](ipod touch 3G/iphone sync over USB)" HOWTO.
[*]Reboot your computer.
[/list]

Now everything should be ready!

[INDENT][SIZE=3]**3. Tether the connection**[/SIZE][/INDENT]

 Next up are the steps to actually activate connection tethering.

[list]
[*]The usbmuxd package comes with a nifty utility called ***iproxy*** that creates a tunnel between a port of your local computer and one of the device's ports. Since the OpenSSH we installed listens on port 22 of the iPhone by default, we want to create a tunnel to it. Launch a terminal and type:
> iproxy 2222 22 &
[*]Now that the tunnel is up, we'll need a SOCKS proxy to it for applications to connect through. Conveniently, SSH allows us to do so. In the same terminal, type this:
> ssh -D 1080 -p 2222 root@localhost
This command will create a SOCKS proxy on port 1080 that leads to the tunnel which leads to the device's SSH port.
[*]Wait for a good 30 seconds while the iPhone generates a security key and stuff, then you will be prompted for the iPhone's root password which is "*alpine*" by default. If everything went well up until now, you should land on the device's command line prompt.
[*]**[color=red]Optional[/color]**: While this isn't strictly required, it's still good practice to do so: change the root password! Everyone knows the default password and with OpenSSH running on your iPhone, anybody can get in and wreak havoc everytime you connect to a WiFi network. So just type *passwd* (always in the same terminal) and pick a new one!
[/list]

Alright, now you have a SOCKS proxy which takes advantage of the iPhone's internet connection and it will remain until you close the terminal or type *exit* in it. During the next and last part, if everything goes well you'll see stuff appear in it.

[INDENT][SIZE=3]**4. Configure Firefox**[/SIZE][/INDENT]

Now that there's a SOCKS proxy available on your computer, all that's left to is configure your applications to use it. For the sake of example I'm going to walk you through configuring Firefox but many other applications can use a SOCKS proxy.

[list]
[*]Launch ***Firefox*** and go to *Edit* > *Preferences* > *Advanced* > *Connection settings*.
[*]Check *Manual proxy configuration*.
[*]Enter the following information:
> **SOCKS Host:** localhost
**Port:** 1080
**No proxy for:** localhost, 127.0.0.1
[*] Check *SOCKS v5* and leave the rest empty.
[*]Finally, type "*about:config*" in the address bar, accept that the world might come to an early end, scroll down to the "*network.proxy.socks_remote_dns*" entry and click on it to make it turn to *true*. It should also become bolded. This is required so that the DNS requests also go through the proxy.
[/list]

That's it! You should now be able to browse the web from your box through the iPhone's internet connection!

**[color=red]WARNING![/color]** If you don't want a bad surprise, be sure to check your data plan and carrier's billing policy regarding internet tethering. With mine it falls under the "fair use" category which means it's basically free but I also known it's not the case for everybody.

Now for some fake FAQ, because FAQs are cool!

Q: After having done all this, how do I simply start/stop tethering?
A: In order to start it, type the two commands in part 2 of the tutorial. To stop it, tape *exit* in the terminal and then *killall iproxy*.

Q: Do I have to configure Firefox's proxy settings everytime?
A: You shouldn't have to because if a direct connection is available, Firefox will just ignore the proxy settings. So switching back and forth between a conventionnal internet connection and the tethered connection should be transparent. If that weren't the case though, there are plugins like [FoxyProxy](http://foxyproxy.mozdev.org/) that makes switching between proxies a one-click thing.

Q: How can I use the tethered connection with command line applications?
A: You want to look into ***[proxychains](http://proxychains.sourceforge.net/)***. Once installed and configured, commands as simple as this will work:
> sudo proxychains apt-get update

I'm done, happy tethering!

---

### Post by jpeddicord on 2009-12-28
Approved; thanks for your contribution to Tutorials & Tips!

---

### Post by Whoopie on 2009-12-29
If you don't want to jailbreak your iPhone, you could try the following kernel module:

[http://giagio.com/wiki/moin.cgi/iPhoneEthernetDriver](http://giagio.com/wiki/moin.cgi/iPhoneEthernetDriver)

---

### Post by FuManShu on 2010-01-02
Diego Giagio's Module is genius.  It does not require jailbreaking, nor a SOCKS Proxy.  I would definitely recommend this route.

---

### Post by Mandor_ on 2010-01-04
Problem is the module requires Internet Connection Sharing to be active on the iPhone to work. And with most carriers, that either means paying an extra fee which is usually expensive (30€/month in my case) or overriding carrier settings (by forcing a custom made IPCC file or configuration profile) which is most likely illegal and sometimes breaks other functions. So what I'm saying is, if you're lucky enough that activating ICS on your iPhone is free then go with the module obviously but otherwise this is an overral better solution.

Plus installing OpenSSH on the device basically turns it into a shell which allows you to do all kinds of fun stuff (ever tried running an Apache server on your phone? ;)) so it's not such a bad idea anyway!

---

### Post by Zer0Nin3r on 2010-01-04
Thanks!  Worked like a champ!  Too bad the "Thank You" button has been disabled.  Helped keep the forums clean.

Been waiting for something like this for some time now.

Question:

So with this method do I have to turn on OpenSSH before enabling tethering, and also is there no need to run PDAnet?

---

### Post by Mandor_ on 2010-01-05
> **Zer0Nin3r said:**
> So with this method do I have to turn on OpenSSH before enabling tethering, and also is there no need to run PDAnet?
Yes, OpenSSH has to be on but unless you're using additionnal stuff (like the bigboss bar thingy which an SSH switch) it should automatically start when the device (re)boots.

Also, no need for PDANet indeed!

---

### Post by BAleR187 on 2010-01-08
does this work for 3gs?

---

### Post by Mandor_ on 2010-01-09
I don't have one handy to try but I see no reason this wouldn't work.

---

### Post by vladiny on 2010-01-10
Awesome! Worked for me on my 3gs. Thanks!

---

### Post by Zorael on 2010-01-10
I can't make this work, I'm not sure what I'm doing wrong.

I can start iproxy and everything looks great. I start ssh to tunnel the port, and after logging in I'm inside the phone. But when I try to use the proxy (127.0.0.1:1080), I just get a blank page (Firefox) or a timeout message (Konqueror). proxychains in Karmic seems broken, I just get an LD_PRELOAD error.

For what it's worth, I have a first-gen iPhone, so no 3G. I had hoped to get limited GPRS connectivity with this.

---

### Post by Mandor_ on 2010-01-11
Did you set *network.proxy.socks_remote_dns *to true in the "about:config" page of Firefox?

When you type the following command with the SSH dynamic port redirection running: > telnet localhost 1080Does it accept the connection?

Finally maybe this just won't work on first gen iPhones. To check install the "net-utils" package from Cydia, SSH into your iPhone and ping google or something. If that doesn't work then you're probably screwed.

---

### Post by supermanjaylin on 2010-01-24
Ok, Maybe I'm doing something wrong. I've installed iFuse and proxychains but can only tether in Firefox. Ubuntu software center, Vuze, and the rest of my apps that require internet connection are not getting a connection. Also when I search for iFuse and proxychains I can't  find them. This tutorial states that iFuse is suppose to have an icon but I don't.

I've had Ubuntu on my pc since 9.04 now I'm running 9.10 and have tethered other phones before(Blackberry and Lg Vu). I really need help with the iPhone. I've had it for 6mths it jailbroken with all the goodies installed on it. I'm just tired of switching out my sim card back a forth when I want to tether.

PLEASE HELP:confused:

Thanks

---

### Post by jrowland on 2010-02-02
What's the best way to exit out of iproxy back to the terminal?  When I'm at my shell prompt, and type in iproxy 2222 22 &, I get a "blank screen".  I'm assuming that I'm now in iproxy, and when I type in ssh -D 1080 -p 2222 root@localhost, I am taken to the iPhone logon screen.  After logging on, I get a prompt again.  When I'm done, and I type exit, I get back to the "blank screen" (i.e. no prompt).  From here, I cannot figure out how to exit (what I assume is) iproxy cleanly.  I can use the menu (file > exit), which tells me that there are still processes running and that continuing will kill those processes.  Is this the only way out?

Also, is it possible to script this whole connection method? I know I can script the invoking of iproxy, but can I pass the ssh command into the iproxy service somehow?

Thanks

---

### Post by crowdedelevator on 2010-02-07
Es this not work if you don't have Internet on your laptop? Because I configured my iPhone but when doing the source change to 9.04 in synaptic I hit walls and I'm not computer wise but  doing as told and nothing is making sense

---

### Post by Zer0Nin3r on 2010-02-28
> **jrowland said:**
> What's the best way to exit out of iproxy back to the terminal?  When I'm at my shell prompt, and type in iproxy 2222 22 &, I get a "blank screen".  I'm assuming that I'm now in iproxy, and when I type in ssh -D 1080 -p 2222 root@localhost, I am taken to the iPhone logon screen.  After logging on, I get a prompt again.  When I'm done, and I type exit, I get back to the "blank screen" (i.e. no prompt).  From here, I cannot figure out how to exit (what I assume is) iproxy cleanly.  I can use the menu (file > exit), which tells me that there are still processes running and that continuing will kill those processes.  Is this the only way out?

Also, is it possible to script this whole connection method? I know I can script the invoking of iproxy, but can I pass the ssh command into the iproxy service somehow?

Thanks

What works for me is this:

1) Open up a terminal window and create an extra tab.

2) From the first tab run the iproxy command as it say in the guide.

3) In the second tab run the ssh command to log into the iphone as the guide prompts.

4) Keep the windows open/minimize them!  Very important otherwise you're just shutting down the connections.

5) Make sure the settings in Firefox are correctly set **especially** the about:config settings!

I also find the *killall iproxy* command useful when I'm tinkering around with the settings to make sure I don't have more than one instance up and running.

Now My Question:

How do I share the connection with my other applications?  Is there a global setting I can make?  I tried the settings described in the System-->Preferences-->Network Proxy and can't get other programs to tunnel through the proxy.

---

### Post by myrice on 2010-03-14
> **Zer0Nin3r said:**
> What works for me is this:

1) Open up a terminal window and create an extra tab.

2) From the first tab run the iproxy command as it say in the guide.

3) In the second tab run the ssh command to log into the iphone as the guide prompts.

4) Keep the windows open/minimize them!  Very important otherwise you're just shutting down the connections.

5) Make sure the settings in Firefox are correctly set **especially** the about:config settings!

I also find the *killall iproxy* command useful when I'm tinkering around with the settings to make sure I don't have more than one instance up and running.

Now My Question:

How do I share the connection with my other applications?  Is there a global setting I can make?  I tried the settings described in the System-->Preferences-->Network Proxy and can't get other programs to tunnel through the proxy.

Ditto. This is my concern as well.

Other than that minor snag, great writeup!

---

### Post by anachoret on 2010-12-11
Will it work with iPod Touch?

I know it might sound strange but anyway, let say I would like to get access to wifi via iPod Touch. Does the approach described above help me?

---

### Post by Mole92db on 2011-01-25
> **anachoret said:**
> Will it work with iPod Touch?

I know it might sound strange but anyway, let say I would like to get access to wifi via iPod Touch. Does the approach described above help me?

Yeah it does, I'm using mine as a wifi adapter lol

I'm also stuck on how to get this connection to work for other things, mainly Ubuntu software center.

---

