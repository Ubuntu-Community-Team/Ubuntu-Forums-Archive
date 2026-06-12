---
title: "Uninstalled Thunderbird - Menu bar mail client?"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by linuxguy049 on 2012-08-23
Hey all.  ):P

After installing CLAWS mail client, I purged Thunderbird.

But now in the menu bar, under the mail icon, clicking "mail" redirects to nothing.

I can't seem to right-click and edit it, and I'm not sure where to enable CLAWS as the default mail client. In fact, I'm kinda lost with Unity: I prefer KDE, but Kubuntu was a little unstable on my machine.

Thoughts?

---

### Post by Kopkins on 2012-08-23
> **linuxguy049 said:**
> Hey all.  ):P

After installing CLAWS mail client, I purged Thunderbird.

But now in the menu bar, under the mail icon, clicking "mail" redirects to nothing.

I can't seem to right-click and edit it, and I'm not sure where to enable CLAWS as the default mail client. In fact, I'm kinda lost with Unity: I prefer KDE, but Kubuntu was a little unstable on my machine.

Thoughts?

You should be able to edit that through the default settings manager. 

Open the dash and type default. You should have a couple applications to choose from. Choose the one that says details. 

A window will open with your system details and there should be some categories on the left. The second one down is the defaults for your programs. You should be able to change the default mail client from there. 

Best of luck,
Kopkins

---

### Post by linuxguy049 on 2012-08-23
> **Kopkins said:**
> You should be able to edit that through the default settings manager. 

Open the dash and type default. You should have a couple applications to choose from. Choose the one that says details. 

A window will open with your system details and there should be some categories on the left. The second one down is the defaults for your programs. You should be able to change the default mail client from there. 

Best of luck,
Kopkins


Thanks Kopkins! However, the mail button still won't open up Claws. Is there a way I can disable this mail button? I'm kinda anal-retentive, and if I can't get it to work, I really would just like to get rid of it :lolflag:

---

### Post by Kopkins on 2012-08-23
I did some digging around the internet for a way to change that or remove it, but I couldn't find anything. This is linux, so there is a way, you just have to find it. If I have much spare time in the near future (unlikely), I will fiddle with the system and try to find out how to get it working for you. Chances are, that if someone figures out how to get rid of it completely then it wouldn't be much more difficult to change it's action.

Kopkins

---

### Post by linuxguy049 on 2012-08-25
> **Kopkins said:**
> I did some digging around the internet for a way to change that or remove it, but I couldn't find anything. This is linux, so there is a way, you just have to find it. If I have much spare time in the near future (unlikely), I will fiddle with the system and try to find out how to get it working for you. Chances are, that if someone figures out how to get rid of it completely then it wouldn't be much more difficult to change it's action.

Kopkins


Thanks Kop.

I may take a peruse around in the non-beginner forums, to see if anyone is talking about editing the unity layout.

---

### Post by cryptotheslow on 2012-08-25
This way works to remove the mail (Thunderbird) icon from the launcher.

Install Dconf Editor from the Software Centre or using Synaptic.

Start Dconf Editor and navigate in the left pane to:

desktop > unity > launcher

Edit the **favourites** entry and remove this text from the list:

```
'thunderbird.desktop',
```

The icon disappears from the launcher immediately.

HTH

---

### Post by linuxguy049 on 2012-08-25
> **cryptotheslow said:**
> This way works to remove the mail (Thunderbird) icon from the launcher.

Install Dconf Editor from the Software Centre or using Synaptic.

Start Dconf Editor and navigate in the left pane to:

desktop > unity > launcher

Edit the **favourites** entry and remove this text from the list:

```
'thunderbird.desktop',
```The icon disappears from the launcher immediately.

HTH

It's not in the launcher, otherwise I'd just remove it. lol

It's at the top right hand corner, what I thought was called the "menu". 

With the battery, bluetooth, wireless, etc, there's a mail icon. Click that, choose mail, nothing happens. Click it, choose chat, some chat thing opens up. I just want to get rid of it: I'll be removing the default chat client aswell.

---

### Post by cryptotheslow on 2012-08-25
Not enough coffee yet :D

