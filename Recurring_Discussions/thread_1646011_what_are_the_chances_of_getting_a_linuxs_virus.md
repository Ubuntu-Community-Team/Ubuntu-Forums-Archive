---
title: "what are the chances of getting a linuxs virus?"
date: 2010-12-15
forum: Recurring Discussions
---

### Post by Spyderkid on 2010-12-15
I would like to know i've been using linux for a while...

>what are the statistics of getting a virus? (eg.. 1/100)

>can you get viruses from just visiting sites like on windows

>and can you get for example trojan viruses or are they just the annoying mess your computer ones (so are they all obvious)

thanks!

---

### Post by Swagman on 2010-12-15
Practically Zero <--- But depends on user stupidity for all those questions

---

### Post by TeoBigusGeekus on 2010-12-15
[Interesting article.]("http://www.neowin.net/news/a-history-of-viruses-on-linux")

---

### Post by mmsmc on 2010-12-15
The only way you can get a virus on linux is that it has to be wrutten for linux, very few(dont know the stats) **AND **you have to give it access via your password.
Remember linux is not eindows so you cannot get a vvirus by just visiting a webpage, but if you do feel that you are not safe web surfer, you should use the no script and WOT add ons fro firefox, they will definitly prevent any viruses from affecting your comp(almost impossible)
 
keep in mind though that a virus may not affect your linux system,but it still can exist in a file and be transferred to a windows system

---

### Post by Habitual on 2010-12-15
3 word answer.

slim to none.

'nuff said.

---

### Post by WorMzy on 2010-12-15
~>1%

[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

---

### Post by philinux on 2010-12-15
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Moved to Recurring Discussions.

---

### Post by aysiu on 2010-12-15
Whether you get malware or not is not primarily a matter of chance.

This is like saying "What are the chances of my getting an orange juice this morning?"

Well, it's not up to chance. It's up to you. If you decide to buy orange juice, you'll get it. If you decide not to, you won't. Sure, there is a tiny chance someone may just randomly, without you asking, throw a box of orange juice at you, but it's not mainly a matter of chance.

Computer security should never be left up to chance. Be informed. Learn how to protect yourself (strong passwords, system updates, NoScript, AppaArmor, etc.) and don't rely on fake protection (false promises about chances of getting a virus, so-called "antivirus" software that's useless).

---

### Post by Spyderkid on 2010-12-16
is Klam anti-virus worth getting or not?

and thanks for the information.

Is one of the only ways to get a virus on linux to run a script downloaded from the internet from non-certified places?



and also is it safe to download most stuff from source-forge? (I know its trusted by ubuntu I just wondered)

---

### Post by deanjm1963 on 2010-12-16
Clam (Klam) is only valuable if you receive "attachments" from windows machines and if you're going to send those attachments to other windows machines. Viruses as such can't run on a linux box as they don't haved the necessary permissions.

And as far as Source-Forge goes - it's like crossing the road, look left, look right and look left again. I've never had a problem from the few things that I've downloaded from there, mainly gparted, but you have to remember, this is open source - once there's a bug or a malicious piece of code it is soon reported - to EVERYONE and fixes are soon put in place - so I think you'd be fairly safe - just keep an eye out for "Crazy Joes Horizonal Cha Cha Movie Downloader.deb" etc ;)

Hope this helps.

---

### Post by Anteaus on 2010-12-16
> **Spyderkid said:**
> is Klam anti-virus worth getting or not?

and also is it safe to download most stuff from source-forge? (I know its trusted by ubuntu I just wondered)

Clam AV is good, if rather prone to false positives. Thus if it tells you there is an infection, don't panic and do anything drastic. Upload the file to virustotal for a second opinion.

Though, I don't run resident AV on Linux, and (touch wood) have never yet been hit. I may manually scan the fs occasionally when I'm feeling paranoid, that's about all.

Unlikely you will find malware on Sourceforge, but remember most of the stuff is beta code, so always the risk of a coding blunder causing damage. Best advice is to test on a non-production computer first. A virtual machine is handy here.

As regards the web-browsing risks, I wonder if there are any stats regarding buffer-overrun exploits in Linux browser-plugins like Flash? These tend to be the main risk on a Win/Firefox setup, once IE is out of the picture.

---

### Post by amsterdamharu on 2010-12-16
Installing stuff out of the repositories might break your system even if it wasn't intended as a virus. Or you might do something wrong to force a package to install and break something.
My advice is to ask here before installing anything that is not in the repository.

As for Klam av I hear it doesn't detect so good and it's only to detect Windows viruses, so ok if you want to check before sending files to someone or scan your Windows partition but it might not detect a virus that is there.

