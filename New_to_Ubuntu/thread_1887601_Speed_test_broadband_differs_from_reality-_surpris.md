---
title: "Speed test broadband differs from reality- surprise !"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by grey1beard on 2011-11-27
I'm having problems with speed and trying to install BBC Iplayer, via our broadband connection.

I forget where, but it might have been the BT pages, I got the info that our phone line from the local exchange was capped to 500kb.

I've just used the BBC speed test on the diagnostics page, and it gives a result, fairly consistently, of 290 Kbs (As do many other speed tests, and we pay for 2mb !)

Immediately afterwards using the update manager showed a speed of 40kbs, sometimes dropping to 20 KBs , and the same speed with Adobe Air download !!!

We live in a rural area with few ( probably less than 1000 subscribers) connected to the local exchange. The downside is that, with little else to do, we might have a higher proportion of gamers.

I've done this several times over the past few days, and come to the conclusion that the speed test tells you only what the maximum you might get if no one else was on your line to the exchange, not what it actually is at that moment.

If it _is_ the real speed, how is that achieved ?

I'd be interested to know if anyone has any similar thoughts, and more usefully anything that can be done about it.

John

EDIT Just found this in the small print of one of the many speed test online

> Any results generated are not a guarantee of your true connection speed.

---

### Post by Mark Phelps on 2011-11-27
The speed test that is commonly used times both the upload and download of files from your PC involving a server you select.  Thus, it is NOT a maximum; but instead, is the actual test results.

I can run the same test time after time, and each time, it gets different results -- which would not be the result if it were only reporting maximums based on ISP ratings.

---

### Post by grey1beard on 2011-11-28
Possibly, Mark, but then how is it that there is such a huge variation in what they report, and what my download speed of actual files is ?
My "reported" speeds also vary, but only by a few kbs. 
Update manager downloads for example, are coming in at 10's of kbs, not 100's.

John

---

### Post by coffeecat on 2011-11-28
I wonder if this is the issue:

> **grey1beard said:**
> 
Immediately afterwards using the update manager showed a speed of 40kbs, sometimes dropping to 20 KBs 

Kbps (kilobits per second) is a different thing from KBps (kilobytes per second). I suspect that Update Manager is reporting in KBps and is varying between 40 KBps (not Kbps) and 20 KBps. Your speedtest download speed of 290 Kbps equals 36.25 KBps which puts it in the same ball-park as your Update Manager speeds, if they are indeed in KBps.  

A couple of other points. You say you pay for 2 Mbps, are capped to 500 kbps and actually get 290 Kbps. My guess would be that you are not capped, but that you are some distance from the exchange. With traditional copper wire, attainable speeds drop dramatically after a mile or so. How far are you from the exchange?

Also - 2 Mbps. That was the speed of the old BT adsl service which I thought had been replaced by the "up-to" 8 Mbps adsl max introduced in 2006. Or perhaps BT didn't upgrade all their exchanges. Do you know which you are on? Not that adsl max would make much difference if you are some distance from the exchange.

---

### Post by lisati on 2011-11-28
My $0.02:
A number of things can add a degree of confusion to the results you can get from services which measure the speed of your connection. These include what's actually being reported (see coffecat's post above), network congestion, and how busy the server you are using is. Sometimes even the server that is geographically closest isn't the fastest. 

At home I get results that meet my needs most of the time. At work, using the same ISP and telco, but further away from the local exchange, the results are usually better. Part of this could be the DIY nature of my phone wiring @ home.

---

### Post by grey1beard on 2011-11-28
Hi coffecat, and thanks for your post.

I suppose, like talking too much, I give too much info, and consequently make typos and lead people astray !
Yes, my electronics background gives me enough to spot the difference, but I never learnt to type.

The nub of the problem is this.
While I am downloading, be it from update manager or wherever, the indicated download speed can drop from say 170k to 40k to 10k(choose your own units), in other words a massive speed drop.
Simillarly when streaming a video, it may work well for a few minutes, then suddenly stops, buffers or even pops up a message "Insufficient Bandwidth", which I have always assumed meant that a "gamer" has come between me and the exchange, and is hogging all available.(The logic there is a bit flakey, but I hope you see my feelings.)

When these effects are being seen consistently, why is it that a speed test carried out immediately, doesn't show up any difference, but _always_, within a few percent, gives a consistent reading ?

Regards
John

---

