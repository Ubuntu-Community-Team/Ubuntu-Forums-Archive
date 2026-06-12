---
title: "HOWTO:Change language in Firefox/Swiftfox"
date: 2006-07-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Bossieman on 2006-07-09
I have seen some threads about changing the language in Firefox/Swiftfox and this guide will hopefully solve the problem.

First of all go to this page and install the language xpi that you want (Just klick the .xpi to install it). This is for Firefox/Swiftfox 2.0.0
[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0/linux-i686/xpi/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0/linux-i686/xpi/)
Dont forget to allow popup when you are there.
After you have installed the xpi file, open up a new window/tab. In the addressbar copy and paste 
```

about:config

```
Hit enter and you will see a list of stuff. Now copy and paste the following into the search/flter area
```

general.useragent.locale

```
Now you will se only one entry, doubleclick on it and add the code for your language (the same as the xpi file).
So if you installed the sv-SE.xpi you enter sv-SE.
After this, restart Firefox/Swiftfox and you have your preffered language.

---

### Post by pgmario on 2006-07-11
Thanks, worked great!

---

### Post by pinguin on 2006-11-07
To Bossieman
You wrote:
> First of all go to this page and install the language xpi that you want. This is for Firefox/Swiftfox 1.5.0.4
[http://ftp.mozilla.org/pub/mozilla.o...inux-i686/xpi/](http://ftp.mozilla.org/pub/mozilla.o...inux-i686/xpi/)
Dont forget to allow popup when you are there.
_After you have installed the xpi file_, open up a new window/tab. In the addressbar copy and paste 

Where I have to install .xpi file, please? Folder name?
thanks

---

### Post by stalefries on 2006-11-19
Pinguin: just click it, and tell it to install.

---

### Post by Handi on 2006-12-23
Is it possible to make the language in Swiftfox changed automatically by referring to the locale used? Just like the firefox that came from ubuntu package.
I have 2 users that use different language in one computer. The users do not like to change through about:config everytime they want to use their preferred language.

---

### Post by Bomper on 2006-12-31
> **Handi said:**
> Is it possible to make the language in Swiftfox changed automatically by referring to the locale used? Just like the firefox that came from ubuntu package.
I have 2 users that use different language in one computer. The users do not like to change through about:config everytime they want to use their preferred language.


Locale-Switcher Extension:

[http://benjamin.smedbergs.us/switch-locales/](http://benjamin.smedbergs.us/switch-locales/)

---

### Post by mmxbass on 2007-12-12
What did I do wrong here?
[IMG]http://www.acmlm.org/mmxbass/misc/ff_fail.png[/IMG]

---

### Post by Bossieman on 2007-12-14
> **hexnet said:**
> What did I do wrong here?
[IMG]http://www.acmlm.org/mmxbass/misc/ff_fail.png[/IMG]

I dont know what the problem is. Did you follow the guide? Its an old firefox you have there. Try upgrading to latest firefox and install the latest language pack.

---

### Post by mmxbass on 2007-12-14
> **Bossieman said:**
> I dont know what the problem is. Did you follow the guide? Its an old firefox you have there. Try upgrading to latest firefox and install the latest language pack.2.0.0.11 is old? I was under the impression this was the latest stable version.

---

### Post by Bossieman on 2007-12-14
> **hexnet said:**
> 2.0.0.11 is old? I was under the impression this was the latest stable version.

Yes, but look at this

[http://img338.imageshack.us/my.php?image=fffailcw8.png](http://img338.imageshack.us/my.php?image=fffailcw8.png)

If I was you I would install this one: [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.11/linux-i686/xpi/sv-SE.xpi](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.11/linux-i686/xpi/sv-SE.xpi)

---

### Post by thenes on 2008-05-07
I have the exact same problem as bossieman. I have followed the guide, with the only difference that I downloaded my xpi-file from [this page]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.13/win32/xpi/"), as the page linked to does no longer exist.

---

### Post by thenes on 2008-05-08
Sorry. What I meant is that I have the exact same problem as hexnet, the one who posted the picture in the tread.

---

### Post by benphane on 2008-06-21
Thanks!  Why for your post doesn't have the cute little "Thank you" button.

---

### Post by Blue Dolphins on 2009-08-11
How do I install the XPI file?  Do I have to do the ./configure, make, make install thing?  It came as a tar.bz2 file that seems to contain an entire firefox program(not just the language I want) but there's no ./configure file to ./configure.  Which is, as far as I'm aware, the only way to install something without the package manager.

---

### Post by arunvishy on 2010-07-30
I did the same and downloaded Kannada XPI......but my firefox is still showing in english........why is it so.......what steps would i have missed????

---

### Post by Ronok on 2010-10-16
the Links above are Broken...
--> Need something New and up-to-date 
--> From any Language To Any Language for everyone

> **Not Found**

The requested URL /pub/mozilla.org/firefox/releases/2.0/linux-i686/xpi/ was not found on this server.

[CENTER][URL="http://ubuntuforums.org/showthread.php?t=1598235"]From a new thread I started as 
all other hits were wrong Date model or scenario [/URL][/CENTER]
> How Do I Change Firefox **MENU** language to --> **Chinese**

Mozilla **Firefox 3.6.10** for Ubuntu Canonical - 1.0
CPU:    Intel Pentium Dual-Core  CPU E5300  @ 2.60GHz
System: **Ubuntu Linux 9.10** (karmic)
GNOME:  2.28.1 
Kernel: 2.6.31-22-generic

System > Administration > Language Support > Menus = Chinese

most everything else in this machine is in Chinese,
But Firefox is still has English Menus

I looked at **Firefox**: Edit > Preferences > Content > Languages ...
it seems this is for "Displaying Pages" not for Firefox Menus themselves 
I tryed putting: "about:config" in the address bar and looking at "general.useragent.locale"

But ! (still only English ?)
Not sure how to make it work ?
there must be a way?
**Thanks**
Ronok
[URL="http://www.gongkuo.com/linuxcli.htm"]
http://www.gongkuo.com/linuxcli.htm[/URL]

---

### Post by jasmineaura on 2010-11-18
Here's updated info for those struggling with getting additional language to work in swiftfox just like it does in standard firefox packages (provided you installed the appropriate language-support package(s)s for your language(s) and set your locale)

Start swiftfox, go to about version, to verify your version, then:
1. Go to [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/)
2. Click the version matching your version (say 3.6.12), or click "latest" if you know you're running latest version
3. Click "linux-i686"
4. Click "xpi"
after this step, you should end-up with a URL like this:
[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.12/linux-i686/xpi/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.12/linux-i686/xpi/)
(replace 3.6.12 with your version, or the word "latest" - symbolic  link to latest version/release)
5. Click the xpi file corresponding to your language code (in my case ar.xpi for Arabic)
6. SwiftFox will prompt you (yellow information bar) to allow installing it, so click "Allow"
7. Restart swiftfox and let your grandma enjoy surfing at ease :P

---

### Post by Ronok on 2010-12-14
Thank You: **jasmineaura** for your insight

[I marked my other thread about this topic as [solved]]("http://ubuntuforums.org/showthread.php?t=1598235")
Because after **Upgrading**

From Ubuntu **9.10** To Ubuntu **10.10**
&
From Firefox **3.6.10** To Firefox **3.6.13**

It Just Automatically Worked
"Multi Lingual" Really Truly

also thanks again for your insight 
[URL="http://www.gongkuo.com/linuxcli.htm"]Thanks
Ronok [/URL]

---

