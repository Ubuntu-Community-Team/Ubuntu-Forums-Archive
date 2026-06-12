---
title: "How to make Java work on a browser (Midori)?"
date: 2015-08-24
forum: New to Ubuntu
---

### Post by joo11 on 2015-08-24
So I don't know anything about Linux or Java[/B] but I have to make Midori run this game that uses java: [http://oldschool.runescape.com/game?world=369](http://oldschool.runescape.com/game?world=369)

I download Java and Midori but I still couldn't load that site. I used these:
sudo add-apt-repository webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
sudo apt-get install midori

Then I read this on Midori faqs:
"Java is supported in WebKitGTK+ since 1.1.22. If you need Java, you need to upgrade to at least that version. Sun/ Oracle Java as well as IcedTea are known to work. Distribution specific setup might be required, such as setting LD_LIBRARY_PATH to include the location of libxul.so and making a symbolic link for libnpjp2.so to /usr/lib/mozilla.
icedtea6 version 1.8 and above has been known to crash midori. If this is the case for you, try sun-jre."

Then I spent hours on the terminal doing a lot of things with libnpjp2.so; LD_LIBRARY_PATH and libxul.so (I probably did it wrong) but nothing worked.

Then I found out I had to use this to update the Midori: sudo apt-add-repository ppa:midori/ppa && sudo apt-get update -qq && sudo apt-get install midori.

The site now loaded; but the "activate java" button didn't pop up -.-

And now idk wtf I should to; why is this so hard ffs...

edit: I use XUBUNTU
[IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/icons/useragent/icon_linuxubuntu.gif[/IMG] [IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/statusicon/forum_new.gif[/IMG]

---

### Post by tristan16 on 2015-08-24
Are you sure the game is compatible with Ubuntu? When I tried loading it and clicked on the Not Loading help link, it says to download a .msi file, which is a Windows Installer. Maybe I'm wrong, but I don't think Windows programs can interface with a web browser through WINE.

---

