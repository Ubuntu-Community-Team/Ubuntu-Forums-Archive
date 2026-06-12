---
title: "mistake in the upgrades!?!?!???!?!?!?!"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by DexterLB on 2008-05-29
Today I've got the normal update notification, but look at the summary:
```

    To be removed:

firefox
firefox-3.0
firefox-gnome-support
firefox3.0-gnome support
ubofox


    To be upgraded:
....... I don't wanna write any more

```
Why does it want to remove firefox? Should I press OK?

---

### Post by hyper_ch on 2008-05-29
what does
```

sudo apt-get update && sudo apt-get upgrade

```
output?

---

### Post by dark_harmonics on 2008-05-29
I just ran my upgrades with nothing like that popping up.

---

### Post by guildofghostwriters on 2008-05-29
The same happened to me but I foolishly just assumed everything would be okay and allowed it to go ahead. After the update, I had no firefox 3. I tried to install firefox 3 again (I was using the beta, not the rc) using add/replace and it said it was unable to do so because of unresolved dependencies and to use synaptic. I tried synaptic and that said it was unable because of unresolvable dependencies so I installed ff2 instead. Now that is acting weirdly - no navigation buttons in the toolbar and when I look in add-ons, all the add-ons are listed and with the option to disable or uninstall but they are clearly not active (ie no adblock plus/forecast fox/tabmixplus stuff on the browser window). What gives?

---

### Post by rpainter on 2008-05-29
I got the same thing. Like a dummy, I did it before asking. Now, all I have on my laptop is Firefox 2.

Now...whenever I go in to the Update Manager, it tells me that I need to do a partial upgrade. When I run the partial upgrade, it tells me that my system is up to date, and the upgrade wil be canceled.

Please Help. Thanks.

---

### Post by FuturePilot on 2008-05-29
I haven't received any update notification yet, but I'm assuming they pushed Firefox 3 RC1 out. It looks as though there's a package that hasn't been uploaded to the repos yet which is causing a dependency error. Best thing to do now is probably just wait and try again later.

---

### Post by Seisen on 2008-05-29
That's weird I don't even have an update for firefox in today's updates, did you happen to remove any packages recently?

---

### Post by PmDematagoda on 2008-05-29
This must be a problem related to the Firefox RC1 package not uploaded as of yet. Be patient, the problems will sort themselves out soon.

---

### Post by DexterLB on 2008-05-29
> **Seisen said:**
> That's weird I don't even have an update for firefox in today's updates, did you happen to remove any packages recently?
No, but I have a custom kernel since yesterday

> **hyper_ch said:**
> what does
```

sudo apt-get update && sudo apt-get upgrade

```
output?

That did the job. It upgraded perfectly without needing to remove firefox. Well done! (moving the thread to solved)

---

### Post by abrianb on 2008-05-29
I got the same thing, need to partial upgrade. Did it then lost FF3b5. Tried to re FF3b5 no go . Installed ff2.

---

### Post by Seisen on 2008-05-29
I'm not special :( I don't have that update

---

### Post by FuturePilot on 2008-05-29
> **Seisen said:**
> I'm not special :( I don't have that update

Don't worry, neither do I. I'm not special either. :(

---

### Post by j8a on 2008-05-29
I have successfully upgraded Ubuntu hardy from gutsy. Actually I have a problem which is the following: when I run the update-manager I cannot upgrade the new packages. I did it by running the following command: apt-get update && apt-get upgrade 
The upgrade ends but I think there is another problem. Could you help me?

---

### Post by Seisen on 2008-05-29
> **j8a said:**
> I have successfully upgraded Ubuntu hardy from gutsy. Actually I have a problem which is the following: when I run the update-manager I cannot upgrade the new packages. I did it by running the following command: apt-get update && apt-get upgrade 
The upgrade ends but I think there is another problem. Could you help me?

Can you post the exact error?

---

### Post by PmDematagoda on 2008-05-29
Firefox 3 has now reached the Sri Lankan servers, so be patient everyone, it's on it's way.

> I have successfully upgraded Ubuntu hardy from gutsy. Actually I have a problem which is the following: when I run the update-manager I cannot upgrade the new packages. I did it by running the following command: apt-get update && apt-get upgrade
The upgrade ends but I think there is another problem. Could you help me? 
Please post the exact error you receive.

---

### Post by Inxsible on 2008-05-29
> **j8a said:**
> I have successfully upgraded Ubuntu hardy from gutsy. Actually I have a problem which is the following: when I run the update-manager I cannot upgrade the new packages. I did it by running the following command: apt-get update && apt-get upgrade 
The upgrade ends but I think there is another problem. Could you help me?

Did you use sudo before the commands ?      I didn't get the update for FF3 either. So I guess I am now warned :)  I read something similar about nvidia-glx borking the system. So I de-selected nvidia-glx during my upgrade two days back. I guess I will keep an eye for FF3 packages as well.

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-05-29
> **Seisen said:**
> That's weird I don't even have an update for firefox in today's updates, did you happen to remove any packages recently?

Hmm. Yes, you're right there! I was wondering the same thing. I didn't get any updates for Firefox today. Heck with that, I didn't receive any updates at all today!:confused:
Maybe you touched some of the archives and accidentally deleted it... But still, you can upgrade from Firefox 2 to 3 right? Try going to their website. I'm pretty sure they have a downloadable version of Firefox 3...
Not a cause for the problem, but at least it helps some how, right?

Hope it does:)
Armageddon

---

### Post by phoenix_abhi on 2008-05-29
I Do Not Have Any Update For A Few Days !

---

### Post by DexterLB on 2008-05-29
The problem is that the package information wasn't reloaded and so there was a mistake in the respositories. All you have to do is ```
sudo apt-get update
``` or just press the reload button in synaptic. Then everything looks fine

P.S. How can I mark the thread as [solved]????????

---

