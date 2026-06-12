---
title: "On-screen notification of new Thunderbird email"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by soze on 2006-06-03
This is a silent (but effective) and quite cool way to get notified of your new Thunderbird email using an "on-screen" display.

(see attached screenshot for an example)

First, some prerequistites:

[LIST]
[*]You need to install the **xosd-bin** package.
[*]You need to download and install the *Mailbox Alert *Thunderbird extension. This can be found [here]("http://www.extensionsmirror.nl/index.php?showtopic=5128").
[/LIST]

Next create a file called ~/bin/newmail with the following:
```

#!/bin/bash
echo "You have new mail" | osd_cat -d 10 -i460 -o500 -f lucidasans-bold-24 -c green

```

Note: depending on the resolution of your monitor and your preference for the message position, you may want/need to tweek the -i and -o parameters.

After you save the file:
```

chmod a+x ~/bin/newmail

```

Now, go into Thunderbird, right-click on your inbox and select "Mailbox Alert".
Check "Execute a Command" and in the textbox to the right enter:
```

~/bin/newmail

```
Click ok and you are done!

As configured above, the message will appear on the screen for 10 seconds. You can adjust this time by tweeking the -d option in your ~/bin/newmail file.

Enjoy!

---

### Post by SaadN on 2006-06-03
Is it possible if you can post screenshot?

---

