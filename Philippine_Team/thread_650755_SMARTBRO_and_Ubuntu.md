---
title: "SMARTBRO and Ubuntu"
date: 2007-12-26
forum: Philippine Team
---

### Post by bme on 2007-12-26
mga Kabayan,
I am an OFW. I use my dell laptop extensively on my work. I connect it to my office lan to access the internet so there is no doubt as to its working condition under ubuntu 7.10.
I am now on vacation. I triple boot vista,xp and ubuntu. On vista and xp I am able to connect to smartbro. However I am unable to connect using ubuntu. the network monitor states that the "wired conncection" is connected but I am unable to connect using firefox. also I am not able to ping any site.
Salamat sa tulong and Merry Christamas/Happy New Year!!!!

---

### Post by raxso on 2007-12-27
That's weird coz i am using dell inspiron 6400 and right now im using ubuntu 7.10 without problem.... maybe you can check if you got an ip address first....

---

### Post by bme on 2007-12-27
how do I check if I have an IP address?

---

### Post by loell on 2007-12-27
if this is smartbro then most probably you'll be using **dhcp** 

go to

**System** menu --> **Administration** --> **Network**

in the **connection** tab , you should see a **wired network** on  the list, select it and click the ** properties ** button 

uncheck first the **enable roaming mode** 

then in the **configuration ** toggle list, select **automatic configuration DHCP** click OK then close.

---

### Post by bme on 2007-12-27
loell,bay kumusta ang davao?
dhcp is already enabled as I have used the lan on the school network abroad.
I forgot to mention the the mozilla website ([http://en-us.www.mozilla.com/en-US/firefox/central/](http://en-us.www.mozilla.com/en-US/firefox/central/)) can be displayed on mozilla. Strange setup isn't it?
Oh, and in vista home basic that I have, google cannot be accessed.
It is only in XP that i have no problems,the speed test on smartbro connection is acceptable.

---

### Post by loell on 2007-12-27
> **bme said:**
> loell,bay kumusta ang davao?


Ok lang bay :)


> **bme said:**
> 
dhcp is already enabled as I have used the lan on the school network abroad.
I forgot to mention the the mozilla website ([http://en-us.www.mozilla.com/en-US/firefox/central/](http://en-us.www.mozilla.com/en-US/firefox/central/)) can be displayed on mozilla. Strange setup isn't it?
Oh, and in vista home basic that I have, google cannot be accessed.
It is only in XP that i have no problems,the speed test on smartbro connection is acceptable.


yeah strange indeed , can you see these adresses in you DNS tab?

---

### Post by raxso on 2007-12-27
type 

sudo ifconfig

it will ask for your password

and look for the inet addr this is your ip address

and follow what loell said and ping the dns address that you have on your dns entry...

if you can ping this entry then you might need to go to portal.smartbro.net and sign in so that your pc can be registered to the smartbro system.... just be ready with your account..

---

### Post by loell on 2007-12-28
yeah, i just remember what raxso said. login to your smartbro account, this solves my similar problem 8 months ago, and this will likely solve your problem too.

---

### Post by bme on 2007-12-28
yes I can ping the dns no problem....the problem is when using ubuntu "portal.smartbro.net" cannot be accessed.
laptop is already registered with smart-otherwise it will not work under XP

---

### Post by bme on 2007-12-28
I would also like to add that I was successful in setup of adhoc network using mydaughter's TOSHIBA tecra and my dell. 
Only ubuntu does not work.....:-(

---

### Post by perbiu on 2007-12-28
Nasubukan mo na bang mag Clear Private Data sa Firefox?

---

### Post by bme on 2007-12-29
nasubukan ko na halos lahat.....andun din  nginstall ako ng kubuntu sa isa pang partition ayaw talaga mg connect sa ibang website except mozilla.
pwede ding mgping ng dns address,mg issue ng "host gmail.com".gumagana rin.

---

### Post by raxso on 2007-12-29
ano ipaddress o inet addr n nkukuha mo sa ubuntu, you said you were able to ping the dns server but can not go to smart portal, if you were able to ping the dns it means you can get thru the portal.smartbro.net. that is really weird problem that you are getting...

---

### Post by bme on 2007-12-29
192.168.244.1 yong ipaddress that i can ping using the network tools and I get 100 %.
Yes my problem is weird but on the other hand linux is somewhat weird-according to my daughter:):):):)
I mean she cannot understand why I have to spend so much time tweaking ubuntu when I have a perfectly working XP.

