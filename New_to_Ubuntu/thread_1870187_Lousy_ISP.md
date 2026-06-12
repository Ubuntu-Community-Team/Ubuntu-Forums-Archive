---
title: "Lousy ISP"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by manners2345 on 2011-10-26
My ISP is apparently sending messages to their router to send ICMP's to my computer. Firestarter, as configured out of the box blocks them. They then disconnect me from the Internet, for authentication failure. I have tried talking to them, but to no avail. The way I see it, is this just a POWER play on their part,to show who is BOSS!!!

I HAVE TOLD THEM THAT I DO NOT USE WINDOWS, they are at a total lose as what to do,that is the only OS they know a tiny bit about.

HOW DO I SOLVE THIS PROBLEM????

---

### Post by ubupirate on 2011-10-26
Are you sure it's your ISP launching ICMP attacks on you?

---

### Post by KL_72_TR on 2011-10-26
> **ubupirate said:**
> Are you sure it's your ISP launching ICMP attacks on you?
Good question.

> **manners2345 said:**
> I HAVE TOLD THEM THAT I DO NOT USE WINDOWS, they are at a total lose as what to do,that is the only OS they know a tiny bit about.
This is very strange! My ISP knows exactly what OS I'm using at that moment.

---

### Post by manners2345 on 2011-10-26
All I know is the url 192.168.254.254

---

### Post by manners2345 on 2011-10-26
Maybe you are dealing with people level of competence is above ZERO.

---

### Post by manners2345 on 2011-10-26
Who else could be disconnecting from the INTERNET beside my ISP???

---

### Post by alphacrucis2 on 2011-10-26
> **manners2345 said:**
> All I know is the url 192.168.254.254

That is not a public internet routable address:

[URL="http://tools.ietf.org/html/rfc1918"]
RFC 1918[/URL]

---

### Post by collisionystm on 2011-10-26
192.168.254.254 is your Router.

---

### Post by manners2345 on 2011-10-26
I know that it is my router, that is the address the ICMP is coming from. so I figure it has to be coming from my ISP!!!

---

### Post by ubupirate on 2011-10-26
> **KL_72_TR said:**
> This is very strange! My ISP knows exactly what OS I'm using at that moment.

So does every website you visit, including this forum. :P

---

### Post by as2000 on 2011-10-26
Maybe the router is schitzoid. Are you certain the router firewall is not blocking them?

---

### Post by collisionystm on 2011-10-26
> **ubupirate said:**
> So does every website you visit, including this forum. :P

They also know what web browser you have

When they run a whois on your ip address, they can find your physical location.

Jeeeezzz... why do you think hackers bounce across so many systems

---

### Post by manners2345 on 2011-10-26
SO, what does that have to do with the original question?? The first computer I played with programming missile stuff was an IBM1401 with Autocoder in 1960, today a good day is remembering my name!!

---

### Post by redmk2 on 2011-10-26
> **manners2345 said:**
> My ISP is apparently sending messages to their router to send ICMP's to my computer. Firestarter, as configured out of the box blocks them. They then disconnect me from the Internet, for authentication failure. I have tried talking to them, but to no avail. The way I see it, is this just a POWER play on their part,to show who is BOSS!!!

I HAVE TOLD THEM THAT I DO NOT USE WINDOWS, they are at a total lose as what to do,that is the only OS they know a tiny bit about.

HOW DO I SOLVE THIS PROBLEM????

Dontcha just love it when nobody directly addresses your question?  LOL  It would help if we knew what the ISP was and what services (ADSL,  FIOS, U-verse, etc.) and what the router you are using is.

I can tell you from personal experience with my ISP that the router (residential gateway really) has firmware built in that allows the provider to access my side of the device (my LAN) with ICMP sweeps.  In my case the ping sweeps are to build a fancy web interface for the router showing all the devices attached.  I never look at it, but I know its there.  :-)    

The discussion about who controls CPE equipment has been going on for as long as I can remember (20+ years), I doubt your ever going to win the battle.

In my case I could convert the device to a single IP address modem (bridge) and provision my own router such as DD-WRT or a Debian dedicated host.  But I'm lazy.  I just moved the router out of sight so I don't have to look at the constantly flashing link light.

---

### Post by manners2345 on 2011-10-27
ISP is Globe Telecom, 3MB connection, Dynamic IP, ADSL, Router, Prolink H5301G using both wired and wireless. About 3 months after IPV6 was deployed I tried to get a dedicated IP address, talked to customer service, they had no idea what IPV6 was!! They told me since I was a residential user and IP addresses were in such short supply, they had to save them for business users!! What a load of _____ you (fill in the blank). I think I read somewhere, that with IPV6 there are 10 to the 28th addresses available for everyone alive on the planet as of Dec.31 2010

---

