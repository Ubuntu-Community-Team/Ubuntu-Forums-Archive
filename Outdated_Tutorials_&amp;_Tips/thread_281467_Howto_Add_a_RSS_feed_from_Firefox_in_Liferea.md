---
title: "Howto: Add a RSS feed from Firefox in Liferea"
date: 2006-10-21
forum: Outdated Tutorials &amp; Tips
---

### Post by timetunnel on 2006-10-21
As of ubuntu 6.10 (Edgy Eft) there's an easy way to add a feed to Liferea automatically by clicking on the feed icon in Firefox.

Setting up Firefox:
[LIST]
[*]go to "Edit->Preferences", choose "Feeds"
[*]enable "subscribe to feeds with", the list of RSS services will get enabled then
[*]there's a button to choose an application, click that and choose the file "/usr/bin/liferea-add-feed"
[*]done
[/LIST]
To add a feed to Liferea:
[LIST]
[*]Firefox and Liferea must be running
[*]Select the target folder in Liferea where you want the feed to appear 
[*]In Firefox, go to the site that offers the feed and click on Firefox's feed button (in the standard theme it's on the right hand side of the URL bar) 
[/LIST]done

There's a Firefox extension called "FeedBag", which does the same, but the current version 1.1 isn't compatible with Firefox 2:
[https://addons.mozilla.org/firefox/2468/](https://addons.mozilla.org/firefox/2468/)
[http://liferea.sourceforge.net/feedbag/](http://liferea.sourceforge.net/feedbag/)

---

### Post by Grog140 on 2006-11-04
I don't have that "Liferea-add-feed" file. I only have "Liferea
" and "Liferea-bin". They don't work to add feeds.

---

### Post by timetunnel on 2006-11-04
Do you really have ubuntu 6.10 (Edgy Eft) installed?

---

### Post by Grog140 on 2006-11-04
Oh crap, I forgot I put Dapper back on. 

Oops, my bad, lol

---

### Post by jlh on 2006-12-29
I can't get liferea-add-feed to do anything.  I've set firefox.  When I click on an icon in Firefox, the progress bar shows something happening.  But the feed I want to add does not show up in Liferea.

I'm running Dapper 6.06 and Liferea 1.2.

Anyone else got this problem?

---

### Post by SHRIKEE on 2007-01-13
works like a charm. 
when i add the feed liferea pops up a thing where i can set some details and at the same time the feed gets downloaded. 
Very easy and very fast performance!

---

### Post by gabkdlly on 2007-02-28
Your How-To does not work for me, although running
```

liferea-add-feed http://www.ubuntuforums.org/external.php?type=RSS2

```
from a terminal does work.

Any ideas?

---

### Post by timetunnel on 2007-02-28
Hmm, no idea. The liferea-add-feed script uses DBUS and I don't know if and how xubuntu (which you seem to be using) uses DBUS.

Maybe this helps (from [http://liferea.sourceforge.net/feedbag/):](http://liferea.sourceforge.net/feedbag/):)
> FeedBag uses DBUS to send subscription requests to Liferea. So both Liferea and Firefox must be started with the dbus-daemon running (ps -ef|grep dbus). For DBUS to work properly the DBUS_SESSION_BUS_ADDRESS environment variable of the calling shell must be set. This should be the case if DBUS is already running. If clicking the feed button in Firefox just does not work please run Firefox in a terminal and check if there are DBUS errors when clicking the feed button.

---

### Post by gabkdlly on 2007-03-01
dbus is running, and the DBUS_SESSION_BUS_ADDRESS variable is also set.

I do use Xubuntu 6.10

Starting Firefox from a terminal and then trying to add a feed does not generate any output on the terminal.

Thanks for your efforts. Perhaps I should file a bug on Lauchpad?

---

### Post by timetunnel on 2007-03-01
Filing a bug report could be a good idea. But it might be better to file the bug at the Liferea developer site - or post the same question in the forum there beforehand:

[http://sourceforge.net/projects/liferea/](http://sourceforge.net/projects/liferea/)

---

### Post by jpryor68 on 2007-05-28
@gabkdlly, have you found any solution? I'm having the same problem (I'm also running Xubuntu Feisty, and Liferea 1.2.14, which I compiled myself).

---

### Post by ButteBlues on 2007-05-31
> **jpryor68 said:**
> @gabkdlly, have you found any solution? I'm having the same problem (I'm also running Xubuntu Feisty, and Liferea 1.2.14, which I compiled myself).
I can report similar on Gutsy.

Subscribing from Epiphany works, but not Firefox. I've reset the FF preferences several times and no luck.

However, I used an FF3 tarball I had and it worked. It's gotta be something with the Ubuntu FF.

---

### Post by munkar on 2007-06-28
has anyone had any luck with this? has a bug been reported?

i'm running Ubuntu (not Xubuntu) Feisty and DBUS is enabled. adding a feed to Liferea using liferea-add-feed from the command line works, but doing it from Firefox doesn't seem to.

i'm not a scripting expert, but i also tried to set up Firefox to run a simple debugging script when getting a feed:

```
echo "hi" > /home/user/Desktop/new.log
```

this didn't work either, though i'm not sure whether it's supposed to. how can we find out whether Firefox is passing the feed URL to any script at all?

---

### Post by demonbane on 2008-02-19
Just fixed this for myself at least. You need to install firefox-gnome-support for some reason. I really don't see why launching a shell script requires gnome support, but there you have it. Now everything works as expected.

---

