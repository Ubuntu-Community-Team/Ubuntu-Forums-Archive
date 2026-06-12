---
title: "avant window navigator"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by forcerecon808 on 2008-08-31
I recently installed awn on ubuntu from the repositories and it came with no applets. I read somewhere that that's because the awn in the ubuntu repositories isn't the complete version. If this is true, how do I uninstall the one I have now and install the complete version with applets. If it isn't true, what is? The only applets I need that I can't already get are "trash" and "show desktop" and I don't even know if they are included in the applets I don't have so, are they? I am computer retarded and have had ubuntu for about two days now so go easy on me. Thanks.

---

### Post by pfdevil on 2008-08-31
Hey do a google search for avant window navigator, you'll find a link to the wiki. Read through the FAQ and then you'll see a link where you can download the exstra applets. The Ubuntu repositories doesn't support these. Yes, there are applets for trash and show desktop.

---

### Post by nothingspecial on 2008-08-31
Go to system > administration > software sources.

Click the third party tab and add these 2 lines
```

deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

When you close the window it will ask you if you want to reload. Do it.

Then go to system > administration > synaptic package manager
Search for awn and mark any awn you have for complete removal.
Mark the new awn packages for instalation.

You can add a launcher to awn by right clicking on a something in your menus, say pidgin or soundjuicer and choosing add to desktop.
Create a folder in your home called launchers or something like that. Drag the new icon on your desktop into your new launchers folder and from there drag it onto your awn bar. Putting the launchers in a folder will save trhem so that they are on the bar every time you log in.

---

### Post by billgoldberg on 2008-08-31
> **forcerecon808 said:**
> I recently installed awn on ubuntu from the repositories and it came with no applets. I read somewhere that that's because the awn in the ubuntu repositories isn't the complete version. If this is true, how do I uninstall the one I have now and install the complete version with applets. If it isn't true, what is? The only applets I need that I can't already get are "trash" and "show desktop" and I don't even know if they are included in the applets I don't have so, are they? I am computer retarded and have had ubuntu for about two days now so go easy on me. Thanks.

Yes there are no applets in the default repo's.

You can add them, but why don't you give Cairo-Dock a try.

I find a better dock app.

[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

[IMG]http://linuxowns.files.wordpress.com/2008/05/cairo.png[/IMG]

---

### Post by forcerecon808 on 2008-08-31
> **nothingspecial said:**
> Go to system > administration > software sources.

Click the third party tab and add these 2 lines
```

deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

When you close the window it will ask you if you want to reload. Do it.

Then go to system > administration > synaptic package manager
Search for awn and mark any awn you have for complete removal.
Mark the new awn packages for instalation.

You can add a launcher to awn by right clicking on a something in your menus, say pidgin or soundjuicer and choosing add to desktop.
Create a folder in your home called launchers or something like that. Drag the new icon on your desktop into your new launchers folder and from there drag it onto your awn bar. Putting the launchers in a folder will save trhem so that they are on the bar every time you log in.

Thanks. Worked perfectly.

---

### Post by gjoellee on 2008-08-31
I will make it easy for you :)
[http://www.kshoster.net/?c=downloads_apturl](http://www.kshoster.net/?c=downloads_apturl)
just find AWN

---