### Post by grey1beard on 2011-11-28
Hi lisati.
As my recent post, my problem is consistency, and the difference in reported speed from a speed test and during a file download where the download speed is indicated.

---

### Post by coffeecat on 2011-11-28
I doubt you'll ever get satisfactory video streaming with even a consistent download speed in the 300 Kbps area, so I don't think you can read much into the buffering issues you see with streaming. And as far as iPlayer is concerned, I doubt you'll ever be able to use it with that connection - sorry. With problems I've been experiencing with download speeds, iPlayer has become unusable below about 1500 Kbps for me.

My experience of speedtest results is that they are reliable and consistent with the sort of speeds I get with the package managers. It is interesting that [s]Download[/s] Update Manager starts with a (relatively) faster speed and then drops off. Is your "wherever" using Firefox and another download server? Have you tried downloading a big file in Firefox in another OS such as Windows or MacOS to see if the same happens?

---

### Post by jockyburns on 2011-11-28
Probably something due to the servers between you and wherever the update manager get's it's files from. You could have a 100Mbs connection, but if only one of the multitude of servers between you and another website only has a 1Mbs connection, then that's all you'll get. Sadly most ISP's state that they offer you a service of **up to** XXXMbs, but know they can't ever possibly supply XXXMbs. My brother is with Sky and pays for their **up to** 20Mbs service, (simply because there's no limit on downloads) He only manages around 2Mbs on a good day, downhill with  the wind behind it.;);)

---

### Post by grey1beard on 2011-11-28
> **coffeecat said:**
> I doubt you'll ever get satisfactory video streaming with even a consistent download speed in the 300 Kbps area, so I don't think you can read much into the buffering issues you see with streaming. And as far as iPlayer is concerned, I doubt you'll ever be able to use it with that connection - sorry. 

Curiously, this hasn't been a problem for us over the previous months. In fact up to a week ago, we could use my wife's laptop (32 bit) and have no problems streaming one comedy program after another on a Saturday evening.
Now, it's a different story.
I've been trying to get iPlayer onto my 64 bit desktop, but that's turned into a can of worms, which is where I'm typing this, and is the current pc I'm using for testing speeds.
This is connected to the router via a lan, whereas the laptops are on a wireless link.
They all show exactly the same symptoms, so I can rule out my pc as being the source of the problem.

As for speeds dropping off with download manager, I use that as an example that shows a speed bar. It may be other downloads that show it too.

I realise that I'm never going to get  the full speed advertised. That isn't the point. It's the lack of consistency in reported speeds and experience.

---

### Post by grey1beard on 2011-11-28
I've just updated the firmware of my "Belkin Enhanced Wireless Modem" router, to rule out another possible source of trouble, but perhaps the two attached screen grabs will illustrate the problem I'm facing.

On the other hand they may only confuse the issue. They certainly confuse me. :confused:

One shows the download on iPlayer of the Antiques Roadshow, about 530Mb file, where it indicates a download speed of 319Kb/sec with an estimated time of 4:03 hours to complete.
I leave you to check the maths, but that's about 25Kb/sec.

The other is of the BBC speed test I then did, with the download paused, and you can see the results - a streaming speed averaging about 280Kb/sec.

How am I supposed to make any headway in analysing the source of the problem, when this is the sort of info I get.

---

### Post by sandyd on 2011-11-28
> **grey1beard said:**
> I've just updated the firmware of my "Belkin Enhanced Wireless Modem" router, to rule out another possible source of trouble, but perhaps the two attached screen grabs will illustrate the problem I'm facing.

On the other hand they may only confuse the issue. They certainly confuse me. :confused:

One shows the download on iPlayer of the Antiques Roadshow, about 530Mb file, where it indicates a download speed of 319Kb/sec with an estimated time of 4:03 hours to complete.
I leave you to check the maths, but that's about 25Kb/sec.

The other is of the BBC speed test I then did, with the download paused, and you can see the results - a streaming speed averaging about 280Kb/sec.

How am I supposed to make any headway in analysing the source of the problem, when this is the sort of info I get.
Theirs several reasons I could think of.

a)The ISP offers speeds UP TO. the advertised speed. Theirs no guarantee. If all the people in your neighborhood were downloading all the same time, none of you would reach your maximum speed, since node serving your community will have a lower connection speed. The traffic spikes are simply caused by other people in your neighborhood doing whatever. For example, if I download a 25mb file, it would instantly slow down your internet. These things are equal share -i.e. if everyone downloaded at the same time, you would all get the same speed regardless of how much your advertised speed is.

