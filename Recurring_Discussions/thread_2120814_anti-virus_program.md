---
title: "anti-virus program"
date: 2013-02-27
forum: Recurring Discussions
---

### Post by Brutus Blutoski on 2013-02-27
when using Ubuntu as your only operationg system I read somewhere a while back that you didn't need an anti virus package like you do with windows.......I have to admit this doesn't make sense to me........
 
Do I need to get an anti-virus program and install it on my machine.......if not....why not.......
 
if I do need one, which one should I get....are there some free ones that are good packages to get (download)
 
probably should sign this post "thick as a brick" but learning

---

### Post by Frogs Hair on 2013-02-27
While Windows executable viruses won't run in Linux you can pass them to a windows machine via files. There are Linux viruses and root kits in the wild but alot fewer by comparison to Windows. Internet browsers share non virus vulnerabilities regardless of platform. See the stickies at the link.           [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

More about security: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by CharlesA on 2013-02-27
> **Frogs Hair said:**
> While Windows executable viruses won't run in Linux you can pass them to a windows machine via files. There are Linux viruses and root kits in the wild but alot fewer by comparison to Windows. Internet browsers share non virus vulnerabilities regardless of platform. See the stickies at the link.           [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

More about security: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

This pretty much covered it.

I just let Windows machines scan for Windows viruses.

---

### Post by MadmanRB on 2013-02-27
As mentioned an antivirus is not needed in linux, it is safe from such matters as it uses a different codebase then windows thus making windows viruses useless.

---

### Post by fdrake on 2013-02-27
you do not need an anitvirus, but you need to know what your are doing at a basic level at least.

---

### Post by Baldrick_NZ on 2013-02-27
> 
i just let windows machines scan for windows viruses.

+1

---

### Post by Lisiano on 2013-02-27
... As long as you don't try running a virus from Wine.
You don't need an antivirus if:
[LIST]
[*]You don't share files with Windows users (Or don't care about their safety)
[*]You don't run untrusted Windows executables with Wine
[/LIST]
You do need an antivirus if:
[LIST]
[*]You care about Windows user safety
[*]You run random Windows executables using Wine
[/LIST]
Truth be told, Linux antivirus that do exist (ClamAV, Kaspersky, Avast!, ESET, etc) check for Windows viruses, as such they are useless for almost every Linux user.

---

### Post by CharlesA on 2013-02-27
Nice catch with the wine thing, Lisiano.

I don't touch wine, so that's not a problem for me.

---

### Post by fdrake on 2013-02-27
> **Lisiano said:**
> ... As long as you don't try running a virus from Wine.
You don't need an antivirus if:
[LIST]
[*]You don't share files with Windows users (Or don't care about their safety)
[*]You don't run untrusted Windows executables with Wine
[/LIST]
You do need an antivirus if:
[LIST]
[*]You care about Windows user safety
[*]You run random Windows executables using Wine
[/LIST]
Truth be told, Linux antivirus that do exist (ClamAV, Kaspersky, Avast!, ESET, etc) check for Windows viruses, as such they are useless for almost every Linux user.

that's a good point but, if you install wine in ~/.wine you shoul not have serious problems. If instead you have compiled it into /root/.wine than you are playing with fire.
it all depends how you install/run a program, same thing goes for all apps. you could open an untrusted file with "sudo vim file " and that file would have #shell right the way.

---

### Post by Lisiano on 2013-02-27
Regardless where you keep your Wine prefix, it can still access your /home and / with whatever permissions your user has, so a Windows based virus designed to steal passwords, could scan every folder from Wine C: and land into C:\Users\Username which would translate to /home/Username, where it can get inside ~/.config/{chromium,Empathy,google-chrome,*}, ~/.{purple,mozilla,*} and other folders and if the virus is smart enough, notice that the folder structures are that of Chrome, Firefox, Empathy, Pidgin, * and grab the database files or plaintext passwords in plaintext files (Looking at you Pidgin).
Right... Basically don't install Wine. :D

