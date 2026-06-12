---
title: "Blocking Domains and Host names to End Agressive Advertising"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by ac5jw on 2013-03-16
I want to solve my problem of pesky Internet advertisers clogging my web browser to the extent that I cannot perform the task that I originally want to do.

Is there a domain blocking solution available to Ubuntu 12.04.2 LTS or at least an easy-to-use firewall that can block communications with offending host names or domains?

I would not mind using IP blocking, but I am not smart on how to quickly and easily convert hundreds of host names and domain names to IP addresses for blocking.

I am keeping a sorted list of host names and domains for future input into a solution.

What should I be learning about or thinking of trying?

---

### Post by TVTrukChik on 2013-03-16
What  browser are you using?  You can get the Ad Block Pro extension for Chrome and Firefox.

---

### Post by ac5jw on 2013-03-16
Thanks for the ideas.  I am using Mozilla Firefox 19.0.2.  I am hoping to find a solution that permits me to input my list of hosts and domains to block.  I can check out the two plugins that you suggested to see if I can do that.

---

### Post by tgalati4 on 2013-03-16
I like Ad Block Edge.  Apparently Ad Block Pro has changed to allow "acceptable ads".  I'm not sure what defines "acceptable ads", but I'm pretty sure I don't want them.  Don't forget to add NoScript, the premier Javascript blocker/controller.

---

### Post by ac5jw on 2013-03-16
Thanks!  I have not yet tried these ideas yet, but I will maybe tomorrow after some sleep.  I imagine any acceptable advertiser will be paying money to the Ad Blocker service to let its ads remain displayed.  Kind of an extortion racket that does not benefit the audience, such as we web surfers.

I have not heard of Ad Block Edge until now.

---

### Post by ttoilleb on 2013-03-16
How about something Free, and fairly effective?

[http://winhelp2002.mvps.org/hosts.htm](http://winhelp2002.mvps.org/hosts.htm)  This web site maintains a hosts file blocking a large number of the sites that cause these problems.  It does this by directing URLs to 127.0.0.1

[http://www.putorius.net/2012/01/block-unwanted-advertisements-on.html](http://www.putorius.net/2012/01/block-unwanted-advertisements-on.html) and this site shows you how to automatically update on Linux.

Don't let the winhelp2002 fool you.  I have been using this for years and it catches about 95+% of unwanted sites.

The following is the script that I use.  It must run as root since you will be touching /etc/hosts.  Note the last line of the script.  Before I use this script for the first time, I do

sudo cp /etc/hosts /etc/hosts.local

From then on, I apply any local changes I make to the /etc/hosts.local file then run the script.

#!/bin/bash

#  script to download [http://winhelp2002.mvps.org/hosts.txt](http://winhelp2002.mvps.org/hosts.txt)
#
#  this file contains blocks for numerous spam, ad-tracking, etc sites
#  it blocks them by directing various urls to 127.0.0.1
#

cd /tmp
rm hosts.txt
wget [http://winhelp2002.mvps.org/hosts.txt](http://winhelp2002.mvps.org/hosts.txt)
rm /etc/hosts
mv hosts.txt /etc/hosts
cd /etc
cat hosts.local >> hosts

---

### Post by oldos2er on 2013-03-17
> **tgalati4 said:**
> I like Ad Block Edge.  Apparently Ad Block Pro has changed to allow "acceptable ads".  I'm not sure what defines "acceptable ads", but I'm pretty sure I don't want them. 

I use Ad Block Plus (not Pro) on both Chrome and Firefox; while it's true that it now has an option to "Allow some non-intrusive advertising" it's easily configured to block all ads if you prefer.

---

### Post by SeijiSensei on 2013-03-17
Install Ghostery along with AdBlock Plus to block tracking cookies.  I find it much more user-friendly than NoScript even with the new more glossy interface.

---

### Post by ac5jw on 2013-03-17
Thanks for the extra information, everyone!  I will examine all of it before committing to one solution because I want to meet my original goal.  I also am fairly new with Linux networking, so I want to tread carefully on this subject else I must reinstall to recover :)

The ideas you gave appear simple enough to explore and discover.  Please continue to post your suggestions if any more come to mind.

Best,

Raleigh - ac5jw

---

### Post by ac5jw on 2013-03-18
Hi everyone,

Thanks for all your help and advice!  I was able to implement the HOSTS file solution and perform all my host and domain name blocking from there.  I did not use the script, but I did follow the commands in the terminal and managed to create a good HOSTS file with all my desired blocking.  I am noticing that some websites like video.ftc.gov are coming in without choppiness or delays.  Prior to implementing the new HOSTS file, I was experiencing serious delays.

Because I retain complete control over my hosts file without giving up any control to another entity, I have decided to keep the HOSTS file solution.  I already wrote myself some notes about how to recreate the HOSTS file should I need to make changes in the future.

One thing I noticed was that my Ubuntu desktop name had a local address 127.0.1.1 and I went ahead and copied it from the original HOSTS file into the new one.  Then the computer told me after saving the file, that it could not resolve the local host for my desktop.  Of course, my desktop resolution was WHY I copied it into the file in the first place.  So, I simply logged out and back in to my desktop and tried out some blocked domains to see.  Everything was blocked as it should be, so I am convinced that I did it correctly.  That error message about resolving the desktop host name has not returned.

:D

---

### Post by DuckHook on 2013-03-18
...moreover, I actually find myself in agreement with the new Adblock Plus philosophy: namely, that discreet nonintrusive advertising can be a good thing. Many do-it-yourself websites support themselves by advertising, including sites owned by members of this very forum who maintain their highly informative sites as a public service but find some ad revenue desirable in offsetting costs. Provided their ads are not popups, resource hogs, A/V dynamic or otherwise in my face, I don't mind them. The new Adblock plus just defaults to allowing nonintrusive static ads from a list of vetted advertisers. And as @oldos2er observes, it is easy to turn off all ads entirely. Since I reject cookies by default and use cookie culler even on those cookies I accept, I don't have any concerns about ads tracking me either. It's a small and painless way to help out an ecosystem that is distinguished by how much we otherwise get for free.

---

### Post by tgalati4 on 2013-03-18
Thanks for the explanation behind "Acceptable Ads".  I was under the impression that it was a pay-to-let-slip-through service as you described earlier, but now it makes sense.  I will give it a spin.

---