---

### Post by Nessa on 2007-12-30
I'm using smartbro with an xp/7.04 desktop. Nung bagong-bago pa lang ang ubuntu, I had to go to [http://portal.smartbro.com](http://portal.smartbro.com) to login. 

Ewan ko kung bakit. Pareho naman ang MAC address kahit bali-baliktarin mo ang OS. Smartbro is weird that way.

---

### Post by perbiu on 2007-12-31
Subukan mo gumamit nang Ubuntu Live Cd kung puede doon mag internet. Baka kasi bad installation lang o corrupted yung OS?.

---

### Post by bme on 2007-12-31
kung ako ang binibigyan mo ng advice,nasubukan ko na lahat ng live cd na meron ako-kubuntu 7.04,7.10,ubuntu 7.04,an old kanotix,the latest pclinux os-ayaw talaga gumana ang smartbro......

---

### Post by perbiu on 2008-01-01
SmartBRO sa Ubuntu 7,10 din kasi gamit ko, Ok naman.

---

### Post by raxso on 2008-01-05
nakakapunta ka ba sa portal ng smartbro.

---

### Post by Nessa on 2008-01-07
Ang weird naman. Sir, may router ba or direct to the motorola canopy?

---

### Post by bme on 2008-01-08
direct to smartbro canopy ito....
I have since discovered that when I try to connect Ubuntu and later on use the other laptop with xp on it I can no longer connect to smartbro...
I had to wait for about an hour with the ac adaptor of smart unplugged before connecting the xp laptop....
big headache itong smart talaga pagdating sa different OS...parang there is something in smartbro that needs to be reset everytime one switches to another OS.
I also discovered that when I use Vista on smartbro some websites cannot be reached....
Because the internet is so important to my daughter's studies I am for now giving up experimenting with ubuntu.....
THANKS FOR ALL REPLIES!

---

### Post by raxso on 2008-01-08
Nakakalungkot naman experience mo about ubuntu, but i never experience this, because i am also experimenting and alos using smart bro, my sister is using mac on her laptop, and i am using ubuntu sometimes fedora and i did not experience this, it is really weird.... but i do hope you'll try again.... have a great day...

---

### Post by daxumaming on 2008-01-09
> **bme said:**
> kung ako ang binibigyan mo ng advice,nasubukan ko na lahat ng live cd na meron ako-kubuntu 7.04,7.10,ubuntu 7.04,an old kanotix,the latest pclinux os-ayaw talaga gumana ang smartbro......

Gagana sya sa SmartBro.... I used to have SmartBro.. pero mag-re-reauthenticate ka muna bago ka makapag-surf. Problema naman, pag nakapag-surf ka, mag-re-re-authenticate ka sa Windows.

So I did the most logical thing.... Nuke Windows!

Back to the topic: If you don't have a router... then disconnect the power supply from SmartBro's POE. Wait for a few hours, probably 2-3hrs para ma-refresh system mo sa DHCP server ng Smart. Reconnect mo bago mo i-power-on ang PC. Once you launch Firefox, it'll direct you to the portal page. Just authenticate, and you're good to go.

If you have a router, that's even better..... copy your PCs' MAC Address and replace the one on your router... no need to wait for a few hours. And you can use both Windows and Linux without being directed to the portal page. You can even use it at the same time if you have more than one pc.

SmartBro claims to only use MAC Authentication, pero their DHCP server also detects OS changes. Kaya pag-naka-dual boot ka, patay ang isa.. you need to re-authenticate. However, i've tested it out before. I installed XP, 2000, 98, Kubuntu, Ubuntu, PCLinuxOS, Bayanihan, and OpenSUSE on one PC. Kung naka-authenticate ka sa windows, kahit mag-boot ka to XP to 2000 to 98, walang problema. Pero pag nag-boot ka na to Kubuntu, you need to re-authenticate. If already authenticated, kahit mag-switch ka to other Linux distros, wala ka na namang problema..... Yun nga lang, pagbalik mo sa Windows.... portal page na naman.