---

### Post by CharlesA on 2013-02-27
Or if you do install Wine, confine it with AppArmour.

---

### Post by Sef on 2013-02-27
Also too avoid running flash and java.

---

### Post by Lisiano on 2013-02-27
Better yet, avoid using the GUI, might get a wine keylogger (I wonder if those work?), just sit in a VT. Only use cat and echo to manage documents, occasionally vi or nano if the documents are big. Use only wget and lynx for web browsing. Also run only in read-only mode. Also a good idea would be to just purge netbase so people can't hack into your box from the network. Maybe even encrypt the whole drive with a 4096-bit token and a 128 char password. Also keep the HDD in a safe, that is located in a bank vault which only opens for a few minutes once a year. Wait... Someone could write something in the BIOS rom, keep that in a separate vault that opens at a different time once every 2 years.

Heh. Right. Heavy sarcasm aside, just don't do stupid stuff and use common sense.

Also, it's quite interesting how security based questions grow into a discussion on these forums.

---

### Post by zrdc28 on 2013-02-27
clamav is a virus catcher for linux, you can probably get it from any repo. The better way to check the whole computer is to use a live cd with clamav and then you can check linux and windows with nothing mounted. rkhunter is a really good package for find rootkits.
  I use a live cd with clamav, when windows has a virus to bad to even boot, clamav can find and destroy it.

I never worry about anything when on linux, I open everything that I'm interested in and all email & have never had problem in 12 years of using many different distros.

---

### Post by audiomick on 2013-02-27
> **Lisiano said:**
> 
Heh. Right. Heavy sarcasm aside, just don't do stupid stuff and use common sense.

That is and has always been my policy, and I don't think I have ever had a virus, either on a Linux install (no surprise) or a Windows install. I have Avira on my Vista install at the moment, but my main protection is that I try and only go on the 'net with Linux.

---

### Post by Ms. Daisy on 2013-02-27
*sigh*

Anti-virus software will scan for windows (and maybe Mac) viruses, but none of them scan for linux malware. It's not that there cannot be linux malware, it's just that mass market malware for windows has a much greater return on investment for attackers.

The OP's instinct is correct that you need something for security, AV is just not the answer. As previously mentioned read the basic security wiki for actual effective security measures for a linux machine.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by 3rdalbum on 2013-02-28
> **Brutus Blutoski said:**
> when using Ubuntu as your only operationg system I read somewhere a while back that you didn't need an anti virus package like you do with windows.......I have to admit this doesn't make sense to me........

A computer virus isn't like a biological virus. It is not a physical thing, it is only a computer program created by a human.

Like all computer programs, it must be written for an operating system. Viruses are almost always written for Windows. If Linux can't run Windows programs, then neither will it run Windows viruses.

Linux is designed to be secure - it is a lot more difficult to write a Linux virus, and as there are fewer Linux desktop computers it's nearly impossible to actually have a Linux virus spread far.

---

### Post by siddharth007 on 2013-02-28
Try Clamav anti-virus package.It provides effective protection and the updates are available frequently.

```
apt-get install clamav
```

---

### Post by sleash78 on 2013-02-28
clamav

---

### Post by Paqman on 2013-02-28
> **siddharth007 said:**
> Try Clamav anti-virus package.It provides effective protection

I disagree. Clamav's performance is [mediocre at best](https://en.wikipedia.org/wiki/Clamav#Effectiveness). The best antivirus suites for Linux are Avast and Avira. So if you decide you really need AV for some reason, go for one of those.

---

### Post by cortman on 2013-02-28
My favorite answer to the anti-virus for GNU/Linux question comes from the Unix Koans of Master Foo:

