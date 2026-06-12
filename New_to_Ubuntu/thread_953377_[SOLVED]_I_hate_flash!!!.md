---
title: "[SOLVED] I hate flash!!!"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by eternalnewbee on 2008-10-20
Two weeks ago I had a problem with flash. There was no sound when playing videos from youtube. Iaculallad solved that for by advising to sudo libflash...
Perfect! And now, out of the blue I get the following message when trying to view a video:
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.
What happened?

---

### Post by northern lights on 2008-10-20
Are you using gnash or flashplugin-nonfree?

The latter, though closed source, does yield better results.

---

### Post by eternalnewbee on 2008-10-20
> **northern lights said:**
> Are you using gnash or flashplugin-nonfree?

The latter, though closed source, does yield better results.

I think gnash...
How do I find out though?

---

### Post by WRDN on 2008-10-20
> **eternalnewbee said:**
> I think gnash...
How do I find out though?

In the address bar in Firefox, type:

```
about:plugins
```

This will tell you what is installed. You could also look to see what is installed in Synaptic.

---

### Post by northern lights on 2008-10-20
> **eternalnewbee said:**
> I think gnash...
How do I find out though?
Via the above or by running ```
aptitude search flashplugin-nonfree
```
and checking whether it's got an "i" flag. Anyhow, should it be installed apt-get will just ignore you trying to install it, so we might as well just give it a go.

Run```
sudo apt-get update && sudo apt-get autoremove totem-mozilla && sudo apt-get install mozilla-mplayer flashplugin-nonfree
```Most likely, that's going to improve your situation noticeably.

If you want to have wma/wmv support as well, you have to enable the medibuntu repositories. They yield DVD support as well. Check [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by eternalnewbee on 2008-10-20
> **WRDN said:**
> In the address bar in Firefox, type:

```
about:plugins
```

This will tell you what is installed. You could also look to see what is installed in Synaptic.

This was the outcome:

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

What do I do next?

---

### Post by philinux on 2008-10-20
> **eternalnewbee said:**
> Two weeks ago I had a problem with flash. There was no sound when playing videos from youtube. Iaculallad solved that for by advising to sudo libflash...
Perfect! And now, out of the blue I get the following message when trying to view a video:
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.
What happened?

If you have flash 10 then some sites have not update there recognition. They see 10 as less than 9 and think you've not got the latest installed. They will all catch up pretty fast now that 10 final is out.

---

### Post by northern lights on 2008-10-20
This is the nonfree/proprietary plugin.

It would still be useful to run the above, without the *flashplugin-nonfree* installation to replace *totem-mozilla* by *mozilla-mplayer*, which tends to handle youtube and the like better.

```
sudo apt-get update && sudo apt-get autoremove totem-mozilla && sudo apt-get install mozilla-mplayer
```

---

### Post by northern lights on 2008-10-20
> **philinux said:**
> If you have flash 10 [...]

> **eternalnewbee said:**
> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
That can't be it here...

---

### Post by llebegue on 2008-10-20
Do you use NoScript firefox extension ... If you do that would lead to this behavior. Make sure to accept the web site you want to view.

---

### Post by eternalnewbee on 2008-10-20
> **llebegue said:**
> Do you use NoScript firefox extension ... If you do that would lead to this behavior. Make sure to accept the web site you want to view.

I don't use Noscript.

---

### Post by rebaccawood911 on 2008-10-20
sorry dear i don't use flash & no idea about that..:lolflag:

---

### Post by eternalnewbee on 2008-10-20
> **northern lights said:**
> Via the above or by running ```
aptitude search flashplugin-nonfree
```
and checking whether it's got an "i" flag. Anyhow, should it be installed apt-get will just ignore you trying to install it, so we might as well just give it a go.

Run```
sudo apt-get update && sudo apt-get autoremove totem-mozilla && sudo apt-get install mozilla-mplayer flashplugin-nonfree
```Most likely, that's going to improve your situation noticeably.

If you want to have wma/wmv support as well, you have to enable the medibuntu repositories. They yield DVD support as well. Check [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

I followed this advice.
Still the same massage from youtube. I'm going to reboot the system and see if it worked.

---

### Post by eternalnewbee on 2008-10-20
> **rebaccawood911 said:**
> sorry dear i don't use flash & no idea about that..:lolflag:

Why, thank you dear. Don't worry about it. This will be solved. No doubt.

---

### Post by eternalnewbee on 2008-10-20
> **northern lights said:**
> Via the above or by running ```
aptitude search flashplugin-nonfree
```
and checking whether it's got an "i" flag. Anyhow, should it be installed apt-get will just ignore you trying to install it, so we might as well just give it a go.

Run```
sudo apt-get update && sudo apt-get autoremove totem-mozilla && sudo apt-get install mozilla-mplayer flashplugin-nonfree
```Most likely, that's going to improve your situation noticeably.

If you want to have wma/wmv support as well, you have to enable the medibuntu repositories. They yield DVD support as well. Check [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
OK. That didn't work.
My motto is: "Patience is a virtue"
So bear with me... What's next?

---

### Post by eternalnewbee on 2008-10-20
Any solutions?

---

### Post by billgoldberg on 2008-10-20
> **eternalnewbee said:**
> Two weeks ago I had a problem with flash. There was no sound when playing videos from youtube. Iaculallad solved that for by advising to sudo libflash...
Perfect! And now, out of the blue I get the following message when trying to view a video:
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.
What happened?

You could install the latest flash player from the adobe website.

Flash player 10 comes as a .deb package. Just double click to install.

First remove flash from your system before install Flash player 10.

Use this command:

```
sudo apt-get remove libflash-mozplugin libflashsupport flashplugin-nonfree
```

And in the /home/username/.mozilla/plugins folder, remove libflashplayer.so

Then install the .deb

---

### Post by eternalnewbee on 2008-10-20
OK, it's working again. The strangething is it didn't work after I rebooted the first, but I just rebooted again and what do you know? It works. Thanks to everybody who helped out.

---

### Post by razer22 on 2008-10-24
hi i have the same how do you reboot the system.thanks from a noob:)

---

### Post by eternalnewbee on 2008-10-25
Reboot = Restart

---

### Post by razer22 on 2008-10-25
ohh!!! thanks:redface:

---

### Post by eternalnewbee on 2008-10-25
You're welcome.

---

