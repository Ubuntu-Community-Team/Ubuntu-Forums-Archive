---
title: "Installing Firefox help - Package download 404ing?"
date: 2014-02-01
forum: New to Ubuntu
---

### Post by komali2 on 2014-02-01
[FONT=arial]Hey all!

I've been trying to install firefox for a while now, and I guess I'm just not understanding how to do it. I've tried two methods: using synaptics package manager and manually downloading the files from the firefox website. 

Synaptics Package manager is pointing to here to get the files: [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_22.0+build2-0ubuntu0.13.04.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_22.0+build2-0ubuntu0.13.04.2_amd64.deb)

However, there is nothing there. So, I guess I can't use that method? 

My second method is the one listed here [http://support.mozilla.org/en-US/kb/install-firefox-linux](http://support.mozilla.org/en-US/kb/install-firefox-linux)

However, I get stuck at the step "[COLOR=#484848]To start Firefox, run the [/COLOR][COLOR=#484848]*firefox*[/COLOR][COLOR=#484848] script in the [/COLOR][COLOR=#484848]*firefox*[/COLOR][COLOR=#484848] folder: [/COLOR]~/firefox/firefox"

I've tried googling what it means to "run a script" and have tried doing various forms of "sh" but I get errors like 

```
[/FONT][FONT=arial]firefox: 1: firefox: Syntax error: word unexpected (expecting ")")[/FONT]
[FONT=arial]
```[/FONT][FONT=arial]
I've tried manually selecting the file in my file browser and clicking "run" or "run in terminal," neither of which does anything. Nothing happens. 

I'm pretty stuck here, can anyone lend me a hand? Thank you![/FONT]

---

### Post by Dennis N on 2014-02-01
Here are the general procedures to follow in Ubuntu to install software:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

However, Firefox should already be installed by default. Check the Unity Launcher.

---

### Post by komali2 on 2014-02-01
Thank you for the link! Unfortunately, it just lists help for the software manager and .deb files. For .tar.gz, which is what I have for firefox, it says the following:

"If you have trouble installing a .tar.gz file, you can ask for help on [the Ubuntu Forums]("http://www.ubuntuforums.org/")."

So... heh


[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) I read through there, but again I get stuck at, basically, "ok now that you've extracted the .tar.bz, just follow the developer instructions"

---

### Post by deadflowr on 2014-02-01
What are you running?
(system os-wise)

For the record I didn't see any firefox22's listed in here
[http://security.ubuntu.com/ubuntu/pool/main/f/firefox/](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/)
which explains the 404s.

---

### Post by monkeybrain20122 on 2014-02-01
Which Ubuntu are you using? FF is installed by default.

---

### Post by Bucky Ball on 2014-02-01
Yes, installed by default. Perhaps if you tell exactly what you are trying to do it would help. I'm presuming that, not happy with the default version of Firefox in the repositories, you are attempting to upgrade it to 4.2 by manual methods? There's probably a PPA about, which would be easier.

[https://duckduckgo.com/?q=firefox+4.2+ppa](https://duckduckgo.com/?q=firefox+4.2+ppa)

---

### Post by Dennis N on 2014-02-01
You didn't identify your os, so we tend to assume it is Ubuntu with Unity desktop.

My advice (same advice as on the page I referred you to) is to star over, use the Ubuntu Software Center as described on the linked page, and let it do the installing for you. Directions are on that page. In this way, you get support for the software in the form of updates through the update manager, plus the packages are tailored for your Ubuntu system. This is the usual way people install software on Ubuntu.

Unless you deleted it some way, Firefox is already installed. It's launch button is near the top of the Unity launcher. Hovering with the mouse should identify what each button does.

---

### Post by komali2 on 2014-02-01
Apologies for the delayed response. I am running lubuntu. Blame my misunderstanding of basics but.... lubuntu is kind of a type of ubuntu, right? I'm worried I might be in the wrong place if not. 

Would using a different package manager work? I tried synaptic package manager and lubuntu software center, and both 404'd when trying to download firefox. 

I already have the .tar.bz, is there some way I can install using that? Perhaps there's some way to run an "executable" that I'm not understanding? I can't figure out the file extension for the "firefox" executable that the mozilla tutorial is telling me to "run." 

thank you all for your replies so far

---

### Post by Bucky Ball on 2014-02-01
What web browser does Lubuntu use by default?

[http://linuxg.net/its-official-firefox-is-the-default-web-browser-on-lubuntu-13-10/](http://linuxg.net/its-official-firefox-is-the-default-web-browser-on-lubuntu-13-10/)

You still haven't mentioned which release you're using, or I've overlooked something.

---

### Post by monkeybrain20122 on 2014-02-01
I see, which lubuntu? I think since 12.04 they have switched to FF as the default (before they had Chromium). So it seems that you are using an old release of lubuntu that is no longer supported (hence no more package in the repo). 

You should back up your data and do a fresh install of a supported version if you are using an old release.

BTW, the tarball from Mozilla doesn't need installation, just extract it in your home. Open the extracted folder and click firefox and it will open.

---

### Post by deadflowr on 2014-02-01
> **Bucky Ball said:**
> What web browser does Lubuntu use by default?

I thought it moved to firefox on 13.10.
Was chromium before, if I remember right.

But that begs the other question, which version of lubuntu?

From the 404 link provided to Ubuntu firefox archives it was for a 13.04 package.
If the OP is using 13.04, then it makes sense.
13.04 is now dead.

---

### Post by Bucky Ball on 2014-02-01
> **deadflowr said:**
> 
If the OP is using 13.04, then it makes sense.
13.04 is now dead.

^^^
This.

If this is you, move on. I'd do a reinstall of 12.04 LTS or 13.10, both directly upgradeable to 14.04 in April. Or wait til April.

---

### Post by monkeybrain20122 on 2014-02-01
> **Bucky Ball said:**
> ^^^
This.

If this is you, move on. I'd do a reinstall of 12.04 LTS or 13.10, both directly upgradeable to 14.04 in April. Or wait til April.

lubuntu 12.04 is not a LTS, though the repo for FF would still be active since it is the same as Ubuntu's. For the small number of things stuffs not in the common ubuntu repos, add this ppa
[https://launchpad.net/~lxle/+archive/stable](https://launchpad.net/~lxle/+archive/stable)

---

### Post by Bucky Ball on 2014-02-01
> **monkeybrain20122 said:**
> lubuntu 12.04 is not a LTS ...

My mistake. Thanks. ;)

---

### Post by komali2 on 2014-02-01
edit; double post, sorry, one sec, lemme read up to here real quick

edit2: So I did "lsb-release" and got back

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"
```

But I'm not sure how to find the exact lubuntu version, sorry... I'll keep googling.

edit3: ah, ok, so apparently I'm using an outdated version of lubuntu? That is good to know, thank you! I will update when I'm back home. I'll try extracting directly to home and see what happens in the meantime. For the record, yes, currently the default browser is chromium.

> **monkeybrain20122 said:**
> I see, which lubuntu? I think since 12.04 they have switched to FF as the default (before they had Chromium). So it seems that you are using an old release of lubuntu that is no longer supported (hence no more package in the repo). 

You should back up your data and do a fresh install of a supported version if you are using an old release.

BTW, the tarball from Mozilla doesn't need installation, just extract it in your home. Open the extracted folder and click firefox and it will open.

So I tried extracting to /home/me and now there's a directly /home/me/firefox. Inside I clicked the file just named "firefox" with no extension that I can see, it gave me the option to "execute" or "execute in console." Clicking either doesn't seem to do anything... When I tried extracting directly into home it said I don't have permission to do that. Do I need to do a sudo thing and force it to extract into home, will that solve the problem?

---

### Post by deadflowr on 2014-02-01
You can grab the latest lubuntu from here
[http://lubuntu.net/](http://lubuntu.net/)

Good Luck.

---

### Post by komali2 on 2014-02-01
> **deadflowr said:**
> You can grab the latest lubuntu from here
[http://lubuntu.net/](http://lubuntu.net/)

Good Luck.


Will do. Thank you!

---

### Post by monkeybrain20122 on 2014-02-01
> **komali2 said:**
> So I tried extracting to /home/me and now there's a directly /home/me/firefox. Inside I clicked the file just named "firefox" with no extension that I can see, it gave me the option to "execute" or "execute in console." Clicking either doesn't seem to do anything... When I tried extracting directly into home it said I don't have permission to do that. Do I need to do a sudo thing and force it to extract into home, will that solve the problem?

You right click the file, go to Properties > Permission and check the box "allow to execute as a program".

---

### Post by Bucky Ball on 2014-02-02
Post a new thread with any issues you're having on the supported Lubuntu. No point going on here and you can mark thread as solved or I can close it. ;)

13.04 is a rather pointless endeavour, although by jumping through numerous hoops you MIGHT get things back on track. You will still be left with a vulnerable computer as far as security goes and I would take that machine offline.

---

### Post by oldos2er on 2014-02-02
> **komali2 said:**
> [FONT=arial]I've been trying to install firefox for a while now, and I guess I'm just not understanding how to do it. I've tried two methods: using synaptics package manager and manually downloading the files from the firefox website. 

Synaptics Package manager is pointing to here to get the files: [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_22.0+build2-0ubuntu0.13.04.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_22.0+build2-0ubuntu0.13.04.2_amd64.deb)

However, there is nothing there. So, I guess I can't use that method? [/FONT][FONT=arial][/FONT]

Just FYI, to install a package with Synaptic, right-click, choose 'Install' then click 'Apply' on the top menu.

---

### Post by komali2 on 2014-02-04
Thank you all for the help! I'll mark it as solved and make a new thread if I can't figure it out when I upgrade to the new lubuntu. 

Incidentally, in reply to the person mentioning permissions, I don't see the permission option "run as program," just stuff related to users. I'm assuming it must be available in the next version of lubuntu.

Anyway, thank you all very much!

---

