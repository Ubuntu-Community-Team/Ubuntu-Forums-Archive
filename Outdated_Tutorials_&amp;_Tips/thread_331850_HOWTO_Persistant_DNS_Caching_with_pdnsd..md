---
title: "HOWTO: Persistant DNS Caching with pdnsd."
date: 2007-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by bmt on 2007-01-05
A common complaint on the Ubuntu forums (and many other Linux sites, it seems) is the slow DNS look-up performance, especially compared with the same hardware running Windows.

One way of improving performance is to provide DNS caching on the local machine, so that repeated look-ups are quicker -- a local request rather than a trip out to the Internet and back.  Although some client programs do this for themselves (notably web browsers), many don't (notably mail clients, it seems to me).

This being Linux, there are many ways to achieve local DNS caching, of course, ranging from the simple to the complicated.  I have looked at several methods and this is the one that suits my needs.  I'm running a desktop installation on a small home network and the machine is rebooted daily.  This means that I need a solution that remembers its cache after a reboot -- I don't want to have to cache everything every morning.  This requirement for persistence let me to pdnsd (p for persistent ;-) ), but it suffers from a remarkable lack of documentation for the novice.  Eventually, I found [this article]("http://www.debian-administration.org/articles/390") on the Debian Administration site, which got me going in the right direction, but there are a couple of things to be clarified.

This is the procedure as I did it.

Note that these details are for Dapper with Gnome and without resolvconf installed.  I don't think anything will break if these changes are made to a different setup, but it may not work.  I haven't tried it.

Install pdnsd -- either by Synaptic or apt:

```
sudo apt-get install pdnsd
```

Now some editing of the pdnsd.conf file.  Start gedit as root user in a terminal (or Alt-F2):

```
gksudo gedit /etc/pdnsd.conf
```

Substitute your preferred editor, as required.

Save a back-up of the original -- e.g., Save As -> pdnsd.conf.orig

Now, find the part of pdnsd.conf that contains the DNS server to be used:

**Original:**
```

/*
server {
	ip="192.168.0.1";
	timeout=30;
	interval=30;
	uptest=ping;
	ping_timeout=50;
	purge_cache=off;
}
*/
```

and change it to read:

**Modified:**
```


server {
	label=OpenDNS;
	ip=208.67.222.222;
	ip=208.67.220.220;
	timeout=30;
	interval=30;
	uptest=ping;
	ping_timeout=50;
	purge_cache=off;
}
```

**Notes:**
1. It is vital to remove the '/*' and '*/'.  These are comment markers and nothing will work if they are left in!  Not obvious if you're not familiar with coding conventions (that's me!).
2. It is vital to include the semi-colon at the end of each line.
3. The 'label=' entry is optional, but may be useful for future diagnostics.
4. I have used the OpenDNS IP addresses.  These will work, but you may prefer to use your ISP's or other DNS servers.

Summary: I removed the comment signs and added a label and the two IP addresses.  Other entries are unchanged.

Next, comment out the part referring to resolvconf by adding /* and */ so that it looks like this:

**Modified:**
```
/*
# if you installed resolvconf, and status_ctl=on
server {
    label="resolvconf";
}
*/
```

Save the file as /etc/pdnsd.conf but don't close the editor window yet.

Most of us, I expect, use DHCP to set IP addresses on boot, so we need to make sure that our settings survive a reboot.  Amongst other things, DHCP tells the system where to find DNS servers, so open /etc/dhcp3/dhclient.conf in the editor.

