---
title: "Enabling Fluendo mp3/wma plugin for Rhythmbox"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by JeremyP99 on 2008-10-19
Bought from Canonical and installed (right click, Gdebi package installer). Seems to be installed OK. Listed in plugins.

However, Rhythmbox appears not to recognise it automatically, and the PLugin option in the Rhythmbox Preferences menu only shows installed ones, and does not seem to have an option to add new ones.

How to proceed? I have over 4 Tbs of wma, and am looking to escape MS. Ubuntu newbie, with some Unix experience a while back, so instructions must be simple! Assume I know nothing!

Thanks in advance- hope someone can help. 8.10 Alpha, last updated a few days back, and just starting to come together.

Jeremy Poynton

---

### Post by ezramorris on 2008-10-19
> **JeremyP99 said:**
> Bought from Canonical and installed (right click, Gdebi package installer). Seems to be installed OK. Listed in plugins.

However, Rhythmbox appears not to recognise it automatically, and the PLugin option in the Rhythmbox Preferences menu only shows installed ones, and does not seem to have an option to add new ones.

How to proceed? I have over 4 Tbs of wma, and am looking to escape MS. Ubuntu newbie, with some Unix experience a while back, so instructions must be simple! Assume I know nothing!

Thanks in advance- hope someone can help. 8.10 Alpha, last updated a few days back, and just starting to come together.

Jeremy Poynton

Is there a particular reason why you wanted to use Fluendo? The GStreamer plugins worked OK for me.

---

### Post by JeremyP99 on 2008-10-19
> **ezramorris said:**
> Is there a particular reason why you wanted to use Fluendo? The GStreamer plugins worked OK for me.

wma media file type. Over 4 terabytes, lossless, so I need to be able to play wma. Googling and advice to no avail, and the only option I could find was to buy the plugin. If there's another way that DOES work, well and good - but no wma no Ubuntu!

Cheers

---

### Post by ezramorris on 2008-10-19
> **JeremyP99 said:**
> wma media file type. Over 4 terabytes, lossless, so I need to be able to play wma. Googling and advice to no avail, and the only option I could find was to buy the plugin. If there's another way that DOES work, well and good - but no wma no Ubuntu!

Cheers

It's in gstreamer0.10-plugins-ugly in Universe IIRC.

---

### Post by JeremyP99 on 2008-10-19
> **ezramorris said:**
> It's in gstreamer0.10-plugins-ugly in Universe IIRC.

So how do I get rhythmbox to see the plugin? And thanks.

---

### Post by ezramorris on 2008-10-19
> **JeremyP99 said:**
> So how do I get rhythmbox to see the plugin? And thanks.

I think it just works when you install that package.

---

### Post by gandaran on 2008-10-19
> I think it just works when you install that package.

yes it does, but why install the free codecs when hes got the fluendo ones
which are much better and could conflict with the gstreamer ones

---

### Post by gandaran on 2008-10-19
edit: double post

---

### Post by ezramorris on 2008-10-19
> **gandaran said:**
> yes it does, but why install the free codecs when hes got the fluendo ones
which are much better and could conflict with gstreamer

dunno. uninstall the fluendo ones, install the gstreamer ones.

he is, after all, only wanting to play music on rhythmbox.

---

### Post by Tom--d on 2008-10-19
Install all the gstreamer packages in Add/remove

Rhythmbox will pick them up (may need to restart Rhythmbox tho to refesh)

---

### Post by ezramorris on 2008-10-19
> **Tom--d said:**
> Install all the gstreamer packages in Add/remove

Rhythmbox will pick them up (may need to restart Rhythmbox tho to refesh)

You will need to select "All available applications" from the drop-down menu, then select "GStreamer plugins for mms, wavpack, quicktime, musepack" and "GStreamer extra plugins".

---

### Post by gandaran on 2008-10-19
and its the same thing for fluendo, install them and Rhythmbox or any other gstreamer based player will pick them up. you don't have to enable anything, what I don't know is if you can have both gstreamer and fluendo  installed, will they conflict? which one will rhythmbox pick up?

---

### Post by ezramorris on 2008-10-19
> **gandaran said:**
> and its the same thing for fluendo, install them and Rhythmbox or any other gstreamer based player will pick them up. you don't have to enable anything, what I don't know is if you can have both gstreamer and fluendo  installed, will they conflict? which one will rhythmbox pick up?

Well, according to the OP, Rhythmbox didn't pick them up.

They could conflict - not sure. If it did, it would be because there are two plugins trying to deal with the same codec.

---

### Post by JeremyP99 on 2008-10-19
OK. So it is clear I can play wma. gstreamer will do it, but fluendo is better. I have fluendo, but don't know how to enable it. 

Simple instructions please!

Will report back. Probably tomorrow. Thanks to one and all

Jeremy

---

