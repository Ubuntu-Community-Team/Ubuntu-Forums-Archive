---
title: "Firefox video problem"
date: 2016-07-01
forum: New to Ubuntu
---

### Post by rdb3 on 2016-07-01
All videos that I try to play on Firefox have the audio & video out of sync.  This happens on Youtube and on any other online video that I try to watch.

I do not have this problem when watching videos on Chromium.

Firefox 47 and Ubuntu 16.04.

Thanks in advance.

---

### Post by poorguy on 2016-07-01
Hey rdb3,

You are not alone as I experience the same problem although I notice mine is only with HD video streaming.

Seems every other update of firefox creates a new issue.

I don't seem to have any problem with this issue using Puppy 64 (Tahrpup 6.0.5) as my browsers are Pale Moon and SeaMonkey which are also Mozilla products.

---

### Post by &amp;KyT$0P# on 2016-07-01
Are these videos Flash or HTML5?

---

### Post by poorguy on 2016-07-01
> **halogen2 said:**
> Are these videos Flash or HTML5?

I don't have Adobe Flash installed so I would think they are HTLM5.

---

### Post by &amp;KyT$0P# on 2016-07-01
Hmm, looks like someone at [mozillaZine]("http://forums.mozillazine.org/viewtopic.php?f=38&t=3012263") has the exact same issue, but no sign of a solution there either...

Being a user of SeaMonkey and Firefox 45 ESR I don't really have any solutions either, sorry... but maybe I can at least help investigating.

If it's specifically YouTube where you see this issue, note that they are using Media Source Extensions to serve the video, and the audio and video are actually separate streams playing simultaneously.  If you just load a "normal" HTML5 video, such as [one of these]("http://www.quirksmode.org/html5/tests/video.html"), does the problem occur?

Does it still occur in a new [profile]("http://kb.mozillazine.org/Profile")?

---

### Post by poorguy on 2016-07-01
Hey halogen2,


Your question.
  If you just load a "normal" HTML5 video, such as [one of these]("http://www.quirksmode.org/html5/tests/video.html"), does the problem occur?

Answer.
No, all 3 Big Buck Bunny test videos work fine.

Your question.
 It's specifically YouTube where you see this issue?

Answer.
Yes only YouTube.

Your question.
Does it still occur in a new [profile]("http://kb.mozillazine.org/Profile")?         

Answer.
I haven't tried a new profile.
I never created any user profile.

I'm not quite sure exactly what that is.

No apologies are needed for not having any solutions as your attempt at a solution is greatly appreciated.
Anyway at least now we know that HTLM5 test video works so that may be a start as to what may or may not be occurring.

Thanks

---

### Post by X-RED_Tech on 2016-07-01
When you login with your Google account at Youtube you load your account profile settings. 
Sometime ago I notice a few users who didn't opt-in for HTML5 when it was experimental in Youtube, had the old Flash being used in Firefox whereas Chrome/Chromium defaulted to HTML5 regardless of user settings.

You can right-click in any video running in FF and check the last line to make sure whether it's using Flash or html5.

And perhaps you can test in a guest session which will use the plain Firefox with all the defaults as installed (no user addons that sometimes have unpredictable results).

---

### Post by poorguy on 2016-07-01
> **X-RED_Tech said:**
> When you login with your Google account at Youtube you load your account profile settings. 
Sometime ago I notice a few users who didn't opt-in for HTML5 when it was experimental in Youtube, had the old Flash being used in Firefox whereas Chrome/Chromium defaulted to HTML5 regardless of user settings.

You can right-click in any video running in FF and check the last line to make sure whether it's using Flash or html5.

And perhaps you can test in a guest session which will use the plain Firefox with all the defaults as installed (no user addons that sometimes have unpredictable results).

I don't have a YouTube account but I will try your suggestion and see what happens.

Thanks

---

### Post by &amp;KyT$0P# on 2016-07-01
> **poorguy said:**
> Your question.
Does it still occur in a new [profile]("http://kb.mozillazine.org/Profile")?         

Answer.
I haven't tried a new profile.
I never created any user profile.

I'm not quite sure exactly what that is.
See the link - the profile is where all the user settings for Firefox are stored.  Firefox creates one for you by default.  Run Firefox from the command line with [FONT=Courier New]-profilemanager[/FONT] option in order to access the built-in profile manager.  Everything there should be self explanatory except to **leave the default folder location when creating a new profile!**  (Changing the default folder location is dangerous and can result in instability and data loss.)

Since Ubuntu doesn't install a customised profile, testing in a Guest session as suggested by X-RED_Tech should be equivalent if you disable all extensions listed under Tools > Add-ons Manager > Extensions (if any).

---

### Post by rdb3 on 2016-07-01
The Big Buck Bunny videos all work fine.

I have the problem on Youtube and on streaming videos (like on news web sites, etc).

I signed into Youtube with my Google account.  I get:

The HTML5 player is currently used when possible.

I went to Extensions in Firefox and disabled the only one showing (Ubuntu Modifications) did a restart, and that did not correct the problem.

---

