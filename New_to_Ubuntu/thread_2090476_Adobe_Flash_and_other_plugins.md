---
title: "Adobe Flash and other plugins"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by philpense on 2012-12-02
Working with Lubuntu and Chromium.  Have read everything I can find on the Adobe Flash plugin.  Apparently Flash exists within Chromium but disabled.Have gone  the appropriate Adobe Flash site.  Several 'flavors' have been downloaded.  Launch attempts have failed on the two flavors tried.  entering 'plugins' in the web browser has not worked.  Attempted the Chromium "tools" option found at: 
[http://helpx.adobe.com/flash-player/kb/flash-player-google-chrome.html#main_How_do_I_install_the_latest_version_of_Flash_Player_in_Google_Chrome_](http://helpx.adobe.com/flash-player/kb/flash-player-google-chrome.html#main_How_do_I_install_the_latest_version_of_Flash_Player_in_Google_Chrome_)

Launching the downloaded flash software are halted shortly after.  Out of ideas.

---

### Post by Pilot6 on 2012-12-02
If your cpu is old and does not support sse2, you need to download and manually install libflashplayer.so from flash 10.3.
You can find how to do it by forum search.

---

### Post by gandaran on 2012-12-02
> **philpense said:**
> Working with Lubuntu and Chromium.  Have read everything I can find on the Adobe Flash plugin.  Apparently Flash exists within Chromium but disabled.Have gone  the appropriate Adobe Flash site.  Several 'flavors' have been downloaded.  Launch attempts have failed on the two flavors tried.  entering 'plugins' in the web browser has not worked.  Attempted the Chromium "tools" option found at: 
[http://helpx.adobe.com/flash-player/kb/flash-player-google-chrome.html#main_How_do_I_install_the_latest_version_of_Flash_Player_in_Google_Chrome_](http://helpx.adobe.com/flash-player/kb/flash-player-google-chrome.html#main_How_do_I_install_the_latest_version_of_Flash_Player_in_Google_Chrome_)

Launching the downloaded flash software are halted shortly after.  Out of ideas.
Chromium is not exactly the same as Google Chrome, Chrome does have built-in flash, Chromium doesn't have it yet it uses the system installed flash, open the Ubuntu Software Center or Synaptic Package Manager type flash in the search box and install the flashplugin-installer package, no need to download anything from adobe website, if this doesn't work then you maybe using an older version of Ubuntu that is no longer supported.

---

### Post by deadflowr on 2012-12-02
There is no built-in flash inside chromium.
Google-Chrome comes with pepperflash.
Chromium, like Firefox and other browsers use the flash installed on your system.
Chromium can however run the pepperflash plugin, but you'd need to install google-chrome.
Chromium uses free software by default, so non-free software is not included by default.

---

