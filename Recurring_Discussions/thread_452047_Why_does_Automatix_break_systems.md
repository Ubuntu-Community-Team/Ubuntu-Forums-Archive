---
title: "Why does Automatix break systems?"
date: 2007-05-22
forum: Recurring Discussions
---

### Post by Hex_Mandos on 2007-05-22
Installer scripts seem to be a touchy subject in the community. I used Automatix in my first install of Ubuntu, and had no problems. When I switched to Feisty, I did clean install (I had to replace XP with something else), and got everything working without any outside script.

However, I haven't found WHY outside scripts are so bad. Is it the extra repositories they add? Or is it the non-repository software they install? Or something else? Basically, I'd like to know how to avoid replicating their ill effects on my own.

---

### Post by jacksaff on 2007-05-22
A very large part of the problem is not that install scripts will break your system, but that they make it very hard to support and troubleshoot any problems you might have.
Debian is very robust and adding different repositories or adding software outside of the package manager shouldn't cause it any problems at all. But ubuntu can't be answerable for the quality of this stuff, or be expected to know about any bugs or compatiblity issues it brings.

---

### Post by Hex_Mandos on 2007-05-23
Well, it IS probably harder to troubleshoot, but that wouldn't justify the outrage I've seen here. Not that I'm out to defend Automatix, I just want to know whether I'm going to break my system by doing manually some things that Automatix does... automatically.  Or, for example, suppose I made a much simpler shell script for friends new to Ubuntu that  modifies their sources.list and downloads some software from unofficial repos. How could I do it so that it doesn't break during an upgrade?

---

### Post by maniacmusician on 2007-05-23
The problem is not with Automatix at all. The problem is that some packages are not the best quality, and they basically don't transition well during an upgrade. Most likely, these are from third party repos. So, you just have to be careful and make sure the packages you use are of decenft quality. 

Automatix has improved considerably in this regard. Most of their packages work well. I haven't had any breakages recently at all. I use it just because it's easier. They have the "extra fonts" option, which is much more convenient than tracking down all those fonts and installing them yourself. 

Err anyways. It all just depends on the packages and where you install them from.

---

### Post by Hex_Mandos on 2007-05-23
So that's the whole deal? I thought it'd be something more serious. However, what makes it different from, say, Getdeb?

---

### Post by ThinkBuntu on 2007-05-23
I've used Automatix for fonts and codecs (I still use it for codecs. Ubuntu's codec finder was spotty) and never experienced any problems...I just disabled the Automatix repos and uninstalled Automatix when I finished.

---

### Post by compiledkernel on 2007-05-23
> **Hex_Mandos said:**
> So that's the whole deal? I thought it'd be something more serious. However, what makes it different from, say, Getdeb?

GetDeb only provides you with the nessecary packages for installation. 

Automatix on certain levels configures, and creates configurations for you - ie. Its NTFS setup or Beryl Setup.

Some might consider this to be negative in manner.

---

### Post by Hex_Mandos on 2007-05-23
Thanks. That makes more sense. I know I can't have replicated that by myself.

---

### Post by cyrusrayne on 2007-05-23
I have yet to have any problems with Automatix.  I haven't used it for very long, but given the amount of stuff I've installed with it (JRE, KDE extras, fonts, audio codecs) I would've been bound to find something by now I'd think.

---

### Post by H.E. Pennypacker on 2007-05-23
I have wanted to ask the same question, because lots of people try to make Automatix out to be Satan himself.  What they never explain is exactly how Automatix causes problems.  Since it is a script that downloads and installs software, I am not so sure what the problem is.  You may say the problem is with the software that Automatix installs, but then Automatix is not really the problem, is it?  The problem would have to be with the developer or the person who packaged the application.

---

### Post by Hex_Mandos on 2007-05-23
> **H.E. Pennypacker said:**
> I have wanted to ask the same question, because lots of people try to make Automatix out to be Satan himself.  What they never explain is exactly how Automatix causes problems.  Since it is a script that downloads and installs software, I am not so sure what the problem is.  You may say the problem is with the software that Automatix installs, but then Automatix is not really the problem, is it?  The problem would have to be with the developer or the person who packaged the application.

Not only that, but installing the same app the hard way would break the system just the same. So far, compiledkernel's answer makes most sense: it's not the software, but the configuration tweaks.

---

