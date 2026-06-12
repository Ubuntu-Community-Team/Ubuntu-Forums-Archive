---
title: "HOWTO: Setup slrn"
date: 2007-06-15
forum: Outdated Tutorials &amp; Tips
---

### Post by andrew.46 on 2007-06-15
============
**Introduction**
============

This 'Howto' page demonstrates how to setup the great console newsreader slrn under Ubuntu Linux and deals with the 'release' version slrn 0.9.9. Setting up slrn requires a little preparation as it deals with not just slrn but a few 'companion' programs as well.

But first some preparation work: 

====================
**Set a FQDN**
====================

For the best setup you should have an *unique* Fully Qualified Domain Name (FQDN) set to your system. Check this with the following command:
```
$ hostname --fqdn
```

If this is not set you will need to alter your /etc/hosts file to reflect your FQDN. The default Ubuntu /etc/hosts file tends to look something like this:

```
127.0.0.1       localhost
127.0.1.1       desktop
```

Alter this to something like:

```
127.0.0.1       localhost
127.0.1.1       desktop.your.domain     desktop
```

*(Thanks to PJR for the information above)*. For your own, unique FQDN you have 3 good choices:

[LIST=1]
[*]If you own your own Domain Name use this in conjunction with a subdomain and the hostname of your computer.
[*]Use a service such as [dyndns.org]("http://www.dyndns.com/services/dns/dyndns/") which will give you a domain name for free.
[*]Use the news service [individual.net]("http://www.individual.net/faq.php#4.4") which will give you a free FQDN.
[/LIST]

A word of warning: an incorrect or false FQDN might expose you to merciless flaming so spend a little time getting this set correctly. Next we set up the text editor vim and the then Mail Transport Agent (MTA) msmtp:

========================
**Getting Acquainted with vim**
========================

slrn does not come with a built-in editor and the best editor to use with slrn is vim, although many will argue this point. A version of vim comes as part of the default Ubuntu installation but before launching into this reasonably complex program I would advise you to run through vim's tutorial program which can be launched with the following command:

```
$ vimtutor
```

A skill with vim is not the mandatory part of a Linux experience that it once was but you will find skills in vim will be very useful to you in other areas. Next to set up our MTA:

=================
**Setting up an MTA**
=================

To reply by email to a news posting sendmail or a substitute is required and in this 'Howto' msmtp will be used. To reply by email rather than post directly to the newsgroup is not *often* appropriate but it has its uses. The following command downloads and installs msmtp + a certs pack:

```
$ sudo apt-get install msmtp ca-certificates
```

This very simple program needs a single configuration file to be created, a logfile to be created, an addition made to the ~/.slrnrc file, and then it will happily send email from within slrn:

```
$ touch $HOME/.msmtprc
$ touch $HOME/.msmtp.log
$ chmod 0600 $HOME/.msmtprc
```

Below is the required configuration for a Gmail server:

```
account default              
host smtp.gmail.com          
port 587                     
from **[COLOR="Red"]full.gmail.address@gmail.com[/COLOR]**   
tls on                       
tls_starttls on              
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on                     
user **[COLOR="Red"]gmail.username [/COLOR]**       
password **[COLOR="Red"]mypassword [/COLOR]**       
logfile ~/.msmtp.log
```

With both vim and msmtp setup it is time to move on to slrn itself:

==========================
**Download slrn**
==========================

Times have changed with the new release of slrn and finally users of Jaunty Jackalope can get a perfectly usable version direct from the Ubuntu repository:

```
$ sudo apt-get install slrn
```

Previous versions of Ubuntu are not so fortunate but Thomas Wiegner has been good enough to make Ubuntu packages of the latest slrn available from his site: [slrn patches and ubuntu repository/packages]("http://www.foory.de/thw/slrn/"). These packages can either be downloaded and installed directly from his site or can be accessed by adding either of the following lines to /etc/apt/sources.list:

**Gutsy Gibbon:**
```
 deb http://www.foory.de/thw/slrn/ gutsy/ 
```

**Hardy Heron:**
```
 deb http://www.foory.de/thw/slrn/ hardy/ 
```