Using a router's the easiest option. You should use it if you dual-boot between Windows and Linux.

---

### Post by perbiu on 2008-01-09
Maganda yung router, bumili din kami niyan kasi naging dalawa na computer namin mga P2,500, yun may Wifi kahit nag memeryenda ang utol ko sa labas ay nakaka pag internet siya sa Laptop niya.

---

### Post by bme on 2008-01-13
dax,
magandang idea yong router....however since I discovered that my smartbro has problems with Vista then I am reluctant to spend another 2k plus on a router.....
Also as I have stated swithing between Vista and XP also has its own "reseting" problem...contrary to what you have on your smartbro na between linux and windows lang ang problema.

---

### Post by bme on 2008-01-13
dax,
seems to be u r an expert in ubuntu kaya gusto ko dadagan mga nabanggit ko.
you mentioned that whenever you try to surf using ubuntu(or any other distro/OS) you get "redirected to the smartbro portal". I NEVER experienced this on my ubuntu-the network icon gets stuck at "acquiring network address". I even tried for almost an hour waiting to be connected-wala talaga.
then I tried the "ifconfig" option after editing the network interfaces-wala rin...
talagang kaiba itong smartbro ko....the support hotline was no help either-tried twice and 2 different answers-one blamed "base" ,the other one blamed Vista....
Thanks anyway!

---

### Post by dodimar on 2008-01-13
dual boot ako, XP and Ubuntu 7.10. Kakainstall ko lang last week ng Ubuntu and ni hindi nga ako nag daan sa smartbro portal when I first run Ubuntu (installed using alternate CD). And everytime I swhitched back and forth between XP and Ubuntu, hindi ako nag-re-authenticate.
My brother has triple boot (Vista/XP/Ubuntu), but no problem with accessing sites,and kahit magpabalik balik siya on those OS, hindi na kailangan mag-re-authenticate.

i think wala sa Ubuntu ang problem (nor sa Vista or XP), I think sa smartbro ang problem. Because some base stations have different configurations (based sa pakikipag-usap ko sa mga contractors ng smart na may hawak ng base stations).

I am no expert, but I would suggest try using the laptop on a different smartbro na nakaconnect sa ibang base station (if you know someone). If wala ng problem, then base station ang problem. If same pa rin, better call smart, and demand for a solution (I say demand, not request).

Suggestion lang po...

Cheers...

---

### Post by bme on 2008-01-14
I also believe nothing is wrong with any of my rigs(toshiba tecra,sony vaio,and a dell inspiron) nor with my softwares/OS.
No point also in demanding smart solve the problem-what I did was just to tell users to use XP in connecting to smartbro.No problem that way.No increase in High Blood pressure.......:):lolflag:
I still use ubuntu sa mga hotspot ng starbucks though......

---

### Post by dodimar on 2008-01-15
Yeah, talagang high blood.....

Kakaiba talaga ang smartbro.....

It's not Ubuntu that is having problem, it is smartbro.

Enjoy surfing at home using XP, and away from home using Ubuntu..

(How I wish I have my own laptop :( )

---

### Post by februarius on 2008-01-16
tama po c papi daxumaming, ipa re-authenticate mo po sya,
kasi po minsan ung mga canopy nag rerely sila sa mac address nung router or ung pc na unang pinag saksakan ng canopy, or kung makuha mo ung mac address nung unang pinag saksakan nung canopy, then i clone mo lang sya lagay mo uli dyan sa running os mo,

---

### Post by daxumaming on 2008-01-16
I was one of the first who got a smartbro account when they first pilot tested it here in baguio before being deployed in GMA. now im not sure kung me binago sila sa configuration nila since it's almost a year now since i last used my smartbro. 

I used to work at a call center (AT&T FastAccess account) and the need for me to have a multi-boot OS was a necessity ( I had it all, XP, Vista, 98, 2000, and even 95, not to mention other distros). But my experience may have resulted from an old configuration on Smart. However, I always have to re-authenticate when switching from windows to linux and back. And it's been the bane of my existence since i didn't have a router back then (which costs around 4-5K). Since being released from my company, i no longer find any need to have a multi-OS configuration.. so i did the most logical thing..... dump windows.

I needed a host a server, kaya i switched to PLDT. But i did try to convince a friend to dual-boot xp and kubuntu just recently, and as expected, he has to reauthenticate to the server. After using kubuntu, he had to switch back to windows. he called me up to inform that he has to reauthenticate again. so i guess we still have the same base configuration here in baguio.

Regarding your issue of having no live connection to the server.... I'm stumped.. I honestly don't know what advise to give you. Now I'm not sure if it's really Smart since it never happened to me, but after rebooting, have you tried powercycling your PoE device? Sorry, but that's the only thing i can think of right now.

As for the reauthenticate when switching to Vista and XP... also never happened to me. So again... can't give any advice.

As for dodimar's no-reauthentication, that's really great. I've heard of such, i think i saw it at smartwifi.com.ph or pinoydsl.com, but i always assumed that they're using a router. but i never asked.

Now, if you're adamant of purchasing a router for fear that it might not work, then try borrowing a router from a friend or relative (don't forget to change its mac address) and then try switching OS. if it works, then you could purchase that same model.

