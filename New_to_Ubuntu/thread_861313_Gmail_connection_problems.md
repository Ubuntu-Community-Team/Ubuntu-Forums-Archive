---
title: "Gmail connection problems"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by ukurko on 2008-07-16
Just recently I have been unable to connect to Gmail.  I don't use a mail client, always connect via browser.  I upgraded to Firefox 3 as part of the Ubuntu 8.04 upgrade.  

At first, everything was fine, but it seems to have become gradually more difficult to connect to Gmail.  (I also had an intermittent problem when posting to a web forum that instead of my posting being made, Firefox would invite me to download a php file. )
A Google of this issue led me to clear the cache in Firefox, which seemed to help for a while.  

I have tried using Opera to access Gmail, but the symptoms are the same.

Usually I just get a blank page, but occasionally I get the Gmail page that says "this seems to be taking longer than usual" - that page offers me the basic version or the https version, and has a link to reload, but none of them works.

I'm sorry to say that booting into windows vista (I have a dual boting laptop) is now the only way I can get gmail! Using IE or Firefox (v2) in Vista using the same internet connection works fine.

I can ping gmail.com and googlemail.com from the command line so I think it's something in both browsers or the way Ubuntu is sending my http requests to gmail - but I don't know where to look.

Other than the occasional php glitch mentioned above, other websites are working fine.

I tried to load the Gmail "troubleshooter" from their help page, but even that wouldn't load.

Ubutunu 8.04 Firefox3 Opera 9(ish -can't look it up now) Sony Vaio VGN TX5MN 1.5g Ram, 1.2 MHz processor.

---

### Post by elmoosecapitan on 2008-07-16
Depending on how recently you installed 8.04 you may not have downloaded or enabled something, e.g., javascript and/or cookies, that are required to access email.

---

### Post by ukurko on 2008-07-16
Ok thanks - I will check these, but I don't believe I've changed anything recently, and Gmail worked right after the upgrade (which is a few weeks back now) - however, I have downloaded updates since - it's odd I get the same issue in Firefox and Opera though, the settings for these are independent aren't they?

Thanks for the speedy reply!

---

### Post by phidia on 2008-07-16
Simply as a test you could install epiphany (it's a gnome based browser) and see if that works. I've noticed on various computers that ff sometimes struggles with loading gmail-why that is I'm not sure.

---

### Post by ukurko on 2008-07-16
Well it's mysteriously fixed itself - rebooted into Ubuntu and all working fine now.

Thanks for everyone's help - I'm still baffled as I'd already tried rebooting - maybe it just fancied a couple of hours Vista.

---

### Post by ukurko on 2008-07-29
This is a terrible intermittent problem which has returned - and it's getting very very frustrating to the point where I'm going to have to stop using ubuntu.

On an apparently random basis, using either Firefox 3 or Opera, gmail just won't load.  I have cleared cache, cookies and all private data over and over - sometimes this helps, sometimes it doesn't.

Occasionally on an equally random basis I have a problem posting on forums using firefox (and this morning epiphany) - instead of posting my reply it offers me a php file to download.

I am getting really despondent - I have a dual boot machine and the only way I can reliably do my everyday tasks now is to boot into Vista.

I did download epiphany - it works ok about 90% of the time, but I'm having trouble getting it to connect to gmail all the time.

I am really at a loss - using the same internet connection and booting into Vista has everything working fine.

Is it time to ditch Ubuntu?

---

### Post by Frenske on 2008-07-29
Are you sure it is just gmail you can't access or is this related to other pages! I never had any problems accessing gmail trough the browser.

Sounds to me, a non-expert, you might have some problems with the drivers. Experience has taught me that the default drivers are not always the best one.

Check the forums if there are problems reported using your network card related to native ubuntu drivers.

---

### Post by ukurko on 2008-07-29
> **Frenske said:**
> Are you sure it is just gmail you can't access or is this related to other pages! I never had any problems accessing gmail trough the browser.

Sounds to me, a non-expert, you might have some problems with the drivers. Experience has taught me that the default drivers are not always the best one.

Check the forums if there are problems reported using your network card related to native ubuntu drivers.

Yes I am sure it's Gmail - apart from the other issue on posting to forums.  I am using a 3g connection which ubuntu regards as dial-up so it isn't a network card driver issue, but thanks for the reply.

---

### Post by ukurko on 2008-07-31
I think I've solved this (fingers crossed) by turning off Windows tcp scaling - details [here]("http://kerneltrap.org/node/6723").  Google was my friend again on this occasion, once I'd figured out what to ask for.  Thanks to all who contributed.

---

