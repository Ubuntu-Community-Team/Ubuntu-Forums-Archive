---
title: "HOWTO: Subscribe to RSS Feeds in Akregator or Liferea from Chromium with Two Clicks"
date: 2010-06-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ode on 2010-06-11
1. Install the ['RSS Subscriptions with FEED: Handler Support'](https://chrome.google.com/extensions/detail/ehojfdcmnajoklleckniaifaijfnkpbi) Chromium extension.


2:
  2.1 Alt+F2--->gconf-editor

  2.2 In gconf-editor: Ctrl+F--->Search for 'feed'

  2.3 In the search box at the bottom of gconf-editor you will get some results (I got two.) Click on '/desktop/gnome/url-handlers/feed'.

  2.4 In the options box in the top right click on the 'command' key.

  2.5 Change the value to either 'liferea-add-feed "%s"' or 'akregator -a "%s"' depending on your preference. Press return to complete the edit.


3:
  3.1 Goto a webpage whose feed you wish to subscribe to.

  3.2 Now that you have installed the extension there will be an rss icon in the right of Chrome/Chromium's location bar. Click it.

  3.3 The browser will take you to a 'Subscribe to feed' page. In the dropdown box next to 'Subscribe to this feed using:' select 'Default Application'.

  3.4 Click the 'Subscribe Now' button. A warning box named 'External Protocol Request' will pop up. Press the 'Launch Application' button and confirm that the feed has been added to your reader.

  3.5 If the feed was added you can click the 'Remember my choice for all links of this type.' checkbox in the 'External Protocol Request' box the next time you subscribe to a feed. Now the next time you click the rss button in the location bar then the 'Subscribe Now' button on the 'Subscribe to feed' page the feed should be added to your reader.equest({msg: "

---

### Post by BoHu on 2011-03-29
step 3.4 click on "subscribe now" results in the following error message:

No webpage was found for the web address: chrome-extension://ehojfdcmnajoklleckniaifaijfnkpbi/http%3A//lxer.com/module/newswire/headlines.rss
Error 6 (net::ERR_FILE_NOT_FOUND): The file or directory could not be found.

---

### Post by ode on 2011-03-29
That feed works for me (in Chromium 9).

I think there must be an error in your setup.

---