Remove the comment mark (#) from the beginning of this line:

```
#prepend domain-name-servers 127.0.0.1;
```

and save the file.

In order to avoid having to reboot immediately, edit /etc/resolv.conf and add this line at the top of the file:

```
nameserver 127.0.0.1
```

(This is what the changes to dhclient.conf will do automatically at boot.)

The system will now look to the local cached DNS information rather than going directly to the Internet.

Restart pdnsd to make our changes active:

```
sudo /etc/init.d/pdnsd restart
```

If you want to test this arrangement and compare results, that is explained in the [reference article]("http://www.debian-administration.org/articles/390"), but I found that it was pretty obvious just by browsing to websites.

The first time a site is visited, there will be a delay while pdnsd finds the IP address from the external DNS servers, but subsequently it will just pull it from its cache -- like lightning!

References:
[Steve Kemp's article on Debian Administration]("http://www.debian-administration.org/articles/390") -- thank you very much.
man pdnsd
man pdnsd.conf
[pdnsd homepage]("http://www.phys.uu.nl/~rombouts/pdnsd/index.html"): Comprehensive documentation is here, but it may not be very accessible to us novices.
Also mentioned in [this thread]("http://www.ubuntuforums.org/showthread.php?t=197748") in connection with Internet Connection Sharing.

Uninstallation:
Remove the pdnsd package with Synaptic or apt:
```

sudo apt-get remove pdnsd

```
Restore original backup file for /etc/dhcp3/dhclient.conf (or add the # to the beginning of the 'prepend' line).
Restore original backup file for /etc/resolv.conf (or remove the 'nameserver 127.0.0.1' line).

Support:
I am not an expert.  I'll answer questions if I can, but mostly I'd have to research the answers first.  Or you could do the research and tell the rest of us. ;-)

Applicable to:
Ubuntu 6.06 Desktop i386, up to date today, Friday, 5 January 2007.

Please form an orderly queue with corrections. ;-)

---

### Post by madrano on 2007-01-13
won't work man

---

### Post by compuguy1088 on 2007-04-26
> **madrano said:**
> won't work man

Works fine for me, with both 6.10 and 7.04 with the settings mentioned in this guide.

---

### Post by silent1643 on 2007-09-11
using the dig feature to test this, and the cache doesn't appear to work

---

### Post by Max Randor on 2007-09-22
I use my laptop on more than one network. If I append the ip="192.168.1.1";
after the ip="..." that are for the network I use most frequently will it work?

---

### Post by eXSiR on 2007-09-22
thaks for howto, dns caching is working and feisty is faster than before.
```
xxx@ubuntu:~$ dig  @localhost youtube.com mx

; <<>> DiG 9.3.4 <<>> @localhost youtube.com mx
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50474
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;youtube.com.                   IN      MX

;; ANSWER SECTION:
youtube.com.            191     IN      MX      10 sjl-mbox1.sjl.youtube.com.

;; AUTHORITY SECTION:
youtube.com.            720     IN      NS      dns1.sjl.youtube.com.
youtube.com.            720     IN      NS      dns2.sjl.youtube.com.

;; ADDITIONAL SECTION:
sjl-mbox1.sjl.youtube.com. 191  IN      A       208.65.153.154
dns2.sjl.youtube.com.   705     IN      A       208.65.152.137

;; Query time: 34 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sat Sep 22 23:16:46 2007
;; MSG SIZE  rcvd: 129

```

```
xxx@ubuntu:~$ dig  @localhost youtube.com mx | grep time
;; Query time: 0 msec
```

---

### Post by trak87 on 2007-09-23
It works for me. Much faster internet now.

I don't know enough about OpenDNS to use their servers though. I'll stick to my isp's dns servers.

---

### Post by bionnaki on 2007-09-24
do you recommend this for users with routers? I already have opendns set on my router.

---

### Post by trak87 on 2007-09-26
Yes, it will make dns searches faster even if your router is providing the dns resolution. With pdnsd your local machine keeps a small cache of the dns data and thus avoids repeated resolution out on the 'net (via the router). For a big network with a lot of computers it would not be feasible to put pdnsd on all computers. In that case you'd want a local dns cache for your lan. But for one or a few computers it isn't much of a problem to set up.

---

### Post by lonoy on 2007-10-26
Thanks for the great instructions. Just a couple of questions please:

On the Open DNS page:

[https://www.opendns.com/start/ubuntu.php]("https://www.opendns.com/start/ubuntu.php")

It has the following instructions to make Open DNS work in Ubuntu:

```
$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ sudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
$ sudo ifdown eth0 && sudo ifup eth0 
```

I followed these instruction before yours as I am trying to make the Adult Content Filter work as well as improve my Internet speed.

My first question is should I have the line; 

prepend domain-name-servers 208.67.222.222,208.67.220.220;

present in /etc/dhcp3/dhclient.conf after following your instructions or is it not required as it was inserted by following the Open DNS guide.

Second question please, when I use the code:

```
sudo ifdown eth0 && sudo ifup eth0
```

Should the correct response be:

ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.

I am using 7.10 32 bit

Thanks again for sharing the knowledge.

Cheers
Lonoy

---

### Post by kerry_s on 2007-10-26
hmm, i use dnsmasq.
i do mine similar to yours:

sudo apt-get install dnsmasq
sudo xedit /etc/dhcp3/dhclient.conf
prepend domain-name-servers 127.0.0.1, 208.67.222.222, 208.67.220.220;

sudo xedit /etc/dnsmasq.conf
listen-address=127.0.0.1
(i also increase the cache, but it's not necessary)

then just reboot and your good to go

---

### Post by lonoy on 2007-10-26
I removed this line that I added from the Open DNS instructions:

prepend domain-name-servers 208.67.222.222,208.67.220.220;

and it is now working fine. Once I visit a page the second time it has now been cached and appears almost instantly as above.

One more question please, how does one clear the local cache if required?

---

### Post by bmt on 2007-10-26
Hi.

Apologies for not responding to queries earlier (except things like 'It won't work').  Thanks for contributions from others, which have mostly answered the questions, I think.

I have since upgraded to Feisty (via Edgy) and whatever was causing the delay in processing DNS queries seems to have gone away, to a large degree.  In reviewing my original post, I noticed that the dhclient.conf and resolve.conf files had been changed (probably during an  upgrade), so the local cache was no longer being used.  I have to say, I had not noticed a great difference in site access speed.

For some reason, I have only just found the [pdnsd homepage]("http://www.phys.uu.nl/~rombouts/pdnsd/index.html").  Click on the 'Documentation' link there, to find an additional comprehensive source of information!

From that page, the cache can be cleared by:```
sudo pdnsd-ctl empty-cache
```(I can offer no warranty on that instruction.)

In summary, I no longer use Dapper; the use of a local cache doesn't seem (to me) to be as necessary on Feisty, but the original instructions still work with Edgy and Feisty.

---

### Post by lonoy on 2007-10-26
Thanks.

Had a look at the documentation but it is way above my tech level.

I have your instructions working fine on Gutsy. The second time I visit a page it loads almost instantaneously which it was not doing before. 

Is there any way to retain the DNS cache between sessions?

---

### Post by bmt on 2007-10-26
> **lonoy said:**
> ...  when I use the code:

```
sudo ifdown eth0 && sudo ifup eth0
```

Should the correct response be:

ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.
It would appear that your network interface is not eth0, but the changes that the OpenDNS instructions give will become active at a reboot anyway.

---

### Post by bmt on 2007-10-26
> **lonoy said:**
> Had a look at the documentation but it is way above my tech level.
...
Is there any way to retain the DNS cache between sessions?
Shouldn't you Aussies be in bed by now? ;)

Don't imagine that I understand the docs for pdnsd!  A search in the page for 'empty' just brought up the right line.

The cache is persistent across reboots -- that's the 'p' in pdnsd.

---

### Post by lonoy on 2007-10-26
Rust never sleeps:)

Rebooted and all is fine. Thanks again for your time.

---

### Post by helpdeskdan on 2008-01-20
Great tutorial, thanks!  pdnsd appears to be better than dnsmasq!

---

### Post by CypherHackz on 2008-01-31
how about DSL? everytime when i reconnect to the internet, the nameserver in resolv.conf file change.

---

### Post by gary4gar on 2008-02-05
Thanks a Ton!
It helped me alot, before this i have tried Dnsmasq & Bind but none of them could save cache on disk.

Thanks again, I think you should post this to ubuntu wiki :)

---

### Post by Gathers on 2008-04-02
Thanks for the HOWTO! :)

I initially had some problems with pdnsd seemingly failing about a minute after starting. If I did nslookup or dig on a hostname I noticed I always got a SERVFAIL from 127.0.0.1 and then the normal dns-server was used. I guess pdnsd lost connection to the OpenDNS servers. If anyone else notices the same thing then try this config instead, in pdnsd.conf. (it has the long default timeouts and uses empty queries instead of pings as uptest)

```
server {
	label=OpenDNS;
	ip=208.67.222.222;
	ip=208.67.220.220;
#	timeout=30;
#	interval=30;
	uptest=query;
#	ping_timeout=50;
	purge_cache=off;
}
```

Btw, interval=30 seems a bit low? The default is 900 seconds, so it means 30 times more (mostly useless) pings for the OpenDNS servers to handle.

---

### Post by helpdeskdan on 2008-04-06
It seems as though hardy heron beta has better support for pdnsd.  Install resolvconf at the same time you install pdnsd.

sudo apt-get install pdnsd resolvconf

When it prompts, tell it to get it's configuration from resolvconf.   If you accidentally pick something else, do:

sudo dpkg-reconfigure pdnsd

That's all it takes - it will get the DNS servers from your ISP.  You can still manually edit the file, just be sure to check the status with:

sudo pdnsd-ctl status

---

### Post by Excalibre on 2008-09-27
> **helpdeskdan said:**
> It seems as though hardy heron beta has better support for pdnsd.  Install resolvconf at the same time you install pdnsd.

sudo apt-get install pdnsd resolvconf

When it prompts, tell it to get it's configuration from resolvconf.   If you accidentally pick something else, do:

sudo dpkg-reconfigure pdnsd

That's all it takes - it will get the DNS servers from your ISP.  You can still manually edit the file, just be sure to check the status with:

sudo pdnsd-ctl status
Right, but that doesn't actually work.

Does anyone know how to get this working, and test it to see if it's actually doing something? Because here's what happened to me: no difference, until I added that line in resolv.conf -- but once I add that, EVERYTHING returns "0 ms" when I do a dig, even domains that I haven't visited before. And obviously (since it's clearly not set up properly) it doesn't make my web browsing any faster.