You can remove that mail icon from the panel completely by:

```
sudo apt-get remove indicator-messages
```

There's probably a means to just disable it rather than remove it, but that seems to work.

---

### Post by linuxguy049 on 2012-08-25
> **cryptotheslow said:**
> Not enough coffee yet :D

You can remove that mail icon from the panel completely by:

```
sudo apt-get remove indicator-messages
```There's probably a means to just disable it rather than remove it, but that seems to work.

Worked perfectly after a restart! 

Are all those things called indicators? I'm not really quite sure exactly what to call the top part of the desktop :/

Thanks a bunch!

---

### Post by cryptotheslow on 2012-08-25
I call it the right bit of the top panel or the systray :D It probably has a more correct Ubuntuish name :D

But yes, they do appear to be called indicators. A couple of the others are indicator-datetime, indicator-sound and indicator-session. I don't recommend just ripping them out without good reason and knowing which bits are going to vanish when you do :D

I did some testing, installed Claws Mail then from the Dash launched Details and set Claws Mail as the default mail app. After a logout / login the generic mail icon on the messaging menu does indeed launch Claws Mail - however the menu item is tagged as "Set Up Mail.....". Had a quick look around the interwebs and found a Claws Mail plugin that apparently integrated it with that menu in Ubuntu 11.04 - however it refuses to compile on 12.04 - mostly because it relies on GTK2 functionality whereas 12.04 is using GTK3.

I didn't mess with the other tray indicator plugins - but if you enable one in Claws Mail you will need definitely need to use Dconf Editor and add it to the desktop > unity > panel > systray-whitelist entry for it to have any chance of displaying up there. I've no idea what you would need to add to the whitelist there, in a pinch you could just set that value to 'all' and be done with it.

For reference the 11.04 integration plugin can be found here: [http://freecode.com/projects/claws-mail-indicator](http://freecode.com/projects/claws-mail-indicator) (the one that won't compile!) maybe someone will come along with a wizardly way to get it working :D

Good luck.

---

### Post by linuxguy049 on 2012-08-25
> **cryptotheslow said:**
> I call it the right bit of the top panel or the systray :D It probably has a more correct Ubuntuish name :D

But yes, they do appear to be called indicators. A couple of the others are indicator-datetime, indicator-sound and indicator-session. I don't recommend just ripping them out without good reason and knowing which bits are going to vanish when you do :D

I did some testing, installed Claws Mail then from the Dash launched Details and set Claws Mail as the default mail app. After a logout / login the generic mail icon on the messaging menu does indeed launch Claws Mail - however the menu item is tagged as "Set Up Mail.....". Had a quick look around the interwebs and found a Claws Mail plugin that apparently integrated it with that menu in Ubuntu 11.04 - however it refuses to compile on 12.04 - mostly because it relies on GTK2 functionality whereas 12.04 is using GTK3.

I didn't mess with the other tray indicator plugins - but if you enable one in Claws Mail you will need definitely need to use Dconf Editor and add it to the desktop > unity > panel > systray-whitelist entry for it to have any chance of displaying up there. I've no idea what you would need to add to the whitelist there, in a pinch you could just set that value to 'all' and be done with it.

For reference the 11.04 integration plugin can be found here: [http://freecode.com/projects/claws-mail-indicator](http://freecode.com/projects/claws-mail-indicator) (the one that won't compile!) maybe someone will come along with a wizardly way to get it working :D

Good luck.

Well I don't really care about the indicators, except for one thing: How can I leave applications going, without actively having a window open? Like MSN worked on windows, or something? I had thought that was what the mail indicator was for, but that just opened up a window for thunderbird.

Thanks for all your help! :KS

---

### Post by cryptotheslow on 2012-08-25
That is exactly what the mail indicator is for - it's just that Claws Mail hasn't coded to integrate with it and there are no plugins to do it - perhaps you'd be better served finding a Claws Mail forum to ask about a plugin for Unity indicators.

As for messaging - Empathy integrates with the messaging menu and works with MSN contacts. But you have now removed the messaging menu that's irrelevant.

Try Pigdin messenger and whitelist its systray notifier in dconf editor - you should then be able to minimise it to the tray.

---