> 
There was a novice who learned much at the Master's feet, but felt something to be missing. After meditating on his doubts for some time, he found the courage to approach Master Foo about his problem.
"Master Foo," he asked "why do Unix users not employ antivirus programs? And defragmentors? And malware cleaners?"
Master Foo smiled, and said "When your house is well constructed, there is no need to add pillars to keep the roof in place."
The novice replied "Would it not be better to use these things anyway, just to be certain?"
Master Foo reached for a nearby ball of string, and began wrapping it around the novice's feet.
"What are you doing?" the novice asked in surprise.
Master Foo replied simply: "Tying your shoes."
Upon hearing this, the novice was enlightened.

---

### Post by DuckHook on 2013-02-28
> **cortman said:**
> my favorite answer to the anti-virus for gnu/linux question comes from the unix koans of master foo:
Wonderful

---

### Post by Ms. Daisy on 2013-02-28
> **3rdalbum said:**
> A computer virus isn't like a biological virus. It is not a physical thing, it is only a computer program created by a human.

Like all computer programs, it must be written for an operating system. Viruses are almost always written for Windows. If Linux can't run Windows programs, then neither will it run Windows viruses. OK, I was with you on this part except that you're not including Java & Adobe exploits in there- those are platform agnostic.  I'm not with you at all on this part: > **3rdalbum said:**
> Linux is designed to be secure - it is a lot more difficult to write a Linux virus, and as there are fewer Linux desktop computers it's nearly impossible to actually have a Linux virus spread far. Nope.  It's not any more difficult. It's just way more profitable to write malware for Windows as they have the largest market share of PCs by far.

---

### Post by craig10x on 2013-02-28
Ah, but what you are forgetting is that most servers (including most of microsofts...is that not irony?) are on linux....which make them a huge target for malware writers...
While personal use of linux may still be relative small in the overall scheme of things, that is not true on the commercial side...

So, how come we aren't reading about the massive security exploits of linux servers?
Perhaps because Linux is so much more secure in the way it is designed (as compared to windows)...

---

### Post by ikt on 2013-02-28
> **Ms. Daisy said:**
> It's just way more profitable to write malware for Windows as they have the largest market share of PCs by far.

[http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/#myth1](http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/#myth1)

Android vs Iphone also supports this argument, as the iphone for a long time was more popular than android but doesn't have the malware problem android has.

Security through obscurity is no security at all.

---

### Post by CharlesA on 2013-02-28
Do you surf the web from a server?

Pretty much +1 to what ikt said.

---

### Post by Ms. Daisy on 2013-02-28
> **CharlesA said:**
> Do you surf the web from a server?
/me thinks it happens more than it should ;)

---

### Post by CharlesA on 2013-02-28
> **Ms. Daisy said:**
> /me thinks it happens more than it should ;)

That's probably right. I've been known to use lynx and curl at times. :p

---

### Post by Grinage on 2013-02-28
I've been running on various Linux builds for years and never been encountered any virus like activity that didn't have some other source, usually something I was doing, but that's beside the point. A poster on a different thread on this forum pointed out to me that he or she did not babysit windows users after it was mentioned that in a mixed computer environment which we all realistically are, such programs as clamAV and all it's various components and add ons was really to keep us from passing windows viruses around whether or not they affected our machines.  I'd always considered it polite behavior to make sure you weren't sending on something that could cause someone else grief, but the more I think about it, I'm starting to agree with that poster.  Perhaps I'm starting to get get tired of having to go out of my way to avoid the microsoft tax.

---

### Post by DuckHook on 2013-03-01
> **Grinage said:**
> I'd always considered it polite behavior to make sure you weren't sending on something that could cause someone else grief, but the more I think about it, I'm starting to agree with that poster.

The problem with antivirus on Linux is multifold:

1. It bogs down my Linux box with worthless bloatware that pointlessly increases complexity and saps performance.
2. It gores a straw man.
3. It diverts limited resources and attention from real security threats.
4. It perpetuates delusions of safety, especially among new users.
5. It co-opts Linux into acting as enablers for the bad habits and deficiencies of others.
6. It burdens me with someone else's shortcomings.

