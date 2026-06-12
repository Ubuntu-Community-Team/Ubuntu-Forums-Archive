---
title: "Paypal won't load on any browser"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by rkstarr on 2014-07-10
Running 12.04 on Asus laptop.  Have suddenly in last month not been able to load paypal site with any browser while all other sites work.  Have tried Firefox, Chromium, Opera and Midori.  Can access paypal on a windows desktop using internet explorer operating through the same wireless modem.  Any suggestions or do I have to wait for the 14.04.1 release to update the whole operating system?

---

### Post by Vladlenin5000 on 2014-07-10
Hi, welcome.

What is just reported is weird, to say the least.
What exactly happens - or what do you see - when trying to access Paypal's website?
Also, if you already tried in Windows with Firefox and Chrome and the results were the same you experienced withe the same browsers in Ubuntu that suggests something wrong in your profiles in both browsers. That "something wrong" would then be synchronized in any other instances (other computers and/or different OSs) as soon as you login in any Google service (Chrome) and similarly in Firefox.

---

### Post by rkstarr on 2014-07-10
Hi.  I do not see anything.  The web sites will not load.  I get a timed out or web site unavailable message.  But when I check web sites that check whether the paypal site (and other sites) is down they say it isn't.  I just tried it on a windows PC using firefox and it loaded fine and I could get into my account.  
I have seen reports on web sites for years ago when people had problems from time to time on ubuntu but nothing for recently.  I am suspecting paypal have upgraded their site but my settings, whatever they are, no longer are up to scratch.  I do not have problems with other sites other than they seem to slow down over time after opening a few pages and youtube and dailymotion often freeze for no reason and I have to move to another browser or reboot completely.

---

### Post by Vladlenin5000 on 2014-07-10
Yes, you have a problem but not the one I though...
You're problem with Paypal, now that they added that movie in the background, and the Youtube/Dailymotion freezes, are probably the same.

Have you installed the *ubuntu-restricted-extras*? That should have gave you the currently supported version of Flash for Linux... If not, how did you install the Flash?

---

### Post by rkstarr on 2014-07-10
Hi.  I have not installed ubuntu-restricted-extras?  I did look at it at one stage when I was having one problems with a few other sites but decided to try different browsers and also wait for the 14.04LTS.  On Firefox it has the  Shockwave Flash 11.2 r202 loaded (libflashplayer.so) as a plugin.   Also on Chromium and firefox I have set them up so that flash is automatically disabled and I am asked to activate - I did this to speed up browsing of web sites as most flash is annoying adverts or unnecessary glitz.

---

### Post by Vladlenin5000 on 2014-07-10
So try to enable it?!? Perhaps that's just what you need for Paypal because it runs something that may require it but in the background. As such I doubt it can trigger the on demand activation.

---

### Post by rkstarr on 2014-07-10
Well if it were just that simple!  I removed the flash blocks on firefox and chromium and rebooted laptop as well.  Made no difference.  Could not load the paypal site on any of the four browsers I previously listed.  I also googled paypal to get links to other parts of their site rather than just the main opening page.  Same problem.  Would not load or said the site was unavailable.  

Will have to put this problem away for another day.  

Thanks for your suggestions to date.

---

### Post by Vladlenin5000 on 2014-07-10
It works in all my browsers - I have a lot more than the ones you mentioned - as it always worked and so does Youtube and any other video streaming website... The only thing not out-of-the-box in my systems, besides new programs, are the aforementioned restricted extras. I never bothered to find & install "alternative" Flash because it just works as expected (so far...). I don't use those ad blockers either and that perhaps makes so difference although I'm positive that just disabling them like you did should be enough as troubleshooting.

On last suggestion is to install Chrome - along or instead of Chromium. The difference is Google's Chrome comes with its own (updated) Flash version and that alone can make a difference. Of course, as soon as it synchronizes your user's profile from Chromium (or just by logging in any Google service) the problem may reveal itself again. If so, you'll know where the problem is...

---

### Post by coffeecat on 2014-07-10
I don't have any really constructive suggestions to add, but just to say that the paypal site works just fine here in both Firefox and Chromium in Ubuntu 14.04. And the background video is a .mp4. 

You can upgrade to 14.04 from 12.04 without having to wait for the 14.04.1 point release - if you want details I can post them - but I'd be surprised if that solves your problem. Offhand I can't think of a reason why 12.04 should suddenly stop allowing you to access paypal in four different browsers.

Long shot this: you can't access paypal from 4 browsers in Ubuntu, but you can on the same local network with Windows and IE. Have you blacklisted paypal in your Ubuntu hosts file and forgotten about this, by any chance?

---

### Post by Vladlenin5000 on 2014-07-10
> **coffeecat said:**
> And the background video is a .mp4. 

Then even if the system has no codec for MP4 it still would show the page except for the background video?

---

### Post by coffeecat on 2014-07-10
> **Vladlenin5000 said:**
> Then even if the system has no codec for MP4 it still would show the page except for the background video?

Just so that we can be sure that we are all looking at the same thing, this was the URL for the UK paypal site that I was looking at:

