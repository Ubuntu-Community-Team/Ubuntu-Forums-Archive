---
title: "OUTLINE: Disable IPv6"
date: 2004-12-01
forum: Outdated Tutorials &amp; Tips
---

### Post by mark on 2004-12-01
I've seen lots of posts about problems with IPv6 (slow network/Internet connections, DNS resolution problems, etc.).  I've also seen several posts presenting solutions to these issues.  Herewith, what I had to do to disable IPv6 and get reasonable connection & DNS speeds.

1. *sudo gedit /etc/modprobe.d/aliases* (or your preferred text editor)
2. Find the line: *alias net-pf-10 ipv6* 
3. Edit this to: *alias net-pf-10 off* 
4. Save the file and reboot

Please note that many of the suggestions I've seen recommend running the command *sudo update-modules* before rebooting; whenever I've done this, I still see IPv6 active (i.e., the *sit0* section when running *ifconfig -a*) and still experience the network performance problems.

Finally, with Mozilla browsers (Firefox or Suite), you can enter *about:config* in the address bar, locate the line starting with *network.dns.disableIPv6* and change the value to *true*.  (I'm not sure if this is necessary; I do know that, by itself, it doesn't solve the problem.  But, hey - it can't hurt!)

As I said, several other folks have offered variations on this procedure - and I think I've tried 'em all.  This is the method that has worked reliably, for me, through the course of several complete reinstalls.

12/15/04 - My last reinstall, this didn't work - what *did* work was: ```
3. Edit this to: *alias net-pf-10 off ipv6* 
``` Not sure what changed, but there it is...

Mark

---

### Post by Old Pink on 2006-10-24
This deserves a BUMP, as it's a really helpful thread.

_**Additional: Disabling ipv6 in Firefox**_[LIST=1]
[*]Type about:config in your address entry bar (in firefox)
[*]Type "ipv6" in the filter
[*]Change the value of "network.dns.disableIPv6" to true[/LIST]

---

### Post by phormion on 2006-10-24
One important thing to note would be that you should only take these steps if you **don't** have any IPv6 connectivity. I know most people don't, but still, you never know who's reading this. 

Also, there's a pretty good description of the network.dns.disableIPv6 option on MozillaZine: [http://kb.mozillazine.org/Network.dns.disableIPv6](http://kb.mozillazine.org/Network.dns.disableIPv6). Basically, if it's not set to true, one extra query is made for each address (that's not in the browser's cache). I don't know why this isn't off by default.

---

### Post by Ublis on 2006-11-25
> **mark said:**
> <snip>
2. Find the line: *alias net-pf-10 ipv6* 
3. Edit this to: *alias net-pf-10 off* 
4. Save the file and reboot
<snip>

This worked for me - browsing is now at normal speed again. It even fixed the problem that after startup, I had to manually run "ifdown -a" followed by "ifup -a" to get the network running (simply disabling/enabling in the GUI tool didn't work, unlike in Dapper).

---

### Post by MkfIbK7a on 2007-01-28
thanks this helped speed up my network greatly!

---

### Post by Quintin Riis on 2007-02-07
Reboot?  wtf?

---

### Post by mux2000 on 2007-02-12
Tried this and it didn't work, Connection still very slow (~3000ms ping to google), and it disconnects every 15-45 minutes as well (though for a few minutes right after reconnecting the speed is good, and then it slows down).

---

### Post by findik1 on 2007-02-16
yes it worked for me

---

### Post by lupin492 on 2007-03-02
> **mux2000 said:**
> Tried this and it didn't work, Connection still very slow (~3000ms ping to google), and it disconnects every 15-45 minutes as well (though for a few minutes right after reconnecting the speed is good, and then it slows down).

MUX2000: You have a poor Internet connection, not DNS problems. When you issue a ping, and the NAME of the site takes long to be related to its address, that's a DNS problem (that may also be due to a poor connectivity).  But if ping tells you 3000ms, better change your ISP !
Regards.

---

### Post by nautilus on 2007-04-20
** ** this no longer provides any improvements to performance on feisty fawn due to patched/updated GNU LibC (see Launchpad) ****

in short, please, stop doing it as the first solution to everything.  it will not fix a broken dialup connection, a bad pppoe situation, or high-latency ping times to google or any other hosts.

this will only fix a possible delay in resolving AAAA records for hosts on archaic routers and other non-standards-compliant hardware (such as cheap routers) which cannot understand the request and, to our dismay, simply refuse to dignify it with any sort of response.

this causes the nslookup on your ubuntu system to eventually timeout, and try the simpler "A" record search.

--

if you disable IPv6, you will need to re-enable it for your system to operate properly on Internet2 in the future.  if you do NOT have IPv6 support on your system, your system is not compliant with current Internet standards.

i hope this clears some things up.  disabling ipv6 is NOT a panacea of any kind for all network issues.  if anything, it's more like amputation.  stop butchering your system! >:O

---

### Post by JBull on 2007-04-21
OK, how do I fix the the proper way?  I'm running Debian Sarge and the DNS is very slow.  I don't experience this problem with my other machines running Windows.  

My router is Actiontech MI424WR, for Verizon fios.  The address of the router is 192.168.1.1 and my Debian DNS points to 192.168.1.1.   It is very slow.

I've read others blacklisting or other disable of IPV6.  This is fine with me but you say that is not the proper way.  Then please advise me how to use IPV6 and have it work correctly.

---

### Post by martel80 on 2007-04-23
> **JBull said:**
> Then please advise me how to use IPV6 and have it work correctly.What about having the OS try IPv4 first, then IPv6 only if failed? (it's vice versa now, if i get it right)

---

### Post by JBull on 2007-04-27
OK, I'll do some research on this and give it a try.  I'll post a step-by-step if it works.

I recently read a tech article that researches in Japan had set a new network speed record using IPV6, something insane like 9 Gbps.  The previous record had been 7Mbps with IPV4.  I don;t remember the exact numbers but these are in the ballpark of what the article said.

---

### Post by ronacc on 2007-04-30
right now here in the US with my provider (comcast cable) ipv6 causes problems , not just in firefox (which I don't use) but in other browsers , synaptic, update-manager ,  I blacklist ipv6 and the problems go away, to me that is UNbutchering my system. If you actualy have ipv6 connectivity use it, if you don't have ipv6 available blacklist it.

---

### Post by fadenb on 2007-05-01
why dont you just get yourself some ipv6 tunnel.
[www.sixxs.net](www.sixxs.net)

---

### Post by giosue_c on 2007-05-29
> **nautilus said:**
> stop butchering your system! >:O

I agree that people should not needlessly disable ipv6, but the fact is some of us are the unfortunate owners of these non standards compliant routers.  I for one spent more than a couple hours figuring out that nothing was wrong with my isp or my computer and that in fact it was my idiot router the whole time.

For the record my idiot router is a 2wire 1000HG.  I can't complain too much.  Integrated wireless for only 20 bucks.  Works great except for ipv6.

---

### Post by eentonig on 2007-06-10
Personally, as a telecom engineer,; IPV6 should break through sooner the better. But in the mean time, it find it a stupid way of working to implement a feature/technology ins such a way, that it cripples 90% of the userbase.

As it stands now. IPV6 isn't used in 90% of the internet traffic. Then why make your systems so that they use that, before trying the existing standards that use IPV4? When IPV6 picks up, it's just a matter of applying a patch to reorder the operations.

Untilll then, I'm more then happy to disable IPV6 to make my system work.

---

### Post by pardesi on 2007-06-10
i did all what was written here and elsewhere in this community.my problem got fixed but now each time i boot i have to reboot to see my FF functional.:(.someone please help me this is making me lose my patience:(

---

### Post by shafin on 2007-08-31
Thanks,The BBC page was a real mess.

---

### Post by nikoPSK on 2007-09-29
thanks Ihd fast internet on windows (downloads = 600 kbps) and on ubuntu I got 65- 90 kbps and you sped it up now its 500-700 great!:KS

---

### Post by brunoscunha on 2007-11-30
Great, worked just fine for me :D

---

### Post by nikoPSK on 2007-11-30
what! Oops, forgot to enable in gutsy. LOL

---

### Post by nautilus on 2007-12-01
IPv6 runs independently of IPv4.  If disabling IPv6 seems to boost your performance in any way I'd like to know more about what your network is like; provider, modem brand, any wireless access points or routers (brand/model) so I can look into it.


<rant>
I find it scary how many people running Ubuntu immediately remove IPv6 support without a second thought, even though it is the -current- Internet standard protocol irregardless of popularity....  If everybody in the world instantly disables the protocol on their system it sure isn't helping the migration, is it?
</rant>

---

### Post by WinterWeaver on 2007-12-01
I'm sorry, my experience is that IPV6 deffinately slows my Ubunut. (oh... and yes.. it is modem/hardware related, but it's cheaper to disable ipv6, than to go and buy a new router). Here is what happens...

When my network cable is active, I typically wait for a app (any app, no matter how small) to load for about 20 seconds... yes... 20 secs, even for the terminal, gedit, calculator, screenshot... ANYTHING.

Boot up time is also significantly longer, because this 20 sec thing applies to every single applet on my panel O.o

When I visited a friend, I noticed a massive change. When plugged into his Router, evering was blazingly fast... apps would load under 5 secs etc...

So at home, I tried disabling the network, and see the speeds... and to my surprize everything was fast again O.o

That's when I tried disabling IPV6, and ... it partially worked. It's still not as fast as when I have the network disabled, but it's faster than what it was.

> IPv6 runs independently of IPv4. If disabling IPv6 seems to boost your performance in any way I'd like to know more about what your network is like; provider, modem brand, any wireless access points or routers (brand/model) so I can look into it.

**my Router is:**
Telkom ADSL Router
made by Marconi
(This Router is known to be troublesome)

---

### Post by nikoPSK on 2007-12-01
I use Motorola routers and I have shaw as a service provider.

---

### Post by nikoPSK on 2007-12-01
And if I told you I lived in victoria would that help?

---

### Post by firefly76 on 2007-12-07
> **WinterWeaver said:**
> I'm sorry, my experience is that IPV6 deffinately slows my Ubunut. (oh... and yes.. it is modem/hardware related, but it's cheaper to disable ipv6, than to go and buy a new router). Here is what happens...

When my network cable is active, I typically wait for a app (any app, no matter how small) to load for about 20 seconds... yes... 20 secs, even for the terminal, gedit, calculator, screenshot... ANYTHING.

Boot up time is also significantly longer, because this 20 sec thing applies to every single applet on my panel O.o


This sounds less like an IPV6 problem and more like a bad network configuration.  Latency when opening programs usually tips me off that the hosts file is out of whack.  Edit /etc/hosts and make certain loopback is setup correctly.  You're going to want:

```

127.0.0.1        localhost.localdomain    localhost
127.0.0.1        hostname.localdomain    hostname

```

where hostname is the name of your box and localdomain is your domain.  If you are using a domain name, make sure it's the same as the router's domain.  The machine is basically trying to open a program on loopback, but not finding the entry in hosts, so times out and then opens it anyway on localhost.

Now for the slow browsing problem I'd wager that is a bad /etc/resolv.conf, I'd expect to see an inappropriate local IP as the first in the list.  I'd insert your ISP's DNS server IPs in resolv.conf and expect to see better name resolution.

Remember that everything runs through your networking config, even local machine functions, so you will notice latency everywhere even when not using the network for bad hosts setups.  Hope this helps.

---

### Post by WinterWeaver on 2007-12-09
> **firefly76 said:**
> This sounds less like an IPV6 problem and more like a bad network configuration.  Latency when opening programs usually tips me off that the hosts file is out of whack.  Edit /etc/hosts and make certain loopback is setup correctly.  You're going to want:

```

127.0.0.1        localhost.localdomain    localhost
127.0.0.1        hostname.localdomain    hostname

```

where hostname is the name of your box and localdomain is your domain.  If you are using a domain name, make sure it's the same as the router's domain.  The machine is basically trying to open a program on loopback, but not finding the entry in hosts, so times out and then opens it anyway on localhost.

Now for the slow browsing problem I'd wager that is a bad /etc/resolv.conf, I'd expect to see an inappropriate local IP as the first in the list.  I'd insert your ISP's DNS server IPs in resolv.conf and expect to see better name resolution.

Remember that everything runs through your networking config, even local machine functions, so you will notice latency everywhere even when not using the network for bad hosts setups.  Hope this helps.

Thankx firefly... that does clear things up for me a bit. I'm still a wee bit confused tho? where do I set my Localdomain? In the hosts file, it's got a name, but under my network configuration it doesn't.

After I've set these up, I'll activate ipv6 again and give it a go.

thx for your explanation :)

WW

---

### Post by superstonerman on 2007-12-14
I’m currently having problems with my ubuntu internet. I’ve tried everything; this seems like something that could work as I haven’t tried it yet but its showing an authentication error when I try and edit the file even though i have opened a shell as root. :(

Does anyone know how to solve this problem thanks.

---

### Post by fenixfox on 2007-12-20
well it was a worth effort but im sad to say it still wont update and i cant go to anything bu tgoogle again...

---

### Post by firefly76 on 2008-02-14
> **WinterWeaver said:**
> Thankx firefly... that does clear things up for me a bit. I'm still a wee bit confused tho? where do I set my Localdomain? In the hosts file, it's got a name, but under my network configuration it doesn't.

After I've set these up, I'll activate ipv6 again and give it a go.

thx for your explanation :)

WW


Do it in /etc/hosts

Don't trust the network config GUI, I've had my own report an empty string with /etc/hosts was screwed up.  Could you post the contenst of your /etc/hosts file?

---

### Post by Dakiraun on 2009-04-22
> **nautilus said:**
> <rant>
I find it scary how many people running Ubuntu immediately remove IPv6 support without a second thought, even though it is the -current- Internet standard protocol irregardless of popularity....  If everybody in the world instantly disables the protocol on their system it sure isn't helping the migration, is it?
</rant>

<counter rant>If it had been put to a popular vote amongst IT professionals, IPv6 would never have become a standard in its current design (which is quite horrid).</counter rant>

Nonetheless, we must all face the fact that eventually it **will** become the primary protocol of the Internet - but how many years (or even decades) that will take is a good question.

IPv6 migration and use is proceeding extremely slow (particularly in North America), and I see this as a trend that will continue for a long, long time.  The reason is simple - to run it and support it requires replacement of equipment from the core to the edge in most networks, and the incredible cost paired with no gains has companies in no rush to take the plunge.  At my work (a University), we will only be adopting it as we slowly replace gear which is EOL.  Full support of the protocol (core to edge) is not likely to be in place for another 8 to 12 years.  Even once it is physically supported in the hardware, unless there is a direct need to run it, the drive to logically implement it could take years more.

I think most companies are in that exact same scenario.  In ours, devices that can spot IPv6 are told to drop the packets entirely, as they have been found to cause a slew of interesting issues (mostly with Vista machines).  Unless you know you're actually going to be on an IPv6 Network (quite unlikely in North America), there's no use in having it active in Ubuntu (or any OS).  Besides, if you know how to turn it off, it can be easily re-enabled should the time come that it's required.

---

### Post by kingswood71 on 2009-04-23
ok guys I have followed the ipv6 disable thread, and have done everything...I am connected, can ping and get good results back, but firefox refuses to load a single bloody page!!!! Help!!
cheers Rohan

---

### Post by Dakiraun on 2009-05-01
> **kingswood71 said:**
> ok guys I have followed the ipv6 disable thread, and have done everything...I am connected, can ping and get good results back, but firefox refuses to load a single bloody page!!!! Help!!
cheers Rohan

The IPv6 stuff would not prevent you from getting to a page in the first place.  You may have another network issue preventing Firefox (or other network services) from running.  What troubleshooting (if any) have you done to confirm that you're functioning properly.  If you've not tried anything yet, try pinging your gateway to make sure you can hit it, then check to see if you can resolve names properly with the command "nslookup", run from a command terminal.  Just use any site like "nslookup www.ubuntu.com", and you should see results.  If you can't get a name to resolve, check your DNS settings to make sure they're correct.  

If you can't ping or do nslookups, then your problem is definitely network related, and not Firefox related. If you can do a name lookup and ping, then it may be something less obvious.  Try using a command like "wget http://www.ubuntu.com" - it should download the file "index.html".  If it does not, then something is blocking port 80 traffic.  If it does, port 80 is okay.

If port 80's okay and Firefox still has issues, try installing an alternate browser like Seamonkey and see if that works.  If so, it may be a broken Firefox install.  Remove the package and delete the .mozilla directory in your profile (save your bookmarks first), then reinstall.

---

### Post by kingswood71 on 2009-05-01
thanks for reply. Sorted now.. it was /etc/resolv.conf problem!

---

### Post by Kevin Jayne on 2009-11-29
Using the about:config trick in Firefox did the trick! The browser feels like it's 10x faster now. Many thanks.

---