Any one of these is reason enough to avoid it. Their cumulative weight is overwhelming.

---

### Post by Soul-Sing on 2013-03-01
> 
1. It bogs down my Linux box with worthless bloatware that pointlessly increases complexity and saps performance.
2. It gores a straw man.
3. It diverts limited resources and attention from real security threats.
4. It perpetuates delusions of safety, especially among new users.
5. It co-opts Linux into acting as enablers for the bad habits and deficiencies of others.
6. It burdens me with someone else's shortcomings.

1) No, an ondemand antivirus scanner takes no resources. Nothing. A realtime/on acess will, don't use them. (There are some around)

3) Referring to a false security sentiment, as in Microsoft systems?

4) There are many linux users, using antivirus, because they are aware of risks of file sharing files/etc. between linux and windows machines.

5) Why is that?

---

### Post by DuckHook on 2013-03-01
> **Soul-Sing said:**
> 1) No, an ondemand antivirus scanner takes no resources. Nothing. A realtime/on acess will, don't use them. (There are some around)

3) Referring to a false security sentiment, as in Microsoft systems?

4) There are many linux users, using antivirus, because they are aware of risks of file sharing files/etc. between linux and windows machines.

5) Why is that?

1. ...except that we are told by many of those who use them, and certainly by antivirus vendors, that on-demand scanners are less effective (and, by implication, less safe) than memory resident autoscan types. And they have a point--*if* we accept the premise that they do any good in Linux--one of the key features of antivirus programs being their ability to be on constant alert versus the the human propensity to procrastinate or forget.

3. ...if I was making such a reference, it would have been #4, but I was not referring to any system but Linux. Numerous new users ask about antivirus on these forums and it is evident in the way they phrase their questions that they feel the installation of antivirus is their foremost (and for too many, their only) concern. Whether they inherit such attitudes from proprietary systems is a topic for another day. The fact is they approach antivirus that way, which is an attitude that all of the security stickies and primers on this very forum and other sites seek to change. Developers are not the only people who have limited attention and resources: users do to. And when these are directed at non-problems, the real problems don't get addressed.

4. ...then they should install it on the Windows side where it belongs. I operate mixed OSes. The Windows boxes have not only antivirus, but all the malware scanners that are unfortunately needed for Windows. The Linus boxes do not.

5. ...the prevalent attitude among users of proprietary OSes is that virii are an unavoidable consequence of computing in general and part of the natural computing landscape. It is, in fact, a form of normalizing the abnormal. Yet, in Linux, we have an OS that stands as a stark counterexample to that fallacy. If Linux must saddle itself with pointless bloatware for the sake of another's deficiencies, then what is this but further enabling of those deficiencies? If proprietary OSes have a virus problem, fix it. It is nothing less than enablement for Linux to participate in and thus sustain their deficiency industry.

Don't mean to get too mystical here, but the guiding principle behind all of the 'nixes, Linux included, is to do only that which is needful. This is what minimizes risk and keeps Linux out of most of the trouble that other OSes get themselves into. Do one thing, but do it well. Don't run what isn't needed. Minimal access, minimal privileges, minimal services. The application of this guiding principle turns out numerous good practices. Quite aside from the practical aspects already discussed, antivirus--at least to this user--offends this aesthetic.

---

### Post by maglinu on 2013-03-01
I seem to be in a very small minority here, but, amongst other security measures, I do run a real-time AV on my system (Comodo antivirus for Linux).

I'm not qualified to disagree with anything that has been said, but in my mind I do it because:

(i) It costs nothing. It auto-updates, so it is essentially fit and forget. The performance impact is clear on initial use of any application on my old machine, but hardly noticeable on subsequent use. On my new machine it is hardly noticeable at all.
(ii) I hope it offers some protection against cross-platform malware
(iii) I also hope that Comodo will eventually get around to including signatures for any new Linux malware that appears, such as this
[https://isc.sans.edu/diary/SSHD+rootkit+in+the+wild/15229](https://isc.sans.edu/diary/SSHD+rootkit+in+the+wild/15229)
I do my best to prompt them to.

I would say that I've never encountered any malware in Linux, but then nor did I in twelve years with Windows. I guess I'm just not an adventurous sort!

---

### Post by Soul-Sing on 2013-03-01
> (i) It costs nothing. It auto-updates, so it is essentially fit and forget. The performance impact is clear on initial use of any application on my old machine, but hardly noticeable on subsequent use. On my new machine it is hardly noticeable at all.
1) No costs, is an non argument, and makes no sense using whatever software
2) Auto-update, scary imho. :)
3) Fit and forget. No-way. Security in linux goes it bit further than this. Learn, be critical, and get fam. with apparmor/luks/(g)ufw/iptables. DuckHook had a point there.

---

### Post by maglinu on 2013-03-01
> **Soul-Sing said:**
> 1) No costs, is is non argument, and makes no sense using whatever software
2) Auto-update, scary imho. :)
3) Fit and forget. No-way. Security in linux goes it bit further than this. Learn, be critical, and get fam. with apparmor/luks/(g)ufw/iptables. DuckHook had a point there.

1. It is an argument if you can't afford it - but I agree it usually isn't a clincher. What I really had in mind was the avoidance of annual online financial dealings to renew - or even worse having to cancel attempted auto-renewal of products you want to ditch. I've had grief from several well known windows AV vendors in the past over this.

2. Only the virus database auto-updates, but again I agree, it can be scary. It's a trust issue. If you can't trust the people who provide your security software then it is bad. Should I trust Comodo? Then again, should I trust Canonical or Microsoft? 

At present I'm still too new to Linux to trust anything sensitive to it - or rather I don't trust my use of it that far yet.

3. Apparmor is in enforce mode on quite a few profiles - including Firefox. Ufw is blocking all ports inbound, and only a few essential ports are open outbound. I've not figured out if I can limit by application outbound. Encryption is currently limited to Home - I've pondered full disk encryption - maybe next time;)

---

### Post by DuckHook on 2013-03-01
Interesting article.

No one is chiding you for installing antivirus. Not me, anyway. I don't believe in crusades of any sort. The foregoing was as much academic exercise as best practice. If you simply must have antivirus installed to feel safe, then--and here's the signficant part--***provided you take all of the other precautions***, go ahead and use it. The antivirus won't do diddly-squat, it's the other precautions that really protect you; but humans have an appendix, so why not graft one onto Linux? If it offends my aesthetic, that's my problem.

That said, one of the favourite ploys of the antivirus industry is to take a threat and present it completely out of context. Or, if they do not actively do so, they make no effort to educate when people jump to the wrong conclusions. Why would they? Sells more software to let people do pointless things based on misdirected paranoia. Most people's reaction to this report is a perfect example. Please indulge me as I comment:

1. This trojan is no different than numerous other trojans, whether proof of concept or actual malware, that have been coded to infect Linux over the decades. Those of us who have an interest in security matters are fully aware of the nasties that are regularly discovered. Security gurus like Ms Daisy, Dangertux, bodhi.zazen and many others tirelessly remind us that it is almost trivial to write malicious code that will compromise a Linux system. In that very restricted sense, Linux is not inherently more hardened. It is certainly not infallible as some suggest. I am not remotely a coder or even a net-admin, but even I can put together a two-line script which, were you foolish enough to run it, would open your system up to being owned by anyone who could see your IP address. Lesson: reading about malicious code is critically incomplete and therefore almost meaningless in the absence of context.

2. Don't hold your breath waiting for this one to be added to antivirus signatures. Antivirus companies cannot just add any potential threat--the signature file would grow to infinity--they must restrict it to real threats. This example is not a real threat, witness ISC's own threat level of Green. BTW, SANS does phenomenal work. This report is totally valid: it's their job to capture threats, analyze and report on them. It's the misdirected response to this threat that is the problem.

