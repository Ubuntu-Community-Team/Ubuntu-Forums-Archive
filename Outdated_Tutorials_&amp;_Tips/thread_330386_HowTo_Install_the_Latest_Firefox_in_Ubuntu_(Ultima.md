---
title: "HowTo Install the Latest Firefox in Ubuntu (Ultimate HowTo)"
date: 2005-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by aysiu on 2005-05-24
**What's the issue?**
Ubuntu updates its software versions every six months with a new release. Mozilla, however, upgrades Firefox every month or two--sometimes every week--with security patches or new feature-based releases. Ubuntu often includes security patches with its own versions a day or a week after Mozilla releases their patches, but many Ubuntu users are impatient and would prefer to install the latest version of Firefox from Mozilla and use that instead of the Ubuntu build of Firefox.

Basically almost all of the methods outlined below do essentially the same thing--download Firefox from the Mozilla website and use that instead of Ubuntu's Firefox. Most also "install" Firefox to the /opt directory.

**What are the methods?**

*Manual* - This involves copying and pasting a lot of terminal commands to get Firefox fully integrated with your system. If you want to learn some terminal commands and get to know your system a little better, this is a great way to install the latest Firefox. Instructions are here:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

*Automated* - This script basically takes the commands in the manual version and saves you the trouble of copying and pasting them all. It also automates a few other things--it automatically detects and downloads the latest version of Firefox, it allows you to select your locale, and it verifies the integrity of the download.
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

*Manual with no integration* - All the aforementioned methods assume you want the command *firefox* to launch the new Firefox from Mozilla, that you want your plugins to work with Firefox, and that you want Firefox to be "installed" systemwide for all users. If you just want Firefox to be able to run but not be integrated with plugins or run with the regular *firefox* command or able to be run by all users easily, then just download the Firefox .tar.gz file from Mozilla to your desktop or home folder, double-click it (or single-click if you're using Kubuntu), extract the .tar.gz using File-Roller or Ark, go to the newly created folder and double-click (or single-click for Kubuntu) the file called *firefox*. That will launch Firefox.

*Use Klik* - Klik is a way to install software directly off the web but not using your regular package manager.
First learn how to use Klik:
[http://klik.atekon.de/wiki/index.php/How_to_use_klik](http://klik.atekon.de/wiki/index.php/How_to_use_klik)

Then get Firefox from Klik:
[http://firefox.klik.atekon.de/](http://firefox.klik.atekon.de/)

*Stick with the Ubuntu version of Firefox* - Ubuntu will continue to update Firefox with security patches as long as they support the release you're using (Dapper, as of this writing, is supposed to be supported for three years). The security patches may not come immediately when Mozilla releases them, but they usually come within a week. 

*Edit*: Actually, since you are not the root user on your system, the *Check for Updates* button in Firefox will be greyed out, even if you use the Mozilla version. For more details on how to install upgrades, see [this post](http://ubuntuforums.org/showthread.php?p=2222326#post2222326).

A combination of the *manual* and *manual with no integration* methods can be found [here](http://ubuntuforums.org/showthread.php?p=2392054#post2392054).

**Why this thread?**
There were way too many HowTos on installing the latest Firefox, so I'm creating the ultimate HowTo that outlines the major methods. It's better for new users to have one place to find all the major ways to upgrade than fifteen different HowTos of varying quality. Any "new" upgrade-to-Firefox HowTos will simply be merged into this thread. If a method is actually new and not just a rehash of another method, I'll incorporate that new method into this initial post.

---

### Post by shakin on 2005-06-10
This install should not harm your existing Firefox installation. This basically walks you through the official Firefox installer and is mainly for the benefit of people who are worried that it might harm their system or that they might do it incorrectly and overwrite their existing Firefox version.

Let's roll...

Backup your firefox profile, just in case the new version corrupts it (nothing bad happened to my profile).
```

$ cd ~/.mozilla
$ tar -cMf firefox.tar firefox/

```

Now install Firefox 1.1 Alpha 1.
```

$cd ~
$ wget ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/deerpark/alpha1/linux-i686/en-US/deerpark-alpha1.installer.tar.gz
$ tar -zxf deerpark-alpha1.installer.tar.gz
$ sudo firefox-installer/firefox-installer

```

Installer wizard (custom install):

1. Click Forward
2. Click Accept
3. Select Custom for install type
4. Click Forward
5. Click "Yes" to create the directory
6. Select any components you want to install.
7. Click Forward.
8. Click Install.

Run Firefox 1.1
```

$ /usr/local/firefox/firefox

```

Use the above executable when making a shortcut. Do *not* use the firefox-bin executable.

---

### Post by Kyral on 2005-06-10
Works perfectly! I heart much :D

---

### Post by pdk001 on 2005-06-10
i will try it thx guy

---

### Post by vassalle on 2005-06-10
great tip! tried it but somehow the plugins are not in there.. any shortcuts on how i can get the working plugins in my old firefox to work with the new firefox 1.01 ?

---

### Post by shakin on 2005-06-10
[QUOTE=vassalle]great tip! tried it but somehow the plugins are not in there.. any shortcuts on how i can get the working plugins in my old firefox to work with the new firefox 1.01 ?[/QUOTE]

Plugins or extensions?

Plugins like Flash Player are in ~/.mozilla/plugins and should be shared. I'm not sure about Java or mplayer... I haven't checked those yet.

Some of your extensions will be disabled until you update them. TabBrowser prefs and all-in-one gestures were disabled for me until I clicked the update icon in the corner of the browser window. Greasemonkey is still disabled until they release an update.

---

### Post by notos on 2005-06-11
i have made this (instaled it in /opt/deerpark) rember its a alpha and should be installed for Testing Propouses Only you should make it clear for newbie users :)

---

### Post by JimmyJazz on 2005-06-27
how do I remove it so i can use the regular version?

---

### Post by shakin on 2005-06-28
[QUOTE=JimmyJazz]how do I remove it so i can use the regular version?[/QUOTE]

You need to update your shortcuts so intead of pointing to '/usr/local/firefox/firefox' they just point to 'firefox'.

You can also remove the /usr/local/firefox directory if you want to reclaim the disk space.

---

### Post by fishfork on 2005-10-19
How to do it **without** messing up your system and confusing the package manager (hopefully!)

The Howto is on the wiki at [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion). Comments here please.

---

### Post by chanders on 2005-10-20
Any particular reason you want to use version 1.05? If not, then you can get the latest using synaptic.

One common problem people usually have is that they dont uninstall Firefox first. Dont worry, ALL of your stuff will be safe, including your bookmarks etc. When uninstalling the old version just select remove, NOT completly remove.

When it is finished, look for it again (mozilla-firefox) and then mark for installation. When it is installed you should have a brand spanking new Firefox.

---

### Post by aysiu on 2005-10-20
1.5 is the newest beta version.
1.05 was too versions ago from the latest stable version (1.07).
They're different.
1.5 is not in the repositories--hence the HowTo.

---

### Post by chanders on 2005-10-20
Didnt know a 1.5 beta existed..... I stand enlightened :D

---

### Post by aysiu on 2005-10-20
[QUOTE=chanders]Didnt know a 1.5 beta existed..... I stand enlightened :D[/QUOTE] I'm using beta now. It's great. Very speedy. And extension developers have been slowly updating to be compatible with 1.5 (I'd say it's about 50/50 now on extension compatibility).

---

### Post by crypto178 on 2005-10-20
Great how-to, worked with no issues and I can feel the speed difference.
Could someone explain what does the dpkg-divert step?

EDIT : woops, the totem plugin doesn't work anymore (firefox closes down when browsing pages with embedded videos in it), anyone else experiencing that?

---

### Post by dlpfmVfH on 2005-10-20
[quote=crypto178]Great how-to, worked with no issues and I can feel the speed difference.
Could someone explain what does the dpkg-divert step?

EDIT : woops, the totem plugin doesn't work anymore (firefox closes down when browsing pages with embedded videos in it), anyone else experiencing that?[/quote]

Me too...totem doesn't work in beta, but it works in the 1.07...so it is plugin related..cause we copied the plugins from 1.07 to the beta...

---

### Post by No6 on 2005-10-20
If you want speed, have you tried fasterfox? [http://fasterfox.mozdev.org/]("http://fasterfox.mozdev.org/")

It is great. (Also works in 1.0x)

---

### Post by Syphin on 2005-10-20
wow this loads alot faster then i thought it would, thanks :)

Might want to note in the howto, I just did a fresh system install, and had to install 'libstdc++5' before firefox1.5 would launch at all.  after that, works great :)

---

### Post by guyomarj on 2005-10-20
Nice and easy...

And, yes, it IS faster.

---

### Post by fishfork on 2005-10-20
[QUOTE=crypto178]woops, the totem plugin doesn't work anymore (firefox closes down when browsing pages with embedded videos in it), anyone else experiencing that?[/QUOTE]
Your right. I think the plugin's not compatible with 1.5. I've updated the howto. I've also changed it to link to the plugins instead of copying them, which is probably a better way to do it.

---

### Post by Cl1mh4224rd on 2005-10-21
Thanks for this. :)

I do have a minor problem, though, and it concerns extensions. Every one I've installed so far has given me a "chrome registration" error, and yet seems to install and work just fine. Has anyone else had this problem? I did have the older version running when I first ran 1.5b2, though. Anyone think that could've been the cause? If so, is there anyway to correct it?

---

### Post by Ivhassel on 2005-10-22
[QUOTE=Cl1mh4224rd]Thanks for this. :)

I do have a minor problem, though, and it concerns extensions. Every one I've installed so far has given me a "chrome registration" error, and yet seems to install and work just fine. Has anyone else had this problem? I did have the older version running when I first ran 1.5b2, though. Anyone think that could've been the cause? If so, is there anyway to correct it?[/QUOTE]


I'm practically sure you have the AdBlock plugin, and that's what's causing your troubles. Try uninstalling it. Worked for me to solve this, though I had to restart Firefox twice :???:

---

### Post by Van_Gogh on 2005-10-22
[QUOTE=Ivhassel]I'm practically sure you have the AdBlock plugin, and that's what's causing your troubles. Try uninstalling it. Worked for me to solve this, though I had to restart Firefox twice :???:[/QUOTE]

Hi,

I just installed Mozilla Firefox 1.5 and I had the same problem as Ivhassel the first time I started FF 1.5 up and I positively don't have adblock installed.

However, It was just the first time I started up and gone now...

---

### Post by Cl1mh4224rd on 2005-10-22
[QUOTE=Ivhassel]I'm practically sure you have the AdBlock plugin, and that's what's causing your troubles.[/QUOTE]
Unfortunately, no... I don't have AdBlock installed. :|

---

### Post by beeldings on 2005-10-23
Thank you for such a helpful guide. I cannot believe how much faster the Beta version is compared to the Ubuntu build. The only problems I experienced when I installed the Beta version was that I had to reset my preferences and reinstall all of my extensions. I loaded in Fasterfox and now my Firefox blows Opera and Epiphany out of the water!

---

### Post by wellery on 2005-10-23
I'm getting an error:

```
/opt/firefox/firefox-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

---

### Post by wellery on 2005-10-23
[quote=wellery]I'm getting an error:

```
/opt/firefox/firefox-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```[/quote]

Ignore. It's fixed now. I just had to install the libstdc++5 package.

---

### Post by drummer on 2005-10-23
Holy. Friggin. Crud monkeys... Beta 2 is soooo fast!! I *LOVE* it :D

I too had an error pop up about the chrome registry.. can't remember what it said though. I didn't have my old bookmarks in beta 2 even after copting bookmarks.html from the old .mozilla directory. So I just moved my old .mozilla directory back to where it was (~/.mozilla) and opened beta 2.. the error popped up again but it seems fine now. I also looked it .mozilla and it looks like it created a separate chrome profile for itsself (or whatever it's called, 7dblah.default)... as long as it's working I'm happy, and I don't think I'll be going back to the default/stable firefox any time soon :P

The forms need some prettying up though - [http://gnome-look.org/content/show.php?content=21812](http://gnome-look.org/content/show.php?content=21812)

---

### Post by Footer on 2005-10-23
[QUOTE=fishfork]How to do it **without** messing up your system and confusing the package manager (hopefully!)

The Howto is on the wiki at [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion). Comments here please.[/QUOTE]

Great 'How to' ... Thanks!  But my question is this:  Why is the Ubuntu build of Firefox so slow???  This could be bad news for someone trying out Ubuntu for the first time since browsing the web is most likely one of the first things they'd try ... right?  It takes almost FOREVER to load and everything about it feels sluggish yet the exact same version from Mozilla makes a world of speed difference.

I'm currently using ver. 1.0.7 from Mozilla and it works great.  I tried ver. 1.5 beta and it's even better and I'd use it right now if more of my favorite extensions worked ... Thus, I wait.

:)

---

### Post by linasgricius on 2005-10-23
Ubuntu 5.10, FF 1.5b2 - unable to use "HELP->Check for updates..." menu... Am I alone?

---

### Post by bored2k on 2005-10-23
Update menu worked here.

---

### Post by Donza on 2005-10-23
Update menu isn't working. What could be the problem? I have installed extensions: mouse gestures, fasterfox, downthemall, adblock plus.

---

### Post by XDevHald on 2005-10-23
[QUOTE=Donza]Update menu isn't working. What could be the problem? I have installed extensions: mouse gestures, fasterfox, downthemall, adblock plus.[/QUOTE]
If it's not enabled that means it's not ready for updates to be processed. I have the Check for Updates, but it's not highlighted for clicking.

Is what you mean?

---

### Post by 23meg on 2005-10-23
Is there any word on when approximately 1.5 will be final?

---

### Post by linasgricius on 2005-10-23
[QUOTE=linasgricius]Ubuntu 5.10, FF 1.5b2 - unable to use "HELP->Check for updates..." menu... Am I alone?[/QUOTE]

I've made some changes: 

chown my_user:my_group -R /opt/firefox/*

as it was root'ed.

After that menu is enabled.

And problem was with flash plugin: I had to install it by hands...

---

### Post by fishfork on 2005-10-23
[QUOTE=Footer]Great 'How to' ... Thanks!  But my question is this:  Why is the Ubuntu build of Firefox so slow???[/QUOTE]

Glad I'm not the only one to have noticed this then! I don't know why it's so slow, but it is extremely annoying on slightly older hardware. There's a [bug open about it](http://bugzilla.ubuntu.com/show_bug.cgi?id=15534), but no progress - seems it may be due to some of the patches in the Ubuntu version.

---

### Post by sailor420 on 2005-10-24
Very good and very fast, but it doesnt seem to have imported my profile... Any ideas?

---

### Post by Footer on 2005-10-24
[QUOTE=fishfork]Glad I'm not the only one to have noticed this then! I don't know why it's so slow, but it is extremely annoying on slightly older hardware. There's a [bug open about it](http://bugzilla.ubuntu.com/show_bug.cgi?id=15534), but no progress - seems it may be due to some of the patches in the Ubuntu version.[/QUOTE]

Imagine if you're a brand new Linux user and out to try Linux for the first time...and you try Ubuntu/Kubuntu.  And assume you have fairly new hardware (P4/Athlon XP 3000+).  All goes well with the install, all hardware recognized, all is well so far!  Then you say, let's browse the Internet and see how that goes?  You quickly realize that your browsing experience is quite hampered by a sluggish Firefox.  And you say <gasp>, I guess I'll just stick to Windows, Linux is STILL not ready for primetime!

Fortunately, this was not the scenario for me as I've been using Linux for awhile ... But this would truly be ashame for any Linux newb out there.

Well, I'm glad to see there's a bug open about it but it appears that it may not get resolved until Dapper ... <sigh>

---

### Post by fishfork on 2005-10-24
[QUOTE=Footer]And assume you have fairly new hardware (P4/Athlon XP 3000+).[/QUOTE]
Is the slowdown noticeable on a machine this fast? If so all I can say is ... wow, how did they mess it up so badly? :( Thought it would only make a difference on old machines like my Athlon 800.

---

### Post by drummer on 2005-10-24
[QUOTE=fishfork]Is the slowdown noticeable on a machine this fast? If so all I can say is ... wow, how did they mess it up so badly? :( Thought it would only make a difference on old machines like my Athlon 800.[/QUOTE]
I was getting lag of about 5 or so seconds when FF was rendering some pages.. it just locked up for that time, with 100% cpu usage. And that's on an Athlon64 3000, 512meg ram :?

---

### Post by Footer on 2005-10-24
[QUOTE=fishfork]Is the slowdown noticeable on a machine this fast? If so all I can say is ... wow, how did they mess it up so badly? :( Thought it would only make a difference on old machines like my Athlon 800.[/QUOTE]

Yes, it is quite noticeable.  I have an Athlon XP 3000+ with 1GB of RAM and it took about FOREVER to just load Firefox itself!  Seriously, I would sit there and watch the bouncing fox for a good 30-45 seconds before the browswer would even come up and start to load pages.  Very pathetic.  The 1.0.7 build from Mozilla loads in mere seconds.

---

### Post by vassie on 2005-10-25
[quote=linasgricius]I've made some changes: 

chown my_user:my_group -R /opt/firefox/*

as it was root'ed.

After that menu is enabled.

And problem was with flash plugin: I had to install it by hands...[/quote]

I had a problem installing the Flash plugin too, I found that if you close the installer screen and kept try, it will install, had to do it about 5 times

Ben

---

### Post by Mr_J_ on 2005-10-26
I followed the entire thing up to where I'm suposed to start firefox with the firefox command and it won't start with that command.
I wen't to Opt and started it up myself.
Got some chrome errors, which I believe is due to some pluggins I had, but I don't mind that.

My shortcut to start firefox won't start because the firefox command doesn't exist.
Everything seems to work... In terms of the HOWTO that is.
The thing is. I was using Firefox to read to HOWTO, so it was open while the changes where being made. Could that affect the result?
I have the lib mentioned earlier in the howto.

---

### Post by corbs83 on 2005-10-26
.

---

### Post by fishfork on 2005-10-26
[QUOTE=Mr_J_]My shortcut to start firefox won't start because the firefox command doesn't exist.[/QUOTE]
It should exist! What does ```
ls -l /usr/bin/firefox*
``` give?

---

### Post by fishfork on 2005-10-26
[QUOTE=corbs83]MIddle clicking a tab used to close it, now it loads CNN.com

What the?!

EDIT: In fact, it just seems to load a random site. How can I return to the good old days of the middle-click close?

By the way though, thanks for install guide for Fx 1.5 beta2 ... It's so much faster than the default.[/QUOTE]

How bizarre! It seems to be doing a google I'm Feeling Lucky search on the clipboard contents, or maybe something else. You could try [forums.mozillazine.org](forums.mozillazine.org) - someone there might know why it does this.

---

### Post by bionnaki on 2005-10-28
I can only run this as root from the terminal.

the output from ls -l /usr/bin/firefox* gives:

> bill@ubuntu:~$ ls -l /usr/bin/firefox*
lrwxrwxrwx  1 root root 20 2005-10-28 00:01 /usr/bin/firefox -> /opt/firefox/firefox
lrwxrwxrwx  1 root root 30 2005-10-26 05:03 /usr/bin/firefox.ubuntu -> ../lib/mozilla-firefox/firefox
bill@ubuntu:~$


any ideas on how to change this?

---

### Post by kakashi on 2005-10-28
i have just read the tutotrial and have have 1 comment. 
don't install 1.5B as default firefox. 

best thing to do is to unpack firefox in you home direcotry and launch it using the script given or  create a launcher for it and place it on your taskbar.

---

### Post by bionnaki on 2005-10-28
why?

---

### Post by drummer on 2005-10-28
[QUOTE=kakashi]i have just read the tutotrial and have have 1 comment. 
don't install 1.5B as default firefox. 

best thing to do is to unpack firefox in you home direcotry and launch it using the script given or  create a launcher for it and place it on your taskbar.[/QUOTE]
If it's not set as the default FF, opening a link from any other application will load in the old FF, not the beta 2.

@bionnaki: perhaps the 'firefox' file that's linked to doesn't have the right permissions, should probably be 755 to allow every user to execute it.

---

### Post by bionnaki on 2005-10-28
I figured it out.
thanks!

---

### Post by b_chris on 2005-10-29
Ok stupid question, how do you install package libstdc++5 ??

I know, I know, but I'm only new.

regards.

---

### Post by Arktis on 2005-10-29
```
sudo apt-get install libstdc++5
```
OR
Open up synaptec, search for libstdc++5, and install it from there.

---

### Post by b_chris on 2005-10-29
Thank-you.

---

### Post by subliminal on 2005-10-29
Everything worked first time, but not having you're preferences, and if you use firefox to store passwords etc is a little annoying.
I tried to copy individual files over but, the new firefox didnt like them, so i copied the whole directory over ~/.mozilla.ubuntu/firefox/<profile name> to ~/.mozilla/firefox/ and changed the profiles.ini file at ~/.mozilla/firefox/profiles.ini 
```

...
[Profile0]
...
Path=<profile name>
...

```

For, example my old mozilla profiles ~/.mozilla.ubuntu/firefox/fnsyg2jk.slt was moved to ~/.mozilla/firefox/fnsyg2jk.slt and profiles.ini now looks like
```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=fnsyg2jk.slt


```

(Incidentally this profile folder has been with me since a much older version of the mozilla suite.)

When I started mozilla I got a chrome error thing, it checked out my extensions, told me they wouldnt work and asked if I wanted to check for updates, I did and most now work. No sign of any more chrome error things so I assume it's happy. :D

---

### Post by GoA on 2005-10-30
Is adblock working for everyone? If yes then I have a problem. It doesn't show any links to block ads.

---

### Post by bionnaki on 2005-10-30
adblock seems broken...
it'll block ads just fine, but you
have to right>click>copy image location
and manually enter this link into
adblock (tools>adblock>preferences)

---

### Post by MihaiM on 2005-10-31
[QUOTE=linasgricius]I've made some changes: 

chown my_user:my_group -R /opt/firefox/*

as it was root'ed.

After that menu is enabled.

And problem was with flash plugin: I had to install it by hands...[/QUOTE]
I did chown the files to my user but still not solved. Check for updates is still not clickable.

I've installed flash manually too

---

### Post by 23meg on 2005-10-31
Anyone using Tab Mix or Tab Mix Plus? Is the option for saving sessions working for you?

---

### Post by openmind on 2005-10-31
For everyone having trouble with extensions on 1.5beta, The [Nightly Tester Tools Extension]("http://users.blueprintit.co.uk/%7Edave/web/firefox/buildid/nightly.html") will get most of them running in this version. There's a couple I'm still having problems with, but 90% of them will work with this extension.

---

### Post by MihaiM on 2005-10-31
Did someone figure out how to enable the "Check for updates" funtion?
I ask because Firefox 1.5 PR1 shoud be out any moment now and it would be nice to have it updated automatic when it comes out.

---

### Post by .Danny on 2005-10-31
Flash is still not working for me. I have sound however I don't see any actual content.

Can anyone tell me which plugins firefox uses? Since there's like 3 or 4 plugins directory. I'd like to try deleting them all and then downloading the flash one from Macromedia itself.

---

### Post by CodeOptimist on 2005-10-31
Nice howto - I followed it and got 1.5b2 working under Breezy. However, I got the "chrome registration" (or somesuch) error as a couple other reported above when I first started Firefox. The second time I started it, there were no problems.

I installed some 1.5b2-compatible extensions (SessionSaver, Bookmarks Synchronizer, Tabbrowser Extensions) and received the message again after restarting Firefox. Again, the second time I started it, it was fine (and thereafter), but the extensions don't seem to be working. Even trying to access an extension "Preferences" dialog (via the Extensions panel) does nothing. I'm assuming this has something to do with the error message? Unfortunately, I didn't copy down the exact message, but I could try to reproduce it...

Any ideas? I'd really like to get these extensions working. :)

EDIT: Seems to be working now. I uninstalled the extensions, rebooted, and reinstalled them one-by-one. I did get the error again, but it turns out (by examining the terminal) that it was the TalkBack extension that was causing the issue.

---

### Post by .Danny on 2005-11-01
I am freaking out here. I just can't get flash to work no matter what I do. And the mplayer plugins either.

When i type about:plugins they are there and enabled but they don't seem to work. Why? :confused:

---

### Post by crypto178 on 2005-11-01
One workaround to the totem plugin issue mentionned earlier is simply to use the mplayerplugin, the one available in the repositories is very, very, nice (proper gtk2 control bar, excellent integration with firefox and most of all, plays just about everything if you have the appropriate codecs -w32codecs-, even realmedia,wmv,apple.com/trailers qt stuff)


[QUOTE=Lord Death]Flash is still not working for me. I have sound however I don't see any actual content.

Can anyone tell me which plugins firefox uses? Since there's like 3 or 4 plugins directory. I'd like to try deleting them all and then downloading the flash one from Macromedia itself.[/QUOTE]

If you followed this HOW-TO, you're using firefox 1.5 beta installed in /opt/firefox, right?
If it's the case, you can ~safely try these commands :
sudo rm -r /opt/firefox/plugins
sudo ln -s /usr/lib/mozilla-firefox/plugins /opt/firefox/plugins 

After that flash should be fine if it worked before (with breezy stock firefox). If it doesnt, please give us the output of
ls /usr/lib/mozilla-firefox/plugins/ 
and/or try to reinstall all necessary plugins using synaptic.

---

### Post by .Danny on 2005-11-01
I followed this tutorial yes. After I installed it and was done flash worked.. for a while. Then suddenly it stoped working. I've got no idea why or what I've done.

I tried to remove all plugin packages and reinstall but no go, even downloaded flash from their webpage but that one doesn't work either.

danny@Ryiah:~$ ls /usr/lib/mozilla-firefox/plugins/
flashplayer.xpt  libflashplayer.so

When I do about:plugins in Firefox they are there, and it says enabled. But it's just not working, no matter what I do. It's slowly driving me insane by now, trying to fix this for days.

---

### Post by sal on 2005-11-01
[QUOTE=linasgricius]I've made some changes: 

chown my_user:my_group -R /opt/firefox/*

as it was root'ed.

After that menu is enabled.

And problem was with flash plugin: I had to install it by hands...[/QUOTE]

yes, this worked to get rid of the chrome start error and also to let firefox use flash. let me ask you though, how would i go about getting sound in flash now.
thanks.

**Update:
i got sound in flash working by copying the mozilla-firefoxrc from the /etc/mozilla-firefox directory to the /opt/firefox directory

---

### Post by veloct on 2005-11-01
[QUOTE=linasgricius]I've made some changes: 

chown my_user:my_group -R /opt/firefox/*

as it was root'ed.

After that menu is enabled.

And problem was with flash plugin: I had to install it by hands...[/QUOTE]

Thanks for the tip.  Worked just great for me and it updated 1.5b2 to 1.5 RC 1 without a hitch.

---

### Post by MihaiM on 2005-11-01
New version is out and autoupdate does not work, even with the chown tip.
I would like to update with throught the updater, not by downloading the new version and manually unpack it in place.

---

### Post by magnusbb on 2005-11-02
No, auto-update does not work. But why do that? It's very simple to upgrade manually.

First remove the /opt/firefox directory. Then untar the new version to the same place. Then link the plugin directory with "/usr/lib/mozilla-firefox/plugins" - and restart Firefox.

That's all there is to it. Mine works! And I hope a lot of bugs are fixed, though Beta 2 worked pretty well on my system.

And this is the last time you have to do it manually. In the release notes for RC1 I read:

"Automated update to streamline product upgrades. Notification of an update is more prominent, and updates to Firefox may now be half a megabyte or smaller. Updating extensions has also improved."

---

### Post by Snakey on 2005-11-02
[quote=magnusbb]No, auto-update does not work. But why do that? It's very simple to upgrade manually.[/quote] Why? Because it's even more simpler to use auto-update ;)

---

### Post by magnusbb on 2005-11-02
When it works, yes, of course.

In other news; I am happy to tell that Firefox now (finally) remembers the scrolling position of a web page when switching between pages. At least, that has been a huge problem for me in the past.

---

### Post by fishfork on 2005-11-02
OK, for all the people having problems with auto-update, you might try running firefox as root:
```

$ sudo su
Password:
# firefox
# exit
$

```
When you run it as root, Check for Updates in the Help menu is enabled, and you can update from there. Running firefox once as root like this also seems to fix the annoying chrome corruption error. Let me know if it works for you.

---

### Post by manicka on 2005-11-03
This How-To is also available at the [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page")

---

### Post by MrRoboto on 2005-11-03
[QUOTE=fishfork]OK, for all the people having problems with auto-update, you might try running firefox as root:
```

$ sudo su
Password:
# firefox
# exit
$

```
When you run it as root, Check for Updates in the Help menu is enabled, and you can update from there. Running firefox once as root like this also seems to fix the annoying chrome corruption error. Let me know if it works for you.[/QUOTE]

isn't enough to give yourself permission to /opt/firefox?
i'm at work so i can't try right now.

---

### Post by hallkbrdz on 2005-11-03
And wow is it ever faster. :p  If I could get BB to not write to both the LCD and VGA port on my laptop, it would probably be twice again faster... :rolleyes: 

The only "bad" thing is I have to go and re-establish my password sites (like this forum). And there may be some way around that. But if rc1 is more stable that 1.07, that is fine (1.06 always seemed more stable than the quickly patched 1.07 to me).

Bryan

---

### Post by ubuntumaneh on 2005-11-03
I have installed in two computers this new firefox. Fast to install, fast to use. Nice how-to. 

One further comment, in one of the computer Im still using hoary. The how-to works as well. Cool.

---

### Post by veloct on 2005-11-03
Not to hijack or derail the thread but has anyone tried this with thunderbird?

---

### Post by jeremy on 2005-11-03
[QUOTE=MrRoboto]isn't enough to give yourself permission to /opt/firefox?
i'm at work so i can't try right now.[/QUOTE]
I have done this, and, yes, it works.

---

### Post by Animus on 2005-11-03
I can't get this to work at all, I type in the command sudo cp firefox-1.5b2.tar.gz /opt/ and all I get is "cp: cannot stat `firefox-1.5b2.tar.gz': No such file or directory
".  I thought this might be because I download the first release Candidate, however even by changing the command to "sudo cp firefox-1.5rc1.tar.gz" I get the same response.  I couldn't find the Beat 2 to download.  Anyone have any idea whats going on?

---

### Post by Animus on 2005-11-03
Hello?

---

### Post by hallkbrdz on 2005-11-03
Has anyone got adblock to actually block anything with this release? It must need a new revision (loads but no adblock tags around graphics).

Bryan

---

### Post by seiflotfy on 2005-11-03
[QUOTE=Animus]I can't get this to work at all, I type in the command sudo cp firefox-1.5b2.tar.gz /opt/ and all I get is "cp: cannot stat `firefox-1.5b2.tar.gz': No such file or directory
".  I thought this might be because I download the first release Candidate, however even by changing the command to "sudo cp firefox-1.5rc1.tar.gz" I get the same response.  I couldn't find the Beat 2 to download.  Anyone have any idea whats going on?[/QUOTE]
 i think ur not in the right folder

---

### Post by jeremy on 2005-11-04
[QUOTE=Animus]I can't get this to work at all, I type in the command sudo cp firefox-1.5b2.tar.gz /opt/ and all I get is "cp: cannot stat `firefox-1.5b2.tar.gz': No such file or directory
".  I thought this might be because I download the first release Candidate, however even by changing the command to "sudo cp firefox-1.5rc1.tar.gz" I get the same response.  I couldn't find the Beat 2 to download.  Anyone have any idea whats going on?[/QUOTE]
You should create the /opt directory first:
sudo mkdir /opt
then continue with:
sudo cp firefox-1.5rc1.tar.gz /opt/
etc.........

---

### Post by boles on 2005-11-04
I have everything working great, including extensions.
The only problem I have is with the plugins. I can't seem to get the vlc-plugin acroread-plugin and flashplayer working.

When I go to about: plugins I only see the OpenOffice.org and default plugin.

Hope anyone can help me on this.

---

### Post by Animus on 2005-11-04
When I try sudo mkdir /opt I get the following error:

mkdir: cannot create directory `/opt': File exists

Any ideas?

---

### Post by Animus on 2005-11-04
I got the previous command to work, however I get this when I try sudo tar xzvf firefox-1.5b2.tar.gz.

tar: firefox-1.5b2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Can anyone point me in the right direction?

---

### Post by fishfork on 2005-11-04
Animus, you need to replace firefox-1.5b2.tar.gz with whatever the file you downloaded is called. I also think you would find this easier if you learned a bit more about the linux command line. It can be a bit intimidating to linux novices, but the basics aren't that hard to pick up. There are plenty of sites you can find with google - one I came up with just now is [tuxfiles](http://www.tuxfiles.org/linuxhelp/cli.html). There's [some stuff on the wiki](https://wiki.ubuntu.com/BasicCommands) too.

Regards,

Ben

---

### Post by Animus on 2005-11-04
I got it installed on my own.  Now how do I create icons for it?  I removed the previous firefox, and the icons along with it, and now whenever I want to use firefox I have to open the terminal up.  Anyone know how I'd go about getting some icons made up for it?

---

### Post by Imrahil on 2005-11-04
What is going on here is that ubuntu's firefox changed its config to better match windows behavior (middle click closes tab) whereas unix default behavior is middle click loads clipboard contents. The new firefox no longer as the ubuntu specific tweaks.

To change this or any other behavior setting in firefox type this url:

about:config


then search for middlemouse.contentLoadURL
make sure value is set to false.

Neat huh?

[QUOTE=corbs83]MIddle clicking a tab used to close it, now it loads CNN.com

What the?!

EDIT: In fact, it just seems to load a random site. How can I return to the good old days of the middle-click close?

By the way though, thanks for install guide for Fx 1.5 beta2 ... It's so much faster than the default.[/QUOTE]

---

### Post by bionnaki on 2005-11-04
you rule

---

### Post by muzza on 2005-11-06
Well... I downloaded the .tar.gz file to my desktop, but I can't get past the first command line.

I get this reply; cp: cannot stat `firefox-1.5rc1.tar.gz': No such file or directory

I tried creating a new folder called 'Firefox' in /opt, but it wouldn't allow it.

What do I do now?

---

### Post by drummer on 2005-11-06
before running the first command (sudo cp firefox-1.5rc1.tar.gz /opt/), make sure you're in the same directory as the tarball you just downloaded. If it's on the desktop, do this in a terminal first```
cd ~/Desktop
```that'll change directory to the desktop and then you can run the first command in the wiki.

---

### Post by muzza on 2005-11-07
Thanks Drummer.  That worked.  I noticed that the HowTo actually said to change to the appropriate directory.  (damn newbies!!)

Well, I got it installed, but it's acting very weird.  
- My bookmarks toolbar is empty and I can't add to it
- the bookmarks are there in the Bookmarks drop list, but they don't work
- the only way to link to my bookmarks is to open 'Manage Bookmarks...' and double click on a link
- The current URL doesn't show in the address bar
- the spinning Ubuntu icon (top right corner) doesn't spin when pages are loading
- the forward, back, reload and stop buttons are constantly greyed out

I've read this whole thread and I seem to be alone with these weird goings-on.

Any more ideas???

---

### Post by fishfork on 2005-11-07
[QUOTE=muzza]Thanks Drummer.  That worked.  I noticed that the HowTo actually said to change to the appropriate directory.  (damn newbies!!)[/QUOTE]
That's probably because I just added it to the howto. :)
[QUOTE=muzza]
Well, I got it installed, but it's acting very weird.  
- My bookmarks toolbar is empty and I can't add to it
- the bookmarks are there in the Bookmarks drop list, but they don't work
- the only way to link to my bookmarks is to open 'Manage Bookmarks...' and double click on a link
- The current URL doesn't show in the address bar
- the spinning Ubuntu icon (top right corner) doesn't spin when pages are loading
- the forward, back, reload and stop buttons are constantly greyed out

I've read this whole thread and I seem to be alone with these weird goings-on.

Any more ideas???[/QUOTE]
All I can suggest is starting with a fresh profile. If you followed the howto, your old profile should have been renamed to .mozilla.ubuntu, so you can safely delete .mozilla in your home directory. Do this:
```
rm -r ~/.mozilla
```
and then try to start firefox again. Hope this helps,

Ben

---

### Post by 23meg on 2005-11-07
Has anyone been able to get Java (Sun JRE) working with this version? If so I'd appreciate a few pointers; for me it works in Ubuntu's 1.07 build but not on 1.5rc1, even after symlinking the plugin.

---

### Post by manicka on 2005-11-07
Java is working for me
I have both 1.4 blackdown and 1.5 installed. I have no idea which one it is using. My guess would be 1.5

---

### Post by benplaut on 2005-11-08
[QUOTE=manicka]Java is working for me
I have both 1.4 blackdown and 1.5 installed. I have no idea which one it is using. My guess would be 1.5[/QUOTE]

check about:plugins... blackdown is perfect for me, sun1.5 is b0rked

---

### Post by domino on 2005-11-08
Those getting that chrome error using the default plugin/extention directory, can you try disabling the extension TalkBack 1.5 and/or DOM Inspector 1.8? I disabled those and I have not gotten the chrome error since.

Thanks

---

### Post by eyebrowman92 on 2005-11-08
i cant figure out how to install firefox 1.5. i downloaded the tar to my desktop, but now what?

---

### Post by Mizzou_Engineer on 2005-11-08
I can't get the Flash plugin to work at all, even after manually installing it.

---

### Post by drummer on 2005-11-08
[QUOTE=eyebrowman92]i cant figure out how to install firefox 1.5. i downloaded the tar to my desktop, but now what?[/QUOTE]
Just follow the instructions in the wiki, you need to execute the comands there in a terminal.

---

### Post by 23meg on 2005-11-08
[QUOTE=manicka]Java is working for me
I have both 1.4 blackdown and 1.5 installed. I have no idea which one it is using. My guess would be 1.5[/QUOTE]

For me it's fine in 1.0.7 but not in 1.5. What did you do to get it working?

---

### Post by manicka on 2005-11-08
[QUOTE=23meg]For me it's fine in 1.0.7 but not in 1.5. What did you do to get it working?[/QUOTE]
All I did was installl jre1.5 from the plf repos. I have the blackdown and plf versions installed. Installed Firefox as per the wiki how-to and it worked. 

I've pointed some apps like openoffice at jre1.5 but I have no idea which  one Firefox is using.

---

### Post by Ubuntu Maniac on 2005-11-08
this is eyebrowman92, i made a new account.  ive followed the instruction but i keep getting"the file or folder does not exist" what do  ido?

---

### Post by Sykil on 2005-11-08
Is there anyway to do this easily on an AMD64 machine? I'm not a fan of compiling from source. :x

---

### Post by 23meg on 2005-11-08
[QUOTE=manicka]All I did was installl jre1.5 from the plf repos.  [/QUOTE]

The plf version did it for me, thanks for the pointer!

---

### Post by eyebrowman92 on 2005-11-08
can someone help me?

---

### Post by ptepper on 2005-11-09
I added a similar page to the wiki for Thunderbird: 

[http://wiki.ubuntu.com/ThunderbirdNewVersion]("http://wiki.ubuntu.com/ThunderbirdNewVersion")

There are many bugfixes and nice new features in the new versions of t-bird. For example, there's a problem with 1.0.7 copying mail to IMAP Sent folders, which seems to have been resolved in 1.5. Version 1.5 can also also be set to beep with new mail, which I don't think is available in 1.0.7.

---

### Post by manicka on 2005-11-09
[QUOTE=eyebrowman92]can someone help me?[/QUOTE]

[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by manicka on 2005-11-09
[QUOTE=ptepper]I added a similar page to the wiki for Thunderbird: 

[http://wiki.ubuntu.com/ThunderbirdNewVersion]("http://wiki.ubuntu.com/ThunderbirdNewVersion")
.[/QUOTE]

I've added this how-to to the Ubuntu Document Storage Facility :)

[http://doc.gwos.org/index.php/ThunderbirdNewVersion](http://doc.gwos.org/index.php/ThunderbirdNewVersion)

---

### Post by ptepper on 2005-11-10
[QUOTE=manicka]I've added this how-to to the Ubuntu Document Storage Facility :)

[http://doc.gwos.org/index.php/ThunderbirdNewVersion](http://doc.gwos.org/index.php/ThunderbirdNewVersion)[/QUOTE]

Cool, thanks :smile:

---

### Post by kevcart3 on 2005-11-10
Hey, thanks for the cool guide, one question though:

I had applied the tweak to get a nicer "form style" in Firefox by replacing the "res" directory in /usr/lib/mozilla-firefox. 

I found the "res" directory in /opt/firefox/res and replaced the files, but it doesn't seem to change the form style, any ideas? 

I have replaced the stuff in /usr/lib/mozilla-firefox AND /opt/firefox/res.

:confused:

---

### Post by Cuppa-Chino on 2005-11-10
sorry to have to pester you guys, but I just cannot find the files I need to change to get it to register as firefox 1.5

sites always notice me as 1.0.7 and therefore some plugins and so on do not work - which file do I need to edit - I have tried about:config I have tried looking through all the *.js files:confused:

---

### Post by drummer on 2005-11-10
EDIT - oops, i misread your question Cuppa-Chino

EDIT 2 - my install registers as version 1.5, not sure why yours wouldn't.. either way, this workaround might help: [http://vale.homelinux.net/wordpress/?p=18](http://vale.homelinux.net/wordpress/?p=18) just needed to google a bit.

---

### Post by oobuntoo on 2005-11-10
[QUOTE=GoA]Is adblock working for everyone? If yes then I have a problem. It doesn't show any links to block ads.[/QUOTE]


I suggest that you use Adblock Plus instead. Go to this link [http://bene.sitesled.com/install.htm](http://bene.sitesled.com/install.htm)

and install Adblock Filterset.G Updater while you'are at it.
[https://addons.mozilla.org/extensions/moreinfo.php?id=1136](https://addons.mozilla.org/extensions/moreinfo.php?id=1136)

---

### Post by Cuppa-Chino on 2005-11-10
thanks drummer, thought I had googled enough

did work in the end by me manually running around and just deleting all the *.js and all associated stuff and then did a clean install 

that worked.

I had ended up with lots of profiles from trying and trying and took care deleting them all, might be good to repeat the delete command instructions at the end of the wiki.... :oops:

---

### Post by oobuntoo on 2005-11-10
[QUOTE=corbs83]MIddle clicking a tab used to close it, now it loads CNN.com

What the?!

EDIT: In fact, it just seems to load a random site. How can I return to the good old days of the middle-click close?

Type "about:config" into address (URL) field. Search for "middlemouse.contentLoadURL" and change it's value to "false"

---

### Post by Cuppa-Chino on 2005-11-10
[SIZE="3"]RC2 is out [# Mozilla Firefox für Linux ]("http://www.computerbase.de/downloads/software/browser/mozilla_firefox/?url=3947")[/SIZE](8,1 MB) - link is from computerbase.de

wish me luck getting it to work after my problems with RC1

_Also and more importantly:_
hope this fixes the memory issue I have - Firefox uses up to 150MB of RAM, seems excessive does it not? Has anybody else got this and fixed it?

---

### Post by drummer on 2005-11-10
hmm.. it's not official on the firefox site, RC1 is still the one you can download there, but RC2 is in the release notes.
[http://www.mozilla.org/products/firefox/releases/1.5.html](http://www.mozilla.org/products/firefox/releases/1.5.html)[quote=mozilla.org]Here's what's new in Firefox 1.5 RC 2:

    * Several fixes to automated update system.
[/quote]

Does the auto update feature update from RC1 to RC2? I did an update just now, but don't know if my FF is now RC2.

---

### Post by kevcart3 on 2005-11-10
I updated to RC2 manually, because my check for updates button didn't work, and it still doesn't work :( It's greyed out for some reason

---

### Post by drummer on 2005-11-11
[QUOTE=kevcart3]It's greyed out for some reason[/QUOTE]
Might be because the firefox directory in /opt belongs to root and firefox is running as a user. The updater needs write access to the /opt/firefox directory, so I chowned /opt/firefox to me (sudo chown -R owen:owen /opt/firefox) and it works fine.

---

### Post by veloct on 2005-11-11
[QUOTE=drummer]Might be because the firefox directory in /opt belongs to root and firefox is running as a user. The updater needs write access to the /opt/firefox directory, so I chowned /opt/firefox to me (sudo chown -R owen:owen /opt/firefox) and it works fine.[/QUOTE]

You stole the words right out of my fingers

---

### Post by ngms27 on 2005-11-11
RC2 hangs my machine after a few pages. You can move the mouse, the keyboard doesn't work so you cannot get to a terminal, close X anything. A complete lockup. This was installed as per this thread.

Nothing has ever hung my two installs of Ubuntu previously. The only fix is a power recycle.

JonnyT

---

### Post by sailor420 on 2005-11-11
I had a lock with it too. Not that bad, just kicked me out to the Feedback tool, but it was the first lockup I'd seen with Firefox since 0.5 days.

---

### Post by Cuppa-Chino on 2005-11-11
actually installed the ubuntu 1.0.7 back on and then went to RC2 - I have not had any problems at all, on the other hand I have been brutal again and deleted all profiles etc

---

### Post by jdong on 2005-11-11
I lost a bunch of settings and all my bookmarks doing a Check For Updates over to 1.5RC2 -- I think the updater may have still been broken in RC1 -- it worked fine on Windows though!

---

### Post by Footer on 2005-11-12
Anyone know how to get the SessionSaver extension working with FF 1.5 RC1?  I think I've found a version that works:

[http://adblock.ethereal.net/alchemy.cgi/SessionSaver](http://adblock.ethereal.net/alchemy.cgi/SessionSaver)

But the 'install' button doesn't work on my system and I don't know how to install the .jar file after downloading!  :confused:

Any help, greatly appreciated!!!

---

### Post by Juippisi on 2005-11-12
[QUOTE=Footer]Anyone know how to get the SessionSaver extension working with FF 1.5 RC1?  I think I've found a version that works:

[http://adblock.ethereal.net/alchemy.cgi/SessionSaver](http://adblock.ethereal.net/alchemy.cgi/SessionSaver)

But the 'install' button doesn't work on my system and I don't know how to install the .jar file after downloading!  :confused:

Any help, greatly appreciated!!![/QUOTE]

Try adding the [http://adblock.ethereal.net](http://adblock.ethereal.net) page to the "Allow this site to install software" -list.

---

### Post by Juippisi on 2005-11-12
Does anyone know how to adblock images without using the adblock extension? I've been hearing stories that it would be possible. If I remember correctly, bored2k was telling something about it.

---

### Post by linasgricius on 2005-11-12
[QUOTE=Footer]Anyone know how to get the SessionSaver extension working with FF 1.5 RC1?  I think I've found a version that works:

[http://adblock.ethereal.net/alchemy.cgi/SessionSaver](http://adblock.ethereal.net/alchemy.cgi/SessionSaver)

But the 'install' button doesn't work on my system and I don't know how to install the .jar file after downloading!  :confused:

Any help, greatly appreciated!!![/QUOTE]

do File->open...

---

### Post by bored2k on 2005-11-12
[QUOTE=Juippisi]Does anyone know how to adblock images without using the adblock extension? I've been hearing stories that it would be possible. If I remember correctly, bored2k was telling something about it.[/QUOTE]
> bored2k Juippis, [http://rapidshare.de/files/7542085/hostperm.1.html](http://rapidshare.de/files/7542085/hostperm.1.html) || [http://rapidshare.de/files/7542103/userContent.css.html](http://rapidshare.de/files/7542103/userContent.css.html)
bored2k Juippis, go to CNN and note the banner on top (if it works you'll see it no more
bored2k Juippis, put hostperm.1 in $HOME/.mozilla/username/
bored2k Juippis, and userContent.CSS in $HOME/.mozilla/username/chrome/
bored2k Juippis, and restart
:)

---

### Post by Juippisi on 2005-11-12
Thanks again!
Works just fine :-).

---

### Post by Footer on 2005-11-12
[QUOTE=Juippisi]Try adding the [http://adblock.ethereal.net](http://adblock.ethereal.net) page to the "Allow this site to install software" -list.[/QUOTE]

Hmmm ... I tried that but it didn't work...?

I also tried File --> Open as suggested by another post.  That allows you to extract the file but not sure what to do with it after that?  Maybe put it under ~.mozilla/firefox/my_profile.default/extensions/? or some such...?  I haven't tried that but I'm not quite sure how to go about that or where to put it so it shows up as a valid, installed extension?  Any other suggestions???

Thanks!

:)

---

### Post by Footer on 2005-11-13
[QUOTE=linasgricius]do File->open...[/QUOTE]

WHOOHOO!!!  I finally figured it out.  Instead of trying to open the .jar file, I did File --> Open File (from within Firefox 1.5) on the .xpi file which installed the SessionSaver extension no hass!

After a couple of failed starts due to chrome registration errors, it finally came up and SessionSaver worked!  Can't wait for 1.5 to come out final!

Thanks for the tips!!!

:KS

---

### Post by bionnaki on 2005-11-13
you can also drag/drop into your extensions manager.

---

### Post by fishfork on 2005-11-13
[QUOTE=Juippisi]Does anyone know how to adblock images without using the adblock extension? I've been hearing stories that it would be possible. If I remember correctly, bored2k was telling something about it.[/QUOTE]
I use Privoxy (it's in the repositories) with an extremely cut-down default.action file. Then I put a little link on my bookmarks toolbar to [http://config.privoxy.org/edit-actions-list?f=default](http://config.privoxy.org/edit-actions-list?f=default) which you can click to quickly add domains to the blocklist. It's almost as convenient as adblock, but much speedier (I find adblock really slows down page loads on my machine when the blocklist gets long).

---

### Post by akurashy on 2005-11-16
well i gotta say it screwed 2 times on me =/, i lost my profiles and bookmarks because i had to reinstall the old version, since i lost all i gave it another try for firefox 1.5 gotta say it was worth it, very fast and all! :D

now i'm wondering, do i need to do the same thing when RC3 is out?

---

### Post by drummer on 2005-11-16
Should be able to just use the auto upgrade feature in the help menu.

---

### Post by akurashy on 2005-11-16
this is bugging me a while, firefox 1.5 takes a while to Look up for domains =/ is anyone getting this too?

---

### Post by 23meg on 2005-11-16
[QUOTE=akurashy]this is bugging me a while, firefox 1.5 takes a while to Look up for domains =/ is anyone getting this too?[/QUOTE]
Type about:config in the address bar and set the network.dns.disableIPV6 key to true.

---

### Post by MrRoboto on 2005-11-16
[QUOTE=akurashy]this is bugging me a while, firefox 1.5 takes a while to Look up for domains =/ is anyone getting this too?[/QUOTE]

in the URL write: about:config

search for ipv6 and doubleclik on network.dns.disableIPv6

restart firefox

---

### Post by Footer on 2005-11-16
Has anyone noticed that FF 1.5 RC1 eats up your processor after several hours...like <24 for me.  If I leave it running, the processor gets maxxed out in <24 hours.  Maybe this has been taken care of in RC2 (or RC3?).  I remember reading that others were having this problem with 1.0.X as well ... Maybe it's related to the kernel I'm running which is currently 2.6.12-9-k7 (AMD Athlon XP 3000+ processor)?

Any thoughts/observations, greatly appreciated!

:)

---

### Post by MrRoboto on 2005-11-16
[QUOTE=Footer]Has anyone noticed that FF 1.5 RC1 eats up your processor after several hours...like <24 for me.  If I leave it running, the processor gets maxxed out in <24 hours.  Maybe this has been taken care of in RC2 (or RC3?).  I remember reading that others were having this problem with 1.0.X as well ... Maybe it's related to the kernel I'm running which is currently 2.6.12-9-k7 (AMD Athlon XP 3000+ processor)?

Any thoughts/observations, greatly appreciated!

:)[/QUOTE]

never happend to me. anyway RC2 is already out, upgrade! :)

---

### Post by akurashy on 2005-11-16
[quote=MrRoboto]in the URL write: about:config

search for ipv6 and doubleclik on network.dns.disableIPv6

restart firefox[/quote]

thanks! that worked smooth :D

---

### Post by Footer on 2005-11-16
[QUOTE=MrRoboto]never happend to me. anyway RC2 is already out, upgrade! :)[/QUOTE]

OK, just upgraded to RC2.  I'll give it 24 hours and post back here.

:)

---

### Post by jdong on 2005-11-16
Just to say, a Ubuntu developer informed us today that Firefox 1.5 RC2 is nearly ready for upload into Dapper.

---

### Post by fishfork on 2005-11-16
[QUOTE=jdong]Just to say, a Ubuntu developer informed us today that Firefox 1.5 RC2 is nearly ready for upload into Dapper.[/QUOTE]
Ah, I'd been wondering about this. Do you think there's a chance 1.5 could be added to Breezy Universe, or will it be a Backports job? Either would be very handy, considering the current speed problems with the version in the repositories.

---

### Post by jdong on 2005-11-16
It'll be a Backports job

---

### Post by joakim2 on 2005-11-17
[QUOTE=ptepper]I added a similar page to the wiki for Thunderbird: 

[http://wiki.ubuntu.com/ThunderbirdNewVersion]("http://wiki.ubuntu.com/ThunderbirdNewVersion")

There are many bugfixes and nice new features in the new versions of t-bird. For example, there's a problem with 1.0.7 copying mail to IMAP Sent folders, which seems to have been resolved in 1.5. Version 1.5 can also also be set to beep with new mail, which I don't think is available in 1.0.7.[/QUOTE]

Starting calendar alarm service
./run-mozilla.sh: line 131: 24046 Segmentation fault      "$prog" ${1+"$@"}

Anyone else getting this?

---

### Post by Footer on 2005-11-17
[QUOTE=jdong]It'll be a Backports job[/QUOTE]

Could someone provide a brief explanation about backports and what a good sources.list should look like to include it (if, in fact, that's what needs to be done to accommodate).

Sorry for being a little off topic but ...

:)

---

### Post by jadugarr on 2005-11-17
I think 1.5 final is out. firefox just updated and restarted and now it says 1.5 in the about w/o the RC.

---

### Post by cbudden on 2005-11-17
Nope, its RC3 [http://www.mozilla.org/products/firefox/rc3.html](http://www.mozilla.org/products/firefox/rc3.html)

---

### Post by akurashy on 2005-11-17
ok i restarted X, and i got this weird chrome errors, how can i fix them? i think it will appear everytime i restart X =/

---

### Post by nix4me on 2005-11-17
Just installed 1.5 RC3.  What a memory hog Firefox has become.  Its consuming 249 meg right now.

Why is it getting worse and worse?

nix4me

---

### Post by jdong on 2005-11-17
Part may be attributed to the bfcache that makes Firefox instantaneous when navigating back and forward.

---

### Post by akurashy on 2005-11-18
[quote=jdong]Part may be attributed to the bfcache that makes Firefox instantaneous when navigating back and forward.[/quote]

when Firefox 1.5 rc3 going to the backports? o.o:razz:

---

### Post by Footer on 2005-11-18
[QUOTE=Footer]OK, just upgraded to RC2.  I'll give it 24 hours and post back here.

:)[/QUOTE]

It's been more like 36 hours now but I'm happy to report that the processor usage is back to normal.  Been running FF 1.5 RC2 for the entire time and usage is nice and low like it should be.

But I see RC3 is now out!  <sigh>

:)

---

### Post by jeremy on 2005-11-18
I am using 1.5rc2 and when I do 'Help -> Check for updates' it checks, but says 'there are no updates available...' but rc3 is out now. Is anyone else getting this?

---

### Post by manicka on 2005-11-18
[QUOTE=jeremy]I am using 1.5rc2 and when I do 'Help -> Check for updates' it checks, but says 'there are no updates available...' but rc3 is out now. Is anyone else getting this?[/QUOTE]
Firefox doesn't update itself that way, only the plugins/themes etc. You'll need to download the tarball and replace the directory in /opt as per the how-to

---

### Post by domino on 2005-11-18
FF 1.5rc2 3 tabs/sites open and all plugins disabled used 120mb of memory, compared to Opera 3 tabs/sites 50mb. Both left running over 2hrs time. FF was fun while it lasted. Can someone tell me if the virtual memory usage matters? I can't seam to find the app's physical memory usage.

---

### Post by PenguinZdravko on 2005-11-18
How can I know have I correctly installed Mozilla Firefox 1.5 RC3? In the about dialog it still shows build date 20051111, but I have removed the folder of 1.5 RC2.

---

### Post by jeremy on 2005-11-18
[QUOTE=manicka]Firefox doesn't update itself that way, only the plugins/themes etc. You'll need to download the tarball and replace the directory in /opt as per the how-to[/QUOTE]
Thanks for answering, but I think you are probably wrong about that, see the snapshot of my firefox preferences.

---

### Post by zwz on 2005-11-18
I tried to install both 1.5rc2 and 1.5rc3 in breezy by strictly following the instructions, but got segfaults. Any ideas?

> /opt/firefox/run-mozilla.sh: line 131:  7726 Segmentation fault      "$prog" ${1+"$@"}

---

### Post by akurashy on 2005-11-19
Ok so, I think this is a question I been wondering, can we use themes, because I downloadeda theme and it didn't want to work everytime i restarted firefox..

---

### Post by jeremy on 2005-11-19
[QUOTE=jeremy]Thanks for answering, but I think you are probably wrong about that, see the snapshot of my firefox preferences.[/QUOTE]
I just found this at mozilla forums:
[http://forums.mozillazine.org/viewtopic.php?t=343101](http://forums.mozillazine.org/viewtopic.php?t=343101)

---

### Post by Footer on 2005-11-19
[QUOTE=Footer]Has anyone noticed that FF 1.5 RC1 eats up your processor after several hours...like <24 for me.  If I leave it running, the processor gets maxxed out in <24 hours.  Maybe this has been taken care of in RC2 (or RC3?).  I remember reading that others were having this problem with 1.0.X as well ... Maybe it's related to the kernel I'm running which is currently 2.6.12-9-k7 (AMD Athlon XP 3000+ processor)?

Any thoughts/observations, greatly appreciated!

:)[/QUOTE]

It's BAAAAACK!!!  I'm now running FF 1.5 RC3 and in less than 24 hours, my processor CPU load was maxxed at 100%.  Closed/reopened FF and all is well, back to about 4-5%.  Still running 2.6.12-9-k7 kernel ... Anyone else experiencing this?  I sure hope they get this fixed before the final release.

Thanks.

---

### Post by nix4me on 2005-11-19
[QUOTE=Footer]It's BAAAAACK!!!  I'm now running FF 1.5 RC3 and in less than 24 hours, my processor CPU load was maxxed at 100%.  Closed/reopened FF and all is well, back to about 4-5%.  Still running 2.6.12-9-k7 kernel ... Anyone else experiencing this?  I sure hope they get this fixed before the final release.

Thanks.[/QUOTE]

Are you running any extensions?
I had similar problems and I think it was because of the user agent switcher i had loaded.  Mine is running at 120 mb right now.  Seems to be normal.

Mark

---

### Post by zwz on 2005-11-19
[QUOTE=zwz]I tried to install both 1.5rc2 and 1.5rc3 in breezy by strictly following the instructions, but got segfaults. Any ideas?[/QUOTE]

I traced it down to SCIM. If scim is removed, firefox 1.5rc starts up normally. But since I cannot live without SCIM, I'll have to downgrade to 1.0.7. :(

---

### Post by Cuppa-Chino on 2005-11-19
[QUOTE=zwz]I traced it down to SCIM. If scim is removed, firefox 1.5rc starts up normally. But since I cannot live without SCIM, I'll have to downgrade to 1.0.7. :([/QUOTE]

what is SCIM ? I had posted on the enormous memory consumption earlier, any fixes?

---

### Post by tHub on 2005-11-19
i had firefox 1.5 RC1 working fine, but one day i was browsing and a box popped up saying an important update had been downloaded and firefox needed to be restarted , since then i run firefox for a while and then it just closes out of nowhere.
Older version works fine.
heres the error:
```
th@ubuntu:~$ firefox
INTERNAL ERROR on Browser End: Could not get the plugin manager
System error?:: Success

```
I just did a "fresh install" of 1.5 RC3 and im get this error message when i first start it:
[[IMG]http://img44.imageshack.us/img44/5548/200511191803331024x768scrot2hw.th.png[/IMG]](http://img44.imageshack.us/my.php?image=200511191803331024x768scrot2hw.png)
It runs but i get that error i first mentioned

---

### Post by curtis on 2005-11-19
[QUOTE=tHub]i had firefox 1.5 RC1 working fine, but one day i was browsing and a box popped up saying an important update had been downloaded and firefox needed to be restarted , since then i run firefox for a while and then it just closes out of nowhere.
Older version works fine.
heres the error:
```
th@ubuntu:~$ firefox
INTERNAL ERROR on Browser End: Could not get the plugin manager
System error?:: Success

```
I just did a "fresh install" of 1.5 RC3 and im get this error message when i first start it:
[[IMG]http://img44.imageshack.us/img44/5548/200511191803331024x768scrot2hw.th.png[/IMG]](http://img44.imageshack.us/my.php?image=200511191803331024x768scrot2hw.png)
It runs but i get that error i first mentioned[/QUOTE]

Just a matter of interest, what theme are you using there?
It looks quite good.
But it is not GNOME I guess.

---

### Post by zwz on 2005-11-19
[QUOTE=Cuppa-Chino]what is SCIM ? I had posted on the enormous memory consumption earlier, any fixes?[/QUOTE]

It's an input method platform. [http://packages.ubuntu.com/breezy/utils/scim](http://packages.ubuntu.com/breezy/utils/scim). I am not sure if this problem has been fixed in scim-1.4.2, which has found its way into Dapper.

---

### Post by tHub on 2005-11-19
[QUOTE=curtis]Just a matter of interest, what theme are you using there?
It looks quite good.
But it is not GNOME I guess.[/QUOTE]
thats Xfce + Clearlooks-Graphite

---

### Post by Brando569 on 2005-11-19
all i have to say is wow..... i got used to the sluggish ubuntu firefox and grew to accept it, i installed RC3 and its amazingly fast. although this site did take 14 secs to load :rolls eyes:

---

### Post by Single on 2005-11-20
[QUOTE=zwz]I traced it down to SCIM. If scim is removed, firefox 1.5rc starts up normally. But since I cannot live without SCIM, I'll have to downgrade to 1.0.7. :([/QUOTE]

Someone found a way.
[http://www.ubuntuforums.org/showthread.php?t=92303]("http://www.ubuntuforums.org/showthread.php?t=92303")

---

### Post by Krobar on 2005-11-20
Has anyone had problems using the right click > set as wallpaper function in RC3? I never tried the first two, just got RC3 working today, and the option seems to be missing and I'm not sure why.

Adblock Plus
Faster Fox
Tab Mix Plus

and that's about it I think for extensions.

---

### Post by PenguinZdravko on 2005-11-20
[QUOTE=Footer]It's BAAAAACK!!!  I'm now running FF 1.5 RC3 and in less than 24 hours, my processor CPU load was maxxed at 100%.  Closed/reopened FF and all is well, back to about 4-5%.  Still running 2.6.12-9-k7 kernel ... Anyone else experiencing this?  I sure hope they get this fixed before the final release.

Thanks.[/QUOTE]
Please, tell me whats your build date.

---

### Post by Footer on 2005-11-20
[QUOTE=nix4me]Are you running any extensions?
I had similar problems and I think it was because of the user agent switcher i had loaded.  Mine is running at 120 mb right now.  Seems to be normal.

Mark[/QUOTE]

Yes, I'm running a few:
[INDENT]
Tabbrowser Preferences
SessionSaver .2
Adblock Plus
[/INDENT]

However, I've been running FF 1.5 RC3 for well over 24 hours now without incident ... Processor is running at 4-5% as normal.  GO FIGURE!

How do you measure how much memory it's using?  Is that via command line somehow?

Thanks!

---

### Post by Footer on 2005-11-20
[QUOTE=PenguinZdravko]Please, tell me whats your build date.[/QUOTE]

See attached thumbnail.

---

### Post by curtis on 2005-11-20
I have it working fine with Faster fox, Foxy tunes, Ad-block, Tabbed prefs, Session saver.
On RC3.

---

### Post by doclivingston on 2005-11-20
[QUOTE=Footer]
How do you measure how much memory it's using?  Is that via command line somehow?[/QUOTE]

Measuring how much memory an application is using is a difficult question. A okay approximation can be gotten from opening the system monitor, and:
1) ignoring the "Memory" column. That is the size of the process's address space.
2) Taking the "RSS" value, subtracting the "Shared" value.

The value that gives you will be a bit low, because it doesn't include anything swapped to disk, or any of the shared libraries that are only used by that application. But it's about as good as you are going to get easily.

---

### Post by Footer on 2005-11-20
[QUOTE=doclivingston]Measuring how much memory an application is using is a difficult question. A okay approximation can be gotten from opening the system monitor, and:
1) ignoring the "Memory" column. That is the size of the process's address space.
2) Taking the "RSS" value, subtracting the "Shared" value.

The value that gives you will be a bit low, because it doesn't include anything swapped to disk, or any of the shared libraries that are only used by that application. But it's about as good as you are going to get easily.[/QUOTE]

Thanks for the explanation Doc!  You gotta love Linux eh?  I didn't realize all these details were available (only opened up System Monitor a couple of times in the past).

With two FF windows and each having about a dozen tabs, I'm only using 100MB or so of memory based on your formula.  I'm happy with that since it's only 10% of my total physical memory.

:)

---

### Post by treris on 2005-11-20
I have (finally) updated to FF1.5 today and I must say, i'm glad of it, it's faster and moreover it renders some fonts nicer I think

all in all I don't think I'll be going back to 1.0.7

---

### Post by foxy123 on 2005-11-20
Thanks a lot for the How-to. FF 1.5 loads much faster and feels snapier.

I wonder if anyone has tried TB 1.5 already and what version? RC1 is available from the official website, though on [http://ftp.mozilla.org/pub/mozilla.org/thunderbird/nightly/](http://ftp.mozilla.org/pub/mozilla.org/thunderbird/nightly/) one can find RC3. I wonder which to try.

---

### Post by foxy123 on 2005-11-20
it also calls an old version of firefox from thunderbird. Does anyone know how to fix it?

---

### Post by ssam on 2005-11-21
if you want to do this on powerpc then you can download it from here.

[http://www.tygier.co.uk/linux/firefox.html](http://www.tygier.co.uk/linux/firefox.html)

---

### Post by veloct on 2005-11-21
I have FF 1.5RC3 and TB 1.5RC1 installed and both work as defaults in my system.

---

### Post by jrib on 2005-11-21
[QUOTE=foxy123]it also calls an old version of firefox from thunderbird. Does anyone know how to fix it?[/QUOTE]

make sure that "system > preferences > preferred apps" is set to run the "firefox" command and not "mozilla-firefox" for your default browser

---

### Post by foxy123 on 2005-11-22
thanks _jason, it fixed it.

I am trying to make traybiff extension work with 1.5. I had to compile it from source and point to mozilla-thunderbird-config, which points to 1.5 in opt. The current mozilla-thunderbird-config, which is in /usr/bin points to the old version and there is no mozilla-thunderbird-config in /opt/thunderbird. Any idea how to solve it?

---

### Post by syklitengutt on 2005-11-23
The tut works fine until the last few steps:
cd
 mv .mozilla .mozilla-1.5
 mv .mozilla.ubuntu .mozilla

I get:
mv: cannot overwrite directory `.mozilla-1.5/.mozilla'

I have closed FF when doing this.
And when I type firefox later, the old version starts...

---

### Post by byoon on 2005-11-23
ASTOUNDING!!!

It is amazing what one application can do to your experience of an entire system.  The default firefox makes breezy feel old and decrepit (and I have an Athlon XP 2000 1 GB RAM).  The new firefox makes breezy feel fast and alive.

I've been a full time Ubuntu user since Warty so I know how each version feels.  Because web browsing (for most people) is so central to computer use today the fact that breezy's default firefox is sooooo laggy makes the entire system feel slow (even though breezy is tighter than any other release so far).

My wife and her sister have commented that ubuntu felt slower than Windows 2000 when I had it installed years back, and they said this without even being prompted.  This hurt me to the core, but I think it is because of issues noted above.  I seriously hope we can experience some major breakthroughs regarding performance in gnome and applications like firefox (Ubuntu version) which are so central to the computing experience.

For now, firefox 1.5 is working great.  Thank you for the tutorial.

---

### Post by jrib on 2005-11-23
[QUOTE=syklitengutt]The tut works fine until the last few steps:
cd
 mv .mozilla .mozilla-1.5
 mv .mozilla.ubuntu .mozilla

I get:
mv: cannot overwrite directory `.mozilla-1.5/.mozilla'

I have closed FF when doing this.
And when I type firefox later, the old version starts...[/QUOTE]

that part is to remove the new version, is that what you are trying to do?

---

### Post by syklitengutt on 2005-11-23
I follow the tut the whole wayy but when I get to the end I get some errors.
And If I just compleete the tut and then start ff its version 1.0.7 that starts.

---

### Post by foxy123 on 2005-11-23
[QUOTE=syklitengutt]I follow the tut the whole wayy but when I get to the end I get some errors.
And If I just compleete the tut and then start ff its version 1.0.7 that starts.[/QUOTE]
what are you trying to do? I mean, the tutorial ends with 
```

To ensure it is used as the default version, modify the symbolic link in /usr/bin:

 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/firefox
 
Try it out: :-)

 firefox
 
```

But you go further to remove 1.5 and replace it with 1.07 again. What is the point?

---

### Post by jrib on 2005-11-23
[QUOTE=syklitengutt]I follow the tut the whole wayy but when I get to the end I get some errors.
And If I just compleete the tut and then start ff its version 1.0.7 that starts.[/QUOTE]

The bottom of the tutorial (The part that says "Removing") is for *removing* firefox1.5 if you are unhappy with it.  If you just want to install it you would not do any of the commands in the "Removing" section.

assuming all you have done is what you pasted in that text file, do this part again:

```

chris@chris:~$ sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
chris@chris:~$ sudo ln -s /opt/firefox/firefox /usr/bin/firefox

```

and then just run firefox:

```

chris@chris:~$ firefox

```

---

### Post by foxy123 on 2005-11-23
Does anyone know how to use dev package from TB 1.07 with 1.5 or get a dev package for 1.5? I need to compile an extension and I need a thunderbird development packae for that. The one I have installed is pointing to an old version of TB. 

I tried to edit mozilla-thunderbird-config, but stuck. I changed the prefix to /opt but I guess I need to change other paths as well, but I am not sure to what.

For example, the original mozilla-thunderbird-config has:
```
--cflags)
      if test "/usr/include/mozilla-thunderbird" != /usr/include ; then
        includes="-I/usr/include/mozilla-thunderbird"
```

but there is no /include dir in /opt/thunderbird...

Can anyone help?

---

### Post by Spider-One on 2005-11-25
After a clean install of Ubuntu I followed this how to for the second time (first time worked great) but now it's as slow as ever. When generating a page it seems to free to a split second where I cannot click anything in Firefox, then suddenly it starts up like nothing happened, during the slow down I see extremely high CPU usage. And when a page is newly generated I try to scroll down but it takes a second to kick in and start scrolling, then it's fine at 1-2% CPU at best, until I open a link to a new page or new tab.

Any ideas as to what could be causing this problem that wasn't here on my first install? I see no noticable slow down in any app other than Firefox, so I'm baffled by this. Is there some tweak I'm missing that is supposed to be done by default? I've tried using a CPU specific kernel (K7, was using 386 for a while, and was using 386/K7 when it worked fine before) and it doesn't help.

---

### Post by Owdy on 2005-11-25
edit: fixed

---

### Post by benplaut on 2005-11-25
i'm receiving tons of "script on this page ahs stopped responding"... can someone try an ebay search and confirm?

---

### Post by Insane on 2005-11-26
Well, it is a great tutorial. Thanks!

---

### Post by Footer on 2005-11-26
Ever since installing FF 1.5 (currently running RC3), the links to web sites from within Thunderbird e-mail messages no longer open directly (worked fine under FF 1.0.7 and earlier versions).  I have to 'Copy Link Location', then paste into FF to get to the website.

Anyone know the quick fix for this?

Thanks!

---

### Post by foxy123 on 2005-11-26
[QUOTE=Footer]Ever since installing FF 1.5 (currently running RC3), the links to web sites from within Thunderbird e-mail messages no longer open directly (worked fine under FF 1.0.7 and earlier versions).  I have to 'Copy Link Location', then paste into FF to get to the website.

Anyone know the quick fix for this?

Thanks![/QUOTE]
try this:
[QUOTE=_jason]make sure that "system > preferences > preferred apps" is set to run the "firefox" command and not "mozilla-firefox" for your default browser[/QUOTE]

---

### Post by Footer on 2005-11-26
[QUOTE=foxy123]
try this:
Quote:
Originally Posted by _jason
make sure that "system > preferences > preferred apps" is set to run the "firefox" command and not "mozilla-firefox" for your default browser[/QUOTE]

Ahh yes, that did the trick!  Sort of threw me for a loop though as I use KDE and couldn't figure out where this setting was.  Logged in to GNOME and fixed it and it works perfectly back in KDE.

Thanks!

:KS

---

### Post by foxy123 on 2005-11-26
[QUOTE=Footer]Ahh yes, that did the trick!  Sort of threw me for a loop though as I use KDE and couldn't figure out where this setting was.  Logged in to GNOME and fixed it and it works perfectly back in KDE.

Thanks!

:KS[/QUOTE]
I guess it should be in KDE Control Centre...

---

### Post by Footer on 2005-11-26
[QUOTE=foxy123]I guess it should be in KDE Control Centre...[/QUOTE]

Yeah, I looked in there but couldn't find it.  I honestly don't think it's possible in KDE to set this ... Maybe someone else will figure it out.

:)

---

### Post by foxy123 on 2005-11-26
[QUOTE=Footer]Yeah, I looked in there but couldn't find it.  I honestly don't think it's possible in KDE to set this ... Maybe someone else will figure it out.

:)[/QUOTE]
it is definitely possible since I did it in SuSE, but have not used it for a while.

Found it: KControl Center/KDE Components/Component Chooser

---

### Post by quietglow on 2005-11-26
Excellent guide...the RC3 is SUPER fast!

---

### Post by Footer on 2005-11-26
[QUOTE=foxy123]it is definitely possible since I did it in SuSE, but have not used it for a while.

Found it: KControl Center/KDE Components/Component Chooser[/QUOTE]

Ahh, yes, you are right!!!  I have nothing in the 'Web Browser' component chooser yet it works fine.  Hmmmm ...

---

### Post by Revert on 2005-11-27
I've installed 1.5 v. 3 following the instructions in this thread, and so far everything's been peachy.  I got a chrome error a few times, and it wasn't set as my default browser for awhile, but all that's been worked out.

The one thing I'm having trouble with involves the search plugins in the top right.  I know to delete them you just delete them from the the search plugins folder, but the thing is...I apparently don't have one.  I know where the folder for the ones I've installed myself is, but the usual search plugins folder isn't in the normal directory and I haven't been able to find it through searching.  Is this normal or did I screw something up during the install?  Do other people have the search plugins folder in the normal directory?

---

### Post by jrib on 2005-11-27
[QUOTE=Revert]IDo other people have the search plugins folder in the normal directory?[/QUOTE]

/opt/firefox/searchplugins/ is there for me

---

### Post by Revert on 2005-11-27
[QUOTE=_jason]/opt/firefox/searchplugins/ is there for me[/QUOTE]

Thank you! :p 
It wasn't showing up in my searches or anything.  I can finally get rid of Yahoo now.

---

### Post by jrib on 2005-11-27
[QUOTE=Revert]Thank you! :p 
It wasn't showing up in my searches or anything.  I can finally get rid of Yahoo now.[/QUOTE]

lol, I did the same thing :)

---

### Post by janfsd on 2005-11-29
hi, i followed the tutorial but firefox doesnt seem to run in my computer , i got some chrome registering errors and in the terminal it gives this:

```
(firefox-bin:9572): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(firefox-bin:9572): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:9572): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No such file or directory

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/opt/firefox/run-mozilla.sh: line 131:  9572 Aborted                 "$prog" ${1+"$@"}

```

it seems to be come pango errors,this happened with firefox  1.5rc3 and im running in a AMD64
pls can somebody help?

---

### Post by lucas on 2005-11-29
firefox 1.5 is released!

source: [http://www.osnews.com/](http://www.osnews.com/)
get it here: [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686)
or here: [http://www.mozilla.org/mirrors.html](http://www.mozilla.org/mirrors.html)

:)

---

### Post by Logic* on 2005-11-29
I have RC2 installed as per the method shown in this thread. Could someone tell me how to update to the final version?

Thanks

EDIT: Never mind, I got it :)

---

### Post by foxy123 on 2005-11-29
[QUOTE=lucas]firefox 1.5 is released!

source: [http://www.osnews.com/](http://www.osnews.com/)
get it here: [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686)
or here: [http://www.mozilla.org/mirrors.html](http://www.mozilla.org/mirrors.html)

:)[/QUOTE]
it's the same as RC3 as I understand. I wonder when it will hit repos? I like to have things 'properly' installled and firefox in /opt makes me a bit uneasy, though I really enjoy 1.5...

---

### Post by veloct on 2005-11-29
I have it and thuderbird running from /opt without any issues.  It is the same are RC3.  To get update to work all you have to do is make sure that the /opt/firefox directory has permissions set for user instead of root. I updated from RC1 -> RC2 -> RC3 (and final) via the update  option built into firefox.

---

### Post by foxy123 on 2005-11-29
[QUOTE=veloct]I have it and thuderbird running from /opt without any issues.  It is the same are RC3.  To get update to work all you have to do is make sure that the /opt/firefox directory has permissions set for user instead of root. I updated from RC1 -> RC2 -> RC3 (and final) via the update  option built into firefox.[/QUOTE]
i've got some issues with firefox, like blinking bookmarks (it is difficult to explain, you open bookmarks menu and hover mouse over any bookmark folder, instead to expand the folder, its blinking, so you have to click and then click on the bookmark... it is messy, anyway it never happened with 1.07), so I was hoping to get it sorted in a 'proper' install. (it may be my wm theme although or anthing like that).

The main reason I am looking forward for official package is that I want to compile moztrabiff extension for 1.5 and need firefoox development package.

---

### Post by orbinick on 2005-11-29
I used the wiki to guide me in the installation of FF1.5, but I didn't cut the plugin as it was working perfectly on 1.07, and guess what, it works!!

I installed the plugin with the latest version of EasyUbuntu because it never fails to correctly apply the plugin.

---

### Post by benplaut on 2005-11-30
in KDE, the menu fonts are somewhere around 14, regardless of settings elsewhere... any suggestions?

---

### Post by makhand on 2005-11-30
I cant seem to get java to work with 1.5 any good ideas?

---

### Post by foxy123 on 2005-11-30
[QUOTE=makhand]I cant seem to get java to work with 1.5 any good ideas?[/QUOTE]
java works fine for me... I guess I did not do anything specific to enable it.

---

### Post by PenguinZdravko on 2005-11-30
Is Firefox 1.5 Final 1.5 RC3, because in my about dialog it's still showing build date 20051111?

---

### Post by foxy123 on 2005-11-30
[QUOTE=PenguinZdravko]Is Firefox 1.5 Final 1.5 RC3, because in my about dialog it's still showing build date 20051111?[/QUOTE]
apparently it is... at least it is said on Mozilla forums

---

### Post by TheJoker on 2005-11-30
Any successful reports of running FF1.5 on AMD64? Thanks!

---

### Post by makhand on 2005-11-30
[QUOTE=foxy123]java works fine for me... I guess I did not do anything specific to enable it.[/QUOTE]

Is there anyone for whom it didnt work, but works now? I cant get any applets to come up (yahoo games, poker). It worked fine under 1.0.X... i'd hate to have to switch back

---

### Post by foxy123 on 2005-11-30
[QUOTE=makhand]Is there anyone for whom it didnt work, but works now? I cant get any applets to come up (yahoo games, poker). It worked fine under 1.0.X... i'd hate to have to switch back[/QUOTE]
does about:plugins show java?

---

### Post by makhand on 2005-11-30
[QUOTE=foxy123]does about:plugins show java?[/QUOTE]

Thats weird, it looks like it might: 
```
Java(TM) Plug-in Blackdown-1.4.2-02

    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_08 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_08 	Java 		Yes

```

however, the applets dont start when a page calls for them.

---

### Post by Evoreth on 2005-11-30
The middle mouse button doesn't close tabs anymore. How can I change that? I'm really used to that feature. :(

---

### Post by dweez on 2005-11-30
Thanks alot for the How-To.  Works great.  I had an error regarding "Chrome" come up 2x on the first start up but nothing since.

One question though, now that I have 1.5 installed, is it safe to uninstall 1.07?  Also, when I first began to uninstall it (via Synaptic), it prompted me to uninstall ubuntu-desktop too so I canceled the removal.  Doing a google search, I heard some people say that removal of ubuntu-desktop shouldn't hurt anything (not sure about this, based on the name and the description for it in Synaptic it seems like it might be a crucial component).  For the time being, I'm just gonna leave 1.07 alone as it really isn't hurting anything.  I just like to remove superflous software when it isn't needed.

dweez

---

### Post by foxy123 on 2005-11-30
[QUOTE=dweez]Thanks alot for the How-To.  Works great.  I had an error regarding "Chrome" come up 2x on the first start up but nothing since.

One question though, now that I have 1.5 installed, is it safe to uninstall 1.07?  Also, when I first began to uninstall it (via Synaptic), it prompted me to uninstall ubuntu-desktop too so I canceled the removal.  Doing a google search, I heard some people say that removal of ubuntu-desktop shouldn't hurt anything (not sure about this, based on the name and the description for it in Synaptic it seems like it might be a crucial component).  For the time being, I'm just gonna leave 1.07 alone as it really isn't hurting anything.  I just like to remove superflous software when it isn't needed.

dweez[/QUOTE]
ubuntu-desktop is a meta package... it is safe to remove it. It only matters if you will be upgrading from Breezy to Dapper Drake in future, you will like to have it back....

---

### Post by Cl1mh4224rd on 2005-11-30
[Whoa, I'm an idiot. Ignore this...]

---

### Post by gmleuty on 2005-11-30
[QUOTE=veloct]To get update to work all you have to do is make sure that the /opt/firefox directory has permissions set for user instead of root.[/QUOTE]
Many thanks for the tip.

---

### Post by jdong on 2005-11-30
[QUOTE=Evoreth]The middle mouse button doesn't close tabs anymore. How can I change that? I'm really used to that feature. :([/QUOTE]
about:config, middlemouse.contentLoadURL set to **FALSE**


As far as chowning firefox to a user, that is not a smart decision... It's better to run the browser under gksudo from time to time in order to get updates instead. Ordinary user accounts writing to binaries that multiple users may run, that sounds like a security risk.

---

### Post by nozdormu on 2005-11-30
[QUOTE=foxy123]i've got some issues with firefox, like blinking bookmarks (it is difficult to explain, you open bookmarks menu and hover mouse over any bookmark folder, instead to expand the folder, its blinking, so you have to click and then click on the bookmark... it is messy, anyway it never happened with 1.07), so I was hoping to get it sorted in a 'proper' install. (it may be my wm theme although or anthing like that).

The main reason I am looking forward for official package is that I want to compile moztrabiff extension for 1.5 and need firefoox development package.[/QUOTE]

I mentioned in another thread that this bug has already been filed and all dupes redirected to here: [https://bugzilla.mozilla.org/show_bug.cgi?id=306426]("https://bugzilla.mozilla.org/show_bug.cgi?id=306426")

Even though it seems to be a widespread problem, not much attention has been paid towards fixing it because it is hard to reliably reproduce.  It happens to me, but restarting Firefox fixes it and it may or may not happen again while browsing.

---

### Post by towsonu2003 on 2005-11-30
[QUOTE=fishfork]How to do it **without** messing up your system and confusing the package manager (hopefully!)

The Howto is on the wiki at [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion). Comments here please.[/QUOTE]

perfect guide!

though I'm having "chrome registration" issues after every extension install, I don't care (Dapper is 4 months away hehheh)

= +1 happier user

---

### Post by orb_nsc on 2005-11-30
Well I'm impressed.  It feels like I added another gig of ram to this machine, just by upgrading Firefox.  Thanks for yet another awesome HOWTO!  The last time I tried to update Firefox manually on Ubuntu, I screwed it up so bad it took the rest of the afternoon to correct...

---

### Post by slrafal on 2005-12-01
This is probably a stupid newbie question, but I followed the wiki instructions and I don't see firefox in my *internet* menu.

---

### Post by nozdormu on 2005-12-01
[QUOTE=towsonu2003]perfect guide!

though I'm having "chrome registration" issues after every extension install, I don't care (Dapper is 4 months away hehheh)

= +1 happier user[/QUOTE]

If you disable the Talkback extension, those errors go away.

---

### Post by Iandefor on 2005-12-01
Who needs Firefox when you have links? :)
Ironically, I just installed and am using links and I
actually prefer it over Firefox. Go figure.

Chanders: I tried updating using your method and just got 1.07 even with backports.

---

### Post by towsonu2003 on 2005-12-01
[QUOTE=nozdormu]If you disable the Talkback extension, those errors go away.[/QUOTE]

hey thanks! :)

[QUOTE=Iandefor]I just installed and am using links and I
actually prefer it over Firefox[/QUOTE]

mean lynx? (or elinks)? I like both as well. no flash, no annoying banners, and very fast browsing :rolleyes: :cool:

---

### Post by Iandefor on 2005-12-01
The package I installed was entitled "links" and the executable is "links" so I
figure it'd be safe to call it "links" :D. [Here's]("http://artax.karlin.mff.cuni.cz/%7Emikulas/links/") the project's home page, in case you're interested.

---

### Post by erik-the-red on 2005-12-01
It seems like this "final" release is naught more than RC3.

Does that mean SCIM still poops out Firefox 1.5 "final"?

---

### Post by NegativeZero on 2005-12-01
[QUOTE=janfsd]hi, i followed the tutorial but firefox doesnt seem to run in my computer , i got some chrome registering errors and in the terminal it gives this:

```
(firefox-bin:9572): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(firefox-bin:9572): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:9572): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No such file or directory

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9572): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/opt/firefox/run-mozilla.sh: line 131:  9572 Aborted                 "$prog" ${1+"$@"}

```

it seems to be come pango errors,this happened with firefox  1.5rc3 and im running in a AMD64
pls can somebody help?[/QUOTE]

I'm also getting this problem with Firefox 1.5. I followed the howto exactly (twice, omitting some of the earlier commands eg making directories etc) and Firefox will not load. 

Previously I was running the stock 1.0.7 included with Ubuntu 5.10, which still works (I am posting from it now). Machine is a 64-bit Pentium 4, and I'm running the AMD64 distribution. Language is set to English (Australian) via the Language Selector (EDIT: Switching to English (USA) doesn't fix the problem).


EDIT: Problem semi-solved - it runs fine using linux32, as specified [here](http://www.ubuntuforums.org/showthread.php?t=90106)

---

### Post by doundounba on 2005-12-01
Thanks for this Howto! Very useful! Is there a reason why prefs.js is not included in the files copied over from the old profile? An incompatibility? Some people might be surprised to follow these instructions and loose their preferences. BTW, I did copy it and things seem fine so far...

Also, I think it would be nice if these instructions included something in the case where one has multiple profiles setup. Something like backup all the old profiles somewhere else (like say ~/tmp), then create a new profile with the same name as all the old ones, and for each one, cp the files from the old to the new profile... Just a thought.

EDIT: There also seems to be a file named hostperm.1 that is needed to carry over, or the list of all the sites that can or can't save cookies are lost.

---

### Post by ruffneck on 2005-12-02
Thanks alot for this guide it works a charm! As have been said earlier...firefox is really breezing through now! ;)

---

### Post by KillerKiwi on 2005-12-02
Install Klik
Press Alt-f2 and paste
```
wget klik.atekon.de/client/install -O -|sh
```

Then click these links
[klik://firefox]("klik://firefox")
[klik://thunderbird]("klik://thunderbird")

To delete(uninstall) just trash the file on your desktop

---

### Post by erik-the-red on 2005-12-02
So, what about 1.5 "final" and SCIM?

---

### Post by arnieboy on 2005-12-04
**Update:**
[COLOR="Blue"]**Please use [Automatix]("http://ubuntuforums.org/showthread.php?t=66563") to install Firefox 1.5 and all its plugins with just one click. Please use that instead of this script.**[/COLOR]

---

### Post by Rob2687 on 2005-12-04
It didn't keep anything. :( Just uninstalled some stuff with apt-get then installed a fresh copy of 1.5
Oh well..

Here's the terminal stuff if it's any use
```
robert@ubuntu:~/Desktop$ ./firefox_install
firefox-bin: no process killed
firefox: no process killed
--17:36:11--  http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux- i686/en-US/firefox-1.5.tar.gz
           => `firefox-1.5.tar.gz'
Resolving ftp.mozilla.org... 64.50.236.52, 64.50.238.52, 216.165.129.134, ...
Connecting to ftp.mozilla.org|64.50.236.52|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,444,956 (8.1M) [application/x-gzip]

100%[==========================================================================================>] 8,444,956    195.91K/s    ETA 00:00

17:36:50 (215.28 KB/s) - `firefox-1.5.tar.gz' saved [8444956/8444956]

tar: /opt: Not found in archive
tar: Error exit delayed from previous errors
cp: `/usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so' and `/opt/firefox/plugins/libjavaplugin_oji.so' are the same file
cp: `/usr/lib/mozilla-firefox/plugins/mplayerplug-in-gmp.so' and `/opt/firefox/plugins/mplayerplug-in-gmp.so' are the same file
cp: `/usr/lib/mozilla-firefox/plugins/mplayerplug-in-gmp.xpt' and `/opt/firefox/plugins/mplayerplug-in-gmp.xpt' are the same file
cp: `/usr/lib/mozilla-firefox/plugins/mplayerplug-in-qt.so' and `/opt/firefox/plugins/mplayerplug-in-qt.so' are the same file
cp: `/usr/lib/mozilla-firefox/plugins/mplayerplug-in-qt.xpt' and `/opt/firefox/plugins/mplayerplug-in-qt.xpt' are the same file
cp: `/usr/lib/mozilla-firefox/plugins/mplayerplug-in-rm.so' and `/opt/firefox/plugins/mplayerplug-in-rm.so' are the same file
cp: `/usr/lib/mozilla-firefox/plugins/mplayerplug-in-rm.xpt' and `/opt/firefox/plugins/mplayerplug-in-rm.xpt' are the same file
cp: `/usr/lib/mozilla-firefox/plugins/mplayerplug-in.so' and `/opt/firefox/plugins/mplayerplug-in.so' are the same file
cp: `/usr/lib/mozilla-firefox/plugins/mplayerplug-in-wmp.so' and `/opt/firefox/plugins/mplayerplug-in-wmp.so' are the same file
cp: `/usr/lib/mozilla-firefox/plugins/mplayerplug-in-wmp.xpt' and `/opt/firefox/plugins/mplayerplug-in-wmp.xpt' are the same file
cp: `/usr/lib/mozilla-firefox/plugins/mplayerplug-in.xpt' and `/opt/firefox/plugins/mplayerplug-in.xpt' are the same file
cp: `/usr/lib/mozilla/plugins/libjavaplugin_oji.so' and `/opt/firefox/plugins/libjavaplugin_oji.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-gmp.so' and `/opt/firefox/plugins/mplayerplug-in-gmp.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-gmp.xpt' and `/opt/firefox/plugins/mplayerplug-in-gmp.xpt' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-qt.so' and `/opt/firefox/plugins/mplayerplug-in-qt.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-qt.xpt' and `/opt/firefox/plugins/mplayerplug-in-qt.xpt' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-rm.so' and `/opt/firefox/plugins/mplayerplug-in-rm.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-rm.xpt' and `/opt/firefox/plugins/mplayerplug-in-rm.xpt' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in.so' and `/opt/firefox/plugins/mplayerplug-in.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so' and `/opt/firefox/plugins/mplayerplug-in-wmp.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-wmp.xpt' and `/opt/firefox/plugins/mplayerplug-in-wmp.xpt' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in.xpt' and `/opt/firefox/plugins/mplayerplug-in.xpt' are the same file
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  beagle firefox firefox-gnome-support gnome-app-install j2re1.4-mozilla-plugin libgecko2.0-cil mozilla-firefox mozilla-mplayer yelp
0 upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 40.6MB disk space will be freed.
(Reading database ... 107072 files and directories currently installed.)
Removing beagle ...
Removing mozilla-mplayer ...
Removing j2re1.4-mozilla-plugin ...
Removing libgecko2.0-cil ...
Removing yelp ...
Removing gnome-app-install ...
Removing mozilla-firefox ...
Removing firefox-gnome-support ...
Updating mozilla-firefox chrome registry...done.
Removing firefox ...
find: warning: you have specified the -depth option after a non-option argument -type, but options are not positional (-depth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

Running prelink, please wait...

```

---

### Post by arnieboy on 2005-12-04
[QUOTE=Rob2687]It didn't keep anything. :( Just uninstalled some stuff with apt-get then installed a fresh copy of 1.5
Oh well..[/QUOTE]
woops.. gimme a minute.. will correct a bug.

---

### Post by TwiceOver on 2005-12-04
Heh... Trashed my FireFox.  Had to get 1.07 through the package manager.

```

firefox-bin: no process killed
firefox: no process killed
--16:44:13--  http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686/en-US/firefox-1.5.tar.gz
           => `firefox-1.5.tar.gz'
Resolving ftp.mozilla.org... 64.50.236.52, 64.50.238.52, 216.165.129.134, ...
Connecting to ftp.mozilla.org|64.50.236.52|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,444,956 (8.1M) [application/x-gzip]

100%[====================================>] 8,444,956    318.59K/s    ETA 00:00

16:44:42 (283.49 KB/s) - `firefox-1.5.tar.gz' saved [8444956/8444956]

tar: /opt: Not found in archive
tar: Error exit delayed from previous errors
cp: `/opt/firefox/plugins/': specified destination directory does not exist
Try `cp --help' for more information.
cp: `/opt/firefox/plugins/': specified destination directory does not exist
Try `cp --help' for more information.
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  firefox firefox-gnome-support gnome-app-install mozilla-mplayer
  ubuntu-desktop yelp
0 upgraded, 0 newly installed, 6 to remove and 5 not upgraded.
Need to get 0B of archives.
After unpacking 37.1MB disk space will be freed.
(Reading database ... 90473 files and directories currently installed.)
Removing mozilla-mplayer ...
Removing ubuntu-desktop ...
Removing yelp ...
Removing gnome-app-install ...
dpkg - warning: while removing gnome-app-install, directory `/usr/lib/gnome-app-install' not empty so not removed.
Removing firefox-gnome-support ...
Updating mozilla-firefox chrome registry...done.
Removing firefox ...
find: warning: you have specified the -depth option after a non-option argument -type, but options are not positional (-depth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

./firefox_install: line 12: exec: firefox: not found
root@Lappy:~/Desktop# firefox
bash: firefox: command not found


```

---

### Post by LaSSarD on 2005-12-04
maybe a sudo mkdir /opt on the start of the script will help yo ;)

---

### Post by arnieboy on 2005-12-04
bug fixed in the tar command. should work now.
Please redownload and try again.

---

### Post by arnieboy on 2005-12-04
[QUOTE=LaSSarD]maybe a sudo mkdir /opt on the start of the script will help yo ;)[/QUOTE]
/opt does exist by default on ubuntu AFAIK.

---

### Post by arnieboy on 2005-12-04
any positive news?

---

### Post by TwiceOver on 2005-12-04
Well it worked I guess.  Ton of errors.  Not really sure what happened but my version now says 1.5.

Got a popup error "Firefox could not install this item due to an error in Chrome Registration.  Please contact the author about this problem".

---

### Post by arnieboy on 2005-12-04
[QUOTE=TwiceOver]Well it worked I guess.  Ton of errors.  Not really sure what happened but my version now says 1.5.

Got a popup error "Firefox could not install this item due to an error in Chrome Registration.  Please contact the author about this problem".[/QUOTE]
tons of errors??

just one error bud and its inconsequential.

yeah that error is a gnome based issue (cannot be avoided) and its not a showstopper. it wont come up again (after the first time).
enjoy the sheer speed of firefox 1.5 and if u are in a good enuf mood, try and thank me ;)

what happened was that firefox 1.0.7 was removed, ur settings backed up, version 1.5 downloaded and installed, plugins copied and some of the old settings copied back.

---

### Post by TwiceOver on 2005-12-04
Don't get me wrong... Thanks a bunch.  Read the last how to and it looked like too much hastle.

The errors I got were in the terminal window.  Either way it works.

---

### Post by arnieboy on 2005-12-04
[QUOTE=TwiceOver]Don't get me wrong... Thanks a bunch.  Read the last how to and it looked like too much hastle.

The errors I got were in the terminal window.  Either way it works.[/QUOTE]
the old howto does nothing to keep ur plugins.
this script does that too..
thanks for the appreciation :)

---

### Post by arnieboy on 2005-12-04
I know there are a lot of people here playing the waiting game: "is it safe enuf and bug-free yet to use? are u sure it wont screw up my computer?"
lol.. yeah its bug-free now.. there was one bug in in the first release which got resolved within 2 minutes... go ahead and use it now. create your panel, menu and desktop shortcuts for firefox 1.5 and enjoy it :)

the only issue u might face is with java plugins. if u do let me know and I will tell u how to fix it.

---

### Post by bored2k on 2005-12-04
What exactly does the script do? Does it dpkg-divert firefox? What?

---

### Post by arnieboy on 2005-12-04
[QUOTE=bored2k]What exactly does the script do? Does it dpkg-divert firefox? What?[/QUOTE]
no it doesnt. it makes firefox repo independent.
the sequence of events is as follows:
> 1) closes all instances of firefox
2) downloads firefox 1.5
3) untars the package
4) copies it to /opt/
5) copies all existing plugins of firefox 1.0.7 to firefox 1.5
6) removes firefox 1.0.7
7) backs up the .mozilla (user settings directory)
7) removes the firefox 1.0.7 shortcut (if any) from /usr/bin
8) installs the firefox 1.5 shortcut in /usr/bin
9) runs firefox 1.5 once to create a fresh settings (.mozilla) directory
10) closes all windows of firefox 1.5
11) copies bookmarks, history, cookies etc from the backup directory to the new .mozilla directory.

any more suggestions?

**I did not use the dpkg-divert trick because by any chance if u use firefox 1.0.7 alongside firefox 1.5, there is a very high probability of your settings (.mozilla directory getting screwed up)**

---

### Post by pomalin on 2005-12-04
for me it remove also epiphany, libgecko, yelp, and I loose my bookmarks .....

---

### Post by arnieboy on 2005-12-04
[QUOTE=pomalin]for me it remove also epiphany, libgecko, yelp, and I loose my bookmarks .....[/QUOTE]
yes thats a problem... epiphany depends on firefox 1.0.7. 
if u install epiphany u wont have firefox 1.5
ur bookmarks shd have got restored..
well anyway herez how to get them back.
```
cd $HOME/.mozilla_backup/firefox/*.default
cp -f bookmarks.html ~/.mozilla/firefox/*.default/
```

---

### Post by bored2k on 2005-12-04
[QUOTE=pomalin]for me it remove also epiphany, libgecko, yelp, and I loose my bookmarks .....[/QUOTE]
That's because ephiphany-browser depends on Firefox.

arnieboy, maybe your script shouldn't remove apt firefox ? You could always rename the firefox in usr/bin and find a way other than dpkg-divert to make apps load the firefox in /opt (just like if the user set them up in prefered apps)?

---

### Post by Iandefor on 2005-12-04
Hey, It worked fine for me! Worked much better than the howto, I must say. Required minimal tweaking on my part (Sudo is broken at the moment; I just had to remove all instances of 'sudo' and start it up as root, and even then, it wasn't the fault of the script). I have just one suggestion: retain the packages that depend on firefox when 1.07 is uninstalled, if at all possible, or reinstall them after 1.5 is installed. It removed epiphany and yelp from my system along with a bunch of metapackages like gnome-desktop.

---

### Post by bored2k on 2005-12-04
[QUOTE=arnieboy]yes thats a problem... epiphany depends on firefox 1.0.7. 
if u install epiphany u wont have firefox 1.5
ur bookmarks shd have got restored..
well anyway herez how to get them back.
```
cd $HOME/.mozilla_backup/firefox/*.default
cp -f bookmarks.html ~/.mozilla/firefox/*.default/
```[/QUOTE]
You could safely install epiphany using what my above post says. I know it works because I've done tht quite a few times with my 1.5 install.

---

### Post by arnieboy on 2005-12-04
[QUOTE=bored2k]That's because ephiphany-browser depends on Firefox.

arnieboy, maybe your script shouldn't remove apt firefox ? You could always rename the firefox in usr/bin and find a way other than dpkg-divert to make apps load the firefox in /opt (just like if the user set them up in prefered apps)?[/QUOTE]
the problem with that is the following:
If i rename the firefox 1.5 shortcut in /usr/bin to something else, and dont remove firefox 1.0.7, it will remain in the gnome menu, and people will invariably run firefox 1.0.7. That will conclusively screw up the .mozilla (settings directory). the main problem is that firefox 1.5 does not use a different user settings directory. it uses the same freaking .mozilla/firefox (as version 1.0.7 and all other versions)
Its a lame bug... and needs to be fixed by the firefox devs.. they should make sure every user settings directory goes under a different version based sub directory.

if that is implemented, we dont need to remove anything (we can have ten versions of firefox coexisting)

---

### Post by pomalin on 2005-12-04
[QUOTE=arnieboy]
ur bookmarks shd have got restored..
well anyway herez how to get them back.
```
cd $HOME/.mozilla_backup/firefox/*.default
cp -f bookmarks.html ~/.mozilla/firefox/*.default/
```[/QUOTE]

Yes for the bookmarks, thanks.

Arfff for epiphany :)

---

### Post by jrib on 2005-12-04
[QUOTE=arnieboy]the problem with that is the following:
If i rename the firefox 1.5 shortcut in /usr/bin to something else, and dont remove firefox 1.0.7, it will remain in the gnome menu, and people will invariably run firefox 1.0.7. That will conclusively screw up the .mozilla (settings directory). the main problem is that firefox 1.5 does not use a different user settings directory. it uses the same freaking .mozilla (as version 1.0.7)[/QUOTE]

At the very least I think your first post should inlcude a warning informing users which packages are going to get removed because they depend on 1.07.  A lot of newbies are just going to run this script straight though pressing 'y' everytime they are asked a question.  Then they are going to wonder why they can no longer go to help or add-applications.

[e] never mind, I see you have added that now.  It will also cause "add applications" to be removed iirc.

---

### Post by arnieboy on 2005-12-04
[QUOTE=bored2k]You could safely install epiphany using what my above post says. I know it works because I've done tht quite a few times with my 1.5 install.[/QUOTE]
if u install epiphany again, it will again install firefox 1.0.7.. so we get back to square 1.

---

### Post by arnieboy on 2005-12-04
[QUOTE=_jason]At the very least I think your first post should inlcude a warning informing users which packages are going to get removed because they depend on 1.07.  A lot of newbies are just going to run this script straight though pressing 'y' everytime they are asked a question.  Then they are going to wonder why they can no longer go to help or add-applications.[/QUOTE]
says that in the first post in bold.
"**uninstalls epiphany and yelp**"

---

### Post by arnieboy on 2005-12-04
[QUOTE=_jason]never mind, I see you have added that now.  It will also cause "add applications" to be removed iirc.[/QUOTE]
yes added "add applications" to the "will get uninstalled" list. thanks :)

---

### Post by arnieboy on 2005-12-04
naah.. this needs to be done better.. its doing its job but uninstalling a few key things.. any fresh ideas?

---

### Post by nix4me on 2005-12-04
[QUOTE=arnieboy]naah.. this needs to be done better.. its doing its job but uninstalling a few key things.. any fresh ideas?[/QUOTE]

The right way would be for the Ubuntu devs to realease a backport.  1.07 was broken from day one.  You would think they would have made 1.5 an instant upgrade.  I know its difficult and all for them, but it really is a huge deal.

nix4me

---

### Post by arnieboy on 2005-12-04
[QUOTE=nix4me]The right way would be for the Ubuntu devs to realease a backport.  1.07 was broken from day one.  You would think they would have made 1.5 an instant upgrade.  I know its difficult and all for them, but it really is a huge deal.

nix4me[/QUOTE]
I am aware of the backports situation. The fact is that backporting firefox is too big a security headache more than anything else. as far I remember jdong's words, its NOT going to be backported in breezy.

---

### Post by jrib on 2005-12-04
[QUOTE=arnieboy]naah.. this needs to be done better.. its doing its job but uninstalling a few key things.. any fresh ideas?[/QUOTE]

I'm not sure people should be doing this without understanding what they are doing.

But if you really want to write a script for it:  I don't understand what's wrong with the method the wiki uses.  I understand your concern that running 1.07 accidently will mess up your profile (happened to me with the beta's before I figured out what was going on).  You have to ensure that the default browser runs the "firefox" command and not the "mozilla-firefox" (not sure how to do that with a script but probably googlable (heh new word?--probably not)).  Or you can dpkg-divert the mozilla-firefox command as well.  Any other way that the old version could be run (other than an absolute path to the binary)?

---

### Post by nix4me on 2005-12-04
[QUOTE=arnieboy]I am aware of the backports situation. The fact is that backporting firefox is too big a security headache more than anything else. as far I remember jdong's words, its NOT going to be backported in breezy.[/QUOTE]

Agreed.  I read that too.  Thats too bad.

Honestly, the wiki instructions work fine.  Are people having issues with those instructions?

nix4me

---

### Post by arnieboy on 2005-12-04
[QUOTE=_jason]I'm not sure people should be doing this without understanding what they are doing.

But if you really want to write a script for it:  I don't understand what's wrong with the method the wiki uses.  I understand your concern that running 1.07 accidently will mess up your profile (happened to me with the beta's before I figured out what was going on).  You have to ensure that the default browser runs the "firefox" command and not the "mozilla-firefox" (not sure how to do that with a script but probably googlable (heh new word?--probably not)).  Or you can dpkg-divert the mozilla-firefox command as well.  Any other way that the old version could be run (other than an absolute path to the binary)?[/QUOTE]
sounds like a good idea.. lemme give it a try.

---

### Post by thechitowncubs on 2005-12-04
[QUOTE=nix4me]Agreed.  I read that too.  Thats too bad.

Honestly, the wiki instructions work fine.  Are people having issues with those instructions?

nix4me[/QUOTE]
those work for me everytime

---

### Post by arnieboy on 2005-12-04
**Alright, thanks to jason and some more rethinking on my part, I have edited and updated the script. This time it does not remove firefox 1.0.7 or any other package. Hope this works for u!**

---

### Post by jrib on 2005-12-04
[QUOTE=arnieboy]**Alright, thanks to jason and some more rethinking on my part, I have edited and updated the script. This time it does not remove firefox 1.0.7 or any other package. Hope this works for u!**[/QUOTE]

How did you manage to make sure mozilla-firefox doesn't get run?

---

### Post by arnieboy on 2005-12-04
[QUOTE=_jason]How did you manage to make sure mozilla-firefox doesn't get run?[/QUOTE]
the only executable is /usr/bin/firefox which has been dpkg-divert-ed.. so no other issues that I can see.

---

### Post by majikstreet on 2005-12-04
majikstreet@oreo:/usr/bin$ ls | grep firefox
lrwxrwxrwx   1 root        root           20 2005-12-03 19:38 firefox -> /opt/firefox/firefox
lrwxrwxrwx   1 root        root           30 2005-10-12 16:09 firefox.ubuntu -> ../lib/mozilla-firefox/firefox
lrwxrwxrwx   1 root        root           30 2005-10-12 16:09 mozilla-firefox -> ../lib/mozilla-firefox/firefox

---

### Post by jstritar on 2005-12-04
Has anyone figured out what is causing the "Chrome Registration" errors when installing extensions? The error comes up but it seems to install fine. It'd be nice if I could figure this out b/c I'm an extension author and would like to know when it really does fail.

---

### Post by arnieboy on 2005-12-04
[QUOTE=majikstreet]majikstreet@oreo:/usr/bin$ ls | grep firefox
lrwxrwxrwx   1 root        root           20 2005-12-03 19:38 firefox -> /opt/firefox/firefox
lrwxrwxrwx   1 root        root           30 2005-10-12 16:09 firefox.ubuntu -> ../lib/mozilla-firefox/firefox
lrwxrwxrwx   1 root        root           30 2005-10-12 16:09 mozilla-firefox -> ../lib/mozilla-firefox/firefox[/QUOTE]
yes as long as mozilla-firefox is not called, its fine.

---

### Post by jrib on 2005-12-04
[QUOTE=arnieboy]yes as long as mozilla-firefox is not called, its fine.[/QUOTE]

the problem is that, at least for me, my default broweser in "system -> prefs -> preferred apps" was set to run mozilla-firefox.  This meant that if I didn't already have 1.5 open and clicked on a link in an email, it would run 1.07 since it ran the mozilla-firefox command.

---

### Post by arnieboy on 2005-12-04
[QUOTE=_jason]the problem is that, at least for me, my default broweser in "system -> prefs -> preferred apps" was set to run mozilla-firefox.  This meant that if I didn't already have 1.5 open and clicked on a link in an email, it would run 1.07 since it ran the mozilla-firefox command.[/QUOTE]
**Added a dpkg-divert to mozilla-firefox**
this shd resolve that issue as well..

---

### Post by jrib on 2005-12-04
[QUOTE=arnieboy]**Added a dpkg-divert to mozilla-firefox**
this shd resolve that issue as well..[/QUOTE]

```
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
exec firefox

```

won't that mean that if "mozilla-firefox" get's run, you will get a command not found?

---

### Post by arnieboy on 2005-12-04
[QUOTE=_jason]```
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
exec firefox

```

won't that mean that if "mozilla-firefox" get's run, you will get a command not found?[/QUOTE]
yes thats the whole idea.

---

### Post by jrib on 2005-12-04
[QUOTE=arnieboy]yes thats the whole idea.[/QUOTE]

But if I have mozilla-firefox running as my preferred application I will not be able to click on links in applications like my email client.  Wouldn't it be better to add a symlink to the new firefox like you did for the original firefox command?

---

### Post by arnieboy on 2005-12-04
[QUOTE=_jason]But if I have mozilla-firefox running as my preferred application I will not be able to click on links in applications like my email client.  Wouldn't it be better to add a symlink to the new firefox like you did for the original firefox command?[/QUOTE]
hey thats a great idea! script updated. Thanks Jason. I guess that resolves all the issues.

---

### Post by erikpiper on 2005-12-04
How do you get it to stop saying it couldn't install chrome whatever? It needs an OK every start- annoying.

Neat! I was about to try out 1.5- but then the script came!
Also, for me nothing was backed up- I had backups for my bookmarks though! :)

---

### Post by arnieboy on 2005-12-04
[QUOTE=erikpiper]How do you get it to stop saying it couldn't install chrome whatever? It needs an OK every start- annoying.

Neat! I was about to try out 1.5- but then the script came!
Also, for me nothing was backed up- I had backups for my bookmarks though! :)[/QUOTE]
the chrome registration thing is a gnome thing.
bookmarks, cookies and history :)

---

### Post by nix4me on 2005-12-04
User has to have ownership of the installed dir to get rid of chrome errors.

See the wiki. (Firefox New Version)


nix4me

---

### Post by erikpiper on 2005-12-04
Wait a sec- Nevermind!
I only get the errors when I installed an extention or theme- Never mind! sorry.

---

### Post by arnieboy on 2005-12-04
[QUOTE=nix4me]User has to have ownership of the installed dir to get rid of chrome errors.

See the wiki. (Firefox New Version)


nix4me[/QUOTE]
I never followed the wiki and got the chrome error only the first time, never after that.. so its not an issue. and erikpiper just confirmed that fact.
and for that matter, its not wise to have user ownership on the directory in which your firefox files are installed. That, my friend is a severe security vulnerability.. (same reason why /usr/lib/mozilla-firefox where firefox 1.0.7 is installed does not have user ownership).
One more reason why people should not blindly trust the wiki.

---

### Post by nix4me on 2005-12-04
[QUOTE=arnieboy]I never followed the wiki and got the chrome error only the first time, never after that.. so its not an issue. and erikpiper just confirmed that fact.
and for that matter, its not wise to have user ownership on the directory in which your firefox files are installed. That, my friend is a severe security vulnerability.. (same reason why /usr/lib/mozilla-firefox where firefox 1.0.7 is installed does not have user ownership).
One more reason why people should not blindly trust the wiki.[/QUOTE]

Too bad that 1000's have probably already trusted it.

Good job on the Howto Arnieboy.  Thanks for helping the community.
nix4me

---

### Post by angrylittleman on 2005-12-04
thanks arnieboy, worked like a champ for me!

---

### Post by AndyAWS on 2005-12-04
I believe the reason the wiki suggests User ownership is to allow the user to update firefox through it's built in updater. Although I suppose you could run firefox as root to get the updates, however that is also a security risk.

---

### Post by nix4me on 2005-12-04
[QUOTE=AndyAWS]I believe the reason the wiki suggests User ownership is to allow the user to update firefox through it's built in updater. Although I suppose you could run firefox as root to get the updates, however that is also a security risk.[/QUOTE]

You are correct.  I went back and read up on the topic more.  This too might be why it's too complicated to backport before dapper is out?

Not sure but seems sort of logical I guess.

nix4me

---

### Post by laran on 2005-12-05
[QUOTE=crypto178]If it's the case, you can ~safely try these commands :
sudo rm -r /opt/firefox/plugins
sudo ln -s /usr/lib/mozilla-firefox/plugins /opt/firefox/plugins 

After that flash should be fine if it worked before (with breezy stock firefox). If it doesnt, please give us the output of
ls /usr/lib/mozilla-firefox/plugins/ 
and/or try to reinstall all necessary plugins using synaptic.[/QUOTE]

Thanks for this tip. Mplayer was busted for me and this fixed it. Nice work :)

---

### Post by Sajjen on 2005-12-05
I just used this script on a fresh installation of Kubuntu without installing the Firefox package first. Everything seemed to work fine at first, but Adblock only works if I run Firefox as root (sudo firefox). Any ideas?

---

### Post by arnieboy on 2005-12-05
[QUOTE=Sajjen]I just used this script on a fresh installation of Kubuntu without installing the Firefox package first. Everything seemed to work fine at first, but Adblock only works if I run Firefox as root (sudo firefox). Any ideas?[/QUOTE]
did u install the extension as sudo?

---

### Post by Sajjen on 2005-12-05
I downloaded the extension as a regular user, then started it with sudo. Thought that would fix the chrome registration thingie. I tried to uninstall Adblock and add it again, this time as a regular user but it just gets stuck in 'will be installed when Firefox is restarted'-mode.

---

### Post by arnieboy on 2005-12-05
[QUOTE=Sajjen]I downloaded the extension as a regular user, then started it with sudo. Thought that would fix the chrome registration thingie. I tried to uninstall Adblock and add it again, this time as a regular user but it just gets stuck in 'will be installed when Firefox is restarted'-mode.[/QUOTE]
well then u do realize what u did wrong... 
u shd have simply installed adblock as a regular user. the chrome registration thing should not be much of a bother unless u install extensions. the reason why its not working is because one of the extension files in your .mozilla directory is now owned by root (since u tried to install the extension as sudo).
try doing a ```
sudo chown -R user_name:user_name $HOME/.mozilla
``` 
where u need to replace user_name by your ubuntu user name and see if that helps.

---

### Post by strawman on 2005-12-05
I ran the script and it installed firefox 1.5 but it did not save my bookmarks; it is fast though.:smile:

---

### Post by arnieboy on 2005-12-05
[QUOTE=strawman]I ran the script and it installed firefox 1.5 but it did not save my bookmarks; it is fast though.:smile:[/QUOTE]
do the following to get back ur your old bookmarks:
```
cp -f ~/.mozilla_backup/firefox/*.default/bookmarks.html ~/.mozilla/firefox/*.default/
```

---

### Post by Sajjen on 2005-12-05
[QUOTE=arnieboy]well then u do realize what u did wrong... 
u shd have simply installed adblock as a regular user. the chrome registration thing should not be much of a bother unless u install extensions. the reason why its not working is because one of the extension files in your .mozilla directory is now owned by root (since u tried to install the extension as sudo).
try doing a ```
sudo chown -R user_name:user_name $HOME/.mozilla
``` 
where u need to replace user_name by your ubuntu user name and see if that helps.[/QUOTE]

That did the trick. Thanks a lot. (Should have figured that one out myself...)

---

### Post by strawman on 2005-12-05
got it! thank you;)

---

### Post by strawman on 2005-12-05
just a note on firefox 1.5:  seems like twice as fast on page loading and re-loading.   also disabled ipv6 in "about:config" which helps.

---

### Post by Sajjen on 2005-12-05
[QUOTE=Sajjen]That did the trick. Thanks a lot. (Should have figured that one out myself...)[/QUOTE]

Hmmm, this is strange. Seems it didn't do the trick. It worked fine until I closed Firefox and started it again. Now Adblock doesn't work, neither can I change themes. How would I go about uninstalling this? (so I can do it the right way)

---

### Post by arnieboy on 2005-12-05
[QUOTE=Sajjen]Hmmm, this is strange. Seems it didn't do the trick. It worked fine until I closed Firefox and started it again. Now Adblock doesn't work, neither can I change themes. How would I go about uninstalling this? (so I can do it the right way)[/QUOTE]
adblock is a very tricky customer.. Even advanced linux users treat it with caution.
try the following after closing all firefox windows:

```
sudo chown -R user_name:user_name .mozilla
mv .mozilla .mozilla_wont_screw_up_this_time
```
restart firefox

---

### Post by Sajjen on 2005-12-05
[QUOTE=arnieboy]adblock is a very tricky customer.. Even advanced linux users treat it with caution.
try the following after closing all firefox windows:

```
sudo chown -R user_name:user_name .mozilla
mv .mozilla .mozilla_wont_screw_up_this_time
```
restart firefox[/QUOTE]

That I have done, a few times. Didn't work. Perhaps it has something to do with the fact that I had not installed Firefox 1.0.7 before intalling 1.5?

---

### Post by hey560 on 2005-12-05
I looked into the "chrome registration" error that pops up when installing/uninstalling extensions.  It seems that this error does not come up when you start up firefox with super user privileges or as root.  This probably means that firefox is trying to write to disk where it does not have permission.  I wonder if there is a fix for this harmless yet annoying bug.

---

### Post by arnieboy on 2005-12-05
[QUOTE=Sajjen]That I have done, a few times. Didn't work. Perhaps it has something to do with the fact that I had not installed Firefox 1.0.7 before intalling 1.5?[/QUOTE]
nopes.. ther last time adblock screwed up my firefox, I had to ditch it and move on.
try the following:
```
sudo rm -rf /opt/firefox
sudo rm -f /usr/bin/firefox 
sudo rm -f /usr/bin/mozilla-firefox
```and run the script again.

---

### Post by Sajjen on 2005-12-05
[QUOTE=arnieboy]nopes.. ther last time adblock screwed up my firefox, I had to ditch it and move on.
try the following:
```
sudo rm -rf /opt/firefox
sudo rm -f /usr/bin/firefox 
sudo rm -f /usr/bin/mozilla-firefox
```and run the script again.[/QUOTE]

I think it works now. Thanks again, not just for the great script (that I managed to mess up by beeing clever), but also for the great support. Thanks!

---

### Post by fog on 2005-12-05
Works fine for me. Thanks :KS

---

### Post by foxy123 on 2005-12-05
[QUOTE=jstritar]Has anyone figured out what is causing the "Chrome Registration" errors when installing extensions? The error comes up but it seems to install fine. It'd be nice if I could figure this out b/c I'm an extension author and would like to know when it really does fail.[/QUOTE]
try to remove the two extensions shipped with FF1.5.

---

### Post by hpn on 2005-12-05
[QUOTE=erik-the-red]It seems like this "final" release is naught more than RC3.

Does that mean SCIM still poops out Firefox 1.5 "final"?[/QUOTE]

quite so. Firefox 1.5 has been crashing even with SCIM 1.4.2 (The HOWTO describes that FF crashes with SCIM 1.0.2)

---

### Post by newuser111 on 2005-12-05
this is a good guide, the new firefox (1.5) works faster than opera now

i dont see any harm in giving the /opt/firefox directory user permissions, afterall it is better than running firefox as root

---

### Post by jstritar on 2005-12-05
[QUOTE=hey560]I looked into the "chrome registration" error that pops up when installing/uninstalling extensions.  It seems that this error does not come up when you start up firefox with super user privileges or as root.  This probably means that firefox is trying to write to disk where it does not have permission.  I wonder if there is a fix for this harmless yet annoying bug.[/QUOTE]

I assume we can just find out where it is trying to write and give other users access to write to those files?

---

### Post by hkan on 2005-12-05
Hello everyone. Being a total newbie, forgive me if there is a too obvious solution to the error below...

I've followed the steps in the [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) howto, and trying to run the command firefox just gives me this:

```
hkan@hkansibook:~$ firefox
/opt/firefox/run-mozilla.sh: line 166: /opt/firefox/firefox-bin: cannot execute binary file
```

UPDATE: Of course it has to do with the Apple PowerPC architecture... well, I'll leave this here if anyone else drops by having the same troubles. ([Explained here.]("http://ubuntuforums.org/showthread.php?p=547841#post547841"))

---

### Post by martinbriscoe on 2005-12-06
Thanks for info at: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

I have been using XP for so long that I have become phobic about command line instructions, even after many hours playing with linux my command line attempts more often than not seem to end in failure.

Is there an easy point and shoot way of downloading and upgrading to 1.5?

Many thanks

Martin
Exeter, UK

---

### Post by The Warlock on 2005-12-06
[QUOTE=martinbriscoe]Thanks for info at: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

I have been using XP for so long that I have become phobic about command line instructions, even after many hours playing with linux my command line attempts more often than not seem to end in failure.

Is there an easy point and shoot way of downloading and upgrading to 1.5?

Many thanks

Martin
Exeter, UK[/QUOTE]

Most of the time with *nix operating systems, the command line is the easiest and quickest way to do things. Don't be scared, the command line here doesn't suck like XP's glorified version of DOS.

---

### Post by snooze on 2005-12-06
Thanks Fishfork :p .
This works for me.
Great How-To.
Worked first time.
Nvidia and Breezy.

Can't wait to see my friends drool;)

---

### Post by Cl1mh4224rd on 2005-12-06
[QUOTE=jstritar]Has anyone figured out what is causing the "Chrome Registration" errors when installing extensions? The error comes up but it seems to install fine. It'd be nice if I could figure this out b/c I'm an extension author and would like to know when it really does fail.[/QUOTE]
It happens because the ownership on the directories and files is "root", instead of the account installing the extension (yours).

```
sudo chown -R username:username /opt/firefox
```
Where "username" is *your* username.

This is mentioned in the Wiki article under "Updating", but it seems to be also necessary for error-free extension installation.

---

### Post by Rory on 2005-12-07
I've had two problems with the update from the wiki.

>  *
      To ensure that other programs use version 1.5 of firefox and not the old 1.07 version, go to Preferences -> Preferred Applications in the System menu. For the "Web Browser" tab, choose "Custom" and then enter the command:
       firefox %s
       

Where is System>Preferences>Preferred Applications>Web browser>Custom??  In Firefox?  In KDE Control Center?  If in Gnome, which I'm not running, what should I do?

> 
        Firefox 1.5 should now be installed and working properly. If for whatever reason you become unhappy with firefox 1.5 and would like to remove it, see the "Removing" section below for directions.

Updating

To get firefox's own update/autoupdate to work at all, you have three choices (read them all and choose one):

    *
      Change the /opt/firefox directory to have 'write' permissions & ownership set for the user instead of the root. To change ownership, after installation type:
       sudo chown -R username:username /opt/firefox
       

This command didn't work from me.  If my sign-in to KDE is "rory," should I typing this instead?:
 sudo chown -R rory:rory /opt/firefox

And how can I confirm if worked?

Thanks,
Rory

---

### Post by Dropknee on 2005-12-07
I use the script and work great, but no have flash now, I try to install via update with the same plugin finder and failed, then try it manual install but dont work, maybe Im doing something wrong , pls help

---

### Post by Dropknee on 2005-12-07
Ok I fixed, sorry for that, need to install via synaptic the flashplayer-mozilla, then install the plugin via plug-in finder in the same browser and work now.


Sorry for that :rolleyes:

---

### Post by Hobbsee on 2005-12-07
To your first question:  Kcontrol, kde components, components chooser, web browser.

sudo chown -R rory:rory /opt/firefox is definetly what you want to type in, if your username is rory.  You'll be able to see if it worked when it doesnt give you error messages back, but also by doing an "ls -la /opt/firefox" and seeing no "root" but "rory" instead

---

### Post by giloth on 2005-12-08
I got the following error as well. Mind you that I am in Gnome so I expected this, but I didn't expect it to get rid of my bookmarks and other stored information.

[QUOTE=TwiceOver]Well it worked I guess.  Ton of errors.  Not really sure what happened but my version now says 1.5.

Got a popup error "Firefox could not install this item due to an error in Chrome Registration.  Please contact the author about this problem".[/QUOTE]

---

### Post by cjm5229 on 2005-12-08
Arnieboy,
I just want to say Thank You. As a beginner to Linux and not the most tech savvy person in the world, I have been at a loss trying to set up Ubuntu. I found your Automatix and it solved a big share of my problems. This script did a teriffic job installing FF1.5 for me. OK, It didn't bring any ext. or themes, but most of them aren't yet supported that well in FF1.5 yet anyway. I have my bookmarks backed up too, so if I had lost them it is no big deal. I tried following the directions in the firefox install wiki earlier and all I got was a lot of errors and no Firefox. This took all or 1 min and it works perfectly. 
Thank You Again. Carl

---

### Post by mc_bizon on 2005-12-08
wont uninstallation of 1.0.7 remove directory .mozilla, which is now used by 1.5?
if i install a plugin through synaptic, will it work in 1.5?

---

### Post by beerorkid on 2005-12-08
so looking for a way to get 1.5 going, I searched.  Not supprisingly it is arnieboy who has the answer.

Two questions before I run the script

1. ```
./firefox_install
```should I su or sudo before this?  I am figuring not, just making sure

2. It appears that the epiphany problem has been eliminated, has it?
epiphany is the only browser besides IE (shudder) that will show dialog boxes on VMwares ESX management console correctly.  Needless to say that is very important to me for I am doing this on my work computer.

I will get 1.5 on my virtual XP machine and see if the viewing dialog boxes issue in ESX has been fixed.  Cuz if it has, I would have no reason to use epiphany.

---

### Post by mcduck on 2005-12-08
Thanks. This script worked nice, even mplayer and flash plugins are fine, but Java doesn't work any more. I tried copying my old firefox profile to 1.5, but it didn't help. I also tried to reinstall Java but that didn't help either.

Now, would anybody know what to do to get Java working again?

---

### Post by beerorkid on 2005-12-08
answer my own questions thanks to having a secondary test laptop lying around :p 

1. nope just run it as a normal user

2. the epiphany problem has been fixed.

and drumroll...........
firefox 1.5 has solved my issue with dialog boxes displaying incorrectly.
Once again big shoutout to Arnie and co who made this possible.

And the jumpy mplayer issue that has drove me completely nuts for quite some time seems to have magicaly dissapeared now that I am on 1.5

mcduck:
Mine did not have issues with java, I did loose my bookmarks (lucky for me I back them up to my web server religiously)  Might I suggest automatix and reinstalling java throught it.
[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

---

### Post by beerorkid on 2005-12-08
FYI:  Middle mouse tab closing seems to get a little borked.
I found a post by jdong that fixed it.> go to about:config, turn off middleclick.contentloadURL and middle click works again

---

### Post by arnieboy on 2005-12-08
a quick update: none of the bookmarks get deleted by the firefox script.
try this simple command from terminal to get them back (after closing all firefox windows):
```
cp -f ~/.mozilla_backup/firefox/*.default/bookmarks.html ~/.mozilla/firefox/*.default/
```
If this doesnt work, then u probably stored your bookmarks under a different profile(other than the default) all of which u will get in **~/.mozilla_backup/firefox/<profile_name>/bookmarks.html**
copy this html file into **~/.mozilla/firefox/*.default/**
and u will find all your bookmarks restored for the default profile.
Hope this helps,
Arnie

---

### Post by giloth on 2005-12-08
Thanks arnieboy! Another thing I noticed is that my flash plugin was reset and had to redownload it. I have tested other plugins such as this, but I'm guessing my Java plugin for Firefox has done the same thing.

No matter though, they are easy enough to reinstall. ;)

---

### Post by arnieboy on 2005-12-08
the script copies the plugins (and symlinks for the same) from the following locations:
**/usr/lib/mozilla/plugins/**
and
**/usr/lib/mozilla-firefox/plugins/**
where most plugins get installed by default for firefox which comes preinstalled with ubuntu.
If u have installed your plugins elsewhere, u need to copy them manually to **/opt/firefox/plugins/** (of course as sudo or root)

---

### Post by randcv on 2005-12-08
Oh No! I tried installing firefox 1.5 on my own, and now I seem to have screwed something up. I decided to start all over, and just follow the instructions on the wiki, but when I get to the instruction: 
```
 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
```
I get the error
```

rand@ubuntu:~$ sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
dpkg-divert: Cannot divert directories

You need --help.

```

Anyone have any ideas? I'm a total linux newbie, but I'd really like to get this running...

Thanks,
Rand

---

### Post by aum11 on 2005-12-08
Thanks Arnie for another wonderful script...I have been waiting patiently for this!

Also much thanks for Automatix.  It has been a Godsend.

---

### Post by Burgresso on 2005-12-08
Yea, your scripts great. Thanks.

---

### Post by mcduck on 2005-12-09
[QUOTE=arnieboy]the script copies the plugins (and symlinks for the same) from the following locations:
**/usr/lib/mozilla/plugins/**
and
**/usr/lib/mozilla-firefox/plugins/**
where most plugins get installed by default for firefox which comes preinstalled with ubuntu.
If u have installed your plugins elsewhere, u need to copy them manually to **/opt/firefox/plugins/** (of course as sudo or root)[/QUOTE]
There actually was a 'libjavaplugin.so' in /opt/firefox/plugins/, but I replaced it with a symbolic link to java plugin from /usr/lib/mozilla/plugins/. And now java works. Thanks Arnieboy, You're doing great job.

By the way, the script left a 'firefox' directory in my home, owned by root. I suppose that it's not needed for anything and I can just remove it?

---

### Post by ndhskp on 2005-12-09
First it does work for me.  But the check for updates menu entry is greyed out.  Also when I try to click a URL in Thunderbird it does not launch Firefox.  I had some problems with the script also.  You can see the terminal output below has a problem.

Adding `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
/opt/firefox/firefox-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Fixed by using Synaptic to install libstdc5

However this did confuse me so I ran the script a second time and it seemed to work.  The terminal output is below:

mv: cannot stat `/home/username/.mozilla': No such file or directory
Leaving `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
Leaving `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
ln: `/usr/bin/firefox': File exists
ln: `/usr/bin/mozilla-firefox': File exists

But this seemed to create a Firefox folder in /home/username/.  Which is weird and all.  Should mention that when the Firefox window popped up I had to shut it down manually using file menu.  This promptly ended the script with no migration of profile componets.  Of course I also got the chrome reg problem which seems to be related to root access?  I did get through all that and am now running Firefox at 100MPH compred to Ubuntu's version that is a turd.

Can anybody tell me how to safely get auto update to work without risking security.  And get URL calls in the system to properly start Firefox 1.5.

Thank you arnieboy for the script.  I was too lazy to follow the wiki and the security problem bothered me.  I sure as hell don't want scripts and other crap to have access to opt.

---

### Post by fishfork on 2005-12-09
randcv - what output do you get if you type:
```

ls -l /usr/bin/firefox*

```

---

### Post by ndhskp on 2005-12-09
arnieboy can you update your Firefox post to let people know that if URL calls in their system is not working and they have mozilla-firefox set up as the command in System/Preferences/Prefered Applications that they should try setting the command to simply firefox.

mozilla-firefox %s to: firefox %s

However this seems to revert to the select box as opposed to custom with the flag %s and all.  This should fix URL calls in the system and launch Firefox 1.5.  Also I forgot to mention in my earlier post I had trouble with Java as well so I simply copied the symlink manually so no real problem there.  Againg thanks for the script.  Sorry about the unhappy smiley face the first time around.  I was just using it to express the minor script annoyances.  Here's a happy one this time.

---

### Post by SilentCacophony on 2005-12-09
I also had to install **libstdc++5** to get the firefox to work afterwards. I'm running from the original full release of Breezy, and I had libstdc++6 installed, if it makes a difference.

I also had to make a symlink to the java package that I previously installed.

Otherwise, no problems so far, and it seems quite nice. Thanks for the script. :)

---

### Post by zasf on 2005-12-09
Same error as TwiceOver, but that's ok

[QUOTE=arnieboy]what happened was that firefox 1.0.7 was removed, ur settings backed up, version 1.5 downloaded and installed, plugins copied and some of the old settings copied back.[/QUOTE]

I lost my old settings, not that big problem.. but firefox is (i believe) now installed in my home dir, is that correct?? I'm the only user on this laptop, but what if other users need to use firefox??

```
matteo@zubuntu:~$ ls firefox
browserconfig.properties  libnss3.so          libxpistub.so
chrome                    libnssckbi.so       mozilla-xremote-client
components                libplc4.so          plugins
defaults                  libplds4.so         readme.txt
extensions                libsmime3.so        removed-files
firefox                   libsoftokn3.chk     res
firefox-bin               libsoftokn3.so      run-mozilla.sh
greprefs                  libssl3.so          searchplugins
icons                     libxpcom_compat.so  updater
libmozjs.so               libxpcom_core.so    updater.ini
libnspr4.so               libxpcom.so         xpicleanup

```

should i reinstall it?

---

### Post by arnieboy on 2005-12-09
what error?
The post of mine that u have quoted is old and does not apply any more. the script that u have used does not remove firefox 1.0.7. it merely makes 1.5 the default.

---

### Post by lynng on 2005-12-09
I'm getting the following error when trying to follow the bulleted steps at the beginning of the wiki entry:
```
 sudo apt-get install libstdc++5 Reading package lists... Done
Building dependency tree... Done
libstdc++5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libxml-sax-perl (0.12-5) ...
Can't locate object method "save_parsers_debian" via package "XML::SAX" at /usr/bin/update-perl-sax-parsers line 90.
dpkg: error processing libxml-sax-perl (--configure):
 subprocess post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of libxml-libxml-perl:
 libxml-libxml-perl depends on libxml-sax-perl (>= 0.11); however:
  Package libxml-sax-perl is not configured yet.
dpkg: error processing libxml-libxml-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxml-simple-perl:
 libxml-simple-perl depends on libxml-sax-perl; however:
  Package libxml-sax-perl is not configured yet.
 libxml-simple-perl depends on libxml-libxml-perl | libxml-sax-expat-perl; however:
  Package libxml-libxml-perl is not configured yet.
  Package libxml-sax-expat-perl is not installed.
dpkg: error processing libxml-simple-perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxml-sax-perl
 libxml-libxml-perl
 libxml-simple-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Earlier I followed a howto on installing checkgmail, which had some commands related to perl and xml.  Not sure if that could be part of the problem.  Anyone know how to go on from here?  I don't want to continue with the rest of the instructions for installing FF 1.5, for fear of borking firefox completely.

---

### Post by nrayever on 2005-12-09
it's not working for me!! pango problems. if someone help with this will be appreciated!!

---

### Post by daedalusman on 2005-12-09
Well, I'm having the problem where firefox would load extrenal links aka links from evolution and other programs. I have the command firefox set as my preferred application but still having this problem. Can someone shed some light on this for me, thanks.

---

### Post by ceti on 2005-12-10
Thanks, arnieboy.
Unfortunately, it didn't import anything. I lost Java & firefox plugins and that annoying alert message about Chrome shows up everytime I open Firefox.
Anyway, it's great, thank you.

---

### Post by zasf on 2005-12-10
[QUOTE=arnieboy]what error?
The post of mine that u have quoted is old and does not apply any more. [/QUOTE]

this one "Firefox could not install this item due to an error in Chrome Registration. Please contact the author about this problem".

[QUOTE=arnieboy]the script that u have used does not remove firefox 1.0.7. it merely makes 1.5 the default.[/QUOTE]

what i wanted to know is if firefox 1.5 was installed in my home dir. I figured out not, since i deleted ~/firefox/ and it still works. I also removed Firefox 1.0.7 with apt-get remove.

Great script, thanks

---

### Post by arnieboy on 2005-12-10
[QUOTE=ceti]Thanks, arnieboy.
Unfortunately, it didn't import anything. I lost Java & firefox plugins and that annoying alert message about Chrome shows up everytime I open Firefox.
Anyway, it's great, thank you.[/QUOTE]
the chrome registration will show up only once after u try to install or remove an extension (not otherwise).
u can manually import your cookies and bookmarks from the backup folder ($HOME/.mozilla_backup). refer to the first post for details.
firefox gets installed in /opt/firefox

u lost your plugins because u had them installed in a non-standard location. not a problem really. find out where u had installed them and move them to **/opt/firefox/plugins/**

The standard locations are **/usr/lib/mozilla-firefox/plugins**
and **/usr/lib/mozilla/plugins**

---

### Post by arnieboy on 2005-12-10
[QUOTE=zasf]this one "Firefox could not install this item due to an error in Chrome Registration. Please contact the author about this problem".



what i wanted to know is if firefox 1.5 was installed in my home dir. I figured out not, since i deleted ~/firefox/ and it still works. I also removed Firefox 1.0.7 with apt-get remove.

Great script, thanks[/QUOTE]
u shd not have removed firefox 1.0.7 because lots of packages in ubuntu are dependent on that. (like mozilla-mplayer, yelp, add remove applications, epiphany and they also got uninstalled along with firefox 1.0.7)

---

### Post by olieviya on 2005-12-10
How do you get to write in the folrders or your hardisk? I keep trying to paste stuff and it tells me I heven't the permission.

And I have no idea how to open the "console", anybody help?

---

### Post by arnieboy on 2005-12-10
[QUOTE=olieviya]How do you get to write in the folrders or your hardisk? I keep trying to paste stuff and it tells me I heven't the permission.

And I have no idea how to open the "console", anybody help?[/QUOTE]
Applications -->Accessories --> Terminal

what are u trying to do here? which folders are u trying to write to?

---

### Post by autonomy on 2005-12-10
Thanks

---

### Post by neymac on 2005-12-10
[QUOTE=arnieboy]
download it first and **extract it in your home folder** and then run it from gnome-terminal as follows:
```
./firefox_install
```
[/B][/QUOTE]

I did extract to /home  (my mistake) instead of /home/(My name), and run the script.
Then I use sudo to run the script, because at the first time it didn't run well.

After a while the Firefox 1.5 window opened with the google home page.

Then I closed the Firefox, and when I tried open again after a while, it did not open.

I tried reinstall. And the same: the Firefox 1.5 opened. I close it and try again and nothing.

I have put "#" in the wget line of the script to reinstall faster (not wait till download cause I had already the file).
The same. Then I commented "#" others line of the script until I have only the line: exec firefox.
I made a launcher with "run from terminal" with the the command "sudo ./firefox_install" and it works fine despite the terminal window opened for a while.

I changed the original launcher command from "firefox %u" to "sudo firefox %u" with run from terminal ticked. It worked fine. I have Firefox 1.5 and Epiphany as well.

But: How can I get free of this "sudo" and "run from terminal" of my launchers?
Do you have any clue?

---

### Post by arnieboy on 2005-12-10
[QUOTE=neymac]I did extract to /home instead of /home/(My name), and run the script.
Then I use sudo to run the script, because at the first time it didn't run well.[/QUOTE]
This is where u did things wrong. u shd not have used sudo to run the script (that has messed up your firefox home folder permissions).
U shd have pasted the errors that u were getting while trying to run the script as normal user over here..
sudo isnt a solution to everything. Please try and understand where u need it and where u dont.

---

### Post by neymac on 2005-12-10
[QUOTE=arnieboy]This is where u did things wrong. u shd not have used sudo to run the script (that has messed up your firefox home folder permissions).
U shd have pasted the errors that u were getting while trying to run the script as normal user over here..
sudo isnt a solution to everything. Please try and understand where u need it and where u dont.[/QUOTE]

 Is there any way back?

---

### Post by arnieboy on 2005-12-10
try the following:
1) delete the launcher (which runs firefox as sudo in terminal) that u have made
2) open up terminal and do the following:
```
sudo rm -rf ~/.mozilla
```
now run firefox from the gnome applications menu just like u used to do before. **DON'T run firefox as sudo**

---

### Post by ceti on 2005-12-10
[quote=arnieboy]the chrome registration will show up only once after u try to install or remove an extension (not otherwise).
u can manually import your cookies and bookmarks from the backup folder ($HOME/.mozilla_backup). refer to the first post for details.
firefox gets installed in /opt/firefox

u lost your plugins because u had them installed in a non-standard location. not a problem really. find out where u had installed them and move them to **/opt/firefox/plugins/**

The standard locations are **/usr/lib/mozilla-firefox/plugins**
and **/usr/lib/mozilla/plugins**[/quote]

Arnieboy, you're right. Ev'rything's fine now. No more annoying *Chrome alerts*, Java ok, plugins ok.
Great HowTo, thank you and thanks for **Automatix**, too.

---

### Post by neymac on 2005-12-10
[QUOTE=arnieboy]try the following:
1) delete the launcher (which runs firefox as sudo in terminal) that u have made
2) open up terminal and do the following:
```
sudo rm -rf ~/.mozilla
```
now run firefox from the gnome applications menu just like u used to do before. **DON'T run firefox as sudo**[/QUOTE]

 It worked fine. Thank you. You did solve it very fast indeed.

---

### Post by mike.holland on 2005-12-10
First off, I really want to thank you for your wiki instructions.  It has been a great resource.  The only problem I ran into was the fact that McDonalds somehow managed to force Google to spider "%s" as [www.mcdonalds.com](www.mcdonalds.com).  No big deal, I just removed it from my launchers.  I was just curious as to the significance of adding "%s" to the launcher command.  The "I'm feeling lucky" function immediately takes me to Mickey-Ds instead of my homepage.:confused:

---

### Post by BinaryDigit on 2005-12-11
This script was great :D Worked like a charm...did the workaround to get rid of the error.
Thank you!!!!

---

### Post by zbowling on 2005-12-11
To bad I'm running x86_64... I had to build firefox but that wiki link gave me anough information to use it a lot nicer.

---

### Post by N8K99 on 2005-12-11
I  had to install libstdc5 in order for the Firefox1.5 to work but that was my only hang up. I found my answers in this thread. Thanks alot guys!!:p

---

### Post by siorai on 2005-12-11
I have two problems: 

I can't get the Flash plug-in to install. I've ran through Automatix to install Flash, tried installing flashplayer-mozilla through Synaptic, but when I go to a site that has Flash on it and try to install the plug-in, it will start to download it, but it always stalls about half way through.

The other problem is that I can't open Firefox with a keyboard shortcut. Not nearly as much of an issue as no Flash though.


edit: Ok, got Flash working by manually downloading it from Macromedia and installing it that way. Still can't use the keyboard shortcut though.

---

### Post by macheadPDX on 2005-12-11
Hi Arnieboy!

Thanks for the how-to! It works like charm!:wink:

---

### Post by ceti on 2005-12-11
Just one question: can I safely remove the Firefox folder created in my /home?

Thanks

---

### Post by neymac on 2005-12-11
I've tryed install Java pluggin with Automatix into FF 1.5. Although there wasn't any error msg, when I go into Sun's test page, it says that Java Pluggin is not installed, and there is no option to automatic install (only Manual installation  is available). 
I've installed the full Java as well using Automatix.
The Epiphany at the same Sun's page ([http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp) ) shows that I have Java working.
Do you have any tip how to link Java and FF 1.5 or any Automatix setting to Java pluggin work in FF 1.5?

---

### Post by bierpullen on 2005-12-11
Thanks

This is great !!!
Works !!!! \\:D/ 

------------------------------------------


Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.
[http://www.antarctica-rbak.nl/ubuntu](http://www.antarctica-rbak.nl/ubuntu)

---

### Post by arnieboy on 2005-12-11
[QUOTE=neymac]I've tryed install Java pluggin with Automatix into FF 1.5. Although there wasn't any error msg, when I go into Sun's test page, it says that Java Pluggin is not installed, and there is no option to automatic install (only Manual installation  is available). 
I've installed the full Java as well using Automatix.
The Epiphany at the same Sun's page ([http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp) ) shows that I have Java working.
Do you have any tip how to link Java and FF 1.5 or any Automatix setting to Java pluggin work in FF 1.5?[/QUOTE]
if u have installed java with automatix, herez how to make it work with firefox 1.5:
close all firefox windows and open terminal and do:
```
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins
```
now open firefox and in the site bar type: 
```
about:plugins
```
and u will see java plugin listed

---

### Post by arnieboy on 2005-12-11
[QUOTE=ceti]Just one question: can I safely remove the Firefox folder created in my /home?

Thanks[/QUOTE]
yes indeed. delete the folder.

---

### Post by arnieboy on 2005-12-11
[QUOTE=siorai]I have two problems: 

I can't get the Flash plug-in to install. I've ran through Automatix to install Flash, tried installing flashplayer-mozilla through Synaptic, but when I go to a site that has Flash on it and try to install the plug-in, it will start to download it, but it always stalls about half way through.

The other problem is that I can't open Firefox with a keyboard shortcut. Not nearly as much of an issue as no Flash though.


edit: Ok, got Flash working by manually downloading it from Macromedia and installing it that way. Still can't use the keyboard shortcut though.[/QUOTE]
I dont understand what flash has got to do with opening firefox with a shortcut.
try going to **system-->preferences-->keyboard shortcuts**
and look for the one which says "launch web browser".
set that to a unique keyboard combination or single key.
also make sure that "web browser" in **system-->preferences-->preferred applications** is set to "firefox"

if u have installed flash for firefox with automatix, herez how to install the plugins for FF 1.5:

```
sudo cp /usr/lib/mozilla-firefox/plugins/libflashplayer.so /opt/firefox/plugins
sudo cp /usr/lib/mozilla-firefox/plugins/flashplayer.xpt /opt/firefox/components
sudo cp /usr/lib/mozilla-firefox/components/flashplayer.xpt /opt/firefox/components
```

whenever the destination file exists, u will get an error and thats fine cuz that tells u that the existing file doesnt need to be overwritten.

---

### Post by neymac on 2005-12-11
[QUOTE=arnieboy]if u have installed java with automatix, herez how to make it work with firefox 1.5:
close all firefox windows and open terminal and do:
```
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins
```
now open firefox and in the site bar type: 
```
about:plugins
```
and u will see java plugin listed[/QUOTE]

Thanks once again. It worked fine. Now I have Java in Firefox 1.5.

---

### Post by siorai on 2005-12-11
[QUOTE=arnieboy]I dont understand what flash has got to do with opening firefox with a shortcut.
try going to **system-->preferences-->keyboard shortcuts**
and look for the one which says "launch web browser".
set that to a unique keyboard combination or single key.
also make sure that "web browser" in **system-->preferences-->preferred applications** is set to "firefox"[/QUOTE]

It doesn't, hence why I said I had two problems. Changing the preferred application did the trick though. Thanks. :D

---

### Post by randcv on 2005-12-11
[QUOTE=fishfork]randcv - what output do you get if you type:
```

ls -l /usr/bin/firefox*

```[/QUOTE]

rand@ubuntu:~$ ls -l /usr/bin/firefox*
lrwxrwxrwx  1 root root 29 2005-12-08 14:26 /usr/bin/firefox -> /usr/lib/mozilla -firefox-1.5/
lrwxrwxrwx  1 root root 30 2005-08-20 03:17 /usr/bin/firefox-1.06 -> ../lib/mozi lla-firefox/firefox
lrwxrwxrwx  1 root root 30 2005-12-08 14:44 /usr/bin/firefox.ubuntu -> ../lib/mo zilla-firefox/firefox

Thanks!
Rand

---

### Post by tedddee on 2005-12-11
Trying to run this script on a brand new breezy install

/opt/firefox/firefox-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

edit: ok i installed libstdc++ 5 through synaptic, 6 was the default installed version

can i remove this locked "firefox" folder sitting in home?

---

### Post by arnieboy on 2005-12-11
[QUOTE=tedddee]Trying to run this script on a brand new breezy install

/opt/firefox/firefox-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

edit: ok i installed libstdc++ 5 through synaptic, 6 was the default installed version

can i remove this locked "firefox" folder sitting in home?[/QUOTE]
yes delete it.

---

### Post by arnieboy on 2005-12-11
**Updated the script to install libstdc++5 automatically.**

---

### Post by syntaxerror64 on 2005-12-11
Hello, thanks very much for this script it worked great on my new Ubuntu install.

---

### Post by nauseaboy on 2005-12-11
I just used it 10 minutes ago and it didn't really work, but I just copied everything in the /.mozilla_backup/*.default/ to /.mozilla/firefox/*.default/ and it works fine so, thanks anyway. It was a no hassle install for the most part.

---

### Post by arnieboy on 2005-12-11
[QUOTE=nauseaboy]I just used it 10 minutes ago and it didn't really work, but I just copied everything in the /.mozilla_backup/*.default/ to /.mozilla/firefox/*.default/ and it works fine so, thanks anyway. It was a no hassle install for the most part.[/QUOTE]

It surely did work, except that your user settings were not kept back which u copied manually from ur backed up user directory.

it wasnt a good idea to copy "everything" from your backup user directory. The usual stuff u wud be looking to copy are bookmarks, cookies etc.

---

### Post by mishranurag on 2005-12-12
The script worked for me and firefox got installed too, but it is in a directory with access to root only, that means only root can use the firefox 1.5??
I installed firefox without sudo. Please help, I am using another browser firefox is not working :((
Anurag



[QUOTE=arnieboy]It surely did work, except that your user settings were not kept back which u copied manually from ur backed up user directory.

it wasnt a good idea to copy "everything" from your backup user directory. The usual stuff u wud be looking to copy are bookmarks, cookies etc.[/QUOTE]

---

### Post by arnieboy on 2005-12-12
99% of what ubuntu installs are in directories in which only root has write permissions. please try to understand how linux works.
did u try running firefox from your applications-->internet menu?

---

### Post by mishranurag on 2005-12-12
I tried running it from Applications-->Internet Menu and it didn't work!
It works from the home/firefox directory, if I get in as root!
Anurag

[QUOTE=arnieboy]99% of what ubuntu installs are in directories in which only root has write permissions. please try to understand how linux works.
did u try running firefox from your applications-->internet menu?[/QUOTE]

---

### Post by arnieboy on 2005-12-12
[QUOTE=mishranurag]I tried running it from Applications-->Internet Menu and it didn't work!
It works from the home/firefox directory, if I get in as root!
Anurag[/QUOTE]
did u run the script as sudo? like
sudo ./firefox_install

---

### Post by mishranurag on 2005-12-12
Nope!
I tried reinstalling it a couple of times. It didn't work!
Anurag

[QUOTE=arnieboy]did u run the script as sudo? like
sudo ./firefox_install[/QUOTE]

---

### Post by mishranurag on 2005-12-12
Here is the log

anmishra@anmishra:~$  ./firefox_install
Reading package lists... Done
Building dependency tree... Done
libstdc++5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
firefox-bin: no process killed
firefox: no process killed
--01:12:23--  [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686/en-US/firefox-1.5.tar.gz](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686/en-US/firefox-1.5.tar.gz)
           => `firefox-1.5.tar.gz.2'
Resolving ftp.mozilla.org... 64.50.236.52, 64.50.238.52, 216.165.129.134, ...
Connecting to ftp.mozilla.org|64.50.236.52|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,444,956 (8.1M) [application/x-gzip]

100%[====================================>] 8,444,956    170.91K/s    ETA 00:00

01:13:12 (170.55 KB/s) - `firefox-1.5.tar.gz.2' saved [8444956/8444956]

mv: cannot overwrite directory `/home/anmishra/.mozilla_backup/.mozilla'
Leaving `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
Leaving `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
ln: `/usr/bin/firefox': File exists
ln: `/usr/bin/mozilla-firefox': File exists
anmishra@anmishra:~$

[QUOTE=mishranurag]Nope!
I tried reinstalling it a couple of times. It didn't work!
Anurag[/QUOTE]

---

### Post by arnieboy on 2005-12-12
this is a truly unique case (the first of its kind).. lol
alright try this.. open up terminal and do the following:
```
firefox
```

---

### Post by mishranurag on 2005-12-12
Nothing!
Sudo firefox, does open firefox though :)
Anurag


[QUOTE=arnieboy]this is a truly unique case (the first of its kind).. lol
alright try this.. open up terminal and do the following:
```
firefox
```[/QUOTE]

---

### Post by arnieboy on 2005-12-12
[QUOTE=mishranurag]Nothing!
Sudo firefox, does open firefox though :)
Anurag[/QUOTE]
alright buddy..  do this as a last ditch attempt afterclosing all firefox windows
```
sudo rm -rf ~/.mozilla
```
and try running firefox from the menu.

---

### Post by mishranurag on 2005-12-12
Yoooohoo
It did work.
Thanks a lot buddy.
Could you explain what could have caused the problem??
Anurag



[QUOTE=arnieboy]alright buddy..  do this as a last ditch attempt afterclosing all firefox windows
```
sudo rm -rf ~/.mozilla
```
and try running firefox from the menu.[/QUOTE]

---

### Post by arnieboy on 2005-12-12
[QUOTE=mishranurag]Yoooohoo
It did work.
Thanks a lot buddy.
Could you explain what could have caused the problem??
Anurag[/QUOTE]
the problem was that u ran the script initially as sudo (though you fail to recollect that) which overrode your mozilla user directory permissions and set them as root's.
u can now safely delete the firefox folder in your home folder.
'nite :)

---

### Post by mishranurag on 2005-12-12
Thanks Again :)
Good Night!
I would be really happy on the day when I will be able to listen music from [www.raaga.com/channels/hindi]("http://www.raaga.com/channels/hindi") on my comp.
Anurag


[quote=arnieboy]the problem was that u ran the script initially as sudo (though you fail to recollect that) which overrode your mozilla user directory permissions and set them as root's.
u can now safely delete the firefox folder in your home folder.
'nite :)[/quote]

---

### Post by syntaxerror64 on 2005-12-12
A quick question...   this script worked real well, but I am noticing now that when I click a web page link in say X-Chat that it is not opening, even if the browser is already open.  I have to cut & paste the link.  Any idea what would have made that happen?

---

### Post by arnieboy on 2005-12-12
[QUOTE=syntaxerror64]A quick question...   this script worked real well, but I am noticing now that when I click a web page link in say X-Chat that it is not opening, even if the browser is already open.  I have to cut & paste the link.  Any idea what would have made that happen?[/QUOTE]
depends on what the default browser in x-chat is set to (might be konqueror for all u know). as such for gnome apps, u need to do the following to make links open by default in firefox:
go to system -->preferences-->preferred applications
and set your default web browser as "firefox" (minus the quotes of course)

---

### Post by nauseaboy on 2005-12-12
Why is it a bad Idea to copy everything? Everything is working A-OK at the moment.

---

### Post by arnieboy on 2005-12-12
[QUOTE=nauseaboy]Why is it a bad Idea to copy everything? Everything is working A-OK at the moment.[/QUOTE]
because some of the extensions and themes might cause problems because of inter version compatibility.. but the operative word here is "might". good to know that everything's working great for u :)

---

### Post by syntaxerror64 on 2005-12-12
[QUOTE=arnieboy]depends on what the default browser in x-chat is set to (might be konqueror for all u know). as such for gnome apps, u need to do the following to make links open by default in firefox:
go to system -->preferences-->preferred applications
and set your default web browser as "firefox" (minus the quotes of course)[/QUOTE]

Thanks Arnie, I changed the "system -->preferences-->preferred applications" and that seems to have fixed it right up.

---

### Post by arnieboy on 2005-12-12
[QUOTE=syntaxerror64]Thanks Arnie, I changed the "system -->preferences-->preferred applications" and that seems to have fixed it right up.[/QUOTE]
awesome :)

---

### Post by nauseaboy on 2005-12-12
[QUOTE=arnieboy]because some of the extensions and themes might cause problems because of inter version compatibility.. but the operative word here is "might". good to know that everything's working great for u :)[/QUOTE]


Ah that explains it. I wasn't running any extensions or themes to begin with.

---

### Post by hl2u on 2005-12-12
So...my first noob question :-)  :

-breezy on amd 64 ;
-downloaded the script and runned it ;
-got the "mozilla quality feedback agent " prompt;
- firefox is not opening;

```

me@mymachine:~$ ./firefox_install
Password:
Citire liste de pachete... Gata
Se construie&#351;te arborele de dependen&#355;&#259;... Gata
libstdc++5 are deja cea mai nou&#259; versiune.
0 &#238;nnoite, 0 nou instalate, 0 de &#351;ters &#351;i 2 ne&#238;nnoite.
W: Nu pot determina starea listei surse de pachete [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)W: Nu pot determina starea listei surse de pachete [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Nu pot determina starea listei surse de pachete [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: A&#355;i putea vrea s&#259; porni&#355;i 'apt-get update' pentru a corecta aceste probleme.
firefox-bin: nici un proces nu a fost terminat
firefox: nici un proces nu a fost terminat
--11:50:13--  [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686/en-US/firefox-1.5.tar.gz](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686/en-US/firefox-1.5.tar.gz)
           => `firefox-1.5.tar.gz.1'
Rezolvare ftp.mozilla.org... 64.50.236.52, 64.50.238.52, 216.165.129.134, ...
Connecting to ftp.mozilla.org|64.50.236.52|:80... conectat.
Cerere HTTP trimis&#259;, se a&#351;teapt&#259; r&#259;spuns... 200 OK
Dimensiune: 8,444,956 (8.1M) [application/x-gzip]

100%[====================================>] 8,444,956    192.73K/s    ETA 00:00

11:50:57 (189.81 KB/s) - `firefox-1.5.tar.gz.1' saved [8444956/8444956]

Leaving `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
Leaving `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
ln: `/usr/bin/firefox': File exists
ln: `/usr/bin/mozilla-firefox': File exists

(firefox-bin:9502): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:9502): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:9502): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libindustrial.so: cannot open shared object file: No such file or directory

(firefox-bin:9502): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libindustrial.so: cannot open shared object file: No such file or directory

(firefox-bin:9502): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libindustrial.so: cannot open shared object file: No such file or directory

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:9502): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libindustrial.so: cannot open shared object file: No such file or directory

(firefox-bin:9502): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libindustrial.so: cannot open shared object file: No such file or directory

(firefox-bin:9502): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libindustrial.so: cannot open shared object file: No such file or directory

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:9502): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libindustrial.so: cannot open shared object file: No such file or directory

(firefox-bin:9502): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libindustrial.so: cannot open shared object file: No such file or directory

(firefox-bin:9502): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libindustrial.so: cannot open shared object file: No such file or directory

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:9502): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9502): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9502): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9502): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9502): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9502): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9502): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9502): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9502): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9502): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9502): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9502): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9502): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:9502): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
Warning: locale not supported by Xlib, locale set to C
Warning: X locale modifiers not supported, using default
/opt/firefox/run-mozilla.sh: line 131:  9502 Aborted                 "$prog" ${1+"$@"}
me@mymachine:~$ 


```

How am I going to fix what i've  broke ? Thank's in advance !

---

### Post by arnieboy on 2005-12-12
seems to be some pango package missing.. possibly libpango or some other internationalized package? Its a locale specific error. Somebody with more knowledge on locale specific errors will be able to help.
for the time being try to change to the **human** theme and give firefox a shot and post the errors again.

---

### Post by Vantskruv on 2005-12-12
From [https://wiki.ubuntu.com/FirefoxNewVersion:](https://wiki.ubuntu.com/FirefoxNewVersion:) > Notes You may get an error dialog (twice) each time Firefox starts up saying Firefox could not install this item because of a failure in Chrome Registration. Please contact the author about this problem.. This is due to [WWW] this bug. To work round do the following:- sudo touch /opt/firefox/extensions/talkback@mozilla.org/chrome.manifest The only thing I did do was to edit the link for firefox in the menu and set the working folder to the folder where firefox is installed, in my case "/opt/firefox".

(I'm using Kubuntu, but I guess you can do almost the same thing in Ubuntu)

---

### Post by MotoWebmaster on 2005-12-13
arnieboy - You The Man!

I just ran your firefox 1.5 install script. Went as you stated, and I had the bookmarks restore command ready to go at the end.

Noticed your other script, haven't tried it yet but did catch some of the negative comments from others. I can tell you from years of experience, taking a leadership role and donating your time/talents ultimately means that you'll run into situations that will challenge your resolve. In some ways, life is too short to be burden by those who try to take advantage - but on the other hand, I find that pushing forward can help you be creative in ways not previously imagined.

I appreciate all you do!

---

### Post by hl2u on 2005-12-13
**arnieboy**, thanks again for your help.
changed to "human" theme and :

```


me@mymachine:~$ ./firefox_install
Password:
E: Nu pot determina blocajul /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
firefox-bin: nici un proces nu a fost terminat
firefox: nici un proces nu a fost terminat
--21:01:22--  [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686/en-US/firefox-1.5.tar.gz](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686/en-US/firefox-1.5.tar.gz)
           => `firefox-1.5.tar.gz.3'
Rezolvare ftp.mozilla.org... 64.50.238.52, 64.50.236.52, 216.165.129.134, ...
Connecting to ftp.mozilla.org|64.50.238.52|:80... conectat.
Cerere HTTP trimis&#259;, se a&#351;teapt&#259; r&#259;spuns... 200 OK
Dimensiune: 8,444,956 (8.1M) [application/x-gzip]

100%[====================================>] 8,444,956    192.67K/s    ETA 00:00

21:02:06 (189.51 KB/s) - `firefox-1.5.tar.gz.3' saved [8444956/8444956]

mv: cannot overwrite directory `/home/mama/.mozilla_backup/.mozilla'
Leaving `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
Leaving `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
ln: `/usr/bin/firefox': File exists
ln: `/usr/bin/mozilla-firefox': File exists

(firefox-bin:31894): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:31894): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No such file or directory

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:31894): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:31894): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:31894): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:31894): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:31894): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:31894): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:31894): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:31894): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:31894): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:31894): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:31894): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:31894): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:31894): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:31894): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/opt/firefox/run-mozilla.sh: line 131: 31894 Aborted                 "$prog" ${1+"$@"}
me@mymachine:~$ Warning: locale not supported by Xlib, locale set to C
Warning: X locale modifiers not supported, using default


```

---

### Post by kscelt on 2005-12-13
Everything worked fine except for needing to fix flash with a re-install, and Java, which has me stumped.

The problem, I believe, is that an incorrect file for the plugin is in the opt/firefox/plugins directory. There are two java related files there: libjavaplugin.so and libjavaplugin_oji.so, both of which are owned by root.

The java version I am currently using is:

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

When I type "about:plugins" in the browser, it states that the java plugin is:

Java(TM) Plug-in Blackdown-1.4.2-02

There is a libjavaplugin_oji.so file in my /usr/local/jre1.5.0_05/plugin/i386/ns7 directory, which is owned by root.

How do I fix this?

---

### Post by arnieboy on 2005-12-13
do the following and u shd be fine:
```
sudo rm -f /opt/firefox/plugins/libjavaplugin.so
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7libjavaplugin_oji.so /opt/firefox/plugins/
```

---

### Post by kscelt on 2005-12-13
Thanks much - it worked!

---

### Post by arnieboy on 2005-12-13
hl2u: this is what u need to do I think. Open synaptic and search for "pango" under "search for package under names" and install all the packages listed. and then try running firefox (not the installation) again from terminal.

---

### Post by kscelt on 2005-12-13
Rats, no it did not.  Still says I am using the blackdown plugin.

Now in the opt/firefox/plugins directory, I have two files related to java:

libjavaplugin_oji.so and ns7libjavaplugin_oji.so (which under properties is indicated as a broken link).

---

### Post by kscelt on 2005-12-13
ah, a clue - the target file for the link is:

/usr/local/jre1.5.0_05/plugin/i386/ns7libjavaplugin_oji.so

wrong file name being pointed to?

---

### Post by arnieboy on 2005-12-13
[QUOTE=kscelt]Rats, no it did not.  Still says I am using the blackdown plugin.

Now in the opt/firefox/plugins directory, I have two files related to java:

libjavaplugin_oji.so and ns7libjavaplugin_oji.so (which under properties is indicated as a broken link).[/QUOTE]
oops my bad, I made a typo last time. do the following:
```
sudo rm -f /opt/firefox/libjavaplugin_oji.so /opt/firefox/plugins/ns7libjavaplugin_oji.so
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/
```

---

### Post by kscelt on 2005-12-13
Well, I was trying to fix before I read your last reply. Bad idea, lol.

Now I have deleted the libjavaplugin.so and the libjavaplugin_oji.so

Then tried your last code, and I now do not have a libjavaplugin.so file and the browser indicates no java plugin is installed.

Sorry to be such a pain.

I do have a libjavaplugin_oji.so file, however

---

### Post by hl2u on 2005-12-13
[QUOTE=arnieboy]hl2u: this is what u need to do I think. Open synaptic and search for "pango" under "search for package under names" and install all the packages listed. and then try running firefox (not the installation) again from terminal.[/QUOTE]

ok, did install _everything_ ;) related to pango, in Synaptic.
runned Firefox from terminal and :

```


me@mymachine:~$ firefox

(firefox-bin:8383): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:8383): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No such file or directory

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversia de la setul de caractere &#8222;UTF-8&#8221; la &#8222;ISO-8859-1&#8221; nu este suportat&#259;

(firefox-bin:8383): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8383): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8383): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8383): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8383): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8383): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8383): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8383): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8383): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8383): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8383): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8383): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8383): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:8383): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/opt/firefox/run-mozilla.sh: line 131:  8383 Aborted                 "$prog" ${1+"$@"}
me@mymachine:~$ Warning: locale not supported by Xlib, locale set to C
Warning: X locale modifiers not supported, using default



```

---

### Post by kscelt on 2005-12-13
Please disregard, all is now great - thanks so much for the help

---

### Post by kimme on 2005-12-13
It worked here. :)

---

### Post by arnieboy on 2005-12-13
hl2u: I am quite sure the errors being thrown are locale related. I am sorry but I am not really an expert on locale related issues because the only language I have ever used on my computers is American English. I wish I could help u more though.

---

### Post by makis on 2005-12-13
It worked out of the box.

Thx Arnieboy!

---

### Post by majikstreet on 2005-12-13
hl2u

could you please put all those errors in a tag like this: [-code-] errors [-/code-] without the "-"? It'd make it a lot easier to navigate the thread... (Hope I'm not being too much of an ass...)

---

### Post by arnieboy on 2005-12-13
hl2u:
please do the following:
```
sudo apt-get install libpango1.0-0
```
and then try running firefox again

---

### Post by lonetree on 2005-12-13
Help! mine don't seem to work at all. I tried the Howto, it didn't work, and now I tried the script from arnieboy, but it still doesn't work. when I start firefox from console it gives an error.

stealth@linux-nb:~$ firefox
/opt/firefox/run-mozilla.sh: line 131: 10429 Segmentation fault      "$prog" ${1+"$@"}


What could be wrong? Hope someone can help

regards,

---

### Post by arnieboy on 2005-12-13
do the following:
```
sudo rm -rf /opt/firefox
```
and run the script again

---

### Post by lonetree on 2005-12-13
thanks arnieboy, will try that later on. Thanks for your reply.

---

### Post by Ric Fischer on 2005-12-14
[QUOTE=arnieboy]if it works for u, please do post on the thread to say so. :)[/QUOTE]
The install went just fine for me. I love arnieboy's work.

Java didn't work, but after doing the Java 1.5 fix mentioned earlier (where the user kept seeing the Blackdown version of Java instead of 1.5), even that's working.

I also used the new version of the form widgets "update" for Firefox 1.5. The message notes it's for the Firefox 1.5 as per the instructions on the Wiki, but the same steps worked for me in the arnieboy version, too. (Probably because arnieboy's script seems to do all the same things.)

Thanks, arnieboy!

---

### Post by weeguy on 2005-12-14
[QUOTE=arnieboy]do the following:
```
sudo rm -rf /opt/firefox
```
and run the script again[/QUOTE]

> Leaving `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
Leaving `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
ln: `/usr/bin/firefox': File exists
ln: `/usr/bin/mozilla-firefox': File exists
/opt/firefox/run-mozilla.sh: line 131: 14346 Segmentation fault      "$prog" ${1+"$@"}

Had the same problem and "sudo rm -rf /opt/firefox" didn't help. Any idea?

---

### Post by lonetree on 2005-12-14
[QUOTE=arnieboy]do the following:
```
sudo rm -rf /opt/firefox
```
and run the script again[/QUOTE]

Hi arnieboy, did what you mentioned, it din work. Kinda upset, looks like I have to reinstall the whole thing again and do lotsa stuff from scratch again. Sigh!

---

### Post by lonetree on 2005-12-14
Hi guys, 

I solved the problem. If you have install SCIM, this could be the problem (firefox unable to start with error 

/opt/firefox/run-mozilla.sh: line 131:  8175 Segmentation fault      "$prog" ${1+"$@"}

or something similar

Solution :

# sudo gedit /usr/bin/mozilla

add  "export GTK_IM_MODULE=xim" without the quotes, before the line 
moz_pis_startstop_scripts()

save it, and run firefox. It will throw 2 error, after which everything back to normal operation the next time you start firefox again.

However, java runtime need to relink, wonder if I still remember how to, can someone highlight? Also, I have not try adobe plugins and some other plugins.

Anyway, I hope this helps some of you guys out there. Remember, my problem is due to SCIM, and I presume this only could be solved if you have SCIM installed.

to confirm that this is the problem, try this in console first : 

# [COLOR="Red"]GTK_IM_MODULE=xim firefox[/COLOR]

regards,

---

### Post by weeguy on 2005-12-14
I wouldn't consider this a solution, since you would not be able to to use SCIM using this method, hence crippling the browser. Anyway, [hpn compiled a version of Firefox 1.5](http://ubuntuforums.org/showthread.php?t=92303&page=2) that works with SCIM, so SCIM users might want to try that out.

btw: lonetree, glad to see another user from Singapore around here. :) And follow the instructions [here](https://wiki.ubuntu.com/RestrictedFormats#head-ef347c277a133b64af0600bd1bf24bc64e7038b8) to relink java.

---

### Post by tomski on 2005-12-14
Hi there Arnieboy,
i was just wondering if the issue's with the plugins for FF1.5 have been resloved 
because a few friends have told me that it is having problems with active x controls and i need that plugin to work as i have created a couple of sites that use active x or is it just a case of copying over the relevant files from the FF1.0.7 dir to get them all working??

---

### Post by lonetree on 2005-12-14
[QUOTE=weeguy]I wouldn't consider this a solution, since you would not be able to to use SCIM using this method, hence crippling the browser. Anyway, [hpn compiled a version of Firefox 1.5](http://ubuntuforums.org/showthread.php?t=92303&page=2) that works with SCIM, so SCIM users might want to try that out.

btw: lonetree, glad to see another user from Singapore around here. :) And follow the instructions [here](https://wiki.ubuntu.com/RestrictedFormats#head-ef347c277a133b64af0600bd1bf24bc64e7038b8) to relink java.[/QUOTE]

Hi weeguy,

thanks for your reply. Seriously, I was in a rush to try that "solution", and didn't notice that SCIM was crippled. Will try later. 

Where can I get the SCIM supported ff1.5 that you mentioned just now?

Btw, are you from singapore too?

---

### Post by jrib on 2005-12-14
[QUOTE=tomski]Hi there Arnieboy,
i was just wondering if the issue's with the plugins for FF1.5 have been resloved 
because a few friends have told me that it is having problems with active x controls and i need that plugin to work as i have created a couple of sites that use active x or is it just a case of copying over the relevant files from the FF1.0.7 dir to get them all working??[/QUOTE]

Firefox doesn't use activex.  Activex has been the cause of several of IE's security vulnerabilities.  A quick google search gave me [this]("http://www.iol.ie/~locka/mozilla/mozilla.htm") but I have no idea if it works.  I'd try to stay away from activex personally.

---

### Post by arnieboy on 2005-12-14
[QUOTE=_jason]Firefox doesn't use activex.  Activex has been the cause of several of IE's security vulnerabilities.  A quick google search gave me [this]("http://www.iol.ie/~locka/mozilla/mozilla.htm") but I have no idea if it works.  I'd try to stay away from activex personally.[/QUOTE]
this is interesting.. never knew there were working on an active X plugin for mozilla..

---

### Post by lonetree on 2005-12-14
You are right, Weeguy, it really has crippled my SCIM, while I don't really need to type chinese or other language, only sometimes. But the feeling of being crippled is too upset.

Hope someone can get this sovled soon.

So embarass to have posted that so-call solution up there.

One thing I like about ff1.5 is it solve flash problem for me, I used to be only able to load 1/2 or 1/4 of a page for some flash website, now it seem that it is solved, but I may be wrong again. :-)

regards,

---

### Post by tomski on 2005-12-14
[QUOTE=_jason]  I'd try to stay away from activex personally.[/QUOTE]

So do i, but i have to have it so i can edit/update my clients site & make sure its all working.
looks like i'll have to try another way

---

### Post by arnieboy on 2005-12-14
yeah active X is a security nightmare on windows.. they realized it a little late.. too late to roll it back..

---

### Post by tomski on 2005-12-14
aint it just, but some people won't let go.
still luckily i dual boot so not much of a problem but i am hoping to leave windows just seems *nix has its differences so just tring to find different answers to similar problems.

how would this script affect FF use in E17 or other wm's

---

### Post by exkalibur on 2005-12-14
Thanks again for your efforts and good work. The script worked really well and it is sure appreciated.

Regards

---

### Post by tomski on 2005-12-14
thanks arnieboy 
FF1.5 is so quick

---

### Post by swmiller6 on 2005-12-14
I am getting this error message after typing firefox into the comandline...

/opt/firefox/run-mozilla.sh: line 131: 15882 Floating point exception"$prog" ${1+"$@"}

Any help would be greeatly apperciated.

---

### Post by Nunsta on 2005-12-14
Excellent script.  Thanks again, arnieboy.

I had some trouble with the Flash/Shockwave plugins, but I figured out how to install them.

Nice work, as usual.

---

### Post by lonetree on 2005-12-15
[QUOTE=swmiller6]I am getting this error message after typing firefox into the comandline...

/opt/firefox/run-mozilla.sh: line 131: 15882 Floating point exception"$prog" ${1+"$@"}

Any help would be greeatly apperciated.[/QUOTE]

Hi Swmiller6,

do you have SCIM installed on your ubuntu?

---

### Post by dguido on 2005-12-15
Any word on when this is going to be put in breezy-backports?  I don't want to screw up my system by installing 1.5 from source and then installing the dpkg over it when it comes out.

---

### Post by foxy123 on 2005-12-15
[QUOTE=dguido]Any word on when this is going to be put in breezy-backports?  I don't want to screw up my system by installing 1.5 from source and then installing the dpkg over it when it comes out.[/QUOTE]
you won't screw your system by installing FF1.5 in /opt. As soon as it is available from repositories (which can take a while) you have to follow the section in wiki about how to uninstall it and remove /opt/firefox and then install 1.5 from repos... Answering your first question, there is a topic about backporting FF1.5 in Backports forum...

---

### Post by Nunsta on 2005-12-15
I guess I did do something wrong.

When I install extensions and restart Firefox, I get the following error

"Firefox could not install this item because of a failure in Chrome Registration. Please contact the author about this problem."

I can click okay, the extension installs, and everything is fine.  It does this every time I install an extension.

I tried the following and it had no effect
```
sudo chown -R mark:mark $HOME/.mozilla
```

---

### Post by Mudbream on 2005-12-15
Thanks dude!
Seemed I installed it as sudo but then followed some of your instructions in this list and it works fine now! Even my icons that were pointing to the old version are now pointing to the new one!
Thanks - made life alot easier!

---

### Post by NewToUbuntuAlex on 2005-12-15
It works exactly as described.
Thanks! :)

---

### Post by TimelessRogue on 2005-12-15
I've downloaded and installed Foxfire 1.5 on my laptop and workstation for both Windoze and Ubuntu (on both) during the past 48 hours (not that it took me that long!) ... at this point, all is well on all fronts and I've had no errors or malfunctions.  I'm impressed with both Firefox and all of the extensions that are available for it ... including but not limited to Nautilus - my favorite theme.

I tried both installation methods for Ubuntu:  the one recommended by Firefox and the one detailed at [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion).  The first worked sorta but was not as easy as the Wiki.Ubuntu.com methond ... not as simple as a "normal" install, but not particularly difficult either.

So kudos to all involved in the upgrade ... much improved ... thanks ...

---

### Post by lonetree on 2005-12-15
has nobody com out with a solution for SCIM and FF1.5 yet?

---

### Post by adam.tropics on 2005-12-15
A bit confused about permissions etc. I can sudo firefox and start it from the command line, but am unable to start it from a link! As far as I can tell it should, but if i try, I get "Firefox is already running but not responding, to open a new window you must first close the existing firefox process, or restart your system." 

Can't find any firefox processes running, and restart just gives same result again. Any ideas??

---

### Post by pcatiprodotnet on 2005-12-15
How do I install Flash now?
Installing from the repositories didn't work.
[solved]
nevermind.  after adding flash from the repositories, I re-ran the install script and it works now.

---

### Post by swmiller6 on 2005-12-16
[QUOTE=lonetree]Hi Swmiller6,

do you have SCIM installed on your ubuntu?[/QUOTE]


No I do not have SCIM installed... Should I have it installed?

---

### Post by pizzach on 2005-12-16
[QUOTE=lonetree]has nobody com out with a solution for SCIM and FF1.5 yet?[/QUOTE]

From what I read directly off of scim's web site ([http://www.scim-im.org/](http://www.scim-im.org/)) it's from binary incompatibility.  Therfore if you compile 1.5 yourself, scim should work.  (Don't know if you need to compile scim too.)  Which is probably why downloading the binary from mozilla.com doesn't work.

Correct me anyone if I'm wrong.

---

### Post by Chrissss on 2005-12-16
[QUOTE=foxy123]The main reason I am looking forward for official package is that I want to compile moztrabiff extension for 1.5 and need firefoox development package.[/QUOTE]
When you check out the CVS Code of moztraybiff, you also get precompiled binaries. The "mozTrayBiff-1.2-i486-linux-gnu-tb1.5.xpi" works for me (Breezy and TB 1.5RC1)

[http://moztraybiff.mozdev.org/devel.html](http://moztraybiff.mozdev.org/devel.html)

CU
CHristoph

---

### Post by foxy123 on 2005-12-16
[QUOTE=Chrissss]When you check out the CVS Code of moztraybiff, you also get precompiled binaries. The "mozTrayBiff-1.2-i486-linux-gnu-tb1.5.xpi" works for me (Breezy and TB 1.5RC1)

[http://moztraybiff.mozdev.org/devel.html](http://moztraybiff.mozdev.org/devel.html)

CU
CHristoph[/QUOTE]
thanks a lot...

---

### Post by x__dark on 2005-12-16
to anyone who used this installation guide, have you run into any problems with firefox 1.5 crashing a lot?

---

### Post by foxy123 on 2005-12-16
[QUOTE=x__dark]to anyone who used this installation guide, have you run into any problems with firefox 1.5 crashing a lot?[/QUOTE]
no, it works fine...

---

### Post by lonetree on 2005-12-16
[QUOTE=swmiller6]No I do not have SCIM installed... Should I have it installed?[/QUOTE]

No. If you have SCIM installed, you wil have the same error too. Mine have. I am hoping for some solutions to come out soon. Cheers

---

### Post by arnieboy on 2005-12-16
[QUOTE=Nunsta]I guess I did do something wrong.

When I install extensions and restart Firefox, I get the following error

"Firefox could not install this item because of a failure in Chrome Registration. Please contact the author about this problem."

I can click okay, the extension installs, and everything is fine.  It does this every time I install an extension.

I tried the following and it had no effect
```
sudo chown -R mark:mark $HOME/.mozilla
```[/QUOTE]
this is is a known issue with firefox 1.5. The solution is giving user write permissions to the install directory (/opt/firefox) which is suicidal in terms of security. 
It should not be a hassle, because at the end of the day, u will not be installing a dozen extensions every day, just using firefox, and chrome registration errors wont show up in that case.

---

### Post by lost.sync on 2005-12-16
nice.  went off without a hitch.  i don't use firefox that much but it's nice to have around when some site starts complaining about opera.  

thanks, man.

---

### Post by swmiller6 on 2005-12-16
SO nobody has any ideas on this? 
/opt/firefox/run-mozilla.sh: line 131: 15882 Floating point exception"$prog" ${1+"$@"}

I really do not see how anybody can be productive on linux snice I have installed ubuntu all I have been doing is trying to get things to work properly... I mean really  something as simple as installing the latest version of a thrid party software is not suppose to be this hard.
I can not seem to even watch a simple dvd and yeah the dma mode is on, if I want the latest version of say Inkscape or the Gimp I have to wait who knows how long for the repositories to be updated.
And before anybody says I should complie it myself yeah like I have all day to track down dependencies and search countless wiki's to get a simple program to work!!!

Ok now I feel better..... Sorry for the rant....

---

### Post by Mr. Electric Wizard on 2005-12-16
Script worked wonderfully, thanks Arnie:p 
1.5 is much, much better!:D

---

### Post by lonetree on 2005-12-16
[QUOTE=swmiller6]SO nobody has any ideas on this? 
/opt/firefox/run-mozilla.sh: line 131: 15882 Floating point exception"$prog" ${1+"$@"}

I really do not see how anybody can be productive on linux snice I have installed ubuntu all I have been doing is trying to get things to work properly... I mean really  something as simple as installing the latest version of a thrid party software is not suppose to be this hard.
I can not seem to even watch a simple dvd and yeah the dma mode is on, if I want the latest version of say Inkscape or the Gimp I have to wait who knows how long for the repositories to be updated.
And before anybody says I should complie it myself yeah like I have all day to track down dependencies and search countless wiki's to get a simple program to work!!!

Ok now I feel better..... Sorry for the rant....[/QUOTE]

hahahaha swmiller6,

relax, thats linux, I have the same kind of feelings you have previously. You will find the beauty of it one day. Just think that you know somwthing new that most don't. Anyway, I do hope that one day all linux distro will be standardize and installing and upgrading of packages will be as easy. Now, just learn what we can and what we know.

Cheers

---

### Post by armada on 2005-12-17
[QUOTE=fishfork]How to do it **without** messing up your system and confusing the package manager (hopefully!)

The Howto is on the wiki at [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion). Comments here please.[/QUOTE]

I tried it last night unwittingly without libstdc++5 installed and messed up my system.

Had to re-install ubuntu from scratch.

Now I do have a great ubuntu with Firefox 1.5.

Did encounter the chrome bug and use "sudo touch ..." to fix it.

Strongly suggest newbies to backup your ubuntu before attempting this.

---

### Post by ubuntu27 on 2005-12-17
Hello guys! :) Thank you for helping me each time I'm in trouble :D Anyway. I've installed Firefox 1.5 with this wonderful script !!
Anway, look at the attached image.

As you can see Synaptic thinks I still have Firefox 1.0.7 
Do you think something went wrong?

EDIT: Never mind, I've read the whole thread. SO, it means that Firefox 1.0.7 was not unistalled. and that Firefox 1.5 was intalled and made it default. :)

Great.
Thanks ArnieyBoy for the script. It works perfectly !!

---

### Post by adam.tropics on 2005-12-17
I have firefox 1.5 running about right, except I am unable to select text in the address bar using either the mouse or keyboard. I can delete from the beginning, but not backspace from the end!!Very wierd!!

Edit: Turns out it was the widgets! Restoring Res folder solved it.!

---

### Post by kathymacau on 2005-12-17
I ran the script and updated ff to 1.5.  Now when I go to a page which uses Java ff shuts down.  I have read the whole thread and applied all the Java fixes with no change.  Just a tad annoyed cos I had the old version working almost the way I wanted but am willing to persivere till I get it right.  I must mention that I had no error messages when I used the code, I also reinstalled Java using Automatix.

---

### Post by arnieboy on 2005-12-17
[QUOTE=kathymacau]I ran the script and updated ff to 1.5.  Now when I go to a page which uses Java ff shuts down.  I have read the whole thread and applied all the Java fixes with no change.  Just a tad annoyed cos I had the old version working almost the way I wanted but am willing to persivere till I get it right.  I must mention that I had no error messages when I used the code, I also reinstalled Java using Automatix.[/QUOTE]
please paste the results of
```
java -version
```

---

### Post by kathymacau on 2005-12-17
Thanks for the quick response.

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

---

### Post by arnieboy on 2005-12-17
[QUOTE=kathymacau]Thanks for the quick response.

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)[/QUOTE]
try this:
```
sudo rm -f /opt/firefox/plugins/libjava* 
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/
```

---

### Post by kathymacau on 2005-12-17
[QUOTE=arnieboy]try this:
```
sudo rm -f /opt/firefox/plugins/libjava* 
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/
```[/QUOTE]

Now I'm getting onto the site I want and am being asked to install the required plug-in, which would be java-plugin for firefox (I'm guessing)

---

### Post by arnieboy on 2005-12-17
[QUOTE=kathymacau]Now I'm getting onto the site I want and am being asked to install the required plug-in, which would be java-plugin for firefox (I'm guessing)[/QUOTE]
no! java plugin was already installed.
do the following:
open up firefox and in the address bar type:
> about:plugins 
and scroll down and tell me if u see your java plugin listed there or not.

---

### Post by kathymacau on 2005-12-17
[QUOTE=arnieboy]no! java plugin was already installed.
do the following:
open up firefox and in the address bar type:

and scroll down and tell me if u see your java plugin listed there or not.[/QUOTE]

Java plugin isn't listed

---

### Post by arnieboy on 2005-12-17
[QUOTE=kathymacau]Java plugin isn't listed[/QUOTE]
please paste the results of:
```
ls /opt/firefox/plugins
```

---

### Post by kathymacau on 2005-12-17
[QUOTE=arnieboy]please paste the results of:
```
ls /opt/firefox/plugins
```[/QUOTE]

flashplayer.xpt         mplayerplug-in-qt.so   mplayerplug-in-wmp.xpt
libflashplayer.so       mplayerplug-in-qt.xpt  mplayerplug-in.xpt
libjavaplugin_oji.so    mplayerplug-in-rm.so   nphelix.so
libnullplugin.so        mplayerplug-in-rm.xpt  nphelix.xpt
mplayerplug-in-gmp.so   mplayerplug-in.so      nppdf.so
mplayerplug-in-gmp.xpt  mplayerplug-in-wmp.so

---

### Post by arnieboy on 2005-12-17
good. you have ur java plugin installed. close all your browser windows, restart firefox and enjoy java :)

---

### Post by r4ik on 2005-12-17
First of all thanks for the script.
Will you have a look at this output.
I think i missed something somewhere somehow.
When run the script again Firefox pops up in the middle.
I checked no java there.
Is there a work around please ?


r4ik@compu:~$ ls /opt/firefox/plugins
libjavaplugin.so  libnullplugin.so  nppdf.so
r4ik@compu:~$

---

### Post by kathymacau on 2005-12-17
[QUOTE=arnieboy]good. you have ur java plugin installed. close all your browser windows, restart firefox and enjoy java :)[/QUOTE]

Sorry, but it still isn't working.  Giving up for now and heading to bed. 3am my time.

---

### Post by rjwood on 2005-12-17
here's mine arnieboy and I don't have java working either.```
rob@ubuntu:~$ ls /opt/firefox/plugins
libjavaplugin.so  libnullplugin.so

```

---

### Post by arnieboy on 2005-12-17
for those of u who have java 1.5 installed, follow instructions on post # 189 on this thread.

---

### Post by r4ik on 2005-12-17
Will do so thank you.
Sorry for beeing a lazy (beep) i havent read it all.

---

### Post by r4ik on 2005-12-17
No Java plug there re-install ?

Shockwave Flash

    Bestandsnaam: libflashplayer.so
    Shockwave Flash 7.0 r25

MIME-type 	Beschrijving 	Achtervoegsels 	Actief
application/x-shockwave-flash 	Shockwave Flash 	swf 	Ja
application/futuresplash 	FutureSplash Player 	spl 	Ja
Default Plugin

    Bestandsnaam: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME-type 	Beschrijving 	Achtervoegsels 	Actief
* 	All types 	.* 	Nee
Adobe Reader 7.0

    Bestandsnaam: nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME-type 	Beschrijving 	Achtervoegsels 	Actief
application/pdf 	Portable Document Format 	pdf 	Ja
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Ja
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Ja
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Ja
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Ja

---

### Post by unwoken on 2005-12-17
Hi arnieboy,

thanks for this script, once again.  it's really nice to know that people like you are here to help us mortals ;) 

i am having a slight problem now i have 1.5 installed.  it is to do with the 'text zoom' extension from: [http://www.cosmicat.com/extensions/textzoom/](http://www.cosmicat.com/extensions/textzoom/)

i admit that i had to edit the install.rdf to get it to work as the max version wasn't high enough.  it does work fine, and this is certainly not a complaint (as i know it has nothing to do with you), but i'll tell you what's going on anyway, as you know a lot more than me about these sort of things.

i can set the text zoom level, and everything works perfectly.  however, if i restart a saved session (through tab mix plus settings) or open all tabs from a bookmark folder the text zoom is not applied.

i have removed the saved session function on tab mix plus, and don't often open all bookmarks from a particular folder in tabs anyway (i generally do it to test settings on various pages).

anyway, this was working fine on 1.0.7.  do you think that i am having this problem because the extension has not yet been formally updated to 1.5? or could it be something else?

i am very happy though, and would like to thank you again for all the help you have offered, and time you have given...

cheers,
uw.

---

### Post by r4ik on 2005-12-17
Firefox died completely had to install opera and re-run the script
Here's my output at this moment,

r4ik@compu:~$ ls /opt/firefox/plugins
libjavaplugin_oji.so  libnullplugin.so  nppdf.so
r4ik@compu:~$

The #189 did not give any result.
Something has to be wrong on my side. :)

---

### Post by ubuntu27 on 2005-12-17
Need help :(  ok, firefox installed fine. I can install Extension like I always do from my user account (the first account), but the rest of the user accoun can't install any extensiosn at all. I don't remember the error that gives me.. I think it was chromo something...

ah.. and that chromo error keep apearing even in my account each time I install new extensions :shock:

---

### Post by NunoCorreia on 2005-12-17
I didn't read the rest of thread because it was big so I don't know if this has been addressed yet, but after installing FF with the script (which went great, good work ;)) code fields - like those frequently used here to represent commands - appear blank. Although I'm able to select the text and paste somewhere else to see what it is, that's a PITA :???:

Has anyone seen this happen yet and was able to solve it?

---

### Post by galderz on 2005-12-17
i've followed instructions in wiki, but i get to the point of executing firefox and it says that it is an invalid command. checked permissions and x is avaiable for everyone. files are there and ln is pointing to /opt/firefox/firefox

:/opt/firefox$ ls -l
-rwxr-xr-x  1 root root    5239 2005-11-12 00:59 firefox

anything i might be missing?im newbie

---

### Post by akniss on 2005-12-17
The howto on the wiki worked perfectly for me!  Thanks!

---

### Post by kathymacau on 2005-12-17
[QUOTE=kathymacau]Sorry, but it still isn't working.  Giving up for now and heading to bed. 3am my time.[/QUOTE]

Arnieboy thank you, all is go.  Funny how I could see the problem after a sleep.  Could not have done it without your help though, and I have learned heaps.  Must have a look at a command line tutorial though, so I know what instructions are doing, rather than simply following blindly.

---

### Post by rjwood on 2005-12-17
rob@ubuntu:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
This is interesting because in my home folder I have jre-1_5_0_05-linux-i586

---

### Post by rjwood on 2005-12-17
never mind I did the smart thing and read the thread and found my problem.

arnie, you are an outstanding member of this community. Thank you for all the help. Not just on this but other assistence you have given me. Cheers! to a good guy!!

---

### Post by naturalhl2 on 2005-12-18
Ok im having an issue installing this 
I download firefox and I extract to home folder then I go to 
applications-accessories-terminal and then I do that ./firefox_install thing and it says File or directory cannot be found any ideas? 
How do I run the gnome terminal or is that the terminal under accesories

---

### Post by cstudent on 2005-12-18
[QUOTE=naturalhl2]Ok im having an issue installing this 
I download firefox and I extract to home folder then I go to 
applications-accessories-terminal and then I do that ./firefox_install thing and it says File or directory cannot be found any ideas? 
How do I run the gnome terminal or is that the terminal under accesories[/QUOTE]

First, yes that is the terminal.
Second, click on your top menu bar, Places and then Home Folder. See if you can find the file firefox_install. If it's not there then it either didn't get extracted or was extracted to another directory.

---

### Post by unwoken on 2005-12-18
can anyone tell me how to go back to using 1.0.7 as the default?

there are certain extensions i need which are 1.0.7 only, and i am also having a little trouble accessing some sites.

i really appreciate the script, but i would like to go back to 1.0.7 for now.  Can anyone help?

thks.

EDIT: i have found a file "firefox.ubuntu" in /usr/bin which loads 1.0.7.  if i modifiy my launcher to that file, should i do anything else?  thks again.

---

### Post by arnieboy on 2005-12-18
[QUOTE=unwoken]can anyone tell me how to go back to using 1.0.7 as the default?

there are certain extensions i need which are 1.0.7 only, and i am also having a little trouble accessing some sites.

i really appreciate the script, but i would like to go back to 1.0.7 for now.  Can anyone help?

thks.

EDIT: i have found a file "firefox.ubuntu" in /usr/bin which loads 1.0.7.  if i modifiy my launcher to that file, should i do anything else?  thks again.[/QUOTE]
This is what u need to do:
```
mv ~/.mozilla ~/.mozilla-1.5
sudo rm -f /usr/bin/firefox /usr/bin/mozilla-firefox
sudo ln -s /usr/lib/mozilla-firefox/firefox /usr/bin/firefox
sudo ln -s /usr/lib/mozilla-firefox/firefox /usr/bin/mozilla-firefox
```

now run firefox as usual from menu

---

### Post by galderz on 2005-12-18
i managed to get firefox finally running, but instead of executing just 'firefox', i had to execute 'bash firefox', it might sound very silly, but why is that? i bet it's a newbie question.

also, how can i get a link in the desktop to execute 'bash firefox'? i just tried putting that in the command line of the link but did not work.

thanks

---

### Post by Sebby on 2005-12-18
Can anyone help me with the new version of Thunderbird? I followed the Wiki instructions. When I run thunderbird from the command line, it opens Thunderbird 1.5. However, when I now click my Thunderbird icon, nothing opens - running mozilla-thunderbird from the command line gives:

```
run-mozilla.sh: Cannot execute /opt/thunderbird/mozilla-thunderbird-bin.
```

I think I've messed up the symbolic links, but I don't really know how to fix it.

---

### Post by swmiller6 on 2005-12-18
This thread is still about Firefox 1.5 right?

I have been unable to in my limited Linux knowledge to figure this out, can you please point me to the person or place I should post this error message?

/opt/firefox/run-mozilla.sh: line 159:  8731 Floating point exception"$prog" ${1+"$@"}

I have tried the wiki method and also used the automatix script and both turn up the same error message. Could this have something to do with the Easyubuntu script? I used that to install the media playback mess and nvida drivers...

---

### Post by mrcanard on 2005-12-18
The install didn't go exactly as per the HOWTO.
However it was close enough that Firefox 1.5 is up and running on this machine.
Thanks,

---

### Post by pcatiprodotnet on 2005-12-18
I can't get Java to work with this either.  I tried everything suggested here several times.  Note, This is a fresh install with Automatix.

After running ./install_firefox I got this error message:

/lib/i386/libjavaplugin_nscp.so: cannot open shared object file: No such file or directory

---

### Post by arnieboy on 2005-12-18
[QUOTE=pcatiprodotnet]I can't get Java to work with this either.  I tried everything suggested here several times.  Note, This is a fresh install with Automatix.

After running ./install_firefox I got this error message:

/lib/i386/libjavaplugin_nscp.so: cannot open shared object file: No such file or directory[/QUOTE]
try installing firefox 1.5 with automatix 4.0

---

### Post by pcatiprodotnet on 2005-12-18
Ok, I finally got Java working.  This fix may only apply to those who installed Java with Automatix v3.5 or less.
I needed to make a little change to arnieboy's suggested fix:

sudo rm -f /opt/firefox/plugins/libjava*

ORIGINAL:
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/

CHANGED:
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/

works great.  Now lets see what new goodies are in Automatix 4.0 :)

> hey thanks for that pcatiprodotnet
Your welcome, I hope this helps the others above.

---

### Post by arnieboy on 2005-12-18
[QUOTE=pcatiprodotnet]Ok, I finally got Java working.
I needed to make a little change to arnieboy's command:

WAS:
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/

NOW:
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/

works great.  Now lets see what new goodies are in Automatix 4.0 :)[/QUOTE]
hey thanks for that pcatiprodotnet.. that had slipped my notice. infact the same bug had crept into automatix version 4.0.. corrected it now. thanks a lot :)

---

### Post by unwoken on 2005-12-18
[QUOTE=arnieboy]This is what u need to do:
```
mv ~/.mozilla ~/.mozilla-1.5
sudo rm -f /usr/bin/firefox /usr/bin/mozilla-firefox
sudo ln -s /usr/lib/mozilla-firefox/firefox /usr/bin/firefox
sudo ln -s /usr/lib/mozilla-firefox/firefox /usr/bin/mozilla-firefox
```

now run firefox as usual from menu[/QUOTE]

thank you very much arnieboy.  i'm at work now, but will do as you suggested when i get home.  i appreciate the help.

uw.

---

### Post by NunoCorreia on 2005-12-18
[QUOTE=NunoCorreia]I didn't read the rest of thread because it was big so I don't know if this has been addressed yet, but after installing FF with the script (which went great, good work ;)) code fields - like those frequently used here to represent commands - appear blank. Although I'm able to select the text and paste somewhere else to see what it is, that's a PITA :???:

Has anyone seen this happen yet and was able to solve it?[/QUOTE]
Solved. Try selecting a different font setting for Monospace in Preferences.

---

### Post by ubuntu27 on 2005-12-18
[QUOTE=ubuntu27]Need help :(  ok, firefox installed fine. I can install Extension like I always do from my user account (the first account), but the rest of the user accoun can't install any extensiosn at all. I don't remember the error that gives me.. I think it was chromo something...

ah.. and that chromo error keep apearing even in my account each time I install new extensions :shock:[/QUOTE]
so... no solutions, no ideas? :(

---

### Post by spockrock on 2005-12-18
thanks this worked perfectly

---

### Post by unwoken on 2005-12-18
[QUOTE=ubuntu27]so... no solutions, no ideas? :([/QUOTE]

from what i read here the chrome error appears on first reload after every extension install (happened to me also).  i think that is not necessarily a problem, but it shouldn't happen apart from that.

can't offer anything on your other issue, but maybe others can help there.

---

### Post by 5-HT on 2005-12-19
Hi, thanks for the How To.

Just wondering about what the  dpkg-divert step does though?

I've read the man page, but if Firefox 1.5 is not being backported to Breezy... I'm wondering if the dpkg-divert is no longer needed, and if using it may cause problems if updates are available in the repos for Firefox 1.0.7 (which I've kept installed)?

Thanks for anyone who can shed some light on this.

---

### Post by galderz on 2005-12-19
has anyone uninstalled Firefox 1.0x after installing Firefox 1.5 following this how-to? If so, how have you done it in order to avoid messing things up?

many thanks

---

### Post by Darkness3477 on 2005-12-20
G'day, I've tried install it exactly how it says too. I've downloaded the file and put it in my home directory, then why i type the command ```
 sudo cp firefox-1.5.tar.gz /opt
``` i get this error warning --cp: cannot stat `firefox-1.5.tar.gz': No such file or directory

Why is this happening? I really would like firefox 1.5 because right now, i just have the default one that comes with 5.10 and it really sucks.

---

### Post by Sebby on 2005-12-20
Are you sure that's the exact filename of the file you downloaded?

---

### Post by foxy123 on 2005-12-20
[QUOTE=Darkness3477]G'day, I've tried install it exactly how it says too. I've downloaded the file and put it in my home directory, then why i type the command ```
 sudo cp firefox-1.5.tar.gz /opt
``` i get this error warning --cp: cannot stat `firefox-1.5.tar.gz': No such file or directory

Why is this happening? I really would like firefox 1.5 because right now, i just have the default one that comes with 5.10 and it really sucks.[/QUOTE]
what does 'ls' say?

---

### Post by ndhskp on 2005-12-21
How do you run the new Firefox 1.5 along side the old version 1.0.7.  I want to be able to run both versions simultaneously so I can make various comparison.

I installed my Firefox 1.5 this way.

/home/username/firefox

I told the profile.ini file located in /.mozilla to look to /home/username/.Firefox15/mozilla/firefox/ffjsqsgq.default  for the profile.

That takes care of the profile issue.  However I need to move or rename the .mozilla.ubuntu backup for the 1.0.7 version so that 1.0.7 does not rain terror down on 1.5.  The problem is both look to /.mozilla to see where a moved profile has gone so merely moving a profile does not work.

I created a desktop launcher for 1.5 and left the Gnome bar & menu Firefox the way it was meaning they launch 1.0.7.  And no I did not do divert because I want 1.0.7 as the default.  So i'm trying to maintain 1.0.7 as the default and if I want to run 1.5 I click on the desktop launcher.

Anybody know how I can do this?

---

### Post by tomski on 2005-12-21
[QUOTE=arnieboy]try this:
```
sudo rm -f /opt/firefox/plugins/libjava* 
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/
```[/QUOTE]


i tried this restarted FF1.5 and java still is not listed in about:plugins i have the latest java
output of java-version  :

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

i then run :

sudo rm -f /opt/firefox/plugins/libjava*
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/


i even rebooted & still nothing 
any other pointers

---

### Post by arnieboy on 2005-12-21
[QUOTE=tomski]i tried this restarted FF1.5 and java still is not listed in about:plugins i have the latest java
output of java-version  :

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

i then run :

sudo rm -f /opt/firefox/plugins/libjava*
sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/


i even rebooted & still nothing 
any other pointers[/QUOTE]

do the following:
```
sudo rm -f /opt/firefox/plugins/libjava*
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/
```

This will solve your java problem in firefox.
the post of mine that u used had a typo in it. my bad.

---

### Post by tomski on 2005-12-21
bingo 

cheers arnieboy

damn typos gte everone eh

---

### Post by PapaWiskas on 2005-12-22
Arnieboy......
Thanks for all the hard work...it worked great.....

I am so glad I dumped that other OS.....

---

### Post by nozdormu on 2005-12-23
[QUOTE=foxy123]i've got some issues with firefox, like blinking bookmarks (it is difficult to explain, you open bookmarks menu and hover mouse over any bookmark folder, instead to expand the folder, its blinking, so you have to click and then click on the bookmark... it is messy, anyway it never happened with 1.07), so I was hoping to get it sorted in a 'proper' install. (it may be my wm theme although or anthing like that).

The main reason I am looking forward for official package is that I want to compile moztrabiff extension for 1.5 and need firefoox development package.[/QUOTE]

I just wanted to bring this back up.  Both this blinking menu problem and the long delay when opening a save dialog the first time are fixed in the nightlies. These were really driving me crazy, so I just downloaded the 12-21-2005 Linux nightly build from here: [http://www.squarefree.com/burningedge/]("http://www.squarefree.com/burningedge/").

Since I had used the FirefoxNewVersion wiki page to upgrade to 1.5, all I needed to do was backup my Firefox folder (the one in /opt/) and untar+unzip the new version (1.6a1) into /opt/.  I then copied my plugins over.  

Also, be sure to make a backup of your profile just in case.  Some extensions may say they are out of date so I just manually bumped up the version to 1.6 in the install.rdf files, but those Nightly Tester Tools may work (I haven't used them).  I also recommend turning off automatic updates since all I really needed was these two bugs fixed and I don't want to deal with future breakage.  Everything seems to be going fine now, and if you can live with Firefox still being called Deer Park Alpha 2 for some reason, then you may want to try it.

---

### Post by sudokubuntu on 2005-12-23
Yeah! This one worked nice with my Debian based DeMuDi too. That's cool.

---

### Post by The Warlock on 2005-12-24
Hey, I'm just wondering why the wiki says that the deb package is non-free. Firefox is licensed under the MPL, correct? That's a Free Software license; both the OSI and the FSF have said so. Why the warning at the bottom?

---

### Post by OtubrabNad on 2005-12-24
[QUOTE=sailor420]Very good and very fast, but it doesnt seem to have imported my profile... Any ideas?[/QUOTE]
I have the same problem. On the advise of a friend, rather than following the tutorial, I used the installer script [http://ubuntuforums.org/attachment.p...1&d=1134350656](http://ubuntuforums.org/attachment.p...1&d=1134350656) from the thread [http://ubuntuforums.org/showthread.p...ht=firefox+1.5](http://ubuntuforums.org/showthread.p...ht=firefox+1.5) to install version 1.5. This didn't restore my profile, so someone on this forum suggested that I look at [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

After executing the following commands from the wiki (and not following the prior directions I might add):
```
cd ~/.mozilla/firefox
 mkdir ff1.5
 mv profiles.ini *.default ff1.5/
 cp ~/.mozilla.ubuntu//firefox/profiles.ini .
 cp -r ~/.mozilla.ubuntu//firefox/*.default .
```
I recieved this message:
```
cp: cannot stat `/home/hal/.mozilla.ubuntu//firefox/profiles.ini': No such file or directory
```
which messed Firefox up even more. The Flash plugin no longer plays sound and the font on webpages doesn't look as "pretty". My question is, how do I restore my old profile? I've noticed that the subdirectories 7alfwddg.default and emr48nez.default are in ~/.mozilla/firefox. Also 56qy6ilq.default is in ~/.mozilla/firefox/.mozilla_backup/firefox. I believe these three default files have something to do with my old profile if that helps.

---

### Post by ricardo on 2005-12-24
Hi!

Using the instructions of this thread, I installed FF1.5 perfectly. But I have one problem: the display resolution doesn't work.

I go into Edit -> Preferences -> Contents -> Fonts & colors -> Advanced -> Display resolution, and try with 72 dpi, 96 dpi, etc... without any result.

With the FF1.0.7 from Ubuntu, this option works perfectly.

Anyone knows how to activate it?

Thanks a lot.

---

### Post by Freddy on 2005-12-24
Hi could anybody tell me how te remove this version completely, the boot time for this firefox is horrific and I have some other problems too.   /// Freddan

---

### Post by Nunsta on 2005-12-24
[QUOTE=Freddy]Hi could anybody tell me how te remove this version completely, the boot time for this firefox is horrific and I have some other problems too.   /// Freddan[/QUOTE]

Yeah, I'm with you on this one.

---

### Post by Freddy on 2005-12-24
I've kind of solved the boot up time for this Firefox in Kubuntu though.
I used "firefox %u" to start it up and things seem to happen alot faster. Still wan't to remove it from the system though, it still feels sort of unstable for me.   /// Freddan

---

### Post by Humanoid on 2005-12-25
I built my own .deb file. Works fine if you remove Firefox 1.07 before installing this one. Give it a try: [http://www.students.oamk.fi/~t3vasa02/ubuntu/]("http://www.students.oamk.fi/~t3vasa02/ubuntu/")

The other file is the latest vlc with gtk2 support.. don't mind about that ;P

---

### Post by dudus on 2005-12-25
[QUOTE=Humanoid]I built my own .deb file. Works fine if you remove Firefox 1.07 before installing this one. Give it a try: [http://www.students.oamk.fi/~t3vasa02/ubuntu/]("http://www.students.oamk.fi/~t3vasa02/ubuntu/")

The other file is the latest vlc with gtk2 support.. don't mind about that ;P[/QUOTE]

I just can't remove 1.07 couse of the dependencies

---

### Post by shof2k on 2005-12-26
Thanks Arnieboy, worked a treat!

I only had 2 minor snags.  I had to reapply your flash workaround, and I had to edit the /res folder to add in the nicer firefox widgets.  Perhaps this could be added to the script?

roll on firefox 1.7!!!!! :)

---

### Post by arnieboy on 2005-12-26
[QUOTE=shof2k]Thanks Arnieboy, worked a treat!

I only had 2 minor snags.  I had to reapply your flash workaround, and I had to edit the /res folder to add in the nicer firefox widgets.  Perhaps this could be added to the script?

roll on firefox 1.7!!!!! :)[/QUOTE]
not everyone likes the "nice widgets", hence not included.
yes the script does not implement the flash workaround that i had devised because it doesnt work for everyone.

---

### Post by MihaiM on 2005-12-26
It is just me or after the 1.5 update the web links in gaim don't automatically open in Firefox anymore?

---

### Post by Gooks on 2005-12-26
It crashed on me how can i fix this? I am using the mozilla browser now.. I want to get back to the other mozilla browser the Firefox 1 can somebody help?

---

### Post by quonsar on 2005-12-26
[QUOTE=MihaiM]It is just me or after the 1.5 update the web links in gaim don't automatically open in Firefox anymore?[/QUOTE]

i don't know about Gaim, but i noticed that desktop shortcuts no longer launched firefox on my system after installing 1.5. i did some snooping around and noticed that the URL handler for http/https is specified as "mozilla-firefox", but when i typed that in a terminal i got an error from run-mozilla.sh:

```
run-mozilla.sh: Cannot execute /opt/firefox/mozilla-firefox-bin.
```

checking in /opt/firefox i found that indeed there was no such file, there is, however, a file named firefox-bin. i made a link like so:

```
sudo ln -s /opt/firefox/firefox-bin /opt/firefox/mozilla-firefox-bin
```

now desktop shortcuts work as expected! i'll bet this solves your Gaim problem too - give it a shot.

---

### Post by cimi on 2005-12-27
from swiss :thanks,danke,merci ,grazie!!

:)  :p

---

### Post by wakingeden on 2005-12-27
Can you please give me the command(s) to undo everything the script did?
I did everything as stated then I was asked for my password....I did not :repeat: did not sudo the command so I went ahead and gave it my password (stupid mistake).....anyways it installed as root and I want to undo the mistake I made by simply undoing everything, if this is possible please post.

~wakingeden~

---

### Post by calamari on 2005-12-27
[QUOTE=The Warlock]Hey, I'm just wondering why the wiki says that the deb package is non-free. Firefox is licensed under the MPL, correct? That's a Free Software license; both the OSI and the FSF have said so. Why the warning at the bottom?[/QUOTE]

It is my understanding that some of the FF graphics (icons, etc), are not free to distribute (there are free substitutes).  So, I called it non-free, since the FF download comes straight from the firefox site.  If I'm wrong about this please let me know.

---

### Post by simber on 2005-12-28
arnieboy, one little question, how do i change the language of the browser to spanish ?

---

### Post by Il_Tuo_Nome on 2005-12-28
That script rox, thank you ArnieSir:)

---

### Post by tomash_cz on 2005-12-29
Hello everyone,
I did all according to [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) to install firefox 1.5, but in the end when I started firefox using command 'firefox', there was only following error:

/opt/firefox/run-mozilla.sh: line 131: 8786 Segmentation fault "$prog" ${1+"$@"}

Could anyone give me a suggestion (i am a real linux-beginner :confused: )

Thanx!

---

### Post by lonetree on 2005-12-29
[QUOTE=tomash_cz]Hello everyone,
I did all according to [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) to install firefox 1.5, but in the end when I started firefox using command 'firefox', there was only following error:

/opt/firefox/run-mozilla.sh: line 131: 8786 Segmentation fault "$prog" ${1+"$@"}

Could anyone give me a suggestion (i am a real linux-beginner :confused: )

Thanx![/QUOTE]
same question again, do you have SCIM installed? I have the same problem, same error message like yours and I found out that it is due to SCIM, chinese input etc.

---

### Post by tomash_cz on 2005-12-29
Yes, I have SCIM installed for chinese input... is it there some way how to go over it?

---

### Post by erik-the-red on 2005-12-29
I really wish there was, because I have that **exact** same problem with SCIM.

---

### Post by tomash_cz on 2005-12-29
Really big thanx to lonetree, i found his thread
[http://www.ubuntuforums.org/showthread.php?p=572813#post572813](http://www.ubuntuforums.org/showthread.php?p=572813#post572813) 

it really works!!! :):) 

for total beginners (like me) - be sure u edit the right link in /usr/bin/, because my starter is /usr/bin/firefox, so i did 
sudo gedit /usr/bin/firefox and then continue according to lonetree solution

Thanx again!

---

### Post by lonetree on 2006-01-01
I'm afraid that is not a total solution yet. It only disable SCIM with FF1.5. You will notice that you will not be able to input other languages in it. I just hope that SCIM developers will soon find a way to resolve this.

:-)

for the moment, FF 1.5 will still work as long as you disbale SCIM.

cheers all and have a Happy New Year.

regards,

---

### Post by hericus on 2006-01-03
I prefer using Opera/1.07 myself, there are way too many exploits against 1.5 as I've discovered to my own detriment.

---

### Post by Sebby on 2006-01-03
[QUOTE=hericus]I prefer using Opera/1.07 myself, there are way too many exploits against 1.5 as I've discovered to my own detriment.[/QUOTE]
Just out of interest, like what?

---

### Post by Stroganoff on 2006-01-04
Hello,

I'm using Kubuntu 5.10 with Firefox 1.5, I installed Ff the way this thread suggested.
The problem is: The built-in download manager of Firefox is not able to open my applications anymore. When I click on "Downloads are saved in [Downloads]" it should open Konqueror with my download-directory. When I double-click on any of the finished downloads, it should open the appropriate program. But instead nothing happens.

How can I get that to work again?

---

### Post by rth on 2006-01-04
I get the following:
```
(firefox-bin:3960): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:3960): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No such file or directory

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:3960): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No such file or directory

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:3960): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:3960): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:3960): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:3960): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:3960): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:3960): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:3960): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:3960): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:3960): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:3960): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:3960): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:3960): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
Warning: locale not supported by Xlib, locale set to C
Warning: X locale modifiers not supported, using default
/opt/firefox/run-mozilla.sh: line 131:  3960 Aborted                 "$prog" ${1+"$@"}
```

I am using en-GB in Ubuntu and I downloaded that version from the Mozilla web site. Not sure why that should matter... On 5.10 AMD64.

Edit:
Never mind. Found a workaround here:
[http://ubuntuforums.org/showthread.php?t=90106](http://ubuntuforums.org/showthread.php?t=90106)

I install linux32 and recreate the ln -s for Firefox and it now seems to work.

---

### Post by NeoChaosX on 2006-01-04
[QUOTE=Stroganoff]Hello,

I'm using Kubuntu 5.10 with Firefox 1.5, I installed Ff the way this thread suggested.
The problem is: The built-in download manager of Firefox is not able to open my applications anymore. When I click on "Downloads are saved in [Downloads]" it should open Konqueror with my download-directory. When I double-click on any of the finished downloads, it should open the appropriate program. But instead nothing happens.

How can I get that to work again?[/QUOTE]
That's funny, because it never has worked, even with the older Ubuntu packages, in KDE. It only opens the folder if you have Nautilus open, and I'm sure you don't want the folder manager from another DE just to get one function.

---

### Post by tripleee on 2006-01-05
For us amd64 users it would be nice if you could also include a link to [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava) (which should probably be better coordinated with this guideline), perhaps with a small explanation that there is no amd64 version on mozilla.com (as it's apparently now called).

I bet some of the "didn't work for me" reports you see posted here are from amd64 users who didn't know how to proceed. For an example of what it looks like, [http://ubuntuforums.org/showthread.php?t=84975](http://ubuntuforums.org/showthread.php?t=84975) is illustrative.

For the record, I'm seeing good performance improvements with 1.5 here, although not as impressive as I had hoped. I'm a tab junkie (something like 5 Firefox windows with 20 tabs in each right now) and that really bogs down Firefox. But it's no longer keeping the CPU load constantly over 90% so that's already a huge improvement, and the memory leak bugs should be fixed so the memory footprint should at least in principle be less horrendous.

Couple of minor nits:

Just to make it flow nicely you might want to add something like this before the "touch" command:

```
sudo mkdir -p /opt/firefox/extensions/talkback@mozilla.org
```

There is no reason to make a copy of the tar.gz file. Tar can cope with a full pathname just fine. I can see how copying and then removing the file might make things simpler to explain, but technically, it's not necessary.

In the chown command, you could use ${USER}:${USER} instead of the literal username to make the command line usable verbatim.

Since so many people ask about the dpkg-divert, and/or seem to manage to get it wrong (symptom: "firefox" command doesn't work, or starts the wrong version), perhaps you could try to explain what it does in some more detail. (Diversions are a way to tell Debian / Ubuntu to use a different file, or version of a file, than what was installed with the system)

---

### Post by dcstar on 2006-01-06
I did the upgrade without using the full wiki instructions, what I did was:

[LIST=1]
[*]First download the latest Linux package from the Firefox site
[*]Installed it in /usr/local
[*]Ran /usr/local/firefox/firefox for the first time (it picked up all my existing bookmarks and extensions)
[*]Upgraded Extensions as required
[*]Removed incompatible Extensions
[*]Manually copied all of my plug-in .so files from my existing 1.07 install to the new 1.5 Plugin directory (I could have created links, but I just copied the full files)
[*]Created a new desktop shortcut with /usr/local/firefox/firefox as the command (which was then dragged to my top panel)
[/LIST]
One issue I had was with the [Spellbound]("http://spellbound.sourceforge.net/download") extension, I had to uninstall the existing incompatible Mozilla Spellcheck libraries and then install the "Mozilla spell check libraries for Firefox 1.0+" version, then I was able to install my dictionary again and return this handy function to full operation under FF 1.5.

Edit: A new version of Spellbound that works with 1.5.0.1 is available at:

[http://forums.mozillazine.org/viewtopic.php?t=351130&postdays=0&postorder=asc&postsperpage=15&start=0](http://forums.mozillazine.org/viewtopic.php?t=351130&postdays=0&postorder=asc&postsperpage=15&start=0)

So far it all seems to work well, and it is faster than 1.07 on my system (which still runs).

---

### Post by veloct on 2006-01-06
Running 1.5 in windows and linux is really no different.  If you use the profile for 1.0.7 with 1.5 it will cause a lot of issues. Before I installed 1.5 per the guide, I backed up my bookmars and then deleted the 1.0.7 profile. Then I installed 1.5 in /opt and I  did the same thing with thunderbird 1.5, I've had zero issues.

---

### Post by Onos on 2006-01-07
I am really starting to pull my hair out on this, almost ready to give up and use FF 1.07 until Dapper Drake.

Most likely it is a PBKAC (Problem Between Keyboard And Chair) and I simply lack the experience to know where I messed it up.

I followed the HOWTO up til the step where it says to test it by entering firefox in the terminal... and it only loaded version 1.07.

I am using Xubuntu (Xfce4) on i686 machine.

I do not have gnome installed as a desktop environment, nor do I have KDE... my machine is a slow as tar Celeron, 1100 MHz.

I use **uim / uim-anthy** since I need Japanese input.  I read how scim tends to break under FF 1.5, so I made sure any and all instances of it were scrubbed from the machine.

Per the wiki, I have installed:

**libstdc++5**

When I tried to do this step:

```
cd ~/.mozilla/firefox/*.default
 mkdir ~/Desktop/ffsettings
 cp bookmarks.html cert8.db cookies.txt formhistory.dat key3.db signons.txt history.dat  mimeTypes.rdf ~/Desktop/ffsettings
```

it will not allow me to create this ffsettings subdirectory, even when I use sudo -.

Since I figured this is only for settings that I can reset later in the would be install of FF 1.5, I passed this step after trying it a few times without any results.


This seems to have worked, but I did not have libtotem_mozilla.* installed.

```

 cd /opt/firefox/plugins/
 sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
 sudo rm libtotem_mozilla.*
```

This seems to have worked (it did not throw any errors) :

```
 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

And so, when did this in terminal:

```
firefox
```

FF 1.07 came up, with the default ubuntu home page (instead of my normal homepage that I had set to Google.

What am I missing?  

Since I do not have gnome or KDE installed, is it safe for me to completely remove FF 1.07 and try to install FF 1.5 ?

---

### Post by Onos on 2006-01-07
&#12420;&#12387;&#12383;&#65281;

Looks like removing FF 1.07 in its entirety has worked... the only thing that unnerves me a tad was when synaptic removed xubuntu-desktop, but apparently that is not needed.

---

### Post by Yleeyas on 2006-01-08
Being a newbie, I followed the wiki instructions "blindly" , and everything worked as advertised. Thanx for this excellent doc.

What I'd like to do is reverse the line;
#

If you want to keep the original Ubuntu icon for firefox, enter this command:

 sudo cp /usr/share/pixmaps/firefox.xpm /opt/firefox/chrome/icons/default/default.xpm
 

#

and use the Moz Firefox icon.  Can I just reverse the copy, or will I step on something? 

Also, (and this might be a FF thing) in my Windoze version of FF1.5 the 'options' settings are at the bottom of the 'Tools' menu, while this version has the 'preferences' settings (same as options)  at the bottom of the 'Edit' menu. I've got all the same extensions in both, so I don't think it's a function of one of those. Can someone confirm, deny or  clarify the difference?

Yleeyas (newbie)

---

### Post by Onos on 2006-01-08
[QUOTE=Onos]&#12420;&#12387;&#12383;&#65281;

Looks like removing FF 1.07 in its entirety has worked... the only thing that unnerves me a tad was when synaptic removed xubuntu-desktop, but apparently that is not needed.[/QUOTE]

](*,)

 Ack.  I found out that FF 1.5 will work without xubuntu-desktop package... but removing it hoses any desktop background, and the right-click context sensitive menus in the desktop area.

I tried re-installing the xubuntu-desktop package + mozilla (package for FF 1.07) but to no avail.... I now have a brown, icky screen.

I guess my best bet will be either to tough it out for another six months until Dapper Drake, or suffer the wrath of bloat-age from KDE or gnome.

---

### Post by Onos on 2006-01-08
Found a fix for this, **courtesy of Sapo** ... pressing ALT + F2 and then typing xfdesktop seems to have brought my background and context back to life.

---

### Post by ariel on 2006-01-08
[QUOTE=nozdormu]I just wanted to bring this back up.  Both this blinking menu problem and the long delay when opening a save dialog the first time are fixed in the nightlies. These were really driving me crazy, so I just downloaded the 12-21-2005 Linux nightly build from here: [http://www.squarefree.com/burningedge/]("http://www.squarefree.com/burningedge/").

Since I had used the FirefoxNewVersion wiki page to upgrade to 1.5, all I needed to do was backup my Firefox folder (the one in /opt/) and untar+unzip the new version (1.6a1) into /opt/.  I then copied my plugins over.  

Also, be sure to make a backup of your profile just in case.  Some extensions may say they are out of date so I just manually bumped up the version to 1.6 in the install.rdf files, but those Nightly Tester Tools may work (I haven't used them).  I also recommend turning off automatic updates since all I really needed was these two bugs fixed and I don't want to deal with future breakage.  Everything seems to be going fine now, and if you can live with Firefox still being called Deer Park Alpha 2 for some reason, then you may want to try it.[/QUOTE]

I fixed this one in another way. 
First I tried with  with Deer Alpha2 and it made such a mess with my extensions and stuff, that i rolled back.
I downloaded the latest 1.5 branch official build, which i found in:

[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla1.8/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla1.8/)

I think they integrated the patch for the bug in it, because all my problems vanished. Also you can simply download the binary and extract it directly over /opt/firefox, it keeps your profile, extensions etc. This did the trick for me.
Ariel

---

### Post by fishfork on 2006-01-11
[QUOTE=tripleee]
Couple of minor nits:

etc.
[/QUOTE]

tripleee, you seem to have lots of good ideas for the page. Why not register for the Wiki and make the changes yourself? I will add them myself when I get time, but I'm a little busy at the moment. Please do feel free to edit the page; this goes for anyone with something to contribute.

If you look around, there are some useful Wiki pages with tips on getting started with editing that might help you. Good luck!

---

### Post by Tosa on 2006-01-12
Thanks for the script. Everything went like charm.

I did have the issue with left lock file, but that is due to FF not the script.

I really admire the time and effort you must be putting in the whole thing...

---

### Post by Paool on 2006-01-12
Hi :)

In KDE my Firefox 1.5 is running fine, but in fvwm when i run 'firefox' command, version 1.0.7 starts :/

how to make 1.5 default in fvwm?

---

### Post by Frank Golden on 2006-01-12
Hi Guys,
   Was looking for way to update my version of Breezy Badger to FF 1.5 when I stumbled on you site. Got more than I bargained for, very cool!!!. Just what this newbie needed. Got Ubuntu set up on a 80 GB HD in my notebook (dual boot with XP Pro) almost everything works great now. Again thanks.

---

### Post by Danielle on 2006-01-13
hi, i have only read the first 4/5 pages of this thread sorry :( can i ask - if i use Automatix to install 1.5 are there the problems with libgecko, yelp and lost bookmarks which i read the script had problems with, not because of the script but because of firefox? i've never used Automatix but i'd like to try it out :smile:

---

### Post by foxiness on 2006-01-14
i can not get flash work ,

install it from synaptic flash-mozilla or by hand its the same ... opera epiphany its the same ,,, 
```

 ls /usr/lib/mozilla-firefox/plugins/
flashplayer.xpt         mplayerplug-in-qt.so   mplayerplug-in-wmp.so
libflashplayer.so       mplayerplug-in-qt.xpt  mplayerplug-in-wmp.xpt
libmozilla_bonobo.so    mplayerplug-in-rm.so   mplayerplug-in.xpt
mplayerplug-in-gmp.so   mplayerplug-in-rm.xpt
mplayerplug-in-gmp.xpt  mplayerplug-in.so

```

-----------------
```

 ls -li /opt/firefox/plugins
1819497 lrwxrwxrwx  1 root root 32 2006-01-14 15:33 /opt/firefox/plugins -> /usr/lib/mozilla-firefox/plugins

```

---

### Post by polkadotchickens on 2006-01-16
ok, so i followed the wiki and it seems to work ok.  problem: none of my bookmarks and settings and plugins imported.  i'm new at this and i might could figure it out but i'm really afraid i'll break something.  so far in trying ot fix it i've already killed it, but luckily undid everything that killed it, got it back to the original non-remembering my stuff state.  help?

---

### Post by polkadotchickens on 2006-01-16
nevermind, i got it!

woo!  go newbie!

---

### Post by tripleee on 2006-01-17
[QUOTE=fishfork]tripleee, you seem to have lots of good ideas for the page. Why not register for the Wiki and make the changes yourself?[/QUOTE]

Did so. Thanks for the nice words.

I could not quickly find out how to properly link to a page with a weird name so the link to FirefoxAMD64FlashJava looks like an external link. I guess anybody who is competent to fix that should go ahead.

---

### Post by kbunsie on 2006-01-18
I'm kinda new to Ubuntu and Linux and was just wondering why we can't just install Firefox 1.5 to */usr/lib/mozilla-firefox* instead of */opt/firefox*. When installing plugins I noticed that they get downloaded to the previous and not the latter even when I'm not using Synaptic. Also */opt/* seems to be owned by root and it causes my extensions to break. Would there be a problem with Synaptic if i installed 1.5 the way I mentioned? If that is or is not the case then I think the Wiki should be rewritten to reflect this.

---

### Post by HJB on 2006-01-21
Very good howto!
Thanks for the work!!!:KS

---

### Post by Azion on 2006-01-21
Great guide, worked perfect

---

### Post by neoflight on 2006-01-26
i followed the howto and wiki....

and my ff1.5 is still giving me trouble...i uninstalled 1.0.7 using synaptic..
i 'was' using ff1.5 from automatix and was experiencing much trouble. then i came across this howto and wiki and managed to get a new installation from mozilla...but i dont know how to remove the 'old' ff1.5 installation...

here is a snapshot of cnn front page...if u can see to the left of the page where the fonts are all messed up.....

the other thing is that sometimes if i have more than 5 or 6 tabs open then the horizontal width of the browser window goes to infinity as opposed to getting the fonts and stuff justified inside the viewing area....

help me....

---

### Post by neoflight on 2006-01-26
here is the proof of the second problem i was explaining...it happend just now with only a single tab...!!!!
look how the page is cut from the right side...there is now way i can rectify this otherthan to restart FF and copy the link?

---

### Post by PuNGS on 2006-01-26
It worked perfectly for me... I've never seen this error or something similar...

---

### Post by Rhino1 on 2006-01-26
I managed to follow the Wiki all the way through to the start "firefox" from the terminal.  Firefox did initially start, I viewed the new screen, it told me I was offline.  I clicked File>Quit.  obviously,I did something wrong... When I try to start Firefox 1.5 it tells me "Firefox is still running, and not responding, Please close Firefox or restart your computer" No joy!  I rebooted the computer several times with no effect, still get the same message.  I followed the removal scripts at the bottom of the Wiki (actually cut & pasted into my terminal) and am able to return quickly to Firefox 1.0.7.  Any help would be appreciated.:confused:

---

### Post by dimension user on 2006-01-29
Does anybody know when firefox 1.5 will be added to the repos for (semi) automatic install?  It'd be nice to have an even easier 1-click install for beginners from synaptic.

---

### Post by Rory on 2006-01-29
I believe you can install 1.5 from Automatix, although I've heard of issues with that, too.  See: [http://easylinux.info/wiki/Ubuntu#Installing_additional_software_.28Automatix.29](http://easylinux.info/wiki/Ubuntu#Installing_additional_software_.28Automatix.29)

You may want to simply try installing again from the wiki, hoping the problem doesn't crop up again.  The good thing about that is that you will then be able to get updates for it directly from Mozilla, rather than having to depend on the Ubuntu repos.

Sad, really.  Azureus is also not available on any of the repos.  I find it odd that such core programs aren't getting in to the official or unofficial repos.  I think there are some priority askew as we see Ubuntu develop.

R.

---

### Post by breezyfox on 2006-01-29
Hi 
just copied and pasted from how to guide. worked great. no errors. did't even backup my old profile. perfect guide.

bz

---

### Post by bsantos on 2006-01-30
The mozilla.org version does't read /etc/mozilla-firefox stuff. DSP isn't in the run scripts.

To have sound with aoss I changed the run-mozilla.sh to state the following when running the actual mozilla (firefox-bin) binary:

(...)
        ## Run the program
        ##
        BIN=$prog
        URL=${1+"$@"}
        PROG="$BIN $URL"
        if [[ $PROG == "/opt/firefox/firefox-bin" ]]; then
                aoss $PROG
        else
                $PROG
        fi
(...)

EDIT: I had to change it to regard when firefox is already running, now it should work well.

When is this voodoo scripting mozilla is using for so long being dropped? :evil: 


Cheers.

---

### Post by tmahmood on 2006-01-30
hi!
I don't get it! Why do you go through so much trouble! am I missing something!?
this is what I do to make FF1.5 working...

Download the tar.gz file from mozilla website...
first rename the old firefox in the bin to something else
```
sudo mv /usr/bin/firefox firefox-old
```
this will extract all the files in a folder named firefox
```
tar -xf firefox-1.5.tar.gz
```
make a directory named firefox in the /usr/share/ (expecting there is no directory named firefox there)
```
sudo mkdir /usr/share/firefox
```
copy all the files in firefox to /usr/share/firefox/
```
sudo cp -r firefox/* /usr/share/firefox/
```
now cd to /usr/share/firefox/
```
cd /usr/share/firefox
```
make a symbolic link to firefox.sh
```
sudo ln -s /usr/share/firefox/firefox /usr/bin/firefox
```

done! all your bookmarks & settings are available.. any extensions, themes you have installed in your user directory are also available. don't forget to install libstd++ 5

and if you want to use auto-update in the firefox then you need to start FF in super user mode..

```
sudo firefox
```

if I am missing something let me know
bye

---

### Post by DougInKY on 2006-02-02
Thank you very much for your clear instructions. It saved me worrying that I might have problems manually installing Firefox 1.5.0.1 although I have manually installed it many times over the years in Mandrake/Redhat/Fedora. Turns out to work the same. Somehow I was just sure that Ubuntu/Debian would be different. I get caught every once in a while by the little differences between the distros. I swear that I hear chuckles and a "gotcha' from somewhere far off in developer land each time this happens. ;) 

Doug in Kentucky

---

### Post by artik on 2006-02-03
Important notice on FF Update:

I've tryed to update FF 1.5 to FF 1.5.0.1 using suggested method

sudo firefox

It worked but afterwards I had someproblems. They where result of changing owner of several files in profile to root:root

In order to fix this I should run a command afterwards

sudo chown -R ~/.mozilla

Please update WiKi,
Thanks!

---

### Post by zodder on 2006-02-04
Thanks for a great tutorial. It worked flawlessly for me. This release makes the original ubuntu distro seem like it was running on a 486! :) Much snappier and it loads much, much faster.

---

### Post by fishfork on 2006-02-05
[QUOTE=artik]Important notice on FF Update:

I've tryed to update FF 1.5 to FF 1.5.0.1 using suggested method

sudo firefox

It worked but afterwards I had someproblems. They where result of changing owner of several files in profile to root:root[/QUOTE]

I've changed the instructions to avoid this problem, I think. (please test)

While I'm at it, I can't see any advantages of the third updating method over the second. Does anyone mind if I remove it? (The page is getting a bit long and cumbersome.)

---

### Post by Rory on 2006-02-05
I think it's probably fine to remove the third option.  

What we need, however, is a method to be automatically notified an update is available.  Then, go sudo to get the update.  

That would maintain security but still allow you to be notified when an update is available.  The best of both worlds!

By the way, thank you for your instructions.  I was really pleased to see 1.5.0.1 present itself for update last week and then to see the Extensions update, as well.  

Your instructions worked flawlessly for me.  I think it's very useful to be able to update directly from Mozilla when there's an update rather than relying on the Ubuntu package that isn't updated as often.  I hope you keep the instructions for Dapper Drake so people will always have the option of getting and updating Firefox directly from Mozilla.  I think it's a better security approach for such a critical piece of software.   That being said, it would also be nice of Ubuntu package maintainers recognized the central nature of the browser and its security implications and released packages immediately, as Mozilla released them.  SuSE maintainers do this. 

Thanks!
Rory

---

### Post by gregcUK on 2006-02-06
First off - thanks for the guide, I'm posting this from FF1.5 :)

However, along the way I ran into exactly the same problem as Rhino1:

[QUOTE=Rhino1]I managed to follow the Wiki all the way through to the start "firefox" from the terminal.  Firefox did initially start, I viewed the new screen, it told me I was offline.  I clicked File>Quit.  obviously,I did something wrong... When I try to start Firefox 1.5 it tells me "Firefox is still running, and not responding, Please close Firefox or restart your computer" No joy!  I rebooted the computer several times with no effect, still get the same message.  I followed the removal scripts at the bottom of the Wiki (actually cut & pasted into my terminal) and am able to return quickly to Firefox 1.0.7.  Any help would be appreciated.:confused:[/QUOTE]

After a bit of digging around it looks like something had gone wrong with my profiles folder - basically I had my original bookmarks etc in ~/.mozilla/firefox/*.default, but there was also a second profile inside the first one (ie I had ~/.mozilla/firefox/*.default/*.default), which I guess was confusing Firefox.

As I was unsure exactly where the problem was, I made sure I still had a backup of everything, and deleted everything except pluginreg.dat from ~/.mozilla/firefox/ then started Firefox, which created a new profile from scratch. Then, I just followed the instructions on the wiki for restoring themes and extensions, and everything worked perfectly :D

Oh - and hello by the way. I've visited here a few times before, but this is the first time I've been able to contribute. Hope it makes sense.

---

### Post by drfalkor on 2006-02-06
wtf ? when I go into [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion), I read "Install Windows Problem solved" :neutral:

---

### Post by towsonu2003 on 2006-02-06
[QUOTE=drfalkor]wtf ? when I go into [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion), I read "Install Windows Problem solved" :neutral:[/QUOTE]
vandalism by some racist guy.. reverted, try again. if borked again, you could always login / register and revert by yourself to the last known good wiki state ;)
why didn't I get an email for this I wonder - time to check my settings!

---

### Post by Maniak on 2006-02-07
Cheers for the link Fishfork.

Used the upgrade option to go from 1.5 to 1.5.0.1 without drama or issue.

This community is great!

---

### Post by kenweill on 2006-02-07
I just followed the instructions found in the Ubuntu Wiki about installing the New Version of Firefox.

Works just fine.
Typed sudo firefox, then update it to 1.5.0.1

No problem at all.

---

### Post by towsonu2003 on 2006-02-07
I just added a new section to the wiki about installing. This (3rd) section is not a proper ubuntu firefox installation but just a quick dirty install. basically, you untar it to your home, move old profile, change file permissions, and run. I used this method to run the nightly trunks until the 1.5.0.1 was issued (bugs annoying me in 1.5.0.0). 

If something goes wrong in this section and you know how to fix it, it would be great if you could just correct the wiki :)

---

### Post by Sokraates on 2006-02-12
_**Firefox 1.5.0.4 is now supported**_

Upgrading Firefox 1.5 via the menu isn't easy on linux. You need to start Firefox as root to get the menu-option. And then there's a risk, that the ownership of some of you extensions and settings will be changed to root.

Attached you will find the easy solution: ***Fireupdate***

Fireupdate is a simple script, licensed under the **GPL**, that will use Firefox' own updater to perform the update. That way, only the necessary files will be downloaded and no permissions need to be changed.

Before the update, some safety-checks will be performed and of course a backup of Firefox will be created. 

Fireupdate will work with Ubuntu and Kubuntu and **should** work with Xubuntu and Edubuntu as well.

[U][B]Attention:
[/B][/U]1.) You will need to have Firefox from [www.mozilla.com]("http://www.mozilla.com") installed to /opt/firefox. 
     So Fireupdate will **not** work with the version included in Dapper Drake.
2.) At this time, Fireupdate will update the US-version **only**.

**_How to use:_**
Download the script you need, depending on whether you have Firefox 1.5, 1.5.0.1, 1.5.0.2 or 1.5.0.3 installed.

You can find your version by opening Firefox and clicking on "Help" and "about Firefox".

Then simply extract the tarball to your home directory and doubleclick on "Fireupdate".
[U][B]
Contribution:
[/B][/U]Any contribution concerning localization and coding is welcome. Especially for creating a version-check. Please read the comments in the scripts and don't forget to update the information in the main script.

[U]**What's new in 1.5.0.4:**
[/U][Official list of fixed vulnerabilities]("http://www.mozilla.org/projects/security/known-vulnerabilities.html#firefox1.5.0.2")


 ***Fireupdate 1.3, from  1.5:***       [ATTACH]10857[/ATTACH]

*** Fireupdate 1.3, from  1.5.0.1: ***[ATTACH]10858[/ATTACH][I][B]

Fireupdate 1.3, from  1.5.0.2: [/B][/I][ATTACH]10859[/ATTACH][I][B] 

Fireupdate 1.3, from  1.5.0.3: [/B][/I][ATTACH]10860[/ATTACH]

---

### Post by Sokraates on 2006-02-13
Oups! Just noticed that I accidently named the thread "easiliy **upgrade** Firefox" instead of "easily **update** Firefox". 

Could a moderator please change this? Thanks.

---

### Post by BoneKracker on 2006-02-13
I tried Fasterfox and ditched it.  While I didn't do any real tests, I didn't notice any real speed difference, but I did notice it was hogging bandwidth and cpu cycles as it prefetched everything in sight.  If everybody used Fasterfox (or Google's prefetching system), I think we'd probably have the opposite effect and actually slow things down by bogging down the circuits with wasted packets full of stuff we never even looked at.

---

### Post by Sokraates on 2006-02-13
For safely updating your Firefox 1.5 (en-US) to 1.5.0.1, look here:

[http://www.ubuntuforums.org/showthread.php?t=128806](http://www.ubuntuforums.org/showthread.php?t=128806)

---

### Post by cjm5229 on 2006-02-13
That worked great, I have been trying to figure out how to update firefox every since 1.5.0.1 came out. Thanks.

---

### Post by manicka on 2006-02-13
[QUOTE=Sokraates]
Could a moderator please change this? Thanks.[/QUOTE]

np :)

---

### Post by Robor on 2006-02-13
Worked like a charm.  Thanks manicka!

NOTE:  Make sure you close Firefox before launching the updater.

---

### Post by Sokraates on 2006-02-13
Fireupdate will check, whether Firefox is launched and display a pop-up, if needed.

---

### Post by dabear on 2006-02-13
> # For Developers: As you can see, I prefer KDE to GNOME.
# 			    If you know a way to make Fireupdate recognize
#			    the desktop-manager used, please let me know.

Look at DESKTOP_SESSION environment variable 
> 
bjorninge@ubuntuBreezy:~$ env | grep DESKTOP_SESSION
DESKTOP_SESSION=gnome
GNOME_DESKTOP_SESSION_ID=Default


---

### Post by bierpullen on 2006-02-13
Worked like a charm. Thanks  \\:D/ 




------------------------------------------


Acer laptop 1522, 528mb, AMD 64 3000, 64mb Nvidia.
[http://www.antarctica-rbak.nl/ubuntu](http://www.antarctica-rbak.nl/ubuntu)

---

### Post by towsonu2003 on 2006-02-14
recently updated the wiki page, so that there is only one way to update, which does not use sudo, thus not causing the file ownership issues in profile in /home when sudo is used to update.

---

### Post by chris86wm on 2006-02-15
thank you, thank you, THANK YOU!!!! \\:D/

---

### Post by goombah88 on 2006-02-15
seems like i'm the only one this didn't work for.

it acted like it was going fine for a while.  it downloaded the file, then failed.

14:25:54 (308.83 KB/s) - `firefox-1.5-1.5.0.1.partial.mar' saved [623900]

this is the output in the terminal:

/home/goombah/Desktop/Fireupdate: line 139: 10162 Killed                  zenity --progress --pulsate --title "Fireupdate" --text "Downloading update. This may take a few moments."  (wd: /opt/firefox-update)


any help?

---

### Post by Technoviking on 2006-02-15
I'm having a slight problem.

When trying to run /usr/bin/mozilla-firefox, I get the following
```
run-mozilla.sh: Cannot execute /opt/firefox/mozilla-firefox-bin.
```
Even though I have /usr/bin/mozilla-firefox link to /opt/firefox/firefox

/usr/bin/firefox works fine, but thunderbird wants /usr/bin/mozilla-firefox (yes, /usr/bin/firefox is set in Preferred Applications)

Thunderbird is using what '*sudo update-alternatives --config x-www-browser*' point to

When running sudo update-alternatives --config x-www-browser, I get two choices
```
  Selection    Alternative
-----------------------------------------------
*     1        /usr/bin/mozilla-firefox
 +    2        /usr/bin/konqueror
```

Any ideas?

Mike

---

### Post by towsonu2003 on 2006-02-15
[QUOTE=Mike Basinger]
Thunderbird is using what '*sudo update-alternatives --config x-www-browser*' point to

When running sudo update-alternatives --config x-www-browser, I get two choices
```
  Selection    Alternative
-----------------------------------------------
*     1        /usr/bin/mozilla-firefox
 +    2        /usr/bin/konqueror
```
[/QUOTE]
There is a nice application you could use for solving this, though I'm not sure how good it will work. trying won't hurt, as this is a gui thingy.
```

sudo apt-get update
sudo apt-get install galternatives
gksudo galternatives
```scroll down to and choose x-www-browser and click on Add, and add whatever application (and whereever it is) you want. let us know, as I am curious about whether this will work. thanks.

---

### Post by Technoviking on 2006-02-15
No joy:(.

Mike

[QUOTE=towsonu2003]There is a nice application you could use for solving this, though I'm not sure how good it will work. trying won't hurt, as this is a gui thingy.
```

sudo apt-get update
sudo apt-get install galternatives
gksudo galternatives
```scroll down to and choose x-www-browser and click on Add, and add whatever application (and whereever it is) you want. let us know, as I am curious about whether this will work. thanks.[/QUOTE]

---

### Post by udha on 2006-02-16
[QUOTE=Imrahil]What is going on here is that ubuntu's firefox changed its config to better match windows behavior (middle click closes tab) whereas unix default behavior is middle click loads clipboard contents. The new firefox no longer as the ubuntu specific tweaks.

To change this or any other behavior setting in firefox type this url:

about:config


then search for middlemouse.contentLoadURL
make sure value is set to false.

Neat huh?[/QUOTE]


THANK YOU!

I had everything else working, but the middle-click close was acting strangly and I didn't know where to turn, I was finding it hard to surf the way I'm used to without the 'middle-click close'

---

### Post by Sokraates on 2006-02-16
Hmmm ... it looks as if the progressbar was killed together with wget. The update mar-file should be about 600 kb.

Try again and if nothing works, see if /opt/firefox-update is created and the files "updater" and "updater.ini" are copied there already (they sould be, if not, copy them manually from /opt/firefox). 

Then download the update-file manually, rename it to "update.mar", cd to /opt/firefox and run
```
 /opt/firefox-update/updater /opt/firefox-update 0
```

---

### Post by goombah88 on 2006-02-16
[QUOTE=Sokraates]Hmmm ... it looks as if the progressbar was killed together with wget. The update mar-file should be about 600 kb.

Try again and if nothing works, see if /opt/firefox-update is created and the files "updater" and "updater.ini" are copied there already (they sould be, if not, copy them manually from /opt/firefox). 

Then download the update-file manually, rename it to "update.mar", cd to /opt/firefox and run
```
 /opt/firefox-update/updater /opt/firefox-update 0
```[/QUOTE]


thanks for the help sokraates, but i already got it taken care of.  i checked and the latest automatix version 5.4-2 installs firefox 1.5.0.1.  the only thing is you have to copy over the bookmark folder and reinstall your extensions.

so for anyone else who used automatix to install firefox 1.5 this may be the route for you.

---

### Post by Sokraates on 2006-02-16
The difference between Fireupdate and Automatix is, that Automatix will perform a new install of Firefox. For safety measures you will have to do some restoring, since Automatix does not know wich version you had installed before.

Fireupdate on the other hand will perform an update from Firefox 1.5 to 1.5.0.1 so you can avoid the restoring. Then again it will only work with Firefox 1.5 from [www.mozilla.org](www.mozilla.org). ;)

---

### Post by cjm5229 on 2006-02-16
[QUOTE=Sokraates]The difference between Fireupdate and Automatix is, that Automatix will perform a new install of Firefox. For safety measures you will have to do some restoring, since Automatix does not know wich version you had installed before.

Fireupdate on the other hand will perform an update from Firefox 1.5 to 1.5.0.1 so you can avoid the restoring. Then again it will only work with Firefox 1.5 from [www.mozilla.org](www.mozilla.org). ;)[/QUOTE]
 
It worked fine for me, and I installed Firefox with Automatix. \\:D/

---

### Post by YourSurrogateGod on 2006-02-17
Sorry if this was mentioned before, but has anyone had problems with flash?

---

### Post by Sokraates on 2006-02-18
[quote=cjm5229]It worked fine for me, and I installed Firefox with Automatix. \\:D/[/quote] 
Automatix uses the tarballs from [www.mozilla.com]("http://www.mozilla.com") and installs FF to /opt/firefox. So Fireupdate will **always** work with such an installation.

---

### Post by Sokraates on 2006-02-19
_**Fireupdate 1.0 is out!**_

Fireupdate will now work without a terminal. A simple doubleclick will do the trick.

To download the new script, please see the first post in this thread.

---

### Post by steveneddy on 2006-02-19
Why doesn't one open a terminal, open Firefox as Root:

# sudo Firefox

When Firefox opens, go to the "Help" tab on the browser, click the now highlighted "Check for Updates" button, & let Firefox update itself. 

After you update Firefox, restart Firefox _again_ as Root:

# sudo Firefox

...so it will "take" the update.

This is the recommended way to update Firefox. 

Afgter you are done with the update, close Firefox, close terminal window and open Firefox in the normal fashion. You should have the 1.5.01 Firefox.

---

### Post by Sokraates on 2006-02-19
[quote=steveneddy]Why doesn't one open a terminal, open Firefox as Root:
[...]
This is the recommended way to update Firefox. 
[/quote]

Nope. It's **not **recommended, since you risk changing the ownership of your extensions to "root".

The correct way is to start Firefox both times with
```
sudo firefox -safe-mode
```
so that no extensions will be loaded.

You are right, in that the update can be done otherwise and through Firefox' menus. But Fireupdate is for all the users who don't want to use a terminal or remember to start Firefox two times as root. Rather they should just click on an icon and be done.

---

### Post by funchords on 2006-02-19
[QUOTE=Sokraates]_**Fireupdate 1.0 is out!**_

Fireupdate will now work without a terminal. A simple doubleclick will do the trick.

To download the new script, please see the first post in this thread.[/QUOTE]

Hi there,

Thanks for this.  However, this was the first trick I tried after a fresh, default install of 5.10 which comes with Firefox 1.0.7

First question was where to unarchive it?  It really didn't seem to matter because all paths (/tmp/* ~/* and even /opt/firefox-updater/*) eventually led to the same result:

[FONT="Fixedsys"]/opt/firefox-update/updater: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory[/FONT]

So either that's not installed, not in the path, or ... most probably ... pilot error :-)

 -- Robb (still trying to get used to *sudo* in front of everything) ...

---

### Post by funchords on 2006-02-19
[QUOTE=steveneddy]Why doesn't one open a terminal, open Firefox as Root:

# sudo Firefox

When Firefox opens, go to the "Help" tab on the browser, click the now highlighted "Check for Updates" button, [/QUOTE]

Did you mean **Help Menu** item or **Help Tab**?

I didn't see a Help Tab, and I didn't see a (button?) on the Help Menu.  I did see such a choice in the Edit / Preferences / Advanced menu, but it did not return any updates: Firefox was not able to find any available updates.

This is with the Firefox 1.0.7 version that is installed by default on 5.10.

---

### Post by Sokraates on 2006-02-19
[quote=funchords]Hi there,

Thanks for this.  However, this was the first trick I tried after a fresh, default install of 5.10 which comes with Firefox 1.0.7

First question was where to unarchive it?  It really didn't seem to matter because all paths (/tmp/* ~/* and even /opt/firefox-updater/*) eventually led to the same result:

[FONT=Fixedsys]/opt/firefox-update/updater: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory[/FONT]

So either that's not installed, not in the path, or ... most probably ... pilot error :-)

 -- Robb (still trying to get used to *sudo* in front of everything) ...[/quote] 
As far as I understand, you don't even have Firefox **1.5** installed. Fireupdate will work with Firefox 1.5 **only** since older versions didn't even have an update mechanism.

To install Firefox 1.5.0.1 in english, best use [Automatix]("http://www.ubuntuforums.org/showthread.php?t=66563"), for other languages take look at [this excellent HOW-TO]("http://www.ubuntuforums.org/showthread.php?t=79283").

By the way: Fireupdate should be extracted to your home-folder, that is "~/".

---

### Post by funchords on 2006-02-19
Aha! I knew it had to be something simple.  Thanks!

---

### Post by Delphinus on 2006-02-20
Nice tutorial, much appreciated, and I notice that 1.5 is quite a bit faster than 1.0.7

BUT
My DNS has since seemed to have broken itself... as a direct result of following these instructions. 

I noticed as son as i loaded up FF1.5 for the first time it took a long time to find "google.com" but didn't think much of it, but its been getting mostly worst in the last day.

It has appeared to break things system wide, yet somewhat randomly.
Like nslookup on an address mostly times out, then will randomly start working. 
FF will either take a VERY long time to lookup the domain, or time out completely. I'll then refresh and i'll either time out again or work after a little while. 
Once its looked up the domain pages within that domain work awesomely fast.
But as soon as i hit another domain, either typing or a link, we have a huge delay again.
Browsers like konqueror have the same error.

This has only started happening since installing 1.5

Any Ideas?
Thanks, Delph

---

### Post by bman on 2006-02-22
I need alot of help here....nothing is working....I followed tutorials..

Can someone, stepbystep explain how to update from 1.07 to 1.5

Abit of a newbie to linux..

---

### Post by bman on 2006-02-22
It says I don't have permission to access /opt

---

### Post by towsonu2003 on 2006-02-22
[QUOTE=bman]It says I don't have permission to access /opt[/QUOTE]
don't forget the sudo in:
[quote=wiki]#

Install it to /opt/firefox:

 # extract tar into /opt (you should make sure /opt already exists)
 **sudo** tar -C /opt -x -z -v -f firefox-1.5.0.1.tar.gz
 # remove the package if you no longer require it
 rm firefox-1.5.0.1.tar.gz
[/quote]

---

### Post by bman on 2006-02-23
it says sudu cant find command or something like that...

---

### Post by Perfect Storm on 2006-02-23
It's **sudo**

---

### Post by towsonu2003 on 2006-02-23
[QUOTE=bman]it says sudu cant find command or something like that...[/QUOTE]
pls copy paste what u type and what it says (from the terminal to here)

---

### Post by YourSurrogateGod on 2006-02-23
[You can try to install Automatix and have it do what you need for you.](http://easylinux.info/wiki/Ubuntu#Installing_additional_software_.28Automatix.29)

---

### Post by jvnn on 2006-02-24
ARGHHH!!
Where the wiki says:

>Try it out: :-)
>firefox

 >#Restore your old data:
 >cd ~/Desktop/ffsettings
 >mv * ~/.mozilla/firefox/*.default

I started firefox from the panel icon, then restored my old data, then closed firefox.
2 guesses what happened to my huge collection of bookmarks!
ARGHHH!!

---

### Post by dvarsam on 2006-02-27
Hello ALL:

This is a gift from ME to ALL of you !!!

_Tutorial - How to Install Mozilla Firefox 1.5.0.1_:

_For Ubuntu 5.10_:

_Source_:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

_Note_:
Even though, the commands found below, are (almost) the same like those found in the above "Source" Internet Page, you will find that it is easier to install "Firefox 1.5.0.1" with the method shown below.

What I basically do, is I create ONE Script file & type ONLY ONE command in the Terminal.

Unfortunately, the method suggested in the above "Source" Internet Page, requires that YOU type each & EVERY command (one-by-one) in the Terminal.

... and if you make any "typo" mistakes:

a. You might mess up everything & an install might NEVER work out for you,

OR:

b. If you are lucky, you are just going to have to retype the command until you get it right.

However, my method is much more better, because if you EVER decide to Format Your Ubuntu again, you will only have to type ONE command, as opposed to many...


So, Here it goes:


_Part 1 – Backup your Bookmarks_: 
Before you start, make sure you Backup your "Bookmarks" or there is a chance that you might loose them...
To do this, perform the following:

1. Launch a Mozilla Firefox window.

2. From the Menu, select "Bookmarks\Manage Bookmarks"

3. From the New window that pops up, from the Menu select "File\Export"

4. Click on the button named "Save" & your "Bookmarks" will be saved on the 
    Desktop.

Congratulations, your "Bookmarks" Backup (file: "bookmarks.html"), was performed successfully.


_Part 2a – Install your Mozilla Firefox 1.5.0.1_: 
To Install, perform the following steps:

1. Visit the site:

	[http://www.mozilla.com/firefox/](http://www.mozilla.com/firefox/)

2. Click on the link named "Download Firefox" to download your Mozilla Firefox 
    1.5.0.1.
    Save it on your Desktop folder (mine is "/home/dimitris/Desktop")

3. From your Ubuntu's Menu, select "Applications\Accessories\Text Editor"

4. From the Text Editor's Menu, select "File\Save As"

5. Delete the name suggested "Unsaved Document 1" & type the name 
    "installfirefox.sh".

6. Under the "Save in Folder:", instead of "Home" select "Desktop".

7. Click on the button named "Save"

8. Copy & Paste the following text inside your Text Editor opened file (e.g. 
    "installfirefox.sh").

	#!/bin/bash

	## How to install the latest Firefox 1.5.0.1 Internet Browser:
	##
	## Source: "https://wiki.ubuntu.com/FirefoxNewVersion"

	## First download the file "firefox-1.5.0.1.tar.gr" to your Desktop.

	## Then run this file from the Terminal with the command "sh installfirefox.sh"


	cd /

	cd /home/dimitris/Desktop


	## The following command un-zips your downloaded file to inside your folder 
	## named "/opt". 

	sudo tar -C /opt -x -z -v -f firefox-1.5.0.1.tar.gz


	cd /

	cd /opt/firefox/plugins

	## The following command removes "totem-mozilla" because it does NOT 
        ## work with the program you are trying to install (Firefox 1.5).

	sudo ln -s /usr/lib/mozilla-firefox/plugins/* .

	## For some reason I could NOT remove the following (as required):

	# sudo rm libtotem_mozilla.*


	cd /

	cd /home/dimitris

	## Rename your old profile in your "/home/dimitris" directory, leaving it as
	## a Backup:


	mv .mozilla/firefox .mozilla/firefox1.0.x.ubuntu


	## We modify the symbolic link in "/usr/bin", to ensure that the NEW Firefox 
	## is used as the default version:


	## 1. First, we modify the old Firefox in the "/usr/bin/firefox":

	sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
	
	sudo ln -s /opt/firefox/firefox /usr/bin/firefox


	## 2. Then, we modify the NEW Firefox in the "/usr/bin/mozilla-firefox" (it 
	##    will be used as the default gnome browser):

	sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox

	sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox


	## The "dpkg-divert" command moves the OLD system-wide "/usr/bin/firefox" 
        ## to a new name.

	## The "ln" command places a symbolic link to the newly installed Firefox in 
	## "/usr/bin". 


	## Congratulations, you have now installed successfully your Mozilla Firefox 
	## 1.5.0.1 Internet Browser.

	## Go & Check it out !

9. In the above part that you Copied & Pasted, you MUST replace wherever you 
    see the word "dimitris", with YOUR name (e.g. the username you type every 
    time you boot your computer – mine is "dimitris").

10. When finished, from the Text Editor's Menu, select "File\Save" & then again 
      "File\Quit".

11. From your Ubuntu's Menu, select "Applications\Accessories\Terminal"

12. Inside the Terminal, type "sudo -i", to get root privileges. 

13. Then type your Password.

14. Then type "cd /home/dimitris/Desktop" while replacing the "dimitris" with YOUR 
      username (e.g. the username you type every time you boot your computer – 
      mine is "dimitris").

15. Type the command "sh installfirefox.sh" to Run your Script file, named 
      "installfirefox.sh".

Congratulations, you have successfully installed Firefox 1.5.0.1 in your Ubuntu PC.

To test whether it works OK, launch a Mozilla Firefox window & surf around.
Alternatively, from within your Mozilla Firefox's window select "Help\About Mozilla Firefox".
The version stated in the new window should be v1.5.0.1.


_Part 2b - Removing your Mozilla Firefox 1.5.0.1_:
If for some reason you want to undo the installation & revert back to the standard Firefox 1.0.7, perform the following:

1. Part 2: steps 3 & 4.

2. Part 2: step 5, replacing "installfirefox.sh" with "restorefirefox.sh"

3. Part 2: steps 6 & 7.

4. Part 2: step 8, only this time, type the following:

	#!/bin/bash

	## How to Restore your OLD Firefox Internet Browser:
	##
	## Source: "https://wiki.ubuntu.com/FirefoxNewVersion"

	## Run this file from the Terminal with the command "sh restorefirefox.sh"

	cd /

	cd /home/dimitris/Desktop


	## Restore the symbolic link: 

	sudo rm /usr/bin/firefox
	
	sudo dpkg-divert --rename --remove /usr/bin/firefox


	## Restore your old profile:
	## (This is different to what the "Source" Site suggested – the "Source's" 
        ##  site version, created errors).

	cd /home/dimitris/.mozilla

	mv firefox firefox1.5.0.1

	mv firefox1.0.x.ubuntu firefox

	## (optional) Delete the firefox directory 

	sudo rm -r /opt/firefox


	## Congratulations, you have now Restored successfully your OLD Mozilla 
	## Firefox Internet Browser.

	## Go & Check it out ! 

5. In the above part that you Copied & Pasted, you MUST replace wherever you 
    see the word "dimitris", with YOUR name (e.g. the username you type every 
    time you boot your computer – mine is "dimitris").

6. Part 2: steps 10 - 14.

7. Part 2: step 15, replacing "sh installfirefox.sh" with "sh restorefirefox.sh"

Congratulations, you have successfully removed Firefox 1.5.0.1 from your Ubuntu PC.


_Part 3 – Re-install your Bookmarks_: 
To do this, perform the following:

1. Part 1: steps 1 & 2.

2. Part 1: step 3, replacing "File\Export" with "File\Import"

3. Click on the button named "Next".

4. On the right-hand side, click on the button named "Desktop".

5. Scroll down to locate the file named "bookmarks.html" & select it.

6. Click on the button named "Open".

7. From the Menu, select "File\Close".

Congratulations, you have successfully installed ALL your "Bookmarks" to your Firefox 1.5.0.1 in your Ubuntu PC.


_Conclusion_:
Backup the files lying on your Desktop:

1. The downloaded Mozilla Firefox 1.5.0.1 program

2. The file named "installfirefox.sh" you created in this Tutorial

3. The file named "restorefirefox.sh" you created in this Tutorial (if you decided to 
    remove Firefox 1.5)

4.  The file named "bookmarks.html" (your Bookmarks Backup), you created in this 
     Tutorial.


_Advantages_:
If you ever have to Format your Hard Drive & Re-install Ubuntu, you only have to perform "Part 2: steps 11-15", to install your Mozilla Firefox 1.5.0.1.
At the same time, this Install file ("installfirefox.sh"), would work great if you had to install Firefox 1.5.0.1 on multiple PCs.

That was pretty Quick & Neat, wasn't it?

_Note_:
You will probably wonder why there is NO ".deb" file to install, from the "Synaptic Package Manager" or from the "Terminal" (with a command like "dpkg -i package_name.deb")...
To learn why, read the following Ubuntu Forum's thread:

	[http://ubuntuforums.org/showthread.php?t=96595](http://ubuntuforums.org/showthread.php?t=96595)


Have Fun !!!

P.S.1> I hope I have no bad grammar syntax (& repetitions), but I have spent 
           more than 4 hours to create this... 

P.S.2> I would appreciate if somebody has something to Add that corrects me if I 
           have performed a mistake.

           PLEASE do NOT add comments like "thanks dude", or "that's how you do it" 
           because people that want to read a Tutorial, end up reading comments of 
           NO Learning value.
           Thanks !!!

---

### Post by VCSkier on 2006-03-02
sorry if this is a dumb question, but should future updates work naturally (without fireupdate)?  or, should i install fireupdate now just so i can be aware and easily update to future versions?  i am currently running version that i installed via Automatix.  thanks

---

### Post by Sokraates on 2006-03-02
Updates already work using the menu-option in Firefox. The problem is, that you need to start Firefox as root and run the risk of changing ownership of some files. For details on how to update manually, look [https://wiki.ubuntu.com/FirefoxNewVersion]([URL="https://wiki.ubuntu.com/FirefoxNewVersion")]here[/URL].

Fireupdate currently **only** updates FF 1.5 to FF 1.5.0.1. For future updates I will need to include a version-check, since it will be possible to update from 1.5 or 1.5.0.1. I just don't how to do it, yet. ;)

On a sidenote: Fireupdate is not installed, but only extracted. So if you remove the folder, Fireupdate is completely gone from your system.

---

### Post by jvnn on 2006-03-11
I'm having problems with flash too.

---

### Post by kyutums on 2006-03-11
I followed the instructions with a new install of Ubuntu 5.10. Firefox works quite well now. However, my bookmarks don't get saved. When I place a bookmark, it's not there anymore when I close and start Firefox again. Any tips on how I can resolve this?

---

### Post by steveneddy on 2006-03-12
[QUOTE=Sokraates]Nope. It's **not **recommended, since you risk changing the ownership of your extensions to "root".

The correct way is to start Firefox both times with
```
sudo firefox -safe-mode
```
so that no extensions will be loaded.

You are right, in that the update can be done otherwise and through Firefox' menus. But Fireupdate is for all the users who don't want to use a terminal or remember to start Firefox two times as root. Rather they should just click on an icon and be done.[/QUOTE]


I stand corrected, thank you.

---

### Post by steveneddy on 2006-03-12
[QUOTE=funchords]Did you mean **Help Menu** item or **Help Tab**?

I didn't see a Help Tab, and I didn't see a (button?) on the Help Menu.  I did see such a choice in the Edit / Preferences / Advanced menu, but it did not return any updates: Firefox was not able to find any available updates.

This is with the Firefox 1.0.7 version that is installed by default on 5.10.[/QUOTE]


OK....Click "Help" and then Click "Check for updates". Does it need to get any easier. And whats the difference anyway. It is a button, no matter what it looks like.

---

### Post by Sokraates on 2006-03-13
There is a difference between a menu-option and a tab. Anyway, funchords' problem was, that he didn't have FF 1.5 installed in the first place. ;)

---

### Post by Sokraates on 2006-03-13
It looks as if the permissions or the ownership have been changed. Take a look at bookmarks.html (I believe thats the name) in your profile. If the ownership is set to "root", change it with
```
sudo chown -R *yourusername*:*yourusername* ~/.mozilla/firefox/*yourprofile*
``` This will affect the whole profile, since usually a few files are changed.

If you don't have write-permission, type 
```
sudo chmod 660 ~/.mozilla/firefox/*yourprofile*/bookmarks.html
``` This command will only affect the bookmark-file.

---

### Post by Benchrest on 2006-03-13
Sorry if this has already been addressed, (i read the first 8 pages and probasbly should read the rest) but I installed Firefox 1.5 last night on my laptop. The reason I did was I have FF 1.5 on our other operating system and my wife loves it with a particular theme. The Theme is only availible on 1.5 . I thought it would be good to make Ubuntu look the same for her, besides it being faster. First time I installed it, the firefox command from terminal was not recognized. I backed up through my commands and found a typo. Then it started once, but not again even after reboot it said firefox was already running and I had to stop it before restarting. After some looking I could not find the error so I started the install from after downloading the tar. This time it works. But I could not restore my saved bookmarks etc. Said it could find the file on the desktop.  I was looking at my desktop folder and clicked on the ff* folder (don't remember the exact name.) and all of a sudden like I was clicking on things my desktop icons started disappearing one at a time untill they were mostly gone including my FF folder. Not in the trash bin Don't know what happened, but I would guess the directions were ok, just I had to many typo's and something else? 

Anyway my question is, would it be possible when a person creates a write up on how to install ff or any other product, a command file of some kind could be created that us senile old folks could down load with all the commands I had to type?Would minimize finger checks and make the installation easier like for that other operating system. I realise it would work if a person had modified their system but most of us that don't know much are pretty stock. Just an idea. It will be tomorrow night before I get back to the laptop, will try to read more post before then.

---

### Post by Xilon on 2006-03-14
I followed through the steps and it worked great!!... the second time :P, but now the Package Manager wants me to "update" to the 1.0.7 ubuntu version... any ideas how to get rid of this? (I'm pretty new to ubuntu btw)

Edit: Seems like some dependencies are broken... ubuntu-desktop, yelp etc need firefox and it shows up as uninstalled :(

---

### Post by towsonu2003 on 2006-03-14
[QUOTE=Xilon]Seems like some dependencies are broken... ubuntu-desktop, yelp etc need firefox and it shows up as uninstalled :([/QUOTE]
I would say first do these: 
```

cp .mozilla/firefox .mozilla/firefox.backup
# First, /usr/bin/firefox
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
# Then, /usr/bin/mozilla-firefox, used as the default gnome browser
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
```

then let the package manager download firefox 1.0.7 and install it. firefox shouldn't be removed. 

then do these: 
```
# First, /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
# Then, /usr/bin/mozilla-firefox, used as the default gnome browser
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

```

don't launch firefox in the process. This should fix it, as you will have firefox 1.0.7 installed (for dependencies) as well as 1.5 default browser (for enjoyment).

PS. Almost all commands are from the wiki page.

---

### Post by Xilon on 2006-03-15
I think it worked, thanks a lot! :)

---

### Post by OfficeLinebacker on 2006-03-16
hey guys

I was trying to follow the directiosn here:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

And when I try to install 
libstdc++5

, 

It asks for the cdrom.

The thing is, after I set up the system, I removed the cdrom and am just running on the HD (need the CDROM to set-up other systems).

How do I get the package manager to not expect there to be a cdrom drive?

Thanks

---

### Post by towsonu2003 on 2006-03-16
[QUOTE=OfficeLinebacker]hey guys

I was trying to follow the directiosn here:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

And when I try to install 
libstdc++5

, 

It asks for the cdrom.

The thing is, after I set up the system, I removed the cdrom and am just running on the HD (need the CDROM to set-up other systems).

How do I get the package manager to not expect there to be a cdrom drive?

Thanks[/QUOTE]
Do you have internet connection?

If you have internet connection -> open synaptic, choose options (or similar)>repositories and 'un-check' the first repo, which should mention a cdrom. some of the other repos in that list should be checked so that you can install stuff. search the forums or the wiki for 'package management' for those repos. anyway, assuming you have repos enabled, hit ok than tell it to reload the repos. search for libstdc-blabla and check it to install. 

if you do not have internet connection -> you cant install stuff using apt-get unless it's in the cdrom or a local repository. put in the cdrom, make sure it is mounted, and try installing libstdc-blabla again.

---

### Post by OfficeLinebacker on 2006-03-16
I do have internet, I'm posting from the computer now.

Perhaps I can just edit the file?  I have already edited the file that apt-get uses to enable multiverse, etc.  Can I just comment out the part about cdrom?

---

### Post by OfficeLinebacker on 2006-03-16
OK, got it.  Edited sources.list, then followed the directions.  Only my bookmarks didn't get imported, but I only had two of interest :)

---

### Post by firepol on 2006-03-20
I followed the guide and installed firefox 1.5.0.1 accordingly. I use Kubuntu Breezy.

My problem is that when I have firefox already open and I click again on the firefox icon, instead of opening a new tab in firefox instance that is already running, it tries to open a new firefox instance. No, worse: it opens a new firefox instance AND it tries to open a new one. So I see my actual firerox instance + a new one + it loads a new one and it takes about 10 seconds or more and the 3rd one is closed at the end.

This is a wrong behaviour.

I configured the firefox "Preferences" > Tabs:

Open links from other applications in: (checked) a net tab in the most recent window

(checked) Force links that open new windows to open in: (checked) a new tab

(checked) Select new tabs opened from links


Expected behaviour:

I expect that if firefox is already open when i click the firefox icon, it will load a new tab in the instance that is already running. I dojn't want the system to load a new firefox instance (a new window).

Did somebody of you experience the same problem? If yes, how to fix it? Should this be reported as firefox bug or it's ubuntu?

---

### Post by Footer on 2006-03-20
> Expected behaviour:

I expect that if firefox is already open when i click the firefox icon, it will load a new tab in the instance that is already running. I dojn't want the system to load a new firefox instance (a new window).

Did somebody of you experience the same problem? If yes, how to fix it? Should this be reported as firefox bug or it's ubuntu?

I have FF 1.5 installed and when I click on the FF icon, a new window opens regardless of whether I have another instance of FF open or not.  I believe this is expected behavior.  Not sure if there's any way to change it or not.  But it's Linux so maybe!

:)

---

### Post by towsonu2003 on 2006-03-20
[QUOTE=firepol]
I configured the firefox "Preferences" > Tabs:

Open links from other applications in: (checked) a net tab in the most recent window

(checked) Force links that open new windows to open in: (checked) a new tab

(checked) Select new tabs opened from links


Expected behaviour:

I expect that if firefox is already open when i click the firefox icon, it will load a new tab in the instance that is already running. I dojn't want the system to load a new firefox instance (a new window).

Did somebody of you experience the same problem? If yes, how to fix it? Should this be reported as firefox bug or it's ubuntu?[/QUOTE]
Sorry, that's not exactly wrong behavior... your options work when you click on a link that is supposed to be opened in a new firefox window (except popups via ?javascript?). with your option, if firefox is running, that link will be opened in a new tab in the current firefox. 

when you click the firefox icon, you're basically telling the thing to "open a new firefox window", regardless of the options... 

it's like right clicking on a link in current firefox and telling the browser to open the link in a new window, when new tab option is selected. It will open a new window :)

---

### Post by aysiu on 2006-03-27
**News**:
This project has been adopted by *nanotube* who has greatly improved the script. Here are some of the changes:
1. If there's an error or a failed command, the script quits without executing the other commands
2. The script checks to see if you already have a Firefox settings folder
3. The script checks to see what the latest version of Firefox is (when I first wrote the script, it was 1.5.0.1--as of this revision, it's 1.5.0.3, but the script will check even if it's 1.5.0.4 or 2.0)
4. The script will ask what locale you want (Spain, UK, US, etc.)

*nanotube*'s script can be found [here](http://www.psychocats.net/ubuntu/installnewfirefox.sh). Download it to your desktop. Then paste these three commands in the terminal: ```
cd ~/Desktop
chmod +x installnewfirefox.sh
./installnewfirefox.sh
```

**Disclaimers and Context for this HowTo**: There are a lot of ways to install the newest Firefox in Ubuntu...

You can install it manually with a lot of copied and pasted commands from this tutorial:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

There's also [Automatix](http://www.getautomatix.com/), which is a little more involved. It installs Firefox but can install a lot more also.

**So what does this script do, and how is it different?**
Well, first of all, it's a little less invasive than Automatix. It doesn't touch your sources.list. It doesn't really do much at all to your Ubuntu installation. It's not a huge commitment.

It also tries to be as automated as possible but requires a little bit of command-line in the beginning. This gives you the advantage of not having to copy and paste a lot of commands. It gives me the advantage of not having to walk you through pointing here, clicking there, etc.

The script is based on the Wiki Firefox entry, but it's a little bit different. The Wiki Firefox entry tries to back up individual parts of the profile (bookmarks, extensions, etc.) separately. I haven't found this necessary in most cases, so my script basically just backs up the entire Firefox user profile. The uninstall script (in the link below) restores the backup my original script created--not the one from the Wiki.

I also have a slightly easier-to-remember page dedicated to *nanotube*'s script: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by CompShrink on 2006-04-08
Ah, I was considering making something like this and suggesting adding it to the Breezy addon cd. Do you think it would be a good addition?

---

### Post by aysiu on 2006-04-08
[QUOTE=CompShrink]Ah, I was considering making something like this and suggesting adding it to the Breezy addon cd. Do you think it would be a good addition?[/QUOTE] Sure. Why not?

---

### Post by Ensnared on 2006-04-08
I took the liberty of modifying your scripts so one can do the same thing for installing Thunderbird 1.5 :)

The actual process is just slightly different, the differences are that the old Thunderbird uses ~/.mozilla-thunderbird while the new one uses ~/.thunderbird. This script will create a symlink, ~/.thunderbird, pointing to ~/.mozilla-thunderbird. Also, only one symlink is created in /usr/bin (mozilla-thunderbird). There's also some symlinking being done just within the thunderbird directory to fix the differences in filenames in Ubuntu (where it's named mozilla-thunderbird) and vanilla Thunderbird (where it's just named thunderbird).

Some things that you might want to consider for the firefox-scripts as well:
When testing my scripts, when restoring the old version, I got a lot of questions wether I wanted to remove the read-only files in ~/.mozilla-thundrbird when removing it - especially the extensions tended to be read-only. In my script, the removal of directories is therefore performed using "rm -rf" instead of just "rm -r" so you won't get any such questions. It may be that these files aren't normally read-only though, but they were in my case.

In addition, the verbose-switch to tar creates massive output due to all the filenames, so many messages from the script will get "lost" in the spam. My script therefore does not use -v when unpacking the archive.

Anyway, it works, so enjoy :)

---

### Post by manicka on 2006-04-08
I have archived both these howtos/scripts at the Ubuntu Document Storage Facility

[http://doc.gwos.org/index.php?title=Install_script_Firefox_1.5.0.1](http://doc.gwos.org/index.php?title=Install_script_Firefox_1.5.0.1)

[http://doc.gwos.org/index.php/Install_script_Thunderbird_1.5](http://doc.gwos.org/index.php/Install_script_Thunderbird_1.5)

---

### Post by vol_freak on 2006-04-09
It worked great for me. Thank you!

---

### Post by aysiu on 2006-04-09
[QUOTE=Ensnared]I
Some things that you might want to consider for the firefox-scripts as well:
When testing my scripts, when restoring the old version, I got a lot of questions wether I wanted to remove the read-only files in ~/.mozilla-thundrbird when removing it - especially the extensions tended to be read-only. In my script, the removal of directories is therefore performed using "rm -rf" instead of just "rm -r" so you won't get any such questions. It may be that these files aren't normally read-only though, but they were in my case.[/quote] I've made this change in the remove script. Thanks for the note about it.

> 
In addition, the verbose-switch to tar creates massive output due to all the filenames, so many messages from the script will get "lost" in the spam. My script therefore does not use -v when unpacking the archive. I'm going to keep verbose in. I think it's good for people to be able to see what's happening, even if they don't actually do much to make it happen.

[quote=vol_freak]It worked great for me. Thank you![/quote] That's good to hear. I'm no programmer, so I want to know that it works on more than just my machine.

---

### Post by cowboyenvy on 2006-04-09
Just a few questions, I myself installed Mozilla firefox in it's previous location ie /usr/lib/mozilla-firefox.

I did this by moving /usr/lib/mozilla-firefox to /usr/lib/mozilla-firefox-1.0.7
extracted the tar.gz file to /usr/lib/mozilla-firefox-1.5.0.1 and creating a symbolic link, this way if I encountered a problem I could easily downgrade back to mozilla firefox with just a quick sym link replacement.

Why did you choose to install it in the /opt directory, it seems that that might indeed create more trouble than simply dropping the new version of in the 'same' location.

Kevin

---

### Post by aysiu on 2006-04-09
I actually prefer /usr/local/bin, but I was basing this script mainly off the Wiki, which chose to put it in the /opt directory. I don't see how this "create[s] more toruble" exactly. Could you explain what you mean?

You can really put it wherever you want.

---

### Post by rmlLinux on 2006-04-11
Thank you aysiu and Ensnared these scripts, worked flawlessly, as a complete newbie they are much appreciated. Cheers . S

---

### Post by TmP on 2006-04-11
Hey!

I installed firefox 1.5 with automatix, and the extensions doesn't seem to work with this version (adblock for instance). Is it the price to pay for the new/unstable firefox under Breezy or have I pushed the wrong lever again?

Thanx

---

### Post by mstlyevil on 2006-04-11
[QUOTE=TmP]Hey!

I installed firefox 1.5 with automatix, and the extensions doesn't seem to work with this version (adblock for instance). Is it the price to pay for the new/unstable firefox under Breezy or have I pushed the wrong lever again?

Thanx[/QUOTE]

You might want to repost the question in the Automatix sub forum for direct help with your problem. It is a little out of place here in this thread.

---

### Post by carverj on 2006-04-12
awww, magic. It even links automatically with the menu icon automatically.
couldn't figure that bit our for myself last time when I tried to upgrade from source.
thanks again aysiu and I hope Dapper is coming along nicely.

---

### Post by aysiu on 2006-04-12
[QUOTE=carverj]
thanks again aysiu and I hope Dapper is coming along nicely.[/QUOTE] You're welcome. Once Dapper comes out, this script will be obsolete, actually.

---

### Post by geeknation on 2006-04-12
:D Works, yay! Thanks for the info!

---

### Post by Sokraates on 2006-04-14
_**Fireupdate 1.1 is out!**_

Fireupdate will now update your favorite browser to version **1.5.0.2**.

To download the new script, please see the first post in this thread.

---

### Post by morbid_bean on 2006-04-14
Please help me!!!!

After a long day of playing with ubuntu for the first time i finnaly figured out how to set up my modem, and it worked!! :D Now i have another problem to deal with... i would like to install the newest firefox which is v. 1.5 and the defult v. i have in this ubuntu is 1.0.7. I have read the step by step guide on how to install it    ( [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) ) and i somewhat get it but when it comes to the part where it says something like install it to opt/firefox or extract files to there i cant do it because i dont have permission to extract the files there.  And im wondering how the heck do i fix this problem. i have installed the libstdc++5 package already. If possible please help me out and if you can please make it as detaild as possible because I dont have much experience with this stuff.

---

### Post by aysiu on 2006-04-14
Try this. It's a script that automates the Wiki instructions.
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by morbid_bean on 2006-04-14
alright then ill give that a try thanks

---

### Post by aysiu on 2006-04-14
[QUOTE=morbid_bean]alright then ill give that a try thanks[/QUOTE] I just modified it today to point to 1.5.0.2 instead of 1.5.0.1, but I haven't had a chance to test the revised script yet. Please let me know if it fails, and I'll try to tweak it more. Sorry to make you the guinea pig.

---

### Post by morbid_bean on 2006-04-14
GREAT!! now another problem
after i do step 3 it asks for a password...i do know the password however when i try to type it in nothing happens my keyboard is almost new so i know it isnt messed up.

---

### Post by towsonu2003 on 2006-04-14
```
sudo tar -C /opt -x -z -v -f firefox-1.5.0.1.tar.gz
```
make sure you use sudo in the above command (command is from the wiki).

---

### Post by morbid_bean on 2006-04-14
Im sorry i have no clue what you mean by that?....do i type that code very first in the  terminal thing?

---

### Post by aysiu on 2006-04-14
[QUOTE=morbid_bean]GREAT!! now another problem
after i do step 3 it asks for a password...i do know the password however when i try to type it in nothing happens my keyboard is almost new so i know it isnt messed up.[/QUOTE] An administrator should be installing it. If you're logged in as the first user you created during installation, you're an administrator, and the password should be your password.

When you type your password in, there's no visual feedback, but it **is** being accepted.

---

### Post by aysiu on 2006-04-14
[QUOTE=morbid_bean]Im sorry i have no clue what you mean by that?....do i type that code very first in the  terminal thing?[/QUOTE] towsonu2003 was responding to your original question about permissions and the /opt directory.

---

### Post by morbid_bean on 2006-04-14
ok cool so far its working its downloading now...as far as me being a guinea pig im an honord to do this

---

### Post by morbid_bean on 2006-04-14
HELL YES! It works! Thanks alot. by the way that link you gave me was it your website or what...because its now in my bookmarks

---

### Post by Harold P on 2006-04-14
That was an easy installation.

Just do:

./firefox

Inside the directory you extracted it into.

---

### Post by aysiu on 2006-04-14
[QUOTE=morbid_bean]HELL YES! It works! Thanks alot. by the way that link you gave me was it your website or what...because its now in my bookmarks[/QUOTE] Thanks for being the guinea pig on the 1.5.0.2 version, and, yes, that is my website.

---

### Post by joe_bling on 2006-04-14
Ensnared, I followed your instructions to the letter on my Ubuntu 5.10 box. I have Thunderbird in Applications-->Internet Gnome menu. When I click to start it, nothing happens. Do you have any suggestions?

---

### Post by Ensnared on 2006-04-14
[QUOTE=joe_bling]Ensnared, I followed your instructions to the letter on my Ubuntu 5.10 box. I have Thunderbird in Applications-->Internet Gnome menu. When I click to start it, nothing happens. Do you have any suggestions?[/QUOTE]
Not really, other than trying to run "mozilla-thunderbird" from a command-prompt and see if you get any errors.
You might also want to make sure your menu-item is executing the "mozilla-thunderbird" command - I use KDE, but in Gnome I think you have to right-click the menu and select "Edit Menu" to check this.

---

### Post by Rikostan on 2006-04-15
Very cool script aysiu, thanks for writing it up!

---

### Post by aysiu on 2006-04-15
[QUOTE=Rikostan]Very cool script aysiu, thanks for writing it up![/QUOTE] Use it while you can--it becomes obsolete in June.

---

### Post by asusrules on 2006-04-16
i have a big problem here
i went through your steps to update the firefox to 1.5 but whenever i try to launch firefox, i get this message," can not launch icon, reason, can not run child processor 'firefox' files does not exist"
what should i do to fix this and get back to 1.0.7 instead?

many thanks

---

### Post by aysiu on 2006-04-16
It sounds as if your icon might have the wrong command? Right-click on the icon and select "Configure" or "Properties" and see what the command is.

If you really want 1.0.7 back, you can use [the uninstall script](http://www.psychocats.net/ubuntu/removenewfirefox.sh), unless, of course, you didn't use the install script to begin with. Otherwise, you should follow [these instructions](https://wiki.ubuntu.com/FirefoxNewVersion#head-51054869b8a40ea50859b0163c806e76f882499c).

---

### Post by towsonu2003 on 2006-04-16
[QUOTE=asusrules]i have a big problem here
i went through your steps to update the firefox to 1.5 but whenever i try to launch firefox, i get this message," can not launch icon, reason, can not run child processor 'firefox' files does not exist"
what should i do to fix this and get back to 1.0.7 instead?
many thanks[/QUOTE]
Try doing these (in that order), but it's not guaranteed to work:

```

sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
#######
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

```

Ignore #######. Those are place holders for myself. Using the commands before ####### gives you firefox 1.0.7, using commands after ####### gives you 1.5.0.2 back (hopefully). Commands are taken from the wiki page. 

another option is to right click the icon, select properties, (as per azz) and put this as command to run:
/opt/firefox/firefox

Important note: you did NOT uninstall firefox using synaptic, did you? If you did (which breaks half of your system), install it back using synaptic and use above commands after #######.

---

### Post by drpaul on 2006-04-16
When I try to run firefox 1.5 after the installation [after the first try this], I get a box with a meesage about can't run because conflicts with another instance running, but there is none.

I can run 1.5 with gksudo, but I concerned about the security of doing that.

I haven't looked at all 40 pages of this thread, but I've looked at more than half :neutral: .

Any ideas about the cause?

TIA

Paul

---

### Post by asusrules on 2006-04-16
thank you aysui and towsonu2003 for th quick replys, but it still does not launch the firefox
 i tried both ways icon thing and the new coding to back to 1.0.7 and to get 1.5.  now i get message every time i click on the firefox icon. "cannot launch entry. Reason:failed to execute child process 'firefox' (no such file or directory. and also when i code it for to remove   /usr/bin/mozilla-firefox to say no file exist.
i  am thinking that i should just reinstall ubuntu or can you help me get the firefox to work

thanks
asusrules

---

### Post by SomeoneWhoIsntMe on 2006-04-16
The default FF theme breaks my GTK theme, where can I find the Ubuntu FF theme?

---

### Post by towsonu2003 on 2006-04-16
[QUOTE=asusrules]thank you aysui and towsonu2003 for th quick replys, but it still does not launch the firefox
 i tried both ways icon thing and the new coding to back to 1.0.7 and to get 1.5.  now i get message every time i click on the firefox icon. "cannot launch entry. Reason:failed to execute child process 'firefox' (no such file or directory. and also when i code it for to remove   /usr/bin/mozilla-firefox to say no file exist.
i  am thinking that i should just reinstall ubuntu or can you help me get the firefox to work
[/QUOTE]
I don't think it's worth reinstalling just for firefox. we'll fix this one way or another. At this point though, let's just uninstalling and reinstalling. Make sure firefox is installed in synaptic. Than go to the wiki page (wiki.ubuntu.com/FirefoxNewVersion), read and do everything it says under section "removing". Than go back to "installing" and do everything it says to install. than run firefox from a terminal (type firefox, press enter) and copy paste any errors you get. also, copy paste any errors you get during the steps (along with the command you used). 

[quote=drpaul]When I try to run firefox 1.5 after the installation [after the first try this], I get a box with a meesage about can't run because conflicts with another instance running, but there is none.

I can run 1.5 with gksudo, but I concerned about the security of doing that.

I haven't looked at all 40 pages of this thread, but I've looked at more than half .

Any ideas about the cause?[/quote]
don't run it with gksudo. try removing the lock file firefox puts in place. do the following (close firefox first!):
```

rm -i ~/.mozilla/firefox/[doubletab and choose directory]/lock

```
[doubletab and choose directory]: firefox puts your profile in a weirdly named directory. it's usually a <randomnumbers>.default directory. after typing ~/.mozilla/firefox/, double tab (tab key on keyboard) to see available profiles, put its name and continue. after giving the command, make sure rm is confirming the correct file, than type "y" (no quotes) and press enter. If there are more than one profiles, rm the lock file in all of them. you might also want to check under /root/.mozilla/firefox/<blabla>/lock to see if exist, but be careful very with the root. 

here is what the command is in **my** system:
```
sudo rm -i /root/.mozilla/firefox/0xso281u.default/lock
``` this was for root lock file
```
rm -i ~/.mozilla/firefox/4flv42qy.default/lock
```
and this one was for my own account. 

**make sure you close firefox (if running) before hand.** To check if it's running, type
```
ps aux | grep firefox
```
here is the output for me, firefox is running:
```
username    8248  0.0  0.1   4656  1644 ?        S    14:44   0:00 /bin/sh /usr/bin/firefox
username    8259  0.0  0.1   4700  1676 ?        S    14:44   0:00 /bin/sh /opt/firefox/run-mozilla.sh /opt/firefox/firefox-bin
username    8264  8.8  4.1 112600 48340 ?        Sl   14:44   2:18 /opt/firefox/firefox-bin
username    9121  0.0  0.0   3256   588 pts/2    R+   15:10   0:00 grep firefox
```
the last one will show up even if firefox is running. If you get such an output, I'd just log out and log in to X to clear it.

If this doesn't work, reboot (I still have the windows mentality) and (don't open firefox) move away your profile:
```

cp -R ~/.mozilla/firefox ~/.mozilla/firefox.busted
mv ~/.mozilla/firefox ~/Desktop/firefox.busted #this is for you to locate your bookmarks and stuff. delete that folder that gets placed on your desktop afterwards.
```
none of these should produce errors. if cp produces errors, don't do mv and copy paste errors.

---

### Post by romulus on 2006-04-18
Geeezze, all I wanted to do was update from 1.0.7 not rewrite the whole damn program.

Please make this easier for noobs like me. I love what you guys are doing and I love the Kubuntu version. I also love the latest and greatest apps as well. 

Linux has come a long way since I first tried it in 1998. But I am still dependent on Windows. I will dump Windows when Linux becomes more automated for things like installing apps and has a more universal driver support.

If I'm missing something please tell me because I really do like KDE and Linux.

---

### Post by towsonu2003 on 2006-04-18
[QUOTE=romulus]Please make this easier for noobs like me. [/quote]
unfortunately, updating firefox from 1.0.7 to 1.5.x is relatively easy, compared to updating other programs... problem is the updating policy in ubuntu -> no updates at all, except security patches to existing programs, once a release is out...
[QUOTE=romulus]
But I am still dependent on Windows. I will dump Windows when Linux becomes more automated for things like installing apps and has a more universal driver support.[/quote]
I can't see any of these two to become a widespread reality in the near future. I heard Linspire is fairly automated though (subscription-based "Click and run" service). But for the driver support, I don't think that will happen :( [1]

[1]sorry for offtopic...

---

### Post by joe_bling on 2006-04-18
I tried running it from the command line, here is the error:

/opt/thunderbird/mozilla-thunderbird-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory

Yet a find / -name libmozjs.so returns:

/usr/lib/mozilla-firefox/libmozjs.so
/usr/lib/mozilla-thunderbird/libmozjs.so
/opt/firefox/libmozjs.so
/opt/thunderbird/libmozjs.so

:confused:

---

### Post by lovebyte on 2006-04-19
I have a problem with this update.  I normally use firefox with profiles (one for my wife and one for me) and so run firefox with the -P option, for instance firefox -P X and firefox -P Y.
This worked with the firefox coming from breezy, but it is not working with ff1.5.  With the latter, once I run with one profile, I cannot have a second instance of firefox with another profile.  It seems that the second time it quits and opens a new window from the first instance.

Any idea what's going wrong?

---

### Post by Sokraates on 2006-04-19
I never managed to have two separate instances running at the same time. Neither with 1.0.x, nor with 1.5.x. As far as I can tell, this is a feature normally not supported by Firefox.

Maybe the Ubuntu-developers have tweaked the code to make this work? If so, maybe you'll want to wait for Dapper, which brings Firefox 1.5.x.

---

### Post by Ensnared on 2006-04-19
That's weird... never had any problems like that before. Try to run 'sudo ldconfig' and see if that helps.

---

### Post by domino on 2006-04-19
I don't know if it's in any interests to anyone and I also don't know how urgent it is to update to 1.5.0.2. So just a heads up. :)

Firefox Multiple Vulnerabilities: [http://secunia.com/advisories/19631/](http://secunia.com/advisories/19631/)

---

### Post by joe_bling on 2006-04-19
Many thanks for your help, Ensnared - and for the scripts. ldconfig got it working fine!

---

### Post by asusrules on 2006-04-20
I just read that there will be a new version of ubuntu (6.06) coiming in June with the new firefox 1.5,do you think updating firefox now will conflict the new verison of ubuntu?

---

### Post by asusrules on 2006-04-20
this is where i found the soon to be released ubuntu
[http://madpenguin.org/cms/index.php/?m=show&opt=printable&id=6699](http://madpenguin.org/cms/index.php/?m=show&opt=printable&id=6699)

---

### Post by Sokraates on 2006-04-20
[quote=asusrules]I just read that there will be a new version of ubuntu (6.06) coiming in June with the new firefox 1.5,do you think updating firefox now will conflict the new verison of ubuntu?[/quote]

Ubuntu installs his Firefox in a different directory. Most how-tos and scripts for installing the FF 1.5 tarball use /opt/firefox. So in the end you will have two different installations. The difference being, that the ubuntu-version can be updated through the repositories.

The profile (located in /home/*youruser*/.mozilla/firefox/*randomfolder*) will be shared by both installations, but thats not a problem.

Eventually, I recommend removing the folder /opt/firefox (if that's where your FF 1.5 is installed) **after** updating to Dapper Drake.

---

### Post by Sokraates on 2006-04-20
Thanks, domino. 

I've updated the first post with links to more information on the fixes and changes.

---

### Post by skeezer65134 on 2006-04-20
OK, I have been running 1.5 for a while (1.5.0.1 actually). The wiki article worked flawlessly.

My question is, 1.0.8 showed up in the repos today so, naturally, Ubuntu wants to upgrade. I'm worried, though, that doing so will break my 1.5 install. Has anyone done the upgrade even though they are running 1.5? Did they have to put the 1.5 install back as the default? Did they lose any of their FF profile info?

Any advice is appreciated!

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=skeezer65134]OK, I have been running 1.5 for a while (1.5.0.1 actually). The wiki article worked flawlessly.

My question is, 1.0.8 showed up in the repos today so, naturally, Ubuntu wants to upgrade. I'm worried, though, that doing so will break my 1.5 install. Has anyone done the upgrade even though they are running 1.5? Did they have to put the 1.5 install back as the default? Did they lose any of their FF profile info?

Any advice is appreciated![/QUOTE]
so far there were 3 approaches that I saw:
**1**. lock firwfox version to 1.0.7 via synaptic (what I did)
**2**. back up your firefox profile, follow wiki instructions to remove firefox (only the following) ```
# First, /usr/bin/firefox
 sudo rm /usr/bin/firefox
 sudo dpkg-divert --rename --remove /usr/bin/firefox
 # Then, /usr/bin/mozilla-firefox, used as the default gnome browser
 sudo rm /usr/bin/mozilla-firefox
 sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
``` do the upgrade, and do installation instructions on wiki (only these) ```
# First, /usr/bin/firefox
 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/firefox
 # Then, /usr/bin/mozilla-firefox, used as the default gnome browser
 sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
``` without starting/running firefox during this process

**3**. backup your profile and do the upgrade, hoping it will not break anything. 

I don't remember anyone choosing any of these options reporting any problems to the forum about the upgrade

---

### Post by Sokraates on 2006-04-20
Updating 1.0.8 will delete your original Firefox-icons, if you have them installed.

Your profile is safe, but won't work at all with 1.0.8. 

If you diverted firefox to mozilla-firefox, you will have to do it again. 

Apart from that, you  should have no problems.

---

### Post by skeezer65134 on 2006-04-21
[QUOTE=towsonu2003]so far there were 3 approaches that I saw:
**1**. lock firwfox version to 1.0.7 via synaptic (what I did)
[/QUOTE]

I wasn't aware you could even do that. That brings the next question; how do I lock it at a version?

---

### Post by aysiu on 2006-04-21
[QUOTE=skeezer65134]I wasn't aware you could even do that. That brings the next question; how do I lock it at a version?[/QUOTE] Like this.

---

### Post by aysiu on 2006-04-23
Ensnared, I've updated your script to use Thunderbird 1.5.0.2.

---

### Post by Ensnared on 2006-04-23
Good stuff :)

I almost forgot about this since I've upgraded to Dapper on everything except my server, so thanks for taking care of it :)

---

### Post by erlendba on 2006-04-26
Hi

Followed the script and it worked perfectly, except for the keyboard shortcut that I used for the browser. It does not work at all, even after I tried resetting it. Does anyone have a clue?

Second question: Are the files from my previous version removed?

---

### Post by sumgai on 2006-04-26
I tried the script and it worked fine except I can't install extensions unless I run firefox as root (obviously when I try to run firefox as the user, the extensions aren't there).

It seemed like firefox was also forgetting changes to preferences, so in a blind attempt, I chmod'ed all the relevant files to +w for all and that seemed to fix the preferences issue, but I've still got the extensions problem.

Also, I tried the script for thunderbird.  All the files seem to be where they belong, but I don't get anything when I try to run it (from the menu or from command line).

Bear in mind that it's been about 20 years since I've seriously used any Unix-like OS, so I apologize for being a reborn noob.

Any help would be mucho appreciado!

Mitch

---

### Post by vexorian on 2006-04-28
After using this article to install firefox 1.5.0.1 when I wanted to update to 1.5.0.2 I just had to use:

$ sudo firefox

Then the Help/Check for updates was available and I could update easily.

Is there a way to make ubuntu's auto update thing stop bothering me about updating to 1.0.9 ?

---

### Post by aysiu on 2006-04-28
[QUOTE=vexorian]
Is there a way to make ubuntu's auto update thing stop bothering me about updating to 1.0.9 ?[/QUOTE] Yes. Look at the post above yours--with a screenshot of how to do it.

---

### Post by LazyBoy on 2006-04-28
Anyone know how to fix the icons in the title bar and panel?
They've defaulted to boring X's.
(The running application icons, not the launcher icons -- see attachment.)

Thanks,
LB

**Follow-up:**  This was specific to 64-bit installs, and is solved here: [http://ubuntuforums.org/showthread.php?p=1040925#post1040925](http://ubuntuforums.org/showthread.php?p=1040925#post1040925)

---

### Post by akimmell on 2006-04-28
Hi,
Automatix is awesome.

The only problem I'm having it trying to install java realtime.
I've read all the instructions and tried making the link (ln -s etx) but it doesn't work.   I selected the package with Automatix but i still don't think it's installed.  When I go to some websites like time.gov or flightview.com my apps don't work.  Thanks for all the work with Automatix.  Any help with Java appreciated.

---

### Post by OfficeLinebacker on 2006-04-28
Is 1.5 in the repositories now?

---

### Post by vexorian on 2006-04-29
[QUOTE=aysiu]Yes. Look at the post above yours--with a screenshot of how to do it.[/QUOTE]
My bad for not noticing it, I wouldn't now the thread was 22 pages long, so I didn't really see the posts, thanks for pointing out

---

### Post by aysiu on 2006-04-29
Anyone want to be a guinea pig for my Swiftfox 64-bit script?

---

### Post by pigFoot on 2006-04-29
[QUOTE=Sokraates]
If you diverted firefox to mozilla-firefox, you will have to do it again. 
[/QUOTE]
I just ran the update against my 1.5.0.2 and did not find this to be the case.

$ ls -l `which firefox`
lrwxrwxrwx  1 root root 20 2006-03-27 20:04 /usr/bin/firefox -> /opt/firefox/firefox

---

### Post by Giga on 2006-04-29
where is the button to delete this msg?

---

### Post by Giga on 2006-04-29
Aysiu,

i use your script to install firefox 5.1

didnt work... im using breezy 5.10 , cpu am64 (with Ubuntu for 64bits)


i use the remove script to uninstalled also
im browsing through Galeon now :)

Well.. when i execute firefox 1.0.7.. nothing happens..the mouse cursor just get busy for a few seconds.. and thats it.

Any idea of what might be happened?

---

### Post by aysiu on 2006-04-29
The original script (post #1) is for x86, not AMD64.

Mozilla does not precompile an AMD64 version of Firefox.

Post #25, however, has a script for installing Swiftfox (another version of Firefox) specifically for AMD64. Unfortunately, not having a 64-bit processor myself, I'm not able to test it out. Would you like to be a guinea pig for the script in post #25?

---

### Post by Giga on 2006-04-29
Sure.. im going to test it
i let you know.

So.. There is no Firefox 1.5 for 64bits??

In Windows.. the same software 1.5 works for both versions..

i thouth only drivers need especifically 64bits version.
I think this is not the case for Linux,, am i wrong? There has to be every single software version for 64 bits and x86, no matter if its drivers or single softwares like firefox or Amule..etc?

Another example.. i was installing logitech 510 mouse.. works great
but when i try to installed the applet.. (i think its like a control panel like you have in windows).. didnt work .. returns a (this applet works only for x86).

Well.. if i installed Ubuntu x86 in my computer that has CPU 64buts.. it will work flawlesssly? What you recommend me to do?

Thank u very much :)

---

### Post by aysiu on 2006-04-29
[QUOTE=Giga]
So.. There is no Firefox 1.5 for 64bits??[/quote] Not unless you compile it from source.

> 
In Windows.. the same software 1.5 works for both versions.. I'm not sure why this is.

> Well.. if i installed Ubuntu x86 in my computer that has CPU 64buts.. it will work flawlesssly? From what I've read, yes--and you'll have more software easily available. > What you recommend me to do? For now... test the Swiftfox script. If it doesn't work, I'll quickly compose an uninstall script. If it works, great. And, you may eventually want to try Ubuntu x86.

---

### Post by Giga on 2006-04-29
Unfortunately, didnt work.

Well... i will do what you recommend me. Try install x86 Ubuntu

---

### Post by aysiu on 2006-04-29
[QUOTE=Giga]Unfortunately, didnt work.[/quote] Sorry. Do you know at what point it failed? Did it *appear* to work but just not launch? Or did you get some errors that appeared during the actual installation?

> 
Well... i will do what you recommend me. Try install x86 Ubuntu This is just based on what I've read, as I don't have a 64-bit processor, but I think the only reason to use the AMD64 version of Ubuntu is to take full advantage of what your 64-bit processor can do (is it more powerful? faster? I don't know what the actual advantage is... better graphics capability?), but if you use the x86 version, it's just as if you didn't have a 64-bit processor.

Speaking loosely based on what I've heard and know. If someone knows better about this, please correct me.

---

### Post by Giga on 2006-04-29
[quote=aysiu]Sorry. Do you know at what point it failed? Did it *appear* to work but just not launch? Or did you get some errors that appeared during the actual installation?[/quote]

It happens the same thing.. when i click on the blue world icon, the cursor get busy for a few seconds and nothing happens..
tell me what to do at terminal to get error msgs so i paste here..
sorry, im newbie and im still a bit confused about how the tree files of Linux works...


[quote=aysiu]  reason to use the AMD64 version of Ubuntu is to take full advantage of what your 64-bit processor can do (is it more powerful? faster? I don't know what the actual advantage is... better graphics capability?),[/quote]

That is one the things i would like to know.. :)  What i would gain if i keep amd64?
i also thought about things you have said like speed and better graphics, but i dont exaclty what would be these advantages..

---

### Post by aysiu on 2006-04-29
[QUOTE=Giga]It happens the same thing.. when i click on the blue world icon, the cursor get busy for a few seconds and nothing happens..
tell me what to do at terminal to get error msgs so i paste here..
sorry, im newbie and im still a bit confused about how the tree files of Linux works...[/quote] You haven't uninstalled Swiftfox, then? If so, go to a terminal and just type ```
firefox
``` If that doesn't work, try typing ```
cd /opt/swiftfox
./swiftfox
``` and post back any errors.[/quote]

> 
That is one the things i would like to know.. :)  What i would gain if i keep amd64?
i also thought about things you have said like speed and better graphics, but i dont exaclty what would be these advantages.. Start a new thread and ask what the advantages are of running AMD64 versus x86.

---

### Post by Giga on 2006-04-29
[quote=aysiu]You haven't uninstalled Swiftfox, then? If so, go to a terminal and just type ```
firefox
``` If that doesn't work, try typing ```
cd /opt/swiftfox
./swiftfox
``` and post back any errors.[/quote] 
 Start a new thread and ask what the advantages are of running AMD64 versus x86.[/quote]

good idea.. i will do

Well.. about the errors..

it returns sth like: cannot identified TF8 and then cannot find or open PANGO something.. (library?)

(im sorry, i didnt copy the msg because i called to one friend (the one who told me to learn Linux) and he said to me to install x86 instead.
He said i probably wont ge any real advantage (at least, not for now) with 64bits version.

Thank you very much though:)

By the way, i install x86 and use your txt.. guess what? Work flawless :)

---

### Post by aysiu on 2006-04-29
[QUOTE=Giga]By the way, i install x86 and use your txt.. guess what? Work flawless :)[/QUOTE] Well, it's because the script uses the precompiled x86 Firefox package.

The other script for Swiftfox is the 64-bit package, but I've never tested it, so...


... well, in any case, glad it worked out for you finally!

---

### Post by avktm on 2006-05-02
i was trying to extract the firefox tar into the opt folder and it wouldn't let do it , i tried to log in as root and it said wrong password or username whats the deal

---

### Post by aysiu on 2006-05-02
[QUOTE=avktm]i was trying to extract the firefox tar into the opt folder and it wouldn't let do it , i tried to log in as root and it said wrong password or username whats the deal[/QUOTE] A few things:

1. There's a script [here](http://www.psychocats.net/ubuntu/firefox) that will download and install the new Firefox for you, so that you don't have to copy and paste all those commands from [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

2. If you do decide you'd rather copy and paste commands, make sure you **copy and paste** them. Do not try to retype them. This command should extract the .tar.gz to the /opt folder: ```
sudo tar -C /opt -x -z -v -f firefox-1.5.0.2.tar.gz
```

3. You don't log in as root. There is no root account enabled in Ubuntu. Read more here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Sokraates on 2006-05-03
_**Fireupdate 1.2 is out!**_

Fireupdate will now update your favorite browser to version **1.5.0.3**.

To download the new script, please see the first post in this thread.

---

### Post by russbuss on 2006-05-04
Thanks so much for this script.  It is very handy!

One thing I discovered is that I did have to kill Firefox before running the script in order for it work.  If I tried running it with Firefox still running, nothing happened.  I did not get a dialogue box or anything of the sort.

Still, very nice work.

Thanks.

---

### Post by adamkat on 2006-05-04
worked like a charm, thanks!

---

### Post by Russty of Oz on 2006-05-04
I must be **THICK**!](*,) 

I can't work this out.  How do you get this update to work?

---

### Post by Sokraates on 2006-05-04
[quote=russbuss]If I tried running it with Firefox still running, nothing happened.  I did not get a dialogue box or anything of the sort.
[/quote]

Now that's strange. Fireupdate checks, whether a process including the string "firefox" is running. So if you have a process to kill, Fireupdate should give you a popup. Unless you don't have kdialog, dialog or zenity installed.

Which firefox-version did you update from? Also, which desktop environment are you running? 

If you still have that version of firefox handy, backup your profile (removing the "." in front of the folder is enough), rename /opt/firefox, reinstall the old version and then run the script in verbose mode from the console while running Firefox. The output should help me pinpoint the problem.

You can then restore everything by simply renaming the folders as they were before.

---

### Post by Sokraates on 2006-05-04
[quote=Russty of Oz]I must be **THICK**!](*,) 

I can't work this out.  How do you get this update to work?[/quote] 
For starters: check, if you have downloaded the correct Fireupdate. It depends on the firefox-version you want to update from (00, 01 or 02).

Extract the tarball to your homefolder. A **folder** called "Fireupdate" will be created including all the files. One of those is called "Fireupdate".

Close Firefox, if it is open, and doubleclick on the **file** "Fireupdate".

The script will ask you at some point to enter your password. That is your user password. The password is needed, since the sub-script, which will apply the update and modify the folder "/opt/firefox" needs to be run with root-privileges.

If you have any error-output, please post it here. If you have none or it just says, that the update has failed or could not be applied, please run Fireupdate with the verbose argument from the console. The command should look like this:
```
~/Fireupdate/Fireupdate -v
``` Then please post the output.

---

### Post by Russty of Oz on 2006-05-04
Hmmm, well I did say I was thick.

To start with, where do I download Fireupdate, I googled but couldn't find it.  Secondly, what is a 'tarball'?   

I am using FF 1.5.0.1

As you have no doubt guessed, I am new to Linux.  But I love it and am determined to learn how to do all these things!

---

### Post by LazyBoy on 2006-05-04
The HOWTO has some "chown" calls that should be "chmod".

LB

---

### Post by towsonu2003 on 2006-05-04
[QUOTE=LazyBoy]The HOWTO has some "chown" calls that should be "chmod".

LB[/QUOTE]
thanks for letting us know. I always mix up chown with chmod... should be fixed now.

---

### Post by Sokraates on 2006-05-04
[quote=Russty of Oz]Hmmm, well I did say I was thick.

To start with, where do I download Fireupdate, I googled but couldn't find it.  Secondly, what is a 'tarball'?   

I am using FF 1.5.0.1

As you have no doubt guessed, I am new to Linux.  But I love it and am determined to learn how to do all these things![/quote] 
First of all: welcome!

You'll find all the links in the **first** post. You will need to download the file labeled "*** Fireupdate 1.2, from  1.5.0.1***".

Fireupdate will only work with the tarballs from [www.mozilla.com]("http://www.mozilla.com"). How did you install Firefox 1.5.0.1? It is not included in Breezy Badger by default.

Did you use Automatix? Then it will work correctly, since Automatix uses the official tarballs. Was it already included in Ubuntu? Then you are most likely using Dapper Drake Beta. Fireupdate will most probably **not** work in this case, but you will only have to wait a few days to update by Synaptic.

As for Tarballs, take a look [here]("http://en.wikipedia.org/wiki/Tarball").

---

### Post by mrazster on 2006-05-04
Worked like a charm...here to.  \\:D/ =D>

---

### Post by Russty of Oz on 2006-05-04
[QUOTE=Sokraates]First of all: welcome!

You'll find all the links in the **first** post. You will need to download the file labeled "*** Fireupdate 1.2, from  1.5.0.1***".

Fireupdate will only work with the tarballs from [www.mozilla.com]("http://www.mozilla.com"). How did you install Firefox 1.5.0.1? It is not included in Breezy Badger by default.

Did you use Automatix? Then it will work correctly, since Automatix uses the official tarballs. Was it already included in Ubuntu? Then you are most likely using Dapper Drake Beta. Fireupdate will most probably **not** work in this case, but you will only have to wait a few days to update by Synaptic.

As for Tarballs, take a look [here]("http://en.wikipedia.org/wiki/Tarball").[/QUOTE]

Thanks for all that Sokraates!

I installed 1.5.0.1 using Automatix.  

I will follow your instructions and let you know how I get on.

Russty.:cool:

---

### Post by Russty of Oz on 2006-05-04
Hmmmm, something happened but FF is still 1.5.0.1.

I did as you suggested and the terminal opened and then it asked for my password but after that the terminal showed things happening and it said that it was downloading the update to 1.5.0.3 then it all closed.  It was too quick for me to see what was going on.  

So what now?

---

### Post by Russty of Oz on 2006-05-04
[QUOTE=Sokraates]The command should look like this:
```
~/Fireupdate/Fireupdate -v
``` Then please post the output.[/QUOTE]

I typed the above in the terminal and it came back with this;

russell@ubuntu:~$ ~/Fireupdate/Fireupdate -v
/home/russell/Fireupdate/Fireupdate: line 58: dialog: command not found
16023 ?        00:00:00 firefox
16039 ?        00:00:09 firefox-bin
/home/russell/Fireupdate/Fireupdate: line 71: dialog: command not found

What now?

---

### Post by Sokraates on 2006-05-05
When you ran Fireupdate with the verbose argument, you had Firefox running.
[php] 16023 ?        00:00:00 firefox
16039 ?        00:00:09 firefox-bin[/php] There also seems to be a problem with two dialog options ("command not found"). They are responsible for the pop-up notifications.

I'm not at home right now, so I can't check what lines 58 and 71 are about exactly (well, one of those obviously checks for a running instance of Firefiox). I will do so in the evening.

For starters and before running Fireupdate again, please check, if the update has succeeded or not. Simply open Firefox, got to "Help" -> "About Firefox" and if the version is 1.5.0.3, you are set.

---

### Post by Russty of Oz on 2006-05-05
No, it is still 1.5.0.1.

---

### Post by Russty of Oz on 2006-05-05
[QUOTE=Sokraates]When you ran Fireupdate with the verbose argument, you had Firefox running.
[/QUOTE]

I did the verbose thing again without FF running and this was the result;


[B]russell@ubuntu:~$ ~/Fireupdate/Fireupdate -v
/home/russell/Fireupdate/Fireupdate: line 58: dialog: command not found
cp: cannot overwrite non-directory `/opt/firefox_fireupdate_backup/firefox' with directory `/opt/firefox'
--16:40:16--  [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.3/update/linux-i686/en-US/firefox-1.5.0.2-1.5.0.3.partial.mar](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.3/update/linux-i686/en-US/firefox-1.5.0.2-1.5.0.3.partial.mar)
           => `firefox-1.5.0.2-1.5.0.3.partial.mar'
Resolving ftp.mozilla.org... 64.50.236.52, 64.50.238.52, 216.165.129.134, ...
Connecting to ftp.mozilla.org|64.50.236.52|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/1.5.0.3/update/linux-i686/en-US ... done.
==> PASV ... done.    ==> RETR firefox-1.5.0.2-1.5.0.3.partial.mar ... done.
Length: 152,016 (148K) (unauthoritative)

    0K .......... .......... .......... .......... .......... 33%   19.15 KB/s
   50K .......... .......... .......... .......... .......... 67%   50.47 KB/s
  100K .......... .......... .......... .......... ........  100%   51.56 KB/s

16:40:26 (32.69 KB/s) - `firefox-1.5.0.2-1.5.0.3.partial.mar' saved [152016]

/home/russell/Fireupdate/FireupRoot: line 53: 20604 Killed                  zenity --progress --pulsate --title "Fireupdate" --text "Downloading update to version 1.5.0.3. This may take a few moments."  (wd: /opt/firefox-update)
/home/russell/Fireupdate/FireupRoot: line 73: dialog: command not found
russell@ubuntu:~$
[/B]

Does that help?

Russty

---

### Post by Russty of Oz on 2006-05-05
:oops:   [B]Oh well, trust me to get it wrong.  I didn't read the file names properly and tried installing the 1.5.02 to 1.5.03 instead of doing 1.5.01 to 1.5.03!  

So now I have done it CORRECTLY and it worked like a dream!!

Thank you Sokraates, for all you help!  When I said before that I was thick, I didn't realize just HOW THICK I could be!!;) 

Thanks again for being so patient.

Russty.[/B]

---

### Post by Sokraates on 2006-05-05
Glad it worked. Still the dialog-errors bother me. Fireupdate uses kdialog with KDE, zenity with GNOME and dialog for everything else. 

What desktop environment do you use?

---

### Post by Russty of Oz on 2006-05-05
[QUOTE=Sokraates]Glad it worked. Still the dialog-errors bother me. Fireupdate uses kdialog with KDE, zenity with GNOME and dialog for everything else. 

What desktop environment do you use?[/QUOTE]

Desktop environment??   What is that?

I am using Ubuntu Breezy Badger that is all I know about it.

---

### Post by barbarian on 2006-05-05
Thank you, good script..

---

### Post by Sokraates on 2006-05-06
[quote=Russty of Oz]Desktop environment??   What is that?

I am using Ubuntu Breezy Badger that is all I know about it.[/quote] 
For desktop environments, look [url=http://en.wikipedia.org/wiki/Desktop_environment]here(/URL].

In a (ubuntu)nutshell: if it's brown, it's GNOME. If it's blue, it's KDE. ;)

**Edit: **The errors you encountered were due to the app "dialog" not being found. I know it's included in Breezy, but not in Dapper. But dialog is only used, if kdialog (KDE) or zenity (GNOME) are not available, which they are in Dapper. 

Are you bychange running Xubuntu Beta?

---

### Post by Russty of Oz on 2006-05-06
Well, mine is brown so it is GNOME.

No I am not running Xubuntu Beta, it is just plain Ubuntu Breezy Badger 5.10.

Perhaps the "dialog" not being found was due to the fact that I was attempting to update from FF1.5.0.2 to 1.5.0.3 when there was no 1.5.0.2 on the system?  Once I downloaded the right file, it ran with no errors at all.

---

### Post by Sokraates on 2006-05-07
Nope. That wasn't it. Using the wrong file should have resulted in an error message, that the update could not be completed successfully. 

With GNOME, the popups are generated with zenity. But lines 58 and 71 are responsible for dialog, which is only a fallback. It's a strange error I haven't heard about before.

Anyway. I'm working on an improvement.

---

### Post by rockrhino27 on 2006-05-07
I must say this script was ridiculously easy.  Thanks a million to the author of the script.  Awesome Job!!!

Rock

---

### Post by micmic on 2006-05-07
[QUOTE=rockrhino27]Thanks a million to the author of the script.  Awesome Job!!!
Rock[/QUOTE]
Me too, for other locales, edit the FireupRoot and change en-US with your locale (sorry my english)

---

### Post by johansrk on 2006-05-09
An even easier way is to run my script.. It's just the procedure process which is already shown, but this is faster if you are lazzy. But first you must...
- Download the firefox-1.5.0.3.tar.gz file, and put it on your desktop
- make a file called "install.sh" and add the code below
run the script from terminal like this
cd Desktop
sudo sh install.sh

THIS CODE DOES NOT SAVE YOUR BOOKMARKS AND SETTING IN FIREFOX. USE ON OWN RISK.. HOWEVER IT WORKS GREAT ON ALL MY COMPUTERS

```

sudo apt-get install mozilla-mplayer
cd Desktop

#Pak tar filen ud i OPT folderen
sudo tar -C /opt -x -z -v -f firefox-1.5.0.3.tar.gz

#Link til plugins
cd /opt/firefox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .

#Derefter
cd
mv ~/.mozilla/firefox ~/.mozilla/firefox1.0.x.ubuntu
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox


```

---

### Post by giuliastro on 2006-05-10
How come Thunderbird 1.5.0.2 hasn't been added to Dapper's repository yet? Any problems?

---

### Post by aysiu on 2006-05-10
[QUOTE=giuliastro]How come Thunderbird 1.5.0.2 hasn't been added to Dapper's repository yet? Any problems?[/QUOTE] 1.5 is in there. Can't you just use Thunderbird's built-in updater to update it to 1.5.0.2? > Package mozilla-thunderbird
    * dapper (mail): Mozilla Thunderbird standalone mail client
      **1.5**-0ubuntu6: amd64 i386 powerpc

---

### Post by giuliastro on 2006-05-11
[QUOTE=aysiu]1.5 is in there. Can't you just use Thunderbird's built-in updater to update it to 1.5.0.2?[/QUOTE]

Nope, updater is disabled in both thunderbird and firefox. And I understand this since I don't know how well this way to update programs would go along with Dapper updates.

---

### Post by Googler on 2006-05-11
i did all steps to get firefox 1.5 but it didn't work, fireox didn't open
i had to download the other script to remove it
and i'm now running the older on(1.0.8) 
is there an easier way to update it?

---

### Post by aysiu on 2006-05-11
[QUOTE=Googler]i did all steps to get firefox 1.5 but it didn't work, fireox didn't open
i had to download the other script to remove it
and i'm now running the older on(1.0.8) 
is there an easier way to update it?[/QUOTE] It doesn't really get easier than that script, to tell you the truth, and I know it's worked for a lot of people (and I've tested it myself numerous times on my computer).

When you say "it didn't work," what exactly do you mean?

Did it *appear* to work, first of all? In other words, when the script was executing, were there any noticeable errors? And, if so, what were they?

When you say "Firefox didn't open," did you try opening it from the terminal? If so, what errors or output did you get?

You may also want to try from the terminal /opt/firefox/firefox to see if it's the installation or the symlinking to the launcher that's off.

Help me help you make it work.

---

### Post by GMFreak8 on 2006-05-11
Didn't work for me either.  Apparently it doesn't download FireFox from the Mozilla website anymore, which basically renders everything else useless.  At least that's my take on things....

---

### Post by aysiu on 2006-05-11
[QUOTE=GMFreak8]Didn't work for me either.  Apparently it doesn't download FireFox from the Mozilla website anymore, which basically renders everything else useless.  At least that's my take on things....[/QUOTE] Well, it never did download from Mozilla. It always picked a mirror.

But, you're right--that mirror's dead. Let me modify the script.

**Edit**: Okay. The script in the original post has been edited to use an active mirror.

---

### Post by GMFreak8 on 2006-05-11
Oh, I didn't look close enough to see what site it downloads from.  Damn, if I would have known you'd update the script so fast, I would have waited, instead of doing it the long way.

---

### Post by aysiu on 2006-05-11
[QUOTE=GMFreak8]Oh, I didn't look close enough to see what site it downloads from.  Damn, if I would have known you'd update the script so fast, I would have waited, instead of doing it the long way.[/QUOTE] Sorry! Well, it should be working again now.

I did wonder why it would be working for so many people and then all of a sudden not work for two people in a row.

A dead mirror would explain it.

---

### Post by GMFreak8 on 2006-05-11
[QUOTE=aysiu]Sorry! Well, it should be working again now.

I did wonder why it would be working for so many people and then all of a sudden not work for two people in a row.

A dead mirror would explain it.[/QUOTE]


Glad I could help with *something*, instead of asking two million questions. :lol:

---

### Post by oskvaz on 2006-05-13
Excellent!!! It works. I have installed my Firefox 1.5.0.3 whit your script.

Thank you!!!

---

### Post by aysiu on 2006-05-13
[QUOTE=oskvaz]Excellent!!! It works. I have installed my Firefox 1.5.0.3 whit your script.

Thank you!!![/QUOTE] Glad it's working again. Sorry about the interruption, folks.

---

### Post by Polygon on 2006-05-14
sorry to bump this topic, but i have the same problem as someone else in this topic with the thunderbird script, i installed it and followed the directions, but when i click on the icon nothing happens. i dont know if this is because i didnt have thunderbird installed when i ran the script, but neither the thunderbird or profile manager icons do anything. ill just install it off the mozilla site... but the firefox script works nicely, thanks!

---

### Post by aysiu on 2006-05-14
I think I may have found a bug in that old *installnewthunderbird* script. 

It tries to make a symlink from /opt/thunderbird/thunderbird-bin to /opt/thunderbird/mozilla-thunderbird-bin. I'm not sure what that's all about, and I don't see that command in [the Wiki instructions](https://wiki.ubuntu.com/ThunderbirdNewVersion).

I'm not 100% either whether the Thunderbird removal script will fix that error.

I have uploaded here what I think should be a good script, though. I'll test it out and then post an edit on whether it works or not.

**Edit**: I just ran the attached script on my test computer, and it works.

I've also written a script to undo the work of the first script. I have not tested this one, though.

So you would run the undo script first and then run the new script to get Thunderbird properly installed.

1. Download both text files to your desktop.
2. ```
cd ~/Desktop
mv installnewthunderbird.sh.txt installnewthunderbird.sh
mv undothunderbirdscript.sh.txt undothunderbirdscript.sh
./undothunderbirdscript.sh
./installnewthunderbird.sh
```
3. Let me know how it goes...

---

### Post by CharlesG on 2006-05-14
[QUOTE=aysiu]Ensnared, I've updated your script to use Thunderbird 1.5.0.2.[/QUOTE]

Thank you very much for your assistance.  I've finally managed to get Thunderbird 1.5.0.2 installed on Kubuntu Breezy.

One hint for others who like me are trying to install 1.5.0.2 from scratch - for this script to work, one actually needs to install 1.0.8 first, open it, and establish a profile.  I also downloaded some email.  If one doesn't have the profile already set up, then the rest of the script won't function and 1.5 will not open, even though it's installed.

---

### Post by aysiu on 2006-05-14
[QUOTE=CharlesG]Thank you very much for your assistance.  I've finally managed to get Thunderbird 1.5.0.2 installed on Kubuntu Breezy.

One hint for others who like me are trying to install 1.5.0.2 from scratch - for this script to work, one actually needs to install 1.0.8 first, open it, and establish a profile.  I also downloaded some email.  If one doesn't have the profile already set up, then the rest of the script won't function and 1.5 will not open, even though it's installed.[/QUOTE] Good to know.

---

### Post by visik7 on 2006-05-16
1

---

### Post by nox.freak on 2006-05-17
Got a problem,

I did all the steps but after installing libstdc++ now gnome, and any gnoma based app will not run.

running ubuntu 5.10 with kubuntu installed.

tryed removing libstdc++ but no luck.

thanks,

---

### Post by louistan3 on 2006-05-17
this is great! thanks.. worked well for me..:-D

---

### Post by brian g on 2006-05-17
how do i get embedded asx movies to play using this install of firefox?

how do i prevent the old firefox from opening when i click on URLs in other programs (such as Thunderbird or XChat)

---

### Post by hellmet on 2006-05-17
that was so helpful..thnkx man...
worked like a charm

---

### Post by LazyBoy on 2006-05-18
The new firefox doesn't show my printers in it's dialog.  :( 
The old one still does.

Any ideas?
LB

---

### Post by FantasySportsMan on 2006-05-21
Awesome, this worked like a charm!!!

Thank You!!

---

### Post by mrgraz on 2006-05-31
Thanks for the info Great information on how to update firefox to latest version :p

---

### Post by aysiu on 2006-05-31
You want to really know how to do it easily, go here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)

---

### Post by dmizer on 2006-05-31
[QUOTE=CharlesG]Thank you very much for your assistance.  I've finally managed to get Thunderbird 1.5.0.2 installed on Kubuntu Breezy.

One hint for others who like me are trying to install 1.5.0.2 from scratch - for this script to work, one actually needs to install 1.0.8 first, open it, and establish a profile.  I also downloaded some email.  If one doesn't have the profile already set up, then the rest of the script won't function and 1.5 will not open, even though it's installed.[/QUOTE]
indeed that is good to know ... i just ran into that problem myself.  off to fix it ...

okay ... i was able to fix this little glitch because i had all my mail backed up in a previous profile.  i just replaced the profile built by the script with the one i had backed up, and thunderbird works just as it use to.

thanks for the handy script.

---

### Post by picpak on 2006-06-07
Dapper provides a much more sane way to upgrade Firefox. This replaces your current Firefox, and doesn't create two different versions of it.

As far as I know, Automatix still installs Firefox 1.5.0.3. If I'm wrong, you can ignore this for now, but it can be helpful if you want a new version before Automatix gets it. 

Here it goes:

1) Download Firefox 1.5.0.4:
```
wget http://backports.org/debian/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.4-0bpo1_i386.deb
```

2) Download Firefox gnome-support (ignore this if you don't use Gnome):
```
wget http://backports.org/debian/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.4-0bpo1_i386.deb
```

3) Install the downloaded files:
```
sudo dpkg -i firefox*.deb
```

...And you're done. This hasn't been tested on any of the older Ubuntu versions (Warty, Hoary, Breezy).

---

### Post by Sokraates on 2006-06-08
_**Fireupdate 1.3 is out!**_

Fireupdate will now update your favorite browser to version **1.5.0.4**.

To download the new script, please see the first post in this thread.

---

### Post by oskvaz on 2006-06-08
Excellent. I installed it without no problem. 
It's really the easy way.
Thank you very much.

---

### Post by aysiu on 2006-06-08
While this method may have its merits, I would also like to mention that *nanotube* has created [a script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5) for installing the latest Firefox.

It does, in fact, install two Firefoxes (the Ubuntu one, which it doesn't use fully) and the Mozilla one, but the Mozilla one is self-updating.

It automatically checks for the latest version of Firefox (so if you run the script in September, it should install Firefox 2.0) and asks which locale you want, too.

On the same site, *nanotube* also has a script for installing Swiftfox, for you 64-bit users out there.

---

### Post by Geekboy on 2006-06-08
Thanks Aysiu for the link to that script!  That worked great and now I'm at the latest version of Firefox.  :D 

And Thank you Nanotube for the script!

If your looking for an easy way to upgrade, this works.  Very simple.

---

### Post by dief-eh? on 2006-06-09
hello, 

[/QUOTE]
1) Download Firefox 1.5.0.4:
```
wget http://backports.org/debian/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.4-0bpo1_i386.deb
```
2) Download Firefox gnome-support (ignore this if you don't use Gnome):
```
wget http://backports.org/debian/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.4-0bpo1_i386.deb
```
3) Install the downloaded files:
```
sudo dpkg -i firefox*.deb
```

...And you're done. 
[/QUOTE]

thanks for your instructions. i've been puzzled by the info that "about mozilla firefox" supplied: 1.5.0.2, despite running dapper 6.06 (i think)
which -- i was led to believe -- *came* with 1.5.0.3.

unfortunately, about mozilla firefox still shows 1.5.0.2! any ideas about what gives?

TIA

---

### Post by aysiu on 2006-06-09
[QUOTE=dief-eh?]
unfortunately, about mozilla firefox still shows 1.5.0.2! any ideas about what gives?[/QUOTE] "still"--meaning after installing the .deb from the first post of this thread?

---

### Post by dief-eh? on 2006-06-09
[QUOTE=aysiu]"still"--meaning after installing the .deb from the first post of this thread?[/QUOTE]

hello,

thank you for your reply.

yes. pasted each step into a gnome-terminal, and watched while each did its thing. but 'about firefox' still shows 1.5.0.2.

and that's still the case, this morning, after running the morning upgrade manager, which coincidentally, listed firefox as one of the upgrade targets (?)! i'm more confused, if that's imaginable.

any ideas gratefully received...

---

### Post by aysiu on 2006-06-09
Unless picpak has any suggestions, I would just use nanotube's script.

---

### Post by FredB on 2006-06-09
[QUOTE=aysiu]Unless picpak has any suggestions, I would just use nanotube's script.[/QUOTE]

Erh... What about using official updating way ? Ubuntu version of firefox 1.5.0.4 is available since a few hours ;)

---

### Post by aysiu on 2006-06-09
Yeah, but then when version 1.5.0.5 comes out or 2.0 comes out, then people will ask again, "How do I upgrade?" and Ubuntu's repositories will always be a week behind.

If you install the Mozilla version, you'll always be up-to-date.

---

### Post by picpak on 2006-06-09
[QUOTE=dief-eh?]hello, 

> 
1) Download Firefox 1.5.0.4:
```
wget http://backports.org/debian/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.4-0bpo1_i386.deb
```
2) Download Firefox gnome-support (ignore this if you don't use Gnome):
```
wget http://backports.org/debian/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.4-0bpo1_i386.deb
```
3) Install the downloaded files:
```
sudo dpkg -i firefox*.deb
```

...And you're done. 


thanks for your instructions. i've been puzzled by the info that "about mozilla firefox" supplied: 1.5.0.2, despite running dapper 6.06 (i think)
which -- i was led to believe -- *came* with 1.5.0.3.

unfortunately, about mozilla firefox still shows 1.5.0.2! any ideas about what gives?

TIA[/QUOTE]

Is this a fresh install? Perhaps you're running a copy from /opt. Try running "/usr/bin/firefox -v" (without quotes) and show me what it says.

But yes, if Firefox 1.5.0.4 is in the repositories, I suggest using that. The new version overwrites this version anyway.

---

### Post by tunads on 2006-06-10
what about for those of us with x64 based systems?

---

### Post by aysiu on 2006-06-10
[QUOTE=tunads]what about for those of us with x64 based systems?[/QUOTE] 64-bit, you mean? nanotube wrote [a script to install Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox), a Firefox derivative that makes a version for 64-bit.

---

### Post by heffo_j on 2006-06-10
Hi there,

I've got the same problem as dief-eh?. I've upgraded FF 3 times today. 1st using the auto update process but still running 1.5.0.2.. Second time, using the script above; but still running 1.5.0.2, and 3rd, auto update told me that a new version of FF was waitng to be upgraded so I gave it a go once more; still 1.5.0.2.. And yes I went out of FF and restarted each time. I even rebooted but to no avail.

What next?

John

---

### Post by heffo_j on 2006-06-10
I've had a read out of /usr/bin/firefox -v. Here is what mine says:

Mozilla Firefox 1.5.0.2, Copyright (c) 1998 - 2006 mozilla.org

What am I to understand form this?

John

---

### Post by aysiu on 2006-06-10
heffo_j, can you paste these commands in the terminal and see what version you get? ```
cd /opt/firefox
./firefox
```

---

### Post by heffo_j on 2006-06-10
G'day Aysiu,

When I post the above it opens FF in my homepage. Incidently, after I posted my previous post I tried the script you offered. It did the trick. I am now running on 1.5.0.4. Thanks for the tip.

John

---

### Post by dief-eh? on 2006-06-10
[QUOTE=aysiu]heffo_j, can you paste these commands in the terminal and see what version you get? ```
cd /opt/firefox
./firefox
```[/QUOTE]

hello aysiu,
looks like heffo_j got the script to work, but i'm still having trouble.

the ./firefox line, above, still shows 1.5.0.2, btw. 

nano's script barfs (?) at:
Linking launcher to new Firefox

Leaving `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
ln: creating symbolic link `/usr/bin/firefox' to `/opt/firefox/firefox': File exists
Previous command did not complete successfully. Exiting.

hth someone.

---

### Post by Patsoe on 2006-06-10
Firefox security updates are also made available through Ubuntu's own Update Manager. It updated to 1.5.0.4 here for me yesterday morning, so you should see it too by now. Basically, that makes the thread obsolete :)

---

### Post by aysiu on 2006-06-10
[QUOTE=dief-eh?]hello aysiu,
looks like heffo_j got the script to work, but i'm still having trouble.

the ./firefox line, above, still shows 1.5.0.2, btw. 

nano's script barfs (?) at:
Linking launcher to new Firefox

Leaving `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
ln: creating symbolic link `/usr/bin/firefox' to `/opt/firefox/firefox': File exists
Previous command did not complete successfully. Exiting.

hth someone.[/QUOTE]
If you get that error, it means you've already installed Firefox to the /opt directory (which is where nanotube's script is trying to install it).

In that case, try ```
gksudo firefox
``` and then click **Help** and **Check for Updates**.

---

### Post by dief-eh? on 2006-06-10
[QUOTE=aysiu]If you get that error, it means you've already installed Firefox to the /opt directory (which is where nanotube's script is trying to install it).

In that case, try ```
gksudo firefox
``` and then click **Help** and **Check for Updates**.[/QUOTE]
thank you for your reply. gksudo firefox produced a second firefox window with a 1.5.0.4, but without the bookmarks etc. in 1.5.0.2. will closing .0.2 and restarting nuke the bookmarks? 
yours in newbie confusion.

---

### Post by aysiu on 2006-06-10
Eek. Sorry. I should have said to close the old Firefox before you run ```
gksudo firefox
``` which runs Firefox as the root user (which is why your personal settings--bookmarks and such--wouldn't be there, as you're not root), so you can get the updates to 1.5.0.4.

Once you update that, close it, and then run Firefox as a regular user. It should now be 1.5.0.4.

---

### Post by dief-eh? on 2006-06-10
[QUOTE=aysiu]Eek. Sorry. I should have said to close the old Firefox before you run ```
gksudo firefox
``` which runs Firefox as the root user (which is why your personal settings--bookmarks and such--wouldn't be there, as you're not root), so you can get the updates to 1.5.0.4.

Once you update that, close it, and then run Firefox as a regular user. It should now be 1.5.0.4.[/QUOTE]
no worries, mite! thanks for your help. for any other out-there newbies' info, i just closed off my 1.5.0.2 firefox, re-ran the gksudo firefox, (whether i needed to or not!), re-started firefox, et viola! (as they say in france...) a fresh, shiny firefox 1.5.0.4! 

merci beaucoup. mille grazie! hai. danke. one less mystery in the universe.

---

### Post by fragos on 2006-06-10
Firefox 1.5.0.4 was available a couple of days ago as an upgrade for 32 bit and it came up last night for AMD64.  A little patience and it came.

---

### Post by user1397 on 2006-06-10
[quote=aysiu]On the same site, *nanotube* also has a script for installing Swiftfox, for you 64-bit users out there.[/quote]actually, swiftfox is not only for 64-bit amd's, it's also for 32-bit amd's (i have tried it on my amd athlon xp and it worked)

---

### Post by aysiu on 2006-06-10
[QUOTE=erik1397]actually, swiftfox is not only for 64-bit amd's, it's also for 32-bit amd's (i have tried it on my amd athlon xp and it worked)[/QUOTE]
And Nanotube's script asks you which architecture you're using and installs the appropriate version of Swiftfox.

---

### Post by user1397 on 2006-06-10
[quote=aysiu]And Nanotube's script asks you which architecture you're using and installs the appropriate version of Swiftfox.[/quote]ah ok, now it makes sense

---

### Post by Nordoelum on 2006-06-12
Thank you for this guide :D

---

### Post by dewclaw82 on 2006-06-23
[QUOTE=aysiu] I would also like to mention that *nanotube* has created [a script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5) for installing the latest Firefox. [/QUOTE]

Thank you aysiu for the direction and thanks nanotube for the wonderful script.  The rest of my upgrade to Dapper went wonderfully but I was struggling with Firefox](*,)  until I found this post.  The script worked like a charm.:-D  IMHO, the script should be a sticky on the updates page with a cross reference to or from the Newbies pages.

---

### Post by termite on 2006-08-31
Thanks for nanotube for the original script for this.  I just modified it to install the new beta.

Anyway, here goes:
[LIST=1]
[*] Download the attached file.
[*] Switch to the directory you downloaded the file to and type ```
gunzip installnewfirefox.sh.gz
```
[*] Type ```
chmod +x installnewfirefox.sh
```
[*] Execute the script by typing ```
./installnewfirefox.sh
```
[*] Choose your localization.
[*] Watch the script in action...
[*] Enjoy firefox!
[/LIST]

Note: you may want to install the Nightly Tester Tools extension ([http://users.blueprintit.co.uk/~dave/web/firefox/buildid/nightly.html]("http://users.blueprintit.co.uk/~dave/web/firefox/buildid/nightly.html")) to make your extensions compatible with this new version.  Warning: some extensions will break!

---

### Post by Ahriman on 2006-09-01
Looks good. No problems during installation, and it seems to run OK.

Do you know of a way I can run this and normal Firefox side-by-side? This seemed to take over the already installed one. During install, I got the following code:

```
Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
Adding `local diversion of /usr/bin/mozilla-firefox to 'usr/bin/mozilla-firefox.ubuntu'
```
I should be able to rename them back if FF2.0 goes pear-shaped, right?

---

### Post by termite on 2006-09-01
Undo instructions (adapted from [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion))

Restore links in /usr/bin/firefox: ```
sudo rm /usr/bin/firefox
 sudo dpkg-divert --rename --remove /usr/bin/firefox
```
Restore links in /usr/bin/mozilla-firefox: ```
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
```
Restore your old profile: ```
rm -rf ~./mozilla
cp -R ~/.mozilla_backup<tab> ~/.mozilla
```
Delete new firefox: ```
sudo rm -r /opt/firefox
```

---

### Post by Anonii on 2006-09-01
nevermind, I rebooted and its all right. Firefox2.0 is the default browser now.

---

### Post by Ahriman on 2006-09-01
> **termite said:**
> The script backs up your old preference in ~/.mozilla_backup (followed by some stuff). The code: ..... 
Thanks man, to be honest, I don't think I will be removing this, but it never hurts to have an out planned, especially with Beta software.

What theme are you using for it?

---

### Post by termite on 2006-09-01
noia 2.0 extreme.

I love inline spell checking! And close buttons on tabs!  Yay!

---

### Post by ago on 2006-09-01
I had some larger fonts in the menu-bar than others applications

If it happens to you:

about:config > layout.css.dpi > value = X

where X is the number you see executing $xdpyinfo|grep resolution

---

### Post by hush on 2006-09-02
adam@adam-desktop:~$ gunzip installnewfirefox.sh.gz
gunzip: installnewfirefox.sh.gz: No such file or directory

?

---

### Post by domino on 2006-09-02
hush, installnewfirefox.sh.gz shoud be in your Home driectory. not you deskop. this sould do it:

cd ~
gunzip installnewfirefox.sh.gz

edit/added:

Jut finished installing. Works great and using the nightly-1.1 extension. I have 15 extensions and all but 3 didn't work. Heck, even my Ubuntu Human Theme 1.1 still works 8-) .

thanks for the script =D>

---

### Post by heinouskyle on 2006-09-02
I'm having a strange problem. I suspect it's got something to do with permissions, but I'm not sure. I don't know where to go to fix that either.

The problem is that I can't login to certain websites. I've tried clearing my cache and cookies, restarting FF, and restarting the computer.

Actually I can login, but I don't stay logged in. As soon as I change pages, I'm logged back out again.

---

### Post by termite on 2006-09-02
I'm not sure I can help, but I'll try.  Please give more details (what do you mean by logging on?  What websites, etc)

---

### Post by heinouskyle on 2006-09-02
> **termite said:**
> I'm not sure I can help, but I'll try.  Please give more details (what do you mean by logging on?  What websites, etc)

When I log in to a website, like hotmail or deviantart.com, it stores a cookie telling the website that I'm logged in everytime I get a new page. The problem is that Firefox is not storing that cookie, and I have to keep putting in my username and password for that site.

---

### Post by termite on 2006-09-02
Try changing to your home directory and typing: ```
sudo chown -R <username>:<username> .mozilla
``` (replace <username> with your username, without < and >)

Then restart FF and see if it works.

---

### Post by heinouskyle on 2006-09-02
I went back to the non-beta Firefox for now. Much easier than fiddling around with permissions and stuff.

---

### Post by termite on 2006-09-03
so my instructions to undo the changes worked?

---

### Post by calvinthomas on 2006-09-03
Is it possible to get flash working in this beta? The beta looks good!

Calv

---

### Post by termite on 2006-09-03
My flash worked out of the box, minus sound.  I got sound back by restarting the computer.

Does yours not work at all?

---

### Post by calvinthomas on 2006-09-03
Problem solved, first time using script I had problems so compiled directly from source (I forgot I did that sorry!) and hence flash didn't work, I now used script and everything works really well now!

Calv

---

### Post by angrykeyboarder on 2006-09-05
> **termite said:**
> 
```
sudo dpkg-divert --divert /usr/bin/firefox --rename /usr/bin/firefox.ubuntu
sudo dpkg-divert --divert /usr/bin/mozilla-firefox --rename /usr/bin/mozilla-firefox.ubuntu
``` That should do it, though I'm not 100% sure about the last step.

[SIZE=3]Guess what? You were ***wrong*** about the last step.[/SIZE]

I have a couple of suggestions.:[INDENT]1). Don't post scripts like this unless you're going to also post one to undo it (or post an **accurate** method for manually undoing what the script did).

2).  Don''t post stuff like what's above (the commands to suppoedly undo the diversions) if you don't know for a ***fact*** that it works.

Not only does it not work, but it broke my Firefox installation.  Two manual dpkg installs and purges and several manually deleted and added symlinks later, I got it back.
[/INDENT]I learned a lesson from this.  I hope you did too.

---

### Post by termite on 2006-09-05
Your screen name clearly suits you.

Anyway, thanks for the heads up. I'll get rid of the undo part. I'd also appreciate any ideas you have on the undo.

Edit: Posted new undo instructions.  Hopefully these work.

---

### Post by johnny.olai on 2006-09-06
Thanks alot, man!

Great script, worked like a dream :)

---

### Post by xaos5 on 2006-09-06
These step will show how to install Firefox 2 beta 2 from the i686 precompiled package on [http://www.mozilla.org/projects/bonecho/all-beta.html](http://www.mozilla.org/projects/bonecho/all-beta.html)

_Steps Described below_
1. untar the compressed file
2. move and rename the uncompressed folder to /opt/
3. Make sure firefox 2 can read firefox 1.x plugins
4. Make a Desktop Icon with a text editor

WARNING: I take no responsibility for any damage done to your computer in any way. Please remember this is a beta version and intended for testers only. I assume you have a basic understanding of the bash shell.


**Step one:**```
tar xvf firefox-2.0b2.tar.gz
```
**Step two:**```
sudo mv firefox/ /opt/firefox2-beta2
```
**Step three:**```
sudo ln -s /usr/lib/firefox/plugins /opt/firefox2-beta2/plugins
```
**Step four:**```
/usr/share/applications/firefox2.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Firefox Web Browser 2.0 Beta 2
Comment=Browse the World Wide Web
GenericName=Web Browser
Exec=/opt/firefox2-beta2/firefox %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=/opt/firefox2-beta2/icons/mozicon128.png
Categories=Application;Network;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png
StartupWMClass=/opt/firefox2-beta2/firefox-bin
```

You should now have an entry of firefox 2.0 beta 2 with the original icon located in the gnome menu (should be in the kde menu also) under internet.

NOTE: You can only run one version at a time, if firefox 1.5 (for example) is open and you select firefox 2.0 beta 2, it will launch firefox 1.5 and vise versa. If there is a way around this behavior please let me know.

---

### Post by Psquared on 2006-09-09
What does this script do that just installing the tarball (as posted in another thread) doesn't do?? Seems like the tarball is easier and leaves the Firefox 1.5 intact.

---

### Post by termite on 2006-09-09
Installs and redirects default links.  It does leave 1.5 intact. Though my earlier undo instructions didn't work, the new ones do.

---

### Post by Psquared on 2006-09-09
> **termite said:**
> Installs and redirects default links.  It does leave 1.5 intact. Though my earlier undo instructions didn't work, the new ones do.

ok, thanks. any differences with an AMD as opposed to an intel cpu?

---

### Post by J.Pulumbarit on 2006-09-11
i get this error when i ./installnewfirefox.sh

tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now
Previous command did not complete successfully. Exiting.

what am i doing wrong?

---

### Post by termite on 2006-09-11
> ok, thanks. any differences with an AMD as opposed to an intel cpu?[/quote\
There are builds out there compiled for AMD, this is the general will-run-on-anything build.

[i get this error when i ./installnewfirefox.sh

tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now
Previous command did not complete successfully. Exiting.

what am i doing wrong?
Do you have a /opt directory?  If not, use
```
sudo mkdir /opt
```

---

### Post by aswells on 2006-09-12
I have a question about the undo-code you posted. When you wrote <tab>, should I press the tab button or leave that in the command? Please excuse me if this is a stupid question, I am pretty new to linux in any form.

---

### Post by termite on 2006-09-12
Press tab :)

---

### Post by p.i.m.p on 2006-09-13
```
bash: ./installnewfirefox.sh.gz: cannot execute binary file

```
am i the only one who is having this problem?

---

### Post by ~LoKe on 2006-09-13
> **p.i.m.p said:**
> ```
bash: ./installnewfirefox.sh.gz: cannot execute binary file

```
am i the only one who is having this problem?

Yep.  You need to do the gunzip first. =D

**EDIT:** None of my themes are working, now.  Not even Noia 2.0 eXtreme.  Whuch ones still work?
**EDIT2:** All my extensions stopped working, too. -_-

---

### Post by termite on 2006-09-14
Get the Noia update: [www.deviantart.com/deviation/4266778](www.deviantart.com/deviation/4266778)

For extentions, get Nightly Tester Tools: [http://users.blueprintit.co.uk/~dave/web/firefox/buildid/index.html](http://users.blueprintit.co.uk/~dave/web/firefox/buildid/index.html)

If you need help with either, post here and I'll do my best.

---

### Post by optimusxprime81 on 2006-09-14
I get this message when trying to install this Beta version of Firefox.

gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Previous command did not complete successfully. Exiting.

what's wrong? help....:(

---

### Post by ~LoKe on 2006-09-14
Bah.  I thought I had the Nightly Tester extension. I used to use it, but may have forgotten to install it when I started with Ubuntu.

Thanks. :o

---

### Post by termite on 2006-09-14
> I get this message when trying to install this Beta version of Firefox.

gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Previous command did not complete successfully. Exiting.

what's wrong? help....
Hmm...seems you're just timing out to that server.  Try again later, I suppose.  The server seems to be working for me, but it is a bit slow.

Post again if you can't get it working later.

---

### Post by ciscosurfer on 2006-09-14
@termite (or anyone here, for that matter),

How does FFb2 compare with Swiftfox (in terms of speed, etc.)

---

### Post by termite on 2006-09-14
Swiftfox is just compiled for particular processors.  It will be faster than this beta, no doubt.  If you get a build from [http://www.getswiftfox.com/br18.htm](http://www.getswiftfox.com/br18.htm) you'll be up to date with the development of the new beta on swiftfox.

By the way, the release candidate of the final firefox 2.0 will be available some time in the next two weeks.  It will probably become the final version.

---

### Post by ciscosurfer on 2006-09-14
Thanks...I use Swiftfox because of the speed increase and b/c of how it is setup for specific processors as opposed to regular Firefox.  I will check that link as it looks promising (didn't know it was there, so thanks!)  I appreciate the prompt response!

---

### Post by ciscosurfer on 2006-09-14
Just a quick update: I downloaded the branch build (one.eight) of Swiftfox and absolutely love it...for those who do not want to acutally install it, allowing your previous builds of Firefox or Swiftfox to still function correctly, you simply need to go to the directory where you extracted the files and run ./swiftfox or ./firefox (this way, you don't need to install it, per se, and can run it from the directory, thereby maintaining your other builds in their original compilations.)

Thanks again, Termite, for the heads up!!!

---

### Post by optimusxprime81 on 2006-09-14
so I've downloaded the Beta2 version, is it normal for mplayer and all that not to run in this version?

---

### Post by ciscosurfer on 2006-09-14
No, you just need to have it setup correctly.  Btw, sometimes, even within my regular Firefox or Swiftfox with all plugins loaded, linked, etc., I encounter some problems with playback.

---

### Post by jave on 2006-09-15
This HOWTO is great!  Except that it doesn't work with my PowerPC equipped Mac.... :)

---

### Post by termite on 2006-09-15
Hmmm.  I wonder if there's a different version of firefox for linux on macs.  Anyone know?

---

### Post by David_Scott_1904 on 2006-09-15
Hi

The script fails for me, with the following error:

gpg: Signature made Thu 31 Aug 2006 12:35:33 BST using DSA key ID 1AF32821
gpg: BAD signature from "Mozilla Software Releases <releases@mozilla.org>"
Previous command did not complete successfully. Exiting.

Any idea what the problem is?

Thanks

---

### Post by domino on 2006-09-16
> **termite said:**
> Hmmm.  I wonder if there's a different version of firefox for linux on macs.  Anyone know?

OS X has the same features as Linux build and has the same build number. I'm using the same extensions but different themes on both Linux and OS X beta build.

---

### Post by Dinerty on 2006-09-16
Great guide mate, works a treat I do quite like the look of firefox 2, I think if it had a option to "duplicate" tab's like Opera 9 does, I may be tempted ;)

---

### Post by termite on 2006-09-16
There's a Duplicate Tab extension (google it).  I'm not sure if it's up to date with FF2, but it's worth a shot.

Will answer questions later...

---

### Post by bswilson on 2006-09-28
So you'd like to try the newly released **Firefox 2.0 Release Candidate**, but you're unsure how to do it?  Here's how to download, install, and configure the US English version on Ubuntu 6.06LTS.

1. Download Firefox 2.0 Release candidate from the Web site.  Be sure to get the Linux version!

```
$ cd /tmp
$ wget ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0rc3/linux-i686/en-US/firefox-2.0rc3.tar.gz
```

2. Unpack the file.  We're going to install to the **/opt** directory.

```
$ sudo gunzip /tmp/firefox-2.0rc3.tar.gz
$ cd /opt
$ tar xvf firefox-2.0rc3.tar.gz
```

3. It is installed now!  All you have to do is run **/opt/firefox/firefox**.  I have created a desktop icon for that program, so you can easily double-click on it to launch.

4. Let's copy our plugins over so that they work (Flash 7, RealPlayer 10, etc.)

```
$ sudo cp /usr/lib/mozilla/plugins /opt/mozilla/plugins
```

All done!  Happy surfing.  The original version of Firefox 1.5.x that comes with Ubuntu will be preserved; to launch it simply run **/usr/bin/firefox**.
 
 
*Edit: Updated commands for Firefox 2.0rc3 -- 2006-10-18*

---

### Post by kipeloff on 2006-09-29
Hello, 
**termite**, many thanks for undo instructions, it helped alot.

---

### Post by termite on 2006-09-29
Good good :)

Glad to hear they work.  Can't wait for 2.0 final, hopefully in edgy!

---

### Post by kipeloff on 2006-09-29
I needed to undo the Firefox from beta2 to 1.5, because during rc1 install something went wrong, and installation complained about (directory /opt/firefox already exists, however I copied to /opt/firefox.old).
Anyway I restored old Firefox and installed rc1 once more. It is working fine.:)

---

### Post by masamunex111 on 2006-09-30
When I install firefox, it gives an error, it does not have the permission to  open and read the cache of my profile. what do i do?

---

### Post by Stormx on 2006-10-15
Small problem folks. FFB2 seems to be working fine, except it doesn't render fonts well with letter-spacing in CSS: [http://www.dython.net](http://www.dython.net), It may just be that I use the windows fonts for firefox? I dunno...

---

### Post by shekhark on 2006-10-24
Will this script be updated for the final release of Firefox 2.0, scheduled for sometime today? I would just install it from the Mozilla web-site, but had so many problems with the beta releases that I found this script was the only way to successfully install and configure RC2.

---

### Post by sk8dork on 2006-10-24
hey guys, this site has a quick and easy (much like this thread i'm sure) install script updated for the final release:
 [click me]("http://everythingelse.wordpress.com/2006/07/15/howto-install-firefox-20-bon-echo-in-ubuntu/?namhuy.org")

worked great for me. it pretty much downloads the latest version from the firefox ftp and installs it for you.

---

### Post by jwdvd on 2006-10-24
i got......

-----------------------------------------------------------------------------

Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Previous command did not complete successfully. Exiting.

-----------------------------------------------------------------------------

DAMN :-(

---

### Post by bswilson on 2006-10-24
So you'd like to try the newly released **Firefox 2.0**, but you're unsure how to do it?  Here's how to download, install, and configure the US English version on Ubuntu Dapper **_or_** Edgy.

1. Download Firefox 2.0 from the Mozilla FTP or Web site (command below shows using wget to download it from the FTP site).  Be sure to get the Linux version!  Place this file in your **/tmp** directory.

```
$ cd /tmp
$ wget ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0/linux-i686/en-US/firefox-2.0.tar.gz
```

2. Unpack the file.  We're going to install to the **/opt** directory.  This will allow you to keep the version of Firefox that comes with Dapper/Edgy intact. 

```
$ cd /opt
$ sudo tar -zxvf /tmp/firefox-2.0.tar.gz
```

3. Let's copy our plugins over so that they work (Flash 7, RealPlayer 10, etc.).  This step will copy any plugins you already had over to work with Firefox 2.0.  This step will not install any new plugins; that's a separate thread.  ;) 

```
$ sudo cp /usr/lib/mozilla/plugins /opt/mozilla/plugins
```

4. It is installed now!  All you have to do is run **/opt/firefox/firefox**.  You can create a desktop icon (e.g., launcher) for that program and/or an icon on the Gnome panel, so you can easily double-click on it to launch.  

4a. Create a Gnome panel icon for Firefox 2.0, by saving this code as **~/.gnome2/panel2.d/default/launchers/firefox2.panel**.  Just paste this into a gedit or vi document:
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Exec=/opt/firefox/firefox
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=mozilla-firefox.png
Categories=Application;Network;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;
StartupWMClass=Firefox-bin
TryExec=
X-GNOME-DocPath=
Name[ca]=Navegador web Firefox
GenericName[ca]=Navegador web
Comment[ca]=Navegueu per el web
Name[cs]=Firefox Webový prohlíže&#269;
GenericName[cs]=Webový prohlíže&#269;
Comment[cs]=Prohlížení stránek World Wide Webu
Name[de]=
GenericName[de]=
Comment[de]=Im Internet surfen
Name[es]=Navegador web Firefox
GenericName[es]=Navegador web
Comment[es]=Navegue por la web
Name[fa]=&#1605;&#1585;&#1608;&#1585;&#1711;&#1585; &#1575;&#1740;&#1606;&#1578;&#1585;&#1606;&#1578;&#1740; Firefox
GenericName[fa]=&#1605;&#1585;&#1608;&#1585;&#1711;&#1585; &#1575;&#1740;&#1606;&#1578;&#1585;&#1606;&#1578;&#1740;
Comment[fa]=&#1589;&#1601;&#1581;&#1575;&#1578; &#1588;&#1576;&#1705;&#1607; &#1580;&#1607;&#1575;&#1606;&#1740; &#1575;&#1740;&#1606;&#1578;&#1585;&#1606;&#1578; &#1585;&#1575; &#1605;&#1585;&#1608;&#1585; &#1606;&#1605;&#1575;&#1740;&#1740;&#1583;
Name[fi]=Firefox-webselain
GenericName[fi]=Webselain
Comment[fi]=Selaa Internetin www-sivuja
Name[fr]=Navigateur Web Firefox
GenericName[fr]=Navigateur Web
Comment[fr]=Navigue sur Internet
Name[hu]=Firefox webböngész&#337;
GenericName[hu]=Webböngész&#337;
Comment[hu]=A világháló böngészése
Name[it]=Firefox Browser Web
GenericName[it]=Browser Web
Comment[it]=Esplora il web
Name[nb]=Firefox Nettleser
GenericName[nb]=Nettleser
Comment[nb]=Surf på nettet
Name[nl]=Firefox webbrowser
GenericName[nl]=Webbrowser
Comment[nl]=Verken het internet
Name[nn]=Firefox Nettlesar
GenericName[nn]=Nettlesar
Comment[nn]=Surf på nettet
Name[no]=Firefox Nettleser
GenericName[no]=Nettleser
Comment[no]=Surf på nettet
Name[pl]=Przegl&#261;darka WWW Firefox
GenericName[pl]=Przegl&#261;darka WWW
Comment[pl]=Przegl&#261;danie stron WWW
Name[pt]=Firefox Navegador Web
GenericName[pt]=Navegador Web
Comment[pt]=Navegue na Internet
Name[pt_BR]=Navegador Web Firefox
GenericName[pt_BR]=Navegador Web
Comment[pt_BR]=Navegue na Internet
Name[sk]=Internetový prehliada&#269; Firefox
GenericName[sk]=Internetový prehliada&#269;
Comment[sk]=Prehliadanie internetu
Name[en]=Firefox Web Browser
GenericName[en]=Web Browser
Comment[en]=Browse the World Wide Web
Name=Firefox Web Browser
GenericName=Web Browser
Comment=Browse the World Wide Web

```

4b. Create a Gnome desktop launcher for Firefox 2.0, by saving this code as **~/Desktop/firefox2.desktop**.  Just paste this into a gedit or vi document:
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Elmo's World
TryExec=/opt/firefox/firefox
GenericName=Web browser
Exec=/opt/firefox/firefox
Terminal=false
Categories=Application;Qt;Network;WebBrowser;X-Ximian-Main;X-Ximian-Toplevel
Icon=firefox.png
MimeType=text/html;text/xml;application/xhtml+xml;
Comment=Web Browser
Type=Application
GenericName[en]=Start Firefox 2
Name[en]=Start Firefox 2
Comment[en]=Start Firefox 2 

```

All done!  Happy surfing.  The original version of Firefox 1.5.x that comes with Ubuntu will be preserved; to launch it simply run **/usr/bin/firefox**.
 
 
*Edit 2006-10-25 13:17ET: Updated post to include code for Gnome panel and Gnome desktop launchers.*

---

### Post by aysiu on 2006-10-25
I've just tested it, and this script does work on Edgy for Firefox 2.0.

---

### Post by upanda on 2006-10-25
Dear all,
I run this following command to install firefox 2.0.

```

user@st4:~$ ./installnewfirefox.sh

```

but after finished download tar file, it show the following text!

```

Downloading Firefox from the Mozilla site

--19:58:47--  http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0b2/linux-i686/en-US/firefox-2.0b2.tar.gz
           => `firefox-2.0b2.tar.gz'
Connecting to 192.168.1.253:8888... connected.
Proxy request sent, awaiting response... 302 Moved Temporarily
Location: http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0b2/linux-i686/en-US/firefox-2.0b2.tar.gz [following]
--19:58:51--  http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0b2/linux-i686/en-US/firefox-2.0b2.tar.gz
           => `firefox-2.0b2.tar.gz'
Connecting to 192.168.1.253:8888... connected.
Proxy request sent, awaiting response... 200 OK
Length: 9,598,975 (9.2M) [application/x-gzip]

100%[==================================================================>] 9,598,975     15.74K/s    ETA 00:00/

20:09:38 (14.53 KB/s) - `firefox-2.0b2.tar.gz' saved [9598975/9598975]


Downloading Firefox signature from the Mozilla site

--20:09:38--  http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0b2/linux-i686/en-US/firefox-2.0b2.tar .gz.asc
           => `firefox-2.0b2.tar.gz.asc'
Connecting to 192.168.1.253:8888... connected.
Proxy request sent, awaiting response... 302 Moved Temporarily
Location: http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0b2/linux-i686/en-US/firefox-2.0b2.ta r.gz.asc [following]
--20:10:12--  http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0b2/linux-i686/en-US/firefox-2.0b 2.tar.gz.asc
           => `firefox-2.0b2.tar.gz.asc'
Connecting to 192.168.1.253:8888... connected.
Proxy request sent, awaiting response... 200 OK
Length: 186 [text/plain]

100%[==================================================================>] 186           --.--K/s

20:10:14 (4.03 MB/s) - `firefox-2.0b2.tar.gz.asc' saved [186/186]


Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, t here may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected beha vior.

gpg: directory `/home/user/.gnupg' created
gpg: new configuration file `/home/user/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/user/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/user/.gnupg/secring.gpg' created
gpg: keyring `/home/user/.gnupg/pubring.gpg' created
gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
?: subkeys.pgp.net: Host not found
gpgkeys: HKP fetch error: Connection timed out
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Previous command did not complete successfully. Exiting.

```

so how should i go on... ? please help me!

---

### Post by motang on 2006-10-25
Hello all, as you all know Firefox 2.0 came out yesterday and I wanted to update mine from 1.5.x to 2.0.  I did a search on the forums and found a script that installs Firefox2.0 beta 2 thanks to termite.  I took the script and modified it to install the final build of Firefox 2.0 on a x86 32 bit processor.
Here are instructions:
1. Download the attached file.
2. Navigate to the directory you downloaded the attached file and type
Code:
```
gunzip installnewfirefox.sh.gz
```

3. Type
Code:
```
chmod +x installnewfirefox.sh
```

4. Execute the script by typing
Code:
```
./installnewfirefox.sh
```

5. Choose your localization.
6. Watch the script in action...
7. Enjoy!

Note: Not all of your themes and extension will work with Firefox 2.0 as of yet, so be cautious.

---

### Post by ales on 2006-10-25
Hello I did these commands right like here but when connectig gpg key it always makes error msg that the  pgp server timed out connection when retrieveng the key and installation stops due to that, that the previous operation did not succeed

---

### Post by sblanzio on 2006-10-25
this worked perfectly with me!
thank you very much! :)

---

### Post by aysiu on 2006-10-25
This is a HowTo, not a support question, so I'm moved it to the HowTo subforums.

---

### Post by dinsx on 2006-10-25
Hi, one question. The script seem to be fine but I'm getting an error when executing this gpg --keyserver subkeys.pgp.net --recv 1AF32821. The error say  :

gpg: AVISO: propiedad insegura del fichero de configuración `/home/daniel/.gnupg/gpg.conf'
gpg: llamadas a programas externos inhabilitadas por permisos inseguros de ficheros.
gpg: error de comunicación con el servidor de claves: Error general
gpg: recepción del servidor de claves fallida: Error general

Can you help me? Do you need that I translate the message error?

---

### Post by dutchmega on 2006-10-25
Swiftfox, the optimized version, based on FF2 final is also out:
[http://getswiftfox.com/debian.htm](http://getswiftfox.com/debian.htm)

---

### Post by sbecerra on 2006-10-25
I don't know much about any of this stuff, but I do speak Spanish. The error message in English is "gpg: WARNING: unsafe permissions on configuration file "/home/daniel/.gnupg/gpg.conf". The solution that I found [here]("http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/step-guide/s1-gnupg-warnings.html") was to execute the following: 

chmod 600 ~/.gnupg/gpg.conf

> **dinsx said:**
> Hi, one question. The script seem to be fine but I'm getting an error when executing this gpg --keyserver subkeys.pgp.net --recv 1AF32821. The error say  :

gpg: AVISO: propiedad insegura del fichero de configuración `/home/daniel/.gnupg/gpg.conf'
gpg: llamadas a programas externos inhabilitadas por permisos inseguros de ficheros.
gpg: error de comunicación con el servidor de claves: Error general
gpg: recepción del servidor de claves fallida: Error general

Can you help me? Do you need that I translate the message error?

---

### Post by DOD1951 on 2006-10-25
Thanks for posting this howto worked a treat. Now on V2 no issues so far. :)

---

### Post by dinsx on 2006-10-25
> **sbecerra said:**
> I don't know much about any of this stuff, but I do speak Spanish. The error message in English is "gpg: WARNING: unsafe permissions on configuration file "/home/daniel/.gnupg/gpg.conf". The solution that I found [here]("http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/step-guide/s1-gnupg-warnings.html") was to execute the following: 

chmod 600 ~/.gnupg/gpg.conf

The solution for me was different but I find the solution thanks to your answer. My problem was that the owner of **~/.mozilla** is the root user and the owner of **~/.gnupg/gpg.conf** is my user, then if I execute the installation script without sudo, fail to create the backup of my old firefox but if I execute it with sudo, fail to execute this **gpg --keyserver subkeys.pgp.net --recv 1AF32821**. My solution was to modify the installation script writing sudo before this **cp -R ~/.mozilla ~/.mozilla_backup_`date -Iseconds`** in the line 85.

Thank you very much.

---

### Post by aysiu on 2006-10-25
Wouldn't it make sense to have you (instead of root) be the owner of ~/.mozilla? ```
sudo chown -R dinsx:disnx /home/disnx/.mozilla
```

By the way, you should probably read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by studentism on 2006-10-25
Yes, and I'm about 99% sure if you aren't the owner of .mozilla you can't install extensions/save bookmarks (beyond the current session)/etc.

---

### Post by bloodniece on 2006-10-25
Here is what fixed the gpg ownership error for me.
```
sudo chown -R root /home/tux/.gnupg/

```

---

### Post by pixelboy on 2006-10-25
Thanks motang. :)

---

### Post by KDayz on 2006-10-25
I get this error when using the script:


Linking launcher to new Firefox

Leaving `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
ln: creating symbolic link `/usr/bin/firefox' to `/opt/firefox/firefox': File exists
Previous command did not complete successfully. Exiting.

---

### Post by KDayz on 2006-10-25
Sorry for double post, I just ran the installer again and it worked this time. Altough I had to navigate to opt/firefox and run firefox.sh and that worked. Firefox told me its not my default browser so I just clicked "Yes" and it works now. Woot Woot!

---

### Post by Greeface on 2006-10-26
Tried it on Dapper and it was working good, but then I got ```
gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Previous command did not complete successfully. Exiting.

```

---

### Post by aysiu on 2006-10-26
Try this: ```
sudo chown -R greeface:greeface /home/greeface
``` and then run the script again. That seems to have solved it for some other people.

Substitute your actual username for *greeface*, of course.

---

### Post by Greeface on 2006-10-26
Ah, actually I just ran it a second time a few moments ago and it worked like a charm!  Awesome script, thanks!

---

### Post by aysiu on 2006-10-26
> **Greeface said:**
> Ah, actually I just ran it a second time a few moments ago and it worked like a charm!  Awesome script, thanks!
I didn't write it. I just modified it to work for Edgy.

Glad it worked out, though.

---

### Post by tetherblood on 2006-10-26
thanks motang,

it all worked perfectly :-D

---

### Post by joncheyne on 2006-10-26
I get stuck at the bit below. It waits bit then times ou as below. I own .mozilla and .gnupg

cheers

Jon

```

gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Previous command did not complete successfully. Exiting.
```

---

### Post by lzydba on 2006-10-26
I am getting the same error as joncheyne.

*EDIT*
I can ping subkeys.pgp.net so it's up, but the keyserver error is still there :confused:

---

### Post by kuberprok on 2006-10-26
Thanks man! This realy was easy!

---

### Post by dinsx on 2006-10-26
> **aysiu said:**
> Wouldn't it make sense to have you (instead of root) be the owner of ~/.mozilla? ```
sudo chown -R dinsx:disnx /home/disnx/.mozilla
```

By the way, you should probably read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Thank you for the information.

---

### Post by Jpfan017 on 2006-10-26
I'm getting this error:

gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
?: subkeys.pgp.net: Connection refused
gpgkeys: HKP fetch error: Connection refused
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Previous command did not complete successfully. Exiting.

I've tried all the other things in this thread, still no luck.

---

### Post by Jpfan017 on 2006-10-26
Ya I'm still getting the same error. 

gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
?: subkeys.pgp.net: Connection refused
gpgkeys: HKP fetch error: Connection refused
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Previous command did not complete successfully. Exiting.

---

### Post by aysiu on 2006-10-26
Try clearing your web browser cache and downloading the script.

I've taken out the bit about verifying the key. It seems to be tripping a lot of people up, and I don't think it's really necessary.

---

### Post by HandGrenade on 2006-10-26
I have the same time-out problem as joncheyne and lyzdba. Does anyone have any suggestions?

---

### Post by aysiu on 2006-10-26
Yes, try this script instead--I got rid of the key verification, which is probably not necessary for installing Firefox:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by motang on 2006-10-26
> **aysiu said:**
> Yes, try this script instead--I got rid of the key verification, which is probably not necessary for installing Firefox:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Wow I didn't know so many people would have problems with the PGP key, thanks for the new script file.

---

### Post by aysiu on 2006-10-26
> **motang said:**
> Wow I didn't know so many people would have problems with the PGP key, thanks for the new script file.
I didn't experience it personally, but I've seen several people have sig verification problems. Honestly, the .tar.gz is probably fine if it's being downloaded straight off Mozilla's server, so I just got rid of that part.

---

### Post by Jeremiah478 on 2006-10-26
Thanks, this worked great.

---

### Post by sumithar on 2006-10-26
Hi
I get the 
"The new Firefox version 2.0 has been installed successfully."
message but my icon on the task bar is still pointing to v1.5, it seems.  Because when I click on the icon and it brings up FF and I click Help/About it says 1.5
In the properties window for the icon it says under command
firefox %u

Should I specify some directory or something?
Thanks

---

### Post by aysiu on 2006-10-26
Maybe the symlink didn't come in for whatever reason?

Can you press Alt-F2 and type ```
/opt/firefox/firefox
``` and see if 2.0 comes up?

---

### Post by sumithar on 2006-10-26
Thanks for the response.
Unfortunately, no.  I had tried the same thing from the same terminal window where I ran the script.

I am still hazy about how programs work in linux.  Is there like a firefox.exe file somewhere?  Does this script create a different exe file in a different directory?  Or is that what you were asking me to do- /opt/firefox is where the script installed v2?

I did some digging around:
the /usr/lib/firefox directory has a file called firefox dt 2006/09/21
the /opt/firefox directory has a file called firefox dt 2006/10/11

Regards

---

### Post by aysiu on 2006-10-26
It's not technically a .exe (.exe files are Windows binaries), but what the script does is download a zipped file from Mozilla.

It then unzips the file to the /opt directory so that you have a new directory called /opt/firefox.

Within the /opt/firefox directory, there is an executable called *firefox*, and the script symlinks (think "shortcut" or "alias") /opt/firefox/firefox to /usr/bin/firefox so that you can just type *firefox* and have that command launch /opt/firefox/firefox.

Can you post the output of these commands? ```
cd /opt/firefox
ls
./firefox
```

---

### Post by sumithar on 2006-10-26
Thanks for that explanation.  I remember reading that the x by the side of the ls listing indicates executable, right.

As it turns out I was wasting your time- I had a theme (Noia) that was messing it all up.  The firefox was upgraded, but the theme kept showing as 1.5. Once I figured that out, uninstalled the theme, and restarted (using the link on the action bar, no less) everything looks fine.

And thanks to foxmarks I can import my bookmarks from work!

Thanks again and sorry to have wasted your time!

---

### Post by aysiu on 2006-10-26
It wasn't a waste of time. You probably understand the backend of things a little bit more now, and you have things working--that's what matters.

---

### Post by gamerchick02 on 2006-10-27
I'd like to say thanks for getting the script together.  It made installing 2.0 so much easier.

Amy

---

### Post by kazbear on 2006-10-27
gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error exit delayed from previous errors
Previous command did not complete successfully. Exiting.

Whats up with this?

---

### Post by AlphaMack on 2006-10-27
Followed the instructions to the letter and I get this:

```
/opt/firefox/run-mozilla.sh: line 166: /opt/firefox/firefox-bin: cannot execute binary file
```

---

### Post by bb002 on 2006-10-28
> **alphasubzero949 said:**
> Followed the instructions to the letter and I get this:

```
/opt/firefox/run-mozilla.sh: line 166: /opt/firefox/firefox-bin: cannot execute binary file
```

Hmmmm....looks like for some reason /opt/firefox/firefox-bin didn't get the executable bit set.
run this in a terminal.
```

sudo chmod +x /opt/firefox/firefox-bin

```
That sould get firefox running.

---

### Post by sawjew on 2006-10-28
All you need to do to install firefox 2.0 final in Edgy is ```
sudo apt-get upgrade
``` and you're done.

---

### Post by jjhart on 2006-10-28
What if I don't want to keep 1.5?  I just want to install 2.0 over the top of 1.5.  I don't want to have 1.5 anymore just 2.0, how do I do that?  Do I install it in /usr/bin instead of /opt?

---

### Post by dhallar on 2006-10-28
I'm using Kubuntu with a KDE desktop. I updated to Firefox 2.0. How do I create an icon/shortcut on my K menu? (*,)

---

### Post by uBo on 2006-10-28
Hey, how do I install the Ubuntu-Firefox 2.0, not the mozilla one in Dapper?

I want to stay with dapper for a while, but want Firefox 2.0

I guess I have to play with the repositories?

---

### Post by Azakus on 2006-10-28
Now that Firefox 2 is officially out, the script needs to be updated.
I just used gedit and auto-replaced all instances of 2.0b2 with 2.0

---

### Post by dave37 on 2006-10-29
Thanks bswilson, that worked great!  Also want to add that with 2.0 the slow loading of pages problem that I and many others had is corrected, at least for me.

---

### Post by MadL on 2006-10-29
I'm also wondering if there's a way to get the Ubuntu-fied Firefox 2.0 without upgrading to Edgy -- I'd like to stay with the Drake for a while longer.

---

### Post by zek725 on 2006-10-29
> **sawjew said:**
> All you need to do to install firefox 2.0 final in Edgy is ```
sudo apt-get upgrade
``` and you're done.

upgraded to edgy [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades). firefox didn't upgrade with it. :( it was >1.5.0.2 in Dapper then when upgraded to Edgy, it was downgraded! :o

---

### Post by zek725 on 2006-10-29
This script only works on Breezy or Dapper.

I'm already in Edgy Eft. Firefox did not upgrade with it. [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Synaptic shows I already have firefox 2.0 installed. Help->About 1.5.0.2! :O ](*,)

---

### Post by aysiu on 2006-10-29
> **zek725 said:**
> This script only works on Breezy or Dapper. Which script are you talking about?

I've tested the one in this link, and it definitely works in Edgy, too:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by zek725 on 2006-10-30
[QUOTE=aysiu;1686551]Which script are you talking about?

I've tested the one in this link, and it definitely works in Edgy, too:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)[/QU

Ah! the one posted by motang. :D

---

### Post by zek725 on 2006-10-30
I've reinstalled Xubuntu 6.10 from scratch successfully (FF2 included). However, the homepage from file:///usr/share/ubuntu-artwork/home/index.html
says "Welcome to Xubuntu 6.06". I thought this was Xubuntu 6.10?

---

### Post by bswilson on 2006-10-30
> **alphasubzero949 said:**
> Followed the instructions to the letter and I get this:

```
/opt/firefox/run-mozilla.sh: line 166: /opt/firefox/firefox-bin: cannot execute binary file
```

Actually, you didn't follow the directions.  My post said to run **/opt/firefox/firefox**, not **/opt/firefox/run-mozilla.sh**.  If you really want to run the latter, just enter the command **sudo chmod 755 /opt/firefox/run-mozilla.sh** to change the privileges.

---

### Post by mishranurag on 2006-10-30
Thanks for the script. I installed firefox 2.0 using this script, and it went well. The only problem is that I cannot see the pages in hindi languages properly which I could see before with firefox 1.5.  I can see the same pages properly in another computer with edgy and firefox 2.0.

Anurag

---

### Post by orbital on 2006-10-31
I installed Firefox using this method, but I'm still missing Java in Firefox. How can I get Java working with this install? I'm running Dapper and with Firefox 1.5 Java worked just fine.

---

### Post by aysiu on 2006-10-31
If you're going to manually "install" Firefox 2.0, I would prefer these instructions:
[http://help.ubuntu.com/community/FirefoxNewVersion](http://help.ubuntu.com/community/FirefoxNewVersion)

But there's also a script that does it automatically:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by orbital on 2006-10-31
Yeah the first link is just how I installed it. Anyways, Java ain't working. I have libjavaplugin.so in the plugins directory /opt/firefox/plugins .

Any ideas?

---

### Post by tep200377 on 2006-10-31
Is This thread a joke ?

---

### Post by orbital on 2006-10-31
> **tep200377 said:**
> Is This thread a joke ?

No?

---

### Post by akudewan on 2006-10-31
@ orbital:

Hi,

Have a look at the [firefox help page]("http://www.mozilla.org/support/firefox/faq#q2.2"). Maybe you could delete that libjavaplugin.so in your /opt/firefox/plugins/ directory, and make the symlink again

> 
On Linux, Firefox requires  JRE 1.4.2 or later.

Firefox is compiled with gcc 3.2.3, so a compatible version of the Java plugin must be used. JRE 1.4.2 contains a compatible plugin.

If you installed the JRE 1.4.2_01 RPM, this plugin is /usr/java/j2re1.4.2_01/plugin/i386/ns610-gcc32/libjavaplugin_oji.so and to install it for Firefox, do the following:

   1. Open a terminal
   2. Change to your Firefox plugins directory
   3. Issue the following command: ln -s /usr/java/j2re1.4.2_01/plugin/i386/ns610-gcc32/libjavaplugin_oji.so



(Note: You can use "locate libjavaplugin_oji.so" to find the appropriate directory, instead of the one mentioned above)

Hope this helps

---

### Post by orbital on 2006-10-31
Thanks alot, I did remove the libjavaplugin.so and made the symlink again. Now everything works like a charm, thanks

---

### Post by sawjew on 2006-10-31
> **zek725 said:**
> upgraded to edgy [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades). firefox didn't upgrade with it. :( it was >1.5.0.2 in Dapper then when upgraded to Edgy, it was downgraded! :o

If you followed those directions then you should have firefox2.0dfsg-0ubuntu.  It's the only one in the edgy repositories.  If you didn't get this then your upgrade didn't work correctly.  Just try ```
sudo apt-get update
``` followed by ```
sudo apt-get upgrade
```

If that doesn't work properly try ```
sudo aptitude upgrade
```

You may have a dependency problem preventing firefox from upgrading and aptitude can often resolve these where apt-get can't.

---

### Post by knichel on 2006-10-31
Just followed all of the directions.  Launched firefox from the new dir and went to help menu->About Firefox and...

Still running 1.5.0.7?  What's up with that?  What did I do wrong?

-- 
Mike

---

### Post by drew_t on 2006-10-31
I've upgraded two machines to Edgy, and have the same situation with both of them.  Synaptic indicates that FF 2.0 is installed, but 1.5.0.7 is what continues to run.  It's not just the Help --> About screen that indicates this; the Tools menu continues to have separate entries for "Extensions" and "Themes" instead of 2.0's combined "Add-Ons" entry.

---

### Post by MissMachine on 2006-10-31
same problem as the previous two posters^

---

### Post by aysiu on 2006-10-31
Can anyone experiencing this problem (Edgy but with 1.5.0.7 instead of 2.0) post the output of these commands? ```
cd /opt
ls
firefox.ubuntu
```

---

### Post by TiredHippo on 2006-10-31
I think I may have and idea. It worked for me.

Close all your Firefox windows and run

```
/usr/bin/firefox.ubuntu
```

Or if not then

```
/usr/lib/firefox/firefox
```

You should be running 2.0 now. Check in the Help >About menu.

Now all you have to do is remove the old link.

```
sudo rm -rf /usr/bin/firefox
```

And create a new one

```
sudo ln -s /usr/bin/firefox.ubuntu /usr/bin/firefox
```

Or, because firefox.ubuntu is just a link itself to /usr/lib/firefox/firefox, you could also do...

```
sudo ln -s /usr/lib/firefox/firefox /usr/bin/firefox
```

I hope this helps.

---

### Post by Sgurd on 2006-10-31
> **aysiu said:**
> 
There's also a script that does it automatically:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

I used the script on my Dapper box.

I have Firefox 2.0 in /opt but my html files all open in 1.5, 'Firefox Web Broswer' from the menu bar, 'firefox' from terminal, and the link in my panel all launch 1.5.  

Where is this set at?  And other default program settings?  Thanks in advance - JD

---

### Post by aysiu on 2006-10-31
> **Sgurd said:**
> I used the script on my Dapper box.

I have Firefox 2.0 in /opt but my html files all open in 1.5, 'Firefox Web Broswer' from the menu bar, 'firefox' from terminal, and the link in my panel all launch 1.5.  

Where is this set at?  And other default program settings?  Thanks in advance - JD
Try pasting these commands in the terminal--see if it makes any difference. ```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
```

---

### Post by Sgurd on 2006-10-31
> **aysiu said:**
> Try pasting these commands in the terminal--see if it makes any difference. ```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
```

[SIZE="3"]Worked wonderfully; Thank you![/SIZE] - JD

---

### Post by Sgurd on 2006-11-01
I can run Firefox once, but if I close it and try to open it again I get:
[[IMG]http://img267.imageshack.us/img267/3406/closefirefoxcx2.png[/IMG]](http://imageshack.us)


I wouldn't mind goin' back to 1.5 for now.  I can use the uninstall script I'm sure.  Do I need something to reverse these commands:

```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
```

---

### Post by aysiu on 2006-11-01
Here's the reverse: ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
```

---

### Post by Sgurd on 2006-11-01
Thanks Again- JD

---

### Post by mishranurag on 2006-11-02
Help Please!! I cannot read hindi on this firefox 2.0, and I cannot remove firefox 2.0 either!!

---

### Post by aysiu on 2006-11-02
> **mishranurag said:**
> Help Please!! I cannot read hindi on this firefox 2.0, and I cannot remove firefox 2.0 either!!
I don't know anything about reading Hindi, but you can remove Firefox 2.0 by following [these instructions](https://help.ubuntu.com/community/FirefoxNewVersion#head-51054869b8a40ea50859b0163c806e76f882499c).

---

### Post by frogotronic on 2006-11-03
> **tep200377 said:**
> Is This thread a joke ?

well, I laughed until I cried :)

---

### Post by kroiz on 2006-11-04
> **TiredHippo said:**
> I think I may have and idea. It worked for me.

Close all your Firefox windows and run

```
/usr/bin/firefox.ubuntu
```Or if not then

```
/usr/lib/firefox/firefox
```You should be running 2.0 now. Check in the Help >About menu.

Now all you have to do is remove the old link.

```
sudo rm -rf /usr/bin/firefox
```And create a new one

```
sudo ln -s /usr/bin/firefox.ubuntu /usr/bin/firefox
```Or, because firefox.ubuntu is just a link itself to /usr/lib/firefox/firefox, you could also do...

```
sudo ln -s /usr/lib/firefox/firefox /usr/bin/firefox
```I hope this helps.

Thanks that worked!
I wonder, how is it, that I needed to close firefox in order for this to work?
also I guess I now also have the old version. how do I uninstall it please.

---

### Post by wapowell on 2006-11-06
Has anyone that also uses SCIM updated to FF2 on Dapper?  I tried to run the script from [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox).  It says everything went fine, but fF crashes as soon as I try to launch it.  So I uninstalled it.  Then I was looking at [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) and I see warnings about needing to manually build firefox if you are using SCIM, but I can't find the information about the rebuild.

Has anyone tried this yet?

-Bill

---

### Post by mishranurag on 2006-11-06
Thanks aysiu! I could remove firefox 2.0 from my computer. I wonder how will we get the 2.0 packages from repository!

---

### Post by sKuarecircle on 2006-11-07
> **aysiu said:**
> Try pasting these commands in the terminal--see if it makes any difference. ```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
```

This worked for me as well. shot

---

### Post by antonjah on 2006-11-07
Thanks alot, finally!

---

### Post by mokmoki on 2006-11-07
hmm, tried this one out, but when i run /opt/firefox/firefox and go to Help->About Firefox, version says its still 1.5.0.7? i downloaded the firefox-2.0.tar.gz, so its supposed to be version 2 right?

---

### Post by mokmoki on 2006-11-07
update: sorry, just forgot to restart firefox after install... thanks for the guide!

---

### Post by notoriousdbp on 2006-11-09
Just one comment - I would have hoped that Dapper with it's "Long Term Support" would have had this in the repositories by now.  It's time the developers made good on their promise of "Long Term Support" and sorted this out.  Am I the only one who think Dapper has been left behind a bit lately?

---

### Post by matthew on 2006-11-09
> **notoriousdbp said:**
> Just one comment - I would have hoped that Dapper with it's "Long Term Support" would have had this in the repositories by now.  It's time the developers made good on their promise of "Long Term Support" and sorted this out.  Am I the only one who think Dapper has been left behind a bit lately?I think you have misunderstood what is meant by "long term support." Ubuntu will make sure that Dapper receives ***security*** updates for 3 full years on the desktop and even longer on the server. This does not have anything to do with the latest software releases, just stability and security. If you want the latest packages you will have to hope it gets backported, learn to do this yourself, upgrade to the newest version of Ubuntu, or learn how to install/compile software. Sorry.

---

### Post by eeried on 2006-11-10
> I would have hoped that Dapper with its "Long Term Support" would have had this in the repositories by now. It's time the developers made good on their promise of "Long Term Support" and sorted this out.

Precisely

> I think you have misunderstood what is meant by "long term support." Ubuntu will make sure that Dapper receives security updates for 3 full years on the desktop and even longer on the server. This does not have anything to do with the latest software releases, just stability and security.

Okay, that's what I suspected. But this is not very coherent: you can't have security without software update, especially with FF. FF updates have a lot to do with security, and some with enhanced features. We, long time Dapper users won't have any security updates for FF 1.5.07 because there's no 1.5.0.8.

With Dapper TLS, Ubuntu seems to be able afford to go the mandriva trend : buggy early releases. Xubuntu Edgy, for instance, is released with an Xfce-beta -- is this necessary??

Don't mistake me I really enjoy Ubuntu but I'm a bit disappointed. Just explain to us what's the use of this Dapper *LTS* on desktop (server is a different thing)? Sorry if this is be quite OT.

---

### Post by aysiu on 2006-11-10
> **eeried said:**
> Okay, that's what I suspected. But this is not very coherent: you can't have security without software update, especially with FF. FF updates have a lot to do with security, and some with enhanced features. We, long time Dapper users won't have any security updates for FF 1.5.07 because there's no 1.5.0.8. Quite to the contrary, there might be. In fact, historically, that's what Ubuntu has done. For example, when 1.5.0.6 came out, Ubuntu didn't even create a 1.5.0.6--it just patched 1.5.0.5.

Ubuntu promises security updates. If there are further security flaws discovered in Firefox, they *will* patch them. My understanding is that including Firefox 2.0 will somehow disturb the stability of Dapper. But if they have to patch 1.5.0.7 to make it 1.5.0.8, they will, even if Mozilla doesn't.

---

### Post by eeried on 2006-11-10
> If there are further security flaws discovered in Firefox, they will patch them. My understanding is that including Firefox 2.0 will somehow disturb the stability of Dapper. But if they have to patch 1.5.0.7 to make it 1.5.0.8, they will, even if Mozilla doesn't.

What a lot of work for the Dapper team, then!  

Firefox 2 installed from the Mozilla binaries works fine on my Xubuntu but I'm not questioning the Dapper team's knowledge!

cheers

---

### Post by aysiu on 2006-11-10
> **eeried said:**
> What a lot of work for the Dapper team, then!  

Firefox 2 installed from the Mozilla binaries works fine on my Xubuntu but I'm not questioning the Dapper team's knowledge!

cheers
See--that's the thing, though. Mozilla binaries aren't part of the Ubuntu system; they're "installed" separately in their own directory.

---

### Post by Ulysses on 2006-11-10
> Quote:
Originally Posted by aysiu View Post
Try pasting these commands in the terminal--see if it makes any difference.
Code:

```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox 
sudo ln -s /opt/firefox/firefox /usr/bin/firefox 
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox 
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
```

Hey

Worked for me, too. 
Like a charm.

Can this be made into some kind of script that you can point and  click and make available? I'd do it, but I'm stupid. That's why I come here so I can hang out with the smart guys.

RAR

---

### Post by aysiu on 2006-11-10
> **Ulysses said:**
> Hey

Worked for me, too. 
Like a charm.

Can this be made into some kind of script that you can point and  click and make available? I'd do it, but I'm stupid. That's why I come here so I can hang out with the smart guys.

RAR
Yes, there's a script that *nanotube* has worked very hard to create. It's available here:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

We also have [a thread about it](http://ubuntuforums.org/showthread.php?p=1741607), where we discuss developments, propose new features, and test out new versions of the script.

---

### Post by bader on 2006-11-16
> **bb002 said:**
> Hmmmm....looks like for some reason /opt/firefox/firefox-bin didn't get the executable bit set.
run this in a terminal.
```

sudo chmod +x /opt/firefox/firefox-bin

```
That sould get firefox running.

I tried this and it did not work.

Do I have to download a special version of firefox for PPC, I am running ubuntu on a Mac G3.

Thanks

Bob

---

### Post by aysiu on 2006-11-16
> **bader said:**
> I tried this and it did not work.

Do I have to download a special version of firefox for PPC, I am running ubuntu on a Mac G3.

Thanks

Bob
That makes a big difference, actually.

The .tar.gz in question is specifically for x86 computers, not PowerPC.

---

### Post by vanishedsoul on 2006-11-18
thanks guyz for this howto, it really helped :)

now, one more thing, i first had 1.5.0.7ver of firefox and in trying to install firefox2 i messed it up. Now the firefox2 is up and running the old firefox still exist and the html file which i have saved in my pc dont open with the firefox2, so everytime i have to drag and drop filea in the browser. So is there a way i can make the firefox2 to run the html file bu default??

---

### Post by steven4220 on 2006-11-19
Hi,

I hope this thread is still working as being new at this I seem to have made a mistake and do not want to make it any worse.

I pasted and copied per the directions but I think I missed the following:
1. the unpacking part.
2. I copied and pasted but missed the change dir. (it did not past).

the only thing I can find relating to firefox is a locked firefox symbol in my root directory. I was going to delete it but was not allowed to. I suspect that it may be the original firefox 1.5.0.7. Is that where it is supposed to be?

I guess I'm just not ready to do this on my own yet.

I am using 6.06LT and the 1 piece of good news is that everything seems to be working in spite of myself.:confused: :confused:

---

### Post by aysiu on 2006-11-19
Frankly, the HowTo in this thread is a bit too complicated for new users, I think.

Try this script instead:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Only two commands to copy and paste, and it asks for locale, downloads the .tar.gz for you, and fully integrates it with your Firefox launcher and plugins.

---

### Post by sevenworth on 2006-11-20
is there any way to install firefox 2 using apt-get or synaptic on dapper?

I want to completely replace 1.5

---

### Post by aysiu on 2006-11-20
> **sevenworth said:**
> is there any way to install firefox 2 using apt-get or synaptic on dapper?
No.

---

### Post by sevenworth on 2006-11-20
> **aysiu said:**
> No.

Any reason why? Will the repositories be updated anytime soon?

---

### Post by aysiu on 2006-11-20
> **sevenworth said:**
> Any reason why? Will the repositories be updated anytime soon?
Too many dependency problems.

If you want Firefox 2.0 in Dapper, your best bet is this script:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

If not, upgrade to Edgy or stick with 1.5

---

### Post by sevenworth on 2006-11-20
do you know if at least eventually new software like this will become available on the repository?

---

### Post by Abiezer on 2006-11-21
I upgraded successfully to FF 2.0 using the script linked in this thread. I see there's security upgrades to FF 1.5 available this morning. Just checking that installing them won't affect FF2 - is that right?

---

### Post by BooVeMan on 2006-11-22
Hi,
eventually FF2.0 will have to make in into Dapper Drake, as ther is 3 years of support for 6.06 and FF will only be supported until somewhere into 2007.
... but who wants to wait that long :-)

---

### Post by durant1958 on 2006-11-22
Long Term Support = Doing things that the maintainers really really think are a bad idea and really really don't want to do.

Mark Gosdin

---

### Post by aysiu on 2006-11-22
> **BooVeMan said:**
> Hi,
eventually FF2.0 will have to make in into Dapper Drake, as ther is 3 years of support for 6.06 and FF will only be supported until somewhere into 2007.
... but who wants to wait that long :-)
Actually, I think they'll just keep patching any further security holes that pop up in Firefox 1.5

---

### Post by tOpEzz on 2006-11-23
want to upgrade your firefox to firefox 2.0 ?? i found some interesting website, check this out --->  [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by aysiu on 2006-11-24
> **tOpEzz said:**
> want to upgrade your firefox to firefox 2.0 ?? i found some interesting website, check this out --->  [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
I don't see how this HowTo offers any advantages over the script in that link. The script offers tighter integration, still allows you to launch Firefox 1.5, has fewer steps to get you set up, and has an easy way to uninstall 2.0 should you wish to do so.

If you want to do a lot more steps to understand what's going on, you'd be far better off following these instructions:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

By the way, all the posts regarding the stability of upgrading to Edgy have been moved to [this thread](http://ubuntuforums.org/showthread.php?t=305862).

---

### Post by dcstar on 2006-11-24
> **sevenworth said:**
> do you know if at least eventually new software like this will become available on the repository?

Optimised (for your particular CPU) builds of FF 2 (Swiftfox) are available by adding this repository:

deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

It can't get much simpler than using the standard package tools.

---

### Post by st14n on 2006-11-25
> **dcstar said:**
> Optimised (for your particular CPU) builds of FF 2 (Swiftfox) are available by adding this repository:

deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

It can't get much simpler than using the standard package tools.

I used to manually download and install the deb-packages for Swiftfox myself. Don't know why, this is much simpler. From their homepage: "Compatibility with other distros that are Debian based is not tested, so it might work or it might not." Well, it seems to work:-) But, what are the downsides (if there are any) with using a repository made primarily for Debian?

---

### Post by figo2476 on 2006-11-30
Hi:
Firstly, I downloaded firefox 2.0 from mozilla website, since the link above it is not working.

Then I extracted it to opt/firefox

When I run opt/firefox/firefox, it popped up firefox 1.5. Does it indicates that the command is pointing to the 1.5 version? I remembered I download firefox 2.0.......

Regards

---

### Post by aysiu on 2006-11-30
Try this link:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by figo2476 on 2006-11-30
Run this ./installnewfirefox.sh

I got:
The most recent release of firefox is detected to be 2.0. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.com/](http://www.mozilla.com/)) Is it correct [y/n]? y
Please choose the localization (language) for firefox. Enter the number of your choice from the list below.
Enter your choice of localization:

What is the localization for firefox? Am I supposed to get a list, so that I can input some numbers?

---

### Post by aysiu on 2006-11-30
Localization has to do with geography and language. I live in the US and speak English, so I select EN-US. If I lived in England, I'd select EN-GB.

---

### Post by figo2476 on 2006-11-30
I forgot to tell you, this is the only text I got by using the script.
So I don't what to enter.

The most recent release of firefox is detected to be 2.0. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.com/](http://www.mozilla.com/)) Is it correct [y/n]? y
Please choose the localization (language) for firefox. Enter the number of your choice from the list below.
Enter your choice of localization:

---

### Post by aysiu on 2006-11-30
That's odd. I *just* downloaded the script, and this is what I get.

---

### Post by figo2476 on 2006-11-30
Not sure. Automatix2 doesn't have firefox2 entry, either.

---

### Post by paladin_knight on 2006-12-04
Hello Mr. BsWilson

I followed the code your code to install the plugins in firefox2.0 but the "command not found". I am working in the root directory i guess. I am a newbie in Linux. :D

---

### Post by jclmusic on 2006-12-06
i tried the script posted on here, but with no success. however, i discovered an alternative way of doing it for those who are having the same problem :)

1. uninstall firefox using synaptic package manager

2. download the firefox 2 for your language/region from [www.getfirefox.com](www.getfirefox.com)

3. uncompress it to /opt/firefox or your home directory or anywhere else if you prefer. (remember /opt/firefox requires sudo)

4. update any launchers, menu launchers, preffered applications settings etc to point to /opt/firefox/firefox or where you unpacked it.

it should now work :)

---

### Post by jclmusic on 2006-12-22
found an easier way!

there is an autopackage available from [www.autopackage.org](www.autopackage.org) :)

---

### Post by aysiu on 2006-12-22
> **jclmusic said:**
> i tried the script posted on here, but with no success. however, i discovered an alternative way of doing it for those who are having the same problem :)

1. uninstall firefox using synaptic package manager

2. download the firefox 2 for your language/region from [www.getfirefox.com](www.getfirefox.com)

3. uncompress it to /opt/firefox or your home directory or anywhere else if you prefer. (remember /opt/firefox requires sudo)

4. update any launchers, menu launchers, preffered applications settings etc to point to /opt/firefox/firefox or where you unpacked it.

it should now work :)
That's essentially what the script does... except for uninstalling the Ubuntu Firefox.

---

### Post by rev_b on 2006-12-26
Firefox 2.0.0.1 was released and may seem a minor update, but it seem to have some important fixes.

[http://www.mozilla.org/projects/security/known-vulnerabilities.html#firefox2.0.0.1](http://www.mozilla.org/projects/security/known-vulnerabilities.html#firefox2.0.0.1)

An update isn't still available in the repositories, and I searched the forums for how to update to 2.0.0.1, but found nothing. So I tried to get the job done and I found a way that works well, so I want to share.

Just download firefox-2.0.0.1.tar.gz from [http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/)
Just extract the archive to where you want to run it (I installed it in my ~/ folder), it'll create a folder named firefox

To run it just double-click "firefox" in ~/firefox folder, or update your menu launcher properties. It'll run version 2.0.0.1 and it will still get your settings from the 2.0 version from your ~/.mozilla hidden folder.

To get full functional plugins, just delete ~/firefox/plugins and make it a link for /usr/lib/firefox/plugins

[PHP]ln -s /usr/lib/firefox/plugins ~/firefox[/PHP]

You may also like to make offline content to open with FF 2.0.0.1. Just right click a html file, for instance, select properties -> open with -> Add -> Use a custom command -> Browse and point it to ~/firefox/firefox

This surely isn't an expert guide for installing, but it worked for me and it's a very safe way to run the latest firefox version, as you are only running it from your home folder, so no messing arround with system files.

Check for Updates menu is now active, I don't know if it'll work fine for further versions.

Hope this will be usefull for someone.

---

### Post by ovidescu on 2006-12-26
That worked just fine for me. Thank you, I was really looking for a way to upgrade to 2.0.0.1

Ovidiu

---

### Post by rev_b on 2006-12-26
It's not actually an upgrade, but a way to have 2.0 and 2.0.0.1 installed at the same time, and running 2.0.0.1. I guess one could really upgrade the default 2.0 version, but I really don't feel confortable messing arround with system files.

The correct way would be 2.0.0.1 be added into repositories, and making the upgrade with Synaptic/apt-get. It'll eventually happen (I think), meanwhile firefox guys made the 2.0.0.1 tar.gz very simple to run.

The only trick is replacing the "plugins" folder with a symbolic link as stated. Just copying the files won't work because many files in /usr/lib/firefox/plugins are already just links and they'll be broken in the copy process.

---

### Post by paparucino on 2006-12-27
> **rev_b said:**
> 
The correct way would be 2.0.0.1 be added into repositories, and making the upgrade with Synaptic/apt-get. It'll eventually happen (I think), meanwhile firefox guys made the 2.0.0.1 tar.gz very simple to run.

I've 2.0.0.1 in my synaptic, so I think it's in the repos since I aded nothing to the sources.lists

---

### Post by jclmusic on 2006-12-27
> **aysiu said:**
> That's essentially what the script does... except for uninstalling the Ubuntu Firefox.

i had problems with the script. maybe it's just me, but if not, i thought i should help others :) 

that howto is kind of useless now i found that autopackage, but i'll leave it there in case people have problems with autopackage too.

---

### Post by grizzly on 2006-12-27
how come one the most popular open-source apps needs an how-to for upgrading  whereas a closed-source app ( Opera) provides various deb's  for each major and testing release  immediately . The testing or weekly are released every week!!. 

[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

---

### Post by paparucino on 2006-12-27
> **grizzly said:**
> how come one the most popular open-source apps needs an how-to for upgrading  whereas a closed-source app ( Opera) provides various deb's  for each major and testing release  immediately . The testing or weekly are released every week!!. 

To tell the truth, I installed ff2.0.0.1 without changing anything. Synaptic made the job. :-)

---

### Post by rev_b on 2006-12-27
2.0.0.1 is available in feisty repositories, but, at least for me, I can't see it on edgy ones; it says I have the latest version available (2.0) and won't let me upgrade.

PS: I confirmed it right now. I have feisty installed in a VMWare machine and firefox version in the repos is 2.0.0.1. Edgy is still 2.0...

---

### Post by paparucino on 2006-12-27
> **rev_b said:**
> 
PS: I confirmed it right now. I have feisty installed in a VMWare machine and firefox version in the repos is 2.0.0.1. Edgy is still 2.0...
May be someone forgot to update the Edgy repos or someone thinks it's no ncessary to udate a near to the end release :D

---

### Post by chetroia on 2006-12-28
Yea I agree what does it take to install FF updates ? I am running Edgy too but having to wait this long for updates that fix security issues is crazy. This is what Microsoft does. People are depending on Ubuntu to do the work for updates and new users relay on this too they dont want to drop to bash shell to run commands to install the update manually. They need to consolidate the different gui,s for doing updates too. EX use Aitomatix for this use Synamtec for that apt-get this yum that. Lets have choice but make the tools to have everything then not all thest different tools that you need to spend endless time on internet to find them or odd names to apt-get then try find the icon somewhere in ur menu...
](*,)

---

### Post by DnasTheGreat on 2006-12-29
Yes... I seem to recall reading something about one of the holes fixed in Firefox 2.0.0.1 caused a few people lose all the mail in their Gmail accounts. That's... really... bad...

Come on, we're not like Microsoft! I don't know Ubuntu's packaging policy (it doesn't seem that you like to put major upgrades in repositories... can't say I agree much with that, but whatever.) but a security update is a security update.

And really, how much time could it take? Firefox compilation takes about an hour on my Gentoo box. Only the first few minutes of which need to be supervised. The build system can't have changed any from 2.0 to 2.0.0.1, so the scripts that built 2.0 with Ubuntu patches would still work. And 2.0.0.1 is in feisty, so even if they did change, one could use their setup. A little sanity check here and there (the code probably didn't change much) and a few minutes to make a deb and then you've improved the security of thousands of boxes out there.

One of the things I've always loved about Linux is that the package manager takes care of all the nuances of installation and package maintainace for me. But what's the use if I have to manually hunt down and install even security updates?

A sampling of all the distribution packaging websites I am aware of shows that every distribution that offers Firefox 2 offers 2.0.0.1. I don't see any excuse for why Ubuntu is lagging behind now.

---

### Post by rev_b on 2006-12-29
Maybe too busy getting Feisty out in time?

Anyway *maybe* one could get FF 2.0.0.1 to install altering /etc/apt/sources.list to feisty repositories and installing only firefox... Anyone brave enough to try? ;) Or maybe run firefox as root and see if the check for updates menu is active, it should update itself.

I'm sugesting this because I'm on a windows machine at work, so I can´t try these. Running firefox as root and to see if it updates itself would be one thing I would try now, I didn't think of it before.

And yes, I agree security patches for browser should be top priority in repositories update list.

---

### Post by Poka64 on 2006-12-29
> **rev_b said:**
> Maybe too busy getting Feisty out in time?

Anyway *maybe* one could get FF 2.0.0.1 to install altering /etc/apt/sources.list to feisty repositories and installing only firefox... Anyone brave enough to try? ;) Or maybe run firefox as root and see if the check for updates menu is active, it should update itself.

I'm sugesting this because I'm on a windows machine at work, so I can´t try these. Running firefox as root and to see if it updates itself would be one thing I would try now, I didn't think of it before.

And yes, I agree security patches for browser should be top priority in repositories update list.

You can't update through the update that Firefox uses because the Ubuntu build is different

---

### Post by n3Cre0 on 2006-12-29
Hmm I just updated my firefox trough a script (if anyone needs it i'll look up the link) but I would love to get it updated trough Synaptec.

Is there any way how I can get feisty updates (like firefox 2.0.0.1) trough synaptec/updata-manager without it breaking my edgy installlation?

Would adding the feisty repos work?

---

### Post by DnasTheGreat on 2006-12-29
Feisty seems to use a newer glibc. I got a dependancy problem with it when I tried to download the feisty deb manually. And glibc upgrades tend to be rather prone to breakage, so I didn't really want to download that and the other system-wide dependancies that may have changed in Feisty. (Hence them only being updated when the distro updates.) Besides, it shouldn't be this much work for a security upgrade on a browser. :) The method in this thread is adequate, but misses out on some of the convenient patches that were added. (Vanilla Firefox is somewhat Windows-y.)

---

### Post by david.rahrer on 2006-12-29
This really is confusing to me.  How is this *supposed* to work?  From what I have read, 2.0.0.1 is an important security update.  Wouldn't this normally be a priority in the Repos?  I get update notices for much less important software than Firefox.

---

### Post by rev_b on 2006-12-30
I tried and it's possible to upgrade edgy firefox 2.0 to 2.0.0.1 using feisty repositories.
I've tried this on a virtual machine edgy installation, so try it at your own risk.

Quick and dirty way:

open a terminal and paste 
[PHP]sudo gedit /etc/apt/sources.list 
[/PHP]

Go to search -> replace and replace "edgy" with "feisty". Save the file. (maybe it's a good idea to back it up first).

Launch synaptic, hit reload and search for firefox. You'll see version 2.0.0.1. Mark for upgrade and it'll install FF 2.0.0.1 with all needed upgraded dependencies.

Exit synaptic and replace your sources.list with your backup, or revert the process, i.e., lauch gedit and replace "feisty" entries with "edgy" - if you let it be, update manager will try to upgrade all your system to feisty!!

Launch firefox - you have 2.0.0.1 running.

---

### Post by n3Cre0 on 2006-12-30
Just substituted edgy with feisty.

Will tell you if it works lol

EDIT: It didn't...

---

### Post by papers on 2006-12-30
This worked very good for me.

1. Open terminal and start firefox like this: sudo firefox.

2. Open help menu in Firefox and choose look for updates.

3. When Firefox has confirmed the update [ATTACH]21906[/ATTACH] then..

4. Start your filemanager in terminal with this command; sudo nautilus --no-desktop --browser 

5. Browse to your homefolder and show hidden files, ctrl+h.
    look for .mozilla/firefox/somenumbers.default , change read/write permissions for any 
    file or folder thats been changed to root to be owned by you again.
    It's often extensions you have to change.

6. All done!

---

### Post by david.rahrer on 2006-12-30
It was my understanding that the FF version in Ubuntu is customized.  Wouldn't your method force the standard update over this custom install (i.e. sudo firefox, etc)?  If this were possible, then wouldn't the default Firefox update be enabled from the beginning?  

I'm trying to learn how all this works.  Assuming that important security updates like this one for Firefox are supposed to be supplied to Ubuntu installs, who is responsible for the actual work of updating the repositories?  Is this something individuals can do and submit for approval, or is there a process controlled by someone else?  I've only recently started using Ubuntu on the desktop and I'm concerned about how this should play out.  Thanks for any help understanding this.

---

### Post by nu2this on 2006-12-31
> **papers said:**
> This worked very good for me.

1. Open terminal and start firefox like this: sudo firefox.

2. Open help menu in Firefox and choose look for updates.

3. When Firefox has confirmed the update [ATTACH]21906[/ATTACH] then..

4. Start your filemanager in terminal with this command; sudo nautilus --no-desktop --browser 

5. Browse to your homefolder and show hidden files, ctrl+h.
    look for .mozilla/firefox/somenumbers.default , change read/write permissions for any 
    file or folder thats been changed to root to be owned by you again.
    It's often extensions you have to change.

6. All done!
Didn't work for me in Edgy.

---

### Post by nu2this on 2006-12-31
I think the reason for the delay is the Mozilla guys have to approve the Ubuntu Fx upgrade
has to do with protecting the Fx trademarks. Neither I nor Mozilla want a version of Fx that would do nasty things.

---

### Post by DnasTheGreat on 2006-12-31
Ah. That makes sense.

Hmm... but that's really really ugly... I understand that MozCo wants to protect their trademark but this shouldn't stand in the way of users' security.

Why can't they say that if some patches were approved for one release, they'd be fine for future ones, or at least for security bugfixes? I understand that some patches may break or act weird with minor changes to code here and there, but it's probably the distributor's responsibility to do a sanity check on the patches anyway, and the minor possibility of a distributor purposefully putting out a version of Firefox that happened to do nasty things with a patch that was previously good is worth getting security updates out to all users. After all, having to okay every single release of every single distribution (that doesn't decide to change the name) is very bad for your users. I thought part of the idea of OSS was to promote that idea that the interests of the users have higher priority than those of corporations.

Of course, this doesn't eliminate the possibility that a security patch _does_ break a portion of a pre-okayed patchset (and that the distributor catches it), since then you'd have the go through the review process again, but at least it would put out 99% of such collisions.

Sigh... why can't "don't be stupid" be properly drafted into legalese... would solve a lot of problems in the world. ;)

(Or, even better, they could upstream the Linux patches so that vanilla Fx isn't so Windows-y and works on our platform... as I understand it, the majority of distributions use the same patchset, or have a lot in common at least.)

Besides, personally I think they're a bit more vicious than necessary. Many FOSS apps have trademarks. Linux is a trademark, in fact. But you never hear of any problems with that. I doubt Torvalds is personally okaying every single Linux distro out there...


Is there any official word on this delay? Because I can't consciously reccommend a distro to friends (or myself for that matter) if they don't get their security patches on time.

---

### Post by Hairy_Palms on 2006-12-31
IIRC the security patches from the latest version are put into edgy-security its only the added features that dont get into edgy.

---

### Post by veli on 2006-12-31
Very useful thread.
I'd like only to mention that you could also use the builds of SWIFTFOX. Download to your home directory and follow the directions in the first post.

But run the following command:

ln -s /usr/lib/firefox/plugins ~/swiftfox

It works.

---

### Post by mastergunner on 2007-01-01
How do you install Firefox in to Kubuntu?

---

### Post by rev_b on 2007-01-01
> **mastergunner said:**
> How do you install Firefox in to Kubuntu?

Exactly the same way. Kubuntu and Ubuntu are just diferent names for the same system with different desktop managers. Same steps for Kubuntu.

---

### Post by speedwell68 on 2007-01-01
> **rev_b said:**
> I tried and it's possible to upgrade edgy firefox 2.0 to 2.0.0.1 using feisty repositories.
I've tried this on a virtual machine edgy installation, so try it at your own risk.

Quick and dirty way:

open a terminal and paste 
[PHP]sudo gedit /etc/apt/sources.list 
[/PHP]

Go to search -> replace and replace "edgy" with "feisty". Save the file. (maybe it's a good idea to back it up first).

Launch synaptic, hit reload and search for firefox. You'll see version 2.0.0.1. Mark for upgrade and it'll install FF 2.0.0.1 with all needed upgraded dependencies.

Exit synaptic and replace your sources.list with your backup, or revert the process, i.e., lauch gedit and replace "feisty" entries with "edgy" - if you let it be, update manager will try to upgrade all your system to feisty!!

Launch firefox - you have 2.0.0.1 running.

This worked a treat for me.  Thanks.

---

### Post by rev_b on 2007-01-01
> **veli said:**
> Very useful thread.
I'd like only to mention that you could also use the builds of SWIFTFOX. Download to your home directory and follow the directions in the first post.

But run the following command:

ln -s /usr/lib/firefox/plugins ~/swiftfox

It works.

Very nice. I tried swiftfox 2.0.0.1 Athlon 64 optimized and it works just fine, and seems much faster than default firefox build. I'm using swiftfox instead, now.

---

### Post by svitj on 2007-01-03
> **figo2476 said:**
> I forgot to tell you, this is the only text I got by using the script.
So I don't what to enter.

The most recent release of firefox is detected to be 2.0. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.com/](http://www.mozilla.com/)) Is it correct [y/n]? y
Please choose the localization (language) for firefox. Enter the number of your choice from the list below.
Enter your choice of localization:

Just the same here!! I don't get the list with the code numbers.. Ad if I try, any number:

"Your input is not in the range of available localizations. Please try again:"

---

### Post by apapww on 2007-01-03
Thanks ever so much[.](http://hk.yahoo.com)[.](http://www.ec2biz.com)[.](http://www.rthk.org.hk)[.](http://www.ads28.com)[.](http://www.ec2biz.com)[.](http://www.top1.com.hk)[.](http://www.ads28.com)

---

### Post by r!ots on 2007-01-22
hey guys.

ages ago i installed firefox manually in /opt/firefox.
i was wondering recently why my firefox version always stayed the same although it was updated by synaptic.
today i upgraded to edgy eft and still i didn't have firefox2.0. only then i realised i had two versions installed and the links in my /usr/bin directory pointed to the one in /opt/firefox that didn't get updated by synaptic.
i changed the links so they are pointing to /usr/lib/firfox and now i'm running firefox2.0.

now my question:
how do i uninstall the old firefox in /opt/firefox ?
do i just remove it by typing
```
sudo rm -rf /opt/firefox
```or do i have to care about any links, personal data or anything like that?

---

### Post by towsonu2003 on 2007-01-22
> **r!ots said:**
> hey guys.

ages ago i installed firefox manually in /opt/firefox.
i was wondering recently why my firefox version always stayed the same although it was updated by synaptic.
today i upgraded to edgy eft and still i didn't have firefox2.0. only then i realised i had two versions installed and the links in my /usr/bin directory pointed to the one in /opt/firefox that didn't get updated by synaptic.
i changed the links so they are pointing to /usr/lib/firfox and now i'm running firefox2.0.

now my question:
how do i uninstall the old firefox in /opt/firefox ?
do i just remove it by typing
```
sudo rm -rf /opt/firefox
```or do i have to care about any links, personal data or anything like that?
please refer to [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by eeried on 2007-01-23
> ```
sudo rm -rf /opt/firefox
```

Yes it's that simple! Just before deleting the firefox dir make sure you've saved your plugin dir so you can copy the plugins files into your ```
/usr/lib/firefox/plugins
``` except for your soft link to Java if you have that plugin: the link must be made afresh from the java dir to your new firefox plugin dir.

You can also remove your old firefox icon from the taskbar
cheers  :guitar:

---

### Post by towsonu2003 on 2007-01-23
> **eeried said:**
> Yes it's that simple!

I have to disagree. Many users who installed the new version of Firefox used this document: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) (either manual or script version)

which diverts all kinds of information from the older to the newer version of Fx. So it's a good idea to follow the removal instructions at that page.

---

### Post by Canis familiaris on 2007-02-02
How do I stop dpkg to stop updating my firefox 1.5?

---

### Post by aysiu on 2007-02-02
> **Anurag_panda said:**
> How do I stop dpkg to stop updating my firefox 1.5?
[Lock it in Synaptic](http://ubuntuforums.org/showthread.php?p=2076216#post2076216).

---

### Post by siwli on 2007-02-02
> **svitj said:**
> Just the same here!! I don't get the list with the code numbers.. Ad if I try, any number:

"Your input is not in the range of available localizations. Please try again:"

Hi, I had this problem too. The problem was that my version of Ubuntu is german. If you have a look at the script (for example with gedit or any other editor), somewhere it says  
# Get available localizations
and in the line underneath is a long command with wget and other stuff. The problem is the 'grep directory' part.
I tried out the first part of the command (the wget ftp.... part) and had a look at the output. The word 'directory' did not appear in the output, instead there was the word 'Verzeichnis' which actually means directory in german.
So if you change the script so that it contains the word for directory in your language, you can run it.

Here is the exact line, I highlighted the spot to change (in my editor, it was line 49):

LOCALIZATIONS=( `wget -q -O - ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/ | grep "[COLOR="Red"]Directory[/COLOR]" |grep -v "xpi" |awk '{print $7}' | awk -F\/ '{print $10}'`)

---

### Post by shankru85 on 2007-02-06
thanks for the tipshttp://ubuntuforums.org/images/smilies/smiley-faces-80.gif

---

### Post by Dragon43 on 2007-02-09
Thanks to all in this thread.  I finally got FF 2.0.0.1 running on my 6.06.  Many helped and a big 'Thank You' to all.

After I got some other things about my net connection straightened out, the [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) link worked for me. It was still a bit confusing, but with enough tries, I got it.

When they say to 'save to the desktop', they mean it.

The 'locations' request was confusing because the window was so small that I missed for a while the list in it to pick from and I had no idea what 'locations' they were talking about and that I had to use a number.  ( Real Newbie here.)

A lot of patience is needed as some things go kinda slow and there is no  indication that it is still working.

But it all worked out in the end.

Just noticed that the 'spell checker' does network in 'fast reply' but does in the  'advanced' window.  Hummmmm

*Off to make my next mistake.... *

---

### Post by immanueloffice on 2007-02-27
I followed the tutorial - thanks - it all worked! 

One thing that seems to be missing is how FF will now update itself. At the beginning of the tutorial it says:
> You will no longer get automatic updates for Firefox through the repositories (but Firefox itself has a built into auto-updater, see below for how that works).
But I can't see that anywhere in the tutorial.

When I'm in my new FF2, the Help->Check for Updates is still greyed out. So, I'm worried I'm not going to be notified of updates. Options for updating are also greyed out in Edit->Preferences.

Any idea what I can do to change this?

Thanks!

---

### Post by aysiu on 2007-02-27
When you do need to update, close Firefox, press Alt-F2, type ```
gksudo firefox
``` and then check for updates and install them. After you're prompted to restart Firefox, go ahead and restart it. Then close it again.

Finally, open it again as a regular user.

When you open Firefox with *gksudo* go to only check updates (and your homepage, if you have one). Do not visit any other sites.

---

### Post by immanueloffice on 2007-02-27
Excellent - thanks. I guess that's what happens when you don't use the distro to install updates. :)

---

### Post by aysiu on 2007-03-04
I've removed this part from the original post: > *Automated with extras* - Automatix is a program that allows for easy installation of a lot of popular software. If you want not only Firefox but also Flash, Java, and a lot of other popular proprietary plugins, Automatix may be a good choice for you. There are also other automated scripts for popular and/or proprietary software if you don't like Automatix ([Easy Ubuntu](http://easyubuntu.freecontrib.org/overview.html) and [BUMPS](http://www.ubuntuforums.org/showthread.php?t=181248)), but I don't think they install the latest Firefox.
[http://www.getautomatix.com](http://www.getautomatix.com)
 Apparently, Automatix upgraded Firefox to 1.5 for Breezy but no longer does Firefox upgrades for Dapper or Edgy. It does have Swiftfox, though.

---

### Post by davidgarcin on 2007-03-09
If I start Firefox as su, enable automatic Firefox updating in the Preferences, then restart Firefox as a normal user, the automatic updating option is still checked.  Will Firefox auto-update now when I run it as a normal user, or will it still not have the privileges?

---

### Post by davidgarcin on 2007-03-09
Nope, won't work.  See this post: [http://ubuntuforums.org/showthread.php?p=2269706#post2269706](http://ubuntuforums.org/showthread.php?p=2269706#post2269706)

---

### Post by DJ_Peng on 2007-04-02
I tried the script for installing Firefox, but I was disappointed that the update feature is broken unless your run Firefox as root. I finally documented my install method, and while you have to manually fix your plugins the updates and everything else works as Mozilla intended. This way you can work with beta and nightly builds without jumping through any additional hoops once you get it installed.

**How to install Firefox in Ubuntu to get ALL of the functionality** (link removed because that blog is no longer online)

No, this isn't a knock of the great script from the Psychocats site, I just think if the developers worked as hard as they did to get the update mechanism working the least they could expect from Linux distros is that it works without making the users have to take extra steps.

---

### Post by aysiu on 2007-04-02
This appears to be a combination of the *manual* and *manual with no integration* methods outlined in the thread I merged yours with.

If you view as bothersome occasionally launching *gksudo firefox* to install updates, you can always just use the script and then change ownership of the /opt folder to your user: ```
sudo chown -R djpeng:djpend /opt/firefox
``` Then the updates will work regularly... at least for your user. Some people like to keep the owner as root for /opt/firefox as an extra layer of security.

---

### Post by DJ_Peng on 2007-04-02
Thanks for the merge. I wasn't sure if I should *** it as a new thread or start a new one. The big problem in having to run it as root is if you're running nightlies or betas you want to be able to get the newest versions pretty quickly. I hadn't thought of changing the ownership of the folder, but I don't like changing permissions outside of my home folder. I do wish there were a better way to deal with this other than a script. The developers really busted their hump getting the new update mechanism put together.

---

### Post by aysiu on 2007-04-02
Well, in essence, with your method, it's practically the same thing. By extracting the .tar.gz in and running Firefox out of your home folder, you're doing a passive change of ownership.

The only difference is it being in /home/username/firefox instead of /opt/firefox

From a security/convenience standpoint the two methods are equivalent.

But it's all about choice. If that choice gives you more peace of mind or comfort, then go for it.

---

### Post by izak on 2007-04-16
Hi

I installed firefox 2.0.0.3 using the manual version on the site [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion).

It worked once when I checked it, but after I restored my old data using the recommended

cd ~/Desktop/ffsettings
 mv * ~/.mozilla/firefox/*.default

I get an error window when I try to launch either the new or the old firefox:

"Firefox is already running, but not responding. To open a new window, you must first close the existing Firefox process, or resart your system."

I restarted but still get the same message. Any suggestions? I do not want to use the script, because I want to avoid downloading the 10Mb file at home where I only have dailup...

Thanks for the useful thread.

---

### Post by izak on 2007-04-16
I've now removed the new Firefox using the manual instructions given. I accidentally  did a second "rm /usr/bin/firefox" afterward so I decided to just completely reinstall the old Firefox though synaptic. I still get the same warning:

"Firefox is already running, but not responding. To open a new window, you must first close the existing Firefox process, or resart your system."

but now it appears in a window with the the old Ubuntu Firefox logo. Have I completely broken my system?! Please help!

I tried completely removing Firefox using synaptic and then reinstalling after restarting my system, but still I get the same message. And there is no mention of Firefox in the System Monitor.

---

### Post by DJ_Peng on 2007-04-16
You will need to delete the lock files from your Firefox profile directory. You can get the skinny at [http://kb.mozillazine.org/Profile_in_use]("http://kb.mozillazine.org/Profile_in_use").

---

### Post by ciscosurfer on 2007-04-16
If you get an error message that says Firefox or Swiftfox is already running, you can kill the process and then restart the app.  Or, you can simply logout, log back in and try again.  If this still doesn't take care of the process, then reboot and start again.

---

### Post by DJ_Peng on 2007-04-16
Actually I've had times where I've had to use the info on the page I linked to because no amount of rebooting would let me start Firefox. This especially can happen if you're in Firefox when your computer crashes. Such as when a feline decides to brush against something and dump the power. It's been known to happen, and yes, the feline still lives. 8)

---

### Post by izak on 2007-04-17
Thanks for the great link, DJ_Peng! Indeed, no amount of restarting was fixing the problem. I had managed to both screw up the relative pathname in firefox's profiles.ini AND had firefox1.5 runnning when I backed up the settings resulting in a .lock file.

Apperntly completely removing firefox though synaptic doesn't remove the local user configurations, because that was what was messing things up..

Browsing from firefox 2 in ubuntu with ease now:D

---

### Post by ubuntubrian on 2007-04-30
I'm running Dapper PPC and so I downloaded the source file. I can get the package to build but not to run and I suspect that it's because it is conflicting with 1.5. Is there a way to combine the building from source instructions on the Mozilla website with the Ubuntu How To and get a custom built FF2 to run on PPC?
Here's my quote from the PPC Forum:
"I have been checking the forums and Mozilla site to try and get Firefox 2.0 installed and running. So far I have downloaded the source code and tried, successfully (at least no errors) to build it. I followed the instructions here:
[http://developer.mozilla.org/en/docs..._Build_Options](http://developer.mozilla.org/en/docs..._Build_Options)
I got Sunbird up to the latest version using these instructions.

However it seems that Firefox is not so simple as so many other packages depend on it:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
"Warning: If you use this guide, do not remove the Ubuntu version of Firefox. Doing so will break the following packages: Yelp (help viewer), Epiphany, Gnome-app-install (Add Applications), Liferea, Blam and any application requiring the Gecko rendering engine."

On Bugzilla:
[https://bugs.launchpad.net/dapper-backports/+bug/68158](https://bugs.launchpad.net/dapper-backports/+bug/68158)
They say that it is possible to build a Firefox 2.0 as Firefox2 and run it alongside 1.5 to avoid breaking packages but they don't say how to do this.

It seems possible to build the FF2.0 from source and run it alongside 1.5 but I am not knowledgable enough to do so. I know that the "FirefoxNewVersion" instructions apply to prebuilt debs so that won't work.
I would think the 2.0 version could be built into another directory and renamed but that is beyond me. Can anyone help?"

---

### Post by 1sttimer on 2008-03-29
I installed ubuntu 6.06 on my HP laptop computer. The program it's self works great, but after I updated   ubuntu my Firefox internet program stop working. When I clicked on the firefox icon i got a message that said that it is already running but not responding. Firefox never appears. I have restarted my compute to reset firefox but it changed nothing. I have heared that this problem is due to improper shut down of firefox .I would appreceate any help or sugestion that anyone can give me so that I can get back on the internet.

         PS   I have no proble update ubunto I just don't have use of the internet.


                              Thanks Ed:confused:

---

### Post by aysiu on 2008-03-29
Press Alt-F2 and paste in this command: ```
killall firefox-bin
``` Then try again to launch Firefox.

---

### Post by Catalyst2Death on 2008-03-29
You could also try this:
[https://www.ece.auckland.ac.nz/it-support/wiki/LinuxProblems#Firefoxrefusestostartbecauseitisalreadyrunning](https://www.ece.auckland.ac.nz/it-support/wiki/LinuxProblems#Firefoxrefusestostartbecauseitisalreadyrunning)

I had this problem too, theres a file which gets messed up in the firefox settings that you have to delete, but I can't remember where its at... 

The above link should work, but it may not because it was written for Debian, not ubuntu

---

### Post by 1sttimer on 2008-04-01
I have tried to unlock fire fox as you described but that path doesn't exist on Ubuntu. I feel it would be easer to install a new Firefox and remove the old one, what say you.  I am new and dumb in regard to Ubuntu so please make the solution as painless as possible 


                     Thanks, Ed

---

### Post by DJ_Peng on 2008-04-01
Any chance you'll have a tutorial (info) for those who prefer not to opt-in to Firefox 3 Beta that will be in the released Hardy? Especially info on how to preserve their Fx2 profile so Fx3 doesn't trash it in case they try Fx3 and decide they'd rather use Fx2 as long as it's supported?

---

### Post by aysiu on 2008-04-01
> **DJ_Peng said:**
> Any chance you'll have a tutorial (info) for those who prefer not to opt-in to Firefox 3 Beta that will be in the released Hardy? Especially info on how to preserve their Fx2 profile so Fx3 doesn't trash it in case they try Fx3 and decide they'd rather use Fx2 as long as it's supported?
If you download the .tar.gz for Firefox 2.0 and manually install it, you should be able to use that instead of Firefox 3.0 Beta.

It also may not hurt to back up your ~/.mozilla folder before you upgrade.

---

### Post by DJ_Peng on 2008-04-01
You do realize that if someone does a distro-upgrade to Hardy and decides they want to use Firefox 2 that Firefox 2 won't be able to use the profile that Firefox 3 used, right? That's a long known issue among the Firefox testing community.

---

### Post by aysiu on 2008-04-01
> **DJ_Peng said:**
> You do realize that if someone does a distro-upgrade to Hardy and decides they want to use Firefox 2 that Firefox 2 won't be able to use the profile that Firefox 3 used, right? That's a long known issue among the Firefox testing community.
That may be an issue for many people. Personally, I've had no problems switching back and forth using the same profile, but then I don't really use extensions any more.

I guess my recommendation was more for if you didn't want to use Beta Firefox 3 at all.

---

### Post by DJ_Peng on 2008-04-01
You're actually the first (or possibly 2nd) person I've heard that had zarro issues. Unfortunately most people won't know they don't want to use Firefox 3 until after they've used it. Otherwise they won't know how much has been changed (and not necessarily for the better).

---

### Post by aysiu on 2008-04-01
> **DJ_Peng said:**
> You're actually the first (or possibly 2nd) person I've heard that had zarro issues. Unfortunately most people won't know they don't want to use Firefox 3 until after they've used it. Otherwise they won't know how much has been changed (and not necessarily for the better).
So they should back up the ~/.mozilla folder then.

---

### Post by quill3033 on 2008-04-30
[QUOTE=aysiu;1963105]**What's the issue?**
Ubuntu updates its software versions every six months with a new release. Mozilla, however, upgrades Firefox every month or two--sometimes every week--with security patches or new feature-based releases. Ubuntu often includes security patches with its own versions a day or a week after Mozilla releases their patches, but many Ubuntu users are impatient and would prefer to install the latest version of Firefox from Mozilla and use that instead of the Ubuntu build of Firefox.



My question is - I still have Ubuntu 6.06 Dapper and apparently Firefox 1.5.0.12eol - is that updated sufficiently by Ubuntu to be comparable/equivalent to the latest version of Firefox? If so, I really won't bother downloading latest version separately.

---

### Post by aysiu on 2008-04-30
> **quill3033 said:**
> [QUOTE=aysiu;1963105]**What's the issue?**
Ubuntu updates its software versions every six months with a new release. Mozilla, however, upgrades Firefox every month or two--sometimes every week--with security patches or new feature-based releases. Ubuntu often includes security patches with its own versions a day or a week after Mozilla releases their patches, but many Ubuntu users are impatient and would prefer to install the latest version of Firefox from Mozilla and use that instead of the Ubuntu build of Firefox.



My question is - I still have Ubuntu 6.06 Dapper and apparently Firefox 1.5.0.12eol - is that updated sufficiently by Ubuntu to be comparable/equivalent to the latest version of Firefox? If so, I really won't bother downloading latest version separately.
It'll be updated with security updates until June 2009, but it will not have the same features as Firefox 3.0.

---

### Post by quill3033 on 2008-04-30
thank you for replying so quickly :-)

Ok, I'm  not so worried about Firefox 3 - and from what i've seen in the forum, it sounds like some people don't even like some of the changes but. I'm at uni doing distance education and they have finally decided to support Firefox as a browser but the minimum is version 2. 

I've actually done quite well (even with dial up) uploading things etc and even when they weren't supporting it but I guess I'd like to know whether 1.5 is equivalent to Firefox 2 if i'm getting the dapper updates.

---

### Post by aysiu on 2008-04-30
> **quill3033 said:**
> thank you for replying so quickly :-)

Ok, I'm  not so worried about Firefox 3 - and from what i've seen in the forum, it sounds like some people don't even like some of the changes but. I'm at uni doing distance education and they have finally decided to support Firefox as a browser but the minimum is version 2. 

I've actually done quite well (even with dial up) uploading things etc and even when they weren't supporting it but I guess I'd like to know whether 1.5 is equivalent to Firefox 2 if i'm getting the dapper updates.
No. It isn't Firefox 2.0.

All you're getting is security patches for Firefox 1.5.

Is there any reason in particular you want to stay with Dapper?

---

### Post by quill3033 on 2008-05-01
> **aysiu said:**
> No. It isn't Firefox 2.0.

All you're getting is security patches for Firefox 1.5.

Is there any reason in particular you want to stay with Dapper?



I guess I think don't mess with a good thing and it seems to me to be more stable than the other versions that seem more cutting edge but that might need me to be a bit more savvy about computers. There seem to be a lot of people on these forums who are real programmers and who just know heaps more. Having said that, I'm writing this message via the Ubuntu 8.04 LTS cd version (uninstalled just using it in RAM to have a go) and it definitely seems faster surfing the internet with it so... 

Also the fact that I have downloaded a lot of programs I'm used to and I'm really comfortable with... you know - questions like will it work with the printer, camera etc (though from looking at synaptic it seems to have the printing part covered 
Also don't like the idea of upgrading every six months. 

I will install version 8.04 side by side with the old one and if it 
really grabs me I'll make the full move.

My ideal will be to get another hard disk and use it for downloading each new version. 

But also it's just that 6.06 has been so wonderful and after having a MS computer that kept freezing on me this is just heaven and I didn't want to risk it.

---

### Post by aysiu on 2008-05-01
You don't have to upgrade every six months. You can upgrade every two years to the new LTS (Long-Term Support release). Ubuntu 6.06 is LTS, and so is 8.04.

You can also install Firefox 2.0 on Ubuntu Dapper by following these instructions:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Just make sure you download 2.0 and not 3.0 beta.

---

### Post by quill3033 on 2008-05-01
yep, i'll eventually install 8.04 but i'll wait a few months until the little glitches are resolved. I've just seen the postings on various probs and I don't have the time to resolve them. Plus, using the cd live user thingy, the desktop bar is not the one i've grown to looove. It's great for opening programs and whatever left right and centre and for doing searches. If only the first choice was *not* amazon.com and was google or answers, it would be absolutely perfect. 
RE installing firefox, the link you gave me is a bit difficult to follow and copying and pasting gave me a funny message from the terminal about how one of the items didn't exist.... so I think i'll just download it from the website and see.

---

### Post by quill3033 on 2008-05-01
Sorry, made a mistake in last post. Will do the ubuntuzilla option rather than the tutorial. If you'd like detailed feedback as to how the tutorial could be improved I'm happy to do a write up about what is not immediately understandable from a lay lay person's viewpoint. thanks for your help. :-)

---

### Post by aysiu on 2008-05-01
Instead of giving feedback, just edit it. It's a Wiki.

---

### Post by quill3033 on 2008-05-03
hi,

I used Ubuntuzilla to install Firefox 2 and the latest Thunderbird and it's worked really well. Thank you. 

as for editing - I don't know enough to edit - I do know what I'd like to know that isn't in a particular set of instructions.

I'm waiting on a couple of books to learn a bit more - I prefer books to threads for background and to get a picture of what things are.

Thanks again.

---

### Post by aysiu on 2008-06-17
I did a little cleanup on the Wiki entry. It was extremely old and assumed people were using Breezy or Dapper and firefox 1.* instead of 2.*. It also had a lot of convoluted instructions and things not related to installing the Mozilla build of Firefox.

---

### Post by DeadlyFishy on 2009-05-22
What if I want to install Firefox 2.0.0.20 ?

---

### Post by aysiu on 2009-05-22
> **DeadlyFishy said:**
> What if I want to install Firefox 2.0.0.20 ?
Firefox 2 isn't supported any more.

---

### Post by DeadlyFishy on 2009-05-25
I know that it doesn't get updates and whatnot, but are you saying that Firefox 2 is impossible to install? I just can't stand Firefox 3..

---

### Post by aysiu on 2009-05-25
This may help you:
[http://ubuntuforums.org/showpost.php?p=7173686&postcount=10](http://ubuntuforums.org/showpost.php?p=7173686&postcount=10)

---

### Post by DeadlyFishy on 2009-05-26
> **aysiu said:**
> This may help you:
[http://ubuntuforums.org/showpost.php?p=7173686&postcount=10](http://ubuntuforums.org/showpost.php?p=7173686&postcount=10)

Thanks much! :D

---

### Post by jcm1107 on 2009-07-11
> **DJ_Peng said:**
> 

**How to install Firefox in Ubuntu to get ALL of the functionality**



I was searching this forum and want to inform staff that this link just takes you to an advertisement and should be removed.Thanks.

 I also could ask what I was searching for in the first place. I want to know if I can have two separate Firefox programs running on my computer? I wanted to have on with a lot of plugins and one with bear minimum of plugins for speed. I also want to say that the install with no integration in the first post didn't do that for me, it just launched my current firefox, that is the same as typing "firefox" in a terminal.Thanks!!

---

### Post by DJ_Peng on 2009-07-12
Thanks for pointing that out to me. Unfortunately I shut down that blog quite a while ago and it seems some cybersquatter has placed some adverts at my old URI. I checked the Internet Archive and they didn't snag any of my content from that site so I'm afraid my post has gone to the great bit bucket in the sky.

As far as running two versions of Firefox at one time, I'm afraid that's impossible due to the fact that both versions would run an app called "firefox". The bottom line is that when you launch a second version the OS simply looks at what's running, sees an app called "firefox" is already running, and simply opens a new window for the app already started. The only way around that may be to use a virtual machine to run a different version of Firefox in.

---

### Post by jcm1107 on 2009-07-12
> **DJ_Peng said:**
> Thanks for pointing that out to me. Unfortunately I shut down that blog quite a while ago and it seems some cybersquatter has placed some adverts at my old URI. I checked the Internet Archive and they didn't snag any of my content from that site so I'm afraid my post has gone to the great bit bucket in the sky.

As far as running two versions of Firefox at one time, I'm afraid that's impossible due to the fact that both versions would run an app called "firefox". The bottom line is that when you launch a second version the OS simply looks at what's running, sees an app called "firefox" is already running, and simply opens a new window for the app already started. The only way around that may be to use a virtual machine to run a different version of Firefox in.


That is exactly what it was doing and thanks for letting me know it isn't possible. I know that opening firefox is just the same as typing firefox in a terminal and that opens the current version. I did go on my brothers guest account (which I never use) and there were few plugins there so I guess I could use a different user account to if I want a lighter firefox or a different version. If someone finds a better way of doing this please let me know. I just want a fast light firefox and a seperate one that has alot of plugins and functions. Right now I am using a lot of plugins, so I need to get another install with no plugins that I can configure separate. Thanks:p

---

### Post by andyba on 2009-09-23
You can install firefox in wine and it runs perfectly.
So you have 2 different firefoxes. :)

I first wanted to recommend installing Opera or Konqueror as a second browser but I have discovered recently that google adwords doesn't work in any of them.

So for linux currently there is no alternative but firefox. Unfortunately.

---

### Post by DJ_Peng on 2009-09-23
Actually if you still have the Linux "installer" for Fx2 you can simply extract it and run it. There's a readme in the .tar.gz. You won't be able to run it while Fx3 is running, but I strongly recommend having another browser handy anyway in case you need two different browsers running at once. My personal fav since deciding I don't like Fx3 is GNOME's Epiphany.

---

### Post by von Stalhein on 2009-09-24
I'm not sure how I accomplished it (probably because I am uber clever!) but I have 2 versions of FF.

I've one ```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1) Gecko/20090624 Firefox/3.5
```that executes from /usr/lib/firefox/firefox and one ```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.3) Gecko/20090910 Ubuntu/9.04 (jaunty) Shiretoko/3.5.3
``` that executes from ../lib/firefox-3.5.3/firefox.sh

The first one has all the extensions, themes, bookmarks etc. that I use all the time, but the other one is the one that's automatically updated through Synaptic.

How do I make the later version adopt the profile from the earlier one? Then I can remove the one that doesn't update.

TIA

---

### Post by DJ_Peng on 2009-09-25
You can specify a [specific profile]("http://kb.mozillazine.org/Profile_Manager") with ```
firefox -profilemanager
```. In your case you'd probably run ```
/lib/firefox-3.5.3/firefox.sh -profilemanager
```

---

### Post by von Stalhein on 2009-09-28
> **DJ_Peng said:**
> You can specify a [specific profile]("http://kb.mozillazine.org/Profile_Manager") with ```
firefox -profilemanager
```. In your case you'd probably run ```
/lib/firefox-3.5.3/firefox.sh -profilemanager
```

Thanks awfully DJ_Peng!!

Neither of those worked first off, but I know a variation will do the trick :). I will let you know what did.

---

### Post by DJ_Peng on 2009-09-28
Glad it was helpful. I had to run the profile manager last week when my Fx3 profile got borked and just loading up a page to snag some videos took forever.

---

### Post by von Stalhein on 2009-09-30
> **DJ_Peng said:**
> Glad it was helpful. I had to run the profile manager last week when my Fx3 profile got borked and just loading up a page to snag some videos took forever.

Partly sorted.

I managed to get the profile updated to the new 3.5.3 and it works fine.

Unfortunately I've lost the capability to open hyperlinks from Thunderbird.

This has happened before, and I've always managed to get it back - it's been two nights so far and I've not cracked it. I'm mildly annoyed atm.

I've opened about 15 threads on these forums with various remedies but no luck so far.

---

### Post by Footer on 2009-09-30
> Unfortunately I've lost the capability to open hyperlinks from Thunderbird.

Did your search include this thread:

[http://ubuntuforums.org/showthread.php?t=60427](http://ubuntuforums.org/showthread.php?t=60427)

Specifically post #3?  I know it's an old thread but it's worth a try.  I had the same trouble a long time ago but over time, my computing habits have changed (I use Gmail exculsively vs. ThunderBird) and this is no longer an issue for me.

Let us know what fixed it for you!

---

### Post by DJ_Peng on 2009-09-30
I can't help you there. I switched to Evolution over a year ago and have no problems opening links. But then I also use Epiphany as my default browser so my knowledge of Firefox may not be quite the best available.

---

### Post by von Stalhein on 2009-10-01
> **Footer said:**
> Did your search include this thread:

[http://ubuntuforums.org/showthread.php?t=60427](http://ubuntuforums.org/showthread.php?t=60427)

Specifically post #3?  I know it's an old thread but it's worth a try.  I had the same trouble a long time ago but over time, my computing habits have changed (I use Gmail exculsively vs. ThunderBird) and this is no longer an issue for me.

Let us know what fixed it for you!

> **DJ_Peng said:**
> I can't help you there. I switched to Evolution over a year ago and have no problems opening links. But then I also use Epiphany as my default browser so my knowledge of Firefox may not be quite the best available.

Thanks lads :-)

Yes, I have tried every variation listed in about 15 threads without luck. I'm a bit cranky as I've fixed it before, but can't remember the "magic bullet" for my particular set up.

I just tried links in Evolution by sending myself a test message containing a url - it works. Hmmmmm - just need to find the same process in TBird.....

I'm not overly fussed on any mail client, but I like to think that I can mostly make all the stuff on this box work like it's supposed to.

Yes, I am delusional!!

---

### Post by Footer on 2009-10-01
> **von Stalhein said:**
> Yes, I am delusional!!

Nah, not delusional, just persistent!  It's working on my box, and I was just digging through some 'cheat sheets' I keep and found this:

----------------------------------------------------

To config thunderbird to use firefox for it's links:
In Thunderbird
Edit->Preferences
then go:
Advanced->General

Click on 'Config Editor' and on editor check for a key:
network.protocol-handler.app.http
(you can make it if it doesn't exist) RightClick on the Config Editor Background and:
1. From the pop-up menu, select "New".
2. From the next pop-up menu, select "String".
3. In the pop-up dialog box "Enter preference name", enter "network.protocol-handler.app.http" No Quotes
4. In the pop-up dialog box "network.protocol-handler.app.http" enter  ~/swiftweasel/swiftweasel (/usr/bin/firefox)
and OK finish

----------------------------------------------------

I think I found that on the forums here somewhere and made a note of it.  You've proabably already tried that but thought I'd pass along anyway.

Good luck!!!

:)

EDIT:  DOH!  I looked at post #3 again in the link I provided earlier and it's basically the same thing except the method above is via TBird while post #3 has you edit the file manually.  Oh well, I'm pretty sure that's what worked for me way back when.  :)

---

### Post by von Stalhein on 2009-10-02
I tried to get some interest from [http://ubuntuforums.org/showthread.php?t=1224279]("http://ubuntuforums.org/showthread.php?t=1224279") without luck yet.

The last post (mine) pretty much outlines what I've done so far to restore the linky goodness.

And failed dismally.

---

### Post by von Stalhein on 2009-10-05
> **Footer said:**
> Did your search include this thread:

[http://ubuntuforums.org/showthread.php?t=60427](http://ubuntuforums.org/showthread.php?t=60427)

Specifically post #3?  I know it's an old thread but it's worth a try.  I had the same trouble a long time ago but over time, my computing habits have changed (I use Gmail exculsively vs. ThunderBird) and this is no longer an issue for me.

Let us know what fixed it for you!

> **von Stalhein said:**
> I tried to get some interest from [http://ubuntuforums.org/showthread.php?t=1224279]("http://ubuntuforums.org/showthread.php?t=1224279") without luck yet.

The last post (mine) pretty much outlines what I've done so far to restore the linky goodness.

And failed dismally.

Aww, I dunno - it just came back :( or should that be :) ??

I have been in XP playing IL2 1946, maybe it got jealous or something.

Don't get me wrong, I'm happy it's functional, I'm just curious as to which step fixed it.

FWIW, the config file entries are as follows: -
```
user_pref("network.protocol-handler.app.ftp", "/usr/bin/firefox-3.5");
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox-3.5");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox-3.5");
```

It will be interesting to see if they are borked by the next ff update.

---

### Post by Footer on 2009-10-05
Don't you just love it when things fix themselves?  :)

Yup, it will be curious to see what the next version of FF does.  Or perhaps it's a TBird udpate?  Who knows.  Too many moving parts.

:)

---

### Post by kyle2595 on 2009-10-05
What is the difference between the Ubuntu built Firefox and the Mozilla one?

---

### Post by cataztrophe on 2009-10-06
thnx for your tips!
really helps :D

---

### Post by JakeLawrence on 2010-04-28
Has there been a tutorial on how to install Firefox 3.6.3 on Karmic?

---

### Post by aysiu on 2010-04-28
> **JakeLawrence said:**
> Has there been a tutorial on how to install Firefox 3.6.3 on Karmic?
Yes.

Quick copy-and-paste terminal instructions:
[http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

More involved point-and-click instructions:
[http://www.psychocats.net/ubuntu/ubuntuzilla](http://www.psychocats.net/ubuntu/ubuntuzilla)

---

### Post by JakeLawrence on 2010-04-28
Thank you very much!

Being a 64-bit user, can I still install Firefox's 32-bit builds and still maintain a semblance of stability?

---

### Post by aysiu on 2010-04-28
You know, I moved this to "Outdated tutorials" for a reason.

If you want up-to-date info, please visit this thread:
[Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

