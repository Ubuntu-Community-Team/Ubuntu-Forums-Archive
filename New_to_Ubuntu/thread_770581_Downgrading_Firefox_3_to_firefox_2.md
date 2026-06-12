---
title: "Downgrading Firefox 3 to firefox 2"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Batatolol on 2008-04-27
Ok I hope this is the right forum to post, if not please move 'cos I'm noob :)

Yesterday I updated my ubuntu 7.10 to 8.04, and in the updates was firefox 3 beta 5, and it have been crashing alot since yesterday, how can I downgrade it to firefox 2? 

Thnks in advance =)

---

### Post by hackle577 on 2008-04-27
[SIZE="3"]**To "downgrade" Firefox 3 Beta 5 to Firefox 2 in Hardy:**[/SIZE]

[SIZE="4"]1.[/SIZE] First make a list of any extensions you've installed in FF3 that you want in FF2. [COLOR="Red"]Simply uninstalling FF3 and installing FF2 on top of the same Firefox profile will break your extensions.[/COLOR] You also should back up your saved sessions and anything else you want to save. Your bookmarks can be backed up to your home folder with this command:

```
cp ~/.mozilla/firefox/*.default/bookmarks.html ~
```

[SIZE="4"]2.[/SIZE] To uninstall FF3, wipe your profile, and install FF2, run these commands in the terminal:

```
sudo apt-get purge firefox-3.0
rm -r ~/.mozilla/firefox
sudo apt-get install firefox-2
```

---

### Post by ssadhale on 2008-04-27
You can go to Synaptic. Search for firefox and mark it for complete removal and then reinstall it again Or download the linux version of firefox 2 from mozilla.org and install it separately.

---

### Post by hums07 on 2008-04-27
> **Batatolol said:**
> Ok I hope this is the right forum to post, if not please move 'cos I'm noob :)

Yesterday I updated my ubuntu 7.10 to 8.04, and in the updates was firefox 3 beta 5, and it have been crashing alot since yesterday, how can I downgrade it to firefox 2? 

Thnks in advance =)

AFAIK, Hardy comes with Firefox 3 beta. FF3 will become full release soon so you can update later. In the mean time you can use close alternatif to FF such as epiphany. Do this in terminal:
```
sudo apt-get install epiphany
```

---

### Post by alzie on 2008-04-27
Go into synaptic package manager, search for firefox. 

Click on firefox 3 and choose "mark for removal", Click firefox 2 and mark for installation.

I hope this helps.

---

### Post by Biggy on 2008-04-27
> **hackle577 said:**
> In terminal:

```
sudo apt-get purge firefox
sudo rm -r ~/.mozilla
sudo apt-get install firefox-2
```


Thank You !!!

---

### Post by MangasColoradas on 2008-04-27
> **hackle577 said:**
> In terminal:

```
sudo apt-get purge firefox
sudo rm -r ~/.mozilla
sudo apt-get install firefox-2
```

I had just used synaptic to remove 3 and replace with 2, it caused all kinds of weird errors with addons.

The above code cleared it all up for me, thanks! :)

---

### Post by Batatolol on 2008-04-27
Thank you for the info :D

---

### Post by asgard_command on 2008-04-27
I had the same problem and just removing version 3 and installing 2 left a mess. You do have to totally remove your profile folder the .mozilla file too.

---

### Post by MarilenCorciovei on 2008-04-27
[Same problem]("http://www.len.ro/work/tools/ubuntu-hardy-heron-on-a-dell-d820/ubuntu-hardy-heron-on-a-dell-d820/view"), firefox 3 seems still buggy:

apt-get install firefox-2
rm /usr/bin/firefox
ln -s /usr/bin/firefox-2 /usr/bin/firefox

---

### Post by blazemiskulin on 2008-04-27
Am I correct in understanding that the only way to downgrade is a complete wipe of the current install--including the profile?

That would mean starting from scratch--losing all cookies, passwords, history, etc.

---

### Post by jhnphm on 2008-04-27
I don't think you have to remove the profile, as I've been running FF3 beta along w/ FF2 alongside w/ Gutsy, and haven't had to remove the profile. Whoever posted that command containing "rm -rf ~/.mozilla" should remove it, since they didn't bother telling anyone that that contains the profile.

---

### Post by qopi on 2008-04-28
> **Biggy said:**
> Thank You !!!

Yes, that worked.

Unfortunately no warning is given that your complete mozilla profile disappears when you do this (meaning you loose ALL your plugins, saved sessions, bookmarks, cookies, etc. etc. etc.)

