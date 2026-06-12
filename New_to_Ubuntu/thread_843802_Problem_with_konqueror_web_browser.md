---
title: "Problem with konqueror web browser"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by swimm3r137@gmail.com on 2008-06-28
Hey guys,

When I try to access pandora for example, it says the flash plugin is not installed and asked if I would like to download it from the macromedia website.  Is there any file I can download directly from synaptic to install flash for konqueror instead of having to dl it from the website?  I already have the "nonfree flash plugin9.1024" installed, but I'm assuming it's only compatible with firefox, opera, etc! =(

---

### Post by shae on 2008-06-29
What version of ubutnu are you using?

---

### Post by angry_johnnie on 2008-06-29
Have you installed  **konqueror-nsplugins** ?

It should be available in the repositories, so open Adept, look for the package, and mark it for installation.

Once you have installed it, open Konqueror and go to

**Settings > Configure Konqueror > Plugins**

Then click on **Scan for new plugins**.

And, hopefully, that will do it. :-)

EDIT:

I just noticed a thread on the same subject a little further down this page.  You know, multiple threads aren't helpful, as you are likely to get the same answers again and again.  Don't despair.  A single thread will let others know what has and what hasn't worked already. :-)

Anyway, I've read you can't find 'Plugins' in 'Configure Konqueror'.
Are you absolutely sure about that?

[This]("http://i234.photobucket.com/albums/ee205/yogajuan/konk.png") is what you're looking for.

If it's really not there, then it beats me.

---

### Post by swimm3r137@gmail.com on 2008-06-29
I'm using 8.04 hardy.  Sorry about the multiple threads, I just wish this would work, and have tried multiple times without any luck =(  But, I know you mentioned to install "konqueror-nsplugins", which I did, but it didn't do  squat.  What I did find out is I have the latest version from synaptic, version 4.0.3 of konqueror, which actually, if you download it, you'll see that it does _**NOT**_ have a "plugin" option under "configure konqueror".  But, the older konqueror, version 3.5 or so I think, which I downloaded and tried, does have the plugin option, where flash is much much easier to setup and it actually works.  Problem is, it's extremely slow and it freezes alot.  So, in conclusion, am I one of the few who has this newer version of konqueror, where it's virtually impossible to get flash sites to work?  I'm sorry to say this, but konqueror is a kick *** browser, and it's a damm shame  flash had to ruin it and macromedia won't do anything to fix their **** program.  I would use it, but I need flash for pandora, youtube, and other sites I use daily.  SUcks!

Plus, what's really wierd is, when I had the nonfree-flash plugin installed, konqueror just wouldn't recognize it. (version 4.0.3 that is)  And I can't figure out any reason why they would do away with the plugin option, cuz I can't find any other way to have konqueror recognize that flash is actually installed on my system.  I even tried moving the plugin into the kde plugin folder, but ubuntu wont let me copy/paste or move it there.  Meh, oh well.  Another perfect browser ruined by flash...  _If anyone actually has the up-to-date version of konqueror, and knows how to install flash and have the browser recognize it's actually installed, you'd be a LIFE SAVER!!! THANKS!_

---

### Post by angry_johnnie on 2008-06-29
Well... I'm taking a wild guess here... I don't use kde4, but this is how I solve similar issues with other browsers.

If you know where konqueror's plugin folder is, you could just create a link that points to flashplugin.so or whatever it's called. :-)

You can't just copy/paste because anything that is outside of your home folder needs root privileges in order to be changed.

So, what you do is this:

Find the flash plugin, wherever it is... maybe something like **/usr/lib/mozilla/plugins/flashplugin-something.so**

So, you open a terminal and type:

```
sudo ln /usr/lib/mozilla/plugins/flashplugin-something.so /konqueror/plugins/folder/flashplugin-something.so
```

Just change the above command to reflect your actual directories, and use flashplugin-nonfree.so or maybe flashplugin-alternative.so or whatever it's called.

---

### Post by swimm3r137@gmail.com on 2008-06-29
> **angry_johnnie said:**
> Well... I'm taking a wild guess here... I don't use kde4, but this is how I solve similar issues with other browsers.

If you know where konqueror's plugin folder is, you could just create a link that points to flashplugin.so or whatever it's called. :-)

You can't just copy/paste because anything that is outside of your home folder needs root privileges in order to be changed.

So, what you do is this:

Find the flash plugin, wherever it is... maybe something like **/usr/lib/mozilla/plugins/flashplugin-something.so**

So, you open a terminal and type:

```
sudo ln /usr/lib/mozilla/plugins/flashplugin-something.so /konqueror/plugins/folder/flashplugin-something.so
```

Just change the above command to reflect your actual directories, and use flashplugin-nonfree.so or maybe flashplugin-alternative.so or whatever it's called.

can it be flashplugin-alternative.so or does it have to be from the original flash folder (flashplugin-nonfree.so)?  Also, do you or anyone else have any idea where to direct this flash plugin to?  I've tried numerous folders, and it still doesn't work...  there isn't a folder called /konqueror, but theres /kde4, and ive tried most of the promising plugin folders within that, but clearly im either missing it, or this ain't gonna work lol =( In theory, it sounds promising, so hopefully someone can direct me a lil bit more.

---

### Post by angry_johnnie on 2008-06-29
It may be because of [this]("https://bugs.launchpad.net/ubuntu/+source/kdebase-kde4/+bug/188669"), but then, I don't use kde4, so I'm not sure.  It's not really so much about the search bar itself, but about the fact that you're given no option to configure plugins of any kind.

But there's really no other explanation for it not to have a *plugins* option.

Sadly, that means, you either wait, or use an older version.

---

### Post by swimm3r137@gmail.com on 2008-06-29
well god dammit...  that's too bad.

---

