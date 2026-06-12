---
title: "My IP keeps on changing"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by rozan on 2008-10-03
I have this strange problem, I use ADSL and my ip keeps on changing so i cannot login to any blog site or forums. I cannot use FTP. I found application called 'Hotspot shield' buts works for only windows. Can i have similar kind of application for ubuntu?
Thnx

---

### Post by epidemiks on 2008-10-03
I'm not sure about software to help that, but your ISP may be able to give you a static ip.
But then I've always had dynamic IP's, and I've never had a browsing/login problem because of it.

---

### Post by lisati on 2008-10-03
I, too, have had dynamic IPs on my ADSL connection, and haven't had a problem with it changing all the time. If it's happening quite often (more than, say, once every few days), it could be a sign that there's a problem with the connection between your modem and your ISP - my connection has been known to go haywire when water has found its way into the underground cables on the street (since fixed by the local telephone company)

---

### Post by jerome1232 on 2008-10-03
That's kind of how it works, I've noticed using adsl my ip changes more frequently than it did using a cable connection (probably due to ppoe re-authentication happening in the background every so often). But it's about every 3 - 5 days that it happens.

As lisati said if it's changing multiple times in a day. I'll bet your connection is dropping and getting required.

---

### Post by iponeverything on 2008-10-03
> **epidemiks said:**
> I'm not sure about software to help that, but your ISP may be able to give you a static ip.
But then I've always had dynamic IP's, and I've never had a browsing/login problem because of it.

Question from Location: Kathmandu

Answer from Location: Melburn

Kathmandu -- bandwidth scarce and expensive -- as a provider do everything you can to break torrents other bandwidth hogs.

Melburn   -- bandwidth is good -- as a provider, try not to tick off your customers too much.

---

### Post by lisati on 2008-10-03
> **iponeverything said:**
> Question from Location: Kathmandu

Answer from Location: Melburn

Kathmandu -- bandwidth scarce and expensive -- as a provider do everything you can to break torrents other bandwidth hogs.

Melburn   -- bandwidth is good -- as a provider, try not to tick off your customers too much.

Well spotted: people in different places seem to get different quality service.

---

### Post by lovinglinux on 2008-10-03
You should check if your browser is accepting cookies, which is the most probable cause of login problems. Even if your IP changes several times a day you should be able to login on web sites and stay logged as long as you keep the browser open. 

Depending on how you and the site configure cookies expiration, you can stay logged almost forever, even if you change your IP several hundred times.

---

### Post by hyper_ch on 2008-10-03
well, I get my dyn IP changed something between 1x per day and 1x per month...

are you sure it's the external IP that changes and not the internal IP? I noticed on Ibex that the IP often gets resetted (Kubuntu Ibex)... I uninstalled the network manager completely and use now [WICD]("http://wicd.sourceforge.net/").

That seems to have helped.

So, plz verify whether it's your external IP (assigend by your ISP) that keeps changing or your internal one.

---

### Post by rozan on 2008-10-03
> **hyper_ch said:**
> well, I get my dyn IP changed something between 1x per day and 1x per month...

are you sure it's the external IP that changes and not the internal IP? I noticed on Ibex that the IP often gets resetted (Kubuntu Ibex)... I uninstalled the network manager completely and use now [WICD]("http://wicd.sourceforge.net/").

That seems to have helped.

So, plz verify whether it's your external IP (assigend by your ISP) that keeps changing or your internal one.

Its not 1 per day or 1 per month its like 2-5 every minute. All of my friends who are using ADSL have same problem. My ISP suggest me for application called 'Hotspot shiel' which gives u kinda fake stable IP but this works in windows only not for me.

---

### Post by shifty_powers on 2008-10-03
> **hyper_ch said:**
> well, I get my dyn IP changed something between 1x per day and 1x per month...

are you sure it's the external IP that changes and not the internal IP? I noticed on Ibex that the IP often gets resetted (Kubuntu Ibex)... I uninstalled the network manager completely and use now [WICD]("http://wicd.sourceforge.net/").

That seems to have helped.

So, plz verify whether it's your external IP (assigend by your ISP) that keeps changing or your internal one.

funny, but i had to uninstall knetwork manager and install wicd... knetwork would no do anything with my wireless, but wicd worked straight off..

only thing i haven't liked about kubuntu 8.10. hope they sort out the bugs in it :D

