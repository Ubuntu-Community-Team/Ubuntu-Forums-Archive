---
title: "Getting Evolution to connect to Exchange"
date: 2006-06-28
forum: Outdated Tutorials &amp; Tips
---

### Post by ledonnell on 2006-06-28
A friend in the office (Gentoo user) figured out what is wrong with the current Evolutions and Exchange Connector.  He has submitted some code for a change and we will see if it takes effect.  I have not been able to connect for a LONG time now and I am pleased to say he walked me through how to get it working:

1.  Don't use the menu options for Evolution.

2. Open Gnome-Terminal (or Konsole if you are a heathen) and type: ximian-connector-setup-2.6.  Walk through your setup and let it close.

3.  Open Evolution and ignore the errors.  Go to Edit>Preferences>Accounts.  Edit your accounts.  Where the retarded Evolution bug has re-written your https to http change it BACK to https
*****************IMPORTANT******************
DO NOT click authenticate.  If you click authenticate it will rewrite your https settings again.
Just click ok.
Restart evolution.
You may have to tweak a few settings to your liking.

This has worked like a charm for all of us in the office and from my home connecting in.

Cheers.

---

### Post by nzgreen on 2006-07-28
I followed the instrutions on this webpage to add an Exchange account using the Evolution Druid:
[http://galaxycow.com/blogs/vermyndax/archive/2005/10/18/2380.aspx](http://galaxycow.com/blogs/vermyndax/archive/2005/10/18/2380.aspx)

---

### Post by btdown on 2006-07-28
> (or Konsole if you are a heathen)

Bravo!

---

