---
title: "BBC Video not playing"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-03-10
I use Ubuntu 11.10 I can play video from other websites but those at BBC website do not work. Not only in Firefox but they do not work in Opera also. Adobe website shows i have the latest flash plugin installed.
Can any one please help.

---

### Post by Frogs Hair on 2012-03-10
What site ? . The  iplayer videos are not available in the U.S.. I can only get radio here. I'm not sure if Quicktime is required , but I have it installed via Gsteamer Plug-ins from the software center.

---

### Post by 3dmatrix on 2012-03-10
It is supposed to work in the browser. That is what it does in all other distros. It even worked in my previous Ubuntu install but is not working in 11.10 It has nothing to do with geographiocal location.

[http://www.bbc.co.uk/news/video_and_audio/](http://www.bbc.co.uk/news/video_and_audio/)

I have tried suggestions at these links but nothing works :

[http://ubuntuforums.org/showthread.php?t=1196599](http://ubuntuforums.org/showthread.php?t=1196599)
[http://ubuntuforums.org/showthread.php?t=1612190](http://ubuntuforums.org/showthread.php?t=1612190)


.

---

### Post by sammiev on 2012-03-10
Tried a few of then now and they all worked. Can you please post the addie of the one.

---

### Post by Frogs Hair on 2012-03-10
That site works fine in Opera . The site I was writing about is this one and TV is not available in the U.S. [http://www.bbc.co.uk/iplayer/radio](http://www.bbc.co.uk/iplayer/radio)

---

### Post by 3dmatrix on 2012-03-11
Do you mean Addons ?
I do not think Addons have much to do here as I am not able to access it from any browser.

---

### Post by ron999 on 2012-03-11
> **3dmatrix said:**
> 

[http://www.bbc.co.uk/news/video_and_audio/](http://www.bbc.co.uk/news/video_and_audio/)


Hi
That BBC website needs flash plugin.
Install it like this:-
```
sudo apt-get install flashplugin-installer
```

If you still have problems, look at this thread here ---> [http://ubuntuforums.org/showthread.php?t=1491268]("http://ubuntuforums.org/showthread.php?t=1491268")

---

### Post by sammiev on 2012-03-11
> **Frogs Hair said:**
> That site works fine in Opera . The site I was writing about is this one and TV is not available in the U.S. [http://www.bbc.co.uk/iplayer/radio](http://www.bbc.co.uk/iplayer/radio)

It worked for me after I changed my VPN over to the UK.

---

### Post by Frogs Hair on 2012-03-11
> **3dmatrix said:**
> Do you mean Addons ?
I do not think Addons have much to do here as I am not able to access it from any browser.


You should only need flash as ron999 wrote for the site you are trying to use . I meant media codecs/ plugins which can be installed from the software center .

---

### Post by 3dmatrix on 2012-03-11
I already mentioned :
"**I can play video from other websites** but those at BBC website do not work. Not only in Firefox but they do not work in Opera also. **Adobe website shows i have the latest flash plugin installed**."

* I have Adobe flash installed
* I can watch flash / streaming videos on all other websites
* The problem is with all Browsers
* Earlier I could access BBC videos with earlier versions of Ubuntu
* I have accessed BBC Video many times outside UK

So the problem is somewhere else. There are many others who face the same problem. Check the links already provided :

[http://ubuntuforums.org/showthread.php?t=1196599](http://ubuntuforums.org/showthread.php?t=1196599)
[http://ubuntuforums.org/showthread.php?t=1612190](http://ubuntuforums.org/showthread.php?t=1612190)

---

### Post by Frogs Hair on 2012-03-11
The site works in Firefox and Opera on 11.10 . I don't know why it is  being blocked. I did have to allow scripts in both browsers to watch video because otherwise I get a message telling me to install Flash. I use NoScript in Firefox and NotSripts in Opera. This is not applicable if you are not using browser add-ons.

---

### Post by 3dmatrix on 2012-03-11
I do use No Script in FF but i do not use any such addon in Opera. Moreover, I also tried to put my firewall off and then try accessing it but it didnt work.

One guy in those links wrote that he had to unblock adblocker. So there must be some other reason.

I feel it is more related to network issue than plugin / addon.

One of them wrote, he cud not access on Ubuntu but do so on Mint  :)

---

### Post by Frogs Hair on 2012-03-11
Of the the plug-ins listed at this link I have Flash and Quicktime .[http://www.bbc.co.uk/webwise/guides/what-plugins-do-i-need](http://www.bbc.co.uk/webwise/guides/what-plugins-do-i-need)

All my plug-ins except Flash 64 bit  witch I install via Flash Aid  are in the screen shot .  I don't think you need them but I don't what else to offer at the moment . I thought it may be an ISP problem but if only the Ubuntu version has changed that wouldn't  apply.

---

### Post by 3dmatrix on 2012-03-12
On right clicking, the menu offers an error report :

[COLOR="Red"]EMP v.3.0.0.r617329_617319
 Playlist URL : [http://playlists.bbc.co.uk/news/business-17335620A/playlist.sxml](http://playlists.bbc.co.uk/news/business-17335620A/playlist.sxml)
 [B]Error code : CDNRedundancyManagerError [0] : 
null[/B][/COLOR]

Can this provide any clue about the possible problem ?

---

### Post by Frogs Hair on 2012-03-12
This problem is not limited to Ubuntu.

[http://www.techyv.com/questions/fix-cdn-redundancy-manager-error-null](http://www.techyv.com/questions/fix-cdn-redundancy-manager-error-null)

[http://support.unblock-us.com/customer/portal/questions/124255-watching-bbc-one-live-not-working](http://support.unblock-us.com/customer/portal/questions/124255-watching-bbc-one-live-not-working)

[http://comments.gmane.org/gmane.linux.ubuntu.user/244077](http://comments.gmane.org/gmane.linux.ubuntu.user/244077)

---

### Post by 3dmatrix on 2012-05-14
Recently noticed the flash plugin reporting the error as :

VE_FMS_CONNECT_FAILED

[http://www.bbc.co.uk/news/video_and_audio/](http://www.bbc.co.uk/news/video_and_audio/)

EMP v.3.1.0.r749603_749269_749444_3
 Playlist URL : [http://playlists.bbc.co.uk/news/10462520A/playlist.sxml](http://playlists.bbc.co.uk/news/10462520A/playlist.sxml)
 Error code : CDNRedundancyManagerError [0] : 
null

---

### Post by CaptainJamie on 2012-05-14
You could install get-iplayer and use that if you need to watch something in the mean time. I hardly ever stream from the BBC iPlayer website anymore. There are instructions on [my website]("http://captainjamie.byethost12.com/bbciplayer/") on how to download using it. Sorry if the tutorial is a little basic, I write them for my parents really.

---

