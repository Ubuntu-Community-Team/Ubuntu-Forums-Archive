---
title: "Problem with keyring and google chrome"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by crobertsbmw on 2013-01-19
I have been getting this message with google chrome that "your profile could not be opened correctly". And none of my bookmark images showed up or anything. I did some searching and ended up completely uninstalling and re-installing google chrome and it seemed to be working fine. I then did a bunch of stuff and restarted my computer. When I got back on and launched chrome, I got a prompt that Default wanted a password for the keyring or something. I tried all my passwords and nothing worked. I ended up closing google chrome and exiting the keyring alert. I re-launched chrome and I then got the "your profile could not be opened correctly" message again with all the previous symptoms. I am now convinced the two problems are related. I tried searching on how to deal with this keyring problem and everywhere says to check the "available to all users" box in the network settings. Also I tried to do rm ~/.gnome2.keyrings/*keyring but apperently .gnome2/keyrings doesn't exist.

Any tips at all how to solve this problem?

---

### Post by cogier on 2013-01-19
I'm using Mint so there might be slight differences.

Press the "Super" key and look for an application with "Passwords" and/or "Keys". You should end up with a list of keys that you can delete.

Next time you are asked for a Keyring password just press [Enter] without putting anything in the textbox and accept the ...use unsafe password (or similar) dialogue box and that should solve that problem.

---

### Post by crobertsbmw on 2013-01-19
I opened up the key-passwords or whatever. It was completely empty...

[IMG]http://i68.photobucket.com/albums/i23/croberts_12/Screenshotfrom2013-01-19131341_zps5a86cc38.png[/IMG]

---

### Post by crobertsbmw on 2013-01-19
I clicked out of chrome and reopened it again, it again asked for my keyring stuff, and this time when I clicked cancel, it prompted me for a password. I left it blank and continued with unencrypted and it seems to work now. Thanks.

---

### Post by Paqman on 2013-01-19
I would try completely removing your profile, it sounds like it's messed up. As long as your bookmarks etc are synced to your Google Account you won't lose anything.

Close Chrome, delete or rename the folder ~/.config/google-chrome, start Chrome.

---

### Post by technologicme on 2013-01-21
> **crobertsbmw said:**
> I clicked out of chrome and reopened it again, it again asked for my keyring stuff, and this time when I clicked cancel, it prompted me for a password. I left it blank and continued with unencrypted and it seems to work now. Thanks.
When i downloaded google chrome it would not install so i deleted the file in downloads then i started to get that keyring password problem but i still can not ressole

---