### Post by &amp;KyT$0P# on 2016-07-01
Given [this comment]("http://forums.mozillazine.org/viewtopic.php?p=14643899#p14643899"), does adding an extension for blocking ads & tracking, such as [uBlock Origin]("https://addons.mozilla.org/addon/ublock-origin/"), get it back in sync?

Another possible work-around if you don't care about 480p or resolutions > 720p, might be to go to about:config, set [FONT=Courier New]media.mediasource.enabled[/FONT] to [FONT=Courier New]false[/FONT], and restart Firefox.  This would make YouTube serve the video as chunks of normal HTML5 video.

---

### Post by fdrake on 2016-07-01
try this:
```

sudo apt-get remove flashplugin*  && sudo apt-get update
sudo apt-get install flashplugin-installer

```
does this solve the issue?

---

### Post by &amp;KyT$0P# on 2016-07-01
@fdrake: the audio lag issue with Flash player 11.2 for Linux is a different problem.
This is an issue with MSE audio & video being out of sync in Firefox, it's nothing to do with Flash...

---

### Post by rdb3 on 2016-07-01
halogen2.... tried  going to about:config and setting [FONT=Courier New]media.mediasource.enabled[/FONT]  to [FONT=Courier New]false..... no luck.

fdrake... tried your suggestion... no luck.

My current work-around is using VLC to watch a youtube video that I'm interested in.
[/FONT]

---

### Post by poorguy on 2016-07-01
Hey rdb3,
 
Is your VLC[FONT=Courier New] work-around[/FONT] working for you?

---

### Post by fdrake on 2016-07-01
can you post here a screen shoot of your firefox adds on?  do you have something like this ?

---

### Post by rdb3 on 2016-07-02
> **poorguy said:**
> Hey rdb3,
 
Is your VLC[FONT=Courier New] work-around[/FONT] working for you?

Yes, youtube links in VLC work fine.

> **fdrake said:**
> can you post here a screen shoot of your firefox adds on?  do you have something like this ?

Yes.

---

### Post by poorguy on 2016-07-02
I really believe this issue is a problem within firefox.

Slimjet browser runs without issues / SeaMonkey browser runs without issues / Pale Moon browser runs without issues. 

I know it isn't a Flash Player problem because I don't install Flash Player.

Why three other browsers run perfectly without problems and firefox has the problem.

I don't know firefox and youtube just seem to have some compatibly issues.

---

### Post by rdb3 on 2016-07-02
It also works great on Kodi Media Center, my first choice.  I have Youtube set up there as Video add-on and I can search and play any youtube video I want that way. 

I'm going to have to install Pale moon and give it a try.  Thanks.

---

### Post by Geoffrey_Arndt on 2016-07-02
Another way:  smplayer and the accompanying youtubebrowser for smplayer.

---

### Post by poorguy on 2016-07-03
Well this is what solved all all of my problems with videos on youtube using Ubuntu Mate 16.04.

After it is installed go into settings under Misc look for "Force the use of flash player on all youtube.com" and uncheck it IMO.

[http://www.slimjet.com/](http://www.slimjet.com/)

---

### Post by rdb3 on 2016-07-03
> **poorguy said:**
> Well this is what solved all all of my problems with videos on youtube using Ubuntu Mate 16.04.

After it is installed go into settings under Misc look for "**Force the use of flash player on all youtube.com**" and **uncheck it** IMO.

[http://www.slimjet.com/](http://www.slimjet.com/)

Yes, Slimjet resolves the youtube issue by unchecking that entry.  Thanks.

How does Slimjet work for you on other streaming sources?

Btw, I went to Chromium > Settings  and it does not have a Miscellaneous section like Slimjet.

---

### Post by rdb3 on 2016-07-03
> **torat_hossain said:**
> your flash might be expired

The flash is current but that doesn't resolve the sync problem in my Firefox.

---

### Post by poorguy on 2016-07-03
> **rdb3 said:**
> Yes, Slimjet resolves the youtube issue by unchecking that entry.  Thanks.

How does Slimjet work for you on other streaming sources?

Btw, I went to Chromium > Settings  and it does not have a Miscellaneous section like Slimjet.

Really well.

Yeah I don't get it either but it works so I'm just going to use it.

Yeah Slimjet seems to smoke a lot of the other browsers right now but when everyone catches on I bet it will become another cluttered up browser.

---

### Post by poorguy on 2016-07-03
> **rdb3 said:**
> The flash is current but that doesn't resolve the sync problem in my Firefox.

Flash player is garbage and problem causing crapola IMO. 

I remove it on any of my computers.

I still think it is a firefox issue every other update seems to work and  then the next doesn't.

---

### Post by poorguy on 2016-07-04
I will say that Slimjet is definitely built off Chrome as it sure uses the memory just as Chrome does. 

That seems to be all I can really find to complain about as Slimjet seems to preform flawlessly in my use of it. 

Runs all the video streaming so far without any hitches and has not crashed or stalled out once.

I would recommend it.

---

### Post by rdb3 on 2016-07-04
I'm going to leave this open just in case someone does come up with a cure for this Firefox problem.

---

### Post by rdb3 on 2016-07-04
I have been a user of Slimjet for awhile now.  Then I did a clean install on this pc and forgot about Slimjet.

It's back on my desktop now.

---

