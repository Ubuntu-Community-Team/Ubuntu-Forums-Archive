---
title: "No system &gt; administrative menu after fresh install"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by showmemn on 2013-02-20
I have reinstalled Ubuntu at least 12 times, it's no joke! I keep doing  stupid things to mess up the sytem. One thing I have noticed is the want  of a System > Administration > menu. I have looked everywhere. I  just saw a post that said go to "System > Administration >  "Synaptic Package Manager"" but of course I couldn't. I even tried to  perform sudo apt-get install synaptic. What follows was the message I  received:

webmaster@sv1:~$ sudo apt-get install synaptic
[sudo] password for webmaster:
Reading package lists... Done
Building dependency tree
Reading state information... Done
synaptic is already the newest version.
The following packages were automatically installed and are no longer required:
   calligra-l10n-engb cdparanoia k3b k3b-data k3b-i18n kde-l10n-engb
   kde-l10n-zhcn kdevelop-l10n kdevelop-php-docs-l10n kdevelop-php-l10n
   language-pack-kde-en libk3b6 libkcddb4 linux-headers-3.5.0-15
   linux-headers-3.5.0-15-[INDENT]generic linux-headers-3.5.0-23
   linux-headers-3.5.0-23-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
webmaster@sv1:~$

Can you take five seconds to tell me what I'm missing. Thanks[/INDENT]

---

### Post by snowpine on 2013-02-20
You're almost there; now just type into the terminal:

```
gksu synaptic
```

or press Alt+F2 and type 

```
gksu synaptic
```

or if you are using the new Unity interface, tap the Windows/Super key and type 'synaptic'. 

Be careful following how to's and tutorials for older Ubuntu releases!

ps Depending what you are trying to accomplish, maybe you can also use the Ubuntu Software Center, which is preinstalled by default. It's a simpler point-and-click interface than Synaptic, very easy and user-friendly. :)

---

### Post by showmemn on 2013-02-20
Thanks. I have another question, don't know if I should post it in a new thread or not.
I need a WYSWYG HTML editor like Bluegriffon, but I don't know how and where to install new tar. files after I've downloaded them. Can you explain?

---

### Post by snowpine on 2013-02-20
In Ubuntu we don't typically download apps off the internet (this is the "Windows Way" and why most Windows users get crashes/malware) but rather we install tested & trusted apps from the Ubuntu Software Center. Think of it like the Apple App Store.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

One editor in the Software Center that is very popular is Bluefish; give it a try! :)

I'm sorry but I'm not familiar with Bluegriffon. If you can't find anything in the Software Center that meets your needs, then double-click on the .tar file to extract it (it's like a .zip in Windows) and look for a README or INSTALL file inside that explains what to do. :)

(edit) or read the Bluegriffon Users Manual which appears to contain instructions how to install on Ubuntu! ;)
[http://www.bluegriffon.com/index.php?pages/User-s-Manual](http://www.bluegriffon.com/index.php?pages/User-s-Manual)

---