**Intrepid Ibex:**
```
 deb http://www.foory.de/thw/slrn/ intrepid/ 
```

Use of the repositories should guarantee that slrn will be kept up to date via the Ubuntu package management system.

But now to setup the file ~/.slrnrc:

===============
**Setup ~/.slrnrc**
===============

slrn requires the creation of a personal configuration file: ~/.slrnrc. The following commands transfer a sample file from the slrn website to its correct location and opens it for editing:

```
$ wget http://slrn.sourceforge.net/downloads/slrn.rc -O $HOME/.slrnrc
$ vim $HOME/.slrnrc
```

May I suggest a very few basic settings to make your early days a little easier?

===========================
**Some Suggested ~./slrnrc Settings**
===========================

There are 11 sections, not all of which need to be altered simply to get slrn successfully online. You can see that this file uses the figure % to create a comment, simply remove the % to allow slrn to see and perform the command.

**Section 1:** Tell slrn about your identity. These following fields will usually need to be un-commented and set:

```
% Basic identification information which creates:
% From: Skywalker <luke@deathstar.invalid>
set username "luke"
set hostname "deathstar.invalid"
set realname "Skywalker"

% Also create a real email address that is less likely
% to be spammed, use gmail anyway to be sure:
set replyto  "luke.skywalker@gmail.com"

% Set the location of your signature:
set signature ".signature"
```

Don't forget to create the signature as follows:

```
$ vim ~/.signature
```

Be prepared observe a little netiquette with your signature file or you will meet some serious flame action. You do not have to add the usual signature delineator "-- " as slrn will do this for you automatically.

**Section 3**: Which external programs do you want to use? It is in this section that we will set vim as the default editor with the following line:

```
% Sets vim to edit with 72 character width.
set editor_command "vim '+set tw=72' +%d '%s'
```

This also sets the messages to be 72 characters wide which will save you from the wrath of other newsgroup readers. While you are here you may as well set Firefox as your default browser:

```
% Sets Firefox as default browser.
set Xbrowser "firefox '%s' &"
```

If you are keen to really come to grips with the console you could download the w3m browser and set it in your ~/.slrnrc file as well. Don't forget that you can call up URLs from within your news messages by typing in "U".

Next for the appropriate lines to tell slrn to use our MTA msmtp:

```
% Sets msmtp rather than sendmail.
set sendmail_command "/usr/bin/msmtp -t" 
```

So now you can forward messages to outside addresses by typing in "F" and reply to the given email addresses of newsgroup posters by typing "r". Don't forget to observe a little netiquette: it is almost always better to reply to the group rather than email the poster directly.

**Section 8:** Some preferences for the article pager. Since you have gone to some trouble to set up a decent news reader it is nice to see newsreader other people are using. Un-comment the following line and add in User-Agent:

```
% Sets the default headers you see above messages.
visible_headers "From:,Subject:,Newsgroups:,Followup-To:,Reply-To:,User-Agent:"
```

Remember when you you are reading messages you can toggle full headers and the shorter listing by pressing a lower case "t". For the sake of completion you should add X-Newsreader, X-Mailer and X-Posting-Agent as well as User-Agent.

**Section 9:** Display / color settings. Don't alter these settings yet until you have had a look at the default slrn colours but come back later and alter the colours in the section marked:

```
% These settings are used for color terminals:
``` 

There will be 2 colours set for most elements, the first is foreground the second is background. You can add a third option to the right of these values: bold, blink, underline and reverse. Experiment a little. You can also ask for "default" which will use the default settings of your Terminal program. A *basic* guide for these colors that can be placed in your ./slrnrc file for easy reference is:

```
%--- normal --------- bold ---------

%  0 black         8 gray 
%  1 red           9 brightred 
%  2 green         10 brightgreen 
%  3 brown         11 yellow 
%  4 blue          12 brightblue 
%  5 magenta       13 brightmagenta 
%  6 cyan          14 brightcyan 
%  7 lightgray     15 white
```

This completes the basic setup of your ~/.slrnrc file but I am sure you will be back to make many, many changes. If you are interested there are a couple of extra settings at the base of this page. The next task is to setup the news server in your computer's environment variables:

