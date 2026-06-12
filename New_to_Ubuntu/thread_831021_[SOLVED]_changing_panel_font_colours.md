---
title: "[SOLVED] changing panel font colours"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by taith on 2008-06-16
lookign for a way to change font panel colours per item/panel...

having a background thats light on top, and dark on bottom (for example) would be nice to have a light/dark font on top, and a different light/dark on the bottom...

---

### Post by _sphinx_ on 2008-06-16
Once upon a time I was struggling with the same problem, I did work around but was not able to get it done. Also I was not the member of this community at that time. So, I was forced to change my background. I am looking forward if someone is able to get this this done.

---

### Post by rraj.be on 2008-06-16
you can do this by going to properties of the panel.

Just right click on any free space on panel and click properties.

You can get the required thing.

Further you can customize your desktop with lots of theams here.

```
[www.gnome-look.org/]("www.gnome-look.org/")
```

---

### Post by taith on 2008-06-16
in the panel properties, you can change the panel background... but you cant change the font colour...

---

### Post by y-lee on 2008-06-16
> you can do this by going to properties of the panel.

I'm running dapper and have no such options, but one can still do this by editing the gtk theme file ~/.gtkrc-2.0, creating it if necessary. See [Changing Gnome Panel font]("http://linuxtidbits.wordpress.com/2008/02/13/changing-gnome-panel-font-color/") :)

---

### Post by Golem XIV on 2008-06-16
```
sudo apt-get install gnome-color-chooser
```

---

### Post by taith on 2008-06-16
> **y-lee said:**
> I'm running dapper and have no such options, but one can still do this by editing the gtk theme file ~/.gtkrc-2.0, creating it if necessary. See [Changing Gnome Panel font]("http://linuxtidbits.wordpress.com/2008/02/13/changing-gnome-panel-font-color/") :)

true... but i want to be able to change the panel's font colour independantly of all the other panels (one white, one black for example)

---

### Post by rraj.be on 2008-06-16
Yes. editing the gtk theam file would be good option but i haven't done it before.

There are already lots of theams that are similar to your request are avilable in internet.

---

### Post by y-lee on 2008-06-16
> **Golem XIV said:**
> ```
sudo apt-get install gnome-color-chooser
```

+10 should work tho I don't use it. For more see [Gnome Panel Font Color Part Deux]("http://linuxtidbits.wordpress.com/2008/02/14/gnome-panel-font-color-part-deux/")

---

### Post by taith on 2008-06-16
> **Golem XIV said:**
> ```
sudo apt-get install gnome-color-chooser
```

works wonderful :P except its not panel independant...

---

### Post by y-lee on 2008-06-16
> **taith said:**
> works wonderful :P except its not panel independant...

Hmm you've given me something to ponder. May not be able to do it in gnome alone...I'd love to be wrong tho.

One thing you could do is use a non-gnome panel in combination with a gnome panel but that perhaps is not the best option.

---

### Post by taith on 2008-06-16
well... best option, would be to have it built into the panel properties... put another tab in for font(family, size, colour and effects(bold/italics/etc))... but i know it'd be FAR more difficult then that...

problem with the non gnome panel, is the functionality, and all the plugins that are built into the gnome panel...

---

### Post by y-lee on 2008-06-16
> **taith said:**
> well... best option, would be to have it built into the panel properties... put another tab in for font(family, size, colour and effects(bold/italics/etc))... but i know it'd be FAR more difficult then that...

problem with the non gnome panel, is the functionality, and all the plugins that are built into the gnome panel...


Agreed :) I haven't finished investigating this but for now I am busy doing things here around the house. You are right using a non-gnome panel would lose all the nice add to panel stuff. But the great thing about linux is for the most part you are free to modify the code. I haven't looked at the code for the gnome panels and it may be more hassle than it is worth, require a ton of changes or be in a language I know little about but there may be some solution  we have overlooked and some gnome guru will stumble thru here and know a reasonable answer. Who knows.

Barring that we can suggest to the gnome developers to add this feature to future versions of the gnome panel, they might actually listen.  The future is unknown ya know.

Peace.

---

### Post by kaibob on 2008-06-16
> **Golem XIV said:**
> ```
sudo apt-get install gnome-color-chooser
```

Thanks for the link. I'm an inveterate fidler, and I've been looking for an app like this for some time. I quickly learned that it's easy to get a pretty garish looking desktop, so a little restraint is needed, but I now have things pretty much like I want them. Thanks again.

---

### Post by Nighthawk4900 on 2009-05-19
this program is nice, but it doesnt change the color for a window seeking attention...  what is that even called? for example when a new IM comes in, i want the panel button for the IM window to blink, or change to bright orange or something... so that i can see that a new IM has come in...

---

