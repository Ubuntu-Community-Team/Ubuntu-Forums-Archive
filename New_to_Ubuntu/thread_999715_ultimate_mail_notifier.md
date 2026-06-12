---
title: "ultimate mail notifier"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by Dbugger on 2008-12-02
Ok. I've been googling for ages but I cant find any mail notifier that can do all that follows:

1) tell me if I have MSN mail
2) If I have MSN mail and click, open the MSN web
3) tell me if I have Gmail mail
4) If I have Gmail mail and click, open the Gmail web

Does such thing exist?

Thank you

---

### Post by Her Ghost on 2008-12-02
Pidgin messenger can do this.

You need to set up both your MSN and Google Talk details and select the option in the settings of "Check For New Mail" (or something like that - sorry I'm not at my home PC so can't check exact wording.)

---

### Post by sydbat on 2008-12-02
Yes there is an option in Pidgin to check email from the IM accounts you set up. It is under Accounts > (specific account) > Edit Account > Advanced tab (at least on Pidgin 2.4.1).

---

### Post by Thanoulis on 2008-12-02
There is also an addon for Firefox called WebMail Notifier. Does exactly the stuff you want.

---

### Post by johnkzin on 2008-12-03
Is there one that will check against a gmail search, instead of merely looking at your gmail inbox?

For example, I mostly look at a search for "is:unread" instead of looking at my inbox.  I'd like a notifier for gmail that would tell me that I have new things in that search result, instead of telling me that I have new things in my inbox. (because not all of my unread mail goes into my inbox)

---

### Post by Dbugger on 2008-12-04
The problem of Pidgin is that it doesnt NOTIFY in the system tray of new emails.

---

### Post by kostkon on 2008-12-04
Try the [*Mail Notification*]("http://www.nongnu.org/mailnotify/") tray email notifier. It supports Hotmail and Gmail. It is one of the best email notifiers.

If you are using 8.04 you can download a more recent version from [*getdeb.net*]("http://www.getdeb.net/app/Mail+Notification"), since the one that is in the repositories is a little old. Download the .deb file and double-click on it to install it.

If you have 8.10 you are OK, just install it using *Synaptic* (the package is called [*mail-notification*]("http://packages.ubuntu.com/intrepid/mail-notification")).

Hope that helps.

---

### Post by Dbugger on 2008-12-05
The problem with "mail notifier" is that it doesnt open the web interface, but evolution.

---

### Post by zakhooi on 2008-12-19
> **Dbugger said:**
> The problem with "mail notifier" is that it doesnt open the web interface, but evolution.

The problem with mail-notifier is that it has turned off security (SSL) in the builds (so no IMAPS and POPS).
I only use IMAPS and POPS.
In the past someone repacked mail-notification with SSL enabled but that didn't work anymore as from Ubuntu 8.x

Maybe someone can write a decent and easy-to-use howto on how to rebuild mail-notification on ubuntu 8.x with SSL enabled.

---

