---
title: "Gyachi Log On Problems"
date: 2009-06-23
forum: Philippine Team
---

### Post by ragadanga63 on 2009-06-23
Recently Yahoo did something to their Messenger.  In effect, other IM Clients such as Gyachi, Pidgin, Kopete cannot log in to YM anymore ([http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml](http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml)).  

Do we have a workaround for this problem with Gyachi?

---

### Post by loell on 2009-06-23
unless this is a personal experience, i'm still kinda skeptical about gyachi not able to log in, since the developer implemented YMSG 15 about a year ago and it has been the default, which isn't affected by yahoo's deprecation of YMSG 14 and 13.

i'm raising my eyebrow just about right now, about this softpedia article

> While many of us thought it might be an ISP issue, **some very smart people found out the truth: Yahoo! changed the login method!** 

while in truth, yahoo didn't kept this a secret.

[http://www.ymessengerblog.com/blog/2009/06/09/we%e2%80%99re-retiring-versions-60-to-75/]("http://www.ymessengerblog.com/blog/2009/06/09/we%e2%80%99re-retiring-versions-60-to-75/")

Yahoo's login method has been incremental, YMSG 15 being three years now and YMSG 16 about a year or so , pidgin could have paced with the time but they didn't, instead they make it appear that yahoo deliberately cut older protocols quickly. though I give kudos and credit for some of the pidgin guys implementing the YMSG 16 sequence for pidgin.

I despise those of them, that are not really truthful as to what really happened.

---

### Post by kikoman on 2009-06-23
Yahoo is a headache ever since. It will have the same slow death like ICQ. People i know is now switching either to Google or Skype.

---

### Post by Samhain13 on 2009-06-23
Experiencing Yahoo login problems on Pidgin myself. Buti na lang, nandito sa Pilipinas ngayon ang aleng mahal ko. :D

---

### Post by ragadanga63 on 2009-06-23
Kabayang loell,

I've tried searching the Ubuntu forum about this problem.  Hindi po ako nag-iisa.  Marami rin pala ang nakaranas ng ganito.  

Problema po ito sa 3 desktops ko na may Ubuntu, sa Linux Puppy desktop ko na may Gyachi 1.1.0 (something) na ina-upgrade ko sa 1.1.71, pero ganoon pa rin ang problema.  Pati na rin sa Laptop ko na gumagamit ng mas lumang gyachi, ina-upgrade ko sa 1.1.71, pero ganoon pa rin.

---

### Post by loell on 2009-06-23
check if you're using YMSG 15 login method, 1.1.0 didn't have ymsg 15 so a server change like pidgin user does might do the trick.

also, show me those forum post links (exact gyachi login problems), and i'll try to look into that.

---

### Post by killer_d76 on 2009-06-24
first time Gyachi user here.. i just installed it early this morning... Pidgin is working properly now after the update.. so i got curious using gyachi (i was planning to use this on my kapitbahay's desktop since they have been using YM eversince), and it seems to be very similar to Yahoo's YM!.. so i followed the instruction and install it here on my little laptop.. at first, it seems to be hesitant on logging me in.. then i got connected!, then to test it if it is working i open up Pidgin (using different account name) on the same laptop where i have Gyachi.. i was able to receive messages coming from my account on Pidgin but i can't seem to send/reply to Pidgin using Gyachi?!..

---

### Post by killer_d76 on 2009-06-24
oh and by the way this is the latest Gyache 1.1.71 , and it only opens up using Terminal!.. clicking on the icon from Applications> internet> GYachE Improve can't seem to open Gyache?..

---

### Post by loell on 2009-06-24
> **killer_d76 said:**
>  but i can't seem to send/reply to Pidgin using Gyachi?!..

that's what i've been receiving lately, it's probably a server issue,

try to change the server to **cn.scs.msg.yahoo.com**

---

### Post by killer_d76 on 2009-06-24
ok.. i can only recieve reply on Pidgin from Gyache if i open up a conferrence room?.. but if someone sent me a personal message, i can't seem to send a reply to it?..

---

### Post by loell on 2009-06-24
> **killer_d76 said:**
> oh and by the way this is the latest Gyache 1.1.71 , and it only opens up using Terminal!.. clicking on the icon from Applications> internet> GYachE Improve can't seem to open Gyache?..

that is really strange,

drag the icon to the desktop,  right click it then go to properties, see what command it's using, it should be the command : **gyachi**

---

### Post by killer_d76 on 2009-06-24
> **loell said:**
> that's what i've been receiving lately, it's probably a server issue,

try to change the server to **cn.scs.msg.yahoo.com**

thanks loell... it did fix the issue! it's working now! ;)

---

### Post by Script Warlock on 2009-06-24
@loell, ok na yung gyachi sa lahat na pc kala ko gyachi bugs na sa ubuntu, server lang pala ng yahoo... yung error is all about yahoo server.

yung di mabasa ang reply dagdag lang pala ng cn.

---

### Post by killer_d76 on 2009-06-24
by the way loell, i can't seem to open Gyache by simply clicking on the icon itself?.. though i can only open it on terminal but i need to be root/admin to open it up.. is there a fix on this?.. thanks bro!

---

### Post by killer_d76 on 2009-06-24
> **loell said:**
> that is really strange,

drag the icon to the desktop,  right click it then go to properties, see what command it's using, it should be the command : **gyachi**

yes it says **"gyachi"**

---

### Post by loell on 2009-06-24
i really don't know why it would not execute, do other desktop launchers function well?

---

### Post by wersdaluv on 2009-06-24
I also had this problem earlier. I used to copy Gyachi's server whenever Pidgin is not working. A while ago, Gyachi's the one with the problem.

All I did was to change the server to **scs.msg.yahoo.com**. That fixed the problem :)

---

### Post by ragadanga63 on 2009-06-24
Server lang pala ang problema.  Thanks again loell.

---

### Post by Script Warlock on 2009-06-24
> **killer_d76 said:**
> thanks loell... it did fix the issue! it's working now! ;)

OT: @killer_d76, napagana mo ba ang tamang resolution ng neo basic laptop mo? i now figure out bat di tumoloy maginstall  nag --noapic at --nolapic lang ok na sana pero etong resolution naman ang laki!... any drivers for this? its SIS..

---

### Post by killer_d76 on 2009-06-24
> **loell said:**
> i really don't know why it would not execute, do other desktop launchers function well?

yes i tried dragging some apps on the desktop and they function well, i tried typing gyachi on the terminal and i got "segmentation fault" error!, which i do not get on other apps like pidgin?

@Script Warlock - the resolution on my Neo Empriva 540(?) is okey.. i have no issue on screen resolution since Gutsy ;), i tried installing Ibex on Neo Basic before sa kasama ko sa trabaho and yes i got the same resolution issue, try using older version like hardy or gutsy.. kasi isa dun yung gumana ng maayos yung resolution eh.

