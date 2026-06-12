---
title: "HOWTO: &quot;Downgrade&quot; Firefox 3b5 to Firefox 2 in Hardy"
date: 2008-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by hackle577 on 2008-04-27
A lot of people over in [ABT]("http://ubuntuforums.org/forumdisplay.php?f=326") are asking about downgrading Firefox 3b5 to Firefox 2 in Hardy because a lot of extensions and/or customizations don't work yet. Here's how:

[COLOR="Red"]FF3b5 = Firefox 3 Beta 5 (installed in Hardy by default)

FF2 = Firefox 2[/COLOR]

Tested on Ubuntu Hardy 64-bit.

=======================

[SIZE="4"]1.[/SIZE] Make a list of the extensions you want in FF2. Trying to "backport" extensions from FF3b5 to FF2 can get messy. Simply reinstalling them in FF2 is easier IMHO.

[SIZE="4"]2.[/SIZE] In terminal, type:

```
sudo apt-get purge firefox
```

This will uninstall FF3b5 from your system.

[SIZE="4"]3.[/SIZE] Wipe your FF3b5 profile with:

```
rm -r ~/.mozilla/firefox/
```

[SIZE="4"]4.[/SIZE] FF2 is still in the repos, so you can install it with a simple:

```
sudo apt-get install firefox-2
```

Done!

=======================

[SIZE="4"][COLOR="Red"]TO REVERT CHANGES[/COLOR][/SIZE]

To undo this process and install FF3b5 again:

```
sudo apt-get purge firefox-2
rm -r ~/.mozilla/firefox/
sudo apt-get install firefox
```

---

### Post by walkeraj on 2008-05-28
This did not work for me.  After following all of these steps, firefox 3 was installed again on my system.

---

### Post by PinkFloyd102489 on 2008-05-28
The "firefox" package is a meta-package that refers to the beta. Installing it will reinstall the beta.

Also, if you want to use any plugins for Firefox from the repo, it'll prompt you to reinstall the beta. Best bet is to either bite the bullet and go with the beta or install Swiftfox.

---

### Post by p0tw0r on 2008-06-16
What has worked for me was:

sudo apt-get purge firefox-3.0
rm -R ~/.mozilla/firefox
sudo apt-get install firefox-2
cd /usr/bin
ln -s firefox-2 firefox

WELCOME BACK TAB MIX PLUS!:)

---

### Post by GnuSense on 2008-06-18
Yep, Tab Mix Plus is the indispensable FF-2 extension for me.  I think I could handle the loss of the other extensions, but I HATE a scrolling tab bar and want a multi-row tab bar and don't know how to do that in FF-3.  

Seems like removing your profile is a bit of a nasty.  But strangely enough, once FF-3 has disabled incompatible extensions, you can not re-enable them in FF-2, AFAIK. Ill-behaved bleeding application. I really don't want to wipe my profile, reimport my bookmarks 7 reinstall all my extensions.  Any body figure out how to allow FF-2 to use your old extensions?

---

### Post by GnuSense on 2008-06-18
OK, I answered my own question.  You can delete or rename extensions.rdf in your profile and a new one will be regenerated when you start FF again, so you don't need to delete your old profile and reinstall. 

BTW, there is a beta version of TMP available that is supposed to work with FF-3, though I had to dig a tad to find it:

[http://tmp.garyr.net/tab_mix_plus-dev-build.xpi]("http://tmp.garyr.net/tab_mix_plus-dev-build.xpi")

---

