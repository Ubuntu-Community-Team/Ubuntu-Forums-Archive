---
title: "How-To: Install Mozilla Prism (Run Web Apps as Desktop Apps)"
date: 2007-11-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Espreon on 2007-11-15
OK if you were wondering what Mozilla Prims (often referred to as Prism), it is basically a way to run web apps next to desktop apps. Right now Prism is just a FF window with no location bar and no buttons, but in the future Mozilla is gonna add amazing things.

For more info on Prism go here: [http://labs.mozilla.com/2007/10/prism/](http://labs.mozilla.com/2007/10/prism/)

1. Fire up the terminal and enter this in it:

```

sudo wget http://people.mozilla.com/~mfinkle/prism/prism-0.8-linux.tar.bz2 -O /opt/prism.tar.bz2

```

2. Now enter this:

```

sudo tar -jxvf /opt/prism

```

3. Now lets create the menu entry:

a. Enter this in the terminal:

```

alacarte

```

b. In the Internet category create a new item:

For the command enter /opt/prism/prism

For name make it "Prism" of course (w/o quotes)

For the icon you can find  it in /opt/prism/xulrunner/icons (There is no Prism icon right now).

Enjoy!

If you want to be able to start web apps from the GNOME menu do the following:

1. Start Prism

2. Enter the info and check Create Shortcut on Desktop

3. View the shorcut's properties and look at the shortcut's command and copy it.

4. Create a menu entry for the web app and past the shortcut's command into the command line.

5. Enjoy starting your web app from the GNOME menu

To Uninstall:

Simply enter this command:

```

sudo rmdir /opt/prism

```

and then delete the menu entry.

---

### Post by panaretos22 on 2007-12-16
have you tried it?its ok or is on beta release? i read an article concerning to prisma ....looks nice ...is anybody willing to tell me if is ok to install it???

---

### Post by cwgpress on 2007-12-25
I tried it and it works great. Your tar command didn't work, though. So I just did a sudo nautilus, cd'd my way to opts, and double-clicked the prism tarball. I went up a level and extracted, then exited nautilus to get back on track.

Your alacarte trick is kewl!

Once Prism came up I created a special app for gmail. An icon was placed on the desktop and I dragged it to the top panel to make a launcher there. Works great. Thanks.:KS

---

### Post by airtonix on 2008-01-02
Prism? or firefox?

30sec load time or 30sec load time?

When prism can load the same pages in the same time as Opera....then i'll take it seriously.

Until then, its just xulrunner aka chromelss firefox, with the same laggy load time.

---

### Post by shifty2 on 2008-01-04
The only issue I had with this install was making it use proxy. I had assumed that it would either use my enviromental settings or have an easy interface (such as firefox) to change them, it didn't!

A bit of googling yielded the solution below:

We need to edit the /opt/prism/xulrunner/greprefs/all.js to tell prism to use a proxy:

```
gksudo gedit /opt/prism/xulrunner/greprefs/all.js
```

I then edited the part that originally looked something like this (found about halfway through the document):

```
pref("permissions.default.image",           1); // 1-Accept, 2-Deny, 3-dontAcceptForeign
pref("network.proxy.type",                  0);
pref("network.proxy.ftp",                   "");
pref("network.proxy.ftp_port",              0);
pref("network.proxy.gopher",                "");
pref("network.proxy.gopher_port",           0);
pref("network.proxy.http",                  "");
pref("network.proxy.http_port",             );
pref("network.proxy.ssl",                   "1");
pref("network.proxy.ssl_port",             );
pref("network.proxy.socks",                 "");
pref("network.proxy.socks_port",           800);
pref("network.proxy.socks_version",         5);
pref("network.proxy.socks_remote_dns",      false);
pref("network.proxy.no_proxies_on",         "localhost, 127.0.0.1");
pref("network.proxy.failover_timeout",      1800); // 30 minutes
pref("network.online",                      true); //online/offline
pref("network.cookie.cookieBehavior",       0); // 0-Accept, 1-dontAcceptForeign, 2-dontUse
pref("network.cookie.disableCookieForMailNews", true); // disable all cookies for mail
pref("network.cookie.lifetimePolicy",       0); // accept normally, 1-askBeforeAccepting, 2-acceptForSession,3-acceptForNDays
pref("network.cookie.alwaysAcceptSessionCookies", false);
pref("network.cookie.prefsMigrated",        false);
pref("network.cookie.lifetime.days",        90);
```

I then edited this line:
```
pref("network.proxy.type",                  0);
```
to
```
pref("network.proxy.type",                  1);
```

All that was left was then to fill my proxy into all the relevant fields, giving the section looking like this:

```
pref("permissions.default.image",           1); // 1-Accept, 2-Deny, 3-dontAcceptForeign
pref("network.proxy.type",                  1);
pref("network.proxy.ftp",                   "");
pref("network.proxy.ftp_port",              0);
pref("network.proxy.gopher",                "");
pref("network.proxy.gopher_port",           0);
pref("network.proxy.http",                  "192.168.2.1");
pref("network.proxy.http_port",             800);
pref("network.proxy.ssl",                   "192.168.2.1");
pref("network.proxy.ssl_port",              800);
pref("network.proxy.socks",                 "192.168.2.1");
pref("network.proxy.socks_port",            800);
pref("network.proxy.socks_version",         5);
pref("network.proxy.socks_remote_dns",      false);
pref("network.proxy.no_proxies_on",         "localhost, 127.0.0.1");
pref("network.proxy.failover_timeout",      1800); // 30 minutes
pref("network.online",                      true); //online/offline
pref("network.cookie.cookieBehavior",       0); // 0-Accept, 1-dontAcceptForeign, 2-dontUse
pref("network.cookie.disableCookieForMailNews", true); // disable all cookies for mail
pref("network.cookie.lifetimePolicy",       0); // accept normally, 1-askBeforeAccepting, 2-acceptForSession,3-acceptForNDays
pref("network.cookie.alwaysAcceptSessionCookies", false);
pref("network.cookie.prefsMigrated",        false);
pref("network.cookie.lifetime.days",        90);

```

et Voila! I have my proxy working with  prism. Added it to my start-up programs  with alltray in front of the command so it starts when i log in in the notification area. Very useful piece of software, cheers for the how to.

---

### Post by Espreon on 2008-01-07
> **airtonix said:**
> Prism? or firefox?

30sec load time or 30sec load time?

When prism can load the same pages in the same time as Opera....then i'll take it seriously.

Until then, its just xulrunner aka chromelss firefox, with the same laggy load time.

Well right now its just FF w/o the URL bar and other stuff, but it is what Mozilla is gonna do is the exciting part.

---

### Post by Gigamo on 2008-01-07
Thanks man. This worked except for the alacarte part, but all I needed was a GMail launcher in my xfce menu :)

