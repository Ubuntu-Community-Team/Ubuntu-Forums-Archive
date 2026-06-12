---
title: "Firefox 3.5 Branding Fix for Jaunty"
date: 2009-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by d2globalinc on 2009-07-28
I noticed when installing Firefox 3.5 from the repositories in Jaunty that the branding was set to "Shiretoko".. I couldn't have that because it would just confuse our users.. It's bad enough they ask where the "E" or "Internet Explorer" icon is - and when we finally get them using Firefox and noticing it's icon, we don't need to confuse them yet again.. 

Soooo - I made this little HowTO to Install Firefox 3.5 from the repositories then re-brand it back to Firefox's logo's, name, etc... 


- First - close all firefox windows and open a terminal window.

- Next copy and paste the following:
```

sudo apt-get install firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support


```

- After install I do another sudo command to make sure sudo is still active without having to enter a password.  If it is not - then you will need to enter your sudo password again after entering this command:
```

sudo ls


```

- Finally we copy and paste the following all at once to re-brand Firefox 3.5 using the original Firefox branding information that should still be on your system (because we do not remove Firefox 3.0.x that comes with Jaunty and we leave it on the system):
```


#
sudo cp -v /usr/lib/firefox-3.0*/icons/* /usr/lib/firefox-3.5*/icons/
cd /usr/lib/firefox-3.5*/defaults/preferences/
sudo cp -v firefox.js_bak firefox.js
sudo cp -v firefox.js firefox.js_bak
sudo sed -i "s/pref(\"general.useragent.extra.firefox\", \"Shiretoko\//pref(\"general.useragent.extra.firefox\", \"Firefox\//g" firefox.js
cd /usr/lib/firefox-3.5*/chrome/
sudo cp browser-branding-en-US.jar_bak browser-branding-en-US.jar
sudo cp browser-branding-en-US.jar browser-branding-en-US.jar_bak
sudo cp browser-branding.jar_bak browser-branding.jar
sudo cp browser-branding.jar browser-branding.jar_bak
cd /usr/lib/firefox-3.0*/chrome/
sudo cp -p browser-branding.jar /usr/lib/firefox-3.5*/chrome/
cd /usr/lib/firefox-3.0*/chrome/icons/default/
sudo cp -p * /usr/lib/firefox-3.5*/chrome/icons/default/
sudo mkdir -p /d2tmp/ffbrandnew/
sudo chmod 755 -R /d2tmp
cd /usr/lib/firefox-3.5*/chrome/
sudo cp browser-branding-en-US.jar /d2tmp/ffbrandnew/
sudo unzip /d2tmp/ffbrandnew/browser-branding-en-US.jar -d /d2tmp/ffbrandnew/
sudo rm -f -r /d2tmp/ffbrandnew/browser-branding-en-US.jar
sudo sed -i "s/<\!ENTITY  brandShortName        \"Shiretoko\">/<\!ENTITY  brandShortName        \"Firefox\">/g" /d2tmp/ffbrandnew/locale/branding/brand.dtd
sudo sed -i "s/<\!ENTITY  brandFullName         \"Shiretoko\">/<\!ENTITY  brandFullName         \"Mozilla Firefox\">/g" /d2tmp/ffbrandnew/locale/branding/brand.dtd
sudo sed -i "s/<\!ENTITY  vendorShortName       \"mozilla.org\">/<\!ENTITY  vendorShortName       \"Mozilla\">/g" /d2tmp/ffbrandnew/locale/branding/brand.dtd
sudo sed -i "s/<\!ENTITY  releaseBaseURL        \"http:\/\/www.mozilla.org\/projects\/shiretoko\/releases\/\">/ /g" /d2tmp/ffbrandnew/locale/branding/brand.dtd
sudo sed -i "s/brandShortName=Shiretoko/brandShortName=Firefox/g" /d2tmp/ffbrandnew/locale/branding/brand.properties
sudo sed -i "s/brandFullName=Shiretoko/brandFullName=Mozilla Firefox/g" /d2tmp/ffbrandnew/locale/branding/brand.properties
sudo sed -i "s/vendorShortName=mozilla.org/vendorShortName=Mozilla/g" /d2tmp/ffbrandnew/locale/branding/brand.properties
cd /d2tmp/ffbrandnew/
sudo zip -r browser-branding-en-US.jar locale
sudo cp /d2tmp/ffbrandnew/browser-branding-en-US.jar /usr/lib/firefox-3.5*/chrome/
cd /usr/bin/
sudo rm -f -r /d2tmp/
sudo rm -f -r firefox
sudo ln -s firefox-3.5 firefox
sudo sed -i "s/Name=Shiretoko Web Browser/Name=Firefox 3.5 Web Browser/g" /usr/share/app-install/desktop/firefox-3.5.desktop
sudo sed -i "s/Comment=Firefox 3.5 Beta/Comment=Browse the World Wide Web/g" /usr/share/app-install/desktop/firefox-3.5.desktop
sudo sed -i "s/GenericName=Preview Browser/GenericName=Web Browser/g" /usr/share/app-install/desktop/firefox-3.5.desktop
sudo sed -i "s/Name=Shiretoko Web Browser/Name=Firefox 3.5 Web Browser/g" /usr/share/applications/firefox-3.5.desktop
sudo sed -i "s/Comment=Firefox 3.5/Comment=Browse the World Wide Web/g" /usr/share/applications/firefox-3.5.desktop
sudo sed -i "s/GenericName=Preview Browser/GenericName=Web Browser/g" /usr/share/applications/firefox-3.5.desktop
#

```