b)Traffic problems. Poor networking equiptment /routers/cables can cause this. You should run a ping or traceroute continuously to see if the net slows down at a certain node/router. If that is the case, theirs not much you can do about it yourself - its up to your ISP and their Tier 1 bandwidth providers to sort out. If you don't know how to do this, post your IP (or PM it if you don't want others to see)

---

### Post by coffeecat on 2011-11-28
> **grey1beard said:**
> One shows the download on iPlayer of the Antiques Roadshow, about 530Mb file, where it indicates a download speed of 319Kb/sec with an estimated time of 4:03 hours to complete.
I leave you to check the maths, but that's about 25Kb/sec.

I have checked the maths and that is not what I get. First, a 1-hour programme would be 530**MB** - mega**bytes**, not megabits. A 1-hour 530 Mb file would be of very low quality.

So, assuming it is 530MB, 530 MB = 530 x 8 x 1024 Kilo**bits** = 4341760 Kb.

4 hours 3 minutes = (4 x 60 x 60) + (3 x 60) seconds = 14580 seconds.

4341760 Kb in 14580 seconds = 4341760/14580 Kbps = 297.8 Kbps.

Which almost the 319 Kbps as shown. In fact it seems that you have already downloaded a little and if 4:03 hours are to go, the average download speed will be somewhat lower than 297, but not as low as 25.

An average download speed of 25 Kbps would take 173630 seconds to download a 530MB file =  2894 minutes, which is over 48 hours.

---

### Post by ofnuts on 2011-11-28
I use the small script below to get an idea of my download network usage... this is a better measure than dividing files sizes by times because it also includes the overhead bytes. Although I enjoy a 16Mbs connection, I rarely see it running at that speed.  The best time to measure your max speed is in the wee hours of the morning using a very fast server (GoogleDocs is the only server that got capped by my bandwidth). Wifi usage also impacts the network speed, on my 54Mbps Wifi link it rarely gets better than 600Kbs and I only gte my full ADSL link speed on wire (CPL or Ethernet) .

```
dev=eth0
[[ ! -z $1 ]] && dev=$1


function getcount
{
        local devline=$(grep "$dev:" /proc/net/dev | tr ":" " " | tr -s " ") 
        incount=$(echo $devline | cut -d " " -f 2)
        echo $incount
}


current=$(getcount)

for i in $(seq 1000)
do
        sleep 1
        new=$(getcount)
        diff=$(( $new - $current ))
        diff=$(( $diff / 1024 ))
        echo $diff KB/s
        current=$new
done
```

---

### Post by grey1beard on 2011-11-28
I'm sure you're right coffeecat, but when I've downloaded bbc programs about the same size as this one(it's just finished after about 5 hours) 20 - 25 minutes was the usual time, so the point of my observations remains, even if the maths doesn't.
Regards
John

---

### Post by grey1beard on 2011-11-28
To all readers.
The thrust of my point is _not_ that I don't get what I pay for, but in trying to establish _why_ my observed speed is not what the Speed Tests report.
For whatever reason my connection is being slowed down, why don't the speed tests show it ? 

Sandyd - many thanks for pointing to other possibilities.
email on its way. 

John

---

### Post by coffeecat on 2011-11-28
> **grey1beard said:**
> I'm sure you're right coffeecat, but when I've downloaded bbc programs about the same size as this one(it's just finished after about 5 hours) 20 - 25 minutes was the usual time, so the point of my observations remains, even if the maths doesn't.

Then you need to take it up with your ISP. In fact, I very much sympathise. Even 300 Kbps is absolutely appalling. I was getting download speeds in that range on a line that is capable of about 6500Kbps. 6 weeks after raising a fault ticket it's still not sorted out and my thoughts on the subject are not fit to be made public. 