---

### Post by handy on 2010-12-16
Really it is a silly topic.

If there was a security problem with Linux, viruses & such, it would be a common topic for discussion in this forum. 

It ain't & thus far never has been. :)

Linux users would be using anti-virus software, scanning for mal-ware & such. As it stands some people do an occasional scan for a root-kit. Something I haven't done in well over a year.

There is the occasional security hole discovered in Apache & such, you can imagine how quickly they are fixed... Something like the speed of lightening.

GNU/Linux kernel based systems (& every other system I have seen) is built in a vastly superior fashion when it comes to security than are all of the various versions of Windows that I have seen.

Windows is the odd-system out. If MS had of not incorporated the registry (so as to appeal to the other closed source members of that crew) & had of made the user have an account that did not have administrative privileges then they might have had a chance.

All they can do now is hold on as best they can with their insecure OS's whilst they prepare for their fast approaching new primary source of income being cloud application vendors.

That's how I see it anyway.

---

### Post by Schugy on 2010-12-16
Firefox extensions and java applets are quite dangerous.
[Or install antivirus.]("http://dlpe.antivir.com/package/wks_avira/unix/en/pers/antivir_workstation-pers.tar.gz")

---

### Post by Spyderkid on 2010-12-16
You may think it's a silly topic but in the last two years there has been a 50-100% increase in linux viruses.

Even though there are only admittedly 800ish viruses out on the whole world wide web

---

### Post by handy on 2010-12-16
> **Spyderkid said:**
> You may think it's a silly topic but in the last two years there has been a 50-100% increase in linux viruses.

Even though there are only admittedly 800ish viruses out on the whole world wide web

Sorry, I didn't mean to be personally rude by calling it a silly topic. :)

Back on topic:

So what? There are now something like 16 viruses that can work with the Linux kernel? (There would be more than that, but the architecture of the GNU/Linux kernel based systems just does not lend itself to virus proliferation, the same as the basically Unix based OS X, doesn't either.)

I don't know about the new ones you speak of which undoubtedly exist, but the old ones were mostly created in labs by software engineers as experiments & didn't even go out into the wild.

You are best off to just forget this topic Spyderkid, as at this point in time the only people running a distro that truly need to be concerned about viruses are those people that are running Linux servers that serve Windows machines with mail & such. For obvious reasons you run an anti-virus application for the benefit or your Windows clients & NEVER to protect your server as there is just no need.

Some paranoid Linux users use an anti-virus to protect their systems; they are a minuscule percentage of the flock.

As far as Firefox add-ons are concerned, the only one I have heard about that may be a threat, is GoogleSharing, as it was bought by a bunch of marketroids.  The only add-ons I use are apart from an Oz dictionary, to do with privacy & ad blocking anyway. 

It is probably a good idea to do a Scroogle search on any add-on we want to use before we commit to it, though really, if you watch this forum, someone will create a thread on a known problem pretty quickly. That is one of the benefits of a forum with so many members.

[edit:] I use a bunch of add-ons to protect my privacy & block ads on the web:

Adblock Plus
Beef Taco
BetterPrivacy
GreaseMonkey <with the GooglePrivacy script>
NoScript

I also make a couple of edits to to Firefox via the about:config configuration method:

By setting network.http.sendRefererHeader in Firefox preferences (about:config) to zero, then whenever you visit a link from one site, the destination site doesn't know the original site you were referred from.

This in effect makes the Firefox add-on RefControl redundant. (I think?)

Also, by setting network.prefetch-next to false it brings about the following:

Link prefetching is when a web-page hints to the browser that certain pages are likely to be visited, so the browser downloads them immediately so they can be displayed immediately when the user requests it. This preference controls whether link prefetching is enabled.

I prefer this disabled personally, for a variety of reasons.

By the way, Symantec estimate that their are well over a million viruses out there...

Out of those million little mal-ware programs out there, there are apparently 45 potential threats (mostly useless due to patches). When one of those does actually get onto a distro, THEN the user has to give it permission to do anything, especially anything serious like <sudo run virus>.

***[edit:]** I picked this up from the other current thread on Linux viruses in this sub-forum, I think you'll like it:*

[http://ubuntuforums.org/showpost.php?p=8424962&postcount=13](http://ubuntuforums.org/showpost.php?p=8424962&postcount=13)

---

### Post by rburkartjo on 2010-12-19
been using linux for years and never had a linux virus. i keep a virus scanner bitdefender because i use a few windows programs and i have caught a few viruses. mostly addware.

---

