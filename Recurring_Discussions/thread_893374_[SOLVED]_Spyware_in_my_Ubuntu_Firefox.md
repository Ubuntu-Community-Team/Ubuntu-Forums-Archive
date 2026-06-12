---
title: "[SOLVED] Spyware in my Ubuntu Firefox?"
date: 2008-08-18
forum: Recurring Discussions
---

### Post by laurenipsum on 2008-08-18
[COLOR="Red"]**Abstract:** This problem has been solved. Thanks, everyone! As it turns out, this wasn't really an Ubuntu problem, but a DNS server one, and it had something to do with meridiantelekoms.com. The problem was solved by using OpenDNS.[/COLOR]

Hello, everyone! I'm new here, hope I'm not breaking any forum rules by posting about my problem right after signing up. Anyway. Thank you in advance for your replies. :)

I didn't think it was possible, but I might have **spyware on my Firefox** - when I'm running it on Ubuntu, that is. Pages take too long to load, and when they do, one of the following happens:
[LIST=1]
[*]Most common scenario - I'm redirected to this plain search page with floating keywords (screenshots [**_here_**]("http://i537.photobucket.com/albums/ff333/laurenipsum/Forums/Screenshot1.png") and [**_here_**]("http://i537.photobucket.com/albums/ff333/laurenipsum/Forums/Screenshot2.png")).
[*]Less often - I get a page loading error (page timed out, connection interrupted, network unavailable, etc).
[*]Rare, except with Google and Yahoo and other "major" pages - The page loads normally.
[*]Rare, never happened with Google or Yahoo - The page loads normally, except that its favicon is different. The favicon looks like **_[this]("http://i537.photobucket.com/albums/ff333/laurenipsum/Forums/darnedfavicon.jpg")_**.
[/LIST]My unit is on dual-boot with Ubuntu Hardy and Windows XP. I thought there was a problem with XP that somehow found its way to my Ubuntu, but...is that even possible? 

I first noticed this problem today while I was still using Firefox on Gutsy. So I upgraded to Hardy, reformatted the primary partition. (Not the swap one, though. Only the swap exists in a different partition; I keep everything Linux in one partition, though I admit that can be bad practice.) The problem didn't disappear with the upgrade. 

I also tried installing and reinstalling Firefox; tried to browse in safe-mode. I haven't installed toolbars/any add-on in my Firefox Gutsy yet, and back when I was still using Gutsy I only had Screengrab and Flashblock. I avoid installing toolbars as a rule. I empty my private data every few minutes. Nothing works, I still get redirected to that darned page. I'm now posting this topic using Windows XP, as I couldn't properly browse the forums with Ubuntu Firefox.

What should I do?

---

### Post by Kevbert on 2008-08-18
Welcome to the wonderful world of Ubuntu.
You could try using the No Script plug-in for firefox which will only allow JavaScript and Java from any domains that you allow.  It will stop most spyware from loading and gives you control over what loads.  Go to Tools - Add-ons - Browse all Add-ons and you can get it from there.  You'll be surprised how many websites seem to want your personal browsing information.

---

### Post by linux6994 on 2008-08-18
Things to verify:

1. Under XP bring up a command prompt and do ipconfig /all and note the dns and gateway settings. Are you behind a router or not?

2. Under Ubuntu go to System > Administration > Network and ensure that you have the same dns and gateway a in XP. 

3. Under Ubuntu you can also try opendns, there are open dns servers that provide additional security if needed. These servers are most often free and just require minimal registration and can be used in either XP or Ubuntu.

Please in your next reply include the ipconfig results and Bring up a terminal window and do a netstat -r, please post results for this also.

Hope this helps.

---

### Post by aktiwers on 2008-08-18
What extensions do you have installed?

---

### Post by laurenipsum on 2008-08-18
> **Kevbert said:**
> You could try using the No Script plug-in for firefox which will only allow JavaScript and Java from any domains that you allow.

I have NoScript installed on my Windows Firefox, but not on the Ubuntu Firefox. I felt so safe with Ubuntu, didn't know I needed it. :P Wait, I'll have to reboot to try that. Will update later. 

> **aktiwers said:**
> What extensions do you have installed?

