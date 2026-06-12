---
title: "Getting Facebook, Identica and Twitter in conky"
date: 2009-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by blizzkid on 2009-08-31
I have recently released version 0.1 of Cwibber.
Cwibber is an easy to use command line interface to Gwibber, which makes it easy to get (currently) Identica, Twitter and Facebook messages in your Conky.

First of all, add my ppa to your /etc/sources.list:

```
deb http://ppa.launchpad.net/mcielen/ppa/ubuntu [version] main 
deb-src http://ppa.launchpad.net/mcielen/ppa/ubuntu [version] main
```

Ofcourse subsitute [version] with intrepid, jaunty or karmic. Then add the PGP key:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0DA7F92B
```

Since Cwibber depends on Gwibber >= 2.0, add the Gwibber ppa:

```
deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu [version] main 
deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu [version] main

```

Again subsitute [version] with intrepid, jaunty or karmic. Add the PGP key:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3
```

And, as usual:

```
sudo apt-get update
```

Now you're ready to install Cwibber:

```
sudo apt-get install cwibber
```

Since Cwibber depends on Gwibber, it'll be installed too.

To use Cwibber 0.1, you'll have to run Gwibber to create the accounts you want to use, and run Gwibber once to start the Gwibber Daemon (this will be changed in Cwibber v0.2). Now call Cwibber from your .conkyrc:

${execi 60 cwibber}

**important:** before you can use cwibber you first have to authorize Gwibber through Facebook!

TODO for Cwibber 0.2:

