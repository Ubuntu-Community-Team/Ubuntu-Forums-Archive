---
title: "Moving FF passwords from 7.10 to 8.04?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by laidback on 2008-07-10
Does anyone know how to move the logins and passwords that are present in my 7.10 over to a new installation of 8.04.1? e.g. my Ubuntu forum password, photo company log on and pswd which is saved in 7.10, online email etc. I reckon that they must be in a file somewhere. They're all coming up in FF in 7.10 so I'd like to simply move them over.

Many thanks and

Kindest Regards


Laidback

---

### Post by stchman on 2008-07-10
> **laidback said:**
> Does anyone know how to move the logins and passwords that are present in my 7.10 over to a new installation of 8.04.1? e.g. my Ubuntu forum password, photo company log on and pswd which is saved in 7.10, online email etc. I reckon that they must be in a file somewhere. They're all coming up in FF in 7.10 so I'd like to simply move them over.

Many thanks and

Kindest Regards


Laidback

You simply have to just log in to the each website and tell it to save the password.

---

### Post by aysiu on 2008-07-10
In /home/*username*/.mozilla/firefox/*profilename*, look for the *key3.db* file and the signon files as well (e.g. *signons2.txt*, *signons3.txt*).

---

### Post by laidback on 2008-07-10
ayiu 
Tried that, but the logins and pswds that would pop up in 7.10 don't appear. Perhaps there's another file that I need too?

---

### Post by Xerp on 2008-07-10
I use the firefox password saver addon.

[https://addons.mozilla.org/en-US/firefox/addon/2848](https://addons.mozilla.org/en-US/firefox/addon/2848)

---

### Post by cariboo on 2008-07-10
You can copy the complete .mozilla directory to your new home patition, That way all your settings, addons, bookmarks and passwords are the same. I also do this with .mozilla-thunderbird. If you don't have a separate home directory, back them up to an external drive, dvd or what have you and restore it before you use Firefox. You may have to edit .mozilla/firefox/profiles.ini

Jim

---

### Post by Dr Small on 2008-07-10
> **cariboo907 said:**
> You can copy the complete .mozilla directory to your new home patition, That way all your settings, addons, bookmarks and passwords are the same. I also do this with .mozilla-thunderbird. If you don't have a separate home directory, back them up to an external drive, dvd or what have you and restore it before you use Firefox. You may have to edit .mozilla/firefox/profiles.ini

Jim
+1
I was just going to suggest that.

---

### Post by bluepowder7 on 2008-07-10
the brute-force / manual way - view your log in names and passwords before the upgrade, save or print them out, and then visit the pages again when you've got 8.04 set up and re-enter all your details.  good to use this method when changing your habits from firefox to opera or some other browser.

---

### Post by laidback on 2008-07-11
Many thanks for all you replies..which of course sound very logical. 
I had been reluctant to move .mozilla over as the versions of FF are different and I suspected problems.
I did however move over bookmarks.html and all seemed well until I looked again at the ~/.mozilla/.../bookmarks.html file itself....just look at the attachment!

I have a bookmark file with the default list in it but an FF screen with all my original moved over bookmarks available!! what is going on?

I have FF v 3 in 8.4.1 and v2.xx in 7.10

I seem to either be very confused or have a very odd installation...perhaps both. It's certainly not working the way I expected.

I've yet to get back to the login/paswd issue as I got sidetracked by this oddity. (I have moved over the key.db and signon files, doesn't appear to work though)

Offers?

Many thanks

---

### Post by laidback on 2008-07-11
Xerp,

> **Xerp said:**
> I use the firefox password saver addon.

[https://addons.mozilla.org/en-US/firefox/addon/2848](https://addons.mozilla.org/en-US/firefox/addon/2848)

Thanks for this reference...looks interesting and useful.

---

