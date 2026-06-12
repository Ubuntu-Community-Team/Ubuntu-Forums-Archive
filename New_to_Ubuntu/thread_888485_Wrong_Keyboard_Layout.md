---
title: "Wrong Keyboard Layout?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by metasolaris on 2008-08-13
Hi

I think I have the wrong keyboard layout - possibly the US one rather than the UK one - because when i press the @ key i get " and vis versa.

How do I correct it?

Thanks
MeTa

---

### Post by Dill on 2008-08-13
Try going to **System** -> **Preferences** -> **Keyboard**, choose the "Layout" tab, and check out the options there. You might have luck with the "Reset to Defaults" button on the right side of that tab.

Cheers, 
Dylan

---

### Post by kaboodle_fish on 2008-08-13
Are you using the LiveCD because that defaults to the US keyboard and will reset back again each time you restart 
 
If you have installed Ubuntu then check to see if your localisation is correct. Unfortunately I am on a Windows machine at the moment so hopefully someone else can show you how.

---

### Post by metasolaris on 2008-08-13
I have installed Ubuntu on to PC.

Looked under KEYBOARD and only USA is listed as an option.

Any way of getting a UK layout?

---

### Post by Dill on 2008-08-13
Sure-- back in **System** -> **Preferences** -> **Keyboard** -> **Layouts** tab, click the button that says "Add" with a big plus sign next to it. You should see a new window pop up; on that window, click the drop-down menu next to "Layouts", scroll down to where it says "United Kingdom", and press the button that says "Add" again on the lower-right hand corner of the window. It should appear among the list with the USA layout, and you should be able to select the radio button next to the "United Kingdom" layout to change it. You may have to restart your system, but I bet it should work.

Cheers, 
Dylan

---

### Post by Mad-Halfling on 2008-08-13
In keyboard there is a Layouts tab, under the list of installed layouts there is an [Add] button, this will bring up a  list, UK is under there, that should sort you out

---

### Post by metasolaris on 2008-08-13
THANKS! Back to the British layout!

---

### Post by adam_kimber on 2008-08-22
> **Dill said:**
> It should appear among the list with the USA layout, and you should be able to select the radio button next to the "United Kingdom" layout to change it. You may have to restart your system, but I bet it should work

That worked for me too! However every time i restart it goes back to American. 

> **kaboodle_fish said:**
> If you have installed Ubuntu then check to see if your localisation is correct. 

Is this the reason why the keyboard layout changes back??

---

### Post by billgoldberg on 2008-08-22
> **adam_kimber said:**
> That worked for me too! However every time i restart it goes back to American. 



Is this the reason why the keyboard layout changes back??

Change you're xorg.conf file

```
sudo gedit /etc/X11/xorg.conf
```

In the first block of text you&#8217;ll see:

> Section &#8220;InputDevice&#8221;
Identifier &#8220;Generic Keyboard&#8221;
Driver &#8220;kbd&#8221;
Option &#8220;XkbRules&#8221; &#8220;xorg&#8221;
Option &#8220;XkbModel&#8221; &#8220;pc105&#8243;
Option &#8220;XkbLayout&#8221; &#8220;us"

Change that "us" to "gb".

I presume the correct keymap is "gb", it could be something else.

*(gb should be the uk layout)*

Then it will stay the same all the time.

---

### Post by adam_kimber on 2008-08-27
> **billgoldberg said:**
> Change you're xorg.conf file

```
sudo gedit /etc/X11/xorg.conf
```

Then it will stay the same all the time.

Unfortunately that does not work. The xorg.conf does not have any additional lines like yours, just the driver and the name "default". Adding the lines you have there makes the keyboard go nuts and the same with adding just Option &#8220;XkbLayout&#8221; &#8220;gb". From the logs X thinks my keyboard is a US layout which is silly. I have attached a screenshot of the characters that I get from when i add the following to my xorg.conf

Option &#8220;XkbRules&#8221; &#8220;xorg&#8221;
Option &#8220;XkbModel&#8221; &#8220;pc105&#8243;
Option &#8220;XkbLayout&#8221; &#8220;gb"

---

### Post by adam_kimber on 2008-09-09
Anyone got any suggestions? I am at a loss :(

---

### Post by adam_kimber on 2008-09-12
> **adam_kimber said:**
> Anyone got any suggestions? I am at a loss :(

Not any more. Sorted it. 
I backed up my xorg.conf. 
Ran sudo dkpg-reconfigure xserver-xorg to get my setup for my keyboard autodetected by the xorg setup program. 
It detected a 105 UK keyboard. 
I then copied the keyboard section from that xorg.conf into my backup, making sure the keyboard names matched in the server section and the keyboard device section. 
I got the same error as previously posted. So the above can be done by just adding lines to the xorg.conf
I then went to the gnome keyboard layout and clicked reset to defaults. This used to change it to a US layout but this time it went to a UK. 
Everything now works fine. :D

---

