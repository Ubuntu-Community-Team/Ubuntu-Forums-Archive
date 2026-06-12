---
title: "how to remap keyboard ?"
date: 2017-10-22
forum: New to Ubuntu
---

### Post by photo-grapher on 2017-10-22
Hi,

i am new to linux (l)ubuntu, but everything works very very well so far with one exception, the keyboard layout. i am using a hp netbook 5103 and changed from w7 to lubuntu 17. Under windows i used a tool keyboard remapper to remap the keys. I have a gb keyboard layout, but with some extra keys and also i need to use some german "umlaute", for example  [ä]("https://de.wikipedia.org/wiki/%C3%84"), [ö]("https://de.wikipedia.org/wiki/%C3%96"), [ü]("https://de.wikipedia.org/wiki/%C3%9C") . Since i am new to ubuntu and not familiar on how to do such tasks, is there a graphical utility to do this or a step step guide ?

Thank you in adance for any help

---

### Post by ajgreeny on 2017-10-22
You may already have the character-map utility in your Accessories menu; it is in 16.04 Lubuntu so I imagine it's also in 17.04 and 17.10, but I still use the LTS versions, so have not seen Lubuntu 17.04 0r 17.10.

---

### Post by DuckHook on 2017-10-22
Welcome to the forums, photo-grapher.

I'm not sure what you are actually asking for. If you are looking for an actual German keyboard, then you must install a different keyboard layout. Instructions as follows: [https://help.ubuntu.com/community/Lubuntu/Keyboard](https://help.ubuntu.com/community/Lubuntu/Keyboard)

However, if you wish to use the English layout, but with an easy way to create non-English characters like accents and umlautes, then the best way is to assign a "compose" key which will display non-English characters after being invoked in combination with a character set. Example: <Compose Key> + <"> + <a> will yield ä. I can show you how to do that on Ubuntu Xenial, but unfortunately, I'm not knowledgeable enough to help on Lubuntu, although the link above might point to how to get Lubuntu to work.

For what it's worth, here is an old link instructing how to activate and assign the compose key in LXDE: [https://askubuntu.com/questions/73903/compose-key-in-lxde](https://askubuntu.com/questions/73903/compose-key-in-lxde) Once activated, you should be able to use the different key combos to create all sorts of special characters: [https://en.wikipedia.org/wiki/Compose_key#Common_compose_combinations](https://en.wikipedia.org/wiki/Compose_key#Common_compose_combinations)

**WARNING** The above is an old link, possibly obsolete, and untested by me. Moreover, manually tweaking keymaps is a very dangerous hack. A corrupted keymap will leave you unable to type anything into your session. This makes recovery incredibly difficult. Make sure all of your data is backed up before tinkering. Also, become familiar with booting from a LiveUSB and navigating into your main install to fix damage. Last, but not least, do not edit your keymap without making a backup of it so that you can recover elegantly in case of trouble.

If you use special characters infrequently, you may just wish to follow ajgreeny's advice and cut and paste from the character map when needed. It's much less risky, though admittedly also less convenient.

---

### Post by HermanAB on 2017-10-23
To completely change the keyboard mapping for a different language, you need to look at the region and accessibility setup.

If you only want to re-assign one or two keys, use xev and xmodmap.  

If you want keyboard macros, use Autokey.

---

### Post by photo-grapher on 2017-10-23
Thank you for the info.

Sorry if i did not exaxtly point out. What i want to do is to permanently assign shortcuts to the following keys > a/o/u, especially when pressing altgr+a = ä

Thank you in advance for further help

---

### Post by photo-grapher on 2017-10-23
Again, thank you all for help. I am now a step further after playing around with xmodmap. i found out that entering on the console the following command's will do the trick :

xmodmap -e "remove Lock = Caps_Lock"
xmodmap -e "keycode 38 = a A adiaeresis Adiaeresis"

But after rebooting the system the changes are gone. How can i permanently add this changes ?

Thank you in advance for further help

---

### Post by drs305 on 2017-10-23
I have some keys reassigned via xmodmap. I've placed them in a startup script that includes the following:
```

# Tab key
	xmodmap -e "keycode 82 = Tab"

```
You would need to make an executable script and then place it in a file referenced during startup.  From Dash, select "Startup Applications" and add the script or alter one that is already there.
Big Note: If you are using 17.10 and Wayland, I am not sure you are going to get xmodmap to work any longer...

---

### Post by photo-grapher on 2017-10-23
Well, i have put the commands in a file and execute it as needed. I need the special keys not every time so it is no problem to execute the script before using the keys.

Thank you all for your help

---

