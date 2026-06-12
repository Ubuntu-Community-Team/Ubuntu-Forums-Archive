---
title: "Constant error messages but unable to send error report"
date: 2014-07-03
forum: New to Ubuntu
---

### Post by dtlongrifles on 2014-07-03
Since installing Ubuntu 12.04 LTS I get a system error message, then a message asking me to send an error report when I turn on my Laptop. I try to send the error report but I get a message saying that the report can't be sent so I close it out and immediately get the same error message asking me to send an error report. I can go through this cycle countless times and still can't ever send the error report so now I just close these messages down as fast they pop up and after a minute or so they go away and I can use the Laptop. After a few hours it will happen again, or if I am doing multiple tasks such as listening to Rhythmbox while downloading and scanning Facebook. Also if I'm on the internet and start getting these error messages, Shockwave will crash and I get those "Aw snap" messages. It would be nice if this problem could be resolved. I like Ubuntu and I don't ever want to use Windows again.

---

### Post by ubudog on 2014-07-03
Those errors may be old, and apport just keeps showing them, so you can try this:
```
sudo mv /var/crash /var/crashold
```

Apport should then just report new errors.

---

### Post by dtlongrifles on 2014-07-04
Thank you. That seems to have worked with the constant error message but I'm still getting the "Aw, Snap" message frequently when I'm on the net. When I click for more info I think it gives info for Windows users such as reboot and make sure anti-virus is up to date. I thought Linux didn't get viruses.

---

### Post by ubudog on 2014-07-04
Is this in Chrome/Chromium?  Perhaps [this]("http://www.howtogeek.com/103292/how-to-fix-shockwave-flash-crashes-in-google-chrome/") will help.

And no, there are no Linux viruses in the wild, which doesn't mean that you can't install malware, it's just a lot harder in Linux than in Windows.

---

### Post by dtlongrifles on 2014-07-06
I use Chromium and this is what it looked like when I checked plug-ins: 
[COLOR=#000000][FONT=Ubuntu]**Adobe Flash Player** - Version: 11.2 r202Shockwave Flash 11.2 r202
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu][TABLE]
[TR]
[TD="class: plugin-details-label"]Name:[/TD]
[TD]Shockwave Flash[/TD]
[/TR]
[/TABLE]

[TABLE]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Version:[/TD]
[TD]11.2 r202[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Location:[/TD]
[TD]/usr/lib/flashplugin-installer/libflashplayer.so[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Type:[/TD]
[TD]NPAPI[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"] [/TD]
[TD][Disable]("chrome://plugins/#")[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]MIME types:[/TD]
[TD][TABLE="class: mime-types, width: 100%"]
[TR="class: header"]
[TD]MIME type[/TD]
[TD]Description[/TD]
[TD]File extensions[/TD]
[/TR]
[TR]
[TD]application/x-shockwave-flash[/TD]
[TD]Shockwave Flash[/TD]
[TD][TABLE="class: hlisting"]
[TR]
[TD].swf[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD]application/futuresplash[/TD]
[TD]FutureSplash Player[/TD]
[TD][TABLE="class: hlisting"]
[TR]
[TD].spl


[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
It doesn't quite look like the example that was given.

---

### Post by claracc on 2014-07-06
Is your problem similar to the bug, here reported?: [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1256642](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1256642)

---

### Post by monkeybrain20122 on 2014-07-06
The internal error message is a bug from the error reporting thing, it is enabled for beta testing and should have been turned off at release. So to disable it 
```
gksudo gedit /etc/default/apport
```
and set enabled=0

Also your Chromium is obviously out of date as it no longer supports NPAPI plugins which include flash 11.2 since version 34.

---

### Post by dtlongrifles on 2014-07-10
> **monkeybrain20122 said:**
> 

Also your Chromium is obviously out of date as it no longer supports NPAPI plugins which include flash 11.2 since version 34.

I have [COLOR=#303942][FONT=Ubuntu]Version 34.0.1847.116 Ubuntu 12.04 (260972). I've never received a message that updates were available. So, I uninstalled Chromium and then re-installed it from the Ubuntu Software Center and I got the same version.[/FONT][/COLOR]

---

### Post by ubudog on 2014-07-10
Try using the Chromium PPA:
```
sudo add-apt-repository ppa:chromium-daily/stable
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by dtlongrifles on 2014-07-11
Thank you. The problems seem to have been resolved.

---

