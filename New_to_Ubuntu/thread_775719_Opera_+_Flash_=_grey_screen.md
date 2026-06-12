---
title: "Opera + Flash = grey screen"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by terrordrone on 2008-04-30
Opera doesnt seem to play videos or any flash content...

i have flashplugin-nonfree installed.. and works with firefox..

I have attached the plugins recognised by opera

Thanks in advance

---

### Post by terrordrone on 2008-04-30
bump...

---

### Post by billgoldberg on 2008-04-30
I don't use opera so I haven't come across the problem but this seems relevant:

[http://sysblogd.wordpress.com/2007/08/01/opera-flash-and-ubuntu-feisty-fawn-gutsy-gibbon-and-hardy-heron-also/](http://sysblogd.wordpress.com/2007/08/01/opera-flash-and-ubuntu-feisty-fawn-gutsy-gibbon-and-hardy-heron-also/)

---

### Post by gandaran on 2008-04-30
if you type opera in the search box, you get tons of answers to you problem,
every day someone comes along with the same problem.
anyway,the opera version in the repositories doesn't work with the latest flash,I suggest you download the 9.50b2 version form opera site [http://www.opera.com/download/?ver=9.50b2](http://www.opera.com/download/?ver=9.50b2), it'll work with the flash version installed in mozilla firefox, but also doesn't work with the totem plugins, you can change totem for any other plugin, vlc, mplayer or xine plugin

---

### Post by mano cazalet on 2008-04-30
as said before only the new betas 9.50 work with the current flash,
if you want to use the official opera release (9.27 i believe) you have to install the previous flash plugin, version 9.0.48

[http://ubuntuforums.org/showthread.php?t=745325](http://ubuntuforums.org/showthread.php?t=745325)

---

### Post by terrordrone on 2008-04-30
Thanks for your replies

k.. now i uninstalled the Opera 9.26 and put in the 9.50b
If i open that... it closes after a few seconds.. sometimes.. 1 sometimes 2-3.. 

dont know whats happened

---

### Post by gandaran on 2008-04-30
you have to delete the old home/user/.opera folder, the 9.50 is very different, so it doesn't open due to old settings in the opera folder

---

### Post by Mason Smith on 2008-04-30
When I was running Freebsd 7.0 I had to use flash player 7 with opera in order to watch flash videos. Anything newer than 7 would close the browser within seconds of starting the video. Now there is no flash player support for Freebsd so this was away around that but switching to version 7 may work for you.

---

### Post by terrordrone on 2008-04-30
I did that.. it asked me to accept the agreement.. then it closes after a few seconds :(

But if i remove .opera and uninstall ( when 9.50b2 is installed.. ).. and put back 9.26.. it starts working.. 

if i do the same when 9.26 is installed.. removing the folder and uninstalling it.. and put 9.50b2.. it closes.. as it is happening now

---

### Post by gandaran on 2008-04-30
> **terrordrone said:**
> I did that.. it asked me to accept the agreement.. then it closes after a few seconds :(

But if i remove .opera and uninstall ( when 9.50b2 is installed.. ).. and put back 9.26.. it starts working.. 

if i do the same when 9.26 is installed.. removing the folder and uninstalling it.. and put 9.50b2.. it closes.. as it is happening now

never seen this problem! try starting opera on the terminal, if it shows any errors post them back here, try also opera as root « sudo opera »


edit:
did you downloaded the correct opera ubuntu version, 7.10 or 8.04 ?

---

### Post by Barrucadu on 2008-04-30
> **gandaran said:**
> never seen this problem! try starting opera on the terminal, if it shows any errors post them back here, try also opera as root « sudo opera »
BAD idea! *Never* run something as root unless you need to. You do not need to run Opera 9.50 as root (nor do you need to delete your .opera folder, 9.50 offered to convert all the settings for me when I started it). Just run it in a terminal and post the output.

---

### Post by TeoBigusGeekus on 2008-04-30
[http://ubuntuforums.org/showthread.php?t=745325]("http://ubuntuforums.org/showthread.php?t=745325")

---

### Post by terrordrone on 2008-04-30
when i run through command line.. this is what i got

> opera
** Message: GetValue variable 1 (1)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault (core dumped)

---

### Post by terrordrone on 2008-04-30
> **TeoBigusGeekus said:**
> [http://ubuntuforums.org/showthread.php?t=745325]("http://ubuntuforums.org/showthread.php?t=745325")

Thanks!!!

Opera 9.27 works that way..   :guitar::popcorn:

but dunno why 9.50b2 is crashing on my system

---

### Post by terrordrone on 2008-05-04
well any ideas why 9.5b2 is crashing on my system?

---

### Post by SunnyRabbiera on 2008-05-04
> **terrordrone said:**
> well any ideas why 9.5b2 is crashing on my system?

well it IS a beta, I think that sums up your issue pretty well.
Betas are not meant for everyday use, though for operas case with working with flash its sometimes for the best.

---

### Post by TeoBigusGeekus on 2008-05-04
No idea mate...
In my system 9.5b2 has never crashed... yet!!!
Have you tried *completely* removing all opera instances through synaptic and then reinstalling 9.5b2?

---

### Post by terrordrone on 2008-05-04
> **TeoBigusGeekus said:**
> No idea mate...
In my system 9.5b2 has never crashed... yet!!!
Have you tried *completely* removing all opera instances through synaptic and then reinstalling 9.5b2?

Did that and still crashes :cry:

---

### Post by SunnyRabbiera on 2008-05-04
its how it is sometimes, applications can have a mind of their own sometimes.

---

### Post by TeoBigusGeekus on 2008-05-04
It's a pity, cause 9.5b2 is the best Opera version I've ever used - and I've been using Opera since version 7...
Have patience brother, I think the stable release is due to be out in the beginning of summer...

---

### Post by terrordrone on 2008-05-05
yea tuff luk for me.. 
it was working before... it was promting me for converting some mail format etc at start up and i was clicking 'no' always.. once i decided to get rid of that prompt and clicked on yes.. from that point on i think its crashing

neways hope Opera releases it asap.. but let them take time and be the best 

go Opera go!!:guitar:

---

