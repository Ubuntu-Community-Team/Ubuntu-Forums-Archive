---
title: "zeitgeist-daemon eating up my cpu"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by flipper T on 2011-09-02
just installed latest updates, rebooted, and now zeitgeist-daemon is using 98-100% of one of my two cpu cores.

this is not good.

any ideas ?

---

### Post by 2F4U on 2011-09-02
As far as I know, you can disable part of Zeitgeist through Autostart Applications. Only some part of Zeitgeist is disabled by that, but I guess it is the part that consumes your CPU.

---

### Post by flipper T on 2011-09-02
its not listed in startup applications.

---

### Post by flipper T on 2011-09-02
quick update

zeitgeist daemon now crashes after approx 2 minutes

tried replacing...


> jason@jason-M570RU:~$ zeitgeist-daemon --replace
[DEBUG - singleton] Checking for another running instance...
[DEBUG - root] Replacing currently running process...
[INFO - zeitgeist.sql] Using database: /home/jason/.local/share/zeitgeist/activity.sqlite
[DEBUG - zeitgeist.sql] Core schema is good. DB loaded in 1.84202194214ms
[DEBUG - zeitgeist.extension] Searching for system extensions in: /usr/share/zeitgeist/_zeitgeist/engine/extensions
[DEBUG - zeitgeist.extension] Searching for user extensions in: /home/jason/.local/share/zeitgeist/extensions
[DEBUG - zeitgeist.extension] No extra extensions
[DEBUG - zeitgeist.extension] Found extensions: [<class '_zeitgeist.engine.extensions.blacklist.Blacklist'>, <class '_zeitgeist.engine.extensions.storagemonitor.StorageMonitor'>, <class '_zeitgeist.engine.extensions.fts.SearchEngineExtension'>, <class '_zeitgeist.engine.extensions.datasource_registry.DataSourceRegistry'>]
[DEBUG - zeitgeist.extension] Loading extension 'Blacklist'
[DEBUG - zeitgeist.blacklist] No existing blacklist config found
[DEBUG - zeitgeist.extension] Loading extension 'StorageMonitor'
[DEBUG - zeitgeist.storagemonitor] Setting storage medium 8035-4ED6 'X-FI GO!' as available
[DEBUG - zeitgeist.storagemonitor] Setting storage medium C833-86AF '8.0 GB File system' as available
[DEBUG - zeitgeist.storagemonitor] Creating NetworkManager network monitor
[DEBUG - zeitgeist.storagemonitor] NetworkManager network state: 70
[DEBUG - zeitgeist.storagemonitor] Setting storage medium net as not available
[DEBUG - zeitgeist.extension] Loading extension 'SearchEngineExtension'
[DEBUG - zeitgeist.fts] Opening full text index: /home/jason/.local/share/zeitgeist/fts.index
[DEBUG - zeitgeist.extension] Loading extension 'DataSourceRegistry'
[DEBUG - zeitgeist.datasource_registry] Loaded data-source data from /home/jason/.local/share/zeitgeist/datasources.pickle
[INFO - root] Trying to start the datahub
[DEBUG - root] Running datahub (/usr/bin/zeitgeist-datahub) with PID=6902
[INFO - root] Starting Zeitgeist service...
[DEBUG - zeitgeist.fts] Indexing 'application://chromium-browser.desktop'
[DEBUG - zeitgeist.engine] Inserted 1 events out of 1 in 0.187752s
[DEBUG - zeitgeist.notify] Checking monitor :1.79/org/gnome/zeitgeist/monitor/0
Traceback (most recent call last):
  File "/usr/share/zeitgeist/_zeitgeist/engine/extensions/fts.py", line 281, in _check_index
    self.QUERY_PARSER_FLAGS)
xapian.DatabaseCorruptError: Expected another key with the same term name but found a different one
[DEBUG - zeitgeist.fts] Committing FTS index
Exception in thread IndexWorker:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 552, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/threading.py", line 505, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/share/zeitgeist/_zeitgeist/engine/extensions/fts.py", line 405, in _worker_thread
    self._index.flush()
DatabaseCorruptError: Expected another key with the same term name but found a different one

mean anything to anyone ?

---

### Post by ssadien on 2011-09-02
same here. samsung rv510 laptop. 100% cpu after current updates. 2 sept 2011 1837 SAST

---

### Post by sgage on 2011-09-02
> **flipper T said:**
> just installed latest updates, rebooted, and now zeitgeist-daemon is using 98-100% of one of my two cpu cores.

this is not good.

any ideas ?

I see the same thing here, but no real ideas other than to just kill it.

---

### Post by sgage on 2011-09-02
> **flipper T said:**
> its not listed in startup applications.

Try this:

```
for i in $( ls /etc/xdg/autostart ); do sudo sed 's/NoDisplay=true/NoDisplay=false/g' -i /etc/xdg/autostart/$i; done
```

Then it should show up.

---

### Post by flipper T on 2011-09-02
ok, zeitgeist hub now shows

should i disable ?

have googled for purpose / importance of zeitgeist, but still in the dark.


update : deslected zeitgeist datahub, rebooted, zeitgeist starts anyway, at 100% then crashes 2 minutes later.

---

### Post by ventrical on 2011-09-02
It is suppossed to be a social tracker for helps. There was one forum topic where a member referred to it as spyware. The solution was to uninstall it - if I recall correctly.

---

### Post by flipper T on 2011-09-02
this link refers to zeitgeist in 11.04, but i assume still relevant (very negative about zeitgeist)

[http://johanharjono.com/archives/836](http://johanharjono.com/archives/836)

who is going to be the first brave soul to try it...

---

### Post by ventrical on 2011-09-02
I removed all things zeitgiest and it took the unity lenses with it ! That thing just about fried my processor.

---

### Post by ventrical on 2011-09-02
You can reinstall the Unity-application lens through Software Center - however, after removing all things zeitgiest the zeitgiest deamon is still in the processes and smokin' my CPU!

---

### Post by gunksta on 2011-09-02
I can't even get unity to start. Zeitgest fires up, eats my processor and everything more or less grinds to a halt. I'm posting this from gnome-shell, which doesn't require zeitgeist and is thus still functional. I prefer Unity but it is useful to have more than one desktop shell when running a alpha / beta. Odds are good they won't kill both at the same time, unless they release a borked X build.

Hmmm. Perhaps I should install Wayland as a backup . . . .

---

### Post by ventrical on 2011-09-02
I just installed GNOME SHELLand that little evil  #$^$%#&*! program was still there !! Eating up all my resources!!


  I am now in FVWM-Crystal windows manager and all is cool from here. That zeitgiest has to go!!

---

### Post by gunksta on 2011-09-02
I'm sure its just a development bug. This is a beta after-all. You are correct, when I start gnome-shell works, but zeitgeist does send one of my CPUs to 100%, but I don't notice because I have others. A few minutes after I log in, it crashes. Unity is dependent on Zeitgeist and this problem is surely the reason that Unity is suddenly no longer loading.

I'm sure the devs have noticed this little problem. Give them a few hours to find a solution. Zeitgeist generally works quite well, but the usual beta disclaimers are appropriate here.

---

### Post by ventrical on 2011-09-02
Agreed, but just to make a note of it - this had also been an issue with Natty - there were some users who left Natty because of Zeitgiest

And not being able to remove it or control it is cause for  a flag to go up!

 And thanks to you all for bringing this to light.

---

### Post by sgage on 2011-09-02
> **flipper T said:**
> ok, zeitgeist hub now shows

should i disable ?

have googled for purpose / importance of zeitgeist, but still in the dark.


update : deslected zeitgeist datahub, rebooted, zeitgeist starts anyway, at 100% then crashes 2 minutes later.

Same here! Perhaps we need to drive a stake through its heart?

Zombie zeitgeist.

---

### Post by Quackers on 2011-09-02
Similar here. I just end the zeitgeist daemon process via system monitor.

---

### Post by ventrical on 2011-09-02
But it starts right up again when you least expect it !

---

### Post by sgage on 2011-09-02
> **Quackers said:**
> Similar here. I just end the zeitgeist daemon process via system monitor.

I hate to tell you, but it will re-spawn itself. It truly is evil.

I just did a sudo rm /usr/bin/zeitgeist*

So far, so good :KS

---

### Post by cariboo on 2011-09-02
Zeitgeist keeps track of what files you accesed, for more info have a look [here]("http://gnomejournal.org/article/70/an-introduction-to-gnome-zeitgeist").

---

### Post by lucazade on 2011-09-02
> **sgage said:**
> I hate to tell you, but it will re-spawn itself. It truly is evil.

I just did a sudo rm /usr/bin/zeitgeist*

So far, so good :KS

lol... operation eradication!
hope you've reported as bug before the purge :)

---

### Post by Quackers on 2011-09-02
> **sgage said:**
> I hate to tell you, but it will re-spawn itself. It truly is evil.

I just did a sudo rm /usr/bin/zeitgeist*

So far, so good :KS

Really? Without rebooting?  Hmm, it hasn't done that here yet but I'll be watching for that vermin 8-[

---

### Post by ventrical on 2011-09-02
> **sgage said:**
> I hate to tell you, but it will re-spawn itself. It truly is evil.

I just did a sudo rm /usr/bin/zeitgeist*

So far, so good :KS

  I'm glad I kept my Souped Up Alpha 3 Ocelot version because that 'ghost' is sleeping!

---

### Post by sgage on 2011-09-02
> **Quackers said:**
> Really? Without rebooting?  Hmm, it hasn't done that here yet but I'll be watching for that vermin 8-[

Yes, it will respawn without rebooting - it doesn't do it immediately, but it will...

---

### Post by HunterDX77M on 2011-09-02
Very n00by question: What is Zeitgeist, anyway? :confused: I have seen it around when I look at CPU-related programs, but have no idea what it is. If it's a social networking thing, then I have no use for it (I don't use Facebook, Twitter or any of that useless non-sense). Should I remove it, if it is just a waste of resources?

---

### Post by sgage on 2011-09-02
> **HunterDX77M said:**
> Very n00by question: What is Zeitgeist, anyway? :confused: I have seen it around when I look at CPU-related programs, but have no idea what it is. If it's a social networking thing, then I have no use for it (I don't use Facebook, Twitter or any of that useless non-sense). Should I remove it, if it is just a waste of resources?

I don't think anyone really knows :lolflag:

Seriously, it is a daemon that runs in the background and records all your file accesses into a database. Exactly how this information is used, and by whom, I have no idea.

You can't just uninstall it, since many fundamental packages claim to depend on it. But you can delete the executables, which is what I have done. No problems yet...

---

### Post by flipper T on 2011-09-02
> **sgage said:**
> Yes, it will respawn without rebooting - it doesn't do it immediately, but it will...

true, but it appears to reappear in sleeping mode

as to what it does, well as described above. the real concerns about it are how the data is to be used and by whom. perhaps Canonical's base really is a an hollowed out volcano with a shark infested indoor pool after all.

mmm...sharks with lasers

:)

---

### Post by ventrical on 2011-09-02
I think this one is the culprit because I haven't updated this tower since yesterday and it is working like a stable version with zeitgiest sleeping ... but notice what was waiting in synpatic.

---

### Post by cariboo on 2011-09-02
Please read the description I linked to in post [21]("http://ubuntuforums.org/showpost.php?p=11212628&postcount=21")

We don't need any conspiracy theories, when there is an actual description of what zeitgeist does.

---

### Post by mc4man on 2011-09-02
Whole lot of nonsense in this thread. zeitgeist is just used for your benefit in unity and some of the unity lens searches.

