---
title: "Opera supported?"
date: 2005-02-02
forum: Repositories &amp; Backports
---

### Post by brainstuff on 2005-02-02
Hi

As you can see from my post count I am a complete newb around here - I've been a linux user for about 12 hours now so please don't shout at me if you think this is in the wrong forum.

Anyway, I see in the Synaptic manager that there is an entry for Opera, but no associated downloads - does this mean that support is on its way but not implemented yet?

Call me freak, but I prefer the functionality of Opera to Firefox (page tabs in one window for instance). 

Does anyone know if any of the other Distro versions will work with Ubuntu? There are a lot of other distros supported but no Ubuntu yet.

Thanks in advance for any pointers
brain

Edit: in answer to my own question, pertinent thread here:
[opera forum clicky](http://my.opera.com/forums/showthread.php?threadid=80452&highlight=ubuntu)

---

### Post by Jad on 2005-02-02
go to [http://www.Opera.com/](http://www.Opera.com/)
download the debian package 
then 
sudo dpkg -i opera_7.54-20041210.5-shared-qt_en_sarge_i386.deb

I have opera installed on my system :-)

---

### Post by piedamaro on 2005-02-02
[QUOTE=Jad]go to [http://www.Opera.com/](http://www.Opera.com/)
download the debian package 
then 
sudo dpkg -i opera_7.54-20041210.5-shared-qt_en_sarge_i386.deb

I have opera installed on my system :-)[/QUOTE]
 Every browser on earth has tabbed browsing (ie a part of course...but is it reallty a browser? or a shell?)

The one single thing I find great in opera is the history cached in ram. Going back and forward through the pages is amazingly fast with no network traffic generated.
I spent hard times trying to guess why no oter browser has this feature.
For the rest opera is a ad-ware which IMHO sucks. (I've even made a skin for opera a coule of years ago). I've used it since vedsion 3.5, but now I use epiphany.

---

### Post by az on 2005-02-02
Opera is proprietary software.  

Icky.


No future there.

---

### Post by Jad on 2005-02-02
some people have to make livin :-)
actually I'm using opera only to emulater IE/text/lynx etc
its damn nice feature if you know what I mean.

---

### Post by brainstuff on 2005-02-02
I have much to learn in the way of Linux, this is evident.

I'll check out epiphany too, ta.

One other small thing that annoys me about Firefox is that backspace doesn't act as the back button*.  I can't see anywhere to rebind this shortcut :/

And about the cached history, yep it's a godsend - makes [www.kingdomofloathing.com](www.kingdomofloathing.com) usable!

*It's the little things in life though, isn't it?

Thanks for your helps and comments :)

---

### Post by CowPie on 2005-02-02
[QUOTE=brainstuff]Hi

As you can see from my post count I am a complete newb around here - I've been a linux user for about 12 hours now so please don't shout at me if you think this is in the wrong forum.

Anyway, I see in the Synaptic manager that there is an entry for Opera, but no associated downloads - does this mean that support is on its way but not implemented yet?

Call me freak, but I prefer the functionality of Opera to Firefox (page tabs in one window for instance). 

Does anyone know if any of the other Distro versions will work with Ubuntu? There are a lot of other distros supported but no Ubuntu yet.

Thanks in advance for any pointers
brain

Edit: in answer to my own question, pertinent thread here:
[opera forum clicky](http://my.opera.com/forums/showthread.php?threadid=80452&highlight=ubuntu)[/QUOTE]
 OH, I think you have to install something called libqtmt or whatever through apt-get...Opera won't install until you do (but it'll tell you the exact name when you try to )

BTW I love Opera too :)

---