The only saving grace for you is that BT wholesale will not investigate unless the speed drops below 600 with their speedtester, and it seems as though yours will. Good luck with the BT speedtester. It is the most infuriating thing I have had to deal with this year. :(

---

### Post by sandyd on 2011-11-28
> **grey1beard said:**
> To all readers.
The thrust of my point is _not_ that I don't get what I pay for, but in trying to establish _why_ my observed speed is not what the Speed Tests report.
For whatever reason my connection is being slowed down, why don't the speed tests show it ? 

Sandyd - many thanks for pointing to other possibilities.
email on its way. 

John

I don't know if ubuntuforums still shows my correct email - should be [email]sandy@_replace_.me[/email]

Replace _replace_ with my forum username.

---

### Post by gordintoronto on 2011-11-28
What else is going through your router? Do you have kids? Is your security good, so your neighbours are not leaching from you?

I think you mentioned you have a rural home? Even rain on rural wiring can affect your throughput. How far are you from your Central Office?

---

### Post by grey1beard on 2011-11-28
Hi gordintoronto, and thanks for the lol.
At 75, my kid has flown the nest some time back, and re the rain, it's been the driest autumn in memory !!
As for the neighbours, we live on a farm about +2 miles from the nearest village, and I know my friends here on the farm aren't responsible for the speed problem.

"Central Office" - good grief, what an appalling thought. Go to www fanmaker couk (add dots and spaces) for why.
Regards
John

---

### Post by Zill on 2011-11-28
> **grey1beard said:**
> ..."Central Office" - good grief, what an appalling thought...
Possibly a transatlantic translation error. ;-)  I think "Central Office" may be a reference to your local telephone exchange.

---

### Post by grey1beard on 2011-11-28
> **Zill said:**
> Possibly a transatlantic translation error. ;-)  I think "Central Office" may be a reference to your local telephone exchange.

:D:D:D
Thanks for the translation Zill.

It's about 1.5 miles to the actual building, across the fields !

John

---

### Post by QLee on 2011-11-29
[QUOTE=grey1beard]...
It's about 1.5 miles to the actual building, across the fields ! ...[/QUOTE]

The distance to the exchange that way isn't important unless you are wireless (radio frequency transmission is straight line), your "distance" from the exchange is the path of the wire that brings your service. Long distance does mean some loss of bandwidth but phone companies are aware of that and should advise the customer if it is considered a long run. Their technician should be able to check if your install is capable of delivering what they are charging for. Sometimes something as simple as leaving an unterminated length of cable (going on down the road) connected to a line can affect bandwidth. Even the wiring inside your house and the equipment you have connected could have an effect. I'm assuming you don't have a fibre optics line in a rural setting.

When you download from somewhere, a factor is also the ability of the serving server to deliver bandwidth and that is also affected by the number of clients it is serving to. Sometimes you might get one speed at a time during the day when the serving server is busy and a different speed other times when the server isn't busy.  Add to that the fact that any delays in the route from serving server to your client can also affect the effective throughput of your download. Many servers that have downloads available limit bandwidth to any single client.

Various utilities that show you a speed figure are affected by the paradigm they use for the calculations and instantaneous display can vary as the speed of the 'Net varies, it is generally more accurate to see the final calculation when the download is finished.

Speed test sites in general (at least the good ones) are configured to have sufficient bandwidth for the clients that they serve so that "loading" isn't a factor in the calculations they make (usually they would limit the number of connections at any given time to acheive that), thus they are reasonably good estimations of what your system is capable of at test time. Note that you could get one measure from a speed site and a much lower speed from a site that you are downloading and that might be normal and reasonable. I see (and have always seen) wide variations in throughput of downloads in real life situations although fairly consistent speed tests (once time of day and if it is the day of a distro release, for example, have been taken into account).

Something more concerning is your statement that it worked better until recently, maybe something has changed and after you've eliminated anything in your own wiring it might be reasonable to ask your phone company to check the circuit from your house to see if they think the advertised bandwidth is getting to you. I've repeated a lot of what has already has been stated in this thread in my own words, hopefully to condense it and stimulate your thinking.

Another thing to consider, clarity for that "bandwidth cap" you mentioned and the units thereof. If it is really just 500 MB (no per seconds) that could be involved, I think some providers slow down a connection's max speed after a monthly bandwidth cap (not speed, amount) has been exceeded. You should check carefully the terms of service for your line to determine if this is happening.

---

### Post by grey1beard on 2011-11-29
Thank you to all who have contributed, but I still have no idea what the answer is to my original question.

To try and simplify it so there is no misunderstanding - 

Why does the result of a speed test, conducted at a time when the speed of a downloaded file from any other source is incredibly poor, only show the maximum the line has ever given.

I'm now going to communicate with my isp, stating the results of my labours, but for some reason I'm not expecting any miracles.

John

---

### Post by QLee on 2011-11-29
[QUOTE=grey1beard]...
Why does the result of a speed test, conducted at a time when the speed of a downloaded file from any other source is incredibly poor, only show the maximum the line has ever given.
...[/QUOTE]

