---
title: "Ubuntu-PH Website Hosting"
date: 2009-03-24
forum: Philippine Team
---

### Post by daxumaming on 2009-03-24
Guys,

I'm trying to resurrect our website so we can make our presence known,
provide updates, and establish a point of collaboration. Every
plan/projects we have is dependent on having a website since I don't
believe Ubuntu's wiki would suffice.

I would need your opinion/suggestion as to where it'll be hosted. We
have 2 options here:

Option 1: Canonical Server
Pros:
1) Application updates handled by Canonical Sysadmins
2) Less Downtime / More Reliable
3) Backed by more experienced Sysadmins
4) Stricter QA and Testing

Cons:
1) Very few available applications (Drupal, Moinmoin, Planet, WordPress)
2) Modules, Themes, and other Web Applications has to go through
Testing, QA, and Security Checks which translates to "it'll take a while
before we can approve it."
3) I am still unsure as to how it'll be accessed and managed by Web
Masters. Will we get SSH access? Or will we be limited to SFTP.

Option 2: External Hosting
Pros:
1) We get to choose what web apps, themes, and plugins gets installed.
2) We get to choose when and what apps we upgrade/update

Cons:
1) Shared Hosting's prone to abuse
2) We only get FTP access
3) New account for every domain/sub-domain
4) Reliable server's not cheap
5) No access to shell, backups done via a web apps.

I'm currently eyeing 110mb.com for external hosting since they offer
cheaper rates (one-time payment / lifetime membership). But if you know
someone who'll gladly host our website for a minimum fee, please don't
hesitate to reply.

Thanks

[https://lists.ubuntu.com/archives/ubuntu-ph/2009-March/001753.html](https://lists.ubuntu.com/archives/ubuntu-ph/2009-March/001753.html)

---

### Post by loell on 2009-03-24
I'm all for external web hosting, primarily because we can have more freedom on what we can implement.

I'm proposing though, that we use [Google App Engine]("http://code.google.com/appengine/docs/whatisgoogleappengine.html")

the free quota of 5 Million page views per month and 500 MB of storage on one web app alone will be sufficient for the loco use for quite some time. (couple of years maybe? depending on the loco's growth.)

And should we need more storage and bandwidth it's also relatively cheap. External attacks and abuse is virtually Null, becase.. this is "Google's" :D
Among other things, there is collaboration , basic versioning , and the Dashboard system monitoring.

---

### Post by ysNoi on 2009-03-24
My suggestions is on [PHPOh Hosting](http://php0h.com//component/option,com_wrapper/Itemid,27/) and install something like SMF and Tportal on it.

HTH.. :guitar::guitar:

---

### Post by raxso on 2009-03-24
Count me in for external web hosting... but do we have funds???

---

### Post by daxumaming on 2009-03-25
Web-App Engine and PHP0h are both enticing, however, it's the monthly fees that's turning me off. It's the lack of funds that's preventing us from going external. Please consider that Canonical won't cover for us, it has to come from our own pockets.

---

### Post by ysNoi on 2009-03-25
Just want to ask if we can use a free hosting and domain here..?

---

### Post by loell on 2009-03-25
Yeah, that's why i'm suggesting app engine since its **free** and No monthly fees. and because it is running on google's infrastracture rarely would one ever see a downtime, that is, if ever. ;)

I highly doubt that we need more than GAE's free qouta, 5 million pageviews per month and a 500 MB storage on a single web app, and each developer is given 10 web app spaces, yep, entirely free. 

so imagine this, we could separate the wiki web app from the main site, say wiki.ubuntu-ph.org  and that would sit on another free qouta, not that its necessary given the loco's size and growth rate. :)

---

### Post by daxumaming on 2009-03-25
> **loell said:**
> Yeah, that's why i'm suggesting app engine since its **free** and No monthly fees. 

Re-reading the link...

Update:
loell, I'm quite concerned about this: "Although Python is currently the only language supported by Google App Engine, we look forward to supporting more languages in the future."

Although I'm convinced - we do need PHP since we'll be running Drupal and Planet. And there's no mention of Database.

---

### Post by daxumaming on 2009-03-25
> **ysNoi said:**
> Just want to ask if we can use a free hosting and domain here..?
The domain is free - being paid by Canonical.
The external hosting's preferably free, but we do get what we paid for and I will not stand for substandard services - neither will anyone else in this forum.

---

### Post by jsgotangco on 2009-03-25
GAE utilizes Big Table. I could probably work on something with my company for Drupal but we provide a completely different service that is not common with typical hosting and there's no console access and I'm sure we can't run PlanetPlanet.

Another thing probably that can be done is get a hosting plan and put ads on it but that could be a double edged sword.

---

### Post by loell on 2009-03-25
> **daxumaming said:**
> Re-reading the link...
Although I'm convinced - we do need PHP since we'll be running Drupal and Planet. And there's no mention of Database.

ah yes, its python and as jerome said it utilises big table for the data store.

Yup, if we ever go GAE, we will need to code it in python on a GAE framework or in Django 0.96,  perhaps we could write our own aggregator in python, for our planet?

---

### Post by jsgotangco on 2009-03-25
question is who will code that :) I'm familiar with Django but just have no time to do that. I'm pretty sure the same thing with others so an off the shelf CMS like Drupal is more compelling.

---

### Post by loell on 2009-03-25
> **jsgotangco said:**
> question is who will code that :) I'm familiar with Django but just have no time to do that. I'm pretty sure the same thing with others so an off the shelf CMS like Drupal is more compelling.

heheh, yeah that THE question :), although maybe we could run [feedjack]("http://www.feedjack.org/") and hone it on GAE. I'm not just sure if it can, since its a native django app. 