There was an update to zeitgeist-extension-fts today - if it is causing issue or better yet crashing file a bug on (look in /var/crash

If not using unity or not using the lens that use zeitgeist then it most certainly can be completely removed, 7 packages total on default install
> $ sudo apt-get purge zeitgeist*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libzeitgeist-gio' for regex 'zeitgeist*'
Note, selecting 'libzeitgeist-1.0-1' for regex 'zeitgeist*'
Note, selecting 'zeitgeist' for regex 'zeitgeist*'
Note, selecting 'zeitgeist-core' for regex 'zeitgeist*'
Note, selecting 'libzeitgeist-1.0-1-dbg' for regex 'zeitgeist*'
Note, selecting 'libzeitgeist-dev' for regex 'zeitgeist*'
Note, selecting 'libzeitgeist-doc' for regex 'zeitgeist*'
Note, selecting 'zeitgeist-extension-fts' for regex 'zeitgeist*'
Note, selecting 'zeitgeist-datahub' for regex 'zeitgeist*'
Note, selecting 'zeitgeist-fts-extension' for regex 'zeitgeist*'
Note, selecting 'zeitgeist-extensions' for regex 'zeitgeist*'
Note, selecting 'banshee-extension-zeitgeistdataprovider' for regex 'zeitgeist*'
Note, selecting 'libzeitgeist0.8-cil' for regex 'zeitgeist*'
Note, selecting 'libqzeitgeist-dbg' for regex 'zeitgeist*'
Note, selecting 'libqzeitgeist0' for regex 'zeitgeist*'
Note, selecting 'libqzeitgeist-dev' for regex 'zeitgeist*'
Note, selecting 'libzeitgeist-cil-dev' for regex 'zeitgeist*'
Note, selecting 'monodoc-zeitgeist-manual' for regex 'zeitgeist*'
Package libzeitgeist-1.0-1-dbg is not installed, so not removed
Package libzeitgeist-dev is not installed, so not removed
Package libzeitgeist-doc is not installed, so not removed
Package banshee-extension-zeitgeistdataprovider is not installed, so not removed
Package libqzeitgeist-dbg is not installed, so not removed
Package libqzeitgeist-dev is not installed, so not removed
Package libqzeitgeist0 is not installed, so not removed
Package libzeitgeist-cil-dev is not installed, so not removed
Package libzeitgeist0.8-cil is not installed, so not removed
Package monodoc-zeitgeist-manual is not installed, so not removed
Package zeitgeist-fts-extension is not installed, so not removed
The following packages will be REMOVED:
  libzeitgeist-1.0-1* unity-lens-applications* unity-lens-files* zeitgeist* zeitgeist-core* zeitgeist-datahub*
  zeitgeist-extension-fts*
0 upgraded, 0 newly installed, 7 to remove and 24 not upgraded.
After this operation, 1,651 kB disk space will be freed.
Do you want to continue [Y/n]? n

---

### Post by ventrical on 2011-09-02
> **cariboo907 said:**
> Please read the description I linked to in post [21]("http://ubuntuforums.org/showpost.php?p=11212628&postcount=21")

We don't need any conspiracy theories, when there is an actual description of what zeitgeist does.


I am not suggesting a conspiracy theory - my apologies if it has sounded that way. I am only trying to get to the bottom of why  the zeitgeist -daemon is eating up so much CPU resource. Then I would declare my assumption that the zeitgiest-extensions-fts is most probably the cause (or another depends) because that file was not included in the update that I performed last evening and I would have to say that it just does not make sense that  they would hook a Unity-Lens-Application file to that file logger as a depend.  I would think it more a terminate and stay resident program but to hook it to the main app Unity Interface does not seem to make good programming practice. And another reason why I document testing anomolies.

 To tell everyone to wait a few hours for a fix is not my way of beta testing -so I hope it is understood I am just trying to go after the bugs  and do it aggressively so.

thanks

---

### Post by flipper T on 2011-09-02
well...if you missed the humor intended in my last post...

what can i say ?

oh hum

---

### Post by ventrical on 2011-09-02
> **mc4man said:**
> Whole lot of nonsense in this thread. zeitgeist is just used for your benefit in unity and some of the unity lens searches.

There was an update to zeitgeist-extension-fts today - if it is causing issue or better yet crashing file a bug on (look in /var/crash

If not using unity or not using the lens that use zeitgeist then it most certainly can be completely removed, 7 packages total on default install

 But I am beta testing Unity3D, 2D and GNOME 3 and I think it is nonsense that they hooked that file logger to the Unity App-Lens. So you uninstall zeitgiest and your graphical icons are gone with U2D and U3D. ??

What ...

---

### Post by ventrical on 2011-09-02
> **flipper T said:**
> well...if you missed the humor intended in my last post...

what can i say ?

oh hum

no .. no .. I didn't mean it that way.
 Please accept my apologies.

---

### Post by flipper T on 2011-09-02
lol

wasn't referring to you :)

our posts crossed in the night...by which i'm not implying some kind of conspiracy

:)

---

### Post by cariboo on 2011-09-02
Maybe we should start using [humour] [/humour] tags. :) :) :)

---

### Post by 23dornot23d on 2011-09-02
Zeitgeist is gone and so is the 10 degrees rise in Temp while it was running at 100% ......

used HTOP to kill it .....

then

```

keithg@keith-Aspire-7730ZG:~$ sudo apt-get purge zeitgeist*
[sudo] password for keithg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libzeitgeist-gio' for regex 'zeitgeist*'
Note, selecting 'libzeitgeist-1.0-1' for regex 'zeitgeist*'
Note, selecting 'zeitgeist' for regex 'zeitgeist*'
Note, selecting 'zeitgeist-core' for regex 'zeitgeist*'
Note, selecting 'libzeitgeist-1.0-1-dbg' for regex 'zeitgeist*'
Note, selecting 'libzeitgeist-dev' for regex 'zeitgeist*'
Note, selecting 'libzeitgeist-doc' for regex 'zeitgeist*'
Note, selecting 'zeitgeist-extension-fts' for regex 'zeitgeist*'
Note, selecting 'zeitgeist-datahub' for regex 'zeitgeist*'
Note, selecting 'zeitgeist-fts-extension' for regex 'zeitgeist*'
Note, selecting 'zeitgeist-extensions' for regex 'zeitgeist*'
Note, selecting 'banshee-extension-zeitgeistdataprovider' for regex 'zeitgeist*'
Note, selecting 'libzeitgeist0.8-cil' for regex 'zeitgeist*'
Note, selecting 'libqzeitgeist-dbg' for regex 'zeitgeist*'
Note, selecting 'libqzeitgeist0' for regex 'zeitgeist*'
Note, selecting 'libqzeitgeist-dev' for regex 'zeitgeist*'
Note, selecting 'libzeitgeist-cil-dev' for regex 'zeitgeist*'
Note, selecting 'monodoc-zeitgeist-manual' for regex 'zeitgeist*'
Package libzeitgeist-1.0-1-dbg is not installed, so not removed
Package libzeitgeist-dev is not installed, so not removed
Package libzeitgeist-doc is not installed, so not removed
Package banshee-extension-zeitgeistdataprovider is not installed, so not removed
Package libqzeitgeist-dbg is not installed, so not removed
Package libqzeitgeist-dev is not installed, so not removed
Package libqzeitgeist0 is not installed, so not removed
Package libzeitgeist-cil-dev is not installed, so not removed
Package libzeitgeist0.8-cil is not installed, so not removed
Package monodoc-zeitgeist-manual is not installed, so not removed
Package zeitgeist-fts-extension is not installed, so not removed
The following extra packages will be installed:
  cairo-dock-core cairo-dock-data cairo-dock-plug-ins-data
  cairo-dock-plug-ins-integration
Suggested packages:
  inkscape rhythmbox
The following packages will be REMOVED:
  awn-applet-related* cairo-dock* cairo-dock-plug-ins* dockmanager*
  libzeitgeist-1.0-1* unity-lens-applications* unity-lens-files*
  unity-place-applications* unity-place-files* zeitgeist* zeitgeist-core*
  zeitgeist-datahub* zeitgeist-extension-fts*
The following packages will be upgraded:
  cairo-dock-core cairo-dock-data cairo-dock-plug-ins-data
  cairo-dock-plug-ins-integration
4 upgraded, 0 newly installed, 13 to remove and 65 not upgraded.
Need to get 5,505 kB of archives.
After this operation, 5,599 kB disk space will be freed.
Do you want to continue [Y/n]? 


```

Its History.
Unless someone comes up with a good reason why I may need it ......

---

### Post by mc4man on 2011-09-02
> **ventrical said:**
> But I am beta testing Unity3D, 2D and GNOME 3 and I think it is nonsense that they hooked that file logger to the Unity App-Lens. So you uninstall zeitgeist and your graphical icons are gone with U2D and U3D. ??

What ...
If you want to use unity* and those dash lens' then zeitgeist is what's making them work, nothing wrong there. If one wants there is gnome-activity-journal to adjust. (how well it works in O don't know, haven't tried, probably won't.

As far as cpu use,  if one is fully updated (glib), then the excessive cpu  usage should be gone
Though it's possible  that zeitgeist-daemon will have a login crash, there is a current bug on that but it's private..
(DocNotFoundError in _check_index(): Document 16 not found or similar

---

### Post by pimentel28 on 2011-09-02
Having this issue as well...responded to an existing bug report. 

Hopefully this gets fixed...I had Natty beta, it wasn't as bad as this. Oneiric for me is completely useless. Looks like I have a lot of bug reporting to do.

---

### Post by Script Warlock on 2011-09-03
same here frying my laptop and i have to kill it manually... hoping fix is coming.

---

### Post by Quackers on 2011-09-03
In unity zeitgeist is now firing up using 100% of one cpu for a couple of minutes then goes to sleep.
In gnome-shell it also runs at 100% on one cpu but when attempting to open the Applications menu (by moving the pointer to top left) the desktop crashes, sometimes becoming completely unresponsive.
This could, however, be caused by recent updates, making it a different issue - not sure.

---

### Post by 23dornot23d on 2011-09-03
Gnome-Shell at the moment has gone very unstable .... not sure what the cause is yet ,,,,,

But it happened on the last set of my updates tonight ..... cairo-dock and some python additions
did not catch the full file names .... pyxxxx

But now its like calling up Beetlejuice ........ 

Do [Gnome-Shell --replace] 3 times and it appears for a while .... then stops
the shell in its tracks ......
 either after doing a screenshot or selecting in the cairo-dock ..... or going to the top left corner.

I re-installed zeitgeist too as I thought that may have been the cause ..... as I removed that earlier ....

---

### Post by mc4man on 2011-09-03
> **Quackers said:**
> In unity zeitgeist is now firing up using 100% of one cpu for a couple of minutes then goes to sleep.
In gnome-shell it also runs at 100% on one cpu but when attempting to open the Applications menu (by moving the pointer to top left) the desktop crashes, sometimes becoming completely unresponsive.
This could, however, be caused by recent updates, making it a different issue - not sure.

While did see the 100% use for short time here, repeatable enough to file a bug on, it's gone now completely, the daemon never uses much cpu at all. (could be stopped by downgrading zeitgeist-extension-fts to 0.0.7-0ubuntu2
After upgrading several libglib packages, (2.29.18-0ubuntu3),  then upgrading zeitgeist-extension-fts back to current 0.0.10-0ubuntu1 the excessive cpu use has not returned (& GS is also fine

Previous all .deb is here
[https://launchpad.net/ubuntu/+source/zeitgeist-extensions/0.0.7-0ubuntu2](https://launchpad.net/ubuntu/+source/zeitgeist-extensions/0.0.7-0ubuntu2)

---

### Post by dino99 on 2011-09-03
its quiet here on i386
you should purge then reinstall it

and/or  purge your ppa one by one to find which is to blame.

---

### Post by ventrical on 2011-09-03
> **mc4man said:**
> If you want to use unity* and those dash lens' then zeitgeist is what's making them work, nothing wrong there. If one wants there is gnome-activity-journal to adjust. (how well it works in O don't know, haven't tried, probably won't.

As far as cpu use,  if one is fully updated (glib), then the excessive cpu  usage should be gone
Though it's possible  that zeitgeist-daemon will have a login crash, there is a current bug on that but it's private..
(DocNotFoundError in _check_index(): Document 16 not found or similar

mc4man,

  My point is (and I think the point of the others whom have the same problem) is that we are *beta testing* Unity under Oneiric Ocelot.  My latest install (as of yesterday now) was fully updated and it was that update that appeared to cause the increased CPU activity in question.

 However, I will try an update thismorning to see if that bug is fixed.

Perhaps I assumed wrong  that Unity interface (with lenses) was a standalone app but I still do not see the sound reasoning of hooking a file logger to an icon navigator.

---

### Post by lucazade on 2011-09-03
> **ventrical said:**
> mc4man,

  My point is (and I think the point of the others whom have the same problem) is that we are *beta testing* Unity under Oneiric Ocelot.  My latest install (as of yesterday now) was fully updated and it was that update that appeared to cause the increased CPU activity in question.

 However, I will try an update thismorning to see if that bug is fixed.

Perhaps I assumed wrong  that Unity interface (with lenses) was a standalone app but I still do not see the sound reasoning of hooking a file logger to an icon navigator.

most used applications/files in unity is handled by zeitgeist.
try to purge gnome-shell ppa if enabled.

---

### Post by ventrical on 2011-09-03
> **dino99 said:**
> its quiet here on i386
you should purge then reinstall it

and/or  purge your ppa one by one to find which is to blame.


Did this yesterday. Nothing.

---

### Post by SevenMachines on 2011-09-03
Removing the stored stuff often helps...
~/.local/share/zeitgeist/
maybe the config stuff if that doesnt work,
~/.config/zeitgeist (?)

[EDIT] remembering to 
$ zeigeist-daemon --quit 
first obviously :)

---

### Post by lucazade on 2011-09-03
Try to delete ~/.local/share/zeitgeist and then run zeitgeist-datahub in terminal. Paste the output from running that command.

this should wipe out zeitgeist database (activity.sqlite) and create a new one

---

### Post by VinDSL on 2011-09-03
Heh!  Here's a strange one for you.  I've reproduced it several times...

When I boot up, zeitgeist-daemon is eating CPU cycles, as described above.  100% on one CPU, then 100% on the other - back and forth, but never 100% on both CPUs at the same time.

Actually, it was kind of nice, because it allowed me to adjust the bar graphs in my Conky script.  :D

Anyway, Opera-Next has been crashing on this machine for a couple of weeks.  I open Opera-Next, then after 10 seconds or so, it closes - and asks me if I want to send a bug report - and I decline.

Now here's the kicker...

Immediately after I decline (cancel) zeitgeist-daemon quits eating the CPUs, e.g. it goes to sleep, and everything is normal for the remainder of the session.

LoL!  Go figure...

---

### Post by RainCT on 2011-09-03
This is most likely a FTS bug.

The latest version (0.0.10-0ubuntu1) may be fixing it.

Removing the FTS index in case it got corrupted may also help ("rm -r ~/.local/share/zeitgeist/fts.index"). This won't lose any data since it will be restored with the next start of Zeitgeist (unlike activity.sqlite, whose deletion shouldn't be necessary).

If not, you can uninstall FTS with "sudo apt-get remove zeitgeist-extension-fts" and restart Zeitgeist -so it loads without FTS- with "zeitgeist-daemon --quit"). (I don't use Oneiric so I don't know if that will work. If apt-get tries to uninstall Unity with it, you can just "sudo rm /usr/share/zeitgeist/_zeitgeist/engine/extensions/fts.py" instead).

However, note that uninstalling FTS will break functionality in Unity Lenses.

---

### Post by Quackers on 2011-09-03
Thanks RainCT, the "rm -r ~/.local/share/zeitgeist/fts.index" seems to have worked here. I ran that then rebooted and no dodgy cpu figures :-)
I'll keep an eye on it.

---

### Post by flipper T on 2011-09-03
same here

you could be my hero, but to early to tell

---

### Post by flipper T on 2011-09-03
nope

problem returned after 2nd reboot

---

### Post by ventrical on 2011-09-03
That script by RainCT works initially but I am going to try a clean boot ans see whats up. Good to hear they have a fix in the works also because it really impedes on the beta testing.

---

### Post by ventrical on 2011-09-03
flipper - your right .. it's back !! after hardboot.

---

### Post by ventrical on 2011-09-03
> **VinDSL said:**
> Heh!  Here's a strange one for you.  I've reproduced it several times...

When I boot up, zeitgeist-daemon is eating CPU cycles, as described above.  100% on one CPU, then 100% on the other - back and forth, but never 100% on both CPUs at the same time.

Actually, it was kind of nice, because it allowed me to adjust the bar graphs in my Conky script.  :D

Anyway, Opera-Next has been crashing on this machine for a couple of weeks.  I open Opera-Next, then after 10 seconds or so, it closes - and asks me if I want to send a bug report - and I decline.

Now here's the kicker...

Immediately after I decline (cancel) zeitgeist-daemon quits eating the CPUs, e.g. it goes to sleep, and everything is normal for the remainder of the session.

LoL!  Go figure...

It is extremely anomolous behaviour.

---

### Post by mc4man on 2011-09-03
Turns  out here It was not an upgrade of glib that stopped the cpu use, that was coincidental  to  using Dash > Find Files & opening several  files
Then on a log out/in  zeitgeist-daemon will silently crash which has the benefit of preventing the excessive cpu use - 
zeitgeist-daemon crashed with DocNotFoundError in _check_index():
  Document X not found

Edit: if you can get zeitgeist-daemon to start crashing then the main bug on has just been made public - tracked here
[https://bugs.launchpad.net/ubuntu/+source/zeitgeist-extensions/+bug/839739](https://bugs.launchpad.net/ubuntu/+source/zeitgeist-extensions/+bug/839739)

---

### Post by VinDSL on 2011-09-03
> **ventrical said:**
> It is extremely anomolous behaviour.
For sure!

Anyway, I discovered a quick workaround, until they fix it.


From a terminal:
```

**[COLOR="Blue"]zeitgeist-daemon -r[/COLOR]** (if Zeitgeist instance is running, replace it)

**[COLOR="Blue"]ctrl-c[/COLOR]** (may have to do it a couple of times to break out)

```

zeitgeist-daemon drops back to a normal state, until next boot.  ;)

---

### Post by cbowman57 on 2011-09-03
Is it zeitgeist itself or has anyone pinpointed it by disabling some plugins?

Just a thought.

---

### Post by VinDSL on 2011-09-03
> **cbowman57 said:**
> Is it zeitgeist itself or has anyone pinpointed it by disabling some plugins?

Just a thought.
I have a *feeling* that it's zeitgeist itself, but...

It's one of those "which came first, the chicken or the egg" things.

Looking at the errors, in debug, it's having a problem with Python 2.7.  Plus, D-Bus isn't connecting all the time.

I installed Activity Journal, from the zeitgeist PPA, and it wouldn't do jack, until I killed the local stores.

After that, Activity Journal would open, but I haven't seen an event in 12-hours.  LoL!

This is a real corker - hard to pinpoint!

---

### Post by 23dornot23d on 2011-09-03
Funny thing is ...... I purged zeitgeist completely last night and then shortly afterwards
I re-installed it as my system started to act strange .....

Today everything is just running so well and the CPU is stable ..... both cores sitting quietly 
even had my games of scrabble on facebook which always normally kicks everything up
the Graphics card temps would be up at 70 and the processors and fans would be going
crazy ....... not today though .....

[URL="http://img822.imageshack.us/img822/3366/scrsbble.jpg"][COLOR=Red][B]
SCREENSHOT[/B][/COLOR][/URL] - Check out the CONKY readings all good ..... even plugin-container which goes mad
sometimes ...... 
( this was towards the end of a game too .... which would be at its worst .... the Nvidia Temp is incredibly low for this machine )

---

### Post by ventrical on 2011-09-03
> **VinDSL said:**
> For sure!

Anyway, I discovered a quick workaround, until they fix it.


From a terminal:
```

**[COLOR=Blue]zeitgeist-daemon -r[/COLOR]** (if Zeitgeist instance is running, replace it)

**[COLOR=Blue]ctrl-c[/COLOR]** (may have to do it a couple of times to break out)

```zeitgeist-daemon drops back to a normal state, until next boot.  ;)

I ran the script suggested by RainCT and it worked for the session but came back on the next hard boot session. Will try yours also.

  This process is akin to a buffer_overflow with an infinite loop but has a _wait_for _app to knock it out of it's loop. and/or a do/until. in the line code that most likley does not have an _eof flag :):)

---

### Post by VinDSL on 2011-09-03
> **23dornot23d said:**
> Funny thing is ...... I purged zeitgeist completely last night and then shortly afterwards
I re-installed it as my system started to act strange .....
~Cool!

I added the zeitgeist PPA to my sources, last night.

I'll try the ol' wash, rinse, and restyle in a couple of hours.

Gotta get some work done, right now...  ;)

