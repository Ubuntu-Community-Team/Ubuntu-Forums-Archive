---
title: "Problems setting up Apache on Ubuntu 16.04"
date: 2019-06-07
forum: New to Ubuntu
---

### Post by mwoosley on 2019-06-07
Hello everyone.  I am hoping that I can get a recommendation for support regarding my LAMP stack install.

Linux installed with no issues and Apache is where I'm struggling at currently.

I am following a tutorial from Digital Ocean ([https://tinyurl.com/y98gxrg3](https://tinyurl.com/y98gxrg3)), and for whatever reason(s), I cannot access my 2 additional virtual websites (the default one works fine).  I've pretty much followed the tutorial to the letter but am now wondering if the tutorial has missing steps.

One of those steps that isn't mentioned is the *POTENTIAL* need to edit the /etc/apache2/apache2.conf file.  Some techs state that you should NEVER touch this file, while others say go ahead.  From what I understand, one can setup their entire config in this one file, but again, most say to formulate individual files and leave this file alone.  

I'm at a loss of what to do in order to have all 3 websites (default and 2 additional) work.

Could someone direct me to a resource other than Digital Ocean for setting up Apache.  Even the Apache website differs in comparison to what others say works, hence the confusion behind my dilemma.

*quick update - found Ubuntu's Apache page, but it appears that it is inline with Digital Oceans tutorial... so I'm apparently missing something important.  If anyone has tips to share, I would love to hear them.

Thanks.

---

### Post by SeijiSensei on 2019-06-07
First, I'd use 18.04 rather than 16.04.

As for configuring multiple virtual hosts, take a look at my post here: [https://ubuntuforums.org/showthread.php?t=2420197&p=13863238&viewfull=1#post13863238](https://ubuntuforums.org/showthread.php?t=2420197&p=13863238&viewfull=1#post13863238)

---

### Post by mwoosley on 2019-06-08
SeijiSensei, I am going to take your initial advice and remove 16.04 and install 18.04, as I'm having too many problems with how Ubuntu is working.  Right now, I keep getting errors saying the Apache2 service is unavailable due to the LSB not loading.  

Please keep this thread open so we can relook this and I can update you on my status.  I am eager to get this off the ground as soon as possible.

Thanks a million for stepping in with your advice :)

---

### Post by mwoosley on 2019-06-09
[COLOR=#000000]SeijiSensei, I took your advice and installed Ubuntu 18.04.  This and installing Apache2 again did not present my neither of my additional domains.  I'm sure it's something I have not touched yet or quite possibly don't understand (I'm doing something wrong)
If I may, I'll illustrate in steps what I did...
[LIST]
[*]Performed a clean install on a physical PC (no additional OSes)
[*]Installed MC (sure this doesn't matter, but just in case)
[*]Performed initial server setup by installing SSH keys (instructions from Digital Ocean)
[*]Installed Apache
[*]Added Apache to the UFW (universal firewall)
[*]Checked my server IP address and noted it
[*]Edited the /etc/hosts file by adding the servers ip address and domain name below the local loop addresses
[*]From ANOTHER computer (Windows 10), I typed my IP address into the address bar... the default page was returned (At this point, the 000-default site is still enabled... this is what we expect though)
[*]I created 2 virtual host files, one for domain1.com and one for domain2.com (I use the format provided by Digital Ocean)
[*]I disable (a2dissite) the 000-default site and ENABLE the other 2 domains with 'a2ensite domain1.conf' and a2ensite domain2.conf' (verified that default WAS NOT enabled and the other 2 are ENABLED)
[*]Restarted Apache with 'sudo systemctl restart apache
[*]When I enter my IP address this time, my domain1 website shows (obviously, the ip address is only going to return 1 site)
[*]If I attempt to enter the 'domain1.com OR the 'domain2.com' into the address bar (NOT he IP Address), I get a server address not found.
[*]In other words, I have not been able to bring up my second domain, domain2, PLUS, these other issues.
[*]What I think I want, is the ability to, from ANOTHER network Windows PC, to open my domain1 and domain2 sites with Chrome using their domain names... without regard to the servers IP address.
[*]Finally, I may be trying to over-simplify some stuff and in turn I'm failing to see what I need to see.
[/LIST]

So, this is where my ignorance comes into play.  After following the tutorials at hand, I still cannot figure out why I cannot render either domain1 or domain2 with the domain names in the web browser.  I know it's something I don't know or understand as I'm truly trying to self teach myself these things.  Neither of these domains are what I think they call FQDN's, whatever that means.  

Based of what I have read so far, I should be able to put ANY domain name into my config files and they should work... at least locally.  

Any thoughts to help out a slightly IT challenged wanna be?

PS - If I need to provide my files, I am not opposed to doing so.[/COLOR]

---

### Post by SeijiSensei on 2019-06-09
First, a "fully-qualified domain name" consists of a host and domain, like "www.ubuntuforums.org". The domain is ubuntuforums.org; the hostname is www. Put the two together to get an FQDN.

Apache identifies virtual hosts by their fully-qualified names, not their IPs. Connecting to the IP should bring up the default page, though you apparently disabled it. Are you the registrant for the domains you are using?  Or did you just make them up?  

I would make sure /etc/hosts on both the server and client have entries for the names you intend to use.  Use the aliasing feature to assign all the names to the IP address like this:

```
10.10.10.10     www.domain1.name domain1.name www.domain2.name domain2.name
```

Then make sure you can "ping www.domain1.name" and get a response from the server.  Same for domain2.

---

### Post by mwoosley on 2019-06-09
SeijiSensei, thank you again for all your help.  Your suggestion to edit the client machines host file did the trick.  I ran across this situation a few years ago, but as I'm getting older, much of this stuff escapes me.  I do own a couple domains that I will eventually forward to my server for my own hosting, but for now and  the very near future, I want to pick up the needed skills to do so in a manner that at least looks like I know what I'm doing.  So, for now, the make believe domains will work and help me grown my IT skills.  

I wish, and I know it's a stretch, that these tutorials would elaborate a little on the not so obvious topics such as client/server relationships... in my case, remind us knuckleheads to update both client/server host files.  

Regardless, thank you so much for your help and I will hopefully someday be able to pay it forward.

Best,
Mike

---

