---
title: "Startup/Password Issues"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Inxi on 2008-11-24
After making a new user, I seem to be having some strange problems. I made a new user "public" through the newuser command, and I gave him a password through the passwd command. Then I changed my own password with this same command. It seemed to be OK until my internet disabled itself.

I restarted. A message came up, saying that some program, NetworkManager Applet, I believe, cannot access a keyring without permission. It asks for a password. My "new" password does not work, but the password I have changed from does. It asks this every time I restart the computer.

At first, the internet works. Then it crashes and asks me for the WEP key. I enter the key, it accepts it. Next time something happens to the connection (my own connection is a bit unstable due to wireless), it asks me the WEP key again. I believe this is something that I could automate.

Any way I can automate those two things so that they don't ask me for my passwords and keys every time something goes wrong?

This particular restart, it told me that it couldn't activate my keyboard or something of that sort. I clicked OK and my keyboard was fine. Not sure what that was.

---

### Post by The Cog on 2008-11-24
Under System->Preferences->Encryption and Keyrings - that's where you can change the keyring password to match your new login password. I don't know the details, but I'm sure it's in there somewhere.

---

### Post by Inxi on 2008-11-24
They keyring windows says this: 
Default Key: None. Promt for a key
I really don't want to screw anything up... and if there is no key there... what does that mean? It also has the "When encrypting, always include myself as recepient" that means what, exactly?

---

### Post by The Cog on 2008-11-24
Ah. I don't know. One problem with Ubuntu / gnome is the dire lack of documentation. I have never seen any documentation or links to documentation on this keyring thingy. There is this: [http://live.gnome.org/GnomeKeyring/KeyringIntro](http://live.gnome.org/GnomeKeyring/KeyringIntro) but it doesn't really help explain how to use or configure it.

---

### Post by Inxi on 2008-11-24
Documentation or not, I'm pretty sure someone has dealt with this.

---

### Post by Line on 2008-12-06
Hi!
A wise man spoke here:
[http://ubuntuforums.org/showthread.php?t=1003471]("http://ubuntuforums.org/showthread.php?t=1003471")

Hope you make it

---