==============================
**Setting the NNTP Environment Variable**
==============================

slrn needs to know where your news server is. To do this you will need to set set the environment variable "NNTPSERVER" to the hostname of your preferred newsserver. Open the file ~/.bashrc as follows:

```
$ vim ~/.bashrc
```

and add the following lines, substituting 'your news server' with the actual address of your news server, leaving the apostrophes in place:

```
# Sets the News Server Environment as required by slrn
NNTPSERVER='my.news.server' && export NNTPSERVER
```

A few more steps and then slrn can be run for the first time:

==================
**Running the program**
==================

slrn needs to download a list of newsgroups from your news server, setup the file ~/.jnewsrc and optionally download a list of newsgroup descriptions. Open a Terminal window and type the following:

```
$ slrn --create
$ slrn -d
```

Congratulate yourself a little and type the next simple command into a Terminal window: slrn and yes, you have successfully installed slrn. The program has already subscribed you to a few newsgroups, navigate these by using the arrow keys and enter each group with the space bar. If and when you get stuck in the early stages press the "?" key and a list of basic commands will be revealed. Can I suggest a little time on alt.test before venturing on to other groups?

================
**And in conclusion**
===============

Be prepared for a steep learning curve but when you have mastered the basics of the program I predict you will never return to a GUI newsreader. If you get tangled up a little: close the program down, have a cup of tea, and read the [slrn manual online]("http://slrn.sourceforge.net/documentation.html"). Perhaps you would like to use the NNTP proxy server Leafnode-2 with slrn as I do? Try another guide I have written on these forums: [[Howto] Setup and use Leafnode-2 with the newsreader slrn]("http://ubuntuforums.org/showthread.php?t=676837").

April 13th, 2009
Andrew Strong

---

### Post by ctyc on 2007-12-13
Thanks Andrew, the default slrn found in the repositories for Ubuntu 7.10 works just fine with your walkthrough.

---

### Post by andrew.46 on 2007-12-13
Hi,

 Thanks for your message:

> **ctyc said:**
> Thanks Andrew, the default slrn found in the repositories for Ubuntu 7.10 works just fine with your walkthrough.

Good to see another slrn user, I hope to see you on news.software.readers! Perhaps at some stage you might be interested in investigating the newer versions that have come out. Thomas Wiegner has created a deb package suitable for Gutsy at:

[http://www.foory.de/thw/slrn/](http://www.foory.de/thw/slrn/)

 All the very best,

   Andrew

---

### Post by andrew.46 on 2007-12-20
Hi,

 Although this page has not been hugely popular I have rewritten it and added information to allow access the the svn repository. Hopefully I can add information soon to download the release version slrn 0.9.9.

 I no longer use Ubuntu Linux but I have decided to maintain *this* walkthrough because Ubuntu was so good to me and because I would like to continue to raise the slrn flag wherever I can :-)

 All the best,

    Andrew Strong

---

### Post by Moog on 2008-01-07
> **andrew.46 said:**
> Hi,

 Although this page has not been hugely popular I have rewritten it and added information to allow access the the svn repository. Hopefully I can add information soon to download the release version slrn 0.9.9.

 I no longer use Ubuntu Linux but I have decided to maintain *this* walkthrough because Ubuntu was so good to me and because I would like to continue to raise the slrn flag wherever I can :-)

 All the best,

    Andrew Strong

Yo. Andrew.

One thing that would help would be a  leafnode, slrnpull "HOWTO:"

The reason I ask is I'm struggling like anything getting either going. ;-). Any help appreciated and I think this would be the relevant place to post it.

Keep up the good work BTW. 

Take Care
Moog.

---

### Post by andrew.46 on 2008-01-07
Hi Moog!

> **Moog said:**
> Yo. Andrew.

One thing that would help would be a  leafnode, slrnpull "HOWTO:"The reason I ask is I'm struggling like anything getting either going. ;-). Any help appreciated and I think this would be the relevant place to post it.
Keep up the good work BTW. 
Take Care
Moog.

