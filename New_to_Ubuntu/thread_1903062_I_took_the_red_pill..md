---
title: "I took the red pill."
date: 2012-01-01
forum: New to Ubuntu
---

### Post by jiryan2316 on 2012-01-01
I finally got Linux up and running.  I also now know that there is an imminent hard disk failure.  I feel free, but I'm limited as to the things I can do.  I can't get Thunderbird mail to recognize my yahoo account.  I have a few problems, and I assume that it is because I am unfamiliar with having to do these things for myself.  can anyone help?

---

### Post by Paqman on 2012-01-01
I can't help with the Yahoo mail setup, but Google can probably sort you there. What other problems are you having?

I'm assuming you've got your data backed up and a new hard drive on the way?

---

### Post by jiryan2316 on 2012-01-01
Sadly, newegg says that the A505D hard drive that I have is no longer available.  and I honestly would not know how to replace it.  I am not a tech guy.  yet...

---

### Post by jiryan2316 on 2012-01-01
also, how would I learn to use ubuntu effectively?  I need some training apps or something.  also, have I limited myself in the way of commercial products?  Can I now no longer play things like Battlefield and Total War and The sims?

---

### Post by Paqman on 2012-01-01
> **jiryan2316 said:**
> Sadly, newegg says that the A505D hard drive that I have is no longer available.  and I honestly would not know how to replace it.  I am not a tech guy.  yet...

Hard drives are generic componants, you can replace it with any laptop sized (2.5") SATA drive. Replacing it is as simple as unplugging the old one and plugging the new one in. That is, assuming you've got access on the bottom of the machine to the drive bay...if you have, it's just a couple of screws to undo and you're in. If you haven't then you'd have to disassemble the machine, which can get a bit hairy with some laptops.

---

### Post by jiryan2316 on 2012-01-01
and commercial software?

---

### Post by Paqman on 2012-01-01
> **jiryan2316 said:**
> Can I now no longer play things like Battlefield and Total War and The sims?

Those are Windows games, so they'll run best on Windows. You can have both Windows and Ubuntu on your machine and switch between them. Some of the older games like Battlefield 1942, the original Sims and Shogun:Total War would run ok in a virtual machine. There's also a bit of a fudge called Wine that allows some Windows apps to run on Linux, but it's pretty hit-and-miss. Just using Windows for Windows games is by far the easiest thing to do.

---

### Post by jiryan2316 on 2012-01-01
So where do I find Linux games?

---

### Post by jiryan2316 on 2012-01-01
And is it true that with Linux I don't have to worry about viruses and hackers and such?

---

### Post by yugnip on 2012-01-01
I could be wrong, but I believe Yahoo only allows imap and pop forwarding if you have a paid account, not a free one. That may the problem with Thunderbird.

The best way to learn Ubuntu or any other Linux distro is to use it as much as possible. The community is here for help, and there is a plethora of reading available online. It's addictive and fun. And you'll be helping others in no time.

---

### Post by drklunk on 2012-01-01
typed A505D into google [shop]("https://www.google.com/webhp?hl=en#q=A505D+replacement+hard+drive&hl=en&site=webhp&prmd=imvns&source=univ&tbm=shop&tbo=u&sa=X&ei=W7wAT_TgNcKItwftxYjQBg&sqi=2&ved=0CFMQrQQ&bav=on.2,or.r_gc.r_pw.r_cp.,cf.osb&fp=2279860aca39e76e&biw=1366&bih=630")

you can definitely find a way to set up yahoo in thunderbird by searching google. when you get your replacement hard drive, do the same thing. its pretty easy to find a good tutorial, with pictures and all, using google ;)

---

### Post by tomski on 2012-01-01
For games & other windows applications wine (mentioned previously) is getting better all the time & i use it to run borderlands (relatively new game released last year)

To get wine going you need to install it & a couple of other items too:
Applications>Administration>Synaptic Package Manager
feed it you password when prompted
search for wine then install
Wine
Wine Gecko
Winetricks

then click apply

once you have that open web browser & goto:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

when that loads search for sims & in the results find the version you want to install & review what others have said about installing it in ubuntu & follow the howto for you ubuntu version (caveat: try to follow the highest rating how to, they are listed as garbage/bronze/silver/gold/platinum)

essentially you will be using winetricks to kick off the install of sims(or game of choice) & create a 'prefix' (prefix = a copy of wine specificly tailored to run the game of choice with pre-requisites required to get it to work) 

it sounds more complex than it is, just keep posting here for help & i am sure others will give a helping hand to help you break you windows connection :) 

good luck

PS:
you will be surprised what games & app do actually work in wine & bizarley some games actually give better results in wine than in windows, i dual boot with xubuntu 11.10 &  win7, i use win7 as a last resort if i cannot get an app to work in wine.
Dual booting for you could cause a further headache as that is pretty complex but there are howto's for it but if you want to learn thing the ubuntu way then i would stick with what you have, persevere & get it to do what you want ;)

---