There we go!  Everything should now be labeled Firefox instead of Shiretoko, and the original link to firefox should now point to firefox 3.5!

- Enjoy!

Shane Menshik
D2 GLOBAL INC
[http://www.d2global.com](http://www.d2global.com)

---

### Post by rpotter28 on 2009-07-28
Has anyone tried this?

---

### Post by hatemben on 2009-07-29
tested and working fine here. Thanks

---

### Post by mikewhatever on 2009-07-29
That's a lot of commands to paste just to get rid of Shiretoko. Wouldn't it make sense to put them all in a script and just run it once?

---

### Post by vmatherly on 2009-07-29
Worked perfect!

---

### Post by pjalegria on 2009-07-29
The icons are not from FF3.5...

---

### Post by ivotron on 2009-07-30
Thank you, worked perfectly

---

### Post by binbash on 2009-07-30
It works

---

### Post by Arup on 2009-07-30
Works like a charm, thank you. Most important is that open with in Opera now opens pages with FF 3.51 by default.

---

### Post by Robbie7up on 2009-07-31
Worked perfectly, ended a week long hunt to get Firefox 3.5 on my computer.

---

### Post by racmar on 2009-08-05
Thanks!  That headache was driving me crazy on sites that actually check if the user-agent is Firefox, not Shiretoko.

---

### Post by stillious on 2009-08-05
Cool, won't have to put up with that crappy icon and user agent any more :guitar:

---

### Post by exoren22 on 2009-08-05
How can I modify this script to allow me to remove ff3.0 afterward? I only need one and if you remove 3.0 it destroys the links and everything.

---

### Post by bchalstrom on 2009-08-07
The script seemed to work fine for me -- ALL except the Help menu still says "About Shiretoko".  Not a big deal, but are others of you seeing this too?

---

### Post by racmar on 2009-08-07
Mine says "About Mozilla Firefox".  Maybe if you re-run the script?  Also, I had to run it again after the 3.5.2 upgrade.

---

### Post by Goombie on 2009-08-07
This fix worked fine for me. :) I did need to run it again after installing Firefox 3.5.2, though. But it's no big deal, since it takes all of 30 seconds to run.

---

### Post by rcayea on 2009-08-09
Worked great for me.

---

### Post by naturenut on 2009-08-12
Worked like a charm, except for one thing. I'd already removed 3.0 from my system so I don't have the icons anymore. Any way to get a copy of them? Don't want to reinstall 3.0 and jump through all the hoops to get it back to 3.5...

---

### Post by naturenut on 2009-08-12
> **exoren22 said:**
> How can I modify this script to allow me to remove ff3.0 afterward? I only need one and if you remove 3.0 it destroys the links and everything.

I had installed 3.5 prior to the official release, so it copied my profile to it's setup. I uninstalled 3.0 and installed 3.5, both using Synaptic. That gave me Shiretoko as the browser that starts from Applications/Internet. Didn't like the icon and name (expected them to be corrected with the official update), so some searching brought me here and I ran the above commands to rebrand as FF. It worked great, except I still have the Shiretoko icons because I'd removed the 3.0 setup - 3.0.12 directory only contains a directory named Updates, which has an empty directory named 0 in it. Didn't lose any settings, addons or bookmarks. Hoping someone can give me some pointers on getting the right icons, but that's in another post to this thread...