Feels a bit odd seeing you here and not in a.o.l.u. :-) (unless of course there are 2 'Moogs'!). 

I still look after a couple of 'Howto's on this forum: this slrn one and an svn mplayer one but it has been a little while since I have been regularly using Ubuntu linux. So further development, such as leafnode or slrnpull may be a while coming on *this* particular page. I will admit that leafnode has crossed my mind a few times as I have seen discussion on it in various places. I saved a link for future reference that might help a little:

[http://homepage.ntlworld.com/garryknight/linux/leafnode.html](http://homepage.ntlworld.com/garryknight/linux/leafnode.html)

 All the very best,

     Andrew

PS Just thoroughly read through that Leafnode page. Looks like a long afternoon's work to get that all setup :-)

---

### Post by Moog on 2008-01-10
> **andrew.46 said:**
> Hi Moog!



Feels a bit odd seeing you here and not in a.o.l.u. :-) (unless of course there are 2 'Moogs'!). 

I still look after a couple of 'Howto's on this forum: this slrn one and an svn mplayer one but it has been a little while since I have been regularly using Ubuntu linux. So further development, such as leafnode or slrnpull may be a while coming on *this* particular page. I will admit that leafnode has crossed my mind a few times as I have seen discussion on it in various places. I saved a link for future reference that might help a little:

[http://homepage.ntlworld.com/garryknight/linux/leafnode.html](http://homepage.ntlworld.com/garryknight/linux/leafnode.html)

 All the very best,

     Andrew

PS Just thoroughly read through that Leafnode page. Looks like a long afternoon's work to get that all setup :-)

Andrew,

Yes. It's the very same one. And you're right. It's quite a strange experience conversing with you on here.

That page looks just like what I need. I'll plod through it on Sunday and use it has an excuse to get away from the kids.

Take care.
Moog

---

### Post by andrew.46 on 2008-01-20
Hi again Moog:

> **Moog said:**
>  That page looks just like what I need. I'll plod through it on Sunday and use it has an excuse to get away from the kids.

Actually I installed leafnode on my new Feisty partition and it looks like you can probably forget that long document if you install the repository version of leafnode. A nice script actually does all the settings for you: sets up the news server + hourly cron job etc Only extra is for individual.net you need to add username and password to /etc/news/leafnode/config and twiddle a few download settings. 

I have now also setup Leafnode 2 up on my Slackware 12 partition and I will admit to a little bit of hard going for a while. Server settings had to be done by hand, config file was untouched and crontabs for fetchnews and texpire needed to be manually added. Also settings for host.allow / deny + ~/.bashrc / NNTPhost setting by hand as well. Ubuntu makes it *very* easy in this case :-)

I suspect that I will need to pick up a few months of usage and experience with Leafnode before I dare to write a walkthrough with any degree of expertise.

   Andrew

---

### Post by Zack McCool on 2008-01-29
I've been looking, but obviously not very well:  Are there any good slrn scorefile tutorials available?

And thanks for the great directions.

---

### Post by andrew.46 on 2008-01-30
Hi Zack:

> **Zack McCool said:**
> I've been looking, but obviously not very well:  Are there any good slrn scorefile tutorials available?

And thanks for the great directions.

There definitely *should* be some slrn scorefile tutorials but slrn has never been the best documented software in the world :-) However I can suggest at least a starting point. This tutorial has a big brother at:

[http://www.andrews-corner.org/slrn.html](http://www.andrews-corner.org/slrn.html)

that has a small section entitled: 'Scoring in slrn' which should definitely get you started at least. There are links on this page to the 2 best source documents about scoring which I will repeat here:

[http://www.slrn.org/docs/score.txt](http://www.slrn.org/docs/score.txt)
[http://slrn.sourceforge.net/manual/slrn-FAQ-4.html](http://slrn.sourceforge.net/manual/slrn-FAQ-4.html)

Hope this gets you started until somebody eventually writes a more detailed page :-)

    Andrew

---

### Post by Zack McCool on 2008-01-30
Thanks Andrew.  That is perfect.  I am not looking to do too much, just filter out some of the more annoying garbage.

Any suggestions for the MI5 Persecution garbage that keeps coming up?  ;)

BTW:  I am "Joe" in a.o.l.u...

---

### Post by andrew.46 on 2008-01-30
Hi again Zack,

Or should I say 'Joe' now that your disguise has slipped :-) 

