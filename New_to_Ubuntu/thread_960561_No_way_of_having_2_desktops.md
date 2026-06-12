---
title: "No way of having 2 desktops"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by belier on 2008-10-27
Hi.

I go to the desktop option of settings, I select two desktops but it doesn't appear. I'm stuck with just one desktop.

I have Compiz fusion installed and an NVidia 8800GTS with the hardware acceleration enabled.

Any suggestion?

Thanks in advance

---

### Post by GumboLinux on 2008-10-27
yea what you do is go to terminal and type in  ccsm

then go to general options > desktop size .> horizontal virtual size = whatever you wish      when set hold crtl + alt and press left/right arrow to change

---

### Post by Elfy on 2008-10-27
assuming that it's installed

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by GumboLinux on 2008-10-27
> **belier said:**
> Hi.

I go to the desktop option of settings, I select two desktops but it doesn't appear. I'm stuck with just one desktop.

I have Compiz fusion installed and an NVidia 8800GTS with the hardware acceleration enabled.

Any suggestion?

Thanks in advance

keyword i have compiz fusion installed >.>

---

### Post by dracayr on 2008-10-27
> **GumboLinux said:**
> keyword i have compiz fusion installed >.> having compiz installed isn't equal to having ccsm installed. By default, compiz is installed, but ccsm is not.

dracayr

---

### Post by philinux on 2008-10-27
Once installed there's no need to run ccsm from the terminal. It's in System>prefs>advanced desktop effects settings.

---

### Post by GumboLinux on 2008-10-27
> **philinux said:**
> Once installed there's no need to run ccsm from the terminal. It's in System>prefs>advanced desktop effects settings.

exactly -_-

---

### Post by blackened on 2008-10-27
You can enable the Workspace Switcher panel applet, right click on it, go to preferences and increase the "Rows" setting. This is also settable through gconf-editor.

Edit:
This is for KDE, just ignore me. :)

---

### Post by belier on 2008-10-27
Thanks to all that have replied.

Well. I've ccsm installed. Just the same as going to System->Prefs->advanced desktop effects settings. I've selected there Horizontal virtual Size = 2. Now the question is how to access second desktop. On the destop selector on right bottom corner I can only see one desktop. Or this is useless when using Compiz Fusion?

Thnks in advance

---

### Post by philinux on 2008-10-27
Desktop selector >right click then Edit Prefs.

---

### Post by belier on 2008-10-27
> **philinux said:**
> Desktop selector >right click then Edit Prefs.

I go to desktop settings, I select 2 desktops but still only one. :confused:

---

### Post by belier on 2008-10-27
What I've seen:

Using metacity or KWin I have two desktops. Using compiz just one, unless I select Kwin to have the 2 desktops and then going back to compiz... :(

---