### Post by aysiu on 2006-06-03
I just use this Thunderbird extension:
[http://moztraybiff.mozdev.org/](http://moztraybiff.mozdev.org/)

But that's cool to know another way to do it.

---

### Post by soze on 2006-06-03
[QUOTE=SaadN]Is it possible if you can post screenshot?[/QUOTE]

Done!

---

### Post by brentoboy on 2006-06-04
aysiu,
is there a way to get that icon to persist after I close thunderbird?
I hate having thunderbird minimized all the time, I close it on accident, and then I have no notification.

---

### Post by aysiu on 2006-06-04
[QUOTE=brentoboy]aysiu,
is there a way to get that icon to persist after I close thunderbird?
I hate having thunderbird minimized all the time, I close it on accident, and then I have no notification.[/QUOTE] I don't think so--since the notification comes from Thunderbird itself. If the program is closed, it, by definition, can't operate.

I do think there are some notification programs that will notify you in the system tray (or through gDesklets) whether certain POP or IMAP folders have new messages (regardless of whether or not your email client is open). I'm not sure exactly how to use these, though, or which to recommend.

I'm not sure if this extension works for Linux, but you can also try [MinimizeToTray](https://addons.mozilla.org/thunderbird/2110/).

---

### Post by toorima on 2006-06-04
GKrellM if you use it can check mail and open your mailclient when you click on the notification part of gkrellm

---

### Post by Denta on 2006-06-04
kubuntu users can try the following:

```
kdialog  --msgbox 'You got new mail' -nograb --caption Thunderbird -title Information
```

kDialog is a very neat way of delivering information through scripts.

---

### Post by wh0rd on 2006-06-06
[QUOTE=brentoboy]aysiu,
is there a way to get that icon to persist after I close thunderbird?
I hate having thunderbird minimized all the time, I close it on accident, and then I have no notification.[/QUOTE]

[SIZE="4"]Y[/SIZE]ou can actually do this using the extension posted by **aysiu**:

> I just use this Thunderbird extension:
[http://moztraybiff.mozdev.org/](http://moztraybiff.mozdev.org/)

[SIZE="4"]A[/SIZE]fter installing the extension select the following in the **New Mail Icon** extension **Preferences**:
1. Show tray icon when new messages arrive
2. Always show tray icon (providing quick access to Thunderbird )

[SIZE="4"]T[/SIZE]hen just **right click** on the icon in the notificaiton area and click **Hide window**. It should stay in the notification area without being in the windows list.

---

### Post by snipe122 on 2006-06-06
I just use Ubuntus build-in email-notification... its simple and displays all necessary details of incoming mails in the tray...

greets
snipe

---

### Post by oyvindaa on 2006-06-06
soze:

This only works after I've opened Thunderbird.

Why is that?

---

### Post by wh0rd on 2006-06-07
Kubuntu, KDE users can use SuperKaramba with the Aero AIO plugin. It's got a new mail notification option:[B]
[http://www.kde-look.org/content/show.php?content=24626](http://www.kde-look.org/content/show.php?content=24626)[/B]

---

### Post by soze on 2006-06-07
[QUOTE=oyvindaa]soze:

This only works after I've opened Thunderbird.

Why is that?[/QUOTE]

It's because Thunderbird is performing the notification. 

What I do is keep Thunderbird running all the time and keep it minimized to a system tray icon using AllTray.

---

### Post by oyvindaa on 2006-06-07
[QUOTE=soze]It's because Thunderbird is performing the notification. 

What I do is keep Thunderbird running all the time and keep it minimized to a system tray icon using AllTray.[/QUOTE]

Oh right, thanks.

I'll have to try that then.

---

### Post by zeus77 on 2006-06-08
[QUOTE=snipe122]I just use Ubuntus build-in email-notification... its simple and displays all necessary details of incoming mails in the tray...

greets
snipe[/QUOTE]

Where do I find Ubuntu's built-in notification?  In Thunderbird, I have "Show an Alert" turned on in the preferences... but I get no notification in the tray.  I couldn't find anything in the Gnome panel config that looked relevant, either.  

Thanks for any help.

---

### Post by snipe122 on 2006-06-08
under system - preferences - email notification

or under synaptic: mail-notification

---

### Post by Zhukov on 2006-06-08
Maybe this is nicer (IMHO):

sudo apt-get install libnotify-bin

And then add this command to be executed when mail arrives:

/usr/bin/notify-send -i /usr/share/pixmaps/mozilla-thunderbird.xpm %sendername %subject


Sexy...

---

### Post by pchr on 2006-06-10
I use mail-notification.  Does just the job, I noticed since I've installed dapper (about 12 hours ago) the more limited sound dialogue no longer lets me add a sound for when mails come in.  I was pretty fond of that, has anyone got an idea what file needs to be tinkered with now that the gui for this has been removed?

---

### Post by snipe122 on 2006-06-10
it is possible to start a program when mail arrives... does anyone know how I play a sound via command-line?

---

### Post by Chrissss on 2006-06-10
[QUOTE=snipe122]it is possible to start a program when mail arrives... does anyone know how I play a sound via command-line?[/QUOTE]

Yep, just use aplay or mpg321 (you've got to install alsa-utils and mpg321)

# aplay /path/to/sound.wav
# mpg321 /path/to/soung.mp3

CU
 Christoph

---

### Post by rbalfour on 2006-06-16
Thanks!

Sweet mod..

---

### Post by LordRaiden on 2006-06-16
A very good KDE solution is Korn.

```
sudo apt-get install korn
```

It has visual alerts, docking, sound alerts, the ability to lauch an application on new mail. It can even (instead of having a mail received icon) tell you how much new mail you get.

---

### Post by cevans on 2006-06-16
A few points should be remembered about mail-notification:

[LIST=1]
[*]It is not by any means Ubuntu's built-in mail notification. In fact, it isn't even in main.
[*]Due to legal issues and stubbornness on both sides, the Debian maintainers have disabled SSL/TLS support, making it useless for many users without building it from source.
[/LIST]

---

### Post by bjtuna on 2007-02-27
> **cevans said:**
> A few points should be remembered about mail-notification:

[LIST=1]
[*]It is not by any means Ubuntu's built-in mail notification. In fact, it isn't even in main.
[*]Due to legal issues and stubbornness on both sides, the Debian maintainers have disabled SSL/TLS support, making it useless for many users without building it from source.
[/LIST]

Seriously? I guess that would explain why Mail Notification never worked for me.  Anyway since finding the moztraybiff extension my problems are solved -- because it's Thunderbird doing the notifying, I don't have to incur extra hits against my mail server, and it's nice and fast -- as soon as mail comes in, the icon is in my tray.

---

### Post by Sensenseppl on 2007-09-05
Hello!

I am currently writing a bash-script, which displays mail-information on the display of my logitech G15 when thunderbird receives a new mail.
I did this by installing the extension [“Mail Alert”]("http://addons.mozilla.org/de/thunderbird/addon/2610") to thunderbird. This extension allows me execute a script if a new mail is received.

My problem is that I need some plugin/tool/script that will inform me (or execute a script) if all the mails in the inbox (in all inboxes) of thunderbird are read, so that I can discard the displayed information if all new mails have been checked by the user.
Do you possibly know how I could do this?

Greetings,
Sensenseppl

---

### Post by woifi on 2007-09-05
Hi!

I use Mozilla Thunderbird 2.0.0.6 and it has such a feature built-in (you may know this from Windows). I got Thunderbird directly from mozilla.org, so it can co-exist with Thunderbird from Ubuntu repository.

bye

woifi

---

### Post by Sensenseppl on 2007-09-05
> **woifi said:**
> Hi!

I use Mozilla Thunderbird 2.0.0.6 and it has such a feature built-in (you may know this from Windows). I got Thunderbird directly from mozilla.org, so it can co-exist with Thunderbird from Ubuntu repository.

bye

woifi

Griaß di Woifal! ;)

Could you please be more specific about what exactly Thunderbird 2.0.0.6 has built-in in case you misunderstood me?

What I need are features that let me:
- execute a bash-script if a new mail is received
- execute a bah-script if all mails in all inboxes are read

I don't want a notification popup or something like that.

Greetings,
Sensenseppl

---

### Post by woifi on 2007-09-06
Servas Sensenseppl! :)

Oops, I guess I read over your post too fast. As all posts before deal just with simple notification I thought it would be nice to mention that Thunderbird 2.x already has such a feature. I'm sorry for that.

In the days of Breezy I used the moztraybiff extension (as mentioned on page 1 in this topic). This plugin shows a litte icon in the taskbar if a new email is received and when you read it, the icon is gone. You can do a little research and have a look at the source code. There has to be a little event or something - maybe you can use the knowledge for your own script.

hth, bye

woifi

---

### Post by Sensenseppl on 2007-09-27
Just in case someone has the same problem that I had:
The mail-notification in the Ubuntu repository has the feature to execute a script if new mail arrives (only once if there is new mail, not once per mail), and execute a script if all mail is read.

Sensenseppl

---

### Post by AhJah on 2007-10-24
I installed mail-notification via Synaptic, however the popup just flashes and disappears immediately.
Changing the timeout values seems to be useless. I also set it to "never expire" but without success.

Any hint?

TIA
Leo

---

### Post by macvr on 2008-09-16
i'm unable to install this>[http://moztraybiff.mozdev.org/releases.html]("http://moztraybiff.mozdev.org/releases.html")

tried version 1.2.4 from the .xpi and got incompatibility error that my system is LINUX x86-gcc3 !!!
which is the version i have to  install?

or does the synaptic mail-notification work with thunderbird??

---

### Post by Cris(c) on 2008-09-17
> **macvr said:**
> i'm unable to install this>[http://moztraybiff.mozdev.org/releases.html]("http://moztraybiff.mozdev.org/releases.html")

tried version 1.2.4 from the .xpi and got incompatibility error that my system is LINUX x86-gcc3 !!!
which is the version i have to  install?

or does the synaptic mail-notification work with thunderbird??

Mail notification should work just fine unless you need ssl/tsl support. In that case, check this [ post]("http://ubuntuforums.org/showthread.php?t=589115") to enable support for these. If you are going for ssl support make sure that aside from the packages the how-to will indicate to download, you have build-essential; gnome-core-devel; libnotify-dev; libgnome2-dev and libgmime-2.0-2-dev (these are the dependencies I found out are need after some trial and error process) packages. With these, everything should go ok.

Hope it helps,

Cris.

---

### Post by dryicebomb on 2009-03-25
> **aysiu said:**
> I just use this Thunderbird extension:
[http://moztraybiff.mozdev.org/](http://moztraybiff.mozdev.org/)

But that's cool to know another way to do it.

I also use this, it works awesome for me.

---

### Post by timetourist on 2009-05-30
With this Thunderbird-Addon you can make use of Ubuntu Jaunty's new Notification System: 
[https://addons.mozilla.org/de/thunderbird/addon/11530](https://addons.mozilla.org/de/thunderbird/addon/11530)

---

### Post by khughitt on 2009-07-08
Anyone know if it's possible to setup the New Mail Icon plugin so that when you hit "close" on Thunderbird, it simply minimizes to the system tray?

Right now I can click on the icon in the tray to hide Thunderbird, but this isn't the most intuitive way to do this.

---