Also, when I removed the packages it didn't automatically copy /etc/resolv.conf.dpkg-old back into place, so I couldn't resolve any domain names for a minute. Good job, Ubuntu!

---

### Post by aladinonl on 2008-09-27
> **Excalibre said:**
> Right, but that doesn't actually work.

Does anyone know how to get this working, and test it to see if it's actually doing something? Because here's what happened to me: no difference, until I added that line in resolv.conf -- but once I add that, EVERYTHING returns "0 ms" when I do a dig, even domains that I haven't visited before. And obviously (since it's clearly not set up properly) it doesn't make my web browsing any faster.

Also, when I removed the packages it didn't automatically copy /etc/resolv.conf.dpkg-old back into place, so I couldn't resolve any domain names for a minute. Good job, Ubuntu!

Hi, I got the same problem. Everything needs 0 ms to llokup even with ones I tried the first time. Ridiculous! I really want to use this tool. Can anyone offer help?

---

### Post by bmt on 2008-09-29
> **Excalibre said:**
> Also, when I removed the packages it didn't automatically copy /etc/resolv.conf.dpkg-old back into place, so I couldn't resolve any domain names for a minute. Good job, Ubuntu!

From the original post:
> Uninstallation:
...
Restore original backup file for /etc/dhcp3/dhclient.conf (or add the # to the beginning of the 'prepend' line).
Restore original backup file for /etc/resolv.conf (or remove the 'nameserver 127.0.0.1' line).

---

### Post by bmt on 2008-09-29
> **aladinonl said:**
> Can anyone offer help?

I'm afraid I'm still using Gutsy (where it still works fine, using the original instructions), but any Hardy users are welcome to step in here.

---

### Post by Excalibre on 2008-09-29
> **bmt said:**
> From the original post:
Yeah, I fixed it. I was just complaining because the package manager should have handled that automatically.

---

### Post by davidryder on 2008-10-02
Anyone compare the results of this to that of using BIND?

---

### Post by helpdeskdan on 2008-10-10
Still working great for me.  Post an nslookup of google and a sudo pdnsd-ctl status and I'll tell you what is wrong.

I just set it up on a computer with a static IP.  Here are the steps I used to get it working with opendns:

sudo apt-get install pdnsd resolvconf
(select manual this time)
edit the /etc/pdnsd.conf 
comment out line so (may already be commented out):

/*
server {
    label="resolvconf";
}
*/

Add this right after:
server {
        label=OpenDNS;
        ip=208.67.222.222;
        ip=208.67.220.220;
        timeout=30;
        interval=30;
        uptest=ping;
        ping_timeout=50;
        purge_cache=off;
}

Do a:
sudo /etc/init.d/pdnsd restart

And it should work.  Last time I tried my previous instructions, it worked - not sure why they don't work now.  Perhaps I'll look into it later, I don't use DHCP right now because my cheap linksys is horrible.  Note also that my /etc/resolv.conf is blank.

---

### Post by poopypants on 2008-10-21
to get this working on intrepid/8.10 using dhcp I did:
```
sudo apt-get install pdnsd resolvconf
```
choose the resolveconf option (I think, accidentally chose manual initially then went back into the dialog using dan's sudo dpkg-reconfigure pdnsd).

then put the dns servers in my dhcp setup:
```
sudo vi /etc/dhcp3/dhclient.conf
....
#prepend domain-name-servers 127.0.0.1;
prepend domain-name-servers 127.0.0.1, 208.67.222.222, 208.67.220.222, 208.67.220.220;
request subnet-mask,....

```

configure pdnsd commenting out resolvconf and adding the opendns entry (per the default commented-out sample and here):
```
sudo vi /etc/pdnsd.conf
....
/*
server {
    label="resolvconf";
}
*/
server {
        label=OpenDNS;
        ip=208.67.222.222, 208.67.220.222, 208.67.220.220;
        timeout=5;
        uptest=query;
        interval=30m; // test every half hr
        ping_timeout=300; // 30 sec
        purge_cache=off;
        exclude = .localdomain;
        policy = included;
        preset = off;
}

```

reboot and it seems to work. is there anything I should've done differently?

---

### Post by budjo on 2008-10-27
I think it's working on my hardy using poopypants step. Moreover, how to set it as dns proxy for networked computer?? It should be possible I guess. Thanks.

---

### Post by Warren Watts on 2008-10-27
I wrote a perl program a while back to analyze the relative speeds of each of the DNS servers detected by dhcpcd (DHCP client daemon) through use of dig (a DNS lookup utility) and display a sorted list of DNS servers from fastest to slowest.

Here's the perl script and the corresponding output from the command line:

```
#!/usr/bin/perl 

######################################################################################
# scan_dns.pl version 0.7 9/20/07
# Author: Warren Watts (kingbeetle_66(at)yahoo(dot)com

# This program will analyze the relative speeds of each of the DNS servers
# detected by dhcpcd (DHCP client daemon) through use of dig (a DNS lookup utility)
# and display a sorted list of DNS servers from fastest to slowest.
# This sorted list can then be used to tweak the /etc/resolv.conf file, providing
# faster DNS lookups while browsing, etc.
 
# I included three domains for dig to lookup.  They are stored in @domain_list.
# Feel free to add to the list or change the domain list to any domains you wish.
# Be aware that the more domains in the list, the longer the scan will take!
#######################################################################################

use strict;

my (@DNS,$IP,$time,$domain,$dig,%time,$key);

# Read the DNS list from /etc/resolv.conf and store the list in an array
my $resolv = `cat /etc/resolv.conf`;
while ($resolv =~ /nameserver (.*)\n/g) {push(@DNS,$1)}

#List the DNS servers listed in /etc.resolv.conf
print "+----------------------------------------------------------------------+\n";
print "The following DNS servers are listed in /etc/resolv.conf:\n";
foreach $IP (@DNS) {print "$IP\t"}
print "\n";

# Store list of domains to be looked up by dig in an array
my @domain_list = ('www.yahoo.com' ,'www.fasthit.net' ,'zz.nullwave.ru');

# List the domains to be used by dig during the scan
print "The following domains will be for this scan:\n";
foreach $domain (@domain_list) {print "$domain\t"}
print "\n";
print "+----------------------------------------------------------------------+\n";

# Count number of domains stored in the array
my $domain_count = @domain_list; 
# Go through the list of DNS servers and execute dig for each DNS server and each  
# domains in the domain list, extract the time taken and average the times together,
# then store the DNS and averaged time in a hash.
foreach $IP (@DNS) 
{
  print "Scanning $IP\n";
  $time = '';
  foreach $domain (@domain_list)
  {
    print "-->  $domain\n";
    $dig = `dig \@$IP $domain`;
    if ($dig =~ /Query time: (.*) msec/) 
    {
      $time = $time + $1;
    }
  }
  $time{$IP} = int(($time / $domain_count) +0.5);
}
print "+----------------------------------------------------------------------+\n";

# Display the results sorted by time in ascending order
foreach my $key (sort hashValueAscendingNum (keys(%time))) 
 {
  print "Average fetch time for $key : $time{$key}\n";
}

# Subroutine to sort by time rather than by DNS address
sub hashValueAscendingNum 
{
   $time{$a} <=> $time{$b}
}
```


Sample output:
> everyone@ubuntu550:~/Desktop$ perl test.pl
+----------------------------------------------------------------------+
The following DNS servers are listed in /etc/resolv.conf:
208.67.222.222  208.67.220.220  192.168.0.1
The following domains will be for this scan:
[www.yahoo.com](www.yahoo.com)   [www.fasthit.net](www.fasthit.net) zz.nullwave.ru
+----------------------------------------------------------------------+
Scanning 208.67.222.222
-->  [www.yahoo.com](www.yahoo.com)
-->  [www.fasthit.net](www.fasthit.net)
-->  zz.nullwave.ru
Scanning 208.67.220.220
-->  [www.yahoo.com](www.yahoo.com)
-->  [www.fasthit.net](www.fasthit.net)
-->  zz.nullwave.ru
Scanning 192.168.0.1
-->  [www.yahoo.com](www.yahoo.com)
-->  [www.fasthit.net](www.fasthit.net)
-->  zz.nullwave.ru
+----------------------------------------------------------------------+
Average fetch time for 208.67.222.222 : 43
Average fetch time for 208.67.220.220 : 291
Average fetch time for 192.168.0.1 : 834

You should be able to use this to test whether your local DNS cache is working, right?

I also included the script as a handy tarball as well.

---

### Post by jonthysell on 2009-09-05
This is all I did in Jaunty, without any config file editing.

**Quick Summary:**

```
sudo cp /etc/resolv.conf [COLOR="SeaGreen"]/etc/resolv.conf.bak[/COLOR]
sudo apt-get install resolvconf
sudo apt-get install pdnsd
```

Choose "Use resolvconf". In the next line, replace [COLOR="Magenta"]eth0[/COLOR] with the name of your interface if it's different.

```
sudo mv [COLOR="SeaGreen"]/etc/resolv.conf.bak[/COLOR] /etc/resolvconf/run/interface/[COLOR="Magenta"]eth0[/COLOR]
sudo resolvconf -u
```

Done! If you want step-by-step explanations:

**Longer Steps:**

First, save your current nameserver setup (this is not superfluous paranoia, you're going to need this later):

```
sudo cp /etc/resolv.conf [COLOR="SeaGreen"]/etc/resolv.conf.bak[/COLOR]
```

Next install resolvconf. If we don't install it first, we'll get weird errors from pdnsd because of how resolvconf replaces the /etc/resolv.conf file with a symbolic link:

```
sudo apt-get install resolvconf
```

Next install pdnsd:

```
sudo apt-get install pdnsd
```

Choose "Use resolvconf".

You'd assume that it would just work, but it doesn't, cause the setup process has lost your original nameserver information.

So when you try to resolve a name, the system will look to resolvconf, who'll direct the request to pdnsd. Pdns has nothing cached yet, so it asks resolvconf for the next server to check, but resolvconf has no one to ask next.

So, we tell resolvconf that for that network interface, to use the config we were using before we started any of this. So move the backup file we made where resolvconf can see it. Since this was for my [COLOR="Magenta"]eth0[/COLOR] interface, I used:

```
sudo mv [COLOR="SeaGreen"]/etc/resolv.conf.bak[/COLOR] /etc/resolvconf/run/interface/[COLOR="Magenta"]eth0[/COLOR]
```

Finally, update resolvconf with:

```
sudo resolvconf -u
```

Took me a few tries to pare this down, but this works for me, end to end.

For a wireless config (where you're connecting to different networks), or if you just want to use say, OpenDNS for all of your interfaces all the time, just create a file /etc/resolvconf/run/interface/opendns with the following:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

Then update resolvconf again with:

```
sudo resolvconf -u
```

Hope this helps!

---

### Post by noren on 2009-10-10
wow it worked from the help of above post real short and simple

---

### Post by djkmmo on 2009-12-01
> **aladinonl said:**
> Hi, I got the same problem. Everything needs 0 ms to llokup even with ones I tried the first time. Ridiculous! I really want to use this tool. Can anyone offer help?

A bit late, but I haven't used this tool before. I run 8.04 and had the same problem as you and this solved it for me: pdnsd doesn't honor the settings in /etc/pdnsd.conf if AUTO_MODE is set in /etc/default/pdnsd and it is set to resolveconf by default. I.e. you can change whatever you want in /etc/pdnsd.conf and it will have no effect whatsoever.

The solution is to comment out AUTO_MODE in /etc/default/pdnsd, then /etc/pdnsd.conf will be used insted of /usr/share/pdnsd/pdnsd-$AUTO_MODE.conf (/usr/share/pdnsd/pdnsd-resolvconf.conf in most cases). You shouldn't edit /usr/share/pdnsd/pdnsd-$AUTO_MODE.conf directly as this file probably will be replaced when the package is upgraded.

If you want to see if it's actually caching anything you can do a lookup in the cache with pdnsd-ctl dump before and after you have done a dig:

```
USER @ Computer:~$ sudo pdnsd-ctl dump |grep -i google.com
[1] USER @ COMPUTER:~$ dig  @localhost google.com mx
...
USER @ Computer:~$ sudo pdnsd-ctl dump |grep -i google.com
google.com.
```
Replace "google.com" with an address you haven't visited. The "[1]" after the first command means that grep couldn't find any hits for the string from the output of pdnsd-ctl dump.

---

### Post by noren on 2009-12-03
is there any way to use ad-block list with pdsd

---

### Post by gillespiea on 2009-12-16
I'd just like to say a big thank you.
I was wondering why my internet wasn't loading as fast as it did when i used windows, then i stumbled on this. thanks soooo much. My internet is now stupidly fast again :D

---

### Post by Artemis3 on 2010-02-08
I'm even lazier so avoided resolvconf by using the magical command:

```
sudo apt-get --no-install-recommends install pdnsd
```

And followed instructions exactly like the first post :)

---

### Post by allstats on 2010-03-12
> **Artemis3 said:**
> I'm even lazier so avoided resolvconf by using the magical command:

```
sudo apt-get --no-install-recommends install pdnsd
```And followed instructions exactly like the first post :)
Thats it. Me too. Grate effect on my netbook.

---

### Post by corruptor1972 on 2010-05-23
FYI there is a bug registered on Launchpad:  [pdnsd requires manual restart after new WiFi connection gets established]("https://bugs.launchpad.net/ubuntu/+source/pdnsd/+bug/452351").  

I was having all sorts of problems with this issue and (eventually) came up with the solution I posted there.

I installed pdnsd and resolvconf and chose the Manual setup when prompted.

---

### Post by karmila on 2010-08-01
Thank you for this tutorial. I simply followed your instruction, and up my browsing speed.

I will read all over the post, and maybe back for some question later (actually, i have some questions but i don't want to bother you with asking the same question twice) ;)

---

### Post by lhaeh on 2010-12-05
It says that it fails when trying to restart the daemon:

```

lhaeh@ubuntu:~$ sudo /etc/init.d/pdnsd restart
 * Stopping pdnsd                                                        [ OK ] 
 * Starting pdnsd                                                        [fail] 
```



I get this from my syslog:
```
Dec  5 16:09:30 ubuntu pdnsd[13171]: Could not bind tcp socket: Address already in use
Dec  5 16:09:30 ubuntu pdnsd[13171]: Could not bind to udp socket: Address already in use
Dec  5 16:09:30 ubuntu pdnsd[13171]: tcp and udp initialization failed. Exiting.
Dec  5 16:13:03 ubuntu named[3588]: error (network unreachable) resolving 'ns3.mydns.pro/A/IN': 2001:500:1::803f:235#53
Dec  5 16:13:03 ubuntu named[3588]: error (network unreachable) resolving 'ns2.mydns.pro/AAAA/IN': 2001:7fd::1#53
Dec  5 16:13:03 ubuntu named[3588]: error (network unreachable) resolving 'ns4.mydns.pro/AAAA/IN': 2001:503:c27::2:30#53
*SNIP*
```


However, when I use dig to measure how long it takes to resolve names, I find that caching IS working.


Edit: Seems to be a conflict between it and bind, killing named before trying to run pdnsd lets it run, however then bind has issues when you restart it:
```
lhaeh@ubuntu:~$ sudo killall named
lhaeh@ubuntu:~$ sudo /etc/init.d/pdnsd restart
 * Stopping pdnsd                                                        [ OK ] 
 * Starting pdnsd                                                        [ OK ]

lhaeh@ubuntu:~$ sudo /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                        
rndc: connect failed: 127.0.0.1#953: connection refused
                                                                         [ OK ]
 * Starting domain name service... bind9                                        
Failed: Bad server label.
Opening socket /var/cache/pdnsd/pdnsd.status
                                                                         [ OK ]
```

So, I guess the thing to do is to keep one of them from trying to use port 953, but I don't know how do that.

---

### Post by zenon222 on 2011-04-18
I'm having an issue with local windows servers.  For example if I navigate to ```
smb://dave-12183u0zgf/shareddocs/
```With pdnsd running, no dice.  Perform a ```
sudo /etc/init.d/pdnsd stop
```And I'm back in business.

Ideas??

---

### Post by ticket on 2011-07-02
Trying to get this DNS caching working for natty 11.04.

Almost did it - but I can't get it to 'stick'.

Here's what i did to get it almost working:
(with thanks to all the contributors to this thread):

Install pdnsd. 
(Synaptic likes to also install the resolvconf package - this form of the command stops that) 
```
sudo apt-get --no-install-recommends install pdnsd
```

Edit the pdnsd config file:
```
gksu gedit /etc/pdnsd.conf
```
And make the changes suggested in post #1, i.e. comment out the server section for resolv.conf, and modify the other server to point to your favourite DNS server.

Then modify these files:
```
gksu gedit /etc/dhcp/dhclient.conf
gksu gedit /etc/dhcp3/dhclient.conf

```
to remove the # in the line: 
```
#prepend domain-name-servers 127.0.0.1;
```
(i.e. uncomment it).

Note: I could only get 'nameserver 127.0.0.1' to appear in /etc/resolv.conf by editing /etc/dhcp/dhclient.conf.
It is pointless editing /etc/resolv.conf as it is automatically generated.

Finally, check that /etc/default/pdnsd is like this:

```
# do we start pdnsd ?
START_DAEMON=yes
# auto-mode, overrides /etc/pdsnd.conf if set [see /usr/share/pdnsd/]
#AUTO_MODE=
# optional CLI options to pass to pdnsd(8)
START_OPTIONS=
```

(If START-DAEMON is commented out, or set to 'no', then it will be impossible to start pdnsd. Also, if AUTO_MODE is set to something, then your custom /etc/pdnsd.conf will be ignored)

Restart the system and test it using 'dig', e.g.
dig [www.goog.com](www.goog.com)     (some site you haven't visited before)

Check the dig query worked (no error):
```
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 33790
```

Check the server used was  127.0.0.1
```
;; SERVER: 127.0.0.1#53(127.0.0.1)
```

If you dug an unvisited site, the reported query time should be around 50ms:
```
;; Query time: 24 msec
```

Do another dig and the query time should become zero.

To check the cache size is increasing with each new web site, use
```
sudo pdnsd-ctl status
```
The first few lines of printout will contain:

```
Cache status:
=============
10240 kB maximum disk cache size.
1207140 of 10496000 bytes (11.5%) memory cache used in 5022 entries. 
```


The contents of my /etc/resolv.conf: (automatically generated)
```
# Generated by NetworkManager
domain lan
search lan
nameserver 127.0.0.1
nameserver 192.xxx.yyy.zzz
```
(192.xxx.yyy.zzz is my router address)

However, in my case, pdnsd only worked successfully if, having logged in, I restarted it using:
```
sudo /etc/init.d/pdnsd restart
```

Otherwise dig queries would always return a query time of 0 msec and the cache would not get updated.

I tried a couple of ways to automatically restart pdnsd during login, 

(a)
Inserted into /etc/rc.local  : 
```
/etc/init.d/pdnsd restart
```

(b)
Put script into /usr/local/bin :
```
#!/bin/sh
/etc/init.d/pdnsd restart
```
& put a script launcher into /etc/xdg/autostart

But neither of these helped.

Something is amiss, but I don't know what.

[Motive for using pdnsd: if ever the PTB kill the internet by killing dns servers, a cache will mean you still have a connection]

---

