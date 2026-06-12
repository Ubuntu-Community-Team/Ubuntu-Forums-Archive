---
title: "Chromium how to secure my data?"
date: 2011-08-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by opodaniel on 2011-08-13
I read some rumors that the 11.11 Ubuntu Oneiric will ditch Firefox for Chrome. Chrome is speedy, nice and dandy. Love the minimal interface, the speed, well if you used it you know what I am talking about. 
      Got a big problem thou. It got no master-password to secure my passwords. That means that If I want to let someone use my computer I absolutely, definitively have to chose between : switch to another account or have to start Firefox or Opera for my buddy in order for him/her to surf the net. 
One point is that someone could access my passwords, the other one is that someone could erase my passwords, since the access to the password is unrestricted. 
     Here you can find more info about this issue
[http://securemybrowser.blogspot.com/2010/10/chrome-unsafe-browser.html](http://securemybrowser.blogspot.com/2010/10/chrome-unsafe-browser.html)

     Here are some links where the problem is debated &#65306;
  [http://code.google.com/p/chromium/issues/detail?id=812](http://code.google.com/p/chromium/issues/detail?id=812)  
  [http://code.google.com/p/chromium/issues/detail?id=1397](http://code.google.com/p/chromium/issues/detail?id=1397)
  [http://code.google.com/p/chromium/issues/detail?id=27971](http://code.google.com/p/chromium/issues/detail?id=27971)
  [http://code.google.com/p/chromium/issues/detail?id=53](http://code.google.com/p/chromium/issues/detail?id=53)

     Since Google don't give a dime about users wishes, and needs is there a way to protect the passwords with the key-ring or to prevent them to be so easily available and erasable?

---

### Post by MacUntu on 2011-08-13
> **opodaniel said:**
> the other one is that someone could erase my passwords, since the access to the password is unrestricted.

That differs from Firefox how exactly?

```
$ rm -rf ~/.mozilla/firefox
```

There, Firefox passwords gone.

The only safe way is to create a guest account for guests.

---

### Post by opodaniel on 2011-08-13
Well I could approach this issues from the Hammer perspective ( a big hammer don't need any Linux command knowledge ;) ) in which case even the guest account won't brig you protection either :d.
So back on topic, how can I add an extra layer of protection to Chromium?

---

### Post by SevenMachines on 2011-08-13
Dont use chromium myself so dont know if this is default or what yet but you can store passwords in gnome keyring/kwallet
[http://groups.google.com/a/chromium.org/group/chromium-dev/browse_thread/thread/814d112acb8944c2](http://groups.google.com/a/chromium.org/group/chromium-dev/browse_thread/thread/814d112acb8944c2)

---

### Post by xebian on 2011-08-13
DON'T LET ANYONE USE YOUR COMPUTER BUT YOU if you are so paranoid.  Lock it in a vault.

Get your buddy a computer if he/she can't get one her/himself.:P

---

### Post by InphekD on 2011-08-13
One of the solutions is to use a plugin for Chrome called "LastPass".

---

### Post by bouncingwilf on 2011-08-13
sudo apt-get install firefox (or similar)

Bouncingwilf

---

### Post by opodaniel on 2011-08-13
@SevenMachines
Thanks a lot dude, you really made my day . I will give it a try.

> I've recently committed r50475 which adds a new flag, 
--password-store, that lets you request GNOME Keyring or (KDE) KWallet 
instead of the built-in unencrypted password store. 
There are three possible values: 
--password-store=gnome 
--password-store=kwallet 
--password-store=detect (this will eventually be the default) 
For now, without the flag, we will continue to use the built-in 
unencrypted store. With the flag, we will now try to use the requested 
store (or autodetect one, and use that) to store passwords, and we 
will migrate existing passwords to this store. This requires GNOME 
Keyring > 2.22 (which rules out Ubuntu 8.04) or KDE 4. In the event of 
failure to initialize the encrypted store, we fall back on the 
built-in store. 
If you'd like to give it a try, you might want to back up your 
existing password store, just in case something goes wrong. It's 
stored in ~/.config/chromium/Default/Login Data (or google-chrome for 
branded builds, once one of those includes this change). 

@others  very smart comments ... LOL.
Google Chrome is becoming stronger by day and in some places already taken the second spot. Linux is from my point a view a combination of simplicity and freedom packed in a strong Security Layer. I like Chromiuum but don't want to step away from that security layer I just mention.
Anyway this is great news Chrome is a safe browser when used in Linux :d.

---

### Post by SoFl W on 2011-08-13
Surely you can trust goog£e, they said they are not evil.

---

### Post by Mr. Picklesworth on 2011-08-14
> **SevenMachines said:**
> Dont use chromium myself so dont know if this is default or what yet but you can store passwords in gnome keyring/kwallet
[http://groups.google.com/a/chromium.org/group/chromium-dev/browse_thread/thread/814d112acb8944c2](http://groups.google.com/a/chromium.org/group/chromium-dev/browse_thread/thread/814d112acb8944c2)

That's a rather old post. The encrypted password storage stuff happens by default at this point.

> **opodaniel said:**
> I read some rumors that the 11.11 Ubuntu Oneiric will ditch Firefox for Chrome. Chrome is speedy, nice and dandy. Love the minimal interface, the speed, well if you used it you know what I am talking about. 
      Got a big problem thou. It got no master-password to secure my passwords. That means that If I want to let someone use my computer I absolutely, definitively have to chose between : switch to another account or have to start Firefox or Opera for my buddy in order for him/her to surf the net. 
One point is that someone could access my passwords, the other one is that someone could erase my passwords, since the access to the password is unrestricted. 
     Here you can find more info about this issue
[http://securemybrowser.blogspot.com/2010/10/chrome-unsafe-browser.html](http://securemybrowser.blogspot.com/2010/10/chrome-unsafe-browser.html)

     Here are some links where the problem is debated &#65306;
  [http://code.google.com/p/chromium/issues/detail?id=812](http://code.google.com/p/chromium/issues/detail?id=812)  
  [http://code.google.com/p/chromium/issues/detail?id=1397](http://code.google.com/p/chromium/issues/detail?id=1397)
  [http://code.google.com/p/chromium/issues/detail?id=27971](http://code.google.com/p/chromium/issues/detail?id=27971)
  [http://code.google.com/p/chromium/issues/detail?id=53](http://code.google.com/p/chromium/issues/detail?id=53)

     Since Google don't give a dime about users wishes, and needs is there a way to protect the passwords with the key-ring or to prevent them to be so easily available and erasable?

Yeah, since Chromium talks to the Gnome keyring daemon, it already goes through a master password. The problem you have is it gets unlocked when you log in.

What you can do here is lock your keyring. Head to Passwords and Encryption Keys (seahorse), right click the keyring and choose Lock. Now you'll need to type in the master password to unlock the keyring again and get at your passwords. There is no need to put that in the browser itself (actually, it would be harmful), since secure password storage is a desktop-wide problem to begin with.

---

### Post by jbicha on 2011-08-14
> **opodaniel said:**
> I read some rumors that the 11.11 Ubuntu Oneiric will ditch Firefox for Chrome.

Ubuntu 11.10 Oneiric will definitely still have Firefox as the default web browser. The final deadline for changing default apps passed last week but that wasn't planned for this cycle anyway.

My gut instinct is that Ubuntu will also keep Firefox as default for the LTS release next April. And it's too early to say for the release after that, 12.10.

For the default to become Chromium, a majority of the Desktop Team will have to be convinced that it is a better choice for Ubuntu.

Personally, I prefer Mozilla's philosophy and Firefox's tab management. I've heard that Chromium may be opening up more of the interface to extensions so the second issue may not be as significant in a year.

---

### Post by opodaniel on 2011-08-15
I also prefer Mozilla's philosophy and I kept away for sometime from Chromium, but lately I started using it again.. Damn it is quick and simple.

---