But then again, I can only encourage you to purchase a router if you have 2 or more PCs at home (which you do), otherwise, it won't make economic sense if you only have one PC and use windows 80% of the time.

Hope my insights helps.

---

### Post by raxso on 2008-01-17
I am also using smartbro here in taguig and my sister an i share the connection and without a router she is using mac os x and i am using ubuntu and fedora, before i we need to re authenticate when using the connection but now there is no need to re authenticate i just plug-in my laptop and it works and when my sister wants to use it she just plugs-in her laptop. but then again if you are really having problems with the connection and you said that you were able to use ubuntu in other location then a router will be great help for you... 

just my 2 cents.....

---

### Post by bme on 2008-01-17
first of all SALAMAT sa lahat ng ng reply....
I already stopped experimenting on different OS to connect to smartbro.basta gumana sa XP ayos na sa amin. Lahat ng 3 laptop may XP na kaya sa ngayon wala ng problem.....
when I told smart customer service about my problem the first one I talked to told me there was a problem sa base station nila and wait daw ako ng 24 hours. so kinabukasan or after 24 hours tawag uli ako dahil problme pa rin. Iba na ang kausap ko at vista naman daw ang problema.ayt that point I got a bit irritated. pag sinabi ko na linux ang gamit  eh baka linux naman ang sisihin.....
so in the end xp na lang ang gamit namin sa bahay......walang iritasyon...

---

### Post by dodimar on 2008-01-17
Kahit saang provider magpunta, there is always a lot of complaints. Internet technology here in Philippines is just emerging (as fas as I know). It seems like everyone is still under an "experimental" stage. And this causes problems and 'headache' to customers (just called smartbro cust service yesterday to report a bill that never came to me) and, bills pa lang yan, sakit na sa ulo..

In short, it's an existing problem sa lahat ng providers (checked the net for a good net provider, pero pag dun ka nag-base, wala kang mapipili...)

regarding my case of not re-authenticating, I tried (yesterday) switching back and forth between XP and Ubuntu, never re-authenticated. I'm not using a router.

bme, good to hear that you're settling now, though it is sad it is not Linux....

As for me, I'm planning to settle with Ubuntu, though I will not remove XP (for my wife)...

good luck internet users in the Philippines, let's hope na maging stable na ang service nila dito sa Pinas...

cheers....

---

### Post by nss_120 on 2008-07-06
Mr. Raxso said:


type

sudo ifconfig

it will ask for your password

and look for the inet addr this is your ip address

and follow what loell said and ping the dns address that you have on your dns entry...

if you can ping this entry then you might need to go to portal.smartbro.net and sign in so that your pc can be registered to the smartbro system.... just be ready with your account..


---------------------------------
Does it work in hardy heron?

Does

---

### Post by Nessa on 2008-07-06
Smartbro user here too. The reauthentication does not pose a problem but it is annoying. We had to get a router because we got more computers and we didn't have to reauthenticate from then on. Pansin niyo na ang public IP niyo ay local din?

---