anyway, if there other web hosting that we can run drupal on, then that's fine by me.

---

### Post by loell on 2009-03-25
I know I keep pushing GAE as our host, that I think i'm sounding like a google reseller. :popcorn:

I'm just going to enumerate the potential projects that we can use, should we go app engine.

1. for cms like management we could use [bloog]("http://billkatz-test2.appspot.com/")  (it has a **drupal** uploader)

2. for the wiki we can use [MobSmarts]("http://mobsmarts.appspot.com/"), Code: [http://code.google.com/p/mobsmarts/]("http://code.google.com/p/mobsmarts/")

3. for the aggregator:  [http://www.feedjack.org/]("http://www.feedjack.org/") (untested on GAE)

I'm just toying with the idea that maybe we could put these apps, and have them put on a subdomain (ie wiki.ubuntu-ph.org , planet.ubuntu-ph.org  ..) 

I should note that i don't have any experience in using these projecs, and so far as GAE, i've only made a minimal web app, the one in my sig.

---

### Post by daxumaming on 2009-03-25
> **jsgotangco said:**
> Another thing probably that can be done is get a hosting plan and put ads on it but that could be a double edged sword.

I agree

> **jsgotangco said:**
> question is who will code that :) I'm familiar with Django but just have no time to do that.

Although this is an opportunity for me to delve deeper into Python and Django, I'm afraid I don't have the time as well.

> **loell said:**
> I know I keep pushing GAE as our host, that I think i'm sounding like a google reseller. :popcorn:

No, not at all.

I've googled around a bit and found that there are distinct advantages on going GAE, and I'm all for it. Besides, part of my plan is to integrate Launchpad with our website to automate translations and even track bugs assigned to our team, and the Launchpad API requires us to interface with Python. 

However, I'm more keen on using a PHP/MySQL host for the simple reason that the [script]("https://edge.launchpad.net/~ubuntu-drupal"), [themes]("https://edge.launchpad.net/ubuntu-drupal-theme"), and [resources]("https://wiki.ubuntu.com/LoCoCreatingWebsite") already exists. I'd also like to note that available modules are abundant.

---

### Post by wersdaluv on 2009-03-25
Good idea.

However, what content do you want to see? Yes, it's feasible to put this thing up but what would it be for? 

I'm thinking Ubuntu Philippine Team news. What else do we put there? How useful would it be? Are there enough benefits to justify (maybe) spending for this, coding stuff, and maintaining the site?

Whatchuthink? :)

---

### Post by daxumaming on 2009-03-25
Are we not looking at this the wrong way? Perhaps we should also consider the first option - have Canonical host our site. The list of approved applications may not be much (still looking for the link) but I still believe we can make do.

Will send a follow-up email to RT.

