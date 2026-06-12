---
title: "[SOLVED] Firestarter, IPBlock, and Torrents setup explained"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by rbjscv on 2008-08-10
I've been going round and round and round (like bad HD) trying to wrap my mere human ram around this one.

To down/upload torrents the correct setup of the following should be?

So far I have one port open on router - in 40000 to 65000 range for torrents.  Firestarter can let in all traffic on my home network (192.168.1.1/24) and also has an the same open port for torrents.

Now right there is something that's counter-intuitive to me.  If I'm using a firewall to stop entry, why do I want to rip a hole in it for any and everything to get through.  Back in my Whineders days I don't recall do such a thing for torrents.  Any and everything came through anyway?

Just of out curiosity I check out a Vista machine with Zone Alarm.  That firewall didn't have an opening for torrents; just the MSHOME network.

So 1. What am I missing something regarding OS's differences?

   2.  Do I have my dear Ubuntu set up anywhere near correct to protect me from the bad gjys?
 
   3.  Why do some folks here advocate just letting the iptables handle whatever comes along?

Now I'll go and preach the truth and goodness of Ubuntu from the street corner.

---

### Post by nicedude on 2008-08-11
Ok first there is no difference in Windows or Linux as far as opening a port for torrents on your router, this is needed on both OS's for proper operation and download speeds and connections with the BT protocol. You can do it without but it wont work very well, maybe Zonealarm automatically opens a port for you ( but if so what other incoming traffic will it just open ports for? ) I don't use Firestarter as I found Guarddog to be more to my liking and for all windows boxes I use Comodo firewall ( its free and secure as hell as long as you set the right rules ), so I can't say about ZA's behavior for sure but it would worry me a little, try one of the various firewall testing sites and see if your ZA passes muster or not. 

What BT program are you using in Ubuntu, I recommend Azureus and can tell you that on both the WIndows and Linux versions it has the same setting for a port to listen on ( which is the prot you must forward in router and firewall, so there is not a lick of difference between Vista & Ubuntu as far as what is required for downloading via BT protocol I am 100% sure of this.

As far as if you have your Ubuntu set up to correctly protect you from bad people I have no idea as to what settings you used in firestarter, but I can tell you probably not nor do you have your Vista box protected as well as possible because I didn't see you mention using any IP list based blocker to block as much RIAA MPAA etc form watching you. I recommend using peerguardian in windows and ipblock in linux ( ipblock is part of a package called iplist which you can find a deb installer for it on sourceforge ) these software allow you to download lists of bad IP addresses to be blocked from any comunication with your PC ( my favorite list is called the microsoft list :-) ). But even with a properly setup Ipblocker in operation nothing is 100% protection, it is at least like a condom which is better than nothing which as far as protection a firewall is 0% protection against companies monitoring your downloads and suing you for copyright infringement ( actually FYI you can only be sued for UPLOADING content not DOWNLOADING content - Not one person in USA has been sued for downloading and won't be as it would be entrapment ).

Lastly they say let iptables handle it because iptables can handle it for most people's home PC needs. All firestarter does is let you configure iptables rules without having to know anything, its still IP tables handling your protection just you adding a few preferences to how it will do it.

For the most part Ubuntu is more secure than Windows, and 99% more in any Virus & malware threat area, but nothing on earth is bullet proof and don't believe anyone who says so. If you want a guarantee that no one can get in your system then disconnect it from the internet and build a locked Faraday cage in your basement to house it in ( its what the CIA does ), thats the only way I know that you could accomplish that. But paranoia withstanding just use an IP blocker and download on Ubuntu until your heart is content and don't worry about it, I don't.

nicedude

---

### Post by josephuser on 2010-03-21
I think I have the next step problem on this thread.  I'm using Ubuntu 9.10 along with downloading torrents in Vuze.  To secure my connection, I'm running IPBlock with all the relevant blocklists, AND I'd like to use a firewall (e.g., gufw, or more preferably, firestarter).  It appears to me that when I start firestarter and open the port Vuze is listening on, firestarter overrides IPblock and nothing shows in IPblock's "log" section (meaning that it is no longer blocking).  

The problem is that I'd like to have both IPblock AND a firewall working together, and I'd like to make sure that IPblock is blocking the relevant IP addresses.  Please help.

---

### Post by Enigmapond on 2010-03-21
You should have just stared a new thread...this one was marked as solved 2 years ago...

I'm not familiar with IP block however, Firestarter is a dead programme and there have been no updates since 2005.  If you need a frontend for iptables the suggestion would be to delete firestarter and install gufw. Just allow the port for Vuze in gufw and there shouldn't be anything overriding the application.

---

### Post by josephuser on 2010-03-21
Thanks, I'll do that.  Didn't realize firestarter was depreciated.  Starting new thread.

---

