---
title: "Improving Tor etc"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by omoto on 2008-07-15
I&#8217;m sorry if this is posted in the wrong spot or area. I&#8217;m new to this. This is my second post here. It will take a few times for me to get things straight on where to post certain topics.

I just upgraded to vidalia bundle 0.2.0.28-rc-0.1.4 (Unstable version) of Tor two weeks ago, but downgraded to the 1.2.19 version after about a week since I felt uncomfortable using the unstable version (0.2.0.28..) thinking it would be easier for someone (Hacker, stalker etc.) to find me. I just recently found out and heard from a friend of mine that [hackers in certain places who have good hacking programs]("http://nowlive.com") can hack proxy servers to find people (For harassment causes.) I was wondering if there was a place to send suggestions to or for improvements for the tor program to make proxy servers more secure (Stronger anonymity) to protect the person who&#8217;s using it for their own privacy?

I&#8217;m also having another problem I think might have to be posted in another thread and/or in a different area.

My parents are using tor besides myself since I suggested them to use it. For some reason, Vidalia works well on my end except for a few slow servers that might come along preventing some pages from loading up fast enough (I just close certain servers off and it works fine after that.) My parents are using Windows Vista Home Premium. For some strange reason, Tor works well on my desktop computer and laptop, BUT it runs slower than an old lady walking across the street. In other words, I even lose some of my patience with it just as well as my parents when trying to view a website(s.) Even when I close certain networks (Closing certain number of networks at certain times vary) to make the page load easier, there is no speed improvement on their computer (The internet works fine without the program enabled on their computer.) Is there any particular reason why Tor works great on my computer and laptop but not on their computer? I know it took my desktop about a month to work through the problems I used to have (Slow page loading,) do you think it&#8217;s the same thing with theirs? I know this might sound like a weird concept, but does Tor have to get used to the computers activity and usage in order to make improvements? I&#8217;ve also noticed regularly with either version that I&#8217;m constantly getting notices of blocked port(s) messages from my firewall. Would this contribute to the problem(s?)

---

### Post by benfindlay on 2008-07-15
Have you also installed privoxy, which accoridng to their site is > a non-caching web proxy  with advanced filtering capabilities for enhancing privacy, modifying web page data, managing HTTP cookies, controlling access, and removing ads, banners, pop-ups and other obnoxious Internet junk. Privoxy has a flexible configuration and can be customized to suit individual needs and tastes. Privoxy has application for both stand-alone systems and multi-user networks.

Most guides I've come across recommend using this along with TOR for best results!

Hope this helps!

---

### Post by omoto on 2008-07-15
> **benfindlay said:**
> Have you also installed privoxy, which accoridng to their site is 

Most guides I've come across recommend using this along with TOR for best results!

Hope this helps!

Yes, Tor and Privoxy come with the Vidalia bundle. I have all three installed. I have the union and "P" icon on my task bar which shows they're both running. I followed all the instructions on how to set it up but it doesn't work on my parents computer for some reason. It works fine on mine.

I just upgraded to the latest version of privoxy 3.0.8 before on my own computer to see how it would work. That version does not work at all. 3.0.8 practically asks for hackers to invade you or other things that might follow you.

---

### Post by benfindlay on 2008-07-16
Is that the same version as is installed on your parents' machine? If so I'd suggest removing it and either manually downloading and installing the .deb of the version you know to work, or you can force synaptic to install a specific version of tor, and then lock it to prevent further upgrading of that package via apt-get update and upgrade

Hope this helps!

---

### Post by omoto on 2008-08-31
> **benfindlay said:**
> Is that the same version as is installed on your parents' machine? If so I'd suggest removing it and either manually downloading and installing the .deb of the version you know to work, or you can force synaptic to install a specific version of tor, and then lock it to prevent further upgrading of that package via apt-get update and upgrade

Hope this helps!


Oddly enough, I finally got tor to work on my parent&#8217;s computer with the latest stable version 0.2.30.

For some reason, when another program like an instant messenger is working at the time tor is working, tor runs at a descent speed for some reason. When the instant messenger is not on, tor cuts down at about 25% when the instant messenger is not working, making tor run only three quarters of the full descent speed it's supposed to work.

There's another thing I've noticed. Version 0.1.2.19 runs almost twice the speed 0.2.0.30 does on my computer. Is it because 0.2.0.30 doesn't cache websites when 0.1.2.19 does? Or is it because (Does) 0.2.0.30 has (Have) to get used to your internet activity in order to work properly or at a descent speed?


[http://xenastreetfighterthenextgeneration.com/TellAllWeeklySeries](http://xenastreetfighterthenextgeneration.com/TellAllWeeklySeries)

---