---

### Post by flipper T on 2011-09-03
have you rebooted lately ?

my experience so far is that the problem has a nasty habit of reappearing

---

### Post by alexvy13 on 2011-09-03
> **23dornot23d said:**
> Funny thing is ...... I purged zeitgeist completely last night and then shortly afterwards
I re-installed it as my system started to act strange .....

Today everything is just running so well and the CPU is stable ..... both cores sitting quietly 
even had my games of scrabble on facebook which always normally kicks everything up
the Graphics card temps would be up at 70 and the processors and fans would be going
crazy ....... not today though .....

[URL="http://img822.imageshack.us/img822/3366/scrsbble.jpg"][COLOR=Red][B]
SCREENSHOT[/B][/COLOR][/URL] - Check out the CONKY readings all good ..... even plugin-container which goes mad
sometimes ...... 
( this was towards the end of a game too .... which would be at its worst .... the Nvidia Temp is incredibly low for this machine )
how did you purge it?

---

### Post by cbowman57 on 2011-09-03
> **alexvy13 said:**
> how did you purge it?


Most likely **sudo apt-get purge zeitgei*** or something like that.

---

### Post by 23dornot23d on 2011-09-03
Thanks Chuck ....

Yep page 4 ..... on here top thread ...... [[COLOR=Red]**LINK**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11212973&postcount=31")

sudo apt-get purge zeitgeist*


Check dependencies too ..... mine wiped out cairo-dock and I had some fun re-installing that last night
in the end used the cairo-dock testing ppa ....

---

### Post by 23dornot23d on 2011-09-03
whoops ... did not mean to double post .....  just making sure VinDSL knows UNITY is not my main system ....

> **VinDSL said:**
> ~Cool!

I added the zeitgeist PPA to my sources, last night.

I'll try the ol' wash, rinse, and restyle in a couple of hours.

Gotta get some work done, right now...  ;)

Be aware though that I am running Gnome Shell on here ..... not sure if it will have the same
effect for UNITY ..... but I hope it does ......

---

### Post by flipper T on 2011-09-03
wow

possibly relevant

---

### Post by VinDSL on 2011-09-03
> **23dornot23d said:**
> whoops ... did not mean to double post .....  just making sure VinDSL knows UNITY is not my main system ....

Be aware though that I am running Gnome Shell on here ..... not sure if it will have the same
effect for UNITY ..... but I hope it does ......
No prob.  Thanks for the heads-up.  Testers can fix anything, except a broken heart, yes?  LoL!  :D

I purged zeitgeist et al. and rebooted.  CPU load was normal.

Then, I installed the zeitgeist core files from their PPA and rebooted.  CPU load was still normal.

Then, I installed the zeitgeist engine fts extension (zeitgeist-extension-fts) and rebooted.

Boom!  CPU load was pegged again!  :)

So, I did a zeitgeist-daemon -r from CLI, and everything simmered down.

Put another way, I'm back to square one, but a little wiser for trying - the engine is running amuck.

I could uninstall zeitgeist-extension-fts, but then I'll lose the application and file lenses in the dash panel.

Hrm...

---

### Post by ventrical on 2011-09-03
I tired to edit a config file - but it did not work.

Check these screenies out.

And I opened the zeitgeist-datahub.conffiles and it is a text script with an auto start command in it .. so I put a '#' in front of it to try and disable it - but the daemon is still there eating CPU sources.

---

### Post by mc4man on 2011-09-03
> **VinDSL said:**
> 

I could uninstall zeitgeist-extension-fts, but then I'll lose the application and file lenses in the dash panel.

Hrm...
Either downgrade to previous zeitgeist-extension-fts or try to get zeitgeist-daemon to crash at login or there-abouts (have noticed no real change in zeitgeist after a login crash other than cpu use is normal as in almost none.

Using the Find file lens to open a few files in gedit seems to start the crash on next login (or attempt to open files - Atm it's 50-50 here, fails to open, opens, fails, opens, ect. ect.

---

### Post by VinDSL on 2011-09-03
> **ventrical said:**
> I tired to edit a config file - but it did not work.[...]
They'll fix it, sooner or later.  They always do.

In the meantime, it's good fun dissecting it.

I fear, there's too many tentacles on this beast for a quick fix...

---

### Post by 23dornot23d on 2011-09-03
Something for the dev's then I guess .... 

Do devs fix broken hearts  .... mine was once and I am still not sure if its got back up to its 99% ok point yet ....... ;)

Fixing computer problems may be a good choice - have never monitored a broken heart ....  ;)

Is there a HTOP available ...... to check out the bad processes  :confused:

---

### Post by VinDSL on 2011-09-03
> **mc4man said:**
> Either downgrade to previous zeitgeist-extension-fts or [...]
There's an idea!

I'm gonna go hunting... BBL  :)

---

### Post by ventrical on 2011-09-03
> **VinDSL said:**
> They'll fix it, sooner or later.  They always do.

In the meantime, it's good fun dissecting it.

I fear, there's too many tentacles on this beast for a quick fix...

But you are very adept at  splicing code.

 I think it may be a config  in one of these files.. ie;


yep .. sure is fun trying to figure it out :)

 I gotta get some zzzzs   :)

Burning the midnightoil... zzzzzzz..

---

### Post by ventrical on 2011-09-03
> **mc4man said:**
> Either downgrade to previous zeitgeist-extension-fts or try to get zeitgeist-daemon to crash at login or there-abouts (have noticed no real change in zeitgeist after a login crash other than cpu use is normal as in almost none.

Using the Find file lens to open a few files in gedit seems to start the crash on next login (or attempt to open files - Atm it's 50-50 here, fails to open, opens, fails, opens, ect. ect.

  I had a similar prob with the AVG daemon in Ubuntu Lucid about a year ago. I just could not get rid of it and it really pressed the CPU.

---

### Post by VinDSL on 2011-09-03
> **23dornot23d said:**
> Is there a HTOP available ...... to check out the bad processes  :confused:
dbus-daemon looks janky - sitting near the top at a constant 3% CPU usage.

I'll reboot, let it run wild, and check HTOP again...

---

### Post by VinDSL on 2011-09-03
Whoa, baby!   HTOP reports zeitgeist-daemon is using 101% CPU.


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop3-sep-2011-5(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop3-sep-2011-5.png")[/INDENT]


Everything else looks normal...

**EDIT**

I wonder why that dbus-daemon has two slashes in front of it (5th line).

Is that normal?!?!?

Shouldn't it be **[COLOR="Navy"]/usr/bin/[/COLOR]** or maybe no path at all (like 7th line)?

---

### Post by VinDSL on 2011-09-03
Downgraded to zeitgeist-extension-fts 0.0.7-0ubuntu2 and rebooted.

Linkage:  [https://launchpad.net/ubuntu/oneiric/i386/zeitgeist-extension-fts/0.0.7-0ubuntu2](https://launchpad.net/ubuntu/oneiric/i386/zeitgeist-extension-fts/0.0.7-0ubuntu2)

zeitgeist-daemon isn't even on the HTOP radar screen now.  Yeah!

We'll see how it sticks...

---

### Post by 23dornot23d on 2011-09-03
Interesting .... maybe its a mistake ...as I cannot find it documented or anywhere else on my system

the //   :confused:

will keep looking though ....

Is the // on the older install you have now .....

---

### Post by VinDSL on 2011-09-03
> **23dornot23d said:**
> Is the // on the older install you have now .....
The only other distro I have on this machine is Maverick.

Heh!  This UbuOO distro is flying now, with zeitgeist-extension-fts 0.0.7-0ubuntu2 installed.

Lenses are all working - Activity Journal is working - Activity Log Manager is working.

Basically, 11.10 is fun again!

I think I'll pin it for a while...  ;)

---

### Post by Script Warlock on 2011-09-04
@VinDSL, you have a nice conky :)

---

### Post by alexvy13 on 2011-09-04
> **VinDSL said:**
> Whoa, baby!   HTOP reports zeitgeist-daemon is using 101% CPU.

[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop3-sep-2011-5%28650x520%29.png[/IMG]]("http://vindsl.com/images/vindsl-desktop3-sep-2011-5.png")[/INDENT]
Everything else looks normal...

**EDIT**

I wonder why that dbus-daemon has two slashes in front of it (5th line).

Is that normal?!?!?

Shouldn't it be **[COLOR=Navy]/usr/bin/[/COLOR]** or maybe no path at all (like 7th line)?

wow what is that panel on the right side???

---

### Post by VinDSL on 2011-09-04
> **Script Warlock said:**
> @VinDSL, you have a nice conky :)
Thanks!

> **alexvy13 said:**
> wow what is that panel on the right side???
Conky.  ;)

---

### Post by ventrical on 2011-09-04
The new 3.0.0-10 kernel did nothing to remedy the situation either.

---

### Post by lucazade on 2011-09-04
also the new wallpaper didn't help..

---

### Post by ventrical on 2011-09-04
> **VinDSL said:**
> Downgraded to zeitgeist-extension-fts 0.0.7-0ubuntu2 and rebooted.

Linkage:  [https://launchpad.net/ubuntu/oneiric/i386/zeitgeist-extension-fts/0.0.7-0ubuntu2](https://launchpad.net/ubuntu/oneiric/i386/zeitgeist-extension-fts/0.0.7-0ubuntu2)

zeitgeist-daemon isn't even on the HTOP radar screen now.  Yeah!

We'll see how it sticks...

  I downloaded it. Now how do I install it using the terminal ?

Fun! :)

---

### Post by VinDSL on 2011-09-04
> **ventrical said:**
> I downloaded it. Now how do I install it using the terminal ?

Fun! :)
Like all-things-Linux, there are many, many, ways to do this.  

