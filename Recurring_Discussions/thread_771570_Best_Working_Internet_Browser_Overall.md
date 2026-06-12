---
title: "Best Working Internet Browser Overall??"
date: 2008-04-27
forum: Recurring Discussions
---

### Post by swimm3r137@gmail.com on 2008-04-27
Hi,

I don't think firefox beta is working that well, therefore I'm uninstalling it.(at least until firefox 3)  I'd like some suggestions of alternative browsers.  I did try opera in the past(like a year ago at least), it was quick, but I dropped it because it wasn't as compatible with sites as I liked it to be.  I realize if compatibility is what I'm searching for, IE or firefox is the way to go, but obviously, I'm looking to change.  Help!  =)  

Also, how do I uninstall firefox 3 beta COMPLETELY?  I tried in add/remove, but it said try synaptic.  Where do I find the firefox files I need to remove to be RID OF THIS BETA P.O.S!!??  Sorry, I'm a bit newbish to linux...

---

### Post by InfinityCircuit on 2008-04-27
I recommend just using Opera or going back to Firefox 2.0.0.x if you are not pleased with Firefox 3.  To completely remove firefox 3, open a terminal and type the following:

```
sudo apt-get remove --purge firefox-3.0
rm -rf ~/.mozilla
sudo apt-get install firefox
```

I don't know exactly what you are using so I can't say 100% what the correct names for the packages are.  Also, if you installed from a tarball the procedure is different.

---

### Post by hackle577 on 2008-04-27
Here's the correct code. This will take you back to Firefox 2:

```
sudo apt-get purge firefox
rm -r ~/.mozilla/firefox
sudo apt-get install firefox-2
```

InfinityCircuit's code will merely uninstall then reinstall Firefox 3.

---

### Post by PhoenixP3K on 2008-04-27
I will recommand **Opera** as well, but I've been working with their latest beta buil for version 9.5 and you should at least give it a quick try.
You can download the .deb and install it very easily (they've come some way if you tryed it last year)
[http://snapshot.opera.com/unix/snapshot-1929/intel-linux/opera_9.50-20080417.6-shared-qt_i386.deb](http://snapshot.opera.com/unix/snapshot-1929/intel-linux/opera_9.50-20080417.6-shared-qt_i386.deb)

Concerning the compatibility of certain sites, if you land on a page that tells you that you need Firefox or Internet explorer by pressing F12 you can go on Edit Site Preferences, then on the Network tab you'll have the option to MASK Opera as Firefox or Internet Explorer, use that to fool those websites.

If your installing Firefox 2, try looking for firefox-2 in the Synaptic Packet Manager (It's in System > Administration )

---

### Post by swimm3r137@gmail.com on 2008-04-27
what do you guys think about:
1) seamonkey
2) kazehakase


Also, since I already uninstalled firefox 3, i tried looking in both add/remove and synaptec for opera, but its nowhere!! lol, do I have to install firefox 2 again to download opera since it's not there or is there another way to get it without having a browser.  

incase you guys are wondering, im on another computer :)

---

### Post by madjr on 2008-04-27
> **swimm3r137@gmail.com said:**
> what do you guys think about:
1) seamonkey
2) kazehakase


Also, since I already uninstalled firefox 3, i tried looking in both add/remove and synaptec for opera, but its nowhere!! lol, do I have to install firefox 2 again to download opera since it's not there or is there another way to get it without having a browser.  

incase you guys are wondering, im on another computer :)

seamonkey and kazehakase

are good if you are low on resources. But you would need to try em yourself and see if you like them.

Anyway aside from plugins what issues u had with FF3?

if you use many flash websites then usually the browser is not the problem, but flash (see my sign).

FF2 is still a bit better than ff3 beta, so try using that or download the latest Opera at their website.

They have an Ubuntu installer (.deb)

---

### Post by warped0ne on 2008-04-27
You can get Opera in the Synaptic Package Manager.

Just open it and run a search for Opera.  The file is simply named opera and when you select it and click apply, it will download and install a library file as well.

Hope that helps.

---

### Post by swimm3r137@gmail.com on 2008-04-27
> **warped0ne said:**
> You can get Opera in the Synaptic Package Manager.

