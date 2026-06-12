---
title: "system tray icon for mail-notification??"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by Paco62 on 2012-09-05
I just installed 12.04 on a netbook and installed the program 'Mail Notification'.  I tested it with my local (ISP) mail account and it works ie it gives a popup notifier and makes a sound.   But there is no icon in the top panel for the program that shows a new mail message has arrived.  On my desktop with 10.04, there is an icon, which continues to show even after the popup message has disappeared.   How can I get an icon in 12.04?  TIA

---

### Post by NikTh on 2012-09-05
Hello , 

I think is not necessary to install extra program in 12.04 for a message(mail) notification . 
Thunderbird (pre-installed) can do that. 

Just click on message icon on top bar and from the drop-down menu click "Mail" . When Thunderbird window open , setup your account (usually is an easy method). 

You must have in mind , that notifications with Thudnerbird displayed only if Thunderbird is open and running. 

Another - alternate method that I know , is Unity Mail. Search for it in Software Center. 

Thanks

---

### Post by lolpenguin on 2012-09-06
The old notification message tray doesn't support Ubuntu's appIndicator API, so it is disabled by default. You can enable it (and other old message tray icons) by opening dconf-editor (install dconf-tools if it is not), and browsing to desktop/unity/panel and settings systray-whitelist to "all"

---

### Post by black veils on 2012-09-06
or you could be notified by a pop-up through your web browser, either temporary or sticks until you remove it, from the bottom-right corner of the screen. it will show even when the web browser is minimised, and seems to work through full-screen applications.

**firefox**: [https://addons.mozilla.org/en-US/firefox/addon/webmail-notifier/](https://addons.mozilla.org/en-US/firefox/addon/webmail-notifier/)

**chrome**: [https://chrome.google.com/webstore/detail/apebebenniibdlpbookhgelaghfnaonp](https://chrome.google.com/webstore/detail/apebebenniibdlpbookhgelaghfnaonp)

**opera**: [https://addons.opera.com/en/extensions/details/x-notifier-gmail-hotmail-yahoo-aol/?display=en](https://addons.opera.com/en/extensions/details/x-notifier-gmail-hotmail-yahoo-aol/?display=en)

---

### Post by Paco62 on 2012-09-06
> **lolpenguin said:**
> The old notification message tray doesn't support Ubuntu's appIndicator API, so it is disabled by default. You can enable it (and other old message tray icons) by opening dconf-editor (install dconf-tools if it is not), and browsing to desktop/unity/panel and settings systray-whitelist to "all"

I tried setting whitelist to 'all' as you suggested and there is still no icon for mail notification program.  Please note, I am using gnome desktop, not unity.  I also installed gconf-editor and went to schemas/apps/mail-notification and there is a key which says 'always display icon'  and the value for the key is set to <schema>  but apparently there is no way to edit this key to change the value to 'true'.  (It says the ability to edit pairs and schemas is not available, but will be available in a later version.  Is there a ppa to get a later version , if it is available?)

---