---

### Post by dsdeiz on 2009-06-24
> **loell said:**
> that's what i've been receiving lately, it's probably a server issue,

try to change the server to **cn.scs.msg.yahoo.com**
Yes! Nagwork din ito sa pidgin!! (servers from the site #pidgin referred me too didn't) Woot! Btw, I'm using gyachi at home pero i'm using finch sa libreng shell.. Hehe

Madamo gd nga salamat sir!! :guitar:

---

### Post by Script Warlock on 2009-06-25
OT: @killer_d76, ok na pala resulotion ng neo basic laptop nakuha ko na driver para sa sis and now its working perfectly sa laptop ng kaibigan ko.....

---

### Post by Ravskie on 2009-06-25
> **loell said:**
> that's what i've been receiving lately, it's probably a server issue,

try to change the server to **cn.scs.msg.yahoo.com**

Sir loell thanks po dito may pidgin is working fine with yahoo now .....

---

### Post by beh_botehnga on 2009-06-25
> **killer_d76 said:**
> thanks loell... it did fix the issue! it's working now! ;)

thankx to loell also.. now its workin also.. server problem lang pala.. salamat...

---

### Post by killer_d76 on 2009-06-25
@loell,

boss i'm getting "Segmentation fault" error when if i tried opening Gyache thru terminal without typing sudo.. i tried un-installing and re-installing Gyache but i still get the same result, but when i installed it my kapitbahay's desktop computer... okey naman sya?! ???

---

### Post by loell on 2009-06-26
> **killer_d76 said:**
> @loell,

boss i'm getting "Segmentation fault" error when if i tried opening Gyache thru terminal without typing sudo.. i tried un-installing and re-installing Gyache but i still get the same result, but when i installed it my kapitbahay's desktop computer... okey naman sya?! ???

It's probably a binary package gone berserk, maybe redownload a fresh package (not the cached one) , the reinstall it again.

---

### Post by killer_d76 on 2009-06-29
> **loell said:**
> It's probably a binary package gone berserk, maybe redownload a fresh package (not the cached one) , the reinstall it again.

i've updated my ubuntu, and download .deb files from gyache site, uninstall and re-installed gyache.. i'm still getting segmentation fault?!.. well it's okey.. i as long as i can still use it through terminal as root! hehehe :D

---

### Post by j.m.wilson@earthlink.net on 2009-06-30
Changing the server fixed this problem for me

---

### Post by Script Warlock on 2009-07-01
sana ma-update na rin gyachi protocol using 9 na..

---