### Post by deoxyna on 2008-07-06
Natatawa lang ako after reading this thread. Sabi ko sa sarili ko, ibang klase talaga SmartBro, hanggang dito ba naman sa Ubuntu, problema pa din? Matagal na din akong subscriber ng SmartBro, Meridian Telecomms pa dati yan. Naka ilang palit na din ako nga antenna. Originally yung Sendfar from Meridian tapos talong versions na ata ng Motorola canopy. And so far wala naman akong naging problem sa connection. Dual boot din ako XP/Kubuntu, and I don't need to re-authenticate when switching OS. I believe sa base station configuration ng Smart ang problema, yung ibang neighbors ko na naka home sa ibang BTS, hirap minsan mag authenticate. When using a router, make sure na may connection ka muna directly from your box, before you transfer the connection sa router. After that, redirect ka uli sa portal, pero one time process lang naman 'to.

---

### Post by ache109 on 2008-07-07
I'd conducted a test between smartBRO and PLDT myDSL:

Tested it on Ubuntu -myDSL (on my home PC) and winxp - smartBRO (on my ninang's house w/c is utterly near) When the typhoon Frank was surging over Luzon.

Nag internet ako kase walang magawa..(check ng ubuntu forums syempre). Hindi makagala kase may bagyo. I downloaded a application (a game thingy on wine). w/c is 100MB in just 10mins. Ang bilis ng connection at walang hassle.

Then I proceeded to my ninang's house (syempre nagumusta) Then opened their laptop to intall the same game. Inabot ako ng 30mins. Just to dload that 100MB file. Mabagal din ang connection (kahit website ng PAGASA ayaw bumukas) kaya nagtaka ako dahil almost 4 years na ang DSL namen ok ang connection. Ung sa smart bro binagyo lang bagal na.

My conclusion:
Na ung smart bro nagkakaroon ng "Network Interface" kapag there's is someone that is "Interfering it's connection". (kung baga, lumilihis ung connection kaya lumiliit amg bytes na narerecieve ng computer). Since myDSL is a wired connection, mas puro ang dating ng connection. Preffered ko parin ang myDSL kahit na mejo matagal na ang e-net probider na ito.

Or it's because of the OS that i'm using. Kaya hindi ko matanggihan ang ubuntu eh//!!!

Have a Nice Day,

Ache109

UBUNTU rocKS !!:guitar::guitar::guitar:

---

### Post by dodimar on 2008-07-07
> **ache109 said:**
> I'd conducted a test between smartBRO and PLDT myDSL:

Tested it on Ubuntu -myDSL (on my home PC) and winxp - smartBRO (on my ninang's house w/c is utterly near) When the typhoon Frank was surging over Luzon.

Nag internet ako kase walang magawa..(check ng ubuntu forums syempre). Hindi makagala kase may bagyo. I downloaded a application (a game thingy on wine). w/c is 100MB in just 10mins. Ang bilis ng connection at walang hassle.

Then I proceeded to my ninang's house (syempre nagumusta) Then opened their laptop to intall the same game. Inabot ako ng 30mins. Just to dload that 100MB file. Mabagal din ang connection (kahit website ng PAGASA ayaw bumukas) kaya nagtaka ako dahil almost 4 years na ang DSL namen ok ang connection. Ung sa smart bro binagyo lang bagal na.

My conclusion:
Na ung smart bro nagkakaroon ng "Network Interface" kapag there's is someone that is "Interfering it's connection". (kung baga, lumilihis ung connection kaya lumiliit amg bytes na narerecieve ng computer). Since myDSL is a wired connection, mas puro ang dating ng connection. Preffered ko parin ang myDSL kahit na mejo matagal na ang e-net probider na ito.

Or it's because of the OS that i'm using. Kaya hindi ko matanggihan ang ubuntu eh//!!!

Have a Nice Day,

Ache109

UBUNTU rocKS !!:guitar::guitar::guitar:

Primarily it is because Smartbro is a wireless connection. So kapag umulan, degraded yung signal na nare-receive ng Canopy from the base station.

Ako.. wala akong internet nun may bagyo... Smarbro gamit ko...

---

### Post by Nessa on 2008-07-07
Buti nalang hindi binabagyo ang Davao hehe. No problems so far. Basta ang mac address lang ng registered pc ang importante.

---

### Post by dodimar on 2008-07-07
Yeah... MAC and also yung mga puno o building na haharang sa line of sight ng Canopy and ng Base Station...

---

### Post by ebug on 2008-12-30
I wished I read this forum first. :icon_frown:

My wife arrived home from NAIA, and early morning at 3am, excitedly open her laptop with Ubuntu. I called her thru Skype-Out. 

I installed all the bells and whistles in Ubuntu with skype, gyache, openoffice3, hamachi/vnc...even handbrake. 

So, she open up ubuntu ready to skype, but when Smartbro authentication page wont show up, I just told her (thru Skype-out) to restart and just boot to Vista instead.

But then HP/Vista is just directing to factory setting mode. WTF. So I told, just click yes. But then, (opps that's it), I told her to shut the pc at once. (Yeh yeh, I hear you all...that was stupid). ](*,)

So she restarted, and there is GRUB error 17. 

But then, no supergrub or extra ubuntu cd at home. So what else to do?  

XP! :mrgreen:...o goodness ](*,)

So, she reinstall XP since the recovery mode (F11) is no longer working. But as much as I wish that everything should work, the LAN and WLAN are missing. 

Need to download the drivers! WTF...no internet! 
     
*(Kasalan mo at yan Ubuntu na yan!!!)*

I tried to save Ubuntu from her wrath but instead...I got a series of litanies with *"...I will never ever let you install Ubuntu in my laptop again!!!"*

She just went to sleep (too tired from flight and this) and I'm here trying to find a solution. I got few hrs left.

Waaahhhh!!! :cry:

---

### Post by loell on 2008-12-30
> **ebug said:**
> 
     
*(Kasalan mo at yan Ubuntu na yan!!!)*

*I will never ever let you install Ubuntu in my laptop again!!!"*


Waaahhhh!!! :cry:

:lolflag:

hahah!  ok lang yan :)

---

### Post by ebug on 2009-01-01
UPDATE

hey loell, you gyachei god, it's good to get a reply from you. =)

anyway, goodnews to all, got hardy installed on my wife's laptop. hehe. How?...well, thanks to gutsy (yeh gutsy)

So, my wife woke up from slumber. Called me to..."fix her laptop once and for all!". So I asked her to check my cds at home and read each one with anything about hp, xp, ubuntu. And lo and behold there is that lone ubuntu 7.10 cd. (Gutsy, was my intro to ubuntu world but it was not a good one. So it took a working Hardy to really absorb me to ubuntu)  

Gutsy is my last straw. So I asked my wife to install it. After installation, she checked internet, got smartbro authentication page and log on. and that SOB smartbro worked (yehey!!!).

I asked her to upgrade to hardy. it took several hours under smartbro. Got it finished and she installed skype. Everything worked perfectly!  
   
After 20 hrs, i got my well deserve sleep and a sweet "i lov u" from my wife. haaaayyy =)

