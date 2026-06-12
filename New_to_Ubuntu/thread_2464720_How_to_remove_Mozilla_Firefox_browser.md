---
title: "How to remove Mozilla Firefox browser ?"
date: 2021-07-09
forum: New to Ubuntu
---

### Post by Innernet on 2021-07-09
Good evening.

Running Lubuntu 20.04 and would like to make Firefox dissappear first.  Guidance for an old fart, please ?
Then, will try the same for Opera that seems to work better _after_ **four** minutes to load (waaaay beyond reasonable)
Chrome with a vomitive overdose of advertising installed for now, plan is to evaluate for a while if gets the axe or not. :redface:

---

### Post by monkeybrain20122 on 2021-07-09
Just 
```

sudo apt remove firefox && sudo apt autoremove
```

But if it takes you 4 minutes to start firefox there is something wrong with your system or your Firefox profile. Tried opera before, but it seems to have some long standing issues on Linux re media, you may want to check out [Vivaldi]("https://vivaldi.com/") which is like Opera but better maintained for Linux IMO.

---

### Post by guiverc on 2021-07-09
The simple remove of `firefox` using what @monkeybrain20122 works.

I just booted a Lubuntu 20.04 *daily* (what will be 20.04.3 on release) to confirm. 

Lubuntu has to provide a browser that meets the requirements of LXQt, which is easiest using `firefox` so we use that ([https://packages.ubuntu.com/focal/lubuntu-desktop](https://packages.ubuntu.com/focal/lubuntu-desktop)) as it's from 'main' thus is secure with 5 years of support we don't need to worry about.  :)

[https://manual.lubuntu.me/lts/2/2.1/2.1.1/firefox.html](https://manual.lubuntu.me/lts/2/2.1/2.1.1/firefox.html)

You'll find links can no longer be opened though on your system (as `firefox` handled those), though alternatives can be used (see [https://manual.lubuntu.me/lts/3/3.2/3.2.17/alternative_configurator.html?highlight=browser](https://manual.lubuntu.me/lts/3/3.2/3.2.17/alternative_configurator.html?highlight=browser))

Personally I'd opt for keeping `firefox` and finding your issue (*it shouldn't take that long; that's a symptom of a problem which I'd explore before it bites you somewhere else*) and just change default to something else (*see my last alternatives link*).

(*there is a package that lists three browsers that are required; one being `firefox` - the browser needs to be in Ubuntu repositories, but I can't find the rule that I'm looking for which is why I'd leave firefox installed - you may discover it come release-upgrade time though as I don't see it in focal*)

---

### Post by ActionParsnip on 2021-07-10
Or you can run software center or whatever its called now and remove it using a GUI way
The command in the first reply is by far the quickest though. You can launch a terminal by pressing CTRL + ALT + T

---

### Post by mikewhatever on 2021-07-10
There is no special way to remove Firefox. It is removed the same way as any other program. The reasoning seems quite a bit skewed, but anyway, good luck.

---

### Post by fyfe54 on 2021-07-11
+1 for Vivaldi.

---

### Post by Tadaen_Sylvermane on 2021-07-12
> [COLOR=#000000]Chrome with a vomitive overdose of advertising installed for now, plan is to evaluate for a while if gets the axe or not. [/COLOR][COLOR=#000000]

Where are you seeing this "vomitive overdose" of advertising? I run it on Windows and Xubuntu both and the only advertising I see is the same stuff regardless of browser. Site based stuff that chrome has nothing to do with.[/COLOR]

---

### Post by monkeybrain20122 on 2021-07-12
> **Tadaen_Sylvermane said:**
> [COLOR=#000000]

Where are you seeing this "vomitive overdose" of advertising? I run it on Windows and Xubuntu both and the only advertising I see is the same stuff regardless of browser. Site based stuff that chrome has nothing to do with.[/COLOR]

If you install an ad blocker you can screen out almost all of them. Though strangely ublock-origin doesn't work in screening out Youtube ads on Chromium but it works on Chrome but I think it could work there too if I add some filters.

---

### Post by mastablasta on 2021-07-13
> **Tadaen_Sylvermane said:**
> [COLOR=#000000]

Where are you seeing this "vomitive overdose" of advertising? I run it on Windows and Xubuntu both and the only advertising I see is the same stuff regardless of browser. Site based stuff that chrome has nothing to do with.[/COLOR]
without add blocked youtube is terrible experience. and then they offer Try YT premium and see YT free of ads. 

well as i remember YT used to be free of any adds before google bought it. then small adds appeared on the side, then they added them to video, then video adds you could skip and now video ads you can't skip.

so if you watch 20 minute video with no addblock you will get tons of adds. here number of adds, length and timing is regulated for TV, so i am not used ot keep having osme advertisment cutting the video.

---

### Post by Tadaen_Sylvermane on 2021-07-13
Guess I never bothered with any ad blocking other than what it comes with so I never saw a difference. That and I don't do much browsing save a few sites these days.

---

### Post by saitamasan1986 on 2021-07-18
sudo apt purge firefox

---

