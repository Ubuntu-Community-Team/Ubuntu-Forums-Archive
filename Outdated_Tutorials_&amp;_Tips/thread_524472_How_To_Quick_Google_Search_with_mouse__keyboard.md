---
title: "How To: Quick Google Search with mouse / keyboard"
date: 2007-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by adam_r on 2007-08-13
Hi, This is somthing that took me a while to get, and eventually it was very simple,
this is a guide how to make google search with a shortcut key on [COLOR="Red"]selected text[/COLOR].

First thing:

```
sudo apt-get install xsel
```

second thing:

```
cd /ust/local/bin
pico google-search
```

and add this lines:
```
#!/bin/bash
firefox -search "`xsel -p -o`"
```
then save and of course:

```
chmod +x google-search
```

now you can test it, just select some text with the mouse, and run google-search.

now you can add a key shortcut to launch "google-search", i use compiz-fusion so i used "ccsm" to bind it.. but you can use also "gnome-keybinding-properties" or "xmodmaps".

there is also a KDE way to do this:
[http://www.howtogeek.com/howto/ubuntu/enable-google-search-from-shortcut-key-in-kde-on-kubuntu/]("http://www.howtogeek.com/howto/ubuntu/enable-google-search-from-shortcut-key-in-kde-on-kubuntu/")
havent tried it, i use gnome.. and i think my way will work on KDE too.

for those who have a LOGITECH mouse (or diffrent) with a "search" button on it (like i have, and why i did this in the first place) here is a link that explains how to activate the buttons:
[URL="http://andy.hillhome.org/blog/2006/09/27/logitech-mx-revolution-in-linux/"]
http://andy.hillhome.org/blog/2006/09/27/logitech-mx-revolution-in-linux/[/URL]

---

### Post by Whoopie on 2007-08-13
Thanks for this howto.

the following method could be used to assign a hotkey to the shell script. It's just an example. I didn't check if "<Ctrl><Alt>s" or "run_command_10" are already in use.

It's also discribed at [http://www.captain.at/howto-gnome-custom-hotkey-keyboard-shortcut.php]("http://www.captain.at/howto-gnome-custom-hotkey-keyboard-shortcut.php")

```

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_10 "<Ctrl><Alt>s"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_10 "google-search"

```

My google-search script looks like this (it opens the search results in a new tab):

```

cat /usr/local/bin/google-search 
#!/bin/bash
firefox -new-tab http://www.google.com/search?q=`xsel -p -o`&ie=UTF-8&oe=UTF-8

```

Best regards,
Whoopie

---

### Post by adam_r on 2007-08-14
that's a good way too, but dont forget the " " or it wont work on more then one word:

```
cat /usr/local/bin/google-search 
#!/bin/bash
firefox -new-tab http://www.google.com/search?q=**[COLOR="Red"]"[/COLOR]**`xsel -p -o`**[COLOR="Red"]"[/COLOR]**&ie=UTF-8&oe=UTF-8
```

---

### Post by adam_r on 2008-01-29
edit: upps wrong thread

---

