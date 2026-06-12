---
title: "[all variants] HowTo set OpenDNS as DNS in DHCP env"
date: 2008-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by dentaku65 on 2008-07-28
Due to the recent vulnerability in the worldwide DNS
[http://www.vnunet.com/vnunet/news/2222592/first-dns-attacks-reported]("http://www.vnunet.com/vnunet/news/2222592/first-dns-attacks-reported")
[http://www.doxpara.com/?p=1189]("http://www.doxpara.com/?p=1189")
can be useful to change the DNS provided by your provider and use [OpenDNS]("http://opendns.org/") instead.

By the moment you can check if your actual DNS are vulnerable:
[http://www.doxpara.com/]("http://www.doxpara.com/")

Here is described two ways to do it for DHCP users and without touching the router configuration (for users that have a static IP is pretty straightforward).

**Install a simple editor**
Install Scite to simplify and unify the editing for all *ubuntu distros.
```
sudo apt-get install scite
```

The **first **option change permanently the DNS
The **second **option change the DNS "when you need" 


**1) Change DNS permanently**
Edit the dhcp configuration file:
```
sudo scite /etc/dhcp3/dhclient.conf
```
Add this line at the end and save the file:
```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```

Reboot your machine.

Then try a non-existent url like:
[http://seeifthednsischangednow.com]("http://seeifthednsischangednow.com")
You should reach an OpenDNS response as search result in the OpenDNS home page... well you are using OpenDNS DNS.

**2 Change DNS when you need**
Create a file in your home:
```
scite ~/resolv.conf
```
Write the DNS IP of OpenDNS and save it:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```
Create a file under /usr/bin
```
sudo scite /usr/bin/dnsrenew
```
Write the following and save it
```
cp ~/resolv.conf /etc/resolv.conf
/etc/init.d/networking restart
```
Then chmod it to create an executable file:
```
sudo chmod +x /usr/bin/dnsrenew
```
Execute the script:
```
sudo dnsrenew
```
Then try a non-existent url like:
[http://seeifthednsischangednow.com]("http://seeifthednsischangednow.com")

Now you can use the DNS provided by OpenDNS till the next reboot.

**The Samba fix with OpenDNS (or external DNS)**
If you are using Samba (as supposed to be) and you are using the DNS of OpenDNS (or any external dns), you must change the configuration of Samba in order to be able to browse your LAN; so, edit your configuration file in this way:
```
sudo scite /etc/samba/smb.conf
```
and change the line of the *name resolver* section in this way:
```
name resolve order = lmhosts bcast wins host
```
Save and close the file
Then restart Samba:
```
sudo /etc/init.d/samba restart
```
Wait 10/15 minutes and you are able to browse your LAN with the new DNS.

I write this little HowTo just to use OpenDNS because I appreciate their service, I'm not involved in OpenDNS team.

---

### Post by Oldsoldier2003 on 2008-07-28
Temporarily stickied. dentaku, check your Pms :)

---

### Post by hito1 on 2008-07-31
Thanks.

Is this easy to be undone when my DNS gets patched? How?

---

### Post by dentaku65 on 2008-07-31
Yes it is. If you choose the first option just edit the dhclient.conf
```
sudo nano /etc/dhcp3/dhclient.conf
```
and change this line
```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```
with this line
```
#prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```
Reboot your box.

If you choose second option, just reboot the box.

---

### Post by hito1 on 2008-08-01
Thanks again!

---

### Post by andrek on 2008-08-03
Also, if you're having your IP changing every day at midnight for example or it changes every time you disconnect and connect your router - here's my tip how to keep OpenDNS up-to-date with our IP.

First of all, install inadyn :
```
sudo apt-get install inadyn
```
Then, edit /etc/inadyn.conf file :
```
sudo gedit /etc/inadyn.conf
```
Paste there following content :
```

--username YOURUSERNAME
--password YOURPASSWORD
--alias all.dnsomatic.com
--dyndns_server_name updates.dnsomatic.com
--dyndns_server_url /nic/update?

```
As you can see, it uses [www.dnsomatic.com](www.dnsomatic.com) - it's a website related to OpenDNS, so go there and check if you're not registered already. If not, do it ( I haven't got to, I think while registering on opendns.com you're also getting an account on dnsomatic.com ). Then, create a service for your OpenDNS account - remember to set up your network's label ( you may check it on [https://www.opendns.com/dashboard/networks/](https://www.opendns.com/dashboard/networks/) , it's Home by default ).
If dnsomatic says your service is not active, press ALT F2 and type in : inadyn
You won't get any message during this, so go check on dnsomatic again if it's active. You might noticed that inadyn send some information to dnsomatic and opendns about your IP, so that's the job it does. You can add inadyn to your Session as a startup app.

Sorry for littering your topic, dentaku65 - but I find this usable.

By the way, shouldn't this topic be moved to Tutorials & Tips section as a HOWTO guide?

---

### Post by dentaku65 on 2008-08-03
> **andrek said:**
> 
As you can see, it uses [www.dnsomatic.com](www.dnsomatic.com) - it's a website related to OpenDNS, so go there and check if you're not registered already. If not, do it ( I haven't got to, I think while registering on opendns.com you're also getting an account on dnsomatic.com ). Then, create a service for your OpenDNS account - remember to set up your network's label ( you may check it on [https://www.opendns.com/dashboard/networks/](https://www.opendns.com/dashboard/networks/) , it's Home by default ).
If dnsomatic says your service is not active, press ALT F2 and type in : inadyn
You won't get any message during this, so go check on dnsomatic again if it's active. You might noticed that inadyn send some information to dnsomatic and opendns about your IP, so that's the job it does. You can add inadyn to your Session as a startup app.

Sorry for littering your topic, dentaku65 - but I find this usable.

By the way, shouldn't this topic be moved to Tutorials & Tips section as a HOWTO guide?

Yes, I see, I did'n knew dnsomatic (and is related to no-ip too where I have an account); but if you have more than a machine in your lan you must provide an account for any machine (I think); basically this HowTo consider:
[LIST]
[*]A quick way to use OpenDNS
[*]Do not change Router Configuration
[*]Simplicity (IMHO)
[/LIST]

This HowTO was written for the section of Tutorials but in some way did not respect all the criteria for posting there, anyway the Ubuntu Forum Staff sticked here and invited me to rewrite in the proper way for the Tutorial section.

---

### Post by Sef on 2008-08-03
Moved to Tips and Tutorials.

---

### Post by niccholaspage on 2008-08-08
I tried this on my laptop and everything is fine except my speed is still going the same.It starts out fast than goes down to my normal speed and sometimes even slower.I'm trying this by downloading a Xubuntu ISO from the US Mirror.
EDIT:I also tried changing the DNS in my router configuration but it still won't work.

---

### Post by talktorishav on 2008-09-06
why scite?

---

### Post by cjawcrusher512 on 2008-09-09
[[size=2][color=#006699]How to buy a ball mill with quality at reasonable price in China  ?[/color][/size]](http://answers.yahoo.com/question/index?qid=20080826203448AAVEOrl)

---

### Post by dentaku65 on 2008-09-11
> **talktorishav said:**
> why scite?

Why? It's simple:
vi and nano are too complicated for beginners
gedit is present only in Gnome env
kate is present only in KDE env
mousepad is present only in Xfce env

That's why scite.

---

### Post by tm002ly on 2008-10-10
&#23567;&#30333;&#33258;&#20174;&#37027;&#27425;&#8220;&#39321;&#28207;&#20845;&#21512;&#24425;&#8221;&#20107;&#20214;&#21518;&#65292;&#27599;&#22825;&#37117;&#38506;&#30528;&#25105;&#65292;&#32780;&#19988;&#26102;&#38388;&#36234;&#26469;&#36234;&#38271;&#65292;&#19981;&#36807;&#24120;&#24120;&#22312;&#19981;&#33258;&#35273;&#38388;&#23601;&#20250;&#39078;&#30528;&#30473;&#24551;&#37057;&#22320;&#30475;&#30528;&#25105;&#12290;&#25105;&#35828;&#31505;&#35805;&#36887;&#20182;&#20063;&#26410;&#33021;&#20351;&#20182;&#24320;&#24576;&#65292;&#34429;&#26159;&#36731;&#26366;&#36947;&#20154;&#21644;&#30333;&#23567;&#22992;&#30473;&#23431;&#38388;&#30340;&#31070;&#20260;&#65292;&#31505;&#24847;&#20877;&#20063;&#19981;&#33021;&#21040;&#36798;&#30524;&#24213;[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gz.cn)[&#20845;&#21512;&#24425;](http://www.tm203.sc.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.gx.cn)[&#20845;&#21512;&#24425;](http://www.tm203.gd.cn)[&#39321;&#28207;&#20845;&#21512;&#24425;](http://www.tm203.hn.cn)

---

### Post by Megatog615 on 2008-10-16
I wish I could thank you for your Samba fix, but the icon is missing. I have been troubleshooting the Samba issue for months now.

---

### Post by bionnaki on 2008-10-18
> **niccholaspage said:**
> I tried this on my laptop and everything is fine except my speed is still going the same.It starts out fast than goes down to my normal speed and sometimes even slower.I'm trying this by downloading a Xubuntu ISO from the US Mirror.
EDIT:I also tried changing the DNS in my router configuration but it still won't work.

opendns does not speed up downloading such things as .iso's 

opendns will speed up dns resolution (page retrieval speed, basically).

---

### Post by bionnaki on 2008-10-18
instructions are also up on the opendns website: 

[ubuntu]("https://www.opendns.com/homenetwork/start/device/ubuntu")

[routers]("https://www.opendns.com/homenetwork/start/router/")

---

### Post by 080812jk on 2008-10-30
&#29627;&#29827;&#33410;&#33021;&#24212;&#29992;&#26032;&#25216;&#26415;[**&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)  &#22312;&#24314;&#31569;&#33410;&#33021;&#20013;[**&#24314;&#31569;&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)&#26159;&#19968;&#20010;&#38750;&#24120;&#34180;&#24369;&#32780;&#19988;&#24120;&#24120;&#36739;&#26131;&#20026;&#20154;&#24573;&#35270;&#30340;&#37325;&#35201;&#29615;&#33410;&#65292;&#20294;&#21516;&#26102;&#20063;&#26159;&#24314;&#31569;&#33410;&#33021;&#24037;&#20316;&#20013;&#22823;&#26377;&#28508;&#21147;&#21487;&#25366;&#20043;&#22788;&#12290;&#30446;&#21069;&#25105;&#22269;&#35768;&#22810;&#32769;&#24314;&#31569;&#22312;&#22823;&#37327;&#20351;&#29992;&#35013;&#26377;&#26222;&#36890;&#36879;&#26126;&#29627;&#29827;&#30340;&#38050;&#31383;&#12289;&#38109;&#31383;&#65292;&#21363;&#20351;&#26159;&#36817;&#20960;&#24180;&#30340;&#26032;&#24314;&#31569;&#20013;&#65292;&#23588;&#20854;&#27665;&#29992;&#20303;&#23429;&#30340;&#38376;&#31383;&#20173;&#28982;&#22823;&#37327;&#20351;&#29992;&#26222;&#36890;&#36879;&#26126;&#29627;&#29827;&#12290; &#12288;&#12288;&#22312;&#21335;&#26041;&#22320;&#21306;&#28459;&#38271;&#30340;&#22799;&#23395;&#20013;&#65292;&#26085;&#29031;&#20805;&#36275;&#65292;&#27668;&#28201;&#26102;&#24120;&#37117;&#22312;30&#8451;&#20197;&#19978;&#65292;&#30333;&#22825;&#23460;&#22806;&#30340;&#22826;&#38451;&#28909;&#36752;&#23556;&#22823;&#22810;&#26159;&#36890;&#36807;&#29627;&#29827;&#38376;&#31383;&#36827;&#20837;&#23460;&#20869;&#20351;&#23460;&#28201;&#21319;&#39640;&#65292;&#38656;&#35201;&#21152;&#22823;&#21046;&#20919;&#36127;&#33655;&#25269;&#28040;&#28909;&#37327;&#12290;&#22812;&#38388;&#23460;&#20869;&#30340;&#21046;&#20919;&#33021;&#37327;&#22823;&#37117;&#26159;&#36890;&#36807;&#29627;&#29827;&#38376;&#31383;&#27969;&#22833;&#30340;&#65292;&#20174;&#32780;&#22823;&#22823;&#22686;&#21152;&#20102;&#33021;&#28304;&#28040;&#32791;&#65292;&#36825;&#23601;&#26159;&#36896;&#25104;&#24314;&#31569;&#29289;&#20351;&#29992;&#33021;&#32791;&#39640;&#30340;&#30452;&#25509;&#21407;&#22240;&#12290;&#26377;&#25928;&#30340;&#35299;&#20915;&#21150;&#27861;&#20043;&#19968;&#26159;&#37319;&#29992;&#26032;&#22411;&#30340;[**&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)&#65292;&#23613;&#37327;&#20943;&#20302;&#22826;&#38451;&#33021;&#36752;&#23556;&#30340;&#36879;&#36807;&#29575;&#12290;&#12288;&#12288;&#20154;&#20204;&#20063;&#35768;&#27880;&#24847;&#21040;&#25105;&#22269;&#24314;&#31569;&#38376;&#31383;&#25152;&#29992;&#30340;[**&#24314;&#31569;&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)&#65292;&#27491;&#32463;&#21382;&#30528;&#20174;&#26222;&#36890;&#30333;&#29627;&#29827;-&#36739;&#28145;&#39068;&#33394;&#30340;&#21560;&#28909;&#29627;&#29827;&#65288;&#20439;&#31216;&#33590;&#33394;&#29627;&#29827;&#65289;-&#27973;&#32511;&#33394;&#21560;&#28909;&#29627;&#29827;&#21450;[**&#29627;&#29827;&#36148;&#33180;**](http://www.moor88.com/)-&#27973;&#32511;&#33394;&#20013;&#31354;&#29627;&#29827;&#36825;&#26679;&#19968;&#20010;&#21457;&#23637;&#36807;&#31243;&#12290;&#30001;&#20110;&#27973;&#32511;&#33394;&#29627;&#29827;&#20215;&#24265;&#21448;&#30053;&#26377;&#19968;&#23450;&#30340;&#38548;&#28909;&#25928;&#33021;&#65292;&#27491;&#34987;&#22823;&#37327;&#29992;&#20110;&#26222;&#36890;&#20303;&#23429;&#38376;&#31383;&#19978;&#65292;&#32780;&#20013;&#31354;&#29627;&#29827;&#30001;&#20110;&#20855;&#26377;&#33391;&#22909;&#30340;&#38548;&#38899;&#38548;&#28909;&#24615;&#33021;&#65292;&#21017;&#36880;&#27493;&#34987;&#29992;&#20110;&#26032;&#24314;&#30340;&#39640;&#26723;&#35946;&#23429;&#38376;&#31383;&#19978;&#65292;&#20294;&#20854;&#26114;&#36149;&#30340;&#20215;&#26684;&#20063;&#21046;&#32422;&#20102;&#26222;&#21450;&#25512;&#24191;&#12290;&#32780;&#19988;&#19978;&#36848;&#21508;&#31181;&#29627;&#29827;&#37117;&#36824;&#26377;&#19968;&#20010;&#26222;&#36890;&#29627;&#29827;&#26368;&#33268;&#21629;&#30340;&#24369;&#28857;&#21363;&#26131;&#33030;&#26131;&#30862;&#65292;&#20134;&#21363;&#26159;&#29627;&#29827;&#30340;&#23433;&#20840;&#24615;&#33021;&#20302;&#12290;

---

### Post by nu2this on 2008-11-01
THANK YOU!!! dentaku65!!!:D 
The inability of Ubuntu to retain the Opendns servers was the reason I left back at Edgy. Now thanks to your post here I've returned to Ubuntu with Intrepid. I'll be happy relearning Ubuntu and rediscovering what I loved about it. As soon as I find out to add a thanked in post I'm putting one in for you! Once again THANKS!
Finally, if anyone here wants/needs Opendns and you use Intrepid Ibex if you're not sure how to do it go to the start of this thread. IT WORKS!!!

---

### Post by gabo.cr on 2009-02-12
I love this How-to !

The first option makes sense if you only have one computer and if you are not the administrator of the network. I had no idea how to do that.

But if you are the administrator of the network, I think the best option is to use OpenDNS in the router.
:P

---

### Post by grndslm on 2009-03-25
I'd say my solution is a bit simpler, and certainly not as biased toward a specific editor!!

[http://ubuntuforums.org/showthread.php?t=1073838](http://ubuntuforums.org/showthread.php?t=1073838)  -- Scroll down to the "STATIC DNS (OpenDNS), EVEN WITH DHCP" section.

I'm creating my own distribution, so this way I have control over numerous machines' default settings, but not necessarily control over the routers that these machines are using... so this is the way to go.  Laptops that move between many wireless networks definitely benefit from this.  In most other situations, just changing the router's settings is the way to go.

---

