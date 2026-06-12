---
title: "Ubuntu Software Folders not working"
date: 2019-02-24
forum: New to Ubuntu
---

### Post by alejandro202 on 2019-02-24
I recently installed Ubuntu into my system. I have been downloading Apps through the Ubuntu Software. I have grouped my Apps by categories inside folders through the Ubuntu Software. I saved this process. I go ahead to the App Menu and some of them are inside folders but others are not. How can I solve this problem? I want my Apps in the App Menu to be inside folders. I used to us GNOME App Folders Manager, but this software is not packaged and I can't download it via the Ubuntu Software or the sudo apt terminal command.

---

### Post by deadflowr on 2019-02-24
I see the Gnome Apps Folder Manager hasn't been updated in 2 years.
[https://github.com/muflone/gnome-appfolders-manager]("https://github.com/muflone/gnome-appfolders-manager")
Gnome is not static and changes happen all the time, which break things that worked before, especially extensions and things that manipulate the shell.

My suggestion would be to either try to install it (following the howto guide in the github link) 
or
try an alternative like this one:
[https://extensions.gnome.org/extension/1217/appfolders-manager/]("https://extensions.gnome.org/extension/1217/appfolders-manager/")
(It's installable through the Ubuntu Software >> Add-ons >> Shell Extensions
(or you can enable it directly from the browser if you have the chrome-gnome-shell package installed and the added addon/extension enabled in your browser;
chrome-gnome-shell will add an addon/extension called gnome shell integration to your browsers addon/extension listing)

---

### Post by alejandro202 on 2019-02-24
Thanks! Solved, extensions are very fancy and useful.

---

