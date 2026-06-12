---
title: "R some flash players only capable in Windows?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by rlntel on 2008-05-12
Hi All,

The forums have so much information that I spend so much time reading I don't get to play as much as I'd like with Hardy, I just installed. :)

Here's my problem...

I installed Hardy on my wife's computer with the understanding that she could use mine until I could get Hardy on her machine to play CSI-Miami from the CBS.com site.

Well...she's holding my laptop hostage because I can't get her show to play.

I need some help. I've downloaded and installed flash 9.+ but it's not helping. When I get to the CBS page, choose the show of interest, a huge play symbol appears in the pane; however, when I click it, it goes away and....nothing! The screen just sits there in play mode with nothing happening.

Please rescue my laptop and make me a hero.

Thanks.

:)

---

### Post by HornedBeast on 2008-05-12
You may need to install the Java Runtimes too.

Open up a terminal and type this:

```
sudo apt-get install sun-java6-jre
```

That may help your problem - but it could be site specific. Perhaps CBS.com requires some ActiveX controls which Firefox (and Linux in general) does not have.

HB

---

### Post by lswest on 2008-05-12
if you want to get fancy, you can download the useragentswitcher for firefox from the addons page, and use the one that fakes a windows OS firefox signature, so that the video should play when it thinks it's being played in windows.  Not sure if it will work.  Also, not sure where you are, but i believe CBS shows are only available for north american countries, but i assume you had it working before.

---

### Post by kestrel1 on 2008-05-12
I had a similar problem, but found that Flash Player was not being used by the browser. It was using another flash style player that I installed by mistake. Once I got rid of it, things started working. I cannot for the life of me remember it's name though.

---

### Post by gn2 on 2008-05-12
I've just been on the CBS.com website, the CSI shows give an audio message "this content is currently unavailable" which could be because I'm in the UK, but the other shows work OK.

Open Synaptic Package Manager at the left click Sections then at the top left select All then  search for swfdec
There should be eight entries, make sure they are all uninstalled, mark any that are installed for complete removal.

Next search for gnash, do the same, make sure that all seven items are uninstalled.

Mark flashplugin-nonfree for re-installation and click Apply.