I take the easy route.  No reason to make a big deal out of it, you know?  :D

Here's what I did:

[LIST]
[*]Made a new folder: */home/vindsl/Downloads/Zeitgeist* using Nautilus
[*]Downloaded *zeitgeist-extension-fts_0.0.7-0ubuntu2_all.deb* to that folder using Firefox (DownThemAll extension)
[*]Opened a terminal, then...
[/LIST]

```
$ cd Downloads/Zeitgeist
$ sudo dpkg -i *.deb
```

That's it.

Reboot, and you should be good to go...  ;)

BTW, you didn't ask, but I pinned it using Synaptic (Package -> Lock Version), once I knew it worked.

---

### Post by Script Warlock on 2011-09-04
i thought it was fixed as i have not seen my system peaks again... using the kernel 3.0.0.10 and some other updates. same, workaround i guess downgrade zeitgest.

---

### Post by VinDSL on 2011-09-04
> **Script Warlock said:**
> i thought it was fixed as i have not seen my system peaks again... using the kernel 3.0.0.10 and some other updates. same, workaround i guess downgrade zeitgest.
I just did a restart @ 6hr 45min system uptime.

zeitgeist-extension-fts 0.0.7-0ubuntu2 is still working fine - normal CPU usage.

So far, so good...

---

### Post by SilverWave on 2011-09-04
> **VinDSL said:**
> The only other distro I have on this machine is Maverick.

Heh!  This UbuOO distro is flying now, with zeitgeist-extension-fts 0.0.7-0ubuntu2 installed.

Lenses are all working - Activity Journal is working - Activity Log Manager is working.

Basically, 11.10 is fun again!

I think I'll pin it for a while...  ;)

Yep this has worked for me as well :-)

Cheers.

[]("https://launchpad.net/ubuntu/oneiric/amd64/zeitgeist-extension-fts/0.0.7-0ubuntu1")[zeitgeist-extension-fts 0.0.7-0ubuntu2 (amd64 binary) in ubuntu oneiric]("https://launchpad.net/ubuntu/oneiric/amd64/zeitgeist-extension-fts/0.0.7-0ubuntu2")

---

### Post by SilverWave on 2011-09-04
Just Saying.

The more I look into this the more concerned I become.

I think the least we need is a pop up explaining the implications of Zeitgeist and allowing you to configure it.

> These guys look like OK ppl so why are they doing something like this without express user consent?
 If you know what Zeitgeist is and you turn it on to monitor what you do then Zeitgeist is great.
 But if you don&#8217;t know what it is and what it does, and you  haven&#8217;t been asked to opt-in&#8230;** is that not a breach of your right to  privacy?**
[U][here.]("http://silverwav.wordpress.com/2011/09/04/upgrading-to-oneiric-11-10-beta-1-zeitgeist-logs-the-users-activities-and-events-files-opened-websites-visited-conversations-held-with-other-people-etc/")

[/U]This looks like it will do the job:

> # Delete previous logging.
rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace [here.]("http://askubuntu.com/questions/34592/how-to-clear-recently-used-files")

> # Render Zeitgeist illiterate - cannot read or write
chmod -rw ~/.local/share/zeitgeist/activity.sqlite*[here.]("http://johanharjono.com/archives/836")

---

### Post by Quackers on 2011-09-04
> **VinDSL said:**
> Downgraded to zeitgeist-extension-fts 0.0.7-0ubuntu2 and rebooted.

Linkage:  [https://launchpad.net/ubuntu/oneiric/i386/zeitgeist-extension-fts/0.0.7-0ubuntu2](https://launchpad.net/ubuntu/oneiric/i386/zeitgeist-extension-fts/0.0.7-0ubuntu2)

zeitgeist-daemon isn't even on the HTOP radar screen now.  Yeah!

We'll see how it sticks...

Is this version just for 32 bit? Is there a 64 bit version?

---

### Post by SilverWave on 2011-09-04
> **Quackers said:**
> Is this version just for 32 bit? Is there a 64 bit version?

I'm on 64 bit and I used this one... successfully
[https://launchpad.net/ubuntu/oneiric/amd64/zeitgeist-extension-fts/0.0.7-0ubuntu2](https://launchpad.net/ubuntu/oneiric/amd64/zeitgeist-extension-fts/0.0.7-0ubuntu2)

---

### Post by Quackers on 2011-09-04
Thanks, I'll give it a go :-)

---

### Post by Quackers on 2011-09-04
Done :)
So far so good :)
Thanks all!

---

### Post by ventrical on 2011-09-04
> **VinDSL said:**
> Like all-things-Linux, there are many, many, ways to do this.  

I take the easy route.  No reason to make a big deal out of it, you know?  :D

Here's what I did:

[LIST]
[*]Made a new folder: */home/vindsl/Downloads/Zeitgeist* using Nautilus
[*]Downloaded *zeitgeist-extension-fts_0.0.7-0ubuntu2_all.deb* to that folder using Firefox (DownThemAll extension)
[*]Opened a terminal, then...
[/LIST]

```
$ cd Downloads/Zeitgeist
$ sudo dpkg -i *.deb
```That's it.

Reboot, and you should be good to go...  ;)

BTW, you didn't ask, but I pinned it using Synaptic (Package -> Lock Version), once I knew it worked.

You did it again champ!!  :)

Thanks 

...and..... I will ask now .. how do we pin and lock that version for now?

thanks again.

---

### Post by Quackers on 2011-09-04
In the synaptic search box enter zeitgeist and look for that package name then highlight it and in the menu bar click on "package" then "lock version"

---

### Post by ventrical on 2011-09-04
Ok.... I figured it out .. that synaptic package manager is somEthing else !!!!!!!!!!!!!!

 Thanks to all of you who participated  at setting this bug on the shelf until a fix comes. And we can still beta test Unity 3d AND gnome!!

---

### Post by ventrical on 2011-09-04
new bug ...

 The apport -gtk process is now comming in and out . It will not register CPU in processes but does in resources - and it appears to eat up CPU sources.

---

### Post by SilverWave on 2011-09-04
> **ventrical said:**
> 
  .. how do we pin and lock that version for now?

thanks again.

Synaptic Package Manager > zeitgeist-extension-fts

Version Tab > Package > Force Lock

---

### Post by ventrical on 2011-09-04
> **SilverWave said:**
> Synaptic Package Manager > zeitgeist-extension-fts

Version Tab > Package > Force Lock

Thank you very much.

regards, ventrical

---

### Post by flipper T on 2011-09-04
just got back to pc...is this fix working ?

---

### Post by SilverWave on 2011-09-04
> **flipper T said:**
> just got back to pc...is this fix working ?

Yep :-)

---

### Post by flipper T on 2011-09-04
great. will try now.

what happens when the devs actually fix this problem ? (assuming that this solution is a workaround)

will that fix automatically replace this workaround or are we just storing up other problems for the future ?

sorry to sound so negative

edit : ok, done it.

now sudo apt-get update && sudo apt-get upgrade is offering me a zeitgiest update. do i keep ignoring this ? until when ?


> The following packages will be upgraded:
  zeitgeist-extension-fts
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.6 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue [Y/n]? n

---

### Post by VinDSL on 2011-09-04
> **ventrical said:**
> new bug ...

 The apport -gtk process is now comming in and out . It will not register CPU in processes but does in resources - and it appears to eat up CPU sources.
Interesting!

Here's how I'm reading the 'tea leaves'... ;)



The screenie below looks very similar to yours.  CPU usage is motorboating in the System Monitor graph, but...

When you add HTOP to the mix, it would appear that System Monitor itself & LightDM are responsible for the effect.
[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-4-sep-2011(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-4-sep-2011.png")
[/INDENT]



Now, take System Monitor out of the mix, and CPU usage returns to normal.
[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-4-sep-2011-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-4-sep-2011-2.png")
[/INDENT]

---

### Post by VinDSL on 2011-09-04
Last things first...  :)

> **flipper T said:**
> now sudo apt-get update && sudo apt-get upgrade is offering me a zeitgiest update. do i keep ignoring this ? until when ?
You have it pinned in Synaptic, yes?

Apt-get ignores packages that are pinned with Synaptic.

I would suggest using Synaptic to do updates, until a fix is available.

> **flipper T said:**
> what happens when the devs actually fix this problem ?
Simply unpin the package in Synaptic.

---

### Post by flipper T on 2011-09-04
if by pinned you mean package locked, then yes. update still bringing it up.

how do you do a system wide upgrade check in synaptic ? equivalent to sudo update / upgrade ?

how will i know when there is a fixed version so that i can unlock ?

---

### Post by flipper T on 2011-09-04
screenshot from synaptic attached. are these all the packages i need pinned ?

---

### Post by VinDSL on 2011-09-04
The only package I downgraded was *zeitgeist-extension-fts*, so...

That's the only one I pinned.

---

### Post by flipper T on 2011-09-04
as you can see, i have that pinned, but upgrade still being offered when runnihng sudo apt get update / upgrade

what am i doing wrong ?

ps thx for your time & patience

---

### Post by VinDSL on 2011-09-04
> **flipper T said:**
> as you can see, i have that pinned, but upgrade still being offered when runnihng sudo apt get update / upgrade

what am i doing wrong ?

ps thx for your time & patience
apt-get uses its own database.

apt-get doesn't recognize packages that have been pinned with Synaptic.

You can pin/unpin packages with apt-get, but it's a complex PITA - I don't suggest doing it (unless it's a permanent change).

IMO, it's much easier to temporarily pin/unpin packages using Synaptic, but...

Once you do this, you must use Synaptic (or Update Mangler) to check/install updates, not apt-get.

If you pin a package using Synaptic, then check for updates using apt-get, apt-get will not see the pinned package(s), and it will ask you if you want to (in this case) upgrade *zeitgeist-extension-fts*.

So, don't use apt-get to install updates until a fix is available.  Use Synaptic or Mangler to check for updates.

Once, a fix is available, unpin the obsolete *zeitgeist-extension-fts* package using Synaptic, then go back to updating your system using apt-get, or whatever you normally use.

Make sense?  :)

---

### Post by flipper T on 2011-09-04
whats a "database" ?


...no, only joking :)

will give it a go.

thx again

---

### Post by VinDSL on 2011-09-04
> **flipper T said:**
> thx again
My pleasure!

If you hadn't started this thread, we'd be in a world of hurt - literally.  ;)

Judging be the reads, I'd say a lot of ppl are having issues right now.

Hopefully, the devs will fix it soon...

---

### Post by 23dornot23d on 2011-09-04
Have noticed that since downgrading that the // no longer appears ..... in the HTOP listing.

Just an observation ..... ( still unsure if the // signifies anything important at the beginning of a line )

---

### Post by VinDSL on 2011-09-04
> **23dornot23d said:**
> Have noticed that since downgrading that the // no longer appears ..... in the HTOP listing.

Just an observation ..... ( still unsure if the // signifies anything important at the beginning of a line )
My slashes are still there...  ;)

---

### Post by 23dornot23d on 2011-09-04
Yep sorry ...... so are mine too ..... must have glanced over them ..... 

[[COLOR=Red]**SCREENSHOT**[/COLOR]]("http://img847.imageshack.us/img847/9803/slashes.jpg")

[**SCREENSHOT 2**]("http://img217.imageshack.us/img217/9537/conkyz.jpg") - UNITY and GNOME-SHELL co-existing together added the Ricotz PPA now all is good again, ;)

Just my Conky and zeitgeist to be sorted out and we are ready for 11.10 now ...

---

### Post by VinDSL on 2011-09-05
> **23dornot23d said:**
> [**SCREENSHOT 2**]("http://img217.imageshack.us/img217/9537/conkyz.jpg") - UNITY and GNOME-SHELL co-existing together added the Ricotz PPA now all is good again, ;)

Just my Conky and zeitgeist to be sorted out and we are ready for 11.10 now ...

Nice!

---

### Post by SilverWave on 2011-09-05
> **VinDSL said:**
> 
Judging be the reads, I'd say a lot of ppl are having issues right now.

Hopefully, the devs will fix it soon...

[120 replies ]("http://ubuntuforums.org/misc.php?do=whoposted&t=1837836")         3,322 reads.

Oh yeah this one is causing a lot of problems.

I thought I had a drive issue with the noise it started making.

Using 1 core at 100% permanently could have really damaged my PC :S

I hear that zeitgeist kills kittens as well.

---

### Post by VinDSL on 2011-09-05
Wanna hear something frightening?

I'm running Lubuntu 11.10 off a 4GB USB stick ($8 @ Walmart) right now.

Uptime: 1 hr 1 min 56 sec
CPU usage: 0.0% / 0.7%
RAM usage: 160 MB
SWAP usage: 13 MB
LOAD average: 0.32 0.26 0.32

I'm typing this in the same browser that I use in Unity 3D - same theme - same plugins.

There's nothing I do in Unity 3D, that I can't do in Lubuntu.

Makes me wonder why I'm not running Lubuntu all the time.

Sorry!  Just thinking out loud...  :D

---

### Post by lucazade on 2011-09-05
> **VinDSL said:**
> Wanna hear something frightening?

I'm running Lubuntu 11.10 off a 4GB USB stick ($8 @ Walmart) right now.

Uptime: 1 hr 1 min 56 sec
CPU usage: 0.0% / 0.7%
RAM usage: 160 MB
SWAP usage: 13 MB
LOAD average: 0.32 0.26 0.32

I'm typing this in the same browser that I use in Unity 3D - same theme - same plugins.

There's nothing I do in Unity 3D, that I can't do in Lubuntu.

Makes me wonder why I'm not running Lubuntu all the time.

