---
title: "Firefox 3 FINAL in Gutsy"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Dbugger on 2008-06-18
Hello. Is it possible to install firefox 3 FINAL in gutsy gibbon? How?

Help very appriciated :)

---

### Post by NilsE on 2008-06-18
The final is not available in the repositories yet but have you looked in Synaptic to see if it is there at all.  It should be at least RC2.  The final should hit within a week or so when the Ubuntu packaging is done.

I know it is in the Hardy repos but not sure about Gutsy but in any event if it is there it is probably in the proposed repo so make sure that is turned on in software sources.  Just turn on all repos in software sources and reload and see if it is there in Synaptic.

---

### Post by MasterSander on 2008-06-18
You can check getfirefox.com for 3.0, I'm already using it on hardy.

---

### Post by Dbugger on 2008-06-18
Im looking for help in GUTSY GIBBON.

---

### Post by NilsE on 2008-06-18
> **MasterSander said:**
> You can check getfirefox.com for 3.0, I'm already using it on hardy.
That is why I suggested turning on the extra repos to see if it was there in Gutsy

---

### Post by Dbugger on 2008-06-18
I activated ALL the repos and now I see a packet "firefox-3.0" and a "firefox-granparadiso".... which one should I install?

---

### Post by ubukool on 2008-06-18
Hi,

You can easily install Firefox 3 in Gutsy using this tutorial:

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

All you need to do is to cut and paste these commands in your terminal:

      First, back up your bookmarks and settings:

      **cp -R ~/.mozilla ~/.mozilla.backup**

 
      Download Firefox from the [WWW] Firefox website, and change to the directory you downloaded it to.

(e.g., download it to desktop, the open a terminal and type:

**cd /[your home directory name]/Desktop**)
  

      Install it to /opt/firefox (make sure the /opt directory exists first):

      [B]sudo tar -jxvf  firefox-3.0.tar.bz2 -C /opt
      rm firefox-3.0.tar.bz2[/B]

    *

      Link to your plugins and remove totem-mozilla as it doesn't seem to work with Firefox 1.5.x or 2.x:

      [B]sudo mv /opt/firefox/plugins /opt/firefox/plugins.bak
      sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins
      sudo rm /usr/lib/firefox/plugins/libtotem_mozilla.*[/B]

    *

      To ensure it is used as the default version, modify the symbolic link in /usr/bin:

      [B]sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
      sudo ln -s /opt/firefox/firefox /usr/bin/firefox
      sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
      sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox[/B]

      The dpkg-divert command will move the original system-wide /usr/bin/firefox to a new name. The ln command will place a symlink to the newly installed Firefox in /usr/bin.
    *

      Try it out: :-)

      **firefox &**

    *

      Running Firefox in terminal may cause errors to show but don't worry about that, it will still work once Firefox is restarted. The reason for these errors is because Firefox 3 is checking for updates, which is not abnormal activity. Also, running this command make take a some time to execute. Please be patient.
    *

      If you want to keep the original Ubuntu icon for Firefox, enter this command:

**      sudo cp /usr/share/pixmaps/firefox.xpm /opt/firefox/chrome/icons/default/default.xpm**

Some users may find the icon with a different extension, they should use this command:

    *

      sudo cp /usr/share/pixmaps/firefox.png /opt/firefox/chrome/icons/default/default.xpm


Don't be daunted - it's literally a few cut and pastes in your terminal to get it all to work.  Then, when you click on your Firefox icon, you'll get a brand spanking new release of Firefox 3 on your desktop :) It rocks!

Please ask if there's something you're not sure about.

All the best!

Ubukool

---

### Post by Dbugger on 2008-06-18
> **ubukool said:**
> Please ask if there's something you're not sure about.

All the best!

Ubukool

thank you. Awesome tutorial. One question thoguh. Will this remove my old firefox 2? I wouldnt like to have 2 versions of the same webbrowser. Im kinda nitpicky when it comes to the "cleanly-ness" of my system :)

---

### Post by ubukool on 2008-06-18
Hi Dbugger,

Yes, when I installed this last night it took out my Firefox 2.

This tutorial might be better for you because it installs it alongside Firefox 2:

[http://tombuntu.com/index.php/2008/03/11/install-firefox-3-beta-4-in-ubuntu-with-one-command/](http://tombuntu.com/index.php/2008/03/11/install-firefox-3-beta-4-in-ubuntu-with-one-command/)

You can do the same but as it suggests but with the Firefox 3 -just substitute firefox -3.0.tar.bz2 for firefox-3.0b4.tar.bz2.  If that doesn't work you can download the file from here:

[http://www.mozilla.com/en-US/firefox/all-rc.html](http://www.mozilla.com/en-US/firefox/all-rc.html)

or the main Firefox page

Hope it works!

---

### Post by ubukool on 2008-06-18
Sorry, I misread what you said!  Yes, you won't have any problems because this method does remove Firefox 2

:)

P.S., the Firefox in the repositories is Firefox 3 beta 4, not the new release.

---