If you have installed a 64-bit Ubuntu, use these instructions to install flash: 
[http://ubuntuforums.org/showpost.php?p=4822974&postcount=1](http://ubuntuforums.org/showpost.php?p=4822974&postcount=1)

---

### Post by dstin1 on 2008-05-12
I can make it work fine.

type about: plugins (without the space) in the address bar to see which flash plugin you are using.  I have shockwave flash 9 for swf and spl files and mplayerplug-in 3.5 for flv files not sure which format the videos are in but I'll bet it's flv

---

### Post by rlntel on 2008-05-12
"sudo apt-get install sun-java6-jre"

Here's what I got...

'E: Couldn't find package sun-java6-jre'

---

### Post by dstin1 on 2008-05-12
about: plugins will also tell you if java is installed, but I don't think you need it for this site.

---

### Post by kansasnoob on 2008-05-12
Hmmm, I'm scratching my head. I don't know if sun-java6 is available without medibuntu or not. Anyway, what I do is this:

Install the medibuntu repository:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Note: remember to add the GPG Key!

When done I close the terminal and open the Synaptic Package Manager, then I click on "Settings>Repositories". Under the "Ubuntu Software" tab "main", "universe", "restricted", and "multiverse" should all be ticked.

Now click on the "Third party Software" tab. There you want the "Hardy Partner", and the "Medibuntu .. /Hardy free/nonfree ticked. IMPORTANT NOTE: YOU DO NOT WANT THE "SOURCE CODE" BOXES TICKED IF YOUR A NOOB LIKE ME!

Everything else there should be fine unless you want to click on the Statistical tab and tick that box, that just lets Ubuntu know what's being used the most, but don't worry about it.

So click on close.

Now, in the upper left hand corner of Synaptic you'll see a Reload button. Click on it and wait. When it's done running you can see if there are any upgrades available.

When you're all done with that you can just click on "Search" and type in: sun-java6

I install all sun-java6 but sun-java6-doc and sun-java6-source. *doc just wastes space and *source can break stuff!

Then while I'm there I install lots of stuff, but everyones list is different.

I install all "gstreamer", and I mean ALL, the good, bad, and ugly!
Then "totem", "totem-gstreamer" & "totem-mozilla". (Also totem-xine")

Then ALL "vlc".

Then "flashplugin-nonfree".

Then "acroread", which is Adobe reader. ALL acroread!

And finally ............ "non-free-codecs".

Then I have a fully functional desktop for my purposes.

It's all easy using the search tool in synaptic and you can select whatever seems right and then just click install and grab a snack and a glass of moo-juice. Just be a bit careful, crack open a note pad and have fun.

I hope I have that complete.

---

### Post by HornedBeast on 2008-05-12
Go to "System - Administration - Software Sources" and make sure the first 4 sources are ticked on the first page.

Then click "Close".

Then try the command again. Its definatly in the Hardy repos - just tried and it worked fine.

HB.

---

### Post by HornedBeast on 2008-05-12
The JRE is in the Multiverse repo.

---

### Post by rlntel on 2008-05-12
I've nothing for FLV files, but when I review my plugins in FF I see 

"Windows Media Player Plug-in 10 (compatible; Totem)
The Totem 2.22.1 plugin handles video and audio streams"

---

### Post by rlntel on 2008-05-12
"I had a similar problem, but found that Flash Player was not being used by the browser. It was using another flash style player that I installed by mistake. Once I got rid of it, things started working. I cannot for the life of me remember it's name though."

Although I don't think it matters (since FF attempts to play the file, not some other program by default), but out of curiosity, how did you change the default back to FF?

---

### Post by rlntel on 2008-05-12
> **lswest said:**
> if you want to get fancy, you can download the useragentswitcher for firefox from the addons page, and use the one that fakes a windows OS firefox signature, so that the video should play when it thinks it's being played in windows.  Not sure if it will work.  Also, not sure where you are, but i believe CBS shows are only available for north american countries, but i assume you had it working before.

Not finding 'useragentswitch'...is there a new name?

---

### Post by dstin1 on 2008-05-12
I bet you need something to play flv files.  My plugins use mplayer there are probably others.  You can get mplayer through Synaptic.  

Also you may want to consider installing restricted extras I'm not sure if it will solve your problem but it might.

here is the code for in the terminal
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by rlntel on 2008-05-12
> **kansasnoob said:**
> Hmmm, I'm scratching my head. I don't know if sun-java6 is available without medibuntu or not. Anyway, what I do is this:

Install the medibuntu repository:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Note: remember to add the GPG Key!

When done I close the terminal and open the Synaptic Package Manager, then I click on "Settings>Repositories". Under the "Ubuntu Software" tab "main", "universe", "restricted", and "multiverse" should all be ticked.

Now click on the "Third party Software" tab. There you want the "Hardy Partner", and the "Medibuntu .. /Hardy free/nonfree ticked. IMPORTANT NOTE: YOU DO NOT WANT THE "SOURCE CODE" BOXES TICKED IF YOUR A NOOB LIKE ME!

Everything else there should be fine unless you want to click on the Statistical tab and tick that box, that just lets Ubuntu know what's being used the most, but don't worry about it.

So click on close.

Now, in the upper left hand corner of Synaptic you'll see a Reload button. Click on it and wait. When it's done running you can see if there are any upgrades available.

When you're all done with that you can just click on "Search" and type in: sun-java6

I install all sun-java6 but sun-java6-doc and sun-java6-source. *doc just wastes space and *source can break stuff!

Then while I'm there I install lots of stuff, but everyones list is different.

I install all "gstreamer", and I mean ALL, the good, bad, and ugly!
Then "totem", "totem-gstreamer" & "totem-mozilla". (Also totem-xine")

Then ALL "vlc".

Then "flashplugin-nonfree".

Then "acroread", which is Adobe reader. ALL acroread!

And finally ............ "non-free-codecs".

Then I have a fully functional desktop for my purposes.

It's all easy using the search tool in synaptic and you can select whatever seems right and then just click install and grab a snack and a glass of moo-juice. Just be a bit careful, crack open a note pad and have fun.

I hope I have that complete.

Ok...my head's swimming, but I think I've got it. (You give me way too much credit.)

I have a couple of questions...

1) Can you please give me the APT line command for install the medibuntu repo?

and,

2) I installed a GPG key once when installing ndiswrapper for her laptop, but the documentation assumed too much and I think I just got lucky.

Can you give me some help with the key?

Thanks.

---

### Post by gn2 on 2008-05-12
This will help you sort out Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by rlntel on 2008-05-12
> **gn2 said:**
> I've just been on the CBS.com website, the CSI shows give an audio message "this content is currently unavailable" which could be because I'm in the UK, but the other shows work OK.

Open Synaptic Package Manager at the left click Sections then at the top left select All then  search for swfdec
There should be eight entries, make sure they are all uninstalled, mark any that are installed for complete removal.

Next search for gnash, do the same, make sure that all seven items are uninstalled.

Mark flashplugin-nonfree for re-installation and click Apply.

If you have installed a 64-bit Ubuntu, use these instructions to install flash: 
[http://ubuntuforums.org/showpost.php?p=4822974&postcount=1](http://ubuntuforums.org/showpost.php?p=4822974&postcount=1)
Ok...I know I'm closer because the big black screen no longer appears; however, now the page loads and reads 'Done' on the status bar and that's it...nothing else.

Any suggestions?

---

### Post by rlntel on 2008-05-12
> **dstin1 said:**
> I bet you need something to play flv files.  My plugins use mplayer there are probably others.  You can get mplayer through Synaptic.  

Also you may want to consider installing restricted extras I'm not sure if it will solve your problem but it might.

here is the code for in the terminal
```
sudo apt-get install ubuntu-restricted-extras
```
I did this and it ran an impressive number of scripts for quite some time. I'm pretty sure it was this attempt that caused the black screen where the video is supposed to play to go away, but now it's gone. The problem is that no video (or even player) appears on the page...just background color and 'Done' in the status bar.

Any suggetions?

---

### Post by rlntel on 2008-05-12
> **gn2 said:**
> I've just been on the CBS.com website, the CSI shows give an audio message "this content is currently unavailable" which could be because I'm in the UK, but the other shows work OK.

Open Synaptic Package Manager at the left click Sections then at the top left select All then  search for swfdec
There should be eight entries, make sure they are all uninstalled, mark any that are installed for complete removal.

Next search for gnash, do the same, make sure that all seven items are uninstalled.

Mark flashplugin-nonfree for re-installation and click Apply.

If you have installed a 64-bit Ubuntu, use these instructions to install flash: 
[http://ubuntuforums.org/showpost.php?p=4822974&postcount=1](http://ubuntuforums.org/showpost.php?p=4822974&postcount=1)
Yep...here's the error I remember from ndiswrapper...the docs aren't clear for us newbies...

W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277

---

### Post by rlntel on 2008-05-12
Hi again All,

Ok...you all are awesome. It's working.

Once again, I'm not quite sure what was the fix, but after restarting FF, her show is playing.

Yeah...my laptop is free.

Thank you.

---

### Post by dstin1 on 2008-05-12
I'm still pretty sure that you need somthing to play flv files.  Since you installed all this other stuff close firefox and restart do the ```
about:plugins
``` again and see if you have somthing to play flv files.  if you don't try mplayer.  As I said before this site works for me and I don't have ndiswrapper or mediabuntu installed.

If you decide to install mplayer you will most likely have to restart firefox for it to see the plugin.

> Hi again All,

Ok...you all are awesome. It's working.

Once again, I'm not quite sure what was the fix, but after restarting FF, her show is playing.

Yeah...my laptop is free.

Thank you.

Glad it working for you and thanks for the site I didn't know cbs did this.

---

### Post by kestrel1 on 2008-05-12
If you want to install Java for use with the browser you probably want the plugin.
```
 sudo apt-get install sun-java6-plugin
```
Once you have done this you need to open the browser & type adout:plugins as mentioned previously to check that the plugin is installed correctly.

---

### Post by snl2587 on 2008-07-23
Old thread, but:

It turns out that Flash 10 beta works on CBS.com as well (combined with the codecs, of course), and eliminates the gray box problem (at least so far). The only problem is that it refuses to play in full screen, citing my Flash player as being older than Flash 9. Anyone know of a workaround? Like tricking the site?

I suppose that this is a small price to pay for the increased stability I've found with Flash 10 on my 64-bit Hardy installation, especially since the video *works*, just not the fullscreen option. Any ideas, though, would be appreciated.

---

### Post by reginak on 2008-10-02
Resurrecting a really old thread here ... trying with much frustration to watch the Katie Couric candidate interviews on cbs.com.

All my plugins are enabled, I've got Flash 9 and for .flv files, I have a Totem plugin, ver 2.22.1.

I get the gray box, both small screen and full screen. I thought it might be a conflict with Adblock, but I disabled and it still isn't working. I have cookies enabled, too (those were suggestions from Mozilla's help page).

I am an Absolute Beginner and not much of a geek, so please bear with me and break it down to the "for dummies" version.  :)

Thanks

---