### Post by lisati on 2011-10-27
> **manners2345 said:**
> ISP is Globe Telecom, 3MB connection, Dynamic IP, ADSL, Router, Prolink H5301G using both wired and wireless. About 3 months after IPV6 was deployed I tried to get a dedicated IP address, talked to customer service, they had no idea what IPV6 was!! They told me since I was a residential user and IP addresses were in such short supply, they had to save them for business users!! What a load of _____ you (fill in the blank). I think I read somewhere, that with IPV6 there are 10 to the 28th addresses available for everyone alive on the planet as of Dec.31 2010

Yikes! The IP address you used to make the post from is listed at [http://cbl.abuseat.org](http://cbl.abuseat.org) 

edit: the packets you are noticing could be a side effect of something nasty being on your Windows system.

---

### Post by redmk2 on 2011-10-27
> **manners2345 said:**
> ISP is Globe Telecom, 3MB connection, Dynamic IP, ADSL, Router, Prolink H5301G using both wired and wireless. About 3 months after IPV6 was deployed I tried to get a dedicated IP address, talked to customer service, they had no idea what IPV6 was!! They told me since I was a residential user and IP addresses were in such short supply, they had to save them for business users!! What a load of _____ you (fill in the blank). I think I read somewhere, that with IPV6 there are 10 to the 28th addresses available for everyone alive on the planet as of Dec.31 2010

It appears that the setup is similar to all ADSL routers/modems and you should be able to run the device as a simple modem.  Either that or you will have to get a DD-WRT or Tomato firmware Linksys device.  See [**_here_**]("http://www.dd-wrt.com/site/index") and [**_here_**]("http://www.polarcloud.com/tomato").

I see Globe is a Philippine ISP.  I would have no idea on what their supply of IPv4 addresses are.  I don't believe anyone will run out of IPv6 addresses.  Did you ask for a "dedicated IPv6 address"?  I believe these are assigned in blocks rather than specific individual addresses.  Most ISP's are not running IPv6 yet and that is a shame.  Verizon is still running tests her in the USA.  :-(

It is unclear what you mean by this: "*I tried to get a dedicated IP address, talked to customer service, they had no idea what IPV6 was!! They told me since I was a residential user and IP addresses were in such short supply, they had to save them for business users!!*"

I would also seriously consider the information @lisati has mentioned.

---

### Post by manners2345 on 2011-10-27
Sorry it has taken so long to get back on this. My wife was painting the steps from our bedroom to living room stuck in bedroom.

I have no idea what the information @lisati was all about.

I heard about IPV6 several years ago. About 12 yrs ago, I was part of a team which taught CISCO, we had our own class C block of 256 IP addresses. All our computers had their own dedicated IP address(it never changed). Right now i share the IP address with who knows how many other users, a lot of times my INTERNET speed is in bps, not kbs, or even Mbs, I check my speed using speedtest to server in Cody Wy, and do a pingtest to Denver 

Time to shut down, dinner time

---

### Post by lisati on 2011-10-27
> **manners2345 said:**
> 
I have no idea what the information @lisati was all about.

At least two of the IP addresses you have used to post at this forum have been listed at [http://cbl.abuseat.org/](http://cbl.abuseat.org/) - this means that someone (possibly you, possibly not) has malware on one of their computers. **It is really important that you check this out.**

---

### Post by satanselbow on 2011-10-27
> **lisati said:**
> At least two of the IP addresses you have used to post at this forum have been listed at [http://cbl.abuseat.org/](http://cbl.abuseat.org/) - this means that someone (possibly you, possibly not) has malware on one of their computers. **It is really important that you check this out.**

Do you have more than one computer connected to your router? A second laptop, for example, that runs windows and may have an infection?

You might also want to have a look at this page (Wikipedia sorry) that explains what ICMP is and how/why the packets your ISP are apparently sending may be legit and purely error controls. This may also explain your disconnection issues.

[http://en.wikipedia.org/wiki/Internet_Control_Message_Protocol](http://en.wikipedia.org/wiki/Internet_Control_Message_Protocol)

---

### Post by Drenriza on 2011-10-27
> I can tell you from personal experience with my ISP that the router (residential gateway really) has firmware built in that allows the provider to access my side of the device (my LAN) with ICMP sweeps. In my case the ping sweeps are to build a fancy web interface for the router showing all the devices attached. I never look at it, but I know its there.

If my ISP even thinks of sweep my LAN, for any information what so ever :p. They know they are going to deal with me. The ISP,s only job / assignment is to provide a connection from me -> ISP -> WAN. And thats it. I also don't use the router that they provide. Because that is beyond the ISP,s job in my opinion. And then my network is faster = 1 less bottleneck.

At 99% of the time, the ISP,s go beyond their job / assignment. And this annoys me on a personal level :p Grrrr

---

### Post by manners2345 on 2011-10-27
I have two computers, both running versions of ubuntu, desktop is running 64 bit 10.04, laptop is running 32 bit 11.04. I do have MS Vista 32 bit, on Desktop, thru Virtual Box, which I turn on maybe once every two weeks running, I have AVG in the Vista, in the last 2 years it has not found any thing, virus, malware or anything else, the last time I ran it was about a week ago, update vista, avg then did whole computer scan, nothing. 

As what to do about what you said!! have no idea!!

---

### Post by Ex-windows on 2011-10-27
Sometimes it is good to do your scans in safe mode. Also you might want to delete some of your restore points if you have system restore turned on. In addition to your AVG I use 2 malware programs 1=spybot search and destroy (freeware) and Adaware which has a Free version. both are good programs to have if you are using windows.

Good luck   :KS

---

### Post by decoherence on 2011-10-28
I'm having a bit of trouble following this thread so I'll go back to the top...

> **manners2345 said:**
> My ISP is apparently sending messages to their router to send ICMP's to my computer.

Did your ISP tell you this?

> Firestarter, as configured out of the box blocks them. They then disconnect me from the Internet, for authentication failure.

What kind of authentication? Are you using PPPoE or 802.1X or something?

> I have tried talking to them, but to no avail. The way I see it, is this just a POWER play on their part,to show who is BOSS!!!

well, that *would* be a lousy ISP, for sure. I also work for an ISP and we prefer to not tick off our customers...

> I HAVE TOLD THEM THAT I DO NOT USE WINDOWS, they are at a total lose as what to do,that is the only OS they know a tiny bit about.


In a situation like this, often the only solution (other than finding a better ISP) is social engineering.

If you are comfortable decieving tech support, call them back and tell them you are using Windows. When they try and step you through a process to fix it, just smile and nod and tell them that you're going through each step. It is important that you write down each step -- this is the whole point of the phone call. If they ask you any questions you can't answer because you aren't using Windows, just play dumb -- ISPs are used to that.

Once they've exhausted all their troubleshooting steps and start suggesting it's a problem with your computer, tell them you'll look in to it, thank them kindly and hang up. Now with the information you've written down, you can start figuring out what the problem really is and how to fix it. I'm more than happy to help with that, if you like.

If you're not comfortable with the deception, you could just play the straight man and say "I'm not using Windows, but if I were, what would you tell me to do?" but in my experience, you get more information by stringing them along.

Aaaand finally you say that you have a Vista virtual machine. I'm going to assume that you have this problem even when the Vista virtual machine is off. Correct?

---

### Post by lisati on 2011-10-28
> **manners2345 said:**
> I have two computers, both running versions of ubuntu, desktop is running 64 bit 10.04, laptop is running 32 bit 11.04. I do have MS Vista 32 bit, on Desktop, thru Virtual Box, which I turn on maybe once every two weeks running, I have AVG in the Vista, in the last 2 years it has not found any thing, virus, malware or anything else, the last time I ran it was about a week ago, update vista, avg then did whole computer scan, nothing. 

As what to do about what you said!! have no idea!!

Go to the link I send you by PM and you will get detailed instructions on what to check. 

Edit: Using the "moderator's crystal ball", I notice you now have a different IP address. It seems not to be listed on the CBL list. For more information, go to [http://blacklistalert.org](http://blacklistalert.org)

---

### Post by manners2345 on 2011-10-29
As one of the earlier people noted, my IP address is the Philippines. There are 2 large TELECOMS which have a monopoly, which they guard with much vigor. One of the smaller telecoms started to offer basically  wireless broadband with a Dongle, they are now being bought out by the company which controls 70% of the market with government blessing, tho some legislators are trying to get an open review.

---

### Post by manners2345 on 2011-10-29
I have spent several hours reading and trying to figure out what to do. It is clear as London on a foggy day  First where would I look?? Ubuntu, Virtual Box and Windows. I have 2 hard drives, plus flash drives where I put stuff MOST IMPORTANT. I have a 500MB drive which has nothing on it, is not even formatted!! I have been trying to figure out how to make use of it since I got it back from being repaired. Right now I am thinking maybe this is a good time to try out K Ubuntu and just download it using apt, if I can figure that out

---

### Post by The Cog on 2011-10-29
In terms of the original problem:

Is the connecton by cable (like cable tv), by adsl (phone line) or wireless dongle in your PC?

Do they say why they are disconnecting you? Authentication failure sounds very vague. Can you get more detail on what they mean by this?

What do they say you should do to a windows system to cure the problem?

If you are not running services such as VNC/SSH, can you disable firestarter and see if you still get disconnected? If not, can you configure firestarter to allow icmp and see if that stops the disconnections?

---