---

### Post by Espreon on 2008-01-07
> **Gigamo said:**
> Thanks man. This worked except for the alacarte part, but all I needed was a GMail launcher in my xfce menu :)

The reason why the alacarte part did not work is because Alacarte is the GNOME Menu editor...
Oh and BTW, your welcome!

---

### Post by durand on 2008-01-08
Hmm....opera needs something like this....Maybe you can get this to preload when booting up so it loads straight away on the desktop.

PS: You can just use tar -xvf (no j)

EDIT: Just tried it, I'm confused. What exactly does it do that normal opera/firefox doesn't?

---

### Post by Espreon on 2008-01-08
> **durand said:**
> Hmm....opera needs something like this....Maybe you can get this to preload when booting up so it loads straight away on the desktop.

PS: You can just use tar -xvf (no j)

EDIT: Just tried it, I'm confused. What exactly does it do that normal opera/firefox doesn't?

Nothing yet... But it will do more in the future...

---

### Post by durand on 2008-01-09
ok..is it meant to be like active desktop in windows?

---

### Post by codfather on 2008-05-15
There is also an easier way to do this. Once you have installed Prism, click on Applications - Internet - Prism icon.

Now in the URL space type "about:config", and call it prism config.

Also click on the desktop button, so it places an icon on the desktop.

Like this --> [http://www.flickr.com/photos/swcodfather/2494317021/](http://www.flickr.com/photos/swcodfather/2494317021/)

When you click on OK, it will appear with a prompt which says
"I'll be careful I promise". Click on that button.

Like this --> [http://www.flickr.com/photos/swcodfather/2495125438/](http://www.flickr.com/photos/swcodfather/2495125438/)

In the filter box that appears type proxy and enter.

You can then alter the proxy/ssl proxy, proxy port and type as appropriate.

Like this --> [http://www.flickr.com/photos/swcodfather/2495098114/](http://www.flickr.com/photos/swcodfather/2495098114/)

Shut the windows and you will be good to go.

This was adapted from a post I found on a windows site, but works perfectly with Ubuntu.

Cod

---

