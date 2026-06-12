---
title: "icelandic firefox"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Jcinside on 2008-11-02
Can someone tell me how too install icelandic firefox in ubuntu 8.10

---

### Post by Sand Lee on 2008-11-02
After some google searches, i've come up with these links:
[Firefox Download Page]("http://www.mozilla.com/en-US/firefox/all.html")
[FF3 Icelandic]("http://download.mozilla.org/?product=firefox-3.0.3&os=linux&lang=is")
[Installing Mozilla's Firefox]("http://www.psychocats.net/ubuntu/firefox")
[Icelandic Dictionary]("https://addons.mozilla.org/en-US/firefox/addon/3643")

---

### Post by Jcinside on 2008-11-03
Thanks

---

### Post by Bölvaður on 2008-11-03
You need more than that.
When you install the icelandic version you must also link all the plugins and such to it. Unless if you have something against plugins such as flash and java.

This is the GUI way. The terminal way is much shorter, but as you might be new to linux I will not use it.

Go there &#8594; [http://www.mozilla.com/en-US/firefox/all.html]("http://www.mozilla.com/en-US/firefox/all.html") and download the latest icelandic linux version. It is placed at the bottom of the page because the translation hasn't been finished yet.  You can contribute to the transelation by clicking "Help &#8594; Translate This Application..."

Download this to your desktop.
Now you either want to place this where the english version is kept or in your home directory. Lets assume that you use the default one.

Right click the downloaded file and click "extract here"

[SIZE="3"]Now we move this to the default directory:[/SIZE]
start up nautilus as root:
Alt+F2 and type: "gksu nautilus"
Then find /home/username/Desktop/firefox, cut it and paste it to /usr/lib/
If there is another directory called the same, then change the name of the icelandic version to something like firefox_ice.

[SIZE="3"]Setting in pluggins[/SIZE]
Make a link to the plugin/extention place.
You can find them here: /usr/lib/xulrunner-addons
Right click on Plugins and chose "**Make Link**"
Do the same for Extentions.
Now cut the links and paste them over the existing folders in the firefox_ice directory.


Now you are good to go.

Also there is half finished version of gnome in icelandic. You can find it under Administrator &#8594; Language Support.

---

