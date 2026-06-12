---
title: "Deluge Help/Torrent Help"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by BluePlum on 2008-07-12
Don't need major help, Just need to no how to use Deluge. It's pretty confusing for me. All i want to do is no how to start and stop a torrent automatically. But i need to set maximum upload speed and download speed etc etc... Then i found out it could use a block list like peer guardian, Or use a proxy somehow.... Can someone give me a quick tutorial? 

If anyone knows how to start and stop torrents automatically in AUTOMATIC this would be very helpful o.o

thankyou

---

### Post by boblemur on 2008-07-12
i use azureus which i recommend, its reasonably easy to use, you can set a default location and it will automaticly add, you can go into settings and set a global upload limit and download limit...

the proxy is easy enough to setup

im not sure about peer guardian because i dono what that is...

but make sure u select advanced mode so that it shows u all the options...

the onlything that i dont like about it is... you need java and it can be a lil bit of a hog sometimes...

---

### Post by philinux on 2008-07-12
According to all I've read on here, Azureus is buggy and a resource hog because it uses java. I'm sure some people really like it. As they are all free try them out.

Deluge just works away in the background and is very light on resources.

FAQ's just about have it all covered.

[http://deluge-torrent.org/faq.php](http://deluge-torrent.org/faq.php)

---

### Post by quantumstitch on 2008-07-12
i use deluge to manage my torrents. for autostarting, i use ted (only works for tv shows). however, auto stop is easy.

open deluge, click Edit->Preferences. click the Seeding tab. you can select to stop seeding at a given share ratio (i use 1.0) and you can select to clear torrents after they reach that share ratio.

hope this helps.

---

### Post by ugm6hr on 2008-07-12
I'm a bit confused about what you are trying to achieve with deluge.

It is the best torrent engine for Gnome as far as I'm concerned.  Get the latest version in an Ubuntu .deb from their homepage.

Not sure what you mean by start and stop automatically.  Obviously, the point of peer-sharing is that you leave everything up/down-loading indefinitely.

The preferences will allow you to set the maximum upload and download speeds (dependent on your bandwidth availability).  On a UK ADSL line, I use 5-10 upload and 20-40 download (depending on whether there is anyone else trying to use the internet).

You can also limit the number of "open" torrents, and deluge will allow you to send a torrent to the bottom of the list when downloaded (which, if you have more torrents in the queue, will make it stop (or wait in the queue).

Deluge has lots of other features too, which may or may not be important.

If none of this makes any sense, then I suspect you need to do some research on peer-sharing and torrents in general.

If there is a specific reason you are asking about proxies etc - please elucidate (since most home users don't need to use a proxy).

---

### Post by BluePlum on 2008-07-12
Why would i want to stop and start torrents? because i start my torrents automatically at the start of off peak and stop them at the end of off peak so i don't go over my cap. 

thanks for the help guys

---

### Post by Kai-vana on 2008-07-12
I use Utorrent in wine as it lets you set speeds bast on the time and day of the week. I have it set so during the middle of the night and day I'm Uploading downloading at fall speed but in the evening it automatically changes upload/download speeds to that of a dielup connection.

---

### Post by Elfy on 2008-07-12
There is a scheduler plugin for deluge - Edit - Plugins, that should work for you, the similar one in ktorrent does fine for me.

> ( well most of you be sept the last post )Was there a need for that:(

---

### Post by BluePlum on 2008-07-12
I'm in the scheduler add on of deluge. Does the Upload and download limit is set default on -1. Does this mean unlimited?

---

### Post by Elfy on 2008-07-12
I expect so - that's normally the way, I just downloaded it to look for you as I thought there was a plugin, it's gone again now.

---

### Post by philinux on 2008-07-12
open deluge, select preferences, then plugins tab. Tick scheduler then it's prefs for the dialog window.

---

### Post by BluePlum on 2008-07-12
> **philinux said:**
> open deluge, select preferences, then plugins tab. Tick scheduler then it's prefs for the dialog window.

does the scheduler take time to update? Or it isn't working...

---

### Post by philinux on 2008-07-12
[http://www.thinkdigit.com/details.php?article_id=2465](http://www.thinkdigit.com/details.php?article_id=2465)

Scroll down for the scheduler bit.

I've never used it. If you need more help I post in the deluge site forum.

---

### Post by ugm6hr on 2008-07-12
> **BluePlum said:**
> does the scheduler take time to update? Or it isn't working...

Just turn the relevant time slots red (to stop torrents).

See the picture for an example of stopping M-F 5-12pm.

If it doesn't work right away, try restarting Deluge.

---

### Post by BluePlum on 2008-07-12
hooray it worked! Now when i download something VIA torrent i don't go over my limit because it does it at 1AM! 

thank you guys

---

### Post by the_red_devil on 2008-07-13
i dont know how to use the scheduler in KTorrent.......:( please help me guys ......i DL around a 141GB of torrents per month via uTorrent on Windows but on Ubuntu i dont even knw how to use the scheduler :| please help me....as i can only download from 2AM-8AM and as i cant stay up for so much, i need a scheduler :)

-thanks in advance

---

### Post by BluePlum on 2008-07-13
what torrent do you use on ubuntu? I don't torrent on windows incase someone puts a trojan into a game demo :(.

---

### Post by BluePlum on 2008-07-14
I've disabled uploading in deluge but it still uploads... What to do?

---

### Post by Inxsible on 2008-07-14
> **BluePlum said:**
> what torrent do you use on ubuntu? I don't torrent on windows incase someone puts a trojan into a game demo :(.
rTorrent  FTW !!

Simple but powerful !!

Have a look here to see what it can do.

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

### Post by BluePlum on 2008-07-14
i just spent all that time setting up deluge... not switching lol

---

### Post by BluePlum on 2008-07-15
I've disabled uploading in deluge but it still uploads... What to do?

---

### Post by hyper_ch on 2008-07-15
if nobody would upload then you couldn't download anymore ;)

---

### Post by BluePlum on 2008-07-15
> **hyper_ch said:**
> if nobody would upload then you couldn't download anymore ;)

no i always upload heaps but for some reason in deluge when i have it on my internet go's really slow.  And i think it's the uploading and i cant disable it :?

---

### Post by hyper_ch on 2008-07-15
> **BluePlum said:**
> I've disabled uploading in deluge

well, so much to uploading heaps ;)

---

### Post by BluePlum on 2008-07-15
Ive disabled it but it  still does it....

---

### Post by hyper_ch on 2008-07-15
to not having any other issues, limit upload to about max. 90% of your upload speed...

and do you have according ports forwarded from your router to your computer or did you enable UPnP on the router or do you have a firewall?

---

### Post by ugm6hr on 2008-07-15
> **BluePlum said:**
> no i always upload heaps but for some reason in deluge when i have it on my internet go's really slow.  And i think it's the uploading and i cant disable it :?

Torrents are not designed for downloads only.  Just limit the upload speed to something sensible (I use 5k when I'm using the internet).

You can use scheduler to adjust the "peak" and "off-peak" settings.

---

### Post by BluePlum on 2008-07-15
Do i need to forwed ports?

I set the upload 2 1kb's instead of 0 and now it seems not to be passing 1kb's

---

### Post by hyper_ch on 2008-07-16
well, you do need to forward ports if you are behind a router and if that router does not have UPnP enabled....

---

### Post by BluePlum on 2008-07-16
*sigh* UPnP?

---

### Post by hyper_ch on 2008-07-16
UPnP is pretty evil in conjunction with some OSes (M$). Basically the router will try then to automatic portforward stuff... otherwise you'll have to manually forward the according ports that are being used.

---

### Post by BluePlum on 2008-07-16
I don't think it has UPnP i did portforwedding once for a steam server which didn't work.... But the torrent currently downloads fine so do i needa port forwed?

---

### Post by joe3204 on 2008-07-26
has anybody used delige behind a proxy??? even after specifying the proxy settings, i cannot seem to download anything!!!

---

### Post by BluePlum on 2008-07-26
How do i use it behind proxy settings and i'll see if mine works :). Also, Your Sig is the lamest joke ever... :)

---

### Post by expatCM on 2008-07-29
Does anyone happen to know how to get available plug-ins?

I see in this thread mention of the Scheduler plug-in.  I only appear to have the Test, Block List and Label plug-ins.  How did everyone get the scheduler plug-in and any others?

---

### Post by ugm6hr on 2008-07-29
> **expatCM said:**
> I see in this thread mention of the Scheduler plug-in.  I only appear to have the Test, Block List and Label plug-ins.  How did everyone get the scheduler plug-in and any others?

Plugins are in Preferences.

However, I have noticed that the interface and plugins have changed since 0.5.9.3 to RC3, with a loss of all the plugins.

Hopefully they will return with the final version.

---

### Post by mtopro on 2008-07-29
> **BluePlum said:**
> I'm in the scheduler add on of deluge. Does the Upload and download limit is set default on -1. Does this mean unlimited?

Yes, -1 means unlimited bandwidth.  I tweak the upload to max 15-20kb.  This keeps it from getting out of hand.

Also my two cents... I like the deluge package that comes standard with Ubuntu version 0.5.8.9  The newer version is a resource hog. So is KTorrent.  The standard version does everything I could need with minimum use of my CPU. It also gets the highest download speeds in comparison with the other versions.

The only other item I would tweak is under plugins add the blocklist importer.  You will have to add the URL which does not come stock.  Add  "http://www.bluetack.co.uk/config/nipfilter.dat.gz"  into the Blocklist URL and it should download the list and enable it from there.

There are a lot of other plugins you can play with and in my analysis it outperforms the others... Even the latest version.

You can use a the new Deluge or Ktorrent through TOR as a IP mask, but I have read it is unethical due to the draw it puts on the TOR network..  Plus its tough setting up and really slow when you do get it!  
hth :)

---

### Post by nycste on 2008-07-29
deluge knocked my internet out nonstop

anyone else confirm this...

transmission didnt or doesnt, soo explain plzzz


on a side note, my modem died yesturday, i replaced it, im tempted to try deluge again

i used utorrent in windows, i used abc for the last 5years but it never got updated, but still worked fine, azureous like someone said was always bloated and written in java ewww esp in linux

---