Sorry!  Just thinking out loud...  :D

I'm waiting for a gtk3 release of LXDE.. any eta?

---

### Post by RomeReactor on 2011-09-05
Looks like the fixed package (0.0.11-0ubuntu1) was [released a few minutes ago]("https://bugs.launchpad.net/ubuntu/+source/zeitgeist/+bug/722762"). Waiting for it to spread through the mirrors.

---

### Post by the_blue_box on 2011-09-05
Yep I just saw that :D
This has been driving me mad. How long will it be until it has "spread through the mirrors"?

:popcorn:

[COLOR=Navy]The Blue Box[/COLOR]

---

### Post by RainCT on 2011-09-05
No need to wait for the mirrors, you can also fetch and install it manually from:

[https://launchpad.net/ubuntu/+archive/primary/+files/zeitgeist-extension-fts_0.0.11-0ubuntu1_all.deb](https://launchpad.net/ubuntu/+archive/primary/+files/zeitgeist-extension-fts_0.0.11-0ubuntu1_all.deb)

In case you're still experiencing other problems (ie. Zeitgeist crashing), there'll be another zeitgeist-extension-fts upload soon fixing several of those.

---

### Post by RomeReactor on 2011-09-05
It's a matter of hours. You can also get it [here]("https://launchpad.net/ubuntu/oneiric/i386/zeitgeist-extension-fts/0.0.11-0ubuntu1"). Seems that it's the same file for both 32 and [64 bit systems]("https://launchpad.net/ubuntu/oneiric/amd64/zeitgeist-extension-fts/0.0.11-0ubuntu1").

Edit:RainCT beat me to it. On my Oneiric installation there's also the added benefit of lower RAM consumption for zeitgeist-daemon, going from over 100 MB right after boot (and usually over 200MB after a few hours), to around 35 MB after boot.

---

### Post by the_blue_box on 2011-09-05
Thanks you two :KS working like a dream.
My RAM has gone right down as well.

Thanks
[COLOR=Navy]The Blue Box[/COLOR]

---

### Post by the_blue_box on 2011-09-05
Hmmm having said that... It has just crashed :)

---

### Post by Quackers on 2011-09-05
Hmm, interesting.
Screenshot 1 is cpu usage after updating and rebooting. It stays this way for 4 minutes.
Screenshot 2 is how it looks after 4 minutes.
TOP says zeitgeist-fts was causing it.

Apport-gtk is causing the later spikes - still

---

### Post by RomeReactor on 2011-09-05
Hasn't crashed here yet, but it's back to using over 130 MB of RAM after a reboot :(

Also, apport-gtk is spiking here as well, along with the known update-apt-xapian-index CPU-hogging.

---

### Post by Script Warlock on 2011-09-05
> **RomeReactor said:**
> Hasn't crashed here yet, but it's back to using over 130 MB of RAM after a reboot :(

Also, apport-gtk is spiking here as well, along with the known update-apt-xapian-index CPU-hogging.

lately its the cpu peaking now its ram? i can live with that, of course it needs a fix.

---

### Post by alexvy13 on 2011-09-05
ok so ima stick with not updating... 
and my cpu and ram is nomal, but the fan is like always on, and loud. its pretty annoying.
I have the system monitor indicator

---

### Post by Script Warlock on 2011-09-05
oh yeah actually beta is not encourage for our daily usage its only good for testing and reporting any errors/bug issues. but then 11.10 really rocks and sexy. :) still using 11.04 as my primary and 11.10 as my extra beta OS.

---

### Post by fjgaude on 2011-09-05
The subject issue has been fixed in both x32 and x65 versions, in the latest, today, updates.

---

### Post by alexvy13 on 2011-09-05
> **fjgaude said:**
> The subject issue has been fixed in both x32 and x65 versions, in the latest, today, updates.
so i can unlock it and finally update?

---

### Post by fjgaude on 2011-09-05
> **alexvy13 said:**
> so i can unlock it and finally update?

I would think so, but I'm no expert.

---

### Post by Quackers on 2011-09-05
Yes, after tonight's update the zeitgeist problem seems to be fixed now here.

---

### Post by sgage on 2011-09-05
> **alexvy13 said:**
> so i can unlock it and finally update?

I did a couple of hours ago, and the cpu hasn't taken off yet...

---

### Post by ventrical on 2011-09-05
> **VinDSL said:**
> Wanna hear something frightening?

I'm running Lubuntu 11.10 off a 4GB USB stick ($8 @ Walmart) right now.

Uptime: 1 hr 1 min 56 sec
CPU usage: 0.0% / 0.7%
RAM usage: 160 MB
SWAP usage: 13 MB
LOAD average: 0.32 0.26 0.32

I'm typing this in the same browser that I use in Unity 3D - same theme - same plugins.

There's nothing I do in Unity 3D, that I can't do in Lubuntu.

Makes me wonder why I'm not running Lubuntu all the time.

Sorry!  Just thinking out loud...  :D


I have 11.04 on an HP 8GB.. it's like lightning . Makes me wonder why I am doing all of these workarounds. :)

---

### Post by flipper T on 2011-09-05
solved ?

solved !

that was exciting :)

---

### Post by Script Warlock on 2011-09-05
> **ventrical said:**
> I have 11.04 on an HP 8GB.. it's like lightning . Makes me wonder why I am doing all of these workarounds. :) hehehe because of impatience?

i think were done and we can mark this as solved.. lets make another thread like no printer in dash or did they rename it?

---

### Post by cariboo on 2011-09-05
Click on the power button and select System Settings.

---

### Post by Script Warlock on 2011-09-05
yeah i know but what i mean is that it is not included yet in the search blah on dash or its just mine.

---

### Post by ventrical on 2011-09-06
> **flipper T said:**
> solved ?

solved !

that was exciting :)

  Yes it was.  I appreciate the persistence of some of the members here and YOU for keeping at it. Also thanks @VinDSL for comming up with that great temp work-a-round.

  It's a great thing to be part of a group project without having to belong to the Billionaire Boy's Club :)

---

### Post by basilwatson on 2011-09-07
Upgraded to 11.10 , a couple of issues nothing major,

Crashing reports , a couple of programs just seem to crash all the time .  

The MAIN and most worrying , is that the CPUs are always at 100% ,  There was A bug report about this , and I tried the solution , a file , zietgiest??? I cant remember , 

anyway still at 100% , anyone else have this problem , is there a new fix , ( have just updated and about to reboot) 

kind regards Stephen 

Nivida graphic driver , duo core and 3 gig of ram .... not sure what info to post !

---

### Post by lonniehenry on 2011-09-07
Run top in a terminal- it will let you know what is running crazy and then post info about your machines harware.

---

### Post by flipper T on 2011-09-07
have you read this ? sounds like same

[http://ubuntuforums.org/showthread.php?t=1837836](http://ubuntuforums.org/showthread.php?t=1837836)

---

### Post by cariboo on 2011-09-07
Merged two threads on the same subject

---

### Post by VinDSL on 2011-09-08
Unity is a little brittle, right now, with all the incremental changes.

Eight hours ago, out of the blue, Banshee Player became the CPU-hog - using 95% CPU.

I just booted, did an update, and rebooted - and everything is running fine, e.g. normal CPU usage again.

My expectation is... in another eight hours, something else will be hammering the CPUs.

Goes with the turf...  ;)

---

### Post by basilwatson on 2011-09-09
I removed zietgiest , as per a suggestion a while back , then installed the update, now I cannot get any applications to open , I go into dash , type terminal 

nothing 

What have I done and how to fix , 

kind regards Stephen

---

### Post by ventrical on 2011-09-09
> **basilwatson said:**
> I removed zietgiest , as per a suggestion a while back , then installed the update, now I cannot get any applications to open , I go into dash , type terminal 

nothing 

What have I done and how to fix , 

kind regards Stephen

 If you are using  Unity  then you have to reinstall the zeitgeist because those Unity Icon navigators are zeitgeist dependent.

---

### Post by basilwatson on 2011-09-09
> **ventrical said:**
> If you are using  Unity  then you have to reinstall the zeitgeist because those Unity Icon navigators are zeitgeist dependent.

cant even open a terminal

I do have another machine I could download the package?

Stephen

---

### Post by ventrical on 2011-09-09
> **VinDSL said:**
> Unity is a little brittle, right now, with all the incremental changes.

Eight hours ago, out of the blue, Banshee Player became the CPU-hog - using 95% CPU.

I just booted, did an update, and rebooted - and everything is running fine, e.g. normal CPU usage again.

My expectation is... in another eight hours, something else will be hammering the CPUs.

Goes with the turf...  ;)

Cool as a cucumber here

---

### Post by ventrical on 2011-09-09
> **basilwatson said:**
> cant even open a terminal

I do have another machine I could download the package?

Stephen

  I think it is :

sudo apt-get install zeitgeist

I think you can install it from recovery terminal - but wait until another member replies  because I am not 100% on that. I removed it  using terminal and synaptic. I am not sure if it will work with the recovery terminal.

---

### Post by ventrical on 2011-09-09
I think you can get terminal from Gnome fallback at the login if you have Gnome fallback installed.

 When I do fresh installs of betas Iusually install a program called <fvwm-crystal> It is awindows manager desktop that will show up at logon options and then allow you to go to a gnome terminal.

---

### Post by basilwatson on 2011-09-09
> **ventrical said:**
> I think it is :

sudo apt-get install zeitgeist

I think you can install it from recovery terminal - but wait until another member replies  because I am not 100% on that. I removed it  using terminal and synaptic. I am not sure if it will work with the recovery terminal.

> **ventrical said:**
> I think you can get terminal from Gnome fallback at the login if you have Gnome fallback installed.

 When I do fresh installs of betas Iusually install a program called <fvwm-crystal> It is awindows manager desktop that will show up at logon options and then allow you to go to a gnome terminal.

will try , 

I dont have gnome fall back 

Stephen

---

### Post by basilwatson on 2011-09-09
Mr crashy is back 

ok , after removing zeitgiest and reinstalling , it say I have the newest verstion , I now cant use dash , one of  application lenses is broken , so I cant get any applications , even terminal , 

Ive tried logging out and fixing broken packages, in a recovery console ,installing zietgiest 

No luck . 

AND the kicker is I can hear my CPU working again , ie its up into the large percentages , 

How can I reinstall  , either the distro ( i did distro upgrade , not a fresh install ) or get the lenses working again 

AND get the cpu from working so hard 

Stephen

---

### Post by VinDSL on 2011-09-09
> **ventrical said:**
> Cool as a cucumber here
Same old, same old, here...  ;)


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/same-old-same-old(650x520).png[/IMG]]("http://vindsl.com/images/same-old-same-old.png")[/INDENT]

---

### Post by ventrical on 2011-09-09
Mabey I missed an update :)

---

### Post by ventrical on 2011-09-09
> **basilwatson said:**
> Mr crashy is back 

ok , after removing zeitgiest and reinstalling , it say I have the newest verstion , I now cant use dash , one of  application lenses is broken , so I cant get any applications , even terminal , 

Ive tried logging out and fixing broken packages, in a recovery console ,installing zietgiest 

No luck . 

AND the kicker is I can hear my CPU working again , ie its up into the large percentages , 

How can I reinstall  , either the distro ( i did distro upgrade , not a fresh install ) or get the lenses working again 

AND get the cpu from working so hard 

Stephen


I thinkmabey:

sudo apt-get install fvwm-crystal

This will install a windows manager and you should be able to log on at the lightdm and then be able to get to a GNOME terminal and even use synaptic.

Yes .. this is it. You should  have fvwm-crystal in your log-on manager after you log off or re-boot.

It is very straight forwar, has just a few bugs , but will get you synaptic and gnome terminal.

Then, research back in this thread and look for some of the posts by VinDSL , Harry and Mac and there are some scripts at how to remove zeitgeist and re-install it. You will also have to re-install the unity -file  and unity app lenses from synaptic.

---

### Post by ventrical on 2011-09-09
Hoo boy!!  Big Omnibus update !!

 And away we go!

:)

---

### Post by basilwatson on 2011-09-09
> **ventrical said:**
> I thinkmabey:

sudo apt-get install fvwm-crystal

This will install a windows manager and you should be able to log on at the lightdm and then be able to get to a GNOME terminal and even use synaptic.

Yes .. this is it. You should  have fvwm-crystal in your log-on manager after you log off or re-boot.

It is very straight forwar, has just a few bugs , but will get you synaptic and gnome terminal.

Then, research back in this thread and look for some of the posts by VinDSL , Harry and Mac and there are some scripts at how to remove zeitgeist and re-install it. You will also have to re-install the unity -file  and unity app lenses from synaptic.

Ok have my gnome terminal back , thanks that worked a treat,  no to re install the unity file 

Stephen

---

### Post by ventrical on 2011-09-09
Your welcome.

heheh.. I just did an Omnibus update and now all of my Unity is gone and I am typing this from GNOME 3d.

wow... what next ..

 fun eh :)

---

### Post by basilwatson on 2011-09-09
> **ventrical said:**
> Your welcome.

heheh.. I just did an Omnibus update and now all of my Unity is gone and I am typing this from GNOME 3d.

wow... what next ..

 fun eh :)

Done worked a treat , 
fvwm-crystal 

gnome terminal , synaptic ,

unity files 

back to square one 

sitting at 78 % ...which is slightly better 

I dont think you could call  this thread closed 

thanks for all the help 

Stephen

---

### Post by effenberg0x0 on 2011-09-09
Another option, if anyone else fall in the zeitgeist - unity trap and can't see / use any app in the dash:

```

Press ctrl+alt+f1 (f1 to f6 - whatever gets you to console)

Login with your user/password

sudo apt-get install --reinstall unity unity-2d unity-2d-launcher unity-2d-places unity-2d-spread  unity-common unity-greeter unity-lens-applications  unity-lens-files  unity-lens-applications unity-lens-music unity-place-applications unity-place-files unity-services

sudo service lightdm restart

```BTW, Zeitgeist literally disappeared from top here. No idea what I did and why. I would suggest people that are having their CPU killed by it to nice/ionice the PID. And, anyway, what do we loose by just killing it? 

