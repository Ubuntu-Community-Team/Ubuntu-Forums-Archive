---
title: "Themes  .emerald"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by MasterCylinder on 2008-04-23
I have downloaded some .emerald themes, they imitate Aero. And what do I do with them? I have Compiz installed. I keep seeing something about 'Beryl' in google searches, but everytime I look for 'Beryl' with Synoptic or Add/Remove , or 

> sudo apt-get install beryl beryl-manager emerald-themes

I get nothing, besides a "There is no match available". 

I am really want the option of having a Aeroesque theme for my desktop.

Help? (Ubuntu noob, so go easy)

---

### Post by SunnyRabbiera on 2008-04-23
actually just install emerald, you dont need beryl.
Most beryl themes are emerald themes.
just install ememrald by using synaptic and search for emerald

---

### Post by Moop on 2008-04-23
Emerald is a window decorator and doesn't change your whole theme. Sometimes a theme is recomended to go with the emerald theme. Anyway...Install Emerald and the fusion-icon from Synaptic.

---

### Post by Tatty on 2008-04-23
```
sudo apt-get install emerald
```

---

### Post by SunnyRabbiera on 2008-04-23
> **Moop said:**
> Emerald is a window decorator and doesn't change your whole theme. Sometimes a theme is recomended to go with the emerald theme. Anyway...Install Emerald and the fusion-icon from Synaptic.

well if he is running hardy yes fusion icon is a good option, but gutsy doesnt have it.

---

### Post by rouge568 on 2008-04-23
Beryl is outdated, replace by the compiz/emerald combo.
To install an emerald theme, search for "emerald" _[here]("http://www.gnome-look.org/content/search.php")_ and pick your favorite. Then go to System>Preferences>Emerald Theme Manager. Click "import" and find the theme you downloaded. You're all set!

edit: and before you go setting your theme to Aero (though they do have it), I would look around for what is available. For example, _[here]("http://ubuntuforums.org/attachment.php?attachmentid=66256&d=1208465914")_ is my theme.

---

### Post by MasterCylinder on 2008-04-23
Hey thankyou so much for all the help!

I have Emerald installed... and I have the thing I want set up in it, how do I activeate it?

---

### Post by SunnyRabbiera on 2008-04-23
log out, then log back in.

---

### Post by Can+~ on 2008-04-23
> **MasterCylinder said:**
> Hey thankyou so much for all the help!

I have Emerald installed... and I have the thing I want set up in it, how do I activeate it?

Do a single click on one, and... First you need to replace Gnome's one, but before we do it permanent, try it:

```
emerald --replace
```

If it works, the theme selected should be applied, do Ctrl+C on the terminal to abort it.

If you stop having borders, then do this to get the default back:

```
metacity --replace
```

Now, to make it permanent, go to compiz fusion advanced yada yada, windows decorations, add the line, and reload compiz-fusion.

I have some issues with my graphic card, so I have a launcher with a "compiz --replace" on my desktop when I need to change a theme, or compiz breaks.

---

### Post by Vicfred on 2008-04-24
> **MasterCylinder said:**
> Hey thankyou so much for all the help!

I have Emerald installed... and I have the thing I want set up in it, how do I activeate it?

download Compiz Fusion Icon (look for it on synaptic), it's a very easy way.

---

### Post by Can+~ on 2008-04-24
> **Vicfred said:**
> download Compiz Fusion Icon (look for it on synaptic), it's a very easy way.

Oh man, I remembered why I hate that thing. I installed it, and overloaded my custom settings, luckily, I could go back to the previous one.

---

