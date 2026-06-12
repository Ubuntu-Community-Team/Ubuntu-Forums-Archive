---
title: "Firefox 3.0 (&amp; beta) doesn't display some elements"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by smittee on 2008-06-14
Since upgrading to the Hardy Heron + the Firefox beta version a fortnight ago or so, some webpage elements stopped displaying at all - there isn't even a blank space to tell me that something is supposed to be there. I updated Firefox to 3.0 today, which didn't fix it.  Youtube: the spot where the video is supposed to be disappeared and everything underndeath it has just shifted up.  Some jpegs display, some don't.  At a wordpress blog, I couldn't view the jpeg in the page, but I could view it if I clicked the link to see it at it's location.  One website, nothing is visible except the background image.  Flickr seems to work fine.

And occassionally it just shuts down when I close 1 tab, but not every time.

It's a Viao vgn-fs48gp laptop with nvidia video card, I already grabbed the nvidia linux driver from their website when the display went skewiffy after upgrading.

I've got the following firefox extensions:
* Adblock Plus 0.7.5.4  (still have a problem when I disable this)
* Custom buttons 0.0.3.2
* fast dial 1.9
* Greasemonkey 0.8.20080609.0 (I added this extension since the problem started)
* iMacros 6.0.5.3
* Scrapbook 1.3.3.5
* Scribefire 2.2.6
* Stumbleupon 3.18
* Ubuntu Firefox Modifications 0.5

Any help greatly appreciated.  Thanks.

---

### Post by mailtwogopal on 2008-06-14
hi,

  Before upgrading to firefox 3.0, were u getting all the things in all the forementioned sites. What version were u using in firefox browser before upgrading.

---

### Post by alienexplorers on 2008-06-14
Do you have flash installed.  In order to watch video's on YouTube you need flash.  The plugin should be in your ~/.mozilla/plugins folder.  Adblock Plus can also cause strange effects.  Try disabling it and see if your problems improve.

---

### Post by smittee on 2008-06-14
Actually, I have been having lots of trouble with videos prior to upgrading/updating Ubuntu and Firefox.  But I could always see that there was a space where the item should be on a page - if it was a vid I could see the preview-still shot, then it would go black and fail to play.  That was Gutsy Gibbon + Firefox 2.0.0.14.  I hadn't figured out how to play shockwave, but I had installed a flash plugin that seemed to work(? maybe).

Now the space for some things is missing altogether and the page layout is rearranged.  Sometimes the only clue I had that a page wasn't displaying properly was the little adsense "block" tab floating somewhere on a page.  I have uninstalled adsense now, and I still have this problem.

The contents of my ~/.mozilla/plugins folder is:

libflashplayer.so
appreg
pluginreg.dat

I think I might uninstall Firefox 3.0 and go back to 2.0.0.14, but I've had bad experiences uninstalling programs in windows, and I am such a total linux noob that it took me a month to figure out what all the talk about doing stuff in terminals meant.:rolleyes:

Thanks for your help mailtwogopal & alienexplorers.

---

### Post by Happy_Man on 2008-06-14
Well, it seems that your Firefox 3 problems are just the same thing as your firefox 2 problems, so going back wouldn't do anything to help. What happens when you try to install the package flashplugin-nonfree?

---

### Post by alienexplorers on 2008-06-14
When you updated from 2.0 to 3.0 did you completely remove 2.0 or just remove it.  The reason I ask is that if you did not completely remove 2.0 then the ~/.mozilla directory would not be deleted.  Thus when you added 3.0 it would use the same ~/.mozilla directory.  If something was bad in that directory in 2.0 the same problem would show up in 3.0....  You could try making a new profile using in terminal:
> firefox -profilemanager
just pick the default items suggested by the program.  When you return to the main menu delete the default profile.  Start firefox from the main menu.  Shutdown firefox and then wait 10 seconds and restart firefox the way you normally would.  Hopefully this will fix your problem.

---

### Post by smittee on 2008-06-14
I decided to do the Hardy Heron upgrade, and just accepted the upgrade package completely.  afaik nothing was uninstalled first. 

I was thinking my problem getting the black-box for video with GG/FF2 were because I hadn't found or properly installed the right drivers.

The troublesome problems since going to HH/FF3 are very different.  I'm not getting black boxes anymore - I'm not getting anything, not even a gap.  I can see that a jpeg should be appearing per the source code for a page, but there's not even a blank space.  It's not limited to jpgs or videos, but all sorts of things like gifs and text boxes.  Sometimes the text for links appear, but just as text, without the links.

Now I think I've found the problem: I was able to understand a bit of the mozilla firefox 3.0 release notes, [release notes - linux issues]("http://www.mozilla.com/en-US/firefox/3.0rc3/releasenotes/#issues"):

"Incompatibilities between NVIDIA drivers and some versions of the X server cause scaled images to render incorrectly" (link: [bug 411831]("https://bugzilla.mozilla.org/show_bug.cgi?id=411831"))

(I tell you, my nvidia card and ubuntu have not been getting along at all.)

So anything that is scaled down doesn't display properly.  Which fits one experience I had where a thumbnail picture didn't display, but I had no trouble viewing the picture in original size at its location.

Anyway, the details for bug 411831 don't give me any solutions, and it's a major problem.  I do need to change back to FF2.  

Can I rely on the add/remove programs wizard to make the change? Or what's the best way to do it? And are there specific drivers I need to combat that black-box problem and get vids working?

Thanks for all your time.  :)

---

### Post by alienexplorers on 2008-06-14
What's wrong with firefox 3.0 that makes you want to switch back to 2.0...  I have had no problems with firefox 3.0 since switching to Hardy.  All of the extensions I use either are updated to 3.0 or I go in an update the extension myself so it works with 3.0...

---

### Post by Happy_Man on 2008-06-15
If you are using the restricted drivers in Hardy, try switching back to the vesa drivers using ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Not using Nvidia drivers may alleviate the situation.

---

