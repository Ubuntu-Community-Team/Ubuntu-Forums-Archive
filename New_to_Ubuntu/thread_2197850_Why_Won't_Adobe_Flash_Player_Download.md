---
title: "Why Won't Adobe Flash Player Download?"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by TomBrooklyn on 2014-01-05
Might there be any particular reason why I can't get the Adobe Flash Player v.11.2 for Linux from the  Adobe website?


Speaking of downloads, how can I set where Firefox saves downloads?    There is no option for that in Firefox/Tools/Downloads.


Also speaking of downloads, I ran sudo apt-get update and seemingly got a big list of updates from ubuntu.    I don't know where the files downloaded to, and I wonder if they auto-installed and cleaned themselves up, deleting any no longer needed files, etc.

---

### Post by flyfisherbryan on 2014-01-05
Not sure about Adobe, having trouble with that myself.  But I know FireFox is a little different in Ubuntu.  Instead of Tools, click Edit then Preferences.  There you will find the familiar multi-tabbed menu for your FireFox settings.  Download destintion is on the first tab marked General.

---

### Post by mc4man on 2014-01-05
Because they don't actually ofter packages from there anymore. If you want flash then install - 
flashplugin-installer

---

### Post by deadflowr on 2014-01-05
> **mc4man said:**
> Because they don't actually ofter packages from there anymore. If you want flash then install - 
flashplugin-installer
The salad days truly are over, huh?

> **TomBrooklyn said:**
> 
Also speaking of downloads, I ran sudo apt-get update and seemingly got a big list of updates from ubuntu.    I con't know where the files downloaded to, and I wonder if they auto-installed and cleaned themselves up, deleting any no longer needed files, etc.
Running sudo apt-get update doesn't actually download much more than a list of the latest packages available.
To download and install you need to run
```
sudo apt-get upgrade
```
It'll cache the downloaded files in /var/cache/apt/archives.
You clean it by running
```
sudo apt-get clean
```

---

### Post by zemega on 2014-01-06
And sometimes, the server that house the flashplugin-installer becomes really busy that the apt-get process connection times out. I had a day like that, which forces me to get the file through download manager, needless to say I downloaded the file aggressively, and do manual installation.

---

### Post by TomBrooklyn on 2014-01-06
> **mc4man said:**
>  install - flashplugin-installer I found the page for it here:
[http://packages.ubuntu.com/lucid/flashplugin-installer](http://packages.ubuntu.com/lucid/flashplugin-installer)

but what do I install?     Where is the correct download link?

Should I install the source?

near the page bottom are links to get it for AMD64 or i356.      I'm using neither of them, unless an Intell Core 2 Duo processor counts as an i386. 


And, out of curiousity, why does ubuntu make such a basic task as downloading flash so obscure, complex, and difficult?

---

### Post by Bucky Ball on 2014-01-06
Just open Software Centre or Synaptics, search for and install flashplugin-installer.

---

### Post by deadflowr on 2014-01-06
Either use the suggested, and easy way, of opening the software center and install it from there.
Or run
```
sudo apt-get install flashplugin-installer
```
It's that simple.
Either method will download and install the correct arch-type for your machine.

---

### Post by Bucky Ball on 2014-01-06
> **deadflowr said:**
> Either use the suggested, and easy way, of opening the software center and install it from there.
Or run
```
sudo apt-get install flashplugin-installer
```
It's that simple.
Either method will download and install the correct arch-type for your machine.

+1.

---

### Post by deadflowr on 2014-01-06
> **TomBrooklyn said:**
> 
And, out of curiousity, why does ubuntu make such a basic task as downloading flash so obscure, complex, and difficult?

Adobe did that.
Ubuntu can only make do with what tools they are allowed.

---

### Post by sotiris2 on 2014-01-06
Actually it is not obscure , Ubuntu Software Center is the intended way to download software for Ubuntu , especially for new users. If you search for flash there it is the very first result complete with actual flash icon. It's also not complex , you just click install put in your password and it does download and install automatically.

  The main downside is that it does not include all of ubuntu compatible software or the very latest versions (though every software in it is tested to work with your ubuntu version). So if you need to download some program for ubuntu I would suggest you check there first.

---

### Post by Yellow Pasque on 2014-01-06
> **TomBrooklyn said:**
> Why does ubuntu make such a basic task as downloading flash so obscure, complex, and difficult?

It's not difficult at all. You're just used to doing it the Windows way. Notice that Flash isn't available in Windows Update either... Yes, it's easier to download it straight from Adobe's site on Windows, but it's also really easy to end up with Google Chrome installed as your default browser if you're not careful.

Besides, it's not Debian/Ubuntu's fault they can't distribute Flash in the repos. Adobe's licensing forbids it. (They don't want bogus malware versions floating around. They want to shove the EULA down every end user's throat to cover their legal backsides, etc.)

---

