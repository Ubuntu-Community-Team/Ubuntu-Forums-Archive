---
title: "Massive Frustration with Cam4/Ubuntu flash drive"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by FrustratedRainbowzz on 2012-02-22
SIGHBALLS.

okay, I have been trying to figure this out for two days. I am kind of a noob, so bear with me. I'm on Ubuntu trying to get my cam set up and working with Cam4 temporarly(yes, I am a cam girl, I know, I know lol). I can get my webcam to work with Cameroid.com, with stickam for streaming, youtube works etc....but with cam4 all i get is the main flash window with a grey screen where the camera should be and a spinning hourglass forever.

What is the dealie-o?

my pc is an Acer Aspire 5742, Acer Crystal Eye Webcam(aka Suyin Webcam). I'm using firefox and have installed the latest flash and tried to allow cam4 in flash(hate the new settings manager btw.) The problem I am running into that I can tell is that I have to allow a second site acess, but it is not listed in the list of sites i have visited(it is like codel.cam4.com or something like that, I can verify if you think it is necessary).

I am booted off of a flash drive, is this why? Seems unusually i would just have an issue with one site like that(though i DID have issues with everything at first).

HELP! I'm losing moneyyyyy 

also, I think i posted this incorrectly in multimedia, but I dont know how to delete from there.

---

### Post by HeroOfCanton on 2012-02-22
Start your troubleshooting here:

[https://help.ubuntu.com/community/Webcam/Troubleshooting#Fixing_Webcam_issues_while_using_Flash_since_Intrepid](https://help.ubuntu.com/community/Webcam/Troubleshooting#Fixing_Webcam_issues_while_using_Flash_since_Intrepid)

P.S. Pics or we don't believe you...  (Only kidding! Don't make the mods ban us both. :D)

---

### Post by yetiman64 on 2012-02-22
> **FrustratedRainbowzz said:**
> ...also, I think i posted this incorrectly in multimedia, but I dont know how to delete from there.
You can't delete a thread, a moderator needs to do the changes.
If you need to bring a post of yours to the attention of the moderators, use the "report abuse" button on the post. The button is not only for abuse, but for any issue the moderators need to be aware of.

I have done the report for you, just in case nobody else did. Cheers, yetiman64 :)

---

### Post by sffvba[e0rt on 2012-02-22
Duplicate removed.


404

---

### Post by FrustratedRainbowzz on 2012-02-22
My heros!

*swoons* 

Okay, if we are being honest, I never swoon. Anyways I am on this right now. IF you guys can help me figure this out, I will actually maybe stick with linux permanently. I mean, two days in I have learned quite a bit already haha.

Watch this space for further info.

---

### Post by FrustratedRainbowzz on 2012-02-22
Okay, I'm running across something!


The library: /usr/lib/libv4l/v4l1compat.so does not exist.

and this:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so firefox 
results in

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

No change so far. Also as a side note, I hated flash years ago in school too.

:(

---

### Post by stoneage on 2012-02-22
Sounds like you might want to install Video For Linux:-
[http://packages.ubuntu.com/oneiric/libv4l-0](http://packages.ubuntu.com/oneiric/libv4l-0)

```
sudo apt-get install libv4l-0
```

---

### Post by FrustratedRainbowzz on 2012-02-22
Okay, not sure whats up here but that .so file is not in that directory on my machine. It does exist, but at:

/rofs/usr/lib/i386-linux-gnu/libv4l

When i changed the directory, I was able to load it into the preload manager

---

### Post by FrustratedRainbowzz on 2012-02-22
also in gstreamer-properties, I don't have a drop down option for V4l1. Just V4l2 and test and custom. I can successfully test the webcam from there when it is on V4l2.

In before someone tells me to stop using a crappy internal camera and get a real one :P

---

### Post by HeroOfCanton on 2012-02-22
Try this command in terminal

```
LD_PRELOAD=/rofs/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so firefox
```If that works add it to your "etc/environment" file.

---

### Post by HeroOfCanton on 2012-02-22
Almost forgot:

... and spend some of that money you're making on a real cam so you can stop using that crappy internal one. :tongue:

---

### Post by stoneage on 2012-02-22
> **FrustratedRainbowzz said:**
> Okay, not sure whats up here but that .so file is not in that directory on my machine. It does exist, but at:

/rofs/usr/lib/i386-linux-gnu/libv4l

When i changed the directory, I was able to load it into the preload managerWhen you say you 'changed the directory'; did you change the directory the application was looking for it in, or did you change the directory it was in? Other apps may be looking to use it too.

On linux it is better to do the former. If something isn't where an application expects it to be, create a symbolic link(basically a virtual signpost saying 'the lib you need is 'over there').

---

### Post by d4m1r on 2012-02-22
Launch firefox from the terminal (just type firefox), go to cam4, and try to broadcast.

Post any other errors here.

---

### Post by FrustratedRainbowzz on 2012-02-22
> **stoneage said:**
> When you say you 'changed the directory'; did you change the directory the application was looking for it in, or did you change the directory it was in? Other apps may be looking to use it too.

On linux it is better to do the former. If something isn't where an application expects it to be, create a symbolic link(basically a virtual signpost saying 'the lib you need is 'over there').
  yea, i just changed the command to reflect the proper directory i found it in.

The rest of what you said I have no idea how to do.

Sidenote: I found something telling me I need to roll back to flash 9. However, everytime I try to do that, in firefox i just get "Firefox has blocked your outdated  plugin" and for some reason, I don't have permssion to copy the .so file for it to the proper folder. Tells me I am not the owner even when i go in with nautilus and root. and then tells me read-only file system.

---

### Post by FrustratedRainbowzz on 2012-02-22
> **d4m1r said:**
> Launch firefox from the terminal (just type firefox), go to cam4, and try to broadcast.

Post any other errors here.

Nope, same.

---

### Post by d4m1r on 2012-02-22
> **FrustratedRainbowzz said:**
> yea, i just changed the command to reflect the proper directory i found it in.

The rest of what you said I have no idea how to do.

Sidenote: I found something telling me I need to roll back to flash 9. However, everytime I try to do that, in firefox i just get "Firefox has blocked your outdated  plugin" and for some reason, I don't have permssion to copy the .so file for it to the proper folder. Tells me I am not the owner even when i go in with nautilus and root. and then tells me read-only file system.

Google firefox addons and search for "Flash Aid".

---

### Post by FrustratedRainbowzz on 2012-02-22
Okay, progress. I can now SEE my video in the background on the broadcast link. However I am stuck on Detecting Video, and though I seem to be able to click start broadcast, nothing happens. Screenshot:

Do you see where it says "start broadcast"? That is seemingly clickable, but does nothing.

---

### Post by FrustratedRainbowzz on 2012-02-22
ETA: no, of course you can't, as I forgot to upload the shot. SHEESH.

---

### Post by FrustratedRainbowzz on 2012-02-22
I am back to the spinning hourglass now again.

[IMG]http://alltheragefaces.com/img/faces/svg/angry-desk-flip.svg[/IMG]

---

### Post by FrustratedRainbowzz on 2012-02-23
Wanted to add - I've now determined that a fresh boot, install flash aid, allow in Flash Settings, Gstreamer-properties and change the video source to V4l2 and 1.3 HD camera (the only other options besides Default and test) will get me to the point where I can SEE the video in the background, but get stuck on detecting video.

What now, fellas?

---

### Post by HeroOfCanton on 2012-02-23
Forgive me if I'm misunderstanding since I don't use that site (nobody wants to see a male geek cam :D), but I'm assuming that's the screen with the broadcast button???

Since you can see the video only thing I can think of is a website issue. Try installing the firefox plug-in called firebug [http://www.getfirebug.com](http://www.getfirebug.com).

Install it, restart your browser, then click on the little firebug icon (looks like a bug) to the right of the address bar and home button. It will open a panel at the bottom.

Click on the Console tab. If it's not enabled by default click the button/link to enable it and reload your page. This will now list all of the dynamic functions/pages loaded by the website.

When you click on that broadcast button does the list grow? If so, is it red or do any errors show? When you click the + and then the response tab is anything returned?

You've already learned how to use the terminal, edit configuration files, and apt-get new packages. Time to debug dynamic functions on a website... You'll be transferring to an IT job in no time. ;)

---

### Post by FrustratedRainbowzz on 2012-02-23
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<img role="presentation" class="twisty "><html>
<img role="presentation" class="twisty "><head>

<img role="presentation" class="twisty "><body>
<img role="presentation" class="twisty "><object id="Cam4VChat" width="100%" height="440" codebase="http://fpdownload.macromedia.com/get/flashplayer/current/swflash.cab" classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000">

<img role="presentation" class="twisty "><div id="tippingDiv" class="tippingPane">
<img role="presentation" class="twisty "><div id="overlayWrap5" class="overlayWrap" style="display:none;">

<img role="presentation" class="twisty "><div id="overlayWrap6" class="overlayWrap" style="display:none;">

<img role="presentation" class="twisty "><div id="overlayWrap1" class="overlayWrap" style="display:none;">

<img role="presentation" class="twisty "><div id="overlayWrap2" class="overlayWrap" style="display:none;">

<img role="presentation" class="twisty "><div id="overlayWrap3" class="overlayWrap" style="display: none; ">

<img role="presentation" class="twisty "><div id="overlayWrap4" class="overlayWrap" style="display:none;">

<img role="presentation" class="twisty "><div id="options">

<img role="presentation" class="twisty "><script type="text/javascript">

<img role="presentation" class="twisty "><div id="widgetBox">


</div>

<img role="presentation" class="twisty "><script type="text/javascript">

<img role="presentation" class="twisty "><script src="/js/overlays.js" type="text/javascript">

<img role="presentation" class="twisty "><script src="http://cdnis3.cam4.com/js/tip.performer_v0.6.js" type="text/javascript">