### Post by Shay Stephens on 2007-05-23
I have been in conversations with the staff and to me it seems like a primarily political thing that has turned into a blood feud rivalry that might have had some basis in the past but not any longer, but the damage is done, and they attack it at nearly every chance they can, even doing searches and form letter like replies to any post that mentions automatix (at least in the past, I have not kept track of their current SOP's).  

I have used automatix from breezy to edgy without incident and still use it for dapper installs.  I do understand the point about support and third party repos, but that does not explain the level of scorn automatix receives from the staff.  

I am now using feisty, and so far I don't need automatix.  But if I do a new install of dapper, it is one of the go-to tools I rely on.

The staffs treatment of automatix has been a great disappointment for me personally and is the only real tarnish the staff has taken on its otherwise tremendous service in my view.

---

### Post by egon spengler on 2007-05-23
> **Shay Stephens said:**
> The staffs treatment of automatix has been a great disappointment for me personally and is the only real tarnish the staff has taken on its otherwise tremendous service in my view.

Hopefully me posting this won't get the thread deleted but although I would in no way put it past anyone on this forum to be childish, more than likely the attitude of the automatix creator played no small role in any hostilty that lingers.

I have seen the guy claim in this very forum that the success of ubuntu is largely down to him and his script so that gives you somewhat of an idea of the lack of humility

---

### Post by Shay Stephens on 2007-05-23
> **egon spengler said:**
> Hopefully me posting this won't get the thread deleted but although I would in no way put it past anyone on this forum to be childish, more than likely the attitude of the automatix creator played no small role in any hostilty that lingers.

I have seen the guy claim in this very forum that the success of ubuntu is largely down to him and his script so that gives you somewhat of an idea of the lack of humility

Ya there is that too.  Part of the feud.  Stupid.  But indeed he has been instrumental in the success of ubuntu.  I relied on automatix, relied mind you, to make dapper work the way I needed it to.  Thankfully that has changed with feisty.  But he does deserve some credit regardless.

---

### Post by ndefontenay on 2007-05-23
So, in the end Automatix is not bad but it was just not Ubuntu politic...

Something simple like installing proprietary softwares was not recommended by Ubuntu. Not because it would break, but because of the licensing.

They have changed their way big time for Feisty Fawn.

As for Automatix, I don't see any problem as long as you are aware that if something goes wrong, you won't be able to ask for help from this community here.

The reason is that you don't know what's being done. When you do them manually, you know what you have done and can explain it here.

---

### Post by Hex_Mandos on 2007-05-23
Actually, I don't think there's zealotry on the Ubuntu side about much of the proprietary stuff, as there are legal restrictions in several jurisdictions penalizing their distribution. I wouldn't want to risk Ubuntu because of mp3 support, for example.

However, I don't think that doing things the right way is for everybody. For example, average users shouldn't ever touch sources.list, IMO. Not because it's hard to do (objetively speaking, it's pretty easy, the file structure is quite evident), but because they might carelessly break more stuff than Automatix could ever dream about breaking. The command line is great for me, but not for, say, my mom.

---

### Post by Adamant1988 on 2007-05-23
> **Shay Stephens said:**
> I have been in conversations with the staff and to me it seems like a primarily political thing that has turned into a blood feud rivalry that might have had some basis in the past but not any longer, but the damage is done, and they attack it at nearly every chance they can, even doing searches and form letter like replies to any post that mentions automatix (at least in the past, I have not kept track of their current SOP's).  

I have used automatix from breezy to edgy without incident and still use it for dapper installs.  I do understand the point about support and third party repos, but that does not explain the level of scorn automatix receives from the staff.  

I am now using feisty, and so far I don't need automatix.  But if I do a new install of dapper, it is one of the go-to tools I rely on.

**The staffs treatment of automatix has been a great disappointment for me personally and is the only real tarnish the staff has taken on its otherwise tremendous service in my view**.

The 'tarnish' in my view is that the Ubuntu staff puts up with the Automatix developers.  I really wish people like you had a CLUE what the staff has had to endure from them, and what they've been trying to accomplish with them, just so you can have an easier time installing your codecs.  But, in the interest of keeping the peace, and promises to friends, I'll stop this there.

---

### Post by Polygon on 2007-05-23
well they dont even post here anymore do they? they got their 3rd party application forum removed and now have their own forum. I sometimes see arnieboy post... occasionally.

---

### Post by aysiu on 2007-05-23
> **Polygon said:**
> they got their 3rd party application forum removed and now have their own forum. Correction: arnieboy *asked* to have his 3rd-party forum removed.

---

### Post by Polygon on 2007-05-23
yeah thats what i meant. he asked for it to be removed because he got his own website and forums where he could give support without a couple of members giving him greif.

---

### Post by aysiu on 2007-05-23
> **Polygon said:**
> yeah thats what i meant. he asked for it to be removed because he got his own website and forums where he could give support without a couple of members giving him greif.
Uh-huh.

---

### Post by Polygon on 2007-05-24
whether the couple few that ive seen over the years debating whether automatix is good or bad are right or not, its true that they kinda are giving him a hard time about it. The forums are really good about it, but this entry in his FAQ isnt there for no good reason

> 
 Is Automatix2 safe? Folks in #ubuntu on IRC keep telling me it isn't.

    * Yes, it is perfectly safe. Thousands of users worldwide use Automatix2 every day without any issues. If you think you have run into any issues related to Automatix, please report to our forums to get quick and high quality support. 




some guy in the ubuntu irc channel was asking why he couldent play dvds, someone responded that you needed to have dvd codecs installed. he responded with "well how do i install them?" I told him that the easiest way was to use automatix. Big mistake. I had about 5 people call the all powerful ubotu to spit various messages about how automatix is not safe, and how even if it works for me it may not work for everyone. When i tried to ask why they were so hostile towards it they said that the see many many many people com in saying that automatix broke their systems. I highly doubt that it was automatix's fault but i left as i knew i wasnt going to convince them

and like i said, i think i remember arnieboy saying that he asked for his third party software subforum to be closed down so that he could continue support on his own forum and not having to worry about people debating whether this software will destroy your computer or not, but rather for support and bug reports

---

### Post by aysiu on 2007-05-24
These are my thoughts on the issue:
[http://ubuntucat.wordpress.com/2007/05/22/why-i-dont-recommend-automatix-not-what-you-may-think/](http://ubuntucat.wordpress.com/2007/05/22/why-i-dont-recommend-automatix-not-what-you-may-think/)

---

### Post by KiwiNZ on 2007-05-24
This issue has been discussed at length on numerous  occasions.

It has just been through the Forum Council. 

I see no value in continuing it here. I am going to close this thread.

---