Update: [https://lists.ubuntu.com/archives/ubuntu-ph/2009-March/001757.html](https://lists.ubuntu.com/archives/ubuntu-ph/2009-March/001757.html)

---

### Post by jsgotangco on 2009-03-25
It's safer to run it on Canonical servers even if its just in a jail with limited access. We just need to run 2 apps anyway. No need for complication.

---

### Post by jsgotangco on 2009-03-25
> **loell said:**
> I know I keep pushing GAE as our host, that I think i'm sounding like a google reseller. :popcorn:

I'm just going to enumerate the potential projects that we can use, should we go app engine.

1. for cms like management we could use [bloog]("http://billkatz-test2.appspot.com/")  (it has a **drupal** uploader)

2. for the wiki we can use [MobSmarts]("http://mobsmarts.appspot.com/"), Code: [http://code.google.com/p/mobsmarts/]("http://code.google.com/p/mobsmarts/")

3. for the aggregator:  [http://www.feedjack.org/]("http://www.feedjack.org/") (untested on GAE)

I'm just toying with the idea that maybe we could put these apps, and have them put on a subdomain (ie wiki.ubuntu-ph.org , planet.ubuntu-ph.org  ..) 

I should note that i don't have any experience in using these projecs, and so far as GAE, i've only made a minimal web app, the one in my sig.

Those are fine and dandy but in the end it boils down to who can manage it on the long term. The thing with such projects, its exciting at the start, and there's a lot of talk, but once it is implemented, keeping momentum is another. The lesser admin task you undertake, the more focus you provide in content.

I'm not saying its a wrong thing to experiment something new. It's just that having a sustainable community is already a work by itself. Adding more work with infrastructure without clear cut goals and plans is asking for trouble.

---

### Post by daxumaming on 2009-03-25
So I guess we'll be pushing through with Canonical Hosting.... Unless there's any objections.

---

### Post by business.geek on 2009-03-25
Depending on the requirements. I'm willing to allocate my hosting for the ubuntu-ph for free. Since my hosting provider was generous enough to provide unlimited bandwidth, i'd like to volunteer.

let me know how this sounds.

---

### Post by business.geek on 2009-03-25
or we can also go get Google Apps for domains. The Google Sites service of google apps allows you to use your own domain name. I've been testing it for one of my subdomains.

[http://wiki.businessgeeks.org](http://wiki.businessgeeks.org)

This gives the community a chance to hve their own ubuntu-ph.org email address, calender for scheduels, messenging service etc.

---

### Post by loell on 2009-03-25
> **daxumaming said:**
> So I guess we'll be pushing through with Canonical Hosting.... Unless there's any objections.

none. :)

---

### Post by jsgotangco on 2009-03-25
> **business.geek said:**
> or we can also go get Google Apps for domains. The Google Sites service of google apps allows you to use your own domain name. I've been testing it for one of my subdomains.

[http://wiki.businessgeeks.org](http://wiki.businessgeeks.org)

This gives the community a chance to hve their own ubuntu-ph.org email address, calender for scheduels, messenging service etc.

I use it to all my domains as well but the thing is, Ubuntu provides consistent templates and stuff and it would be a shame not to use that infrastructure. Emails would be useful for Google Apps for domains but distribution is a tricky thing.

---

### Post by wersdaluv on 2009-03-26
Canonical, then. :)

---

### Post by Laibcoms on 2009-03-27
Canonical.  Go the easiest and less time consuming route since we're still not that active and solid in terms of supporting the LoCo.

Once we get a dedicated team to handle the website and backend (virtually at least, since canonical will do it all), as well as funds, then we can reconsider self-hosting.  ^_^

Besides, I think our main objective is to further promote and solidify Ubuntu in the Philippines.  Most of us probably have our own blogs and sites.

Unless there are other "immediate" plans that will require self-hosting?  Definitely not downloading of anything, we won't survive in a shared hosting for those ^^.

---

### Post by daxumaming on 2009-05-01
Request is at [https://rt.ubuntu.com/Ticket/Display.html?id=4530](https://rt.ubuntu.com/Ticket/Display.html?id=4530)

--

The request to reinstate [http://ubuntu-ph.org/](http://ubuntu-ph.org/) is already on the Ubuntu Request Tracker as Ticket [4530]("https://rt.ubuntu.com/Ticket/Display.html?id=4530"). You can use ubuntu | ubuntu as the username and password to monitor the progress.

Sun Apr 26 16:13:28 2009 jpds - Merged into ticket #4530
Sun Apr 26 16:13:28 2009 jpds - Ticket 5391: Merged into ticket #4530
Wed Apr 01 15:31:49 2009 nick - Ticket 5391: Queue changed from to LoCo
Wed Apr 01 15:07:12 2009 nick - Merged into ticket #4530
Wed Apr 01 15:07:12 2009 nick - Ticket 5574: Merged into ticket #4530
Wed Mar 25 14:15:45 2009 [email]knightlust@ubuntu.com[/email] - Ticket 5574: Ticket created ([follow-up email]("https://lists.ubuntu.com/archives/ubuntu-ph/2009-March/001757.html"))

---

### Post by kiminaiseah on 2009-05-02
dax,

i do provide hosting with full privileges access for free (XEN-VPS Many Cores upto 12) or (Virtualbox 1 Core Only), we can use afraid.org dns server and point with my dns server, 


> **daxumaming said:**
> Guys,

I'm trying to resurrect our website so we can make our presence known,
provide updates, and establish a point of collaboration. Every
plan/projects we have is dependent on having a website since I don't
believe Ubuntu's wiki would suffice.

I would need your opinion/suggestion as to where it'll be hosted. We
have 2 options here:

Option 1: Canonical Server
Pros:
1) Application updates handled by Canonical Sysadmins
2) Less Downtime / More Reliable
3) Backed by more experienced Sysadmins
4) Stricter QA and Testing

Cons:
1) Very few available applications (Drupal, Moinmoin, Planet, WordPress)
2) Modules, Themes, and other Web Applications has to go through
Testing, QA, and Security Checks which translates to "it'll take a while
before we can approve it."
3) I am still unsure as to how it'll be accessed and managed by Web
Masters. Will we get SSH access? Or will we be limited to SFTP.