3. The proper response, as it has been for years now, will likely turn out to be:
a. close the hole/s that will eventually be identified as the point/s of entry. For new users, this translates into: do not run obsolete versions and install all security updates.
b. If you don't use ssh, then don't install sshd (Minimal access, minimal privileges, minimal services).
c. Do not install stuff outside the repositories.
d. apparmor as much as you reasonably can.
e. Firewall both inbound and outbound.
f. Layer your security. Safety in depth.
g. Read your logs.
h. Backup your stuff.
i. If you've done everything reasonably possible, stop stressing about it and go have a beer.

Now, let's contrast that to what even my own limited experience has exposed attempting to advise new users on these forums:

1. "How do I login automatically?" Nerfs the login challenge, renders encryption pointless, imports the worst of Windows and reinforces truly gawd-awful habits.
2. "How do I operate permanently as administrator?" 'Nuff said.
3. "How do I permanently activate the root account?" Almost as bad as #2.
4. "I run version 9.10. Why can't I update?" They don't make parts for Model-Ts anymore either.
5. "I keep having to login twice. How do I delete the keyring?" Why not just track all of your passwords in a text file?
6. "How do I install this app/driver/service that I downloaded from I-don't-know-where?" Try this one from I-own-you.com
7. "How do I install all of silverlight/java/flash/active-x/mal-script onto my browser?" *sigh*
8. "Apparmor prevents me from doing something. How do I disable it?" The fastest way is by publishing your IP and password on the net.
9. "How do I get rid of permissions?" By using Windows.

These users will sometimes, without even pausing for breath, demand to know what anti-virus they must install. It would be a joke were it not so sad. And this is not even a complete sampling.

---

### Post by ajsalamanca78 on 2013-03-01
I tried installing AVG .deb from their site.  After 30 minutes and 5 reboots, it's gone.  Trying to be prudent and help the "blue pills", as I have to deal with them daily, but its just not worth it.  Ah well...

---

### Post by sunfromhere on 2013-03-02
> **DuckHook said:**
> 
These users will sometimes, without even pausing for breath, demand to know what anti-virus they must install. It would be a joke were it not so sad. And this is not even a complete sampling.

This. Just last month a couple of friends brought me their (Windows) computers for "fix" as they had a virus and had issues with the computers. What they did, I don't know, but one of the computers wouldn't even start Windows, the other would start but that was it. Needles to say, on all of the computers I found **no less than 3 (THREE)** av programs, some free, some commercial, not once run, not once updated. "But we have AV!"

Anyhow, I told them that because of what they did, they can't have Windows anymore (I won't allow it, because it'll just be a monthly reinstall fest) and installed Ubuntu on those machines. So far I haven't had any panic calls. :popcorn:

---

### Post by maglinu on 2013-03-02
> **DuckHook said:**
> Interesting article.

No one is chiding you for installing antivirus. Not me, anyway. I don't believe in crusades of any sort. The foregoing was as much academic exercise as best practice. If you simply must have antivirus installed to feel safe, then--and here's the signficant part--***provided you take all of the other precautions***, go ahead and use it. _The antivirus won't do diddly-squat, _it's the other precautions that really protect you; but humans have an appendix, so why not graft one onto Linux? If it offends my aesthetic, that's my problem.

.
I really hope the AV does do diddly-squat - just like my AV's in Windows have done diddly-squat for over the past 12 years (other than squawk for what turned out to be FPs a handful of times). 

Few would say I've been wrong to have Windows AV all that time though.

As you say, in all OS the other precautions are more important.

I appreciate these discussions - very helpful to the likes of me working up to an OS change decision, and more focussed than simply searching - probably frustrating for you guys who've been round the same issue before though.

So far I've concluded that if it's Linux then it's Ubuntu LTS.

