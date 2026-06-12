---
title: "Alternative to Adobe Flash Player on Firefox"
date: 2015-07-15
forum: New to Ubuntu
---

### Post by MGrowl on 2015-07-15
And yet again, Adobe Flash Player has another zero-day we should all be worried about. I'm sure I'm not the only one tired of it. Can anyone recommend a good alternative to it? Something supported by Ubuntu LTS.

---

### Post by monkeybrain20122 on 2015-07-15
[https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)

Doesn't work on all sites, but on enough of them for most of us. :)

Get up to date mpv from [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) (14.04) or [https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1) (15.04)

<snip>

---

### Post by MGrowl on 2015-07-15
Giving it a try now. Thanks!

---

### Post by monkeybrain20122 on 2015-07-15
@Bucky Ball, youtube-dl is in the official repo, the ppa just provides a up to date version. Since it is used for streaming with mpv  and can be used for sites other than Youtube  rather than for downloading it is not a violation of the coc to mention it.

---

### Post by MGrowl on 2015-07-15
Works great

Btw, I did find it in the official repos too. But it was outdated, so I used the more updated one in the PPA. (regarding youtube-dl)

---

### Post by SeijiSensei on 2015-07-15
I don't see how this works.  I disabled Flash Player in Firefox and left the MPV add-in enabled.  I visited Crunchyroll, one of the sites in the supported list, and was told I needed a copy of Flash to play the video.  I have mpv and youtube-dl both installed.

Visiting YouTube launches its HTML5 player.  I don't know if this is using mpv in the background.  I disabled the Cisco H.264 add-on just to be sure.

---

### Post by monkeybrain20122 on 2015-07-15
> **SeijiSensei said:**
> I don't see how this works.  I disabled Flash Player in Firefox and left the MPV add-in enabled.  I visited Crunchyroll, one of the sites in the supported list, and was told I needed a copy of Flash to play the video.  I have mpv and youtube-dl both installed.

Visiting YouTube launches its HTML5 player.  I don't know if this is using mpv in the background.  I disabled the Cisco H.264 add-on just to be sure.

A disembodied instance of mpv popups to play the video. 

Just tested, it doesn't work on Cruchyroll (maybe you can file a bug report on youtube-dl) But definitely on Youtube, in screenshot I have disabled flash so html 5 player kicked in automatically and mpv is also playing, but you can either close the Youtube window or set flash to "ask to activate" instead that way video will not start in Youtube window. There may be ways to prevent html5 player from starting automatically on Youtube, but I don't know. 

**Edited** Sometimes the addon may start a bit slow so may be you haven't waited long enough. This would seem longer on Youtube since html5 kicks in immediately.

Also You may have other addons which prevent mpv from starting. If still not work can you test with a new profile to be sure?


P.S it defaults to 720p on Youtube if available, for higher resolutions, go to  Tools > Addons > Extensions and add the line 
```
--ytdl-format=bestvideo+bestaudio/best 
```
in Additional player parameters. /best is needed or you get errors on sites other than Youtube which don't use the Dash format.

---

### Post by monkeybrain20122 on 2015-07-15
> **SeijiSensei said:**
> I don't see how this works.  I disabled Flash Player in Firefox and left the MPV add-in enabled.  I visited Crunchyroll, one of the sites in the supported list, and was told I needed a copy of Flash to play the video. 


I think I know why. It seems that Crunchyroll allows only free access to videos for up to 480p. Higher resolution requires membership. The addon's ( or youtube-dl's ) default is 720p if available (to force lower resolution would require settings some parameters). So maybe that's why. But still not right that it doesn't play youtube for you.

---

### Post by mc4man on 2015-07-15
> **monkeybrain20122 said:**
> @Bucky Ball, youtube-dl is in the official repo, the ppa just provides a up to date version. Since it is used for streaming with mpv  and can be used for sites other than Youtube  rather than for downloading it is not a violation of the coc to mention it.