---

### Post by billgoldberg on 2008-10-03
> **rozan said:**
> I have this strange problem, I use ADSL and my ip keeps on changing so i cannot login to any blog site or forums. I cannot use FTP. I found application called 'Hotspot shield' buts works for only windows. Can i have similar kind of application for ubuntu?
Thnx

You most likely have a dynamic IP.

But then so do I and never have any problems.

The login on sites and forums are stored in cookies in your browser and don't have anything to do with your ip.

Do you have cookies enabled?

---

### Post by Sycron on 2008-10-03
Do you need a port forwarding ?

---

### Post by billgoldberg on 2008-10-03
> **rozan said:**
> Its not 1 per day or 1 per month its like 2-5 every minute. All of my friends who are using ADSL have same problem. My ISP suggest me for application called 'Hotspot shiel' which gives u kinda fake stable IP but this works in windows only not for me.

What?

2 - 5 times a minute.

Amateurs.

I can imagine you don't get very high speeds on torrent downloads :p .

Normally a dynamic ip addres should only a few times a month. Depending on how much times you reset your router (don't know with modems).
--

I'm not really good in these kind of things, but shouldn't a service like opendns.com help in your case?

---

### Post by hyper_ch on 2008-10-03
2-5 times every minute cannot be real... can you please verify that you have every every minute another IP address? -->  [http://www.whatismyip.com/](http://www.whatismyip.com/)

---

### Post by lovinglinux on 2008-10-03
Is this the application called "Hotspot shield"?

[IMG]http://superdownloads.uol.com.br/imagens/screenshots/6/1/61699,2.jpg[/IMG]

I never used a VPN and I'm not sure about all this crazy ip changes thing, but I guess the problem is that the internal IP changes so frequently that the router can't keep the connections from/to your machine alive. If this is even possible.

I'm totally guessing, but maybe the VPN application creates a "fake" static internal IP, so that the router always forward the requests to the correct machine.

If this is the case, I guess you could achieve the same result of the "Hotspot shield" using any VPN setup on Ubuntu. But I would advise you to call the ISP support and demand a fix on their side. You are a costumer and I bet the service is not cheap, so you should receive a decent service.

---

### Post by nowshining on 2008-10-03
some sites have a option when logging in to only accept logins from a certain ip, some are checked by default and some are not... This option is suppose to provide better security from crackers... Always make sure if there is one it is NOT checked..

---

### Post by rozan on 2008-10-03
> **hyper_ch said:**
> 2-5 times every minute cannot be real... can you please verify that you have every every minute another IP address? -->  [http://www.whatismyip.com/](http://www.whatismyip.com/)

ok i visited this site and it shows different IP every time i refresh it.

---

### Post by rozan on 2008-10-03
> **lovinglinux said:**
> Is this the application called "Hotspot shield"?

[IMG]http://superdownloads.uol.com.br/imagens/screenshots/6/1/61699,2.jpg[/IMG]

I never used a VPN and I'm not sure about all this crazy ip changes thing, but I guess the problem is that the internal IP changes so frequently that the router can't keep the connections from/to your machine alive. If this is even possible.

I'm totally guessing, but maybe the VPN application creates a "fake" static internal IP, so that the router always forward the requests to the correct machine.

If this is the case, I guess you could achieve the same result of the "Hotspot shield" using any VPN setup on Ubuntu. But I would advise you to call the ISP support and demand a fix on their side. You are a costumer and I bet the service is not cheap, so you should receive a decent service.

yup this is the application i'm taking about.
It would be just waste of time if i call my ISP to fix it. They dont have any solution for this.
Can u suggest me any VPN setup for ubuntu.

---

### Post by hyper_ch on 2008-10-03
> **rozan said:**
> ok i visited this site and it shows different IP every time i refresh it.

now that really sux... ask your ISP what they update the IP this quickly.

---

### Post by lovinglinux on 2008-10-03
> **rozan said:**
> yup this is the application i'm taking about.
It would be just waste of time if i call my ISP to fix it. They dont have any solution for this.
Can u suggest me any VPN setup for ubuntu.

Unfortunately, I know nothing about VPN but I'm sure someone will help you. A quick search on the forums revealed the existence of [openvpn]("http://ubuntuforums.org/search.php?searchid=48987568").

---

