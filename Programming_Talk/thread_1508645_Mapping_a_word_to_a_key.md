---
title: "Mapping a word to a key"
date: 2010-06-13
forum: Programming Talk
---

### Post by quentindemetz on 2010-06-13
Hello!

How can I map a word to a key ? I want to be able to press the "²" key (or any other key, or even a combination of keys such as Ctrl Atl A) and have it display "Hello World" in the active textbox (this must be system-wide!).

Thanks!

Quentin

---

### Post by trent.josephsen on 2010-06-13
Depends on what you mean by "system-wide".  If you just mean "application-independent", you could do that (I think) with Xmodmap or possibly with your window manager -- depending on what you use.  If you want it to work in virtual consoles as well as in X, there's a whole new can of worms to open.  If you want to apply it to all the users of a machine, I think you're out of luck.

---

### Post by rnerwein on 2010-06-14
> **quentindemetz said:**
> Hello!

How can I map a word to a key ? I want to be able to press the "²" key (or any other key, or even a combination of keys such as Ctrl Atl A) and have it display "Hello World" in the active textbox (this must be system-wide!).

Thanks!

Quentin
hi
try a script in /etc/profile with xmodmap - think that will work.
ciao

---

### Post by stylishpants on 2010-06-14
I do it this way.

I wrote a short shell script that accomplishes the typing by pasting from the X clipboard, using xclip and xvkbd (you'll need to install those packages from the ubuntu repositories.)

Then I used the gnome keyboard shortcuts tool (System->Preferences->Keyboard Shortcuts) to define a new custom keyboard shortcut, and use my shell script as the action.

```
#!/bin/bash

# Note:    You need 'xclip' and 'xvkbd' installed
xclip=/usr/bin/xclip
xvkbd=/usr/bin/xvkbd

# Check for required binaries
if [ ! -e "${xclip}" ]
then
	echo "xclip not found at expected location (${xclip})"
	exit 1
fi

if [ ! -e "${xvkbd}" ]
then
	echo "xvkbd not found at expected location (${xvkbd})"
	exit 1
fi

# Save current clipboard contents
$xclip -o | $xclip -i -selection secondary

# Put "ubuntu" in the clipboard
echo "ubuntu" | $xclip

# Paste from the clipboard into the current active window
$xvkbd -xsendevent -text "\[Shift_L]\[Insert]"

# Restore original clipboard contents
$xclip -o -selection secondary | $xclip -i

```

---