<img role="presentation" class="twisty "><script src="/js/tip.toolbar.js" type="text/javascript">

<img role="presentation" class="twisty "><script src="/js/local.en.js" type="text/javascript">

<img role="presentation" class="twisty "><link href="/css/tip.css" rel="stylesheet">

<img role="presentation" class="twisty "><script src="/js/cam_view.js" type="text/javascript">

<img role="presentation" class="twisty "><script src="http://tipping.cam4bucks.com/tipper/tipping.class.php?callback=tipping.uS&params={"operation":"createSession","model_id":"rainbowzz","key":"49a8c5a799af1a2e9bd42cc633ba5c64","lang":"en"}&zzz=0.47581541725872256" type="text/javascript">


</body>


</html>


All that. And of course it didn't show any colors when I pasted. hang on. Screenshot  coming

---

### Post by FrustratedRainbowzz on 2012-02-23
Oh also, it made it worse - back to spinning god forsaken hourglass again

---

### Post by FrustratedRainbowzz on 2012-02-23
popBroadcast is not defined

is definetly one of them

---

### Post by FrustratedRainbowzz on 2012-02-23
nm, my net had died.

Alllllllll this though:


Expected ',' or '{' but found '/'.  Ruleset ignored due to bad selector.

profile.css (line 185)

Expected declaration but found '*'.  Skipped to next declaration.

*margin:0;profile.css (line 213, col 3)




Unknown property '-moz-outline-style'.  Declaration dropped.

-moz-outline-style: none;profile.css (line 498, col 20)




Unknown property 'xwidth'.  Declaration dropped.

xwidth: 200px;profile.css (line 924, col 12)




Expected ',' or '{' but found '/'.  Ruleset ignored due to bad selector.

profile.css (line 185)


Expected declaration but found '*'.  Skipped to next declaration.

*margin:0;profile.css (line 213, col 3)




Unknown property '-moz-outline-style'.  Declaration dropped.

-moz-outline-style: none;profile.css (line 498, col 20)




Unknown property 'xwidth'.  Declaration dropped.

xwidth: 200px;profile.css (line 924, col 12)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch:narrower;cam4_v3.5.css (line 517, col 22)




Expected color but found 'invert'.  Error in parsing value for 'outline'.  Declaration dropped.

outline: invert none 0;cam4_v3.5.css (line 625, col 20)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch:narrower;cam4_v3.5.css (line 863, col 42)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch:narrower;cam4_v3.5.css (line 1964, col 23)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch:narrower;cam4_v3.5.css (line 1975, col 23)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch: narrower;cam4_v3.5.css (line 2383, col 27)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch:narrower;cam4_v3.5.css (line 2592, col 22)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch:narrower;cam4_v3.5.css (line 4457, col 22)




Error in parsing value for 'filter'.  Declaration dropped.