---

### Post by tonylibby on 2009-08-13
Thanks for sharing, It really worked for me.

---

### Post by drskartik on 2009-08-18
Thanks it was of great help, did'nt realise it could be so easy and quick.
Kartik

---

### Post by nortexoid on 2009-09-11
Worked for me. Someone who knows how to make scripts needs to make one so that this routine task can be carried out in a single click/command.

Thanks!

---

### Post by JPKnowMad on 2009-09-11
Hey Guys,
          this worked well for me. One thing, when I opened firefox afterwards it said i should upgrade to 3.5.3. How can I do that while keeping these changes? Thanks

---

### Post by nortexoid on 2009-09-11
Since I've got the mozilla dailys, when I updated Firefox all the changes I made (doing things mentioned here) reverted. I'm back to Shiretoko's branding. Rubbish!

Is there a permanent fix that will survive updates?

---

### Post by -_- Joseph -_- on 2009-09-11
I've had this problem for a while thanks for the update:D:D:D

                      ,Joseph

---

### Post by TokyoYank on 2009-10-14
> **nortexoid said:**
> Since I've got the mozilla dailys...Is there a permanent fix that will survive updates?Just an idea: 

Since there are multiple routes to 3.5, could any gurus reading write a firefox-3.5-fixbranding package, either a) using the OP script or b) packaging required icons?  ...  Is there an easy way to write a script that runs only when a certain file(s) gets touched?

BTW If/when such a package should exist, then I'd be happy to write a "HowTo Upgrade to Firefox 3.5 for 8.10 and 9.04".  If you google "ubuntu firefox 3.5 howto" you get a mix of hits before it was in the repos, but no concise howto for folks wanting "to add plus tab," etc.

/end $.02

---

### Post by nortexoid on 2009-10-15
Try changing the general.useragent.extra.firefox in about:config by replacing 'Shiretoko' with 'Firefox'.

It's not exactly the type of rebranding you want, but it will at least make Shiretoko compatible with sites that check for user agent, e.g. Facebook. I've had no problems so far doing this.

---

### Post by makkirot on 2009-10-15
Works fine !.Thanks buddy

---

### Post by TokyoYank on 2009-10-15
> **nortexoid said:**
> Try changing the general.useragent.extra.firefox in about:config by replacing 'Shiretoko' with 'Firefox'.
Mine said Shiretoko/3.5.3  (which I changed to Firefox/3.5.3)

..does that mean this value gets reset upon 3.5 updates, or just the version number?

So far so good, will try to remember to check this next update

---

### Post by nortexoid on 2009-10-15
> **TokyoYank said:**
> Mine said Shiretoko/3.5.3  (which I changed to Firefox/3.5.3)

..does that mean this value gets reset upon 3.5 updates, or just the version number?

So far so good, will try to remember to check this next update

No, it doesn't get reset, but as you predict, the version number gets updated. The whole value of general.useragent.extra.firefox remains as 'Firefox/[version]', e.g. 'Firefox/3.5.4pre'.

Perhaps if you change the whole value, including the version number tailing the '/' (slash), the whole string might not change at all. I haven't tried this. (Some people remove the 'pre'.)

---

### Post by GadeTerbob on 2009-10-15
Thanks for the how to upgrade Firefox info.

---

### Post by Renée Jade on 2009-10-19
This worked for making facebook get a grip. Thanks! However I already removed firefox 3 a while ago. Any idea how to get my icons back now?

---

### Post by 565Customz on 2009-10-19
worked beautifully! i didnt even lose any of my saved passwords or bookmarks...nice!

---

### Post by TokyoYank on 2009-10-19
> **Renée Jade said:**
> This worked for making facebook get a grip. Thanks! However I already removed firefox 3 a while ago. Any idea how to get my icons back now?
No simple way to reinstall just the icons has been mentioned.  I think most folks are content to simply reinstall firefox-3.0  ... The packages are separate as far as I can tell

---

### Post by Renée Jade on 2009-10-20
I managed to get the GNOME menu to use a firefox logo as the button simply by hunting down the icons and replacing the images with firefox images. I still get the little globe on the task bar and window switcher though, I hunted for that little globe everywhere so I could replace it but I can't find it :(.

---

### Post by dserodio on 2010-02-08
Thanks for the info, but shouldn't the firefox-3.5-branding package take care of this? Shouldn't we file a bug on this package for failing to properly "brand" Firefox?

---