- check whether Gwibber daemon is running, if not start it. For this I depend on the Gwibber developers, since refresh intervals will have to be stored in gconf. Developers promised this will be changed soon. (see [https://bugs.edge.launchpad.net/gwibber/+bug/417903](https://bugs.edge.launchpad.net/gwibber/+bug/417903))

- allow management of accounts through cwibber instead of through Gwibber

TODO for later versions:

- I'm hoping to convince Gwibber developers to split GUI and Daemon. If this won't happen, I might pack the gwibber daemon with Cwibber. (see [https://bugs.edge.launchpad.net/gwibber/+bug/421285](https://bugs.edge.launchpad.net/gwibber/+bug/421285))

**Call for developers and testers**

Test this app, and open an LP bug for any problem you find or features you want to see in next versions.

Since I'm far from a developer myself, I need help for this project. Interested in developing? Contact me through this forum or mail.

---

### Post by endemoniada on 2009-09-01
have just installed cwibber, but can`t seem to get it to work with Facebook enabled, when i tried running it from terminal i got

> ade@ade-laptop:~$ cwibber
FACEBOOK
Traceback (most recent call last):
  File "/usr/bin/cwibber", line 70, in <module>
    print "%s: %s %s" % (message["sender"], message["text"], remove_html_tags(message["extended_text"]))
KeyError: 'extended_text'
ade@ade-laptop:~$

However When I changed the > ct_fb = 2 # Facebook to > ct_fb = 0 # Facebook it works fine albeit with no Facebook messages

Any ideas on resolving this will be greatly appreciated as I`d like to get Facebook messages in conky (already have twitter & identica in conky setup)

---

### Post by 5m0k3 on 2009-09-02
Can we get a screenshot of this in action, per favore?

---

### Post by blizzkid on 2009-09-02
> **endemoniada said:**
> have just installed cwibber, but can`t seem to get it to work with Facebook enabled, when i tried running it from terminal i got



However When I changed the  to  it works fine albeit with no Facebook messages

Any ideas on resolving this will be greatly appreciated as I`d like to get Facebook messages in conky (already have twitter & identica in conky setup)

Have you allowed gwibber through Facebook? I'll add it as a step in the howto.

---

### Post by endemoniada on 2009-09-02
I already had Gwibber 2 running for a couple of days before i installed cwibber, so facebook & other protocols were already setup correctly. I have also tried removing cwibber, Gwibber & all my associated protocol settings & then reinstalled using apt-get install cwibber & run gwibber, added & authorized protocols (twitter,identica & facebook), but still no joy, unless I disable facebook access in /usr/bin/cwibber as mentioned in my previous post. Out of interest I am running Crunchbang 9.04.01, but being as a copy of this thread is also on the crunchbang forums, then I assume that it should work in Crunchbang too.

---

### Post by blizzkid on 2009-09-02
> **endemoniada said:**
> I already had Gwibber 2 running for a couple of days before i installed cwibber, so facebook & other protocols were already setup correctly. I have also tried removing cwibber, Gwibber & all my associated protocol settings & then reinstalled using apt-get install cwibber & run gwibber, added & authorized protocols (twitter,identica & facebook), but still no joy, unless I disable facebook access in /usr/bin/cwibber as mentioned in my previous post. Out of interest I am running Crunchbang 9.04.01, but being as a copy of this thread is also on the crunchbang forums, then it should work in Crunchbang too.

Could you do me a favor and open a bug in Launchpad? ([https://bugs.edge.launchpad.net/~cwibber/](https://bugs.edge.launchpad.net/~cwibber/))

Also, try running gwibber-daemon from terminal and then run cwibber from another terminal (remember to refresh (ctrl+r) once in gwibber first). You should now see some output from the daemon. Paste that in the bug too.

---

### Post by endemoniada on 2009-09-02
I`ll open a bug in launchpad when I`ve figured out how to do so & I`m less tired, thought you might like to know the results of running gwibber-daemon & cwibber from seperate terminals

Gwibber from Terminal results in > ade@ade-laptop:~$ gwibber
WARNING:root:desktopcouch is not available. .  falling back to gconf




nothing else appears, even when i refresh

cwibber from terminal still brings up > ade@ade-laptop:~$ cwibber
FACEBOOK
Traceback (most recent call last):
  File "/usr/bin/cwibber", line 70, in <module>
    print "%s: %s %s" % (message["sender"], message["text"], remove_html_tags(message["extended_text"]))
KeyError: 'extended_text'
ade@ade-laptop:~$ as previously reported

---

### Post by blizzkid on 2009-09-03
> **endemoniada said:**
> I`ll open a bug in launchpad when I`ve figured out how to do so & I`m less tired, thought you might like to know the results of running gwibber-daemon & cwibber from seperate terminals

Gwibber from Terminal results in 
nothing else appears, even when i refresh

cwibber from terminal still brings up  as previously reported

For now change:

```

print "%s: %s %s" % (message["sender"], message["text"], remove_html_tags(message["extended_text"]))
    if fb_cmt > 0:
      for comment in message["comments"]:
        print "  %s: %s" % (comment["sender"], comment["text"])

```

to:

```

print "%s: %s" % (message["sender"], message["text"])

```

(remove the three lines in the if-block).
Something seems to have changed since I wrote the script.

---

### Post by blizzkid on 2009-09-03
Facebook api has changed. Expect an updated version soon.

---

### Post by endemoniada on 2009-09-03
> **blizzkid said:**
> For now change:

```

print "%s: %s %s" % (message["sender"], message["text"], remove_html_tags(message["extended_text"]))
    if fb_cmt > 0:
      for comment in message["comments"]:
        print "  %s: %s" % (comment["sender"], comment["text"])

```

to:

```

print "%s: %s" % (message["sender"], message["text"])

```

(remove the three lines in the if-block).
Something seems to have changed since I wrote the script.

Excellent, that has solved the problem, everything works now, Thank you very much

My next query is, in conky some of the longer facebook messages are too long to fit on the screen, is it possible to get them to append to the next line instead? or is that a conky related issue?, obviously Twitter & Identi.ca messages are fine because of the limited amount of characters allowed

---

### Post by endemoniada on 2009-09-03
Here`s a Screenshot of my desktop with it running, along with my other conky`s and it also shows what i mean about facebook messages going offscreen

[[IMG]http://img300.imageshack.us/img300/3136/2009090312520144191280x.th.png[/IMG]](http://img300.imageshack.us/img300/3136/2009090312520144191280x.png/)

---

### Post by nilarimogard on 2009-09-04
Is it possible to click the links? Without this feature, for me at least it's useless since all those messages contain links...

---

### Post by blizzkid on 2009-09-07
> **nilarimogard said:**
> Is it possible to click the links? Without this feature, for me at least it's useless since all those messages contain links...

Clicking links is not possible (yet). Please open a whishlist bug for this in Launchpad.

---

### Post by blizzkid on 2009-09-07
> **endemoniada said:**
> Excellent, that has solved the problem, everything works now, Thank you very much

My next query is, in conky some of the longer facebook messages are too long to fit on the screen, is it possible to get them to append to the next line instead? or is that a conky related issue?, obviously Twitter & Identi.ca messages are fine because of the limited amount of characters allowed

Sorry for the late reply.
You can update gwibber to the latest version, and reinstall cwibber (or change the lines back to the original ones), and everything will work again.
Line wrapping is a conky issue, you can wrap it by adding | fold -swXX where XX is eg 31 (see man fold).

---

### Post by riktking on 2009-09-16
> **endemoniada said:**
> Here`s a Screenshot of my desktop with it running, along with my other conky`s and it also shows what i mean about facebook messages going offscreen

[[IMG]http://img300.imageshack.us/img300/3136/2009090312520144191280x.th.png[/IMG]](http://img300.imageshack.us/img300/3136/2009090312520144191280x.png/)

any chance of your .conkrc or whatever config your using? :D

---