Just open it and run a search for Opera.  The file is simply named opera and when you select it and click apply, it will download and install a library file as well.

Hope that helps.

its not there.  i searched in synaptic, but its no where to be found =(  I dunno, I guess I'll try ff2...

---

### Post by miwaypet on 2008-04-27
Try Swift Weasel. FF add-ons are compatible. Works like standard FF, just select the one for your specific type processor.

---

### Post by warped0ne on 2008-04-27
> **swimm3r137@gmail.com said:**
> its not there.  i searched in synaptic, but its no where to be found =(  I dunno, I guess I'll try ff2...
You'll have to open the Software Sources application first and enable some things there... sorry, I enabled nearly everything in mine.  Then go back to the Synaptic Package Manager and run a search for Opera.  It'll return well over a hundred results, just left click on any of the package names and then type "opera"  Click the box, click Apply, and it will install.

---

### Post by ChameleonDave on 2008-04-27
> **swimm3r137@gmail.com said:**
> its not there.  i searched in synaptic, but its no where to be found =(  I dunno, I guess I'll try ff2...
Opera is not open source, so you have to enable some extra repositories if you want to get it.

---

### Post by swimm3r137@gmail.com on 2008-04-27
Honestly, ff2 is working flawlessly and it's super fast, unlike ff3.  I'll just stay with this until ff3 and see what that has to offer.

---

### Post by Solrac924 on 2008-04-27
The best overall Web Browser?
that's easy: **Opera**.
*fastest*: Opera 9 (in Linux) is the fastest with Script speed, Multiple images, History. Opera is also the fastest with Rendering.
*most secure*: Opera. There are no open vulnerabilities (no unpatched advisories) according to Secunia, a web security consultant.
*Features*: Opera. It comes fully loaded out of the box. It's also a e-mail client if you want. it can speak, even take voice commands. it has built-in notes, RSS, thumbnail preview, torrent, chat & best of all: widgets.
you asked for it, you got it.

---

### Post by swimm3r137@gmail.com on 2008-04-27
> **Solrac924 said:**
> The best overall Web Browser?
that's easy: **Opera**.
*fastest*: Opera 9 (in Linux) is the fastest with Script speed, Multiple images, History. Opera is also the fastest with Rendering.
*most secure*: Opera. There are no open vulnerabilities (no unpatched advisories) according to Secunia, a web security consultant.
*Features*: Opera. It comes fully loaded out of the box. It's also a e-mail client if you want. it can speak, even take voice commands. it has built-in notes, RSS, thumbnail preview, torrent, chat & best of all: widgets.
you asked for it, you got it.

let me ask you this.  Do you think I should get the stable release (9.27) or should I go with the beta (9.50b)?  The only reason I'm hesitant is because firefox's beta is ****, and beta means beta, hence there are bugs.  How important they are is another story...  Plus it's opera, not firefox, but then again, I'm a newbie to opera, so I have no idea if they would release such a terrible beta like firefox 3.

---

### Post by swimm3r137@gmail.com on 2008-04-27
;

---

### Post by ChameleonDave on 2008-04-28
I've tried the beta and non-beta version of Opera, and I can't get Flash to work properly with either.  I also get the occasional crash.  I've gone back to Firefox 3.

---

### Post by c4v3m4n on 2008-04-28
Swiftweasel is really good and so is swiftfox.  They're compatible with most firefox stuff too.

---

### Post by p_quarles on 2008-04-28
Moved to Recurring Discussions. 

My own opinion on the issue: I've used pretty much every browser available, and I think they all have pretty significant flaws, each in their own special way. I've settled on Konqueror, as it annoys me the least.

---

### Post by mrgnash on 2008-04-28
Firefox 3 is the best :D

---

### Post by quinnten83 on 2008-04-28
> **swimm3r137@gmail.com said:**
> its not there.  i searched in synaptic, but its no where to be found =(  I dunno, I guess I'll try ff2...

Are you selecting "all available applications" or something else in the dropdownlist in add/remove?

---

### Post by swimm3r137@gmail.com on 2008-04-28
> **quinnten83 said:**
> Are you selecting "all available applications" or something else in the dropdownlist in add/remove?

yes I am.  I've done it about 5 times already, and i'm sure it's not there.  Any ideas?

---

### Post by LaRoza on 2008-04-28
> **swimm3r137@gmail.com said:**
> let me ask you this.  Do you think I should get the stable release (9.27) or should I go with the beta (9.50b)?  The only reason I'm hesitant is because firefox's beta is ****, and beta means beta, hence there are bugs.  How important they are is another story...  Plus it's opera, not firefox, but then again, I'm a newbie to opera, so I have no idea if they would release such a terrible beta like firefox 3.

Opera's beta is version 2 now. It works great. I have been using it since it came out. The new beta is very good.

Opera 9.50b2 is what you should get. 

I noticed it didn't come up in the menu until after I rebooted (or logged out, I can't tell).

Until then, press Alt + F2 and type "opera".

Download it from [http://www.opera.com/download/?ver=9.50b2](http://www.opera.com/download/?ver=9.50b2)

---

### Post by yssida on 2008-04-30
I suggest lynx. If you want to use your mouse, try links.

---

### Post by Solrac924 on 2008-05-06
> **yssida said:**
> I suggest lynx. 

Lynx?!? LOL. we're past the mid-nineties buddy! :lol:

---

### Post by ioabs on 2009-07-28
When I am not using firefox I use epiphany...it does not have all the bells and whistles but it runs fast clean and is fully compatible with Ubuntu.

---

### Post by mamamia88 on 2009-07-28
google chrome is great and when final release comes out i will switch from firefox as soon as it lets me use flash

---

### Post by Crunchy the Headcrab on 2009-07-29
Running Firefox 3.5.1.  It's been very fast, I haven't had any errors, and of course it's got the add-ons.  Opera was very slow and IE *gasp* isn't great either.  I've never tried Chrome because I don't like how it looks.  What? :P

---

### Post by Arup on 2009-07-29
Dunno bout best as its quite subjective depending on requirements and indivdual perceptions but Opera has run for me quite well since version 2x, I stuck with it in Linux and now the latest version 10 truly runs good on my Jaunty x64 and best of all its now qt4.

---

### Post by gnomeuser on 2009-07-29
Already in it's current stage I find Chromium (or Google Chrome if one so desires) very appealing. It's fast, stable and elegant. 

I still miss the containment features of the Windows and Mac versions but we have nobody to blame but ourselves for that, we should have settled on one security framework and provided a higher level API for that to let application developers such as the chromium guys take advantage of it easily. Instead we have at least 3 competing with widely different adoption and API. ******* brilliant thinking going on here.

---

### Post by ktechkio on 2009-07-29
Opera 10 has lots of features. Its not only small and light but comes with lots of features. It even has an efficient boost button to compress data transfer via proxy for slow connections.

You may like to try beta 2 unite build with file sharing, music streaming, instant messenger, profile...

See
[http://my.opera.com/desktopteam/blog/2009/07/16/more-than-beta-2](http://my.opera.com/desktopteam/blog/2009/07/16/more-than-beta-2)

---

### Post by th3g1vr on 2010-09-03
> **Solrac924 said:**
> Lynx?!? LOL. we're past the mid-nineties buddy! :lol:

Hey, some of us like the linux(s) of the 90's! Why do you think Slackware is still being actively used and developed?

I happen to like Lynx-- it's especially useful for going through the Gentoo manual in the ttys while trying to install your GUI of choice. 

Even for normal use, It's fast, simple, and best of all doesn't have annoying ads and eye-bleeding CSS everywhere!

---

### Post by Spice Weasel on 2010-09-03
> **th3g1vr said:**
> Hey, some of us like the linux(s) of the 90's! Why do you think Slackware is still being actively used and developed?

I happen to like Lynx-- it's especially useful for going through the Gentoo manual in the ttys while trying to install your GUI of choice. 

Even for normal use, It's fast, simple, and best of all doesn't have annoying ads and eye-bleeding CSS everywhere!

You should try Links2 (in Graphical mode.) No css, but supports images and such.

---