I'm far to old to feel chided by the way. The mag of maglinu stood for middle aged guy. 

Trouble is that was a lot of years ago when I started using it on Windows forums. Not sure what it stands for now!

---

### Post by jackclarck on 2013-03-04
in this program anti virus may not be required, but it is good to have an anti virus in your computer, so you will keep protect from threats which may harm you machine.

---

### Post by Grinage on 2013-03-04
> **sunfromhere said:**
> This. Just last month a couple of friends brought me their (Windows) computers for "fix" as they had a virus and had issues with the computers. What they did, I don't know, but one of the computers wouldn't even start Windows, the other would start but that was it. Needles to say, on all of the computers I found **no less than 3 (THREE)** av programs, some free, some commercial, not once run, not once updated. "But we have AV!"


I can top that, one of my most time consuming jobs was a customer who said his computer was acting strange.  He brought it to me and I turned it on, it was a Windows XP box.  The first thing that caught my attention was that there were multiple AV programs installed.  There were AV programs I hadn't even heard of at the time installed, giving him a grand total of about ten.  Some of them very pricey, corporate versions that no EU would be expected to configure and run.  Within about three minutes of being up the box tried and failed to access the internet and send over a thousand emails.  The error messages were popping up so fast they were overloading the processing power of the machine.  Fortunately XP is about as insecure as anything you'd imagine as long as you're infront of it.  After bypassing the infected account and deleting all but one of the AV programs I found two things, that not one of them had ever been run, and that Windows Update, Windows Firewall, and several services had been disabled, and from the last run notes, had been disabled since the EU unboxed his machine.  The AV programs couldn't run because the Server service had been disabled.  After enabling it, the sole remaining AV found thousands of threats.  Ordinarily a box this badly comprimised would have been considered a lost cause but he had no backup of any type of any of his data.  Twelve hours of updates and cleaning later, the box was stable.  When I asked him why he'd turned off the services he had, he responded that he wanted his machine to run faster and he'd read somewhere that he could do that by disabling unnecessary services he didn't use. 

He is a die hard Microsoft Customer, and has now moved on to Windows 8 and it has already been extremely comprimised twice, once resulting in the total loss of everything on his system.  The best thing any user can do regardless of your OS of choice is find out what the best practices and standards are, and here's the important part *follow them. *There are lots of ways to comprimise any system, regardless of what security measures you've taken, there are also lots of ways to keep your system from being comprimised.  Congrats to the original poster for doing the right thing and asking the question.  It seems that these discussions don't happen enough.

---

### Post by CharlesA on 2013-03-04
Define "threats"

The only ones I know of that are cross platform are Java and Flash exploits and Ms. Daisy already covered those. Unless you are running Wine, you don't really have to worry about Windows viruses.

---

### Post by maglinu on 2013-03-04
> **CharlesA said:**
> Define "threats"

The only ones I know of that are cross platform are Java and Flash exploits and Ms. Daisy already covered those. Unless you are running Wine, you don't really have to worry about Windows viruses.

Thank you - that's helpful information. Much appreciated.

---

### Post by omgimdrunk on 2013-05-18
I am a bit surprised that this has not been brought up yet. I have a feeling I will get flamed but I will give you an serious honest answer. Yes Ubunutu should have an antivirus. There are exploits that will verify what operating system you are running and attempt to use a vulneradbility for that system to run a virus. A virus is simply software with a malisious intenet so there can be viri compiled for Linux aimed at a vulnerability in Ubuntu. the Blackhole kit is a great example. Ther are far fewer viri for mac and linux for the sole reason that there are few mac's and ubuntu systems compared to Windows in use. But Security through obscurity is not security.

AVG or clamAV are great and and have caught a handful of potentials on both my Ubuntu and Gentoo systems.
Yes you do not have to worry that much about Windows bots, trojans and root kit's but don't beleive that you are bullet proof, with more and more people using Ubuntu , there will be more and more people making malcode for it.

---