I just killed Zeitgeist and everything in the desktop seems to be working normally.

Regards,
Effenberg

---

### Post by ventrical on 2011-09-09
The most recent update I did today killed Unity completely. All I have is GNOME and fvwm-crystal at the login.

 So back to square one with Unity.

---

### Post by ventrical on 2011-09-09
Now I can't get Unity back!!
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity : Depends: libnux-1.0-0 (< 1.6.2) but 1.8.0-0ubuntu1 is to be installed
         Depends: libunity-core-4.0-4 (>= 4.12.0) but it is not going to be installed
         Depends: libunity-core-4.0-4 (< 4.14.0) but it is not going to be installed
 unity-2d : Depends: unity-2d-panel but it is not going to be installed
 unity-2d-launcher : Depends: libunity-2d-private0 (= 4.4.0-0ubuntu1) but it is not going to be installed
 unity-2d-places : Depends: libunity-2d-private0 (= 4.4.0-0ubuntu1) but it is not going to be installed
 unity-2d-spread : Depends: libunity-2d-private0 (= 4.4.0-0ubuntu1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
root@dale:~#

---

### Post by flipper T on 2011-09-09
solved ?

unsolved !

oh - hum

---

### Post by basilwatson on 2011-09-09
> **flipper T said:**
> solved ?

unsolved !

oh - hum

tried killing all zeitgeist 

but still no joy 

Big sulky big things 

Stephen

---

### Post by flipper T on 2011-09-09
basil, the outcome of the initial zeitgeist-induced-terror was that 2 days later a new version was released that, however temporarily, solved the issue.

my personal opinion : sit tight / keep updating

ps you using 10.10 ? its in your signature.

---

### Post by VinDSL on 2011-09-09
> **ventrical said:**
> The most recent update I did today killed Unity completely.[...]

 So back to square one with Unity.
Same here.  I'm running E17, as I type.

Wanted to try it in Oneiric anyway...   LoL!  :D

---

### Post by JonM33 on 2011-09-09
Noticed this too recently. Logged out and run in Unity 2D and don't see an issue. Not that I want to use Unity 2D.

---

### Post by ventrical on 2011-09-09
> **VinDSL said:**
> Same here.  I'm running E17, as I type.

Wanted to try it in Oneiric anyway...   LoL!  :D

It's pretty awesome. I think I will uninstall it and try standard mode because I chose scalable mode and had to choose all the programs and  I didn't get it quite right.

---

### Post by basilwatson on 2011-09-10
> **flipper T said:**
> basil, the outcome of the initial zeitgeist-induced-terror was that 2 days later a new version was released that, however temporarily, solved the issue.

my personal opinion : sit tight / keep updating

ps you using 10.10 ? its in your signature.

no sorry haven't updated my signature , will do that now , 11.10 

All the rest id pretty good , in the beginning I wasn't a fan of unity , but now all my computers have it , and I would dearly love the tablet I have to run unity 

but when both Cpu are up around 80 % , , well thing are getting busy down there and I worry 

as I type , the cpu is getting more and more active.......


I would say its a serious bug , and needs some fast action ...imho

Also , all of the warnings of crashing programs , ,,,,, all the time ,,,, but thats  expected a little at this early stage 

hope its all sorted before the release day 

Stephen

---

### Post by RomeReactor on 2011-09-10
> **basilwatson said:**
> no sorry haven't updated my signature , will do that now , 11.10 

All the rest id pretty good , in the beginning I wasn't a fan of unity , but now all my computers have it , and I would dearly love the tablet I have to run unity 

but when both Cpu are up around 80 % , , well thing are getting busy down there and I worry 

as I type , the cpu is getting more and more active.......


I would say its a serious bug , and needs some fast action ...imho

Also , all of the warnings of crashing programs , ,,,,, all the time ,,,, but thats  expected a little at this early stage 

hope its all sorted before the release day 

Stephen

The bug hasn't returned on my system. A few days ago I purged all the zeitgeist packages, deleted **~/.cache/zeitgeist** and **~/.local/share/zeigeist**; then updated and upgraded the system a couple of times (this of course meant that Dash was practically useless for a day or so), and lastly reinstalled zeitgeist-extension-fts and the app and places lenses. zeitgeist-daemon's CPU usage dropped to nothing and its RAM usage dropped from over 130 MB after boot to 20 MB.

If zeitgeist is still giving you trouble you might want to try purging the packages and deleting the folders mentioned, rebooting, then reinstalling zeitgeist and the lenses.

---

### Post by ronacc on 2011-09-10
completely removing zeitgeist including parts left over after removal in /usr by searching with a root nautilus and deleting all things found has no effect on gnome-shell . Here is the description of zeitgeist from synaptic .
"Zeitgeist is a service which logs the user's activities and events (files
opened, websites visited, conversations held with other people, etc.) and
makes the relevant information available to other applications." IMHO this is nothing but a blatant installation of spyware by Ubuntu SHAME SHAME , I would expect that of MS but not canonical . just another example of what crap unity is , change to another DE .

---

### Post by lucazade on 2011-09-10
> **ronacc said:**
> completely removing zeitgeist including parts left over after removal in /usr by searching with a root nautilus and deleting all things found has no effect on gnome-shell . Here is the description of zeitgeist from synaptic .
"Zeitgeist is a service which logs the user's activities and events (files
opened, websites visited, conversations held with other people, etc.) and
makes the relevant information available to other applications." IMHO this is nothing but a blatant installation of spyware by Ubuntu SHAME SHAME , I would expect that of MS but not canonical . just another example of what crap unity is , change to another DE .

spyware? oh my gosh..

](*,)

---

### Post by ronacc on 2011-09-10
what else would you call a piece of software that logs everything you do on your computer ? and does so without asking your permission or even making you aware that it is doing it . In my book that is spyware plain and simple .

---

### Post by lucazade on 2011-09-10
> **ronacc said:**
> what else would you call a piece of software that logs everything you do on your computer ? and does so without asking your permission or even making you aware that it is doing it . In my book that is spyware plain and simple .

it doesn't spread your info around the web.. in that case could be something to worry about :)

this software helps you to find recent apps and files via unity dash or other services, more or less like and indexing service.

windows and osx ship with something similiar, do we want to say all this os come with a spyware?

---

### Post by flipper T on 2011-09-10
> what else would you call a piece of software that logs everything you do on your computer ? and does so without asking your permission or even making you aware that it is doing it . In my book that is spyware plain and simple .


sounds like my ex-girlfriend :)

---

### Post by Retlol on 2011-09-10
> **ronacc said:**
> what else would you call a piece of software that logs everything you do on your computer ? and does so without asking your permission or even making you aware that it is doing it . In my book that is spyware plain and simple .

Don't read your log files then, you might have a seizure.

I heard firefox has this thing that tracks all the websites you visited, they call it "history".

Spyware much?

/facepalm

---

### Post by ronacc on 2011-09-10
my log files are not "available to other applications" and require root authority to access .

---

### Post by cariboo on 2011-09-10
Zeitgeist has been installed since Lucid, so it's not like it was installed all of a sudden.

---

### Post by effenberg0x0 on 2011-09-10
Not that I agree with the spyware "Gator made it into Ubuntu" conspiracy theory, but I'd feel a little better if I could see what it is doing with my CPU cycles, having an easy way of uninstalling / disabling it without breaking the system, etc. I hate things that try to profile me. BTW, for the sake of CPU cycles, I am running with this thing killed for a while now, with no extraordinary symptoms.

Regards,
Effenberg

---

### Post by ronacc on 2011-09-10
> **cariboo907 said:**
> Zeitgeist has been installed since Lucid, so it's not like it was installed all of a sudden.

I just checked my default install of mangy moose ( AKA maverick meerkat ) and zeitgeist is not installed by default .

---

### Post by ventrical on 2011-09-10
> **effenberg0x0 said:**
> Not that I agree with the spyware "Gator made it into Ubuntu" conspiracy theory, but I'd feel a little better if I could see what it is doing with my CPU cycles, having an easy way of uninstalling / disabling it without breaking the system, etc. I hate things that try to profile me. BTW, for the sake of CPU cycles, I am running with this thing killed for a while now, with no extraordinary symptoms.

Regards,
Effenberg

With the exception of - no zeitgeist - no unity lens navigation!

---

### Post by VinDSL on 2011-09-10
> **lucazade said:**
> it doesn't spread your info around the web.. in that case could be something to worry about :)

this software helps you to find**[COLOR="Red"] recent[/COLOR]** apps and files via unity dash or other services, more or less like and indexing service.[...]
My understanding, of zeitgeist, is its supposed to aid you in searching and finding ancient history and activities.

For instance, let's say you read an article about (whatever) a year ago, but you can't remember the web site.  The intended purpose of zeitgeist is to help you find it.

In other words, it's like a "history" log on steroids.

If there is some hidden agenda going on, I'm unaware of it...  ;)

---

### Post by flipper T on 2011-09-10
perhaps the question to ask is: 

does the data it collects have a commercial value ? & who owns it ?

follow up question: would this discussion be better hosted on a different forum ? Community Cafe ?

---

### Post by lucazade on 2011-09-10
> **VinDSL said:**
> My understanding, of zeitgeist, is its supposed to aid you in searching and finding ancient history and activities.

For instance, let's say you read an article about (whatever) a year ago, but you can't remember the web site.  The intended purpose of zeitgeist is to help you find it.

In other words, it's like a "history" log on steroids.

If there is some hidden agenda going on, I'm unaware of it...  ;)

if you install gnome activity journal you can browse thru recent/ancient history and activities.
yes, a history on steroids sounds good. :)

---

### Post by Framli on 2011-09-10
The only abuse of Zeitgeist data I'm aware of is a fault of mine.
For a few months, people using the Unity Books Lens had this feature enabled by default: when you opened the lens, it automatically queried Google Books with the last Zeitgeist item. Let's say you were using a file named "chaos theory", opening the lens would have automatically launched a Google Books query on "chaos theory" (video here [http://www.youtube.com/watch?v=SRM0z9GprQg](http://www.youtube.com/watch?v=SRM0z9GprQg) ) This was a cool feature, but a pretty bad idea for privacy.

---

### Post by ronacc on 2011-09-10
whether or not zeitgeist is itself malicious in intent is entirely irrelevant . The potential for abuse is too great for it to be a default installed feature . As shown by that video It can without your consent or knowledge provide data to other applications ( perhaps a java script one running clandestinely on a web page ) of data it has " collected " on your activities and then again without your knowledge or consent send it out into cyberspace to wander unattended like little red riding-hood into the jaws of a wolfish granny .

---

### Post by VinDSL on 2011-09-10
> **lucazade said:**
> if you install gnome activity journal you can browse thru recent/ancient history and activities.
yes, a history on steroids sounds good. :)
Yep!  I run both "Activity Journal" and "Activity Log Manager".

Between the two, it gives you a high degree of control over Zeitgeist (and your Dash).

---

### Post by ventrical on 2011-09-11
> **lucazade said:**
> if you install gnome activity journal you can browse thru recent/ancient history and activities.
yes, a history on steroids sounds good. :)


In the world of 'malware removal' zeitgeist would definitely be considered a sort of super tracking cookie.

  I think they can streamline the zeitgeist program to work only locally and not over a network and they should unhook it from the lens navigators.

---

### Post by lucazade on 2011-09-11
> **ventrical said:**
> In the world of 'malware removal' zeitgeist would definitely be considered a sort of super tracking cookie.

I think they can streamline the zeitgeist program to work only locally and not over a network and they should unhook it from the lens navigators.

I don't think it is a spyware or tracking cookie at all and I like the integration in the lenses, really handful..at least for me.
Yes, an option to disable it and also to disable software-center integration would be nice but for I prefer they develop a stable shell before adding every kind of option and customization.

