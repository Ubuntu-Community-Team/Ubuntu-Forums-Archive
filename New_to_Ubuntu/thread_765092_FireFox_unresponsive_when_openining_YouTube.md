---
title: "FireFox unresponsive when openining YouTube"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by GoCool on 2008-04-24
I installed the plugin DownloadHelper for downloading the youtube video, but after that when ever I open YouTube, it freezes up the entire system. Even mouse movement is not possible.

Did anyone else encounter this problem?
Any solution for this?

---

### Post by spiderbatdad on 2008-04-24
Are you using FF3 b5?
It's broken. Launchpad bug report suggests removing the file urlclassifer3.sqlite from the .mozilla/firefox/whatever.default folder in your home directory, and restarting firefox as a possible fix. I have switched to using SeaMonkey.

---

### Post by GoCool on 2008-04-24
> **spiderbatdad said:**
> Are you using FF3 b5?

No I am using Firefox 2.0.0.14

> urlclassifer3.sqlite from the .mozilla/firefox/whatever.default folder in your home directory, and restarting firefox as a possible fix.

I couldnt find this file. I even did a search on it. Sorry, but my linux skills is still in developing stage, so a little clarity could help me get through.

> I have switched to using SeaMonkey.
I am not finding it in Synaptic Manager.

Thank you once again atleast for responding to my query, it's highly appreciated.

---

### Post by philinux on 2008-04-24
> **GoCool said:**
> No I am using Firefox 2.0.0.14



I couldnt find this file. I even did a search on it. Sorry, but my linux skills is still in developing stage, so a little clarity could help me get through.


I am not finding it in Synaptic Manager.

Thank you once again atleast for responding to my query, it's highly appreciated.

The urlclassifier file is only used by firefox 3, it's a database for anti phishing and site forgery. But is causing firefox to use a lot of cpu. Hopefully a fix is on the way. For your problem is sounds like best not to use this addon or make sure you've got the latest version. Maybe report a bug to mozilla.

---

### Post by GoCool on 2008-04-24
Thank you for the quick response. Another noob question - I don't know how to uninstall a plugin? Will Synaptic show the plugin?

---

### Post by rlange on 2008-04-24
It is under the tools tab then add ons.

---

### Post by GoCool on 2008-04-25
> **rlange said:**
> It is under the tools tab then add ons.

Thank you.

---

