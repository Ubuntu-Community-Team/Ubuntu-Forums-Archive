---
title: "[SOLVED] What should I backup?"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by tahitiwibble on 2008-08-02
It must be age and the dwindling grey matter or something, but I have tried looking at a lot of web pages to find an answer to my dilemma, in vain. 

I don't know what to backup on my system so that I don't lose all the important information such as emails, work files, settings and the suchlike so that when my system crashes or the hard drive goes south I can just install the latest version of Ubuntu and carry on with eking out my meagre living and not commit suicide.

I don't know how to save and run a script for future use, so I am wishing to copy/paste my "backup" to a second internal hard drive and also periodically to an external USB hard drive.

I apologize for my ignorance guys and would like to express my extreme gratitude to anyone that may afford me a quick and simple "wham, bang, thank you Ma'am" answer.

THANK YOU!

---

### Post by mevets on 2008-08-02
Just backup your home folder.

---

### Post by blue_shift on 2008-08-02
[LIST]
[*]Any custom settings files you may have made, eg. /etc/X11/xorg.conf
[*]the /home/you folder
[*]any "documents" folders you keep outside of /home/you
[/LIST]
Also, try here: [http://www.desktoplinux.com/articles/AT2280165098.html](http://www.desktoplinux.com/articles/AT2280165098.html)
> What should you backup? Your priority should be to backup those files that are most important and hardest to recreate. Here's my take on the importance of backing up certain data from the perspective of a general desktop user, from most important to least:

   1. Your files -- This includes documents, spreadsheets, email, calendar data, financial data, downloaded music -- anything that you've created, recorded or received that has meaning and importance to you. These are clearly the most important and hardest to recreate, because you or others created them from imagination and hard work or because you paid for them.

   2. Your settings -- This includes changes you've made to personal settings: desktop configuration (e.g., colors, backgrounds, screen resolution, mouse settings, locale) and program options, such as settings for OpenOffice, Gimp, your music player, and your email program. These are easier to recreate than your documents, but you'd hate to lose them -- it takes time to recreate them.

   3. System settings -- Many people never touch their system settings -- the settings are created during Linux installation and stay that way. For those people, backing up system settings is less crucial than backing up their personal settings, since a re-installation would fix things. For people who customize their systems -- e.g., changing system configuration files in /etc -- backing up these settings can be at least as important as backing up personal settings.

   4. Installed software (and everything else) -- This category includes installed system software (primarily Linux) and application software (such as OpenOffice, Firefox, and the Apache Web server). Such software can usually be restored by reinstalling, but not always.

You can follow the link for some simple backup script instructions, or indeed use manual methods.
A.

---

### Post by tahitiwibble on 2008-08-02
> **mevets said:**
> Just backup your home folder.

Mevets, you're a Champion! Is it really that simple? 

I have a very "stock" system (7.04) excepting my desktop colours, personalized panels and other such niceties, as well as all my dearly loved programs. 

When the **** hits the fan, do I just install the latest version of Ubuntu, and then replace my home folder?

---

### Post by tahitiwibble on 2008-08-02
> **blue_shift said:**
> [LIST]
[*]Any custom settings files you may have made, eg. /etc/X11/xorg.conf
[*]the /home/you folder
[*]any "documents" folders you keep outside of /home/you
[/LIST]
Also, try here: [http://www.desktoplinux.com/articles/AT2280165098.html](http://www.desktoplinux.com/articles/AT2280165098.html)


You can follow the link for some simple backup script instructions, or indeed use manual methods.
A.

blue_shift THANK YOU, that link was priceless! I actually understood a good part of it!

---

### Post by Paqman on 2008-08-02
> **tahitiwibble said:**
> 
When the **** hits the fan, do I just install the latest version of Ubuntu, and then replace my home folder?

Yep.

That's why a lot of people like to put their /home on a separate partition. When they reinstall the /home is left untouched.

---

### Post by tahitiwibble on 2008-08-02
> **Paqman said:**
> Yep.

That's why a lot of people like to put their /home on a separate partition. When they reinstall the /home is left untouched.

Paqman, I see the logic perfectly. Please, how does one designate the /home location? 

Your suggestion would seem to be the ideal solution to "updating" to newer versions of Ubuntu? It was a catastrophe when I tried to simply "update" from 7.04 to 7.10

---

### Post by drubin on 2008-08-02
> **tahitiwibble said:**
> Paqman, I see the logic perfectly. Please, how does one designate the /home location? 

Your suggestion would seem to be the ideal solution to "updating" to newer versions of Ubuntu? It was a catastrophe when I tried to simply "update" from 7.04 to 7.10
I would personally back up your important documents/files and do a FRESH full install of hardy(8.04) as you would have to upgrate from fiesty to gutsy to hardy. Bit pointless in my mind.


Nice tutorial. 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Ps take a look at the rest of her site it has a lot of nice tutorials on it.

---

### Post by tahitiwibble on 2008-08-02
> **rubinboy said:**
> I would personally back up your important documents/files and do a FRESH full install of hardy(8.04) as you would have to upgrate from fiesty to gutsy to hardy. Bit pointless in my mind.


Nice tutorial. 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Ps take a look at the rest of her site it has a lot of nice tutorials on it.

rubinboy, that link was better than anything I was hoping for THANK YOU!

---

### Post by cybrsaylr on 2008-08-03
I just backup files I want to save, mainly music and pictures. I put them on an external HDD so I have them in two places, so nothing is lost if one of the drives fails. The rest of the contents I don't really worry about losing.

---