Option 2: External Hosting
Pros:
[B]1) We get to choose what web apps, themes, and plugins gets installed.
2) We get to choose when and what apps we upgrade/update[/B]

Cons:
1) Shared Hosting's prone to abuse
2) We only get FTP access
3) New account for every domain/sub-domain
4) Reliable server's not cheap
5) No access to shell, backups done via a web apps.

I'm currently eyeing 110mb.com for external hosting since they offer
cheaper rates (one-time payment / lifetime membership). But if you know
someone who'll gladly host our website for a minimum fee, please don't
hesitate to reply.

Thanks

[https://lists.ubuntu.com/archives/ubuntu-ph/2009-March/001753.html](https://lists.ubuntu.com/archives/ubuntu-ph/2009-March/001753.html)

---

### Post by daxumaming on 2009-05-03
> **kiminaiseah said:**
> i do provide hosting with full privileges access for free

Hi kiminaiseah,

I would just like to clarify... **for free?**

If so, would there be any kind of advertisements on our site?

If no, I'll contact you via email. Shall I contact you via Yahoo, MSN, or AOL?

We're getting desperate here. Seems that Canonical has too much on their hands right now.

@business.geek

I'd like to know more.

---

### Post by kiminaiseah on 2009-05-05
100% Free
(Single Core Package/ Intel E5300 Host Server)
No Adds
Full OS Access Via SSH, VRDP
Request-able Maximum Diskspace
No MBQ(Monthly Bandwidth Quota)
2Mb/1Mb Link Speed
OOYC (OS Of Your Choice)
Uptime Depends On Meralco Service
Max Shared Ram 256M, (upto 16G Ram Just Donate DDR2-PC800 ECC or Non-ECC)
Request-able Image Backup or Recovery

(Multi Core Package(upto 12 Cores)/ AMD X2 7750 Host Server)
No Adds
Full OS Access Via SSH, VNC
Request-able Maximum Diskspace
No MBQ(Monthly Bandwidth Quota)
2Mb/1Mb Link Speed
Selectable OS (Debian[3,4,5,sid],Ubuntu[8.04,8.10,9.10],Fedora[7,8,9,10,11],CentOS[4,5],Redhat[4], or any Xen 3.x Kernel Compatible
Uptime Depends On Meralco Service
Max Shared Ram 256M, (upto 16G Ram Just Donate DDR2-PC800 ECC or Non-ECC)
Request-able Image Backup or Recovery


Everything Credits to Debian/GNU GPL as Part Of Sid/Testing Release

---

### Post by jsgotangco on 2009-05-05
> **kiminaiseah said:**
> 
Uptime Depends On Meralco Service


It's running inside Meralco premises in Ortigas?

---

### Post by daxumaming on 2009-05-06
> **jsgotangco said:**
> It's running inside Meralco premises in Ortigas?

LOL

@kiminaiseah

I'll contact you on your Yahoo email add and cc the mailing list.

---

### Post by kiminaiseah on 2009-05-08
> **daxumaming said:**
> LOL

@kiminaiseah

I'll contact you on your Yahoo email add and cc the mailing list.


@jsgotangco
= nasa bahay ang mga machines ko

@dax
= anytime, down here my contact
-mobile
sun=09239053251
smart=09184341220

-i.m.
yahoo=marlon.delfino@yahoo.com
msn=marlon.delfino@hotmail.com
gmail=februarius.marlon@gmail.com
skype= search "Deuce Gigolo" or search "februariusx"

-voip
h323=000000@februariusx.co.cc

---

### Post by jsgotangco on 2009-05-11
> **kiminaiseah said:**
> @jsgotangco
= nasa bahay ang mga machines ko


LOL sorry. I can be so dense sometimes....

---

