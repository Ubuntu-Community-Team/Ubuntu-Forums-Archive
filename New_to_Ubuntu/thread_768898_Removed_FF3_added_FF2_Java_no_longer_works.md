---
title: "Removed FF3 added FF2 Java no longer works"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Beatnikboy on 2008-04-26
I have searched in synaptic for all things java related and installed and uninstalled them one by one, inc Xubuntu extras, but still no Java.
Also typing "about: plugins" into the address bar shows that only flash is being picked up.
Any suggestions warmly received.

---

### Post by Beatnikboy on 2008-04-26
Bump, as I'm getting nowhere fast

---

### Post by nicedude on 2008-04-26
Add the medibuntu repository for hardy ( search here or google it ) and then go to synaptic and search for java and reinstall it. Also if FF3 is a pain for you uninstall it and reinstall FF2 in synaptic as well.

Here you go

Ubuntu 8.04 "Hardy Heron":

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

Then, add the GPG Key:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Do those two commands and then seach your synaptic

---

### Post by Google Spider on 2008-04-26
> **Beatnikboy said:**
> I have searched in synaptic 

Try this
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Beatnikboy on 2008-04-26
Apologises guys, I can see that my post wasn't clear.

I have already had java successfully installed whilst using Firefox 3.

I have uninstalled FF3 and deleted the home/.Mozilla/Firefox folder and installed FF2. 
Since doing this java no longer works.

I have tried installing/uninstalling the Xubuntu-restricted-extras and also the sun java 6 rte and anything else that looked likely to be useful. But still no java is working.

Also typing "about: plugins" into the address bar shows flash as the only plugin.

Many thanks for you interest and replies.

---

