---
title: "Mail client with notification ?"
date: 2013-11-14
forum: New to Ubuntu
---

### Post by Niemil on 2013-11-14
Well, I got this Thunderbird but I don't understand much of it, it seems like I need to have it actually running in order to make it even work? It seems not be able to go into the Tray or?
I googled just some and finding "Mail notifications" that I thought were good, but I don't get this working also.
What's not working with the Mail notifications is that it seems not to load in any mails at all. I been clicking on "recieve all", and a popup came up, but it's all white with a cancel button. 

I have two mails, one on Gmail with my own domain name, and another on hotmail.
Using ubuntu 12.03.4 LTS 64-bit.

Any tips?

[edit]
I have also tested Gnubiff, but I really hated that software at first sight when it got installed, the icon were big and were covering over the activities area, covering exit button of browser and all.


I just want some notification software with a mail reader, so I can get notification asap when getting new mail on any of my two mail adresses. Then so I easy can read the mail and respond.
And that the icon is in tray or whatever named, so it's on all the time without me accidently quit it.

---

### Post by philinux on 2013-11-14
Maybe you need the package mail-notification to be installed.

---

### Post by buzzingrobot on 2013-11-14
I've used mail notification applets in the past, but I don't know if any are avilable for 12.04 and Unity.

These days, I just keep my mail client (currently Thunderbird) open on its own workspace. Whether it is a notification applet or a full-fledged mail client, both need to query your mail server to determine if you have new mail. The typical difference is that the applet doesn't download the new mail while the client usually does. (Clients can often be configured to download only the subject line from an IMAP server, pulling in the rest only if the user wants to.)

I have multiple accounts as well and forward all mail to one server, which simplifies things. That does mean I need to use a client that enables multiple identities.

---

### Post by Niemil on 2013-11-14
> **philinux said:**
> Maybe you need the package mail-notification to be installed.
Well, how is that done?
> **buzzingrobot said:**
> I've used mail notification applets in the past, but I don't know if any are avilable for 12.04 and Unity.

These days, I just keep my mail client (currently Thunderbird) open on its own workspace. Whether it is a notification applet or a full-fledged mail client, both need to query your mail server to determine if you have new mail. The typical difference is that the applet doesn't download the new mail while the client usually does. (Clients can often be configured to download only the subject line from an IMAP server, pulling in the rest only if the user wants to.)

I have multiple accounts as well and forward all mail to one server, which simplifies things. That does mean I need to use a client that enables multiple identities.
Ah, nice idea that aobut putting it in a single workspace, but does it then send you notifications if you're in another workspace?
Does it work to do that on startup of computer? because I really also want some mail client that starts up when computer starts.

---

### Post by philinux on 2013-11-14
> **Niemil said:**
> Well, how is that done?


Installing any package from a terminal.

```
sudo apt-get install packagename
```

Or search for a package in the software center.

(package = app = software)

---

### Post by buzzingrobot on 2013-11-14
> **Niemil said:**
> 
....does it then send you notifications if you're in another workspace?[/quote\

Yes, you see the standard popup notices.

[quote]Does it work to do that on startup of computer?

No.  It's a function of Thunderbird so Thunderbird needs be running. Any notification applet also needs to be running.  The difference is that the applets are configured to launch at startup. You could, I imagine, add Thunderbird to your list of startup applications. (I don't because I seldom reboot.) 

Notifications are more or less a standard feature of GUI-fied mail apps.

(The mail notification applet is available in Ubuntu's repos.  Search for "mail-notification" in Software Center or Synaptic, or use "sudo apt-get install mail-notification" in a terminal.)

---

### Post by nerdtron on 2013-11-15
You need to install an addon in Thunderbird for it to be able to stay on the system tray/notification area. I forgot the exact name of the addon I used but you can just search for "minimize to tray" it in the addon page. It will enable you to, well, minimize thunderbird to the tray area and show notifications.

---

### Post by Niemil on 2013-11-15
> **nerdtron said:**
> You need to install an addon in Thunderbird for it to be able to stay on the system tray/notification area. I forgot the exact name of the addon I used but you can just search for "minimize to tray" it in the addon page. It will enable you to, well, minimize thunderbird to the tray area and show notifications.
Yeah, I were actually googling for a few minutes ago and found one addon here: [https://addons.mozilla.org/sv-se/thunderbird/addon/firetray/](https://addons.mozilla.org/sv-se/thunderbird/addon/firetray/)
So now problem solved, this seems to work great :)

[edit]
If you're using cairo dock (or GLX dock as its named): [http://download.tuxfamily.org/glxdock/mediacolor/album8/1353108240_efb576ac5b/cairo_dock_unread_messages-1.0.2-tb-linux.xpi](http://download.tuxfamily.org/glxdock/mediacolor/album8/1353108240_efb576ac5b/cairo_dock_unread_messages-1.0.2-tb-linux.xpi)
This one will display undread messages below the thunderbird. May also be fun to have.

---

### Post by nerdtron on 2013-11-15
Good thing you sorted it out. Thanks to our friendly neighbor google. :)

---