Well the forum or any forum can do as they please in such matters. Also whether Youtube's tos is enforceable to the casual visitor of yt isn't of UF's  interest or concern
(- clearly the browsewrap agreement yt uses is not enforceable to the *casual visitor* as it meets none of requirements set in the US by the 2nd circuit court but again that means nothing in terms of what the forum chooses to do..

---

### Post by Mike_Blanton on 2015-07-15
> **monkeybrain20122 said:**
> [https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)<snip>

I installed this on Firefox, but Youtube still doesn't work. Any Ideas???

Mike

---

### Post by monkeybrain20122 on 2015-07-15
> **Mike_Blanton said:**
> I installed this on Firefox, but Youtube still doesn't work. Any Ideas???

Mike

You also need up to date mpv and youtube-dl installed in the system, the addon is just a script to bind the two. 

See post above for mpv, you have to google for youtube-dl because it is not allowed to give you link here.

---

### Post by MGrowl on 2015-07-16
The mpv and youtube-dl, along with mpv-youtube-dl-binding works fine. 

Additionally, if you're not into updating or installing all of this just to watch videos on youtube without the flash. An even easier way is if you have VLC player already installed; if not, try installing it. It runs pretty much all the relevant video formats. 

Right back to the point, if you have VLC installed and want to watch something on the net requiring flash, you can open VLC up (Copy the URL of the video, or make note of it), go to Media > Open network stream > paste the URL of the said video...sit back and enjoy. Just thought this could be of help as an alternative to some who don't want to install mpv, youtube-dl, and mpv-youtube-dl-binding.

---

### Post by monkeybrain20122 on 2015-07-16
> **MGrowl said:**
> 
Right back to the point, if you have VLC installed and want to watch something on the net requiring flash, you can open VLC up (Copy the URL of the video, or make note of it), go to Media > Open network stream > paste the URL of the said video...sit back and enjoy. Just thought this could be of help as an alternative to some who don't want to install mpv, youtube-dl, and mpv-youtube-dl-binding.

Actually you can just copy the url then click Media > Open location at clipboard, then click play .  It seems to work only on youtube though.

---

### Post by MGrowl on 2015-07-16
> **monkeybrain20122 said:**
> Actually you can just copy the url then click Media > Open location at clipboard, then click play .  It seems to work only on youtube though.

That works, too. Unfortunately, you might be right with it only working on YT, I just tested it on another site and it failed to load. I was trying to test if VLC could work in-place of mpv on the mpv-youtube-dl-binding extension. Or even as a stand-alone program. I wonder if there's any way one could apply "play video with VLC" in the context menu when right-clicking on an online video.

---

### Post by monkeybrain20122 on 2015-07-16
> **MGrowl said:**
> That works, too. Unfortunately, you might be right with it only working on YT, I just tested it on another site and it failed to load. I was trying to test if VLC could work in-place of mpv on the mpv-youtube-dl-binding extension. Or even as a stand-alone program. I wonder if there's any way one could apply "play video with VLC" in the context menu when right-clicking on an online video.

I doubt that vlc can work on so many sites without supporting something like youtube-dl. The closest thing I know would be to use it with Viewtube (a greasemonkey script, so you need the greasemonkey addon) 

See 

[http://trisquel.info/en/forum/viewtube-vlc-abrowser](http://trisquel.info/en/forum/viewtube-vlc-abrowser)

Viewtube download link
[http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en)

The list of supported sites for Viewtube is much smaller than youtube-dl's and it often fails to work on some Youtube channels (such as Vevo) so keep that in mind. I used to use Viewtube with gecko-mediaplayer to replace flash but I have never used it with vlc, so the first link will be useful because there seems to be some tricks (you may find a  "vlc plugin" compatible Videos and something like that in Firefox's plugin list, it is a fake, just good old totem aka Videos)

Anyway, IMO mpv is a better player than vlc. The interface is a bit sparse but probably all you ever need to know for streaming videos is that for  volume control 0 = increase, 9 = decrease, and scrolling along = fast forward. :)

---

### Post by Ricial on 2015-07-16
What PPA should I install for updated youtube-dl version?

---

### Post by MGrowl on 2015-07-16
@halefahrams We can't post it here, it was deleted. Try googling for "youtube-dl PPA 14.04" It's pretty easy to find.

---

### Post by Mike_Walsh on 2015-07-16
> **MGrowl said:**
> And yet again, Adobe Flash Player has another zero-day we should all be worried about. I'm sure I'm not the only one tired of it. Can anyone recommend a good alternative to it? Something supported by Ubuntu LTS.

Just out of curiosity, is there an alternative that will play streaming radio, as well as videos? I listen to Radiotunes a lot (used to be Sky.fm). It uses FlashPlayer to deliver its content, though I'm really not certain what the situation is, vis-a-vis purely audio. I know VLC can play streaming content, as long as you specify the relevant URL.....but does it still **play** via Flash?


Regards,

Mike. :)

---

### Post by SeijiSensei on 2015-07-16
> **monkeybrain20122 said:**
> Anyway, IMO mpv is a better player than vlc. The interface is a bit sparse but probably all you ever need to know for streaming videos is that for  volume control 0 = increase, 9 = decrease, and scrolling along = fast forward. :)
SMPlayer now supports mpv as the engine as well as mplayer if you want a better interface than the native mpv one.  Of course, that doesn't apply to this particular application.