### Post by brainstuff on 2005-02-02
argh, well I've got Opera running, but it's not installed *per se* - doesn't show up in Applications - in fact it's running from a sub folder on Desktop which is where I extracted it to. I had to change the permissions to Adm on the opera executable script, and then (because I'm a noob) I had trouble with the usersettings directory saying I had no permission to do anything with it - so I created a new opera directory, copied everything except usersettings folder, and created a new empty one in the new opera folder. That worked - in that Opera now remembers my settings, and has re-populated the new usersettings folder.  

What I can't do is create a Launcher / Shortcut for Opera, and I'm having to browse to its folder each time and find the executable icon. Any ideas anyone?

While I'm here, is there a setting anywhere that allows me to open directories in the parent directory instead of leaving windows all over my desktop?

Thanks
brain

---

### Post by paul cooke on 2005-02-05
[QUOTE=piedamaro]
 > For the rest opera is a ad-ware which IMHO sucks.

if you bought it, then you'd have a key which makes them go away...

I bought opera several years ago (version 5) and the key still works with the latest version

---

### Post by durianking on 2005-02-05
[QUOTE=brainstuff]

One other small thing that annoys me about Firefox is that backspace doesn't act as the back button*.  I can't see anywhere to rebind this shortcut :/

[/QUOTE]

I believe you are still using FireFox v0.93 which comes with the installation cd, please refer to the guide, in Repositories setion, at [http://ubuntuguide.org](http://ubuntuguide.org)  to update your /etc/apt/sources.list file and to a

apt-get update
apt-get upgrade
apt-get dist-upgrade (if necessary)

and you will be at FireFox v1.0 which you can use backspace to go back.

Cheers,

---

### Post by brainstuff on 2005-02-06
thanks for the tips peeps - this post is brought to you via the joy that is Opera!

I ended up trying so many things that one of them must have worked and I found the executable in my /bin/ folder! Freaky. I think I ended up downloading a generic static deb file, whatever one of them is :)

edit: oh and thanks for the pointer to ubuntuguide - it's a good reminder that I need to do a bit more RTing of the FM :)

cheers
brain

---

### Post by rosslaird on 2005-02-06
Opera is indeed an outstanding browser. And generally I find it to be faster than Firefox. I use both. The question of whether software is "free" or not is moot: none of the software we use is "free" -- it requires the investment of time and effort by programmers and requires (typically) that those programmers to be employed by someone who is in the business of making a return on the investment. The fact that we download the software for "free" does not make the arrangement better or more ethical or more pure. I support software that I pay for up front as well as that I pay for in other ways (by donation to the project, for example, or by way of tech support if I require it).

The free/not free dichotomy in the world of open source software is one hurdle preventing its acceptance at large. Free or open source software just uses a different business model, that's all. The programmers are not making the stuff out of charity.

---

### Post by Mike Douglas on 2005-02-06
I suggest you read [Ubuntu's philosophy](http://www.ubuntulinux.org/ubuntu/philosophy/document_view).

---

### Post by rosslaird on 2005-02-06
It's a good philosophy, and I agree with it. Especially this part:

> 
For Ubuntu, the "free" in "free software" is used primarily in reference to freedom and not to price...

Many people, in speaking of software, confuse the "free" of "freedom" with the "free" used in terms of expense (i.e. "free lunch"). So they claim, from an "open source philosophy," that software for which you have to pay money must be less ethical or more aggregious as a product (because people are angry with the MS monopoly) than software for which the price is spread across other levels of the market (programmers, entrepreneurial companies, etc.). The true open source philosophy speaks of "free" in terms of use, not price; but many critics of proprietary software (such as Opera) focus on price as their main objection. Price has nothing to do with software freedom.

Ubuntu intends to make money (among other things, no doubt) from this venture. This is a good thing. Within reason (think MS), the more money Ubuntu makes the better their product is likely to become.

> Canonical's business model is to provide technical support and professional services related to Ubuntu.

I recognize that terms such as "free" and "open source" have very specific meanings depending on who you talk to. But there is no doubt that most of the people in the "free software" business are trying to make a living from it. They are not doing it for free. This is good. It helps everyone. What bothers me is that some people seem to believe that all of this stuff should just be given away, as a kind of gift without reciprocity. This is not how economies work, nor should they.

Well, this has been a (somewhat) long rant to make a small point: I don't mind that Opera charges a bit for their browser. Paying fair money for a good service is proper. And I don't mind that Ubuntu wants to make a living from tech support and other types of consulting (government educational contracts being the holy grail of this type of thing), while offering "free" usage to those who want to take advantage of it. The fact that most of us are not paying their salaries is irrelevant: someone is paying their salaries, if only investors at the moment, and for them the endeavor is certainly not free. It's a big risk, in a community of legendarily stingy users.

---

### Post by landotter on 2005-02-08
[QUOTE=azz]Opera is proprietary software.  

Icky.


No future there.[/QUOTE]

LOL, plenty of future there. 

I consider Opera to be a maker of "boutique" software.

You don't need it since there are many other programs to do the job, but you might prefer their way of doing things and then it's time to pony up the cash.

It's not like they're a humongous company exploiting market domination. :P

Anyhoo, a point to ponder: do Photoshop or MSOffice have ad supported versions? ;)

Opera won me over with their "bork" edition.

[http://www.opera.com/pressreleases/en/2003/02/14/index.dml](http://www.opera.com/pressreleases/en/2003/02/14/index.dml)

The newest Linux beta is indeed wonderful. It would be great on a box where running seperate browser/mail/news/IRC would be overwhelming. Personally I prefer Evo, Pan, Xchat, etc--but I still fire up the new Opera from time to time, because as another poster mentioned, keeping the history in ram cache makes it unbelievably fast.

---

### Post by CowPie on 2005-02-11
[QUOTE=brainstuff]thanks for the tips peeps - this post is brought to you via the joy that is Opera!

I ended up trying so many things that one of them must have worked and I found the executable in my /bin/ folder! Freaky. I think I ended up downloading a generic static deb file, whatever one of them is :)

edit: oh and thanks for the pointer to ubuntuguide - it's a good reminder that I need to do a bit more RTing of the FM :)

cheers
brain[/QUOTE]

Hi,
Ubuntu is based on the unstable Debian (aka sid), so you can go to opera.com and choose the Debian qt-shared version for unstable.

---

### Post by cargo on 2005-03-28
[QUOTE=CowPie]Hi,
Ubuntu is based on the unstable Debian (aka sid), so you can go to opera.com and choose the Debian qt-shared version for unstable.[/QUOTE]
Thank a lot! That's exactly what I was looking for :)
It was not obvious for me...

---

### Post by mohuhau on 2005-10-13
Whats even better than downloading the sid version is to add opera as an apt repository!

Just add this to your /etc/apt/sources.list:
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) sid non-free

:)

---

### Post by CVDpr on 2005-10-14
Opera Yes, for me its more faster, no bulky-bloated, and the best thing the WANN.

FireFox dont ask if i want to save the password  in a lot of pages but Opera always activate the wang, cool.:razz:

---

### Post by CVDpr on 2005-10-14
Opera Yes, for me its more faster, no bulky-bloated, and the best thing the WAND..

FireFox dont ask if i want to save the password  in a lot of pages but Opera always activate the wang, cool.:razz:

---

### Post by erikpiper on 2005-10-14
I use Firefox- and operah- and dillo- etc.

Just wanted to point out that on breezy Firefox has backspace mapped to back unlike what you said- but operah is amazing. :)

---

### Post by xequence on 2005-10-14
Alot of the time non open source can be better then open source.

In the case of opera, this is that time ;)

But other times its the other way around :P

---

