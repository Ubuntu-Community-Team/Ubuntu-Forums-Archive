---
title: "Seamonkey"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by adobrakic on 2008-05-26
I switched over to SeaMonkey, because of FireFox's memory leak. Everything went fine except for one thing. I can't install greasemonkey onto it. I tried from [here]("https://addons.mozilla.org/en-US/seamonkey/addon/748") and i get error-214. What can I do?

also, are there any other themes for seamonkey, other than classic and modern, cause be to honest they're not the best looking things.

---

### Post by bwhite82 on 2008-05-26
Only for the purposes of installing addons, run seamonkey with root privileges. Open a terminal:

> gksu seamonkey

Go back and attempt to reinstall the addon. Then close the browser and re open the normal way.

---

### Post by bwhite82 on 2008-05-26
[Themes]("https://addons.mozilla.org/en-US/seamonkey/browse/type:2/cat:all?sort=name")

---

### Post by spiderbatdad on 2008-05-26
You can google for seamonkey themes ( i like the modern theme) you can also google for extensions and addons by name if you dont find them in the addons page. 

If seamonkey is not installed in your home directory, you can launch seamonkey from the terminal with sudo seamonkey, then navigate to the extensions you want to install. This will give the installer root access to the files in which you wish to install the extensions.

Also you may need to make a change in about:config to prevent crashing while trying to save some file types from webpages. Type: about:config in the address bar and locate the line: > ui.allow-platform-filepickerToggle the value to false.

---

### Post by adobrakic on 2008-05-26
I'm still getting error-214 for both the gksu and sudo commands.
And for the themes, when i try to install them i get the error "install packages not found"
:/

---

### Post by spiderbatdad on 2008-05-26
There is a seamonkey irc.channel. They have great support. Did you install the iceape packages during you seamonkey install? If not, why not remove seamonkey through synaptic, then install all the iceape packages. Re-install all the seamonkey packages, then remove the iceape pakages.

---

### Post by adobrakic on 2008-05-26
no, i didnt install iceape at all. but i dont understand why install the iceape packages, if im going to remove them later?

---

### Post by spiderbatdad on 2008-05-26
see the details in synaptic by highlighting one of the iceape packages.

---

### Post by adobrakic on 2008-05-26
okay, thanks. ill try this now

---

### Post by adobrakic on 2008-05-26
I've done that, and it allowed me to install greasemonkey, though the themes didn't work, but I'm assuming thats the actual themes and not seamonkey.
Anyway, it said that greasemonkey was installed, but when i restarted seamonkey, i can't find greasemonkey anywhere here. i went to usescripts to see if any scripts work but they just download directly to my desktop, not seamonkey.

---

### Post by spiderbatdad on 2008-05-26
I have found their irc channel to be very friendly. Click "SeaMonkey Community" from the home page, then click the irc link.

---