---

### Post by Denny Johnson on 2015-07-16
Hi,
I'm using Firefox.
I just installed mpv and youtube-dl from the Symantic Package Manager, and reinstalled the Watch with MPV add on.
I'm still getting the security warning at you tube.
What else do I need to do?
Change some settings/defaults?
Thanks

---

### Post by MGrowl on 2015-07-16
@Denny Is it the security warning in Firefox for flash? If it is, you should disable shockwave flash found at Plugins in the add-ons tab.

---

### Post by Denny Johnson on 2015-07-16
Thanks MGrowl..........that fixed it.

---

### Post by monkeybrain20122 on 2015-07-16
> **Mike_Walsh said:**
> Just out of curiosity, is there an alternative that will play streaming radio, as well as videos? I listen to Radiotunes a lot (used to be Sky.fm). It uses FlashPlayer to deliver its content, though I'm really not certain what the situation is, vis-a-vis purely audio. I know VLC can play streaming content, as long as you specify the relevant URL.....but does it still **play** via Flash?


Regards,

Mike. :)

Unfortunately not that I know of. You can try user-agent-overrider and fake an iPhone. Not very convenient but probably works. Also if it is a radio station you may be able to stream with something like Rythmbox or Amarok? I don't know.

---

### Post by monkeybrain20122 on 2015-07-16
> **SeijiSensei said:**
> SMPlayer now supports mpv as the engine as well as mplayer if you want a better interface than the native mpv one.  Of course, that doesn't apply to this particular application.

I know, I use Smplayer+mpv for local files. It also stream online contents much the same way as this addon but you need to copy the url and paste it into Smplayer. The addon is more convenient but functionally it is the same.

But actually mpv's interface  is quite OK once you know how things work, like dragging subtitles file into the video to enable it, press S for screenshots etc. 

Edited: The new Smtube is pretty cool too, you can add different external players and pick from the list by right clicking the video, so I have mpv for normal videos and bino for the 3d channel (I don't use it very often but it is good to see that it works. :)) , also can add youtube-dlg (gui for youtube-dl) but I will say no more. ;)

---

### Post by Denny Johnson on 2015-07-16
Any suggestions for viewing Frontline on Firefox?
 I installed mpv and youtube-dl, and installed the Watch with MPV add on, and disabled Shockwave Flash.
You Tube works fine now but not Frontline.
Thanks

---

### Post by monkeybrain20122 on 2015-07-16
> **Denny Johnson said:**
> Any suggestions for viewing Frontline on Firefox?
 I installed mpv and youtube-dl, and installed the Watch with MPV add on, and disabled Shockwave Flash.
You Tube works fine now but not Frontline.
Thanks

I don't know, I am not in the U.S. You can check with youtube-dl's page on github. It is supposed to work.

---

### Post by Mike_Walsh on 2015-07-18
> **monkeybrain20122 said:**
> Unfortunately not that I know of. You can try user-agent-overrider and fake an iPhone. Not very convenient but probably works. Also if it is a radio station you may be able to stream with something like Rythmbox or Amarok? I don't know.

Well, I've sorted it. If you change the output player on the RadioTunes website to VLC, and then hit play, it will provide you with a PLS stream link. VLC is quite happy to work with this.

In the UK, the PLS link as supplied simply repeats, ad nauseam:-

"Due to licensing restrictions in the UK, we recommend you return to the website to enjoy your chosen content..."

This is also because playing direct through the site, they constantly interrupt you every 15 mins, and 'encourage' you to upgrade to the paid, [COLOR=#ff0000]**Premium**[/COLOR] account..! Over my dead body. :P

However; if you then re-route the URL by the use of a proxy, you can get the PLS stream link direct from the site's home territory.....in this case, the US of A. Best of all, I don't need to even bother opening the browser. Having saved the link (which doesn't change), I simply go into VLC, select the link, and hit  'Play'.

Works a treat. Plus, you can listen for hours without constant interruptions. So; I think Flash will be getting a lot less use on **my** machine, at least.....


Regards,

Mike. :)

---

### Post by ray45 on 2016-05-05
Quick fix, use firefox add-ons like "Download YouTube Videos as MP4", and open flv/mp4 files in vlc instead.

---

### Post by oldos2er on 2016-05-06
Please see [http://ubuntuforums.org/showthread.php?t=1850955;](http://ubuntuforums.org/showthread.php?t=1850955;) we do not condone subverting [Youtube's TOS]("https://www.youtube.com/t/terms").

Old thread closed.

---