I just did it and can now get to my bank log-in (which wasn't letting me with FF3.b5) but wish I hadn't :(

All the other stuff I've lost was worth A LOT more than accessing one poxy website :(

/me cries.

---

### Post by qopi on 2008-04-28
> **blazemiskulin said:**
> Am I correct in understanding that the only way to downgrade is a complete wipe of the current install--including the profile?

That would mean starting from scratch--losing all cookies, passwords, history, etc.

Exactly.

Unfortunately no warning is given that your complete mozilla profile disappears when you do this (meaning you loose ALL your plugins, saved sessions, bookmarks, cookies, etc. etc. etc.)

I just did it and can now get to my bank log-in (which wasn't letting me with FF3.b5) but wish I hadn't

All the other stuff I've lost was worth A LOT more than accessing one poxy website

/me cries.

---

### Post by qopi on 2008-04-28
> **hackle577 said:**
> In terminal:

```
sudo apt-get purge firefox
sudo rm -r ~/.mozilla
sudo apt-get install firefox-2
```

Yes, that worked.

Unfortunately no warning is given that your complete mozilla profile disappears when you do this (meaning you loose ALL your plugins, saved sessions, bookmarks, cookies, etc. etc. etc.)

I just did it and can now get to my bank log-in (which wasn't letting me with FF3.b5) but wish I hadn't

All the other stuff I've lost was worth A LOT more than accessing one poxy website

/me cries.

---

### Post by ByteJuggler on 2008-04-28
Backup.  Always.  No exceptions.  :(

---

### Post by Calash on 2008-04-28
I am running FF3 and FF2 as well with no problem.  FF3 slows my system down way too much.  I understand why it was put in by default, but until they get the bugs worked out it may result in more problems than it is worth.

---

### Post by KIAaze on 2008-04-28
> **hackle577 said:**
> In terminal:

```
sudo apt-get purge firefox
sudo rm -r ~/.mozilla
sudo apt-get install firefox-2
```

Mmh, doing "sudo rm -r ~/.mozilla" might remove all bookmarks and thunderbird settings...
I'm not sure of it, but it's something that people should be aware of.
Just export your bookmarks before doing it to be safe.

edit: Too late apparently... :/

---

### Post by padlamoij on 2008-05-02
FYI
Most of the crashes in FF3 are due to the flash plugin. So maybe you should send the folks over at Adobe a little note, since its closed source and no one else can fix the bugs in it.

---

### Post by dstin1 on 2008-05-02
Why can't I have both ff2 and 3 working at the same time using the same pluins and extras?

---

### Post by Xiong Chiamiov on 2008-05-02
As a side note, it's always a good idea to *rename* folders and files rather than deleting them, so that you can just rename them back if you decide you want them.  If you don't, you can then get rid of them afterwards.

You can also run [Swiftweasel]("http://swiftweasel.wiki.sourceforge.net/Apt") if you like, which is the 2.0 branch of Firefox (with no non-free images, etc, etc, read [here]("http://en.wikipedia.org/wiki/Swiftweasel")).

---

### Post by Xiong Chiamiov on 2008-05-02
.

---

### Post by asgard_command on 2008-05-02
I didn't find it a problem removing my profile. I have backups of my bookmarks all over the place and the Thunderbird settings are in a different file. I keep a written note of all the extensions I have installed. So it is a simple job to download and install my extensions and I'm back to square one. Must be a few extra problems for those with more complicated settings such as proxies. 

As a side note I'm sure I read yesterday something about Adobe opening up some aspects of Flash, if that is the problem with Firefox 3 maybe this will help them get it sorted.

---

### Post by Xiong Chiamiov on 2008-05-02
> **asgard_command said:**
> I didn't find it a problem removing my profile. I have backups of my bookmarks all over the place and the Thunderbird settings are in a different file. I keep a written note of all the extensions I have installed. So it is a simple job to download and install my extensions and I'm back to square one. Must be a few extra problems for those with more complicated settings such as proxies. 

As a side note I'm sure I read yesterday something about Adobe opening up some aspects of Flash, if that is the problem with Firefox 3 maybe this will help them get it sorted.
[They're just letting hardware developers include flash for no charge]("http://news.zdnet.co.uk/software/0,1000000121,39408915,00.htm").  No hope for us yet.

---

### Post by Nathan_S on 2008-05-04
tried your suggestions did not work. any other ideas?

---

### Post by DarinB on 2008-05-25
sudo apt-get purge firefox-3.0
rm -r ~/.mozilla/firefox
sudo apt-get install firefox-2

awesome this worked for firefox then i tweaked it for swiftweasel then reinstalled swiftweasel 2.0.0.14 and it works and didn't kill my thunderbird

thanks

---

### Post by ktechman on 2008-06-19
Does FF3 include all of the useful plug-ins like "No script" and "Track Me Not"?  Regards

---

### Post by aysiu on 2008-06-19
> **ktechman said:**
> Does FF3 include all of the useful plug-ins like "No script" and "Track Me Not"?  Regards
I don't know about Track Me Not, but NoScript is definitely updated for Firefox 3.

---

### Post by grok2grok on 2008-08-22
> **hackle577 said:**
> [SIZE="3"]**To "downgrade" Firefox 3 Beta 5 to Firefox 2 in Hardy:**[/SIZE]

[SIZE="4"]1.[/SIZE] First make a list of any extensions you've installed in FF3 that you want in FF2. [COLOR="Red"]Simply uninstalling FF3 and installing FF2 on top of the same Firefox profile will break your extensions.[/COLOR] You also should back up your saved sessions and anything else you want to save. Your bookmarks can be backed up to your home folder with this command:

```
cp ~/.mozilla/firefox/*.default/bookmarks.html ~
```

[SIZE="4"]2.[/SIZE] To uninstall FF3, wipe your profile, and install FF2, run these commands in the terminal:

```
sudo apt-get purge firefox-3.0
rm -r ~/.mozilla/firefox
sudo apt-get install firefox-2
```


Thanks,

It also works well when Firefox is radioactive, maybe with extensions, and you just want to start over.
[http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

---