### Post by ezramorris on 2008-10-19
> **JeremyP99 said:**
> OK. So it is clear I can play wma. gstreamer will do it, but fluendo is better. I have fluendo, but don't know how to enable it. 

Simple instructions please!

Will report back. Probably tomorrow. Thanks to one and all

Jeremy

Well, wait and see if anyone else can come up with anything, but all I have found about fluendo and rhythmbox is that "the songs play, but you can't see the time or slide bar".

---

### Post by gandaran on 2008-10-19
> **JeremyP99 said:**
> OK. So it is clear I can play wma. gstreamer will do it, but fluendo is better. I have fluendo, but don't know how to enable it. 

Simple instructions please!

Will report back. Probably tomorrow. Thanks to one and all

Jeremy

simple instructions? you just install the fluendo package! should work!
what type of package was it? .deb? check if the package is installed in synaptic package manager.

---

### Post by deanjm1963 on 2008-10-19
The fluendo codecs are just that, codecs, not actual plug-ins. They don't add functionality to the interface, only allow you to play music/videos etc.

I have them as well. It's the same deal with totem, they're not listed as a plug-in either.

---

### Post by ezramorris on 2008-10-19
> **gandaran said:**
> you just install the fluendo package! should work!

If I read the opening post correctly, he did this, but rhythmbox did not allow playing of the said file formats.

---

### Post by JeremyP99 on 2008-10-20
Correct. Still no ability to play wma; the gstreamer ugly plugins do not support wma, and the Fluendo plugin is not recognised. Mind you, whilst Ubuntu plays a startup sound, rhythmbox does not recognise my sound card.

Sigh.

---

### Post by ezramorris on 2008-10-20
> **JeremyP99 said:**
> Correct. Still no ability to play wma; the gstreamer ugly plugins do not support wma, and the Fluendo plugin is not recognised. Mind you, whilst Ubuntu plays a startup sound, rhythmbox does not recognise my sound card.

Sigh.

Right, try using the medibuntu repository. With Rhythmbox closed:

1. Go to System>Administration>Software Sources, then the "Third Party Software" tab.
2. Click add, then paste the line:
```
deb http://packages.medibuntu.org/ hardy free non-free
```
Click add, close, then close again.
3. Open up a terminal and type the following commands in turn. Enter your password if and when required:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install w32codecs
```

Then try opening Rhythmbox and playing a wma file.

---

### Post by JeremyP99 on 2008-10-20
> **ezramorris said:**
> Right, try using the medibuntu repository. With Rhythmbox closed:

1. Go to System>Administration>Software Sources, then the "Third Party Software" tab.
2. Click add, then paste the line:
```
deb http://packages.medibuntu.org/ hardy free non-free
```
Click add, close, then close again.
3. Open up a terminal and type the following commands in turn. Enter your password if and when required:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install w32codecs
```

Then try opening Rhythmbox and playing a wma file.

Right! We have sounds! Used the above, and managed to find that my SOundblaster live external 24 bit card needs to be set as OSS, not ALSA.

However, I have 5.1 speakers, and the rear speakers are not being used.Also, the tagging of the files is all to **** - the album tag is not recognised, so it is impossible to navigate the music (I have > 4 terabytes...!)

I'll do some searching on the above, in the meantime, some progress, thanks, and if anyone has any ideas as to how to resolve the above two problems, I'd be grateful. 

Bottom line is that unless Ubuntu can handle my music library as well as XP, it's of no use whatsoever to me!

---

### Post by ezramorris on 2008-10-20
> **JeremyP99 said:**
> Right! We have sounds! Used the above, and managed to find that my SOundblaster live external 24 bit card needs to be set as OSS, not ALSA.

However, I have 5.1 speakers, and the rear speakers are not being used.
Are you using 5.1 audio files, or are you trying to play standard stereo files, and make them use all the speakers?

I'm not sure how far OSS supports surround sound, but you could try checking the volume controls, to check the level for each speaker if you haven't done so already.

Double click on the speaker icon on the system tray, then click File>Change Device>.....(OSS Mixer). Then click Edit>Preferences, and make sure everything relevant is checked.

> **JeremyP99 said:**
> Also, the tagging of the files is all to **** - the album tag is not recognised, so it is impossible to navigate the music (I have > 4 terabytes...!)

Just the album title or all the tags appear as ****?

Did you uninstall Fluendo? If not, go to System>Administration>Synaptic Package Manager, search for Fluendo, then right click on the package with a green square, and click mark for removal. Then click apply to apply changes.

Restart rhythmbox.

> **JeremyP99 said:**
> Bottom line is that unless Ubuntu can handle my music library as well as XP, it's of no use whatsoever to me!

To be fair, the main problem here is the use of a proprietary codec, owned by Microsoft. This means that people making other operating systems can find it very difficult, if not impossible, to legally offer full support for that codec on their operating system.

It's really a small miracle that WMA is supported at all!

---

