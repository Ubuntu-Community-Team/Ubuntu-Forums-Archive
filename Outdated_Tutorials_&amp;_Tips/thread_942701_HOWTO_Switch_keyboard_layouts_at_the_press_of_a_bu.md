---
title: "HOWTO: Switch keyboard layouts at the press of a button"
date: 2008-10-09
forum: Outdated Tutorials &amp; Tips
---

### Post by cleverselfreferentialname on 2008-10-09
For quick switching between keyboard layouts, I've remapped the caps_lock button. Reasons you might want to do this include having to write international characters, or two use different layouts entirely.

To disable caps lock, add the following to your .Xmodmap:

```
remove Lock = Caps_Lock
```

Install xbindkeys:

```
sudo apt-get install xbindkeys
```

Create a default .xbindkeysrc file:

```
xbindkeys --default > .xbindkeysrc
```

Then create a script to the form of the following and save it.

```

#!/bin/bash

if setxkbmap -print|grep symbols|grep -q us;then
  setxkbmap -model pc104 -layout in
  exit 0
elif setxkbmap -print|grep symbols|grep -q in;then
  setxkbmap -model pc104 -layout us
  exit 0
fi
exit 0

```

I named mine switcher.sh. This one switches between my default layout - us - and another I use occasionally - in. Check /usr/share/X11/xkb/symbols/ before switching the country codes to something else. If us is your keyboard layout, it *has* to remain in the script.

Move it to /usr/bin so it's in your $PATH, and make it executable:

```

sudo mv switcher.sh /usr/bin/switcher.sh
sudo chown root:root /usr/bin/switcher.sh
sudo chmod +x /usr/bin/switcher.sh

```

Now add the following to your .xbindkeysrc to make pressing a the key execute the script:

```

"/usr/bin/switcher.sh"
 Caps_Lock

```

You should be able to add it anywhere as long as it's above that 'End of xbindkeys configuration' line and the hash marks around it.

That little indentation before Caps_Lock is supposed to be there. 

You'll need to make the following execute on X start:

```

xmodmap .Xmodmap
xbindkeys

```

You can add them to your .xinitrc (I'm on openbox, it hasn't worked for me - I think it's because I haven't chmod +x'd it yet) or use a method specific to your desktop environment.

If anyone has those methods, they're welcome to post them as addendums and I'll quote them by editing this post.

Thanks, and good luck.

---