[https://www.paypal.com/uk/home](https://www.paypal.com/uk/home)

I also substituted us, es and fr for uk in the URL to get the USA, Spanish and French sites and they also seemed to work just as well. I got bored after four, but no doubt other country codes would work too.

---

### Post by rkstarr on 2014-07-10
Hi all.  I noted that while the other browsers simply failed, Chromium had a tab for more information re a load failure and when I clicked on that I got a DNS error message:

 [COLOR=#444444][FONT=Helvetica]The server at[/FONT][/COLOR][COLOR=#444444][FONT=Helvetica] [/FONT][/COLOR]**[www.paypal.com](www.paypal.com)**[COLOR=#444444][FONT=Helvetica] [/FONT][/COLOR][COLOR=#444444][FONT=Helvetica]can't be found, because the DNS lookup failed. DNS is the network service that translates a website's name to its Internet address. This error is most often caused by having no connection to the Internet or a misconfigured network. It can also be caused by an unresponsive DNS server or a firewall preventing[/FONT][/COLOR][COLOR=#444444][FONT=Helvetica] [/FONT][/COLOR][COLOR=#444444][FONT=Helvetica]Chromium[/FONT][/COLOR][COLOR=#444444][FONT=Helvetica] [/FONT][/COLOR][COLOR=#444444][FONT=Helvetica]from accessing the network.
[/FONT][/COLOR] [COLOR=#A0A0A0][FONT=Helvetica]Error code: DNS_PROBE_FINISHED_NXDOMAIN[/FONT][/COLOR][COLOR=#444444][FONT=Helvetica]

And before you ask - I am not aware of any firewall settings set up or loaded Paypal on to any block lists.  I previously had access up to a month ago (or thereabouts).

Hopefully this will give you something to get your teeth into?

Any suggestions appreciated.

[/FONT][/COLOR]

---

### Post by coffeecat on 2014-07-11
Since you can access the paypal site in Windows but you get a DNS failure in Ubuntu, let's see which DNS servers you are using in the two operating systems.

For Ubuntu, click on the network manager icon, then on connection information. What IPs are showing for Primary and Secondary DNS?

For Windows: [http://windows.microsoft.com/en-gb/windows/change-tcp-ip-settings#1TC=windows-7](http://windows.microsoft.com/en-gb/windows/change-tcp-ip-settings#1TC=windows-7)

What IPs are showing under preferred and alternate DNS?

---

### Post by rkstarr on 2014-07-11
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]ForUbuntu:[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]IPAddress 192.168.1.4[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]DefaultRoute 192.168.1.1[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]DNS192.168.1.1
[/SIZE][/FONT][/COLOR]This is all I can see.  Am I supposed to see more detail?

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif][SIZE=2]ForWindows:[/SIZE][/FONT][/COLOR]
link you gave did notwork – server error- resource could not be found
So run cmd.exe,then ipconfig /all
DNS servers4.2.2.2
                     4.2.2.3

---

### Post by rkstarr on 2014-07-11
I checked on my laptop again under Wicd Network Manager and it has the DNS area unticked and greyed out.  I guess that may be where the problem is?

---

### Post by coffeecat on 2014-07-11
> **rkstarr said:**
> I checked on my laptop again under Wicd Network Manager and it has the DNS area unticked and greyed out.  I guess that may be where the problem is?

Oh dear, you are using wicd. Why? The default Network Manager does a perfectly good job. 

Whatever, your Ubuntu system is using your router (192.168.1.1) as your DNS, which means it is using your ISP's DNS. I can only assume that your ISP DNS is failing to resolve paypal for whatever reason, since you seem to be able to browse other sites OK. Odd that your Windows system was unable to connect to the link I posted - it's a microsoft.com page and reachable from Ubuntu! Anyway, your Windows system is using 4.2.2.2 and 4.2.2.3 for DNS:

[http://en.wikipedia.org/wiki/User:Incu_Master/4.2.2.2](http://en.wikipedia.org/wiki/User:Incu_Master/4.2.2.2)

[http://www.tummy.com/articles/famous-dns-server/](http://www.tummy.com/articles/famous-dns-server/)

Are you a Level 3 customer? If not, how did that DNS setting get into your Windows system?

As far as Ubuntu is concerned, try setting a different DNS in wicd. I have no idea how you do that in wicd - it is not an app I have either the need or inclination to get to know my way around.  However you do it, use one of these pairs of DNS addresses:

Either use Google's freely available DNS: 8.8.8.8, 8.8.4.4

Or I use openDNS: 208.67.222.222, 208.67.220.220

Disconnect from your network and then reconnect. See if you can access paypal from Ubuntu with those DNS. If you find web-browsing is fine with those DNS, you might want to reconfigure your Windows to use them as well.

---

### Post by rkstarr on 2014-07-14
Well that seem to fix things.  I installed the openDNS numbers and can now access Paypal site.  But, and there always seems to be a but whenever I touch a computer, two things:
1.  Midori spat the dummy.  The browser loads but would not open any sites (paypal or anything else).  So I just removed it - it was fast but was not reliable with all sites anyway.  Maybe it was Midori that stuffed up my settings in the first place?
2. The access to Paypal is not 100%.  A couple of times after I started up the computer none of the remaining browsers could access it.  After I rebooted it would.  So I think I still have an issue with my internet access.  But for now it will work.

In response to the other comments raised:
1.  I do not recall ever installing the DNS settings in the Windows machine - it is my wife's and relatively new.  They were probably installed by the windows certified technicians at the computer shop which built the computer.  Given the comments on one of the links I and half the world's computer users must work for the company. Perhaps I should ask for backpay!  I will fix those DNS numbers sometime on the windows machine.

2. In terms of Wicd.  I installed it reluctantly after my laptop would often (very often) randomly drop the wireless internet connection, even when only a couple of meters from the modem.  Since installing wicd I have not had any dropouts.  But I now have random issues at start up when it is occasionally slow to connect to wifi or does not find it all.  So am torn as to whether to remove it or not.  This occasional issue may be linked to the occasional issue I have noted with paypal access (mentioned above).  So perhaps wicd or my connection settings still need cleaning up somewhere? 

Anyway - thanks for the DNS setting advice.

---

