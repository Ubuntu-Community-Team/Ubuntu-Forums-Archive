---
title: "Flash: which package and why"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by oscillator on 2012-02-10
I'm wanting to download the latest flash player (11.1.102.55) and it gives the options of YUM, .tar.gz or .rpm downloads.
Which is better for 10.04 LTS or does it really make no difference which package i install?
Oh and is it better to install through the command line (if so, **how** would be nice!) ?

Cheers.

---

### Post by snowpine on 2012-02-10
Simply follow these easy instructions:

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by oscillator on 2012-02-10
Ah cheers should have checked that out before posting nevermind.

---

### Post by wolfen69 on 2012-02-10
Go to get.adobe.com/flashplayer/ and download the .tar.gz file. Right click it and *extract here*. Put the resulting *libflashplayer.so* file into ~/.mozilla/plugins (this means opening your home folder, doing Ctrl-H, and looking for your .mozilla folder. You might have to create the plugins folder. Restart firefox.
__________________

---

### Post by Cheesemill on 2012-02-10
> **wolfen69 said:**
> Go to get.adobe.com/flashplayer/ and download the .tar.gz file. Right click it and *extract here*. Put the resulting *libflashplayer.so* file into ~/.mozilla/plugins (this means opening your home folder, doing Ctrl-H, and looking for your .mozilla folder. You might have to create the plugins folder. Restart firefox.
__________________

The Flash-Aid plugin for Firefox takes care of all of this for you automatically.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by oscillator on 2012-02-10
Right, installing the ubuntu restricted extras package hasn't enabled me to listen to myspace radio (which is the only thing right now telling me I need to be using flash 11.1.102.55).
I've downloaded the tar.gz file, extracted it and moved it by the terminal to ~/.mozilla/plugins. Then like the lemon I am I've decided to read the rest of wolfen69's instructions, found .mozilla directory through the GUI, but when I go into this and click the file 'plugins' to check what I've done in the terminal, I get "Could not display "/home/oscillator/.mozilla/plugins" as theres apparently no app for opening shared library files. 
Now I'm trying to get to check it's gone there by 'cd .mozilla/plugins' and get 'bash: .mozilla/plugins: Permission denied' back. Yey.
Restart of Ff is pending.

---

### Post by oscillator on 2012-02-10
Right, myspace radio is now working (or rather buffering, and buffering...) so apparently the newest flash version was installed, but thanks for the advice anyway, and hopefully Flash-Aid will help in the future.

---