### Post by Torchwood5 on 2012-01-01
[http://kb.mozillazine.org/Creating_accounts_in_Thunderbird_for_popular_email_providers](http://kb.mozillazine.org/Creating_accounts_in_Thunderbird_for_popular_email_providers)
 
And seriously forget playing games unless you dual boot, but you can find some fun games in software manager.

---

### Post by wildmanne39 on 2012-01-01
Hi, that is true yahoo will not let you use a mail program like thunderbird or whatever the program is called in windows these days unless you pay the yearly rate for it and that is why so many people use google mail.

There are a lot of games in software center and there is a site you can look at also.
[http://www.playdeb.net/welcome/](http://www.playdeb.net/welcome/)
Thanks

---

### Post by chipbuster on 2012-01-01
Amnesia, Minecraft, and UrbanTerror are some pretty good games that run natively in Linux. A lot of popular FPS titles don't though.

As for antivirus and such, I'd recommend reading [this.]("http://ubuntuforums.org/showthread.php?t=510812") 
Generally, Linux is more resistant to malware than Windows, but treating any machine like it's completely immune is just begging to have something bad happen.

EDIT: Also, a good number of indie games support Linux natively. I believe all four Humble Indie Bundles so far have had all their games supported in Linux. Find the latest one [here.]("http://www.humblebundle.com/")

---

### Post by Haneef Mubarak on 2012-01-01
Actually, if you take it (your computer) to Best Buy and tell them (at the geeksquad counter) that you want a new, Linux-compatible HDD, I'm sure they can help. They'll probably even install it if you ask.

---

### Post by fleamour on 2012-01-01
Linux games:

[http://www.gameolith.com/](http://www.gameolith.com/)

---

### Post by Paqman on 2012-01-01
> **Haneef Mubarak said:**
> Linux-compatible HDD

That would be all of them then. Seriously, changing a hard drive is about as hard as changing a light bulb.

---

### Post by saneearth on 2012-01-01
You can find games in the Software Center in the games category or install synaptic and search the games category. I have never worried much about virus's or my system being compromised in Linux though it is possible. To get a Yahoo mail account to work in Thunderbird or ANY mail client you must pay around $20.00 a month. I have for a long time found Gmail to be preferable and there is no addidional cost and plenty of storgage. Mail set up in Thunderbird is identical whether in Windows or Linux. The best way I have found to learn Linux or any Program or OS is to use them, though there are plenty of guides and lots of helphere on these forums for Ubuntu specifiaclly.

---

### Post by guyver_dio on 2012-01-01
Go to software center and download PlayOnLinux. It's like a management tool for installing and running windows applications on linux through wine. I don't know about those particular games, you can try them and they may work but there's no guarantee, but steam works very well in wine aswell as all the games I've tried so you might like to set up a steam account if you haven't already. 

For native linux games, you can find a heap in the software center, or just do a google search for best linux games, that should keep you busy for awhile. 

As for learning ubuntu, the only way is to tinker and use it and when you get stuck or have a question either post it to the forums or run a search in google. Almost everything I wanted to do, someone else has already asked and has been answered. 

Also if you aren't that technically minded yet, ubuntu may not be the easiest distro to start with, so if you feel a little overwhelmed you might like to try these other linux distros.

**Linux Mint**: A very popular distro with a similar feel to windows which goal has been ease of use.  

**PinguyOS**: A linux distro with more of a mac philosophy "works out-of-the-box". It comes pre-installed with all the programs you'll probably ever need.
  
**ZorinOS**: Designed to have the look and feel of windows. Also comes preinstalled with software an average user would expect. 

All of these are based off ubuntu, so you're still using ubuntu basically but set up and tweaked differently.

---

### Post by Torchwood5 on 2012-01-02
> **Haneef Mubarak said:**
> Actually, if you take it (your computer) to Best Buy and tell them (at the geeksquad counter) that you want a new, Linux-compatible HDD, I'm sure they can help. They'll probably even install it if you ask.
 
And charge you out the @$$. Dont do it, its easy to install your own HDD all you need is a small head phillips.

---

### Post by KdotJ on 2012-01-02
> **Torchwood5 said:**
> And charge you out the @$$. Dont do it, its easy to install your own HDD all you need is a small head phillips.

Also, if you're "into computers" then its always good to learn at least a little about the hardware. A little bit of DIY is helpful, and the HDD is an easy one, too.

---

### Post by kurt18947 on 2012-01-02
> **wildmanne39 said:**
> Hi, that is true yahoo will not let you use a mail program like thunderbird or whatever the program is called in windows these days unless you pay the yearly rate for it and that is why so many people use google mail.
<snip>
Thanks

You might be able to cheat;).  Go to your Yahoo! profile or whatever it's called.  Set your location to "Asia".  You should now have free POP in Thunderbird.  I did have a paid Yahoo! work related email address for a while and it did what I needed it to do.   I'll recommend another email provider for a free pop/email service.  I found lavabit.com from a google search.  The web mail page (and the rest of the site) is pretty spartan but it seems to have good uptime and works for POP or IMAP.  Thunderbird will configure it automatically.  They also offer web site hosting though I have no experience with that.  I don't think they're on any 'Top Ten Spam Sites" list yet so perhaps emails sent from there will be less likely to wind up in spam traps. I don't know this but it sounds reasonable.

---