[http://www.apple.com/macosx/apps/#timemachine](http://www.apple.com/macosx/apps/#timemachine)
zeitgeist is similiar to the backend used in time machine, never heard anyone complaining about it.
(obviously it doesn't make backups)

anyway we're going ot with this..

---

### Post by basilwatson on 2011-09-11
No if it does store or even report , or even think about my activity , there should be a disable clause 

BY DEFAULT 

it doesnt  matter about good intension,  there should be a warning and or an explanation 

As we speak,  after all updates , my cpus are still at 80 % and that is unacceptable 

Needs to be sorted ASAP , even if it is Beta 1 

Stephen

---

### Post by ventrical on 2011-09-11
I think that it is a good topic and  should be discussed because there may be a time in the future where we may tend to  to think zeitgest is stable , only to find our CPUs fried!! So it's better to gewt all the bugs out now , the good, the bad and the ugly.

---

### Post by lucazade on 2011-09-11
> **ventrical said:**
> I think that it is a good topic and  should be discussed because there may be a time in the future where we may tend to  to think zeitgest is stable , only to find our CPUs fried!! So it's better to gewt all the bugs out now , the good, the bad and the ugly.

good luck then.. to me this privacy problem is just vaporware.

if there are any issues with zeitgeist a better place is this:
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by effenberg0x0 on 2011-09-11
I guess we could create an apparmor profile for zeitgeist. That way we could limit its freedom in terms of what / where it can read and what it does on networking, while still maintaining lens. I personally dislike apparmor and don't have it enabled right now, but in this case... it fits.

I'd like to hear your opinions. Anyone with some experience in apparmor profiles?

Regards
Effenberg

---

### Post by lucazade on 2011-09-11
> **effenberg0x0 said:**
> I guess we could create an apparmor profile for zeitgeist. That way we could limit its freedom in terms of what / where it can read and what it does on networking, while still maintaining lens. I personally dislike apparmor and don't have it enabled right now, but in this case... it fits.

I'd like to hear your opinions. Anyone with some experience in apparmor profiles?

Regards
Effenberg

it seems a wise idea but have near no experience  with it so i can't add anything else :)

---

### Post by ventrical on 2011-09-11
> **lucazade said:**
> good luck then.. to me this privacy problem is just vaporware.

if there are any issues with zeitgeist a better place is this:
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

  I can live with the spyware .. no sweat - i can control that - but  a fried CPU really hurts my wallet.

So , yeah .. vaporware in my wallet.!

---

### Post by lucazade on 2011-09-12
> **ventrical said:**
> I can live with the spyware .. no sweat - i can control that - but  a fried CPU really hurts my wallet.

So , yeah .. vaporware in my wallet.!

if zeitgeist was a spyware I'd see some inbound/outbound connections, which is not the case.

to see if zeitgeist acts as a internet client is enough to pass this command in the terminal:
```
sudo netstat -tcp
```
or 
```
sudo netstat -tcp | grep zeitgeist
```

to check instead if it is a server:
```
sudo netstat --tcp --listening --programs

```

so you'll see there is no internet traffic.. it simple collects your activities (opened apps, websites, messages, mail, files..) but only *locally*.
it is far better than a simple search tool or of an indexing tool because not all your data are not necessarily a file.

if you have any 'special secrets' you want hide on your own computer you can easily wipe cache with:

```
rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace
```

easy.. isn't it?

ps if it is currently eating your cpu is obviously a bug but it is a separate thing.

---

### Post by VinDSL on 2011-09-12
Gotta say... zeitgeist-daemon (and everything else) is working quite nicely.  5-10% CPU usage, at the moment!  ;)

[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-12-sep-2011(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-12-sep-2011.png")[/INDENT]

---

### Post by basilwatson on 2011-09-12
well my CPU is sitting at 80 % 

I cant figure out why , I THINK its zeitgeist , but as per my other thread ...

Something is making the CPU work and it making the pc unusable 

Ive tried all the solutions offered  

but with no joy 

Stephen

---

### Post by ronacc on 2011-09-12
powertop or system-monitor should tell you what is eating your cpu .

---

### Post by ventrical on 2011-09-13
> **basilwatson said:**
> well my CPU is sitting at 80 % 

I cant figure out why , I THINK its zeitgeist , but as per my other thread ...

Something is making the CPU work and it making the pc unusable 

Ive tried all the solutions offered  

but with no joy 

Stephen


Zeitgeist is pretty well under control here. However, I noticed some other anomolous activity on another install (Acer Aspire 3620) where I started getting  spikes and it was not being reported in system monitor.

  I'm keeping my eye on this beta.

---

### Post by effenberg0x0 on 2011-09-13
Basilwatson,

I may have a couple ideas, not sure. Can you please get and post the info below? I know it's a lot, but I am (wild) guessing you're stuck at a low/wrong cpu frequency or at the performance governor. I want to check what Linux is seeing as your CPU and its limits, the frequency/governor driver, min/max/current frequencies, etc. Plus some other guesses (cpu killers: v86d, mdadm rebuild/check, v86d stuck after changes to console vga gfx mode - which happens sometimes when fiddling with plymouth/grub, etc).

```

uname -a
lsb_release -a
cat /proc/cpuinfo
dmesg | grep cpu
ls -lath /etc/init.d/cpufreqd
px ax | grep cpu
px ax | grep v86d
sudo cat /proc/mdstat
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/bios_limit
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_cur_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_min_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_max_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_driver
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_available_governors
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_governor
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_available_frequencies
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_cur_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_min_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_max_freq

```Regards,
Effenberg

--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)

---

### Post by basilwatson on 2011-09-13
> **effenberg0x0 said:**
> Basilwatson,

I may have a couple ideas, not sure. Can you please get and post the info below? I know it's a lot, but I am (wild) guessing you're stuck at a low/wrong cpu frequency or at the performance governor. I want to check what Linux is seeing as your CPU and its limits, the frequency/governor driver, min/max/current frequencies, etc. Plus some other guesses (cpu killers: v86d, mdadm rebuild/check, v86d stuck after changes to console vga gfx mode - which happens sometimes when fiddling with plymouth/grub, etc).

```

uname -a
lsb_release -a
cat /proc/cpuinfo
dmesg | grep cpu
ls -lath /etc/init.d/cpufreqd
px ax | grep cpu
px ax | grep v86d
sudo cat /proc/mdstat
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/bios_limit
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_cur_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_min_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_max_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_driver
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_available_governors
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_governor
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_available_frequencies
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_cur_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_min_freq
sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_max_freq

```Regards,
Effenberg

--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)

thank you for that post , here 

are the results ; and its a long one , but mostly no such file found .... maybe???

hope this helps 

Stephen 

s@main-desktop:~$ uname -a
Linux main-desktop 3.0.0-10-generic-pae #16-Ubuntu SMP Fri Sep 2 20:09:42 UTC 2011 i686 i686 i386 GNU/Linux
s@main-desktop:~$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu oneiric (development branch)
Release:	11.10
Codename:	oneiric
s@main-desktop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping	: 6
cpu MHz		: 1596.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow
bogomips	: 4775.44
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping	: 6
cpu MHz		: 2394.000
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow
bogomips	: 4776.33
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

s@main-desktop:~$ dmesg | grep cpu
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] KERNEL supported cpus:
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s29952 r0 d23296 u524288
[    0.000000] pcpu-alloc: s29952 r0 d23296 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.004216] Initializing cgroup subsys cpuacct
[    0.060003] smpboot cpu 1: start_ip = 8b000
[    0.264882] ACPI: acpi_idle registered with cpuidle
[    0.864904] cpufreq-nforce2: No nForce2 chipset.
[    0.864906] cpuidle: using governor ladder
[    0.864907] cpuidle: using governor menu
s@main-desktop:~$ ls -lath /etc/init.d/cpufreqd
ls: cannot access /etc/init.d/cpufreqd: No such file or directory
s@main-desktop:~$ ls -lath /etc/init.d/cpufreqd
ls: cannot access /etc/init.d/cpufreqd: No such file or directory
s@main-desktop:~$ px ax | grep cpu
px: command not found
s@main-desktop:~$ px ax | grep v86d
px: command not found
s@main-desktop:~$ sudo cat /proc/mdstat
[sudo] password for s: 
Personalities : 
unused devices: <none>
s@main-desktop:~$ sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/bios_limit
2394000
2394000
cat: /sys/devices/system/cpu/cpu2/cpufreq/bios_limit: No such file or directory
cat: /sys/devices/system/cpu/cpu3/cpufreq/bios_limit: No such file or directory
cat: /sys/devices/system/cpu/cpu4/cpufreq/bios_limit: No such file or directory
cat: /sys/devices/system/cpu/cpu5/cpufreq/bios_limit: No such file or directory
s@main-desktop:~$ sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_cur_freq
2394000
2394000
cat: /sys/devices/system/cpu/cpu2/cpufreq/cpuinfo_cur_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu3/cpufreq/cpuinfo_cur_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu4/cpufreq/cpuinfo_cur_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu5/cpufreq/cpuinfo_cur_freq: No such file or directory
s@main-desktop:~$ sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_min_freq
1596000
1596000
cat: /sys/devices/system/cpu/cpu2/cpufreq/cpuinfo_min_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu3/cpufreq/cpuinfo_min_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu4/cpufreq/cpuinfo_min_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu5/cpufreq/cpuinfo_min_freq: No such file or directory
s@main-desktop:~$ sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/cpuinfo_max_freq
2394000
2394000
cat: /sys/devices/system/cpu/cpu2/cpufreq/cpuinfo_max_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu3/cpufreq/cpuinfo_max_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu4/cpufreq/cpuinfo_max_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu5/cpufreq/cpuinfo_max_freq: No such file or directory
s@main-desktop:~$ sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_driver
acpi-cpufreq
acpi-cpufreq
cat: /sys/devices/system/cpu/cpu2/cpufreq/scaling_driver: No such file or directory
cat: /sys/devices/system/cpu/cpu3/cpufreq/scaling_driver: No such file or directory
cat: /sys/devices/system/cpu/cpu4/cpufreq/scaling_driver: No such file or directory
cat: /sys/devices/system/cpu/cpu5/cpufreq/scaling_driver: No such file or directory
s@main-desktop:~$ sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_available_governors
conservative ondemand userspace powersave performance 
conservative ondemand userspace powersave performance 
cat: /sys/devices/system/cpu/cpu2/cpufreq/scaling_available_governors: No such file or directory
cat: /sys/devices/system/cpu/cpu3/cpufreq/scaling_available_governors: No such file or directory
cat: /sys/devices/system/cpu/cpu4/cpufreq/scaling_available_governors: No such file or directory
cat: /sys/devices/system/cpu/cpu5/cpufreq/scaling_available_governors: No such file or directory
s@main-desktop:~$ sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_governor
ondemand
ondemand
cat: /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor: No such file or directory
cat: /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor: No such file or directory
cat: /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor: No such file or directory
cat: /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor: No such file or directory
s@main-desktop:~$ sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_available_frequencies
2394000 1596000 
2394000 1596000 
cat: /sys/devices/system/cpu/cpu2/cpufreq/scaling_available_frequencies: No such file or directory
cat: /sys/devices/system/cpu/cpu3/cpufreq/scaling_available_frequencies: No such file or directory
cat: /sys/devices/system/cpu/cpu4/cpufreq/scaling_available_frequencies: No such file or directory
cat: /sys/devices/system/cpu/cpu5/cpufreq/scaling_available_frequencies: No such file or directory
s@main-desktop:~$ sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_cur_freq
2394000
1596000
cat: /sys/devices/system/cpu/cpu2/cpufreq/scaling_cur_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu3/cpufreq/scaling_cur_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu4/cpufreq/scaling_cur_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu5/cpufreq/scaling_cur_freq: No such file or directory
s@main-desktop:~$ sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_min_freq
1596000
1596000
cat: /sys/devices/system/cpu/cpu2/cpufreq/scaling_min_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu3/cpufreq/scaling_min_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu4/cpufreq/scaling_min_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu5/cpufreq/scaling_min_freq: No such file or directory
s@main-desktop:~$ sudo cat /sys/devices/system/cpu/cpu{0..5}/cpufreq/scaling_max_freq
2394000
2394000
cat: /sys/devices/system/cpu/cpu2/cpufreq/scaling_max_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu3/cpufreq/scaling_max_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu4/cpufreq/scaling_max_freq: No such file or directory
cat: /sys/devices/system/cpu/cpu5/cpufreq/scaling_max_freq: No such file or directory
s@main-desktop:~$

---

### Post by effenberg0x0 on 2011-09-13
Ok, lets have a look at it. 

- Your CPU has 2 cores. For some reason, one of them (CPU 1) is is stuck at max_freq, the other (CPU 0) seems to be oscillating between min_freq and max_freq.

- Why does it only have two available frequencies? I'm an AMD user. But I doubt an Intel Core 2 CPU can only have two frequencies. This is wrong IMHO. I'd like to hear from people that have Intel CPUs here.

-  Scaling governor is OK (ondemand). 

Lets try this:

```

grep CPU_FREQ /lib/modules/`uname -r`/build/.config
sudo -s
echo 1596000 > /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
echo 1596000 > /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq
echo 1596000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
echo 1596000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_cur_freq

```

QUESTIONS:
- How is the CPU load after the commands above?
- What is your Motherboard vendor / model?
- BIOS settings: Did you disable CPU Stepping features?
- BIOS settings: Did you activate any overclocking feature? Is the BIOS CPU speet set to 2.4GHz? Is the clock set to default (probably 266MHz)?
- If not, try setting the above, restart and verify that you have new possible frequencies: sudo cat/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies


Regards,
Effenberg


--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)

---

### Post by basilwatson on 2011-09-13
> **effenberg0x0 said:**
> Ok, lets have a look at it. 

- Your CPU has 2 cores. For some reason, one of them (CPU 1) is is stuck at max_freq, the other (CPU 0) seems to be oscillating between min_freq and max_freq.

- Why does it only have two available frequencies? I'm an AMD user. But I doubt an Intel Core 2 CPU can only have two frequencies. This is wrong IMHO. I'd like to hear from people that have Intel CPUs here.

-  Scaling governor is OK (ondemand). 

Lets try this:

```

grep CPU_FREQ /lib/modules/`uname -r`/build/.config
sudo -s
echo 1596000 > /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
echo 1596000 > /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq
echo 1596000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
echo 1596000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_cur_freq

```

QUESTIONS:
- How is the CPU load after the commands above?
- What is your Motherboard vendor / model?
- BIOS settings: Did you disable CPU Stepping features?
- BIOS settings: Did you activate any overclocking feature? Is the BIOS CPU speet set to 2.4GHz? Is the clock set to default (probably 266MHz)?
- If not, try setting the above, restart and verify that you have new possible frequencies: sudo cat/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies


Regards,
Effenberg


--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)

thank you 

still running at 70 % just checked 

this is the output , notice permission denied 

s@main-desktop:~$ grep CPU_FREQ /lib/modules/`uname -r`/build/.config
CONFIG_CPU_FREQ=y
CONFIG_CPU_FREQ_TABLE=y
CONFIG_CPU_FREQ_STAT=y
CONFIG_CPU_FREQ_STAT_DETAILS=y
CONFIG_CPU_FREQ_DEFAULT_GOV_PERFORMANCE=y
# CONFIG_CPU_FREQ_DEFAULT_GOV_POWERSAVE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_USERSPACE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_ONDEMAND is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_CONSERVATIVE is not set
CONFIG_CPU_FREQ_GOV_PERFORMANCE=y
CONFIG_CPU_FREQ_GOV_POWERSAVE=y
CONFIG_CPU_FREQ_GOV_USERSPACE=y
CONFIG_CPU_FREQ_GOV_ONDEMAND=y
CONFIG_CPU_FREQ_GOV_CONSERVATIVE=y
s@main-desktop:~$ 
s@main-desktop:~$ sudo -s
[sudo] password for s: 
root@main-desktop:~# echo 1596000 > /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
bash: /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq: Permission denied
root@main-desktop:~# echo 1596000 > /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq
bash: /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq: Permission denied
root@main-desktop:~# 

