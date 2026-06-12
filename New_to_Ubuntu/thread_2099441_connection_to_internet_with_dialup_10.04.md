---
title: "connection to internet with dialup 10.04"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by TimerT on 2012-12-29
I need to know how to get dial up connections to internet.  Using windows I have downloaded gnome-PPP and the twelve supporting files.  When I try to install all I get is "Broken dependences"  They list four but there is no way to fix them.  Any suggestions? 
I thank you for any information you might be able to give me.  I have used Ubuntu for several years now and liked it.  That is when I had a high speed connection with "Openrange".

Thank you 
TimerT

---

### Post by Bashing-om on 2012-12-29
TimerT; Hi !

Are you working at this from the wrong end ? 
> [Gnome PPP]("http://en.wikipedia.org/wiki/Gnome-ppp") is a discontinued GUI frontend for the [wvdial]("http://alumnit.ca/wiki/index.php?page=WvDial")In that you need to work from wvdial back to PPP.

wvdial is available in the software repositories.
```
sudo apt-get install gnome-ppp wvdial
```This link for instructions to follow:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Gnome_PPP_and_wvdial](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Gnome_PPP_and_wvdial)

I used wvdial several years ago and found it quite reliable, took a bit of research to set up the config files. 
[INDENT][INDENT]workie great, last long time < == BDQ

[/INDENT][/INDENT]

---

### Post by TimerT on 2012-12-29
Hi Bashing Om, Thank you for the response.  I have the Wvdial as a down load from windows but it will not load and work.  This is one of the 13 files that I downloaded.  Will this file run by it self? If it does, it would run from the terminal... right rather than GNU...
Tkx again
TimerT

---

### Post by Bashing-om on 2012-12-29
TimerT;

Window's applications for windows; ubuntu for ubuntu.
If it is your desire to run wvdial from ubuntu, then from the ubuntu software center search for and install those two packages. Else from the terminal run that sudo apt-get command(from prior post) and will download and Install wvdial and the GUI frontend PPP; and ALL the dependencies at the same time. Docs to set it up is in the followup links in the link I provided.

Remove all that you have done from the window environment and simply do the above and you will have a dial-up interface.
[INDENT][INDENT]try'n to help <== BDQ
 
[/INDENT][/INDENT]

---

### Post by TimerT on 2012-12-30
I guess I am not explaining this problem to well... The only connection I have is a dial up with windows.  I have gone to ubuntu using windows and down loaded the gnome-ppp and wvdial.  I move the files to the desktop in ubuntu 10.04.  Then try to load them using synaptic package manager.  I get a message saying broken package.  This leaves me with no options. HELP
tIMERt

---

### Post by Bashing-om on 2012-12-30
TimerT;

Now I comprehend ! But, I do not know of any means to accomplish this (installing everything where it has to be located)-- not saying it can not be done -- will take a very deep understanding of the ubuntu operating system.

I am trying to think back how I did it the first time, and I just do not remember how I did it !

Might I suggest that you take the ubuntu box to a high speed internet access and do the install of wvdial (defaults will pick up a hardwire internet connection).

Perhaps others will see this post and offer better advise.
[INDENT][INDENT]sorry, I just can not recall <== BDQ 
[/INDENT][/INDENT]

---

### Post by Bartender on 2012-12-30
TimerT -
Are you saying you had a broadband connection, but now you don't?  I struggled with [Ubuntu and dial-up]("http://ubuntuforums.org/showthread.php?t=1377619") for several years.

We've got satellite "broadband" now, horrible when compared to DSL or cable but at least I can get stuff done.

Do you have any reason to think that your modem will even work in Ubuntu?  Getting gnome-ppp installed is unlikely to solve anything for you if you have a winmodem.

I just checked Synaptic Package Mgr. on our 12.04 PC.  It lists gnome-ppp.  Bashing-om's suggestion is, in my opinion, your best option.  Unplug the PC and take it somewhere with broadband.

---

### Post by TimerT on 2012-12-30
Thank You Bashing Om,  Last question... If I was able to get on line with a Linux system could I down load the files and then transfer them to mobile drive then to ubuntu from the mobile drive?  Do you live near Mountain Home?
TimerT

---

### Post by TimerT on 2012-12-30
Hi Bartender, Thank You much for your input.  I had Openrange which went busted.  It was excellent while it lasted.  I am looking for another broadband provider but not having much luck as they all want too much money.  I was paying $39.00 for Openrange.  Note my response to Bashing Om, trying to down load on a different Linux system then up loading to ubuntu... What do you think?
TimerT

---

### Post by Bartender on 2012-12-30
Well, I think it could be done, but once things go sideways with dependencies you'll be lucky to figure it out.  

I still think the simplest thing to do would be take the PC to the connection!  That solves several problems at once.

What kind of modem do you have, and who's your dial-up ISP?  I'm skeptical that your modem will work.  Did you check out my old dial-up thread?

---

### Post by Bashing-om on 2012-12-30
TimerT;

I concur with bartender, I know that a winmodem will not work for use with ubuntu, most external modems will.

Transferring files from exterior source, same problem as using a windows environment, what is termed dependency hell(aptly). Finding all the dependencies would be simple in respect to installing them properly and in the correct locations...in a production machine I wanted on line soonest; Not even to be considered ! If one really had to get this type of situation on line, there is the thought of compiling from source, even then would be heavily dependent on internet connections for retrieval/install of said dependencies.

I have been racking my brains trying to recall how I initially set up my first ubuntu with dial up. Back then I was into slackware and Knopix, It is conceivable to me that I might have pulled wvdial off of Knopix . They both have the same kernel. I bet though that I did then what I am advising you to do now; Take your box to a broadband connection, "sudo apt-get install" and be done with it.

If the box under consideration were not a primary operating system, one might do the compile from source route for the learning experience- if for no better reason. I would think the documentation to make it happen is still apt to systems of today. Compiling from source is what motivated todays package management system with internet connectivity ! Ease of use, so one does not have to do it the hard -error fraught - way.

[INDENT][INDENT]off my soap box now <== BDQ
[/INDENT][/INDENT]

---