... .ui-widget-content .ui-state-disabled {opacity: 1; filter:Alpha(Opacity=100); cam4_v3.5.css (line 4786, col 84)




Error in parsing value for 'filter'.  Declaration dropped.

filter:Alpha(Opacity=50)cam4_v3.5.css (line 4790, col 17)




Error in parsing value for 'font'.  Declaration dropped.

#abuse-form #overlayWrap {width:380px; font:1.1em; color:#333333}cam4_v3.5.css (line 4803, col 51)




Error in parsing value for 'font-stretch'.  Declaration dropped.

...d; color:#555555; font-stretch:narrower; margin:0; padding:0; width:auto; border...cam4_v3.5.css (line 4820, col 85)




Error in parsing value for 'padding'.  Declaration dropped.

padding:none;cam4_v3.5.css (line 4905, col 40)




Error in parsing value for 'filter'.  Declaration dropped.

...-height:32px; opacity:0.50;filter:alpha(opacity=50); font-size:12px; font-weight...cam4_v3.5.css (line 4969, col 104)




Error in parsing value for 'filter'.  Declaration dropped.

.outerFormWrap #progressBar li:hover {opacity:0.85;filter:alpha(opacity=85);}cam4_v3.5.css (line 4970, col 64)




Error in parsing value for 'filter'.  Declaration dropped.

...t-x center 16px; padding:0; height:32px; opacity:0.50;filter:alpha(opacity=50);cam4_v3.5.css (line 4972, col 197)




Error in parsing value for 'filter'.  Declaration dropped.

...Bar li.active {opacity:1.0;filter:alpha(opacity=100);   background:#9b9b9b; colo...cam4_v3.5.css (line 4975, col 64)




Error in parsing value for 'filter'.  Declaration dropped.

...margin-bottom:10px; opacity:0.5!important; filter:alpha(opacity=50)!important; cam4_v3.5.css (line 5098, col 110)




Selector expected.  Ruleset ignored due to bad selector.

...mailUpdateForm #EmailEdit .twoLastTableOptions .button {margin:0}>>>>>>> .r1337cam4_v3.5.css (line 5367, col 69)




Error in parsing value for 'cursor'.  Declaration dropped.

...isplay:block; text-decoration:none; cursor:hand;  text-shadow: 0 0 1px #9C1F67;cam4_v3.5.css (line 5534, col 177)




Unknown property 'diplay'.  Declaration dropped.

#wishListsTab #saveButton {clear:both; diplay: block;}cam4_v3.5.css (line 5693, col 47)




Unknown property 'zoom'.  Declaration dropped.

...eight:bold; text-decoration:none; zoom:1; color:#fff; -moz-border-radius: 18px; ...cam4_v3.5.css (line 5709, col 165)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image: -webkit-gradient(linear, left top, left bottom, from(#ffcc00),...cam4_v3.5.css (line 5719, col 35)




Error in parsing value for 'background-image'.  Declaration dropped.

...ckground-image: -webkit-linear-gradient(top, #ffcc00, #ff9a00); /* Chrome 10+, S...cam4_v3.5.css (line 5720, col 42)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:-ms-linear-gradient(top, #ffcc00, #ff9a00); /* IE10 */cam4_v3.5.css (line 5722, col 37)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:-o-linear-gradient(top, #ffcc00, #ff9a00); /* Opera 11.10+ */cam4_v3.5.css (line 5723, col 36)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image: linear-gradient(top, #ffcc00, #ff9a00);cam4_v3.5.css (line 5724, col 34)




Error in parsing value for 'filter'.  Declaration dropped.

filter: progid:DXImageTransform.Microsoft.gradient(startColorStr='#ffcc00', EndC...cam4_v3.5.css (line 5725, col 15)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image: -webkit-gradient(linear, left top, left bottom, from(#ff9a00),...cam4_v3.5.css (line 5734, col 37)




Error in parsing value for 'background-image'.  Declaration dropped.

...ground-image: -webkit-linear-gradient(top, #ff9a00, #fc531d); /* Chrome 10+, Saf...cam4_v3.5.css (line 5735, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:     -ms-linear-gradient(top, #ff9a00, #fc531d); /* IE10 */cam4_v3.5.css (line 5737, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

...ground-image:      -o-linear-gradient(top, #ff9a00, #fc531d); /* Opera 11.10+ *cam4_v3.5.css (line 5738, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:         linear-gradient(top, #ff9a00, #fc531d);cam4_v3.5.css (line 5739, col 44)




Error in parsing value for 'filter'.  Declaration dropped.

filter: progid:DXImageTransform.Microsoft.gradient(startColorStr='#ff9a00', EndC...cam4_v3.5.css (line 5740, col 27)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image: -webkit-gradient(linear, left top, left bottom, from(#505050),...cam4_v3.5.css (line 5746, col 37)




Error in parsing value for 'background-image'.  Declaration dropped.

...ground-image: -webkit-linear-gradient(top, #505050, #1b1b1b); /* Chrome 10+, Saf...cam4_v3.5.css (line 5747, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:     -ms-linear-gradient(top, #505050, #1b1b1b); /* IE10 */cam4_v3.5.css (line 5749, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

...ground-image:      -o-linear-gradient(top, #505050, #1b1b1b); /* Opera 11.10+ *cam4_v3.5.css (line 5750, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:         linear-gradient(top, #505050, #1b1b1b);cam4_v3.5.css (line 5751, col 44)




Error in parsing value for 'filter'.  Declaration dropped.

filter: progid:DXImageTransform.Microsoft.gradient(startColorStr='#505050', EndC...cam4_v3.5.css (line 5752, col 27)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image: -webkit-gradient(linear, left top, left bottom, from(#404040),...cam4_v3.5.css (line 5758, col 37)




Error in parsing value for 'background-image'.  Declaration dropped.

...ground-image: -webkit-linear-gradient(top, #404040, #010101); /* Chrome 10+, Saf...cam4_v3.5.css (line 5759, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:     -ms-linear-gradient(top, #404040, #010101); /* IE10 */cam4_v3.5.css (line 5761, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

...ground-image:      -o-linear-gradient(top, #404040, #010101); /* Opera 11.10+ *cam4_v3.5.css (line 5762, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:         linear-gradient(top, #404040, #010101);cam4_v3.5.css (line 5763, col 44)




Error in parsing value for 'filter'.  Declaration dropped.

filter: progid:DXImageTransform.Microsoft.gradient(startColorStr='#404040', EndC...cam4_v3.5.css (line 5764, col 17)




Error in parsing value for 'filter'.  Declaration dropped.

...00%; top: 0; left: 0; position: absolute; opacity: 0; filter:Alpha(Opacity=0); jquery-ui.css (line 18, col 107)




Error in parsing value for 'filter'.  Declaration dropped.

...ate-disabled { opacity: .35; filter:Alpha(Opacity=35); background-image: none; jquery-ui.css (line 73, col 87)




Error in parsing value for 'filter'.  Declaration dropped.

...iority-secondary { opacity: .7; filter:Alpha(Opacity=70); font-weight: normal; jquery-ui.css (line 75, col 94)




Error in parsing value for 'filter'.  Declaration dropped.

...i-widget-overlay { background: #000000; opacity: .50;filter:Alpha(Opacity=50); jquery-ui.css (line 281, col 68)




Error in parsing value for 'filter'.  Declaration dropped.

...50% repeat-x; opacity: .20;filter:Alpha(Opacity=20); -moz-border-radius: 5px; -w...jquery-ui.css (line 282, col 165)




Unknown property 'zoom'.  Declaration dropped.

...ordion-header { cursor: pointer; position: relative; margin-top: 1px; zoom: 1; jquery-ui.css (line 284, col 97)




Error in parsing value for 'filter'.  Declaration dropped.

filter: mask(); /*must have*/jquery-ui.css (line 346, col 17)




Unknown property 'zoom'.  Declaration dropped.

...ent { border: 0; padding: .5em 1em; background: none; overflow: auto; zoom: 1; jquery-ui.css (line 359, col 102)




Unknown property 'zoom'.  Declaration dropped.

.ui-tabs { padding: .2em; zoom: 1; }jquery-ui.css (line 397, col 32)




Error in parsing value for 'filter'.  Declaration dropped.

...14px;text-align:center;width:360px;opacity:0;filter:alpha(opacity=0);float:lefttip_v0.2.css (line 190, col 166)




Error in parsing value for 'filter'.  Declaration dropped.

...14px;text-align:center;width:360px;opacity:0;filter:alpha(opacity=0);float:lefttip.css (line 190, col 166)




Error in parsing value for 'filter'.  Declaration dropped.

...14px;text-align:center;width:360px;opacity:0;filter:alpha(opacity=0);float:lefttip.css (line 190, col 166)




Expected ',' or '{' but found '/'.  Ruleset ignored due to bad selector.

profile.css (line 185)


Expected declaration but found '*'.  Skipped to next declaration.

*margin:0;profile.css (line 213, col 3)




Unknown property '-moz-outline-style'.  Declaration dropped.

-moz-outline-style: none;profile.css (line 498, col 20)




Unknown property 'xwidth'.  Declaration dropped.

xwidth: 200px;profile.css (line 924, col 12)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch:narrower;cam4_v3.5.css (line 517, col 22)




Expected color but found 'invert'.  Error in parsing value for 'outline'.  Declaration dropped.

outline: invert none 0;cam4_v3.5.css (line 625, col 20)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch:narrower;cam4_v3.5.css (line 863, col 42)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch:narrower;cam4_v3.5.css (line 1964, col 23)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch:narrower;cam4_v3.5.css (line 1975, col 23)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch: narrower;cam4_v3.5.css (line 2383, col 27)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch:narrower;cam4_v3.5.css (line 2592, col 22)




Error in parsing value for 'font-stretch'.  Declaration dropped.

font-stretch:narrower;cam4_v3.5.css (line 4457, col 22)




Error in parsing value for 'filter'.  Declaration dropped.

... .ui-widget-content .ui-state-disabled {opacity: 1; filter:Alpha(Opacity=100); cam4_v3.5.css (line 4786, col 84)




Error in parsing value for 'filter'.  Declaration dropped.

filter:Alpha(Opacity=50)cam4_v3.5.css (line 4790, col 17)




Error in parsing value for 'font'.  Declaration dropped.

#abuse-form #overlayWrap {width:380px; font:1.1em; color:#333333}cam4_v3.5.css (line 4803, col 51)




Error in parsing value for 'font-stretch'.  Declaration dropped.

...d; color:#555555; font-stretch:narrower; margin:0; padding:0; width:auto; border...cam4_v3.5.css (line 4820, col 85)




Error in parsing value for 'padding'.  Declaration dropped.

padding:none;cam4_v3.5.css (line 4905, col 40)




Error in parsing value for 'filter'.  Declaration dropped.

...-height:32px; opacity:0.50;filter:alpha(opacity=50); font-size:12px; font-weight...cam4_v3.5.css (line 4969, col 104)




Error in parsing value for 'filter'.  Declaration dropped.

.outerFormWrap #progressBar li:hover {opacity:0.85;filter:alpha(opacity=85);}cam4_v3.5.css (line 4970, col 64)




Error in parsing value for 'filter'.  Declaration dropped.

...t-x center 16px; padding:0; height:32px; opacity:0.50;filter:alpha(opacity=50);cam4_v3.5.css (line 4972, col 197)




Error in parsing value for 'filter'.  Declaration dropped.

...Bar li.active {opacity:1.0;filter:alpha(opacity=100);   background:#9b9b9b; colo...cam4_v3.5.css (line 4975, col 64)




Error in parsing value for 'filter'.  Declaration dropped.

...margin-bottom:10px; opacity:0.5!important; filter:alpha(opacity=50)!important; cam4_v3.5.css (line 5098, col 110)




Selector expected.  Ruleset ignored due to bad selector.

...mailUpdateForm #EmailEdit .twoLastTableOptions .button {margin:0}>>>>>>> .r1337cam4_v3.5.css (line 5367, col 69)




Error in parsing value for 'cursor'.  Declaration dropped.

...isplay:block; text-decoration:none; cursor:hand;  text-shadow: 0 0 1px #9C1F67;cam4_v3.5.css (line 5534, col 177)




Unknown property 'diplay'.  Declaration dropped.

#wishListsTab #saveButton {clear:both; diplay: block;}cam4_v3.5.css (line 5693, col 47)




Unknown property 'zoom'.  Declaration dropped.

...eight:bold; text-decoration:none; zoom:1; color:#fff; -moz-border-radius: 18px; ...cam4_v3.5.css (line 5709, col 165)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image: -webkit-gradient(linear, left top, left bottom, from(#ffcc00),...cam4_v3.5.css (line 5719, col 35)




Error in parsing value for 'background-image'.  Declaration dropped.

...ckground-image: -webkit-linear-gradient(top, #ffcc00, #ff9a00); /* Chrome 10+, S...cam4_v3.5.css (line 5720, col 42)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:-ms-linear-gradient(top, #ffcc00, #ff9a00); /* IE10 */cam4_v3.5.css (line 5722, col 37)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:-o-linear-gradient(top, #ffcc00, #ff9a00); /* Opera 11.10+ */cam4_v3.5.css (line 5723, col 36)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image: linear-gradient(top, #ffcc00, #ff9a00);cam4_v3.5.css (line 5724, col 34)




Error in parsing value for 'filter'.  Declaration dropped.

filter: progid:DXImageTransform.Microsoft.gradient(startColorStr='#ffcc00', EndC...cam4_v3.5.css (line 5725, col 15)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image: -webkit-gradient(linear, left top, left bottom, from(#ff9a00),...cam4_v3.5.css (line 5734, col 37)




Error in parsing value for 'background-image'.  Declaration dropped.

...ground-image: -webkit-linear-gradient(top, #ff9a00, #fc531d); /* Chrome 10+, Saf...cam4_v3.5.css (line 5735, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:     -ms-linear-gradient(top, #ff9a00, #fc531d); /* IE10 */cam4_v3.5.css (line 5737, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

...ground-image:      -o-linear-gradient(top, #ff9a00, #fc531d); /* Opera 11.10+ *cam4_v3.5.css (line 5738, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:         linear-gradient(top, #ff9a00, #fc531d);cam4_v3.5.css (line 5739, col 44)




Error in parsing value for 'filter'.  Declaration dropped.

filter: progid:DXImageTransform.Microsoft.gradient(startColorStr='#ff9a00', EndC...cam4_v3.5.css (line 5740, col 27)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image: -webkit-gradient(linear, left top, left bottom, from(#505050),...cam4_v3.5.css (line 5746, col 37)




Error in parsing value for 'background-image'.  Declaration dropped.

...ground-image: -webkit-linear-gradient(top, #505050, #1b1b1b); /* Chrome 10+, Saf...cam4_v3.5.css (line 5747, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:     -ms-linear-gradient(top, #505050, #1b1b1b); /* IE10 */cam4_v3.5.css (line 5749, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

...ground-image:      -o-linear-gradient(top, #505050, #1b1b1b); /* Opera 11.10+ *cam4_v3.5.css (line 5750, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:         linear-gradient(top, #505050, #1b1b1b);cam4_v3.5.css (line 5751, col 44)




Error in parsing value for 'filter'.  Declaration dropped.

filter: progid:DXImageTransform.Microsoft.gradient(startColorStr='#505050', EndC...cam4_v3.5.css (line 5752, col 27)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image: -webkit-gradient(linear, left top, left bottom, from(#404040),...cam4_v3.5.css (line 5758, col 37)




Error in parsing value for 'background-image'.  Declaration dropped.

...ground-image: -webkit-linear-gradient(top, #404040, #010101); /* Chrome 10+, Saf...cam4_v3.5.css (line 5759, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:     -ms-linear-gradient(top, #404040, #010101); /* IE10 */cam4_v3.5.css (line 5761, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

...ground-image:      -o-linear-gradient(top, #404040, #010101); /* Opera 11.10+ *cam4_v3.5.css (line 5762, col 44)




Error in parsing value for 'background-image'.  Declaration dropped.

background-image:         linear-gradient(top, #404040, #010101);cam4_v3.5.css (line 5763, col 44)




Error in parsing value for 'filter'.  Declaration dropped.

filter: progid:DXImageTransform.Microsoft.gradient(startColorStr='#404040', EndC...cam4_v3.5.css (line 5764, col 17)




Error in parsing value for 'filter'.  Declaration dropped.

...00%; top: 0; left: 0; position: absolute; opacity: 0; filter:Alpha(Opacity=0); jquery-ui.css (line 18, col 107)




Error in parsing value for 'filter'.  Declaration dropped.

...ate-disabled { opacity: .35; filter:Alpha(Opacity=35); background-image: none; jquery-ui.css (line 73, col 87)




Error in parsing value for 'filter'.  Declaration dropped.

...iority-secondary { opacity: .7; filter:Alpha(Opacity=70); font-weight: normal; jquery-ui.css (line 75, col 94)




Error in parsing value for 'filter'.  Declaration dropped.

...i-widget-overlay { background: #000000; opacity: .50;filter:Alpha(Opacity=50); jquery-ui.css (line 281, col 68)




Error in parsing value for 'filter'.  Declaration dropped.

...50% repeat-x; opacity: .20;filter:Alpha(Opacity=20); -moz-border-radius: 5px; -w...jquery-ui.css (line 282, col 165)




Unknown property 'zoom'.  Declaration dropped.

...ordion-header { cursor: pointer; position: relative; margin-top: 1px; zoom: 1; jquery-ui.css (line 284, col 97)




Error in parsing value for 'filter'.  Declaration dropped.

filter: mask(); /*must have*/jquery-ui.css (line 346, col 17)




Unknown property 'zoom'.  Declaration dropped.

...ent { border: 0; padding: .5em 1em; background: none; overflow: auto; zoom: 1; jquery-ui.css (line 359, col 102)




Unknown property 'zoom'.  Declaration dropped.

.ui-tabs { padding: .2em; zoom: 1; }jquery-ui.css (line 397, col 32)




Error in parsing value for 'filter'.  Declaration dropped.

...14px;text-align:center;width:360px;opacity:0;filter:alpha(opacity=0);float:lefttip_v0.2.css (line 190, col 166)




Use of getAttributeNodeNS() is deprecated. Use getAttributeNS() instead.

Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.




Error in parsing value for 'filter'.  Declaration dropped.

---

### Post by HeroOfCanton on 2012-02-23
Wow. That's a lot of bad css declarations! Unfortunately, none of that really helped solve this problem...

Let's try this:

Load the page. Hit "Clear" in the console. Click the broadcast button. Take a screenshot and post. (Get everything returned in the Console section if possible)

---

### Post by FrustratedRainbowzz on 2012-02-24
thought of something...
I downloaded Opera, because it can list errors.Here is what I got:



Validation Output: 56 Errors 
 Line 13, Column 1: Missing xmlns attribute for element html. The value should be: [http://www.w3.org/1999/xhtml](http://www.w3.org/1999/xhtml) 
<html>

&#9993; 

 Many Document Types based on XML need a mandatory xmlns attribute on the root element. For example, the root element for XHTML might look like:
<html xmlns="http://www.w3.org/1999/xhtml"> 
 Line 15, Column 20: there is no attribute "http-equiv" 
  <META http-equiv="content-type" content="text/html; charset=UTF-8" />

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 15, Column 43: there is no attribute "content" 
  <META http-equiv="content-type" content="text/html; charset=UTF-8" />

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 15, Column 71: element "META" undefined 
  <META http-equiv="content-type" content="text/html; charset=UTF-8" />

&#9993; 

 You have used the element named above in your document, but the document type you are using does not define an element of that name. This error is often caused by: 
incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Frameset" document type to get the "<frameset>" element),
by using vendor proprietary extensions such as "<spacer>" or "<marquee>" (this is usually fixed by using CSS to achieve the desired effect instead).
by using upper-case tags in XHTML (in XHTML attributes and elements must be all lower-case).
 Line 39, Column 86: document type does not allow element "object" here; missing one of "p", "h1", "h2", "h3", "h4", "h5", "h6", "div", "address", "fieldset", "ins", "del" start-tag 
…odebase="http://fpdownload.macromedia.com/get/flashplayer/current/swflash.cab">

&#9993; 

 The mentioned element is not allowed to appear in the context in which you've placed it; the other mentioned elements are the only ones that are both allowed there and can contain the element mentioned. This might mean that you need a containing element, or possibly that you've forgotten to close a previous element. 

 One possible cause for this message is that you have attempted to put a block-level element (such as "<p>" or "<table>") inside an inline element (such as "<a>", "<span>", or "<font>"). 
 Line 46, Column 48: cannot generate system identifier for general entity "room" 
…ram name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz&access…

&#9993; 

 An entity reference was found in the document, but there is no reference by that name defined. Often this is caused by misspelling the reference name, unencoded ampersands, or by leaving off the trailing semicolon (;). The most common cause of this error is unencoded ampersands in URLs as described by the WDG in "Ampersands in URLs". 

 Entity references start with an ampersand (&) and end with a semicolon (;). If you want to use a literal ampersand in your document you must encode it as "&amp;" (even inside URLs!). Be careful to end entity references with a semicolon or your entity reference may get interpreted in connection with the following text. Also keep in mind that named entity references are case-sensitive; &Aelig; and &aelig; are different characters. 

 If this error appears in some markup generated by PHP's session handling code, this article has explanations and solutions to your problem. 

 Note that in most documents, errors related to entity references will trigger up to 5 separate messages from the Validator. Usually these will all disappear when the original problem is fixed. 
 Line 46, Column 48: general entity "room" not defined and no default entity 
…ram name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz&access…

&#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 52: reference not terminated by REFC delimiter 
…name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz&accessHash…

&#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 46, Column 52: reference to external entity in attribute value 
…name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz&accessHash…

&#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 46, Column 52: reference to entity "room" for which no system identifier could be generated 
…name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz&accessHash…

&#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 47: entity was defined here 
…aram name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz&acces…
 Line 46, Column 63: cannot generate system identifier for general entity "username" 
…Vars" value="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9…

&#9993; 

 An entity reference was found in the document, but there is no reference by that name defined. Often this is caused by misspelling the reference name, unencoded ampersands, or by leaving off the trailing semicolon (;). The most common cause of this error is unencoded ampersands in URLs as described by the WDG in "Ampersands in URLs". 

 Entity references start with an ampersand (&) and end with a semicolon (;). If you want to use a literal ampersand in your document you must encode it as "&amp;" (even inside URLs!). Be careful to end entity references with a semicolon or your entity reference may get interpreted in connection with the following text. Also keep in mind that named entity references are case-sensitive; &Aelig; and &aelig; are different characters. 

 If this error appears in some markup generated by PHP's session handling code, this article has explanations and solutions to your problem. 

 Note that in most documents, errors related to entity references will trigger up to 5 separate messages from the Validator. Usually these will all disappear when the original problem is fixed. 
 Line 46, Column 63: general entity "username" not defined and no default entity 
…Vars" value="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9…

&#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 71: reference not terminated by REFC delimiter 
…lue="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01…

&#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 46, Column 71: reference to external entity in attribute value 
…lue="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01…

&#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 46, Column 71: reference to entity "username" for which no system identifier could be generated 
…lue="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01…

&#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 62: entity was defined here 
…hVars" value="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab…
 Line 46, Column 82: cannot generate system identifier for general entity "accessHash" 
…=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01bf6ac5b3ef1…

&#9993; 

 An entity reference was found in the document, but there is no reference by that name defined. Often this is caused by misspelling the reference name, unencoded ampersands, or by leaving off the trailing semicolon (;). The most common cause of this error is unencoded ampersands in URLs as described by the WDG in "Ampersands in URLs". 

 Entity references start with an ampersand (&) and end with a semicolon (;). If you want to use a literal ampersand in your document you must encode it as "&amp;" (even inside URLs!). Be careful to end entity references with a semicolon or your entity reference may get interpreted in connection with the following text. Also keep in mind that named entity references are case-sensitive; &Aelig; and &aelig; are different characters. 

 If this error appears in some markup generated by PHP's session handling code, this article has explanations and solutions to your problem. 

 Note that in most documents, errors related to entity references will trigger up to 5 separate messages from the Validator. Usually these will all disappear when the original problem is fixed. 
 Line 46, Column 82: general entity "accessHash" not defined and no default entity 
…=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01bf6ac5b3ef1…

&#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 92: reference not terminated by REFC delimiter 
…om=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01bf6ac5b3ef17dc" />

&#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 46, Column 92: reference to external entity in attribute value 
…om=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01bf6ac5b3ef17dc" />

&#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 46, Column 92: reference to entity "accessHash" for which no system identifier could be generated 
…om=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01bf6ac5b3ef17dc" />

&#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 81: entity was defined here 
…e=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01bf6ac5b3ef…
 Line 47, Column 18: there is no attribute "src" 
      <embed src="/client/Cam4_4.3.0.swf" quality="high" bgcolor="#ffffff"

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 47, Column 51: there is no attribute "quality" 
      <embed src="/client/Cam4_4.3.0.swf" quality="high" bgcolor="#ffffff"

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 47, Column 66: there is no attribute "bgcolor" 
      <embed src="/client/Cam4_4.3.0.swf" quality="high" bgcolor="#ffffff"

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 48, Column 17: there is no attribute "width" 
          width="100%" height="440" name="Cam4VChat" align="middle"

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 48, Column 31: there is no attribute "height" 
          width="100%" height="440" name="Cam4VChat" align="middle"

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 48, Column 42: there is no attribute "name" 
          width="100%" height="440" name="Cam4VChat" align="middle"

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 48, Column 60: there is no attribute "align" 
          width="100%" height="440" name="Cam4VChat" align="middle"

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 49, Column 16: there is no attribute "play" 
          play="true"

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 50, Column 16: there is no attribute "loop" 
          loop="false"

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 51, Column 19: duplicate specification of attribute "quality" 
          quality="high"

&#9993; 

 You have specified an attribute more than once. Example: Using the "height" attribute twice on the same "img" tag. 
 Line 52, Column 17: there is no attribute "wmode" 
          wmode="opaque"

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 53, Column 21: there is no attribute "FlashVars" 
          FlashVars="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee…

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 53, Column 36: reference not terminated by REFC delimiter 
          FlashVars="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee…

&#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 53, Column 36: reference to external entity in attribute value 
          FlashVars="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee…

&#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 53, Column 36: reference to entity "room" for which no system identifier could be generated 
          FlashVars="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee…

&#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 47: entity was defined here 
…aram name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz&acces…
 Line 53, Column 55: reference not terminated by REFC delimiter 
…ars="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01…

&#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 53, Column 55: reference to external entity in attribute value 
…ars="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01…

&#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 53, Column 55: reference to entity "username" for which no system identifier could be generated 
…ars="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01…

&#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 62: entity was defined here 
…hVars" value="locale=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab…
 Line 53, Column 76: reference not terminated by REFC delimiter 
…&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01bf6ac5b3ef17dc"

&#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 53, Column 76: reference to external entity in attribute value 
…&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01bf6ac5b3ef17dc"

&#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 53, Column 76: reference to entity "accessHash" for which no system identifier could be generated 
…&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01bf6ac5b3ef17dc"

&#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 81: entity was defined here 
…e=en&room=rainbowzz&username=rainbowzz&accessHash=7ee0435ab9b123cd01bf6ac5b3ef…
 Line 54, Column 27: there is no attribute "allowFullScreen" 
          allowFullScreen="true"

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 55, Column 29: there is no attribute "allowScriptAccess" 
          allowScriptAccess="always"

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 56, Column 16: there is no attribute "type" 
          type="application/x-shockwave-flash"

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 57, Column 23: there is no attribute "pluginspage" 
          pluginspage="http://www.adobe.com/go/getflashplayer">

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 57, Column 63: element "embed" undefined 
          pluginspage="http://www.adobe.com/go/getflashplayer">

&#9993; 

 You have used the element named above in your document, but the document type you are using does not define an element of that name. This error is often caused by: 
incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Frameset" document type to get the "<frameset>" element),
by using vendor proprietary extensions such as "<spacer>" or "<marquee>" (this is usually fixed by using CSS to achieve the desired effect instead).
by using upper-case tags in XHTML (in XHTML attributes and elements must be all lower-case).
 Line 81, Column 210: end tag for "br" omitted, but OMITTAG NO was specified 
…>MANAGE YOUR PRIVACY FEATURES</h1><br>You can set your cam show to private mod…

&#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 81, Column 206: start tag was here 
…><h1>MANAGE YOUR PRIVACY FEATURES</h1><br>You can set your cam show to private…
 Line 82, Column 215: end tag for "br" omitted, but OMITTAG NO was specified 
…CT VIEWERS FOR A PRIVATE SHOW</h1><br>Would you like to have a private or excl…

&#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 82, Column 211: start tag was here 
…SELECT VIEWERS FOR A PRIVATE SHOW</h1><br>Would you like to have a private or …
 Line 83, Column 211: end tag for "br" omitted, but OMITTAG NO was specified 
…HOW TO WATCH MULTIPLE WEBCAMS</h1><br>As a Gold Member, you may watch multiple…

&#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 83, Column 207: start tag was here 
…<h1>HOW TO WATCH MULTIPLE WEBCAMS</h1><br>As a Gold Member, you may watch mult…
 Line 84, Column 229: end tag for "select" which is not finished 
…sage to <select id="roomList"></select></h1><br><textarea style="width:790px;h…

&#9993; 

 Most likely, you nested tags and closed them in the wrong order. For example <p><em>...</p> is not acceptable, as <em> must be closed before <p>. Acceptable nesting is: <p><em>...</em></p> 

 Another possibility is that you used an element which requires a child element that you did not include. Hence the parent element is "not finished", not complete. For instance, in HTML the <head> element must contain a <title> child element, lists require appropriate list items (<ul> and <ol> require <li>; <dl> requires <dt> and <dd>), and so on. 
 Line 84, Column 239: end tag for "br" omitted, but OMITTAG NO was specified 
…elect id="roomList"></select></h1><br><textarea style="width:790px;height:100p…

&#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 84, Column 235: start tag was here 
…o <select id="roomList"></select></h1><br><textarea style="width:790px;height:…
 Line 84, Column 305: required attribute "rows" not specified 
…;height:100px" id="privateMessageText"></textarea><br><input type="submit" val…

&#9993; 

 The attribute given above is required for an element that you've used, but you have omitted it. For instance, in most HTML and XHTML document types the "type" attribute is required on the "script" element and the "alt" attribute is required for the "img" element. 

 Typical values for type are type="text/css" for <style> and type="text/javascript" for <script>. 
 Line 84, Column 305: required attribute "cols" not specified 
…;height:100px" id="privateMessageText"></textarea><br><input type="submit" val…

&#9993; 

 The attribute given above is required for an element that you've used, but you have omitted it. For instance, in most HTML and XHTML document types the "type" attribute is required on the "script" element and the "alt" attribute is required for the "img" element. 

 Typical values for type are type="text/css" for <style> and type="text/javascript" for <script>. 
 Line 84, Column 321: end tag for "br" omitted, but OMITTAG NO was specified 
…d="privateMessageText"></textarea><br><input type="submit" value="Send" align=…

&#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 84, Column 317: start tag was here 
…x" id="privateMessageText"></textarea><br><input type="submit" value="Send" al…
 Line 84, Column 361: there is no attribute "align" 
…nput type="submit" value="Send" align="right" onclick="sendPrivateMessage();">…

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 84, Column 406: end tag for "input" omitted, but OMITTAG NO was specified 
…submit" value="Send" align="right" onclick="sendPrivateMessage();"></div></div>

&#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 84, Column 321: start tag was here 
…d="privateMessageText"></textarea><br><input type="submit" value="Send" align=…
 Line 85, Column 218: end tag for "br" omitted, but OMITTAG NO was specified 
… WEBCAM SHOWS IN FULL SCREEN!</h1><br>Would you like to get a little closer to…

&#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 85, Column 214: start tag was here 
…ATCH WEBCAM SHOWS IN FULL SCREEN!</h1><br>Would you like to get a little close…
 Line 85, Column 335: end tag for "br" omitted, but OMITTAG NO was specified 
…screen with a Cam4Gold membership.<br><br>CAM4Gold is available for as little …

&#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 85, Column 331: start tag was here 
…ull screen with a Cam4Gold membership.<br><br>CAM4Gold is available for as lit…
 Line 85, Column 339: end tag for "br" omitted, but OMITTAG NO was specified 
…en with a Cam4Gold membership.<br><br>CAM4Gold is available for as little as $…

&#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 85, Column 335: start tag was here 
…screen with a Cam4Gold membership.<br><br>CAM4Gold is available for as little …
 Line 86, Column 1127: there is no attribute "id" 
…></div><div class="avatar"><iframe id="avatarFrame" frameborder="0" width="278…

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 86, Column 1153: there is no attribute "frameborder" 
…><iframe id="avatarFrame" frameborder="0" width="278" height="190"  scrolling=…

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 86, Column 1163: there is no attribute "width" 
…d="avatarFrame" frameborder="0" width="278" height="190"  scrolling="no" src="…

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 86, Column 1176: there is no attribute "height" 
…e" frameborder="0" width="278" height="190"  scrolling="no" src="/profiles/ava…

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 86, Column 1193: there is no attribute "scrolling" 
…" width="278" height="190"  scrolling="no" src="/profiles/avatarUpload.jsp"></…

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 86, Column 1202: there is no attribute "src" 
…278" height="190"  scrolling="no" src="/profiles/avatarUpload.jsp"></iframe></…

&#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 86, Column 1230: element "iframe" undefined 
…="no" src="/profiles/avatarUpload.jsp"></iframe></div><div class="abuse"><h1>A…

&#9993; 

 You have used the element named above in your document, but the document type you are using does not define an element of that name. This error is often caused by: 
incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Frameset" document type to get the "<frameset>" element),
by using vendor proprietary extensions such as "<spacer>" or "<marquee>" (this is usually fixed by using CSS to achieve the desired effect instead).
by using upper-case tags in XHTML (in XHTML attributes and elements must be all lower-case).
 Line 86, Column 1482: end tag for "select" which is not finished 
…me="userBlist" id="userBlist"></select></div><div class="buttonWrap"><a onclic…

&#9993; 

 Most likely, you nested tags and closed them in the wrong order. For example <p><em>...</p> is not acceptable, as <em> must be closed before <p>. Acceptable nesting is: <p><em>...</em></p> 

 Another possibility is that you used an element which requires a child element that you did not include. Hence the parent element is "not finished", not complete. For instance, in HTML the <head> element must contain a <title> child element, lists require appropriate list items (<ul> and <ol> require <li>; <dl> requires <dt> and <dd>), and so on. 
 Line 87, Column 397: cannot generate system identifier for general entity "key" 
…r/reporting/lboard.php?user_id='+uN+'&key='+kN+'&lang='+lang+'&session_id='+ti…

&#9993; 

 An entity reference was found in the document, but there is no reference by that name defined. Often this is caused by misspelling the reference name, unencoded ampersands, or by leaving off the trailing semicolon (;). The most common cause of this error is unencoded ampersands in URLs as described by the WDG in "Ampersands in URLs". 

 Entity references start with an ampersand (&) and end with a semicolon (;). If you want to use a literal ampersand in your document you must encode it as "&amp;" (even inside URLs!). Be careful to end entity references with a semicolon or your entity reference may get interpreted in connection with the following text. Also keep in mind that named entity references are case-sensitive; &Aelig; and &aelig; are different characters. 

 If this error appears in some markup generated by PHP's session handling code, this article has explanations and solutions to your problem. 

 Note that in most documents, errors related to entity references will trigger up to 5 separate messages from the Validator. Usually these will all disappear when the original problem is fixed. 
 Line 87, Column 397: general entity "key" not defined and no default entity 
…r/reporting/lboard.php?user_id='+uN+'&key='+kN+'&lang='+lang+'&session_id='+ti…

&#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 87, Column 400: reference not terminated by REFC delimiter 
…eporting/lboard.php?user_id='+uN+'&key='+kN+'&lang='+lang+'&session_id='+tippi…

&#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 87, Column 400: reference to external entity in attribute value 
…eporting/lboard.php?user_id='+uN+'&key='+kN+'&lang='+lang+'&session_id='+tippi…

&#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 87, Column 400: reference to entity "key" for which no system identifier could be generated 
…eporting/lboard.php?user_id='+uN+'&key='+kN+'&lang='+lang+'&session_id='+tippi…

&#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 87, Column 396: entity was defined here 
…er/reporting/lboard.php?user_id='+uN+'&key='+kN+'&lang='+lang+'&session_id='+t…
 Line 87, Column 412: reference not terminated by REFC delimiter 
…ard.php?user_id='+uN+'&key='+kN+'&lang='+lang+'&session_id='+tipping.sID,'lead…

&#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 87, Column 422: cannot generate system identifier for general entity "session_id" 
…er_id='+uN+'&key='+kN+'&lang='+lang+'&session_id='+tipping.sID,'leaderboard','…

&#9993; 

 An entity reference was found in the document, but there is no reference by that name defined. Often this is caused by misspelling the reference name, unencoded ampersands, or by leaving off the trailing semicolon (;). The most common cause of this error is unencoded ampersands in URLs as described by the WDG in "Ampersands in URLs". 

 Entity references start with an ampersand (&) and end with a semicolon (;). If you want to use a literal ampersand in your document you must encode it as "&amp;" (even inside URLs!). Be careful to end entity references with a semicolon or your entity reference may get interpreted in connection with the following text. Also keep in mind that named entity references are case-sensitive; &Aelig; and &aelig; are different characters. 

 If this error appears in some markup generated by PHP's session handling code, this article has explanations and solutions to your problem. 

 Note that in most documents, errors related to entity references will trigger up to 5 separate messages from the Validator. Usually these will all disappear when the original problem is fixed. 
 Line 87, Column 422: general entity "session_id" not defined and no default entity 
…er_id='+uN+'&key='+kN+'&lang='+lang+'&session_id='+tipping.sID,'leaderboard','…

&#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 87, Column 432: reference not terminated by REFC delimiter 
…+'&key='+kN+'&lang='+lang+'&session_id='+tipping.sID,'leaderboard','width=700,…

&#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 87, Column 432: reference to external entity in attribute value 
…+'&key='+kN+'&lang='+lang+'&session_id='+tipping.sID,'leaderboard','width=700,…

&#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 87, Column 432: reference to entity "session_id" for which no system identifier could be generated 
…+'&key='+kN+'&lang='+lang+'&session_id='+tipping.sID,'leaderboard','width=700,…

&#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 87, Column 421: entity was defined here 
…ser_id='+uN+'&key='+kN+'&lang='+lang+'&session_id='+tipping.sID,'leaderboard',…

---

### Post by audiomick on 2012-02-24
Hey Rainbow, there's a button at the top of the post window that is marked with a hash
#
if you hit that and then put that output between the tags
[tag] here [/tag] where the word "code" is in place of "tag", then your output will appear in a nice box with a scroll bar on the side that makes it a lot easier to navigate the thread.

The added advantage is that stuff between code tags is printed exactly as it is and not interpreted as a smiley or anything. Sometimes relevant when problem solving. ;)

If you feel inspired, you can also go back and edit the posts you have made already. Highlight the output, then hit the button. :)

---

### Post by FrustratedRainbowzz on 2012-02-24
```
Validation Output: 56 Errors 
 Line 13, Column 1: Missing xmlns attribute for element html. The value should be: http://www.w3.org/1999/xhtml 
 <html>

 &#9993; 

 Many Document Types based on XML need a mandatory xmlns attribute on the root element. For example, the root element for XHTML might look like:
 <html xmlns="http://www.w3.org/1999/xhtml"> 
 Line 15, Column 20: there is no attribute "http-equiv" 
 <META http-equiv="content-type" content="text/html; charset=UTF-8" />

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 15, Column 43: there is no attribute "content" 
 <META http-equiv="content-type" content="text/html; charset=UTF-8" />

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 15, Column 71: element "META" undefined 
 <META http-equiv="content-type" content="text/html; charset=UTF-8" />

 &#9993; 

 You have used the element named above in your document, but the document type you are using does not define an element of that name. This error is often caused by: 
 incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Frameset" document type to get the "<frameset>" element),
 by using vendor proprietary extensions such as "<spacer>" or "<marquee>" (this is usually fixed by using CSS to achieve the desired effect instead).
 by using upper-case tags in XHTML (in XHTML attributes and elements must be all lower-case).
 Line 39, Column 86: document type does not allow element "object" here; missing one of "p", "h1", "h2", "h3", "h4", "h5", "h6", "div", "address", "fieldset", "ins", "del" start-tag 
 …odebase="http://fpdownload.macromedia.com/get/flashplayer/current/swflash.cab">

 &#9993; 

 The mentioned element is not allowed to appear in the context in which you've placed it; the other mentioned elements are the only ones that are both allowed there and can contain the element mentioned. This might mean that you need a containing element, or possibly that you've forgotten to close a previous element. 

 One possible cause for this message is that you have attempted to put a block-level element (such as "<p>" or "<table>") inside an inline element (such as "<a>", "<span>", or "<font>"). 
 Line 46, Column 48: cannot generate system identifier for general entity "room" 
 …ram name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz &access…

 &#9993; 

 An entity reference was found in the document, but there is no reference by that name defined. Often this is caused by misspelling the reference name, unencoded ampersands, or by leaving off the trailing semicolon (;). The most common cause of this error is unencoded ampersands in URLs as described by the WDG in "Ampersands in URLs". 

 Entity references start with an ampersand (&) and end with a semicolon (;). If you want to use a literal ampersand in your document you must encode it as "&amp;" (even inside URLs!). Be careful to end entity references with a semicolon or your entity reference may get interpreted in connection with the following text. Also keep in mind that named entity references are case-sensitive; &Aelig; and &aelig; are different characters. 

 If this error appears in some markup generated by PHP's session handling code, this article has explanations and solutions to your problem. 

 Note that in most documents, errors related to entity references will trigger up to 5 separate messages from the Validator. Usually these will all disappear when the original problem is fixed. 
 Line 46, Column 48: general entity "room" not defined and no default entity 
 …ram name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz &access…

 &#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 52: reference not terminated by REFC delimiter 
 …name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz &accessHash…

 &#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 46, Column 52: reference to external entity in attribute value 
 …name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz &accessHash…

 &#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 46, Column 52: reference to entity "room" for which no system identifier could be generated 
 …name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz &accessHash…

 &#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 47: entity was defined here 
 …aram name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz &acces…
 Line 46, Column 63: cannot generate system identifier for general entity "username" 
 …Vars" value="locale=en&room=rainbowzz&username=rainbowzz &accessHash=7ee0435ab9…

 &#9993; 

 An entity reference was found in the document, but there is no reference by that name defined. Often this is caused by misspelling the reference name, unencoded ampersands, or by leaving off the trailing semicolon (;). The most common cause of this error is unencoded ampersands in URLs as described by the WDG in "Ampersands in URLs". 

 Entity references start with an ampersand (&) and end with a semicolon (;). If you want to use a literal ampersand in your document you must encode it as "&amp;" (even inside URLs!). Be careful to end entity references with a semicolon or your entity reference may get interpreted in connection with the following text. Also keep in mind that named entity references are case-sensitive; &Aelig; and &aelig; are different characters. 

 If this error appears in some markup generated by PHP's session handling code, this article has explanations and solutions to your problem. 

 Note that in most documents, errors related to entity references will trigger up to 5 separate messages from the Validator. Usually these will all disappear when the original problem is fixed. 
 Line 46, Column 63: general entity "username" not defined and no default entity 
 …Vars" value="locale=en&room=rainbowzz&username=rainbowzz &accessHash=7ee0435ab9…

 &#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 71: reference not terminated by REFC delimiter 
 …lue="locale=en&room=rainbowzz&username=rainbowzz& accessHash=7ee0435ab9b123cd01…

 &#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 46, Column 71: reference to external entity in attribute value 
 …lue="locale=en&room=rainbowzz&username=rainbowzz& accessHash=7ee0435ab9b123cd01…

 &#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 46, Column 71: reference to entity "username" for which no system identifier could be generated 
 …lue="locale=en&room=rainbowzz&username=rainbowzz& accessHash=7ee0435ab9b123cd01…

 &#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 62: entity was defined here 
 …hVars" value="locale=en&room=rainbowzz&username=rainbowzz &accessHash=7ee0435ab…
 Line 46, Column 82: cannot generate system identifier for general entity "accessHash" 
 …=en&room=rainbowzz&username=rainbowzz&accessHash= 7ee0435ab9b123cd01bf6ac5b3ef1…

 &#9993; 

 An entity reference was found in the document, but there is no reference by that name defined. Often this is caused by misspelling the reference name, unencoded ampersands, or by leaving off the trailing semicolon (;). The most common cause of this error is unencoded ampersands in URLs as described by the WDG in "Ampersands in URLs". 

 Entity references start with an ampersand (&) and end with a semicolon (;). If you want to use a literal ampersand in your document you must encode it as "&amp;" (even inside URLs!). Be careful to end entity references with a semicolon or your entity reference may get interpreted in connection with the following text. Also keep in mind that named entity references are case-sensitive; &Aelig; and &aelig; are different characters. 

 If this error appears in some markup generated by PHP's session handling code, this article has explanations and solutions to your problem. 

 Note that in most documents, errors related to entity references will trigger up to 5 separate messages from the Validator. Usually these will all disappear when the original problem is fixed. 
 Line 46, Column 82: general entity "accessHash" not defined and no default entity 
 …=en&room=rainbowzz&username=rainbowzz&accessHash= 7ee0435ab9b123cd01bf6ac5b3ef1…

 &#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 92: reference not terminated by REFC delimiter 
 …om=rainbowzz&username=rainbowzz&accessHash=7ee043 5ab9b123cd01bf6ac5b3ef17dc" />

 &#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 46, Column 92: reference to external entity in attribute value 
 …om=rainbowzz&username=rainbowzz&accessHash=7ee043 5ab9b123cd01bf6ac5b3ef17dc" />

 &#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 46, Column 92: reference to entity "accessHash" for which no system identifier could be generated 
 …om=rainbowzz&username=rainbowzz&accessHash=7ee043 5ab9b123cd01bf6ac5b3ef17dc" />

 &#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 81: entity was defined here 
 …e=en&room=rainbowzz&username=rainbowzz&accessHash =7ee0435ab9b123cd01bf6ac5b3ef…
 Line 47, Column 18: there is no attribute "src" 
 <embed src="/client/Cam4_4.3.0.swf" quality="high" bgcolor="#ffffff"

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 47, Column 51: there is no attribute "quality" 
 <embed src="/client/Cam4_4.3.0.swf" quality="high" bgcolor="#ffffff"

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 47, Column 66: there is no attribute "bgcolor" 
 <embed src="/client/Cam4_4.3.0.swf" quality="high" bgcolor="#ffffff"

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 48, Column 17: there is no attribute "width" 
 width="100%" height="440" name="Cam4VChat" align="middle"

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 48, Column 31: there is no attribute "height" 
 width="100%" height="440" name="Cam4VChat" align="middle"

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 48, Column 42: there is no attribute "name" 
 width="100%" height="440" name="Cam4VChat" align="middle"

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 48, Column 60: there is no attribute "align" 
 width="100%" height="440" name="Cam4VChat" align="middle"

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 49, Column 16: there is no attribute "play" 
 play="true"

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 50, Column 16: there is no attribute "loop" 
 loop="false"

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 51, Column 19: duplicate specification of attribute "quality" 
 quality="high"

 &#9993; 

 You have specified an attribute more than once. Example: Using the "height" attribute twice on the same "img" tag. 
 Line 52, Column 17: there is no attribute "wmode" 
 wmode="opaque"

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 53, Column 21: there is no attribute "FlashVars" 
 FlashVars="locale=en&room=rainbowzz&username=rainb owzz&accessHash=7ee…

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 53, Column 36: reference not terminated by REFC delimiter 
 FlashVars="locale=en&room=rainbowzz&username=rainb owzz&accessHash=7ee…

 &#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 53, Column 36: reference to external entity in attribute value 
 FlashVars="locale=en&room=rainbowzz&username=rainb owzz&accessHash=7ee…

 &#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 53, Column 36: reference to entity "room" for which no system identifier could be generated 
 FlashVars="locale=en&room=rainbowzz&username=rainb owzz&accessHash=7ee…

 &#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 47: entity was defined here 
 …aram name="FlashVars" value="locale=en&room=rainbowzz&username=rainbowzz &acces…
 Line 53, Column 55: reference not terminated by REFC delimiter 
 …ars="locale=en&room=rainbowzz&username=rainbowzz& accessHash=7ee0435ab9b123cd01…

 &#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 53, Column 55: reference to external entity in attribute value 
 …ars="locale=en&room=rainbowzz&username=rainbowzz& accessHash=7ee0435ab9b123cd01…

 &#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 53, Column 55: reference to entity "username" for which no system identifier could be generated 
 …ars="locale=en&room=rainbowzz&username=rainbowzz& accessHash=7ee0435ab9b123cd01…

 &#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 62: entity was defined here 
 …hVars" value="locale=en&room=rainbowzz&username=rainbowzz &accessHash=7ee0435ab…
 Line 53, Column 76: reference not terminated by REFC delimiter 
 …&room=rainbowzz&username=rainbowzz&accessHash=7ee 0435ab9b123cd01bf6ac5b3ef17dc"

 &#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 53, Column 76: reference to external entity in attribute value 
 …&room=rainbowzz&username=rainbowzz&accessHash=7ee 0435ab9b123cd01bf6ac5b3ef17dc"

 &#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 53, Column 76: reference to entity "accessHash" for which no system identifier could be generated 
 …&room=rainbowzz&username=rainbowzz&accessHash=7ee 0435ab9b123cd01bf6ac5b3ef17dc"

 &#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 46, Column 81: entity was defined here 
 …e=en&room=rainbowzz&username=rainbowzz&accessHash =7ee0435ab9b123cd01bf6ac5b3ef…
 Line 54, Column 27: there is no attribute "allowFullScreen" 
 allowFullScreen="true"

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 55, Column 29: there is no attribute "allowScriptAccess" 
 allowScriptAccess="always"

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 56, Column 16: there is no attribute "type" 
 type="application/x-shockwave-flash"

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 57, Column 23: there is no attribute "pluginspage" 
 pluginspage="http://www.adobe.com/go/getflashplayer">

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 57, Column 63: element "embed" undefined 
 pluginspage="http://www.adobe.com/go/getflashplayer">

 &#9993; 

 You have used the element named above in your document, but the document type you are using does not define an element of that name. This error is often caused by: 
 incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Frameset" document type to get the "<frameset>" element),
 by using vendor proprietary extensions such as "<spacer>" or "<marquee>" (this is usually fixed by using CSS to achieve the desired effect instead).
 by using upper-case tags in XHTML (in XHTML attributes and elements must be all lower-case).
 Line 81, Column 210: end tag for "br" omitted, but OMITTAG NO was specified 
 …>MANAGE YOUR PRIVACY FEATURES</h1><br>You can set your cam show to private mod…

 &#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 81, Column 206: start tag was here 
 …><h1>MANAGE YOUR PRIVACY FEATURES</h1><br>You can set your cam show to private…
 Line 82, Column 215: end tag for "br" omitted, but OMITTAG NO was specified 
 …CT VIEWERS FOR A PRIVATE SHOW</h1><br>Would you like to have a private or excl…

 &#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 82, Column 211: start tag was here 
 …SELECT VIEWERS FOR A PRIVATE SHOW</h1><br>Would you like to have a private or …
 Line 83, Column 211: end tag for "br" omitted, but OMITTAG NO was specified 
 …HOW TO WATCH MULTIPLE WEBCAMS</h1><br>As a Gold Member, you may watch multiple…

 &#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 83, Column 207: start tag was here 
 …<h1>HOW TO WATCH MULTIPLE WEBCAMS</h1><br>As a Gold Member, you may watch mult…
 Line 84, Column 229: end tag for "select" which is not finished 
 …sage to <select id="roomList"></select></h1><br><textarea style="width:790px;h…

 &#9993; 

 Most likely, you nested tags and closed them in the wrong order. For example <p><em>...</p> is not acceptable, as <em> must be closed before <p>. Acceptable nesting is: <p><em>...</em></p> 

 Another possibility is that you used an element which requires a child element that you did not include. Hence the parent element is "not finished", not complete. For instance, in HTML the <head> element must contain a <title> child element, lists require appropriate list items (<ul> and <ol> require <li>; <dl> requires <dt> and <dd>), and so on. 
 Line 84, Column 239: end tag for "br" omitted, but OMITTAG NO was specified 
 …elect id="roomList"></select></h1><br><textarea style="width:790px;height:100p…

 &#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 84, Column 235: start tag was here 
 …o <select id="roomList"></select></h1><br><textarea style="width:790px;height:…
 Line 84, Column 305: required attribute "rows" not specified 
 …;height:100px" id="privateMessageText"></textarea><br><input type="submit" val…

 &#9993; 

 The attribute given above is required for an element that you've used, but you have omitted it. For instance, in most HTML and XHTML document types the "type" attribute is required on the "script" element and the "alt" attribute is required for the "img" element. 

 Typical values for type are type="text/css" for <style> and type="text/javascript" for <script>. 
 Line 84, Column 305: required attribute "cols" not specified 
 …;height:100px" id="privateMessageText"></textarea><br><input type="submit" val…

 &#9993; 

 The attribute given above is required for an element that you've used, but you have omitted it. For instance, in most HTML and XHTML document types the "type" attribute is required on the "script" element and the "alt" attribute is required for the "img" element. 

 Typical values for type are type="text/css" for <style> and type="text/javascript" for <script>. 
 Line 84, Column 321: end tag for "br" omitted, but OMITTAG NO was specified 
 …d="privateMessageText"></textarea><br><input type="submit" value="Send" align=…

 &#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 84, Column 317: start tag was here 
 …x" id="privateMessageText"></textarea><br><input type="submit" value="Send" al…
 Line 84, Column 361: there is no attribute "align" 
 …nput type="submit" value="Send" align="right" onclick="sendPrivateMessage();">…

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 84, Column 406: end tag for "input" omitted, but OMITTAG NO was specified 
 …submit" value="Send" align="right" onclick="sendPrivateMessage();"></div></div>

 &#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 84, Column 321: start tag was here 
 …d="privateMessageText"></textarea><br><input type="submit" value="Send" align=…
 Line 85, Column 218: end tag for "br" omitted, but OMITTAG NO was specified 
 … WEBCAM SHOWS IN FULL SCREEN!</h1><br>Would you like to get a little closer to…

 &#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 85, Column 214: start tag was here 
 …ATCH WEBCAM SHOWS IN FULL SCREEN!</h1><br>Would you like to get a little close…
 Line 85, Column 335: end tag for "br" omitted, but OMITTAG NO was specified 
 …screen with a Cam4Gold membership.<br><br>CAM4Gold is available for as little …

 &#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 85, Column 331: start tag was here 
 …ull screen with a Cam4Gold membership.<br><br>CAM4Gold is available for as lit…
 Line 85, Column 339: end tag for "br" omitted, but OMITTAG NO was specified 
 …en with a Cam4Gold membership.<br><br>CAM4Gold is available for as little as $…

 &#9993; 

 You may have neglected to close an element, or perhaps you meant to "self-close" an element, that is, ending it with "/>" instead of ">". 
 Line 85, Column 335: start tag was here 
 …screen with a Cam4Gold membership.<br><br>CAM4Gold is available for as little …
 Line 86, Column 1127: there is no attribute "id" 
 …></div><div class="avatar"><iframe id="avatarFrame" frameborder="0" width="278…

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 86, Column 1153: there is no attribute "frameborder" 
 …><iframe id="avatarFrame" frameborder="0" width="278" height="190" scrolling=…

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 86, Column 1163: there is no attribute "width" 
 …d="avatarFrame" frameborder="0" width="278" height="190" scrolling="no" src="…

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 86, Column 1176: there is no attribute "height" 
 …e" frameborder="0" width="278" height="190" scrolling="no" src="/profiles/ava…

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 86, Column 1193: there is no attribute "scrolling" 
 …" width="278" height="190" scrolling="no" src="/profiles/avatarUpload.jsp"></…

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 86, Column 1202: there is no attribute "src" 
 …278" height="190" scrolling="no" src="/profiles/avatarUpload.jsp"></iframe></…

 &#9993; 

 You have used the attribute named above in your document, but the document type you are using does not support that attribute for this element. This error is often caused by incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Transitional" document type to get the "target" attribute), or by using vendor proprietary extensions such as "marginheight" (this is usually fixed by using CSS to achieve the desired effect instead). 

 This error may also result if the element itself is not supported in the document type you are using, as an undefined element will have no supported attributes; in this case, see the element-undefined error message for further information. 

 How to fix: check the spelling and case of the element and attribute, (Remember XHTML is all lower-case) and/or check that they are both allowed in the chosen document type, and/or use CSS instead of this attribute. If you received this error when using the <embed> element to incorporate flash media in a Web page, see the FAQ item on valid flash. 
 Line 86, Column 1230: element "iframe" undefined 
 …="no" src="/profiles/avatarUpload.jsp"></iframe></div><div class="abuse"><h1>A…

 &#9993; 

 You have used the element named above in your document, but the document type you are using does not define an element of that name. This error is often caused by: 
 incorrect use of the "Strict" document type with a document that uses frames (e.g. you must use the "Frameset" document type to get the "<frameset>" element),
 by using vendor proprietary extensions such as "<spacer>" or "<marquee>" (this is usually fixed by using CSS to achieve the desired effect instead).
 by using upper-case tags in XHTML (in XHTML attributes and elements must be all lower-case).
 Line 86, Column 1482: end tag for "select" which is not finished 
 …me="userBlist" id="userBlist"></select></div><div class="buttonWrap"><a onclic…

 &#9993; 

 Most likely, you nested tags and closed them in the wrong order. For example <p><em>...</p> is not acceptable, as <em> must be closed before <p>. Acceptable nesting is: <p><em>...</em></p> 

 Another possibility is that you used an element which requires a child element that you did not include. Hence the parent element is "not finished", not complete. For instance, in HTML the <head> element must contain a <title> child element, lists require appropriate list items (<ul> and <ol> require <li>; <dl> requires <dt> and <dd>), and so on. 
 Line 87, Column 397: cannot generate system identifier for general entity "key" 
 …r/reporting/lboard.php?user_id='+uN+'&key='+kN+'&lang='+lang+' &session_id='+ti…

 &#9993; 

 An entity reference was found in the document, but there is no reference by that name defined. Often this is caused by misspelling the reference name, unencoded ampersands, or by leaving off the trailing semicolon (;). The most common cause of this error is unencoded ampersands in URLs as described by the WDG in "Ampersands in URLs". 

 Entity references start with an ampersand (&) and end with a semicolon (;). If you want to use a literal ampersand in your document you must encode it as "&amp;" (even inside URLs!). Be careful to end entity references with a semicolon or your entity reference may get interpreted in connection with the following text. Also keep in mind that named entity references are case-sensitive; &Aelig; and &aelig; are different characters. 

 If this error appears in some markup generated by PHP's session handling code, this article has explanations and solutions to your problem. 

 Note that in most documents, errors related to entity references will trigger up to 5 separate messages from the Validator. Usually these will all disappear when the original problem is fixed. 
 Line 87, Column 397: general entity "key" not defined and no default entity 
 …r/reporting/lboard.php?user_id='+uN+'&key='+kN+'&lang='+lang+' &session_id='+ti…

 &#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 87, Column 400: reference not terminated by REFC delimiter 
 …eporting/lboard.php?user_id='+uN+'&key='+kN+'&lang='+lang+' &session_id='+tippi…

 &#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 87, Column 400: reference to external entity in attribute value 
 …eporting/lboard.php?user_id='+uN+'&key='+kN+'&lang='+lang+' &session_id='+tippi…

 &#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 87, Column 400: reference to entity "key" for which no system identifier could be generated 
 …eporting/lboard.php?user_id='+uN+'&key='+kN+'&lang='+lang+' &session_id='+tippi…

 &#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 87, Column 396: entity was defined here 
 …er/reporting/lboard.php?user_id='+uN+'&key='+kN+'&lang='+lang+' &session_id='+t…
 Line 87, Column 412: reference not terminated by REFC delimiter 
 …ard.php?user_id='+uN+'&key='+kN+'&lang='+lang+'&s ession_id='+tipping.sID,'lead…

 &#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 87, Column 422: cannot generate system identifier for general entity "session_id" 
 …er_id='+uN+'&key='+kN+'&lang='+lang+'&session_id= '+tipping.sID,'leaderboard','…

 &#9993; 

 An entity reference was found in the document, but there is no reference by that name defined. Often this is caused by misspelling the reference name, unencoded ampersands, or by leaving off the trailing semicolon (;). The most common cause of this error is unencoded ampersands in URLs as described by the WDG in "Ampersands in URLs". 

 Entity references start with an ampersand (&) and end with a semicolon (;). If you want to use a literal ampersand in your document you must encode it as "&amp;" (even inside URLs!). Be careful to end entity references with a semicolon or your entity reference may get interpreted in connection with the following text. Also keep in mind that named entity references are case-sensitive; &Aelig; and &aelig; are different characters. 

 If this error appears in some markup generated by PHP's session handling code, this article has explanations and solutions to your problem. 

 Note that in most documents, errors related to entity references will trigger up to 5 separate messages from the Validator. Usually these will all disappear when the original problem is fixed. 
 Line 87, Column 422: general entity "session_id" not defined and no default entity 
 …er_id='+uN+'&key='+kN+'&lang='+lang+'&session_id= '+tipping.sID,'leaderboard','…

 &#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 87, Column 432: reference not terminated by REFC delimiter 
 …+'&key='+kN+'&lang='+lang+'&session_id='+tipping. sID,'leaderboard','width=700,…

 &#9993; 

 If you meant to include an entity that starts with "&", then you should terminate it with ";". Another reason for this error message is that you inadvertently created an entity by failing to escape an "&" character just before this text. 
 Line 87, Column 432: reference to external entity in attribute value 
 …+'&key='+kN+'&lang='+lang+'&session_id='+tipping. sID,'leaderboard','width=700,…

 &#9993; 

 This is generally the sign of an ampersand that was not properly escaped for inclusion in an attribute, in a href for example. You will need to escape all instances of '&' into '&amp;'. 
 Line 87, Column 432: reference to entity "session_id" for which no system identifier could be generated 
 …+'&key='+kN+'&lang='+lang+'&session_id='+tipping. sID,'leaderboard','width=700,…

 &#9993; 

 This is usually a cascading error caused by a an undefined entity reference or use of an unencoded ampersand (&) in an URL or body text. See the previous message for further details. 
 Line 87, Column 421: entity was defined here 
 …ser_id='+uN+'&key='+kN+'&lang='+lang+'&session_id ='+tipping.sID,'leaderboard',
```


sorry. I couldn't find a button in the edit window that had a hash - it seems the edit function post window doesn't have that capability. But thats it there :) :KS

---

### Post by audiomick on 2012-02-24
> **FrustratedRainbowzz said:**
> 
sorry. I couldn't find a button in the edit window that had a hash ..

Ooops, I forgot. Here, you have to select "go advanced" in the edit window to get all the options.

---

### Post by HeroOfCanton on 2012-02-24
Know we already discussed this in PM's Rainbowzz but wanted to leave it here for others just in case:

Since the cam is operational and working on other sites it appears that the problem may be in the flash interpreter used by cam4 on the web server. There may not be a fix available from the user end.

Don't usually wish for this, but hopefully someone will chime in and prove me wrong. ;)

---

### Post by FrustratedRainbowzz on 2012-02-25
Thanks everyone! Still no luck on this, waiting to hear back again from cam4

---

### Post by Acker2012 on 2012-03-19
Hey Rainbowzz,
Followed your thread because I had the same problem. I could receive video fine
but broadcasting would not work on that site or another site I like.
Had the hourglass for awhile. Then kept trying
to get older flash versions. When flash came up to 'accept or deny' it would lock there.
Seriously considered dumping the Ubuntu install.
But I downloaded Opera and used global settings of flash which is done on their website
and set the options for the two websites camera access to 'always allow'.
Seems to have worked.
Also I updated network controller driver and PCI communication driver online which may
have something to do with managing USB devices which is what internal and ext.
cameras are anyway.

Good luck with it.

Acker

---

### Post by rencemc on 2012-10-28
Install Google Chrome - I tried it and you can broadcast on cam4.

---