This is my New Year's day story and unexpectedly ubuntu is the hero. =)

---

### Post by MisterPitt on 2011-04-12
Let me ask, do USB wifi devices work in Ubuntu ?

I have a Smart Bro Plug-It kit like the on [here]("http://smart.com.ph/bro")

---

### Post by Script Warlock on 2011-04-12
> **MisterPitt said:**
> Let me ask, do USB wifi devices work in Ubuntu ?

I have a Smart Bro Plug-It kit like the on [here]("http://smart.com.ph/bro")

if you mean usb prepaid yes i have and 100% working only lang your balance inquiry is thru web connect ng smartbro.

---

### Post by pinoyskull on 2011-04-13
of course it will work :)

---

### Post by Ravskie on 2011-04-14
> **MisterPitt said:**
> Let me ask, do USB wifi devices work in Ubuntu ?

I have a Smart Bro Plug-It kit like the on [here]("http://smart.com.ph/bro")

of course 100% working po ...

---

### Post by MisterPitt on 2011-04-14
Ayos ! Hehe

Its a good thing gumagana yung Smart Bro Plug-It sa Ubuntu :D

---

### Post by MisterPitt on 2011-04-19
Its a good thing na puwede ang Smart Bro Plug-It with Ubuntu. May signal kasi siya kahit saan plus the [rates ]("http://smart.com.ph/bro/services/unlisurf.htm")are pretty affordable :KS

---