I don think i have enabled bios stepping , just accepted the default  it was ok before with 11.04 ...all was well then , but in a fit of madness I upgraded 

thanks Stephen

it would be a pain to do a fresh install,  while this is not my work pc , it does have one or two movies on it !!!!

---

### Post by effenberg0x0 on 2011-09-13
Reading a little more, it became clear to me that you might not be running this CPU at its specs. It is not unusual to have wrong speeds / FSB set in the PC BIOS. You will find many bug reports about Intel processors reporting wrong speeds to Linux if they are overclocked. Asus, Gigabit and other motherboards have "A.I" settings (and features with other names", that "automagically" increase FSB or CPU multipliers to extract an overclocked performance from the CPU. Many times Linux does will handle that OK without some tweaking (cpufreq-set, etc).

If this is the case, reinstalling won't fix the problem. You can actually try this theory by using a Ubuntu Live USB. You can use Universal USB Installer, from [http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe), to download and burn a previous version of Ubuntu to a USB drive. Boot from it in Live mode and check your system / cpu load, available frequencies. The tests we have done above.

But, before going through all that, look at your BIOS man. I really think you should check your PC BIOS, load its default settings,  verify that Speedstep is enabled, disable "overclocking / performance"  features, check that it is set to the right FSB (I think 266) and  multiplier, etc. The tests we done above show that Linux is not getting correct information for your CPU from the BIOS.

Regards,
Effenberg

---

### Post by basilwatson on 2011-09-13
> **effenberg0x0 said:**
> Reading a little more, it became clear to me that you might not be running this CPU at its specs. It is not unusual to have wrong speeds / FSB set in the PC BIOS. You will find many bug reports about Intel processors reporting wrong speeds to Linux if they are overclocked. Asus, Gigabit and other motherboards have "A.I" settings (and features with other names", that "automagically" increase FSB or CPU multipliers to extract an overclocked performance from the CPU. Many times Linux does will handle that OK without some tweaking (cpufreq-set, etc).

If this is the case, reinstalling won't fix the problem. You can actually try this theory by using a Ubuntu Live USB. You can use Universal USB Installer, from [http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe), to download and burn a previous version of Ubuntu to a USB drive. Boot from it in Live mode and check your system / cpu load, available frequencies. The tests we have done above.

But, before going through all that, look at your BIOS man. I really think you should check your PC BIOS, load its default settings,  verify that Speedstep is enabled, disable "overclocking / performance"  features, check that it is set to the right FSB (I think 266) and  multiplier, etc. The tests we done above show that Linux is not getting correct information for your CPU from the BIOS.

Regards,
Effenberg


been into bios , there really isnt much there to change , no over clocking or anything ,,,,
just basic 

have on another partition ubuntu 9.04 kernel 2.6.31.19

and it runs fine , cpu at 10 % cpu 1 at 0 % 

so it is 11.10 , something in this upgrade is causing my cpus to run at 80 % ...

what is it 

soething crashes, shortly after start up as well but it doesn't say , I just get a warning

So 

how do we find out which process ( just checked ) is causing my cpus to run at 80 %

the attached screen shots are of ubuntu 9.04 

kind regards 

Stephen

---

### Post by effenberg0x0 on 2011-09-13
Ok, new game plan. We know your CPU freqs are wrong. We know Linux has problems getting them from BIOS sometimes. There are reports of people with similar CPU with the same problem. Let's attack it.

**1st) **Let's make sure nothing is trying to control your cpu speed but the correct kernel module (acpi-cpufreq). We will teach it the speeds and governors manually and see if it works.

**2nd) **If first strategy fails, we will go userspace with cpufreqd. I use because Linux can't understand my Phenom II X6 speeds. We will use cpufreq-utils to teach it the speeds and governors.

**STRATEGY 1**

We will make sure you don't have any wrong module loaded (modules for Centrino, AMD CPUs, Pentium, etc).
```

sudo modprobe -r powernow-k6 
sudo modprobe -r speedstep-ich 
sudo modprobe -r speedstep-smi 
sudo modprobe -r powernow-k7 
sudo modprobe -r powernow-k8 
sudo modprobe -r longhaul
gksudo gedit /etc/modprobe.d/blacklist.conf 

```Let's blacklist modules that are not fit for an Intel C2D CPU. Add, to the last lines of blacklist.conf, the following lines:
```

blacklist powernow-k6
blacklist powernow-k7
blacklist powernow-k8
blacklist speedstep-ich
blacklist speedstep-smi
blacklist longhaul

```Lets add acpi-cpufreq, the correct module for a C2D CPU, to the list of modules to be loaded at boot time.
```

gksudo gedit /etc/modules

```Add the following line to the end of the file:
```

acpi-cpufreq

```Install cpufreqd and cpufrequtils
```

sudo apt-get install cpufreqd cpufrequtils

```Reboot. Tell me what is the output is for:
```

sudo cpufreq-info

```Here's a sample for my CPU, which uses the powernow-K8 module. The important thing is that is shows the correct min/max speeds.

```

analyzing CPU 5:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 5
  CPUs which need to have their frequency coordinated by software: 5
  maximum transition latency: 8.0 us.
  hardware limits: 800 MHz - 3.50 GHz
  available frequency steps: 3.50 GHz, 2.50 GHz, 1.70 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 3.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 3.50 GHz:1,04%, 2.50 GHz:0,07%, 1.70 GHz:0,06%, 800 MHz:98,84%  (11098)


```Regards,
Effenberg

---

### Post by VinDSL on 2011-09-13
> **basilwatson said:**
> something crashes, shortly after start up as well but it doesn't say , I just get a warning[...]
Aha!  That rang a bell...

Sounds like the ol' apport bug.

Try turning apport off, if you haven't already done so.

```

sudo sed -i 's/enabled=1/enabled=0/g' /etc/default/apport

reboot

```

---

### Post by basilwatson on 2011-09-15
> **effenberg0x0 said:**
> Ok, new game plan. We know your CPU freqs are wrong. We know Linux has problems getting them from BIOS sometimes. There are reports of people with similar CPU with the same problem. Let's attack it.

[/code]Regards,
Effenberg

Thanks 

I have done what u said , here is the output , I will do it again to double check  ( just checked using system monitor , both cpu at 60 %)

Stephen

may have done something wrong as speed seems similar after reboot 


s@main-desktop:~$ sudo cpufreq-info
[sudo] password for s: 
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 1.60 GHz - 2.39 GHz
  available frequency steps: 2.39 GHz, 1.60 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.39 GHz and 2.39 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.39 GHz (asserted by call to hardware).
  cpufreq stats: 2.39 GHz:99.94%, 1.60 GHz:0.06%  (8)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 1.60 GHz - 2.39 GHz
  available frequency steps: 2.39 GHz, 1.60 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.39 GHz and 2.39 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.39 GHz (asserted by call to hardware).
  cpufreq stats: 2.39 GHz:100.00%, 1.60 GHz:0.00%
s@main-desktop:~$

---

### Post by effenberg0x0 on 2011-09-15
I was right. Do you see how wrong this is? Look at this excerpt. The "On demand" governor can't reduce the speed of your CPU. No wonder it is constantly loaded. Even if it did, your BIOS reports two speeds only, which is also wrong.

```

hardware limits: _**1.60 GHz - 2.39 GHz**_  
available frequency steps: _**2.39 GHz, 1.60 GHz**_   
available cpufreq governors: conservative, ondemand, userspace, powersave, performance   
current policy: frequency should be within _**2.39 GHz and 2.39 GHz.**_ 
The governor "_**ondemand**_" may decide which speed to use within this range.   
current CPU frequency is 2.39 GHz _**(asserted by call to hardware).**_

```

At this point I am assuming that if you are absolutely sure that your CPU is properly configured (no overclocking, proper FSB) as I had asked you some posts above, acpi-cpufreq is not compatible with your CPU /BIOS/Motherboard OR you may have ACPI off. It may happen, there are some posts that refer to it on the net. 

I honestly think that theres something wrong in BIOS setup or functionality. I can create this behavior in my PC by setting my FSB or multiplier too high. 

I do not think using a userspace CPU frequency program, such as I had mentioned using cpufreqd will work. The BIOS reports only two speeds the cores. No userspace program will, in my opinion, be able to overcome this limitation.

Just as a lame attempt, give it a try :)

```

sudo cpufreq-set -c 0 -g ondemand -d 800Mhz -u 2.40Ghz -r
sudo cpufreq-set -c 1 -g ondemand -d 800Mhz -u 2.40Ghz -r

```

Wild guessing: Do you think maybe this could be acpi related? Have you ever tried to add acpi=force and acpi=on to the end of your boot line on grub? If you have acpi=off there, remove it! Press shift to see grub when PC is booting, press C to edit the boot line, add acpi=force to the end of the line and proceed with boot. See if cpufreq-info shows you more viable / normal frequency options using cpufreq-info. Again, wild guessing here.

Regards,
Effenberg

---

### Post by basilwatson on 2011-09-15
> **effenberg0x0 said:**
> I was right. Do you see how wrong this is? Look at this excerpt. The "On demand" governor can't reduce the speed of your CPU. No wonder it is constantly loaded. Even if it did, your BIOS reports two speeds only, which is also wrong.

```

hardware limits: _**1.60 GHz - 2.39 GHz**_  
available frequency steps: _**2.39 GHz, 1.60 GHz**_   
available cpufreq governors: conservative, ondemand, userspace, powersave, performance   
current policy: frequency should be within _**2.39 GHz and 2.39 GHz.**_ 
The governor "_**ondemand**_" may decide which speed to use within this range.   
current CPU frequency is 2.39 GHz _**(asserted by call to hardware).**_

```

At this point I am assuming that if you are absolutely sure that your CPU is properly configured (no overclocking, proper FSB) as I had asked you some posts above, acpi-cpufreq is not compatible with your CPU /BIOS/Motherboard OR you may have ACPI off. It may happen, there are some posts that refer to it on the net. 

I honestly think that theres something wrong in BIOS setup or functionality. I can create this behavior in my PC by setting my FSB or multiplier too high. 

I do not think using a userspace CPU frequency program, such as I had mentioned using cpufreqd will work. The BIOS reports only two speeds the cores. No userspace program will, in my opinion, be able to overcome this limitation.

Just as a lame attempt, give it a try :)

```

sudo cpufreq-set -c 0 -g ondemand -d 800Mhz -u 2.40Ghz -r
sudo cpufreq-set -c 1 -g ondemand -d 800Mhz -u 2.40Ghz -r

```

Wild guessing: Do you think maybe this could be acpi related? Have you ever tried to add acpi=force and acpi=on to the end of your boot line on grub? If you have acpi=off there, remove it! Press shift to see grub when PC is booting, press C to edit the boot line, add acpi=force to the end of the line and proceed with boot. See if cpufreq-info shows you more viable / normal frequency options using cpufreq-info. Again, wild guessing here.

Regards,
Effenberg

well ive never really touched the bios , and had no problem before , but Ill have a look 

will post back

 at least we are on to some thing...... 

ok there is nothing really in my bios to change cpu frequency . max cpuid limit . and Hpet ( high precision timer ) 

Im trying acpi 
Stephen 



Stephen

---

### Post by basilwatson on 2011-09-15
here is muy grub file , Im just playing with this now 

Stephen 
 If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=enable pci=noacpi pci=assign-busse acpi=ht "
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)

^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by basilwatson on 2011-09-15
I dont know 

this is what I do know

doesn't happen / didn't happen with 9.04 and 11.04 

Cpu goes up at the same time the unity panel starts , tried killing unity  nothing 

modifying grub hasn't helped 

BIOS , there is nothing in there about setting fsb, so I just set to optimal default

there seem to be no processes  running , apart from desktop,  


the scaling of the CPU seems a good candidate, 

But I'm lost now 

and the cpu is still humming away 

Thanks for all the help  so far ! 

Stephen

---

### Post by effenberg0x0 on 2011-09-20
Hi, sorry for the delay, I've been traveling abroad with very limited Internet access and could not keep up with the posts here. 

Your Grub default Linux command-line seems a little too crowded of workarounds IMHO. I don't know what the origin of all this workarounds is. I have only "noquiet" enabled as an option because I like to see my boot messages and don't care about hiding them. You have "quiet splash acpi=enable pci=noacpi pci=assign-busse acpi=ht".

I am not familiar with acpi=ht but searching for it I found this: (see [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions))

> acpi=ht (...) Deactivates the ACPI system almost completely; only the components required for hyper threading will be used. I don't like it. We need acpi.

I suggest you try the following settings:

```

GRUB_CMDLINE_LINUX_DEFAULT=""

```Save the file, run sudo update-grub and reboot

OR

```

GRUB_CMDLINE_LINUX_DEFAULT="acpi=force"

```Save the file, run sudo update-grub and reboot

Check, using cpufreq-info and top (which we already used in this thread to prove the defective behavior), if you can see change or/and a more proper behavior of the CPU core speeds. Basically were trying to get your BIOS to inform the kernel of the proper speeds and steps for your CPU - this is done through acpi.

Wild guessing: Some motherboard (such as mine) have a switch that automatically overclocks the CPU. Its becoming usual in ASUS, Gigabyte, MSI, ASRock, etc. In my ASUS, this switch messes with CPU Frequency Scalling, so I keep it off. Also, overclocking this way or through any other automatic way is generally lame and not as effective as a proper manual overclock. So if you have such a switch / jumper, you loose nothing by disabling it. If you don't have the manual for your motherboard, you will find it easily in the manufacturer website.

Wild guessing again: See that you have setting such as ahci, ehci, *hci, acpi in your BIOS. If you do, play a little with them, as all of them may have an impact on how acpi works (according to numerous bug reports you'll find on Google).

Start with the Grub changes I suggested and lets go from there.

Regards,
Effenberg

---