> **Zack McCool said:**
> Thanks Andrew.  That is perfect.  I am not looking to do too much, just filter out some of the more annoying garbage.
Any suggestions for the MI5 Persecution garbage that keeps coming up?  ;)
BTW:  I am "Joe" in a.o.l.u...

Of course the best filtering starts from the server end, which is where once again I spruik for individual.net which rarely lets the MI5 material through.

But for the scorefile I have only 2 very simple rules for MI5:

```
     Score:: =-9999
     Subject: MI5
     Subject: M.I.5.
```

This is part of a longish chain of filters, hence the '::' mark which means of course that *any* of the tests can be passed to gain the kill score of -9999. 

The first line gives a score of -9999 if  the word MI5 appears *anywhere* in the line.  You could make it a little safer by making it instead:

```
     Subject: ^MI5
```

which would score -9999 if MI5 appears at the *beginning* of the line. Or even more conservative:

```
Subject: ^MI5 Persecution$
```

would filter for *only* that phrase, with the $ sign signifying the end of the line and the ^ sign signifying the beginning.

The second rule uses the figure '.' to capture single characters between the letters MI5. Therefore if our spammer writes:

```
M*I*5* Persecution

```
in a deliberate attempt to evade filters this rule would catch this.

There has been a recent discussion about MI5 filtering on news.software.readers which may interest you. But the real answer is to get a news server that does most of the filtering for you.

 All the best,

    Andrew

---

### Post by Zack McCool on 2008-01-30
> **andrew.46 said:**
> Hi again Zack,

Or should I say 'Joe' now that your disguise has slipped :-) 

Not much of a disguise.  I had been reading a book where the killer was using this name when I signed up here...   ;)

> 
Of course the best filtering starts from the server end, which is where once again I spruik for individual.net which rarely lets the MI5 material through.

I use giganews, mostly because of their retention times and binaries...   Not great filtering, but I figure I can handle most of that myself...

> 
But for the scorefile I have only 2 very simple rules for MI5:

```
     Score:: =-9999
     Subject: MI5
     Subject: M.I.5.
```

This is part of a longish chain of filters, hence the '::' mark which means of course that *any* of the tests can be passed to gain the kill score of -9999. 

The first line gives a score of -9999 if  the word MI5 appears *anywhere* in the line.  You could make it a little safer by making it instead:

```
     Subject: ^MI5
```

which would score -9999 if MI5 appears at the *beginning* of the line. Or even more conservative:

```
Subject: ^MI5 Persecution$
```

would filter for *only* that phrase, with the $ sign signifying the end of the line and the ^ sign signifying the beginning.

The second rule uses the figure '.' to capture single characters between the letters MI5. Therefore if our spammer writes:

```
M*I*5* Persecution

```
in a deliberate attempt to evade filters this rule would catch this.

There has been a recent discussion about MI5 filtering on news.software.readers which may interest you. But the real answer is to get a news server that does most of the filtering for you.


I am going to add those, and I'll take a look at n.s.r when I get a chance...   Thanks again!

---

### Post by andrew.46 on 2009-03-31
Hi,

I have updated this guide substantially and with the arrival of newer versions in the Ubuntu repositories the compiling material has been removed. Hopefully this will make slrn a little more attractive to new users :-).

Any problems with the new material please drop me a line here.

Andrew

---

### Post by abhilashm86 on 2009-04-10
hi andrew, i tried setting up using slang news reader using this tutorial.......
i just registred with news.motzarella.org, then in file .slrnrc file i completed other process, but when i start slang news reader,
```

abhilash@abhi:~$ slrn -d
slrn 0.9.8.1pl1 [2005-02-17]

Reading startup file /etc/news/slrn.rc.
Reading startup file /home/abhilash/.slrnrc.slrn fatal error:
Unable to find a valid hostname for constructing your e-mail address.
You probably want to specify a hostname in your .slrnrc file.
Please see the "slrn reference manual" for full details.


```

