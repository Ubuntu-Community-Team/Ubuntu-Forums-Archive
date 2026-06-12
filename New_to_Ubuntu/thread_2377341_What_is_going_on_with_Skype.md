---
title: "What is going on with Skype?"
date: 2017-11-12
forum: New to Ubuntu
---

### Post by eliyahu22 on 2017-11-12
On all three my Ubuntu comps Skype started to act up at the same time.   Normally I get logged in automatically, and that is that.  Now, when Skype starts it asks me for my username and password, and when I fill that in it thinks a few seconds, and then closes itself.   

So I cannot use Skype any more on Ubuntu.  

On windows it still works normal.

---

### Post by DuckHook on 2017-11-12
I'm starting to sound like a broken record, but Skype is a Microsoft product, so it would be shocking if it *didn't* work on Windows. However, their Linux support has always been spotty&#8213;which is a rather generous way of putting it.

I don't use Skype for that and other reasons, so my input is of limited value. However, if all three of your computers suddenly developed the identical problem then it is entirely unlikely to be an Ubuntu issue and more likely either an account issue or a change that Skype has made to their server algorithm. In either case, your best bet is to start a ticket with Skype or enquire on their forums. The more Linux-heads complain to them, the more likely they are to take development of Skype for Linux seriously. Perhaps a forlorn hope, but it's the only chance I know of.

---

### Post by HermanAB on 2017-11-13
MS has made many changes to Skype over the years to complay with American snooping laws.  So it is not a distributed peer to peer system anymore and all call information passes through American servers.

So, try to upgrade Skype and if it doesn't work, change to Viber.

---

### Post by eliyahu22 on 2017-11-13
I seem to be unable to delete skype.  How do I do that?

I downloaded Viber for Debian, but I don't know how to install it.   Anybody any suggestions on that one?

---

### Post by DogMatix on 2017-11-13
> **eliyahu22 said:**
> 

... I downloaded Viber for Debian, but I don't know how to install it.   Anybody any suggestions on that one?

If you are running Ubuntu and got the viber.deb from the official Viber website's download page you should simply be able to right click on the downloaded file and select 'Open with Software Install' from the menu.

---

### Post by HermanAB on 2017-11-13
...or:
$ sudo apt install viberfilename.deb

and removing skype should be as simple as:
$ sudo apt remove skype

However, unscrambling an egg is sometimes not a good idea.  I never uninstall stuff, since it sometimes leaves the machine in a broken state and I don't want to take that risk.

---

### Post by monkeybrain20122 on 2017-11-14
What version of Skype and which Ubuntu? Skype 8.1.0.04 works fine here on  16.04, 17.10 and 18.04 developememtal.

There are many VOIP software, the problem is that you use them with other people, so it is no good that you switch to viber or something else while you can't move your contacts along. But if you can switch  [wire]("https://wire.com/en/download/") is open source and feature rich.

---