Before I upgraded to Hardy, I had Screengrab and Flashblock on my Ubuntu FF. Right now, I don't have any add-ons.

---

### Post by laurenipsum on 2008-08-18
> **linux6994 said:**
> Things to verify:

1. Under XP bring up a command prompt and do ipconfig /all and note the dns and gateway settings. Are you behind a router or not?

Okay, this is what I got. Will be posting the results from Ubuntu as soon as I reboot. Erm, sorry, how can I tell if I'm behind a router or not?

[INDENT] [FONT="Courier New"]Windows IP Configuration

Host Name . . . . . . . . . . . . : home-5b14946dcb
Primary Dns Suffix  . . . . . . . :
Node Type . . . . . . . . . . . . : Unknown
IP Routing Enabled. . . . . . . . : No
WINS Proxy Enabled. . . . . . . . : No
DNS Suffix Search List. . . . . . : meridiantelekoms.com

Ethernet adapter Smart:

Connection-specific DNS Suffix  . : meridiantelekoms.com
Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connecti
on
Physical Address. . . . . . . . . : 00-13-20-4B-48-9E
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 192.168.255.214
Subnet Mask . . . . . . . . . . . : 255.255.224.0
Default Gateway . . . . . . . . . : 192.168.224.1
DHCP Server . . . . . . . . . . . : 192.168.224.1
DNS Servers . . . . . . . . . . . : 121.1.3.208
                                    121.1.3.199
                                    203.84.191.216
                                    121.1.3.250
Lease Obtained. . . . . . . . . . : Tuesday, August 19, 2008 4:20:32 AM
Lease Expires . . . . . . . . . . : Tuesday, August 26, 2008 4:20:32 AM[/FONT][/INDENT]

---

### Post by vjkeito on 2008-08-18
have you tried another browser usch as epiphany to see if that does the same?

perhaps purgin firefox and re-installing might help?
```

sudo apt-get remove --purge firefox
```

then re-install

```
sudo apt-get update && sudo apt-get install firefox
```

---

### Post by vjkeito on 2008-08-18
> **laurenipsum said:**
> Erm, sorry, how can I tell if I'm behind a router or not?

simple, do you own a router?

what ISP are you with, did they provide you with a router (wifi?!) or have you only got a modem?

---

### Post by Kevbert on 2008-08-18
Regarding spyware and snoopware.  The problem with all browsers is it's possible to record surfing habits.  Even though Ubuntu is relatively secure when compared with windows, it's still possible to snoop as you surf. 

If you think anyone has compromised your system you could try Wireshark which is in the repos.  From that you can use the Network Tool Whois? (with Hardy Heron by default) to find out who's IP is guilty of snooping.

If anyone has any other recommendations regarding browsing security tools please post them here.....

---

### Post by ModelM on 2008-08-18
You might want to make sure Firefox isn't using a proxy.

In Firefox:

edit > preferences > advanced > network > settings

---

### Post by scottuss on 2008-08-18
You are probably behind a router. Your IP address is in the private address block (192.168.xx etc)

You should find your router and do a hard reset to make sure there are no dodgy settings within that. When you have done that, make sure you enable any security settings within the router such as firewalls etc, and disable UPnP if on there.

As for your PC, remove and reinstall firefox with no extensions and try again. Hopefully this should help

Edit: To hard reset router, locate the small hole usually on the bottom of it that says reset next to it and use a pin or other thin object to press the button in whilst the router is still switched on. The lights may flash or go out and come back on depending on model etc. 

The router should then reset with good security settings already enabled (unless it is a wireless router also in which case you should enable WPA security) to do this type into your web browser 192.168.2.1 or whatever the ip address of the router is.

---

### Post by vjkeito on 2008-08-18
as it has already been stated using [no-script]("https://addons.mozilla.org/en-US/firefox/addon/722") is a good idea.  instead of allowing all sites to run javascript you have to add them to a whitelist first (trusted).

In the days of XSS (cross site scripting) and browser hijacks its best to take a few precautions especially if you frequent dodgy sites?!

---