---

### Post by abhilashm86 on 2009-04-10
```

abhilash@abhi:~$ slrn -d
slrn 0.9.8.1pl1 [2005-02-17]

Reading startup file /etc/news/slrn.rc.
Reading startup file /home/abhilash/.slrnrc.***Warning: Unable to find a unique fully-qualified host name.
            slrn will not generate any Message-IDs.
            Please note that the "hostname" setting does not affect this;
            see the "slrn reference manual" for details.

*** Warning: Score file /home/abhilash/News/Score does not exist
Using newsrc file /home/abhilash/.jnewsrc for server my.news.server.
Connecting to host my.news.server ...
Failed to resolve my.news.server

Run-Time Error
slrn fatal error:
Unable to initialize server.


```
what is exact error, i don't know why daemon going to my.news.server? how to correct this problem.

---

### Post by andrew.46 on 2009-04-10
Hi abhilashm,

Good to hear from you again :-). There are a couple of things to fix up here:

> **abhilashm86 said:**
> ```

abhilash@abhi:~$ slrn -d
slrn 0.9.8.1pl1 [2005-02-17]
```

This is a fairly ancient version of slrn and I would strongly advise that you update to at least the latest release version. If you are using Hardy Heron as your details indicate the easiest way is to add Thomas Wiegner's repository to your /etc/apt/sources.list as follows:

```
deb http://www.foory.de/thw/slrn/ hardy/
```

and then run:

```
sudo apt-get update && sudo apt-get upgrade
```

and this should get you the latest slrn. Thanks again to Thomas for this service that he provides out of the goodness of his heart.

> ```
Reading startup file /etc/news/slrn.rc.
Reading startup file /home/abhilash/.slrnrc.***Warning: Unable to find a unique fully-qualified host name.
            slrn will not generate any Message-IDs.
            Please note that the "hostname" setting does not affect this;
            see the "slrn reference manual" for details.
```

This means that you do not have correct settings in your /etc/hosts file and is a well known enough problem with Ubuntu to have a special entry in the slrn faqs:

2.2 How can I set my ``Message-ID:'' header?
[http://slrn.sourceforge.net/docs/slrn-FAQ-2.html#ss2.2](http://slrn.sourceforge.net/docs/slrn-FAQ-2.html#ss2.2)

which will tell you to alter your /etc/hosts file from something like:

```
        127.0.0.1       localhost
        127.0.1.1       desktop
```

to:

```
        127.0.0.1       localhost
        127.0.1.1       [COLOR="Red"]**desktop.your.domain     desktop**[/COLOR]
```

Taking care to substitute your own details for the settings I have placed in red. Be careful to make a backup of this file before making any alterations.For your own, unique FQDN you have 3 good choices:

[LIST=1]
[*]If you own your own Domain Name use this in conjunction with a subdomain and the hostname of your computer.
[*]Use a service such as [dyndns.org]("http://www.dyndns.com/services/dns/dyndns/") which will give you a domain name for free.
[*]Use the news service [individual.net]("http://www.individual.net/faq.php#4.4") which will give you a free FQDN.
[/LIST]

> ```
*** Warning: Score file /home/abhilash/News/Score does not exist
```

An easy one :-). You need to create this file manually, slrn will not create it or you.

> ```
Using newsrc file /home/abhilash/.jnewsrc for server my.news.server.
Connecting to host my.news.server ...
Failed to resolve my.news.server

Run-Time Error
slrn fatal error:
Unable to initialize server.

```


You need to put your default NNTP server in $HOME/.bashrc as described in the guide but you need to substitute your *own* values for 'my.news.server'.

I trust this is enough to get you on your way? slrn can be difficult to get going but the investment of time and learning is well worthwhile. Hope to see you on alt.os.linux.ubuntu soon :-).

Andrew

---

### Post by andrew.46 on 2009-04-15
I have added Thomas's Intrepid repository to the guide. Thanks again Thomas for making this huge contribution!

Andrew

---