### Post by eliyahu22 on 2017-11-15
I tried to uninstall skype and got this:  $ sudo apt remove skype
```
[sudo] password for eliyahu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 chromium-browser-l10n : Depends: chromium-browser (>= 60.0.3112.113-0ubuntu0.16.04.1298) but it is not going to be installed
                         Depends: chromium-browser (< 60.0.3112.113-0ubuntu0.16.04.1298.1~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Is it deleted now?

My skype version is/was 4.3

How can I see my version of Ubuntu?

What I need is a VOIP with which I can call normal telephones, landlines.

> **HermanAB said:**
> ...or:
$ sudo apt install viberfilename.deb

and removing skype should be as simple as:
$ sudo apt remove skype

However, unscrambling an egg is sometimes not a good idea.  I never uninstall stuff, since it sometimes leaves the machine in a broken state and I don't want to take that risk.

After "$ sudo apt install viberfilename.deb" I get: Command not found.

---

### Post by howefield on 2017-11-15
> **eliyahu22 said:**
> .....How can I see my version of Ubuntu?

```
cat /etc/*-release
```

If it is a recent enough version of Ubuntu the apt install command should work but you will likely need to include the full path to the deb file.

---

### Post by ajgreeny on 2017-11-15
The package is jnow called **skypeforlinux**, not **skype** any more since the version 5.0 arrived, and now version 8.10.0.4 so the command *sudo apt-remove skype* will fail; try *sudo apt-remove skypeforlinux*

---

### Post by monkeybrain20122 on 2017-11-15
> **ajgreeny said:**
> The package is jnow called **skypeforlinux**, not **skype** any more since the version 5.0 arrived, and now version 8.10.0.4 so the command *sudo apt-remove skype* will fail; try *sudo apt-remove skypeforlinux*
He said he had skype 4.3 so it is not skypeforlinux and I suspect he might be on a unsupported version of Ubuntu as well.

---

### Post by ajgreeny on 2017-11-15
> **monkeybrain20122 said:**
> He said he had skype 4.3 so it is not skypeforlinux and I suspect he might be on a unsupported version of Ubuntu as well.
Ah! So he did, and that's why it will no longer work for him, I suspect.

---

### Post by eliyahu22 on 2017-11-15
> **ajgreeny said:**
> The package is jnow called **skypeforlinux**, not **skype** any more since the version 5.0 arrived, and now version 8.10.0.4 so the command *sudo apt-remove skype* will fail; try *sudo apt-remove skypeforlinux*

That command also doesn't work.

---

### Post by ajgreeny on 2017-11-15
> **eliyahu22 said:**
> That command also doesn't work.

No, sorry I missed your comment about still using, or trying to use, skype-4.3, which is no longer working according to users who still have it installed.

---

### Post by DuckHook on 2017-11-17
[LIST=1]
[*]Is it really necessary to uninstall Skype? Please note what HermanAB said about unscrambling an egg. If it does no harm except take up a bit of HDD space, then leave it be and ignore it.
[*]You will run into the same problem with Viber as you are currently wrestling with using Skype. It too is a proprietary app with its own opaque code, its own installation script and its own unconventional quirks. The next time it upgrades, it may very well leave you high and dry, just as Skype did.
[*]For new users, simple is better. To this end, you may wish to install Chromium, which is in the repos and does not require a third-party download. Once it is installed, you can then add the Google Hangouts web-app from within Chromium which will allow you to place land-line calls to anywhere in the the US or Canada for free. If you are in the US, you can even sign up for a US number which will allow others to call you, again for free. The advantage of this method is that you don't have to leave the safety of proven apps that are available in the repos. You can also uninstall them using conventional uninstall procedures that anyone can help you with. And because Hangouts is a web-app, installing/uninstalling it is also far simpler than what you are now wrestling with.
[*]
[/LIST]
From your questions, I assume that you are new to Linux. If so, I would advise that you read the link in my sig: Linux is Not Windows. This is a nice little blurb that informs new users of the cultural and therefore structural differences between Linux and Windows. These differences are important and help you to understand why installing third party apps is fraught with difficulties and dangers in the Linux-sphere.

Linux is a cool and rewarding universe, but it is also very different from the one you may be used to. Applying your old rules to this different universe will often get you into trouble here.

---

### Post by pissedoffdude on 2017-11-17
I'd recommend doing a purge of skype, clearing all settings (if your'e okay with that), and installing the latest one.
You can find skype and purge it through synaptic, or if you prefer a command line way, the following should do it:

1) Find out the name of your skype package:
```
dpkg -l|grep skype
```

should give you something like
```
ii  skypeforlinux                                                    8.10.0.4                                                   amd64        Skype keeps the world talking, for free.

```

2) Use above output to purge:
```
sudo apt purge skypeforlinux

```

3) Clear all your skype settings:
```
rm -rf ~/.config/skypeforlinux/

```

Note, you may have to adjust the above if your package isn't called skype for linux

4) Get the latest skype over at [https://www.skype.com/en/get-skype/]("https://www.skype.com/en/get-skype/").  Be sure to get the deb version

5) Double click and install, or if you prefer command line:
```
sudo dpkg -i skypeforlinux*.deb
```

---

### Post by ChuangTzu on 2017-11-21
> **DuckHook said:**
> I'm starting to sound like a broken record, but Skype is a Microsoft product, so it would be shocking if it *didn't* work on Windows. However, their Linux support has always been spotty&#8213;which is a rather generous way of putting it.

I don't use Skype for that and other reasons, so my input is of limited value. However, if all three of your computers suddenly developed the identical problem then it is entirely unlikely to be an Ubuntu issue and more likely either an account issue or a change that Skype has made to their server algorithm. In either case, your best bet is to start a ticket with Skype or enquire on their forums. The more Linux-heads complain to them, the more likely they are to take development of Skype for Linux seriously. Perhaps a forlorn hope, but it's the only chance I know of.

^ this is spot on.  

I would recommend alternatives to Skype: scroll down to Instant Messaging
[https://prism-break.org/en/categories/gnu-linux/](https://prism-break.org/en/categories/gnu-linux/)

---