### Post by laurenipsum on 2008-08-18
> **linux6994 said:**
> 
2. Under Ubuntu go to System > Administration > Network and ensure that you have the same dns and gateway a in XP. 

Under the _DNS_ tab:
[INDENT]DNS Servers
121.1.3.208
121.1.3.199
203.84.191.216

Search domains
meridiantelekoms.com[/INDENT]
Under the _Hosts_ tab:
[INDENT](Please click [**_here_**]("http://i537.photobucket.com/albums/ff333/laurenipsum/Forums/settingshosts.png") for the screenshot.)[/INDENT]

This is what I got from the netstat -r command:
[INDENT][FONT="Courier New"]rivertam@RiverTam:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.224.0   *               255.255.224.0   U         0 0          0 eth1
link-local      *               255.255.0.0     U         0 0          0 eth1
default         192.168.224.1   0.0.0.0         UG        0 0          0 eth1[/FONT][/INDENT]

---

### Post by laurenipsum on 2008-08-18
> **vjkeito said:**
> have you tried another browser usch as epiphany to see if that does the same?


Yep, I'm using Galeon 2.0.4 right now to post these messages. It's doing well so far, but I'm getting paranoid. 

> perhaps purgin firefox and re-installing might help?

Let me try that again...nope. There it is again.

---

### Post by prshah on 2008-08-18
> **laurenipsum said:**
> 
I didn't think it was possible, but I might have **spyware on my Firefox** - 


First, you need to confirm if it is a firefox issue or something else; download another browser such as Opera, Galeon and/or Epiphany. You can also use lynx in a pinch;```
sudo apt-get install lynx
```

Then check the affected pages using the new browsers.

I doubt it's a browser issue; maybe your DNS/Proxy settings are being subverted somehow.

Post back results on checking with alternate browsers.

---

### Post by laurenipsum on 2008-08-18
> **ModelM said:**
> You might want to make sure Firefox isn't using a proxy.

Okay, I just checked, and it was set to "Use System Proxy Settings." I ticked "No proxy," and still the telltale "Connection interrupted" error message. (The message also crops up whenever I force an https: when typing URLs.)

> **Kevbert said:**
> If you think anyone has compromised your system you could try Wireshark which is in the repos.  From that you can use the Network Tool Whois? (with Hardy Heron by default) to find out who's IP is guilty of snooping.

I've noted this suggestion, thanks! Once I've researched a bit more, I'll get back to you. By the way, I'm finding it hard to download NoScript. Using the "Get Add-ons" function from within FF 3.0, I'm getting this message:

[INDENT][https://addons.mozilla.org/downloads/file/35113/noscript-1.7.8-fx+mz+sm.xpi](https://addons.mozilla.org/downloads/file/35113/noscript-1.7.8-fx+mz+sm.xpi)

because: Download error
-228[/INDENT]

And again, can't access the Add-ons page within the browser itself. FF is having a difficulty with https:, it seems.

> **vjkeito said:**
> simple, do you own a router? what ISP are you with, did they provide you with a router (wifi?!) or have you only got a modem?

God, sorry, I'm pretty ignorant about these things. But if you meant [**_this kind of router_**]("http://en.wikipedia.org/wiki/Image:Linksys_Router.png"), nope, I don't have it. I'm on broadband; I see this cord connected to a socket in my computer which goes out my window and culminates in an antenna on my roof. Errr, sorry. :)

---

### Post by laurenipsum on 2008-08-18
> **scottuss said:**
> You are probably behind a router. Your IP address is in the private address block (192.168.xx etc)

You should find your router and do a hard reset to make sure there are no dodgy settings within that. When you have done that, make sure you enable any security settings within the router such as firewalls etc, and disable UPnP if on there.

Thanks so much, I'll do this as soon as I understand where my router is, if I have one. /is stupid with cables and such

---

### Post by laurenipsum on 2008-08-18
Dammit. They found me.

I mean, I've been using Galeon to browse this forum, so I thought it was a FF thing, and I just got redirected to that fake search engine again. I've just installed Epiphany, currently testing it as well. Update: Epiphany has succumbed to the evil, too.

Oh, and I was finally able to install NoScript via Applications>Add/Remove. It's too late, though, the fake search engine loads nonetheless. 

Hmmm...if it's a router problem, why isn't my Windows Firefox affected?

---

### Post by prshah on 2008-08-18
Your DNS server settings seem fine in the Windows output you posted; are you using the same in Ubuntu? Open a terminal (Applications-Accessories-Terminal) and check```
cat /etc/resolv.conf
```

---

### Post by Kevbert on 2008-08-18
You can also get No-script from the [[COLOR="Red"]website[/COLOR]]("http://noscript.net/").  Another useful Add-on is [[COLOR="Red"]Adblock Plus[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/1865") which stops you having to load adverts and banners.

---

### Post by laurenipsum on 2008-08-18
I'm not sure whether they're the same, I only see one set of numbers matching. Here's what I got:

rivertam@RiverTam:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4787
#
### END INFO

search meridiantelekoms.com


**nameserver 121.1.3.208  <- Only this one matches **
nameserver 121.1.3.199
nameserver 203.84.191.216

---

### Post by LinuxRocks713 on 2008-08-18
> **laurenipsum said:**
> <snip size="huge"></snip>
nameserver 121.1.3.199
nameserver 203.84.191.216

Perhaps that's your problem. Make a backup, remove these two entries and try again.

Alternatively, try clearing all cookies, all saves passwords and logins and the cache.

---

### Post by prshah on 2008-08-18
> **laurenipsum said:**
> 
search meridiantelekoms.com


Yet another Ah Ha! moment.. see [http://www.raylanddelosreyes.com/meridiantelekomscom-defaced-are-smartbro-subscribers-safe/](http://www.raylanddelosreyes.com/meridiantelekomscom-defaced-are-smartbro-subscribers-safe/)

You should remove (or comment out) the "search" line, and change your DNS servers to OpenDNS servers (though the above ones also belong to SmartBro, ie, the same people who own the DNS servers that are set in Windows) to avoid any such problems. Post back for detailed instructions if you would like more help on how to do this.

---

### Post by Master Chief on 2008-08-18
> **laurenipsum said:**
> I'm not sure whether they're the same, I only see one set of numbers matching. Here's what I got:

rivertam@RiverTam:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4787
#
### END INFO

search meridiantelekoms.com

Change [COLOR="Red"]search meridiantelekoms.com[/COLOR] in [COLOR="SeaGreen"]search lan[/COLOR]

> **nameserver 121.1.3.208  <- Only this one matches **
nameserver 121.1.3.199
nameserver 203.84.191.216

These are fine: nsN.smartbro.net are nameservers of Smart Broadband Incorporated.

In case you do want to use OpenDNS: 

208.67.222.222
208.67.220.220

Or look for your hardware on this page (for help):
[https://www.opendns.com/start](https://www.opendns.com/start)

---

### Post by kmseven on 2008-08-18
Hey there. I've been having the same problem (whether on Ubuntu or Windows), and I'm also a SmartBro user. I'm also behind a router, though, and I tried changing my router's DNS settings to use OpenDNS. However, I can't get to any site (DNS is broken?). Any thoughts?

(Sidenote: Those fake search pages seem to come from ADS-Click. I don't have a screenshot to show that, though.)

---

### Post by Master Chief on 2008-08-18
> **kmseven said:**
> Hey there. I've been having the same problem (whether on Ubuntu or Windows), and I'm also a SmartBro user. I'm also behind a router, though, and I tried changing my router's DNS settings to use OpenDNS. However, I can't get to any site (DNS is broken?). Any thoughts?...

I have no idea, because you forgot (?) to add the router brand/type and what setting you changed!

---

### Post by kmseven on 2008-08-18
WRT54G. Added OpenDNS IP addresses to "Static DNS 1" and "Static DNS 2".

---

### Post by Master Chief on 2008-08-19
> **kmseven said:**
> WRT54G. Added OpenDNS IP addresses to "Static DNS 1" and "Static DNS 2".

Right, and what is your DNS in Ubuntu set to?  I mean that should point to your router (192.168.1.254?).

System -> Administration -> Network -> DNS

---

### Post by Orlsend on 2008-08-19
I remember you could stop this Non-sense redirect things easy

by changing **"network.http.redirection-limit"** to 0 in **"about:config"**. 

Will you try sea monkey? see what Happens? It can handle FF extensions sometimes.

---

### Post by Master Chief on 2008-08-19
> **Orlsend said:**
> I remember you could stop this Non-sense redirect things easy

by changing **"network.http.redirection-limit"** to 0 in **"about:config"**.

This preference works in all Mozilla based browsers, including Flock and SeaMonkey, because they are all build from the same tree at the beginning.

See also: [https://bugzilla.mozilla.org/show_bug.cgi?id=83471](https://bugzilla.mozilla.org/show_bug.cgi?id=83471)

However, setting this preference to 0 is not a good idea!

There is also a caveat; because this preference affects HTTP redirects only, not redirects with HTML meta tags or JavaScript. 

> Will you try sea monkey? see what Happens? It can handle FF extensions sometimes.

The official name is SeaMonkey, and yes Philip Chee (do a Google search on the man) is doing a wonderful job by porting over 80 add-ons to SeaMonkey. 

However, SeaMonkey v2 will be more back-end compatible and include most of the Firefox features, if not all any day soon.  For me the most important change for SeaMonkey v2 (aka suiterunner) was the inclusion of the add-on manager.

---

### Post by dazzlindonna on 2008-08-19
It sounds to me like your ISP or whoever supplies your internet connection has a deal with that company to reroute requests that can't be filled (bad url's) to that page.  No doubt they make money off of the deal in some way.  My satellite provider does this, and it's annoying, because it's impossible to switch to any other dns service (such as opendns), since it just won't work with my provider.  Hopefully, you don't have the same restrictions, and are able to change your dns provider.  Good luck.

---

### Post by bryncoles on 2008-08-19
my contribution to this debate is to post a link:

```
http://ubuntuforums.org/showthread.php?t=671604
```

if you're worried / paranoid about internets security (i am!)

---

### Post by amudman on 2008-08-19
using firefox and H.Heron I got a counterfeit anti-spyware software and had to remove and replace firefox to kill the thing. Suggestions, better method?? Hope this is how to post a problem.

---

### Post by billgoldberg on 2008-08-19
> **amudman said:**
> using firefox and H.Heron I got a counterfeit anti-spyware software and had to remove and replace firefox to kill the thing. Suggestions, better method?? Hope this is how to post a problem.

What?

Impossible.

Give us some details.

--

To OP: switch isp's.

I sure wouldn't tolerate this from my ISP.

---

### Post by Master Chief on 2008-08-19
> **billgoldberg said:**
> What?
Impossible.
Give us some details...

Never say "impossible" in the browser world war of madness:

[http://www.theregister.co.uk/2008/08/15/webbased_clipboard_hijacking/](http://www.theregister.co.uk/2008/08/15/webbased_clipboard_hijacking/)
[http://www.theregister.co.uk/2008/08/18/malvertizing_epidemic/](http://www.theregister.co.uk/2008/08/18/malvertizing_epidemic/)
[http://malware-test-lab.blogspot.com/2008/08/analysis-of-mystery-eb-attack-hijacks.html](http://malware-test-lab.blogspot.com/2008/08/analysis-of-mystery-eb-attack-hijacks.html)

---

### Post by billgoldberg on 2008-08-19
> **Master Chief said:**
> Never say "impossible" in the browser world war of madness:

[http://www.theregister.co.uk/2008/08/15/webbased_clipboard_hijacking/](http://www.theregister.co.uk/2008/08/15/webbased_clipboard_hijacking/)
[http://www.theregister.co.uk/2008/08/18/malvertizing_epidemic/](http://www.theregister.co.uk/2008/08/18/malvertizing_epidemic/)
[http://malware-test-lab.blogspot.com/2008/08/analysis-of-mystery-eb-attack-hijacks.html](http://malware-test-lab.blogspot.com/2008/08/analysis-of-mystery-eb-attack-hijacks.html)

That's not spyware.

Just some exploits that won't actually harm your (linux) computer.

From the links you posted I wasn't aware of the first two, but the third has been already closed by the security updates Ubuntu provides.

I'm not 100% sure, but I believe so.

---

### Post by Master Chief on 2008-08-19
> **billgoldberg said:**
> That's not spyware.

Just some exploits that won't actually harm your (linux) computer.

Your understanding of the term "spyware" seems a bit rusty so here's a link for you to freshen it up again:

[http://en.wikipedia.org/wiki/Spyware](http://en.wikipedia.org/wiki/Spyware)

Got it?  Yes, the provided links were talking about adware _and_ spyware (which we like to call malware BTW).

p.s. I also e-mailed The Register to inform them that their NoScript claim is void because this is a flash only issue.

---

### Post by Giant Speck on 2008-08-19
[IMG]http://i279.photobucket.com/albums/kk122/SpecKtacle/Spyware-1.jpg[/IMG]

Couldn't resist. :)

For those that get the meme, that is.  ;)

---

### Post by kmseven on 2008-08-20
> **Giant Speck said:**
> [IMG]http://i279.photobucket.com/albums/kk122/SpecKtacle/Spyware-1.jpg[/IMG]

Couldn't resist. :)

For those that get the meme, that is.  ;)

Haha. XD

Anyway, I got OpenDNS to work. It's quiiick. :D It seems I havn't been reading IP addresses correctly. ^_^'

---

### Post by laurenipsum on 2008-08-20
> **dazzlindonna said:**
> It sounds to me like your ISP or whoever supplies your internet connection has a deal with that company to reroute requests that can't be filled (bad url's) to that page.

But these aren't just bad URLs, a lot of them are perfectly valid locations (and I've checked many times). Hmm. I've yet to contact their tech support, though. I don't expect them to be competent, lol.

To recap everyone's suggestions, these are my options:
1. **Edit the resolv.conf file.** How do I do this? I tried editing it by opening the file, but I was told that I didn't have the necessary permissions to save changes to it. I have to do this in root mode, yes?
2. **Use OpenDNS.** Can someone walk me through this process? I totally have no idea. -_-" kmseven, since you're a SmartBro user too, can you help me? :)

Oh, and sorry, I found out that there's [**_an earlier thread_**]("http://ubuntuforums.org/showthread.php?t=818717&highlight=spyware&page=2") that discussed this problem, only it didn't end on a succesful note. Try reading the user's last message.

---

### Post by prshah on 2008-08-20
> **laurenipsum said:**
> 
1. **Edit the resolv.conf file.** How do I do this? I tried editing it by opening the file, but I was told that I didn't have the necessary permissions to save changes to it. I have to do this in root mode, yes?
2. **Use OpenDNS.** Can someone walk me through this process?

Both questions can be answered/cleared with the below process; Open a terminal and give the command```
sudo gedit /etc/dhcp3/dhclient.conf
``` Look for a line that seems like this:> #prepend domain-name-servers 127.0.0.1; Remove the "#" from the front, and add the OpenDNS servers as mentioned before, Eg the changed line  should read```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
``` Note the semi-colon at the end of the comma-seperated list.

Now, restart networking to make the changes take effect; ```
sudo /etc/init.d/networking restart
``` Check your /etc/resolv.conf file, it should now only list the OpenDNS servers.

---

### Post by laurenipsum on 2008-08-20
THANK YOU. I'm now posting with my Ubuntu Firefox without drama. Thank you so much. If it's not too much to ask, can you also tell me how can I do this with my Windows, too? :D

EDIT: Never mind, I found it on Google. LOL. Again, thank you so much for your help.

---

### Post by smartboyathome on 2008-08-20
@prshah:

It is recommended you use **gksudo** for your graphical applications, not sudo. Using sudo, if an application wants to access a user settings folder, it accesses the one in your home, and can change the permissions to root. This can thus break the program. So please, for now on, use gksudo instead of sudo.

---

### Post by Canis familiaris on 2008-08-20
> **smartboyathome said:**
> @prshah:

It is recommended you use **gksudo** for your graphical applications, not sudo. Using sudo, if an application wants to access a user settings folder, it accesses the one in your home, and can change the permissions to root. This can thus break the program. So please, for now on, use gksudo instead of sudo.

Thanks for reminding. I had read something similar before but forgotten,
I need to change my habit!!! :)

---