If that stated data is correct, and I'm willing to take your word for it since I have no further data and am not there to test. The interpretation I would put on it would be that is the max. for the line. If it is less than you are paying for, then asking the service provider to test is appropriate. They will probably bring their own laptop to verify and if it works for them they will likely not care about any troubles you are having.

---

### Post by grey1beard on 2011-11-29
> **grey1beard said:**
> 
I'm now going to communicate with my isp, stating the results of my labours, but for some reason I'm not expecting any miracles.


Hallelujah !!!

I have been logging on to the isp support forum, and the last few day has seen a massive increase in the complaints of slow broadband speed.
After my previous post, I tried logging on again but the site posted apologies for "suspension of support during servicing until 6.30pm" or some such wording.
Trying another speed test, which seemed slightly higher than usual, I tried the BBC iPlayer site and started another download trial. Same size file as last time, which took 5+ hours, this time took 25 mins.

I now wait with baited breath to see how long it lasts !

John

---

### Post by Zill on 2011-11-29
> **grey1beard said:**
> ...I have been logging on to the isp support forum, and the last few day has seen a massive increase in the complaints of slow broadband speed...
A good move as it is always useful to find out if other users are experiencing similar problems.

Just out of interest, which ISP are you using?  Personally, I use [IDnet]("http://www.idnet.net/") here and have not experienced any speed problems - generally getting around 5Mbit/s in our semi-rural area.  I am approximately 1.2 miles by road (the most likely route for the phone line) from the exchange.

For the benefit of our "overseas" (i.e. non-UK) readers I must explain that we really only have a couple of providers of backbone broadband connections in the UK.  Virginmedia provide high-speed fibre-optic TV, phone and broadband services in the major conurbations but very little outside these.  The rest of the UK is served by the national telco BT.  They are slowly rolling out high-speed fibre-to-the-cabinet around the country but, again, primarily in the heavily populated areas first.

So, if we don't have the benefit of a fibre-optic service in our area then we are left with the old copper telephone wiring using ADSL with a *maximum* speed of 8Mbit/s.  This speed is, of course, reduced as distance from the local exchange increases and with the number of simultaneous users. :-(

Although we now have the luxury of choosing from different retail ISPs, in the end most broadband traffic still ends up going through the same BT pipes!

---

### Post by grey1beard on 2011-11-29
Hi Zill.
Well first it was BT, but then some years back I switched to Tiscali, still paying BT the line rental.
Then I think they were taken over by TalkTalk, so I took their offer of line included in the package with an "up to 2mb speed" (ho ho), but when I logged on a couple of days ago, it looks like they have been taken over by AOL.
Consequently, I don't realy know who's coffers my pennies are filling :)
Regards
John

---

### Post by coffeecat on 2011-11-29
> **grey1beard said:**
> Well first it was BT, but then some years back I switched to Tiscali, still paying BT the line rental.
Then I think they were taken over by TalkTalk,

TalkTalk has local-loop unbundling (their own equipment) in many exchanges, but if you are served by a small rural exchange they probably won't have and will rely on BT (wholesale) for the service at least as far as the backhaul. Remember, there is a difference between BT Wholesale and BT Retail. Which is why I forewarned you that you may have to prove there is a problem with the BT speedtester. Your ISP - TalkTalk - will advise you what you have to do. If it does involve the BT speedtester, then all I can say is that I commiserate. Been there, done that, got the scars to prove it.

---

### Post by I2k4 on 2011-11-30
Can't at all speak to UK services, but my Bell Canada situation changed dramatically over a year or so:  initially I had some  complete cut off reliability problems and they sent a tech out, who apparently concluded that the wires in our condo building weren't up to full spec.  Service resumed but at much lower speeds - I phoned again and after convincing the kid in Bangalore, India that it wasn't a problem with my system (the tech had checked that), I got a Bell Canada manager on the line.  They did some checks of their own side of the connection and found my connection had been reset to half-speed after the technician's report back to head office, to ensure "reliability". The manager was very apologetic.  

From that point on, I had "full service" on the 7mb download subscription - of course "full service" was only about 5mb but far better than the reduced half-speed.   

I suggest using the service [www.speedtest.net](www.speedtest.net) if it is available for your geography/ISP, as the best impartial bandwidth gauge available.  If indeed your connection is less than 2/3 of the "advertised" bandwidth for your subsciption, I suggest calling the ISP and asking them what is going on.  They may require you go through some checks of your own system and settings, but a little insistence might get them to investigate if something on their end is to blame.

---

