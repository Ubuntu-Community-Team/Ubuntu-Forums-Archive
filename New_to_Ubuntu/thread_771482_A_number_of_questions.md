---
title: "A number of questions"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by lavadisco on 2008-04-27
Howdy, total newbie here. Loving Hardy Heron so far. Got a couple of questions. Should be easy for you guys.

[LIST]I have a drawer in one of my panels that has links to a few folders. How can I make it so that the name of each folder in that drawer is shown and not just the icons?
[/LIST]

[list]My panel icons appear to exhibit weird behavior when I try and drag them around into the positions I want. Not all icons on a panel seem to be draggable (mount drive, show desktop). Is there another way to do this?[/list]

[list]Regarding flash objects - Myspace doesn't play audio in Firefox. I get a message, in the playback box, saying "Error Loading XML Document". In general, on any site with a flash element, I get a giant play button. Once I click it, sometimes the flash movie works, but most of the time it doesn't and gives me an "undefined" error or just grey. How can I make it work all the time? And how can I set the default such that all flash elements play automatically? Another thing I have noticed is that my own swf files on the web lose their background transparency - can this be fixed?[/list]

[list]My soundcard works through my laptop speakers fine, but when I plug headphones in, the speakers turn off and no sound comes through the headphones. How can I fix this? I have a pretty generic Realtek HD soundcard.[/list]

There is more, but I think if I can get solutions to these problems I will gain a little familiarity that will allow me to fix those things... Thanks so much!

---

### Post by PhoenixP3K on 2008-04-27
Can't really help much concerning the panels and drawers as I don't really use them. But concerning the Flash problem you might need to re-install **flashplugin-nonfree**. More info is available on the webpage. If you have the right sources enabled you should be able to use the Synaptic packet manager to re-install it.

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

Concerning the soundcard, look up the settings in System (the one that says sound) perhaps the jack you're connecting your headphones to is not checked in the settings or is on mute.

---

### Post by mgmiller on 2008-04-27
In the items in your drawer, a description should appear on mouse over, if not, right click the item and left click properties.  Put some text in the Name: box.

To allow things to move around, right click the item and uncheck "Lock To Panel".  Then you can right click it and select move.  slide your mouse to where you want it and left click.  If you like, right click and select "Lock To Panel" to pin in there.

---

### Post by lavadisco on 2008-04-27
I would rather not have to mouse over all the icons in the drawer to find the one I want, I'd rather read it right away. Is there no way to do that?

I uninstalled swfdec-mozilla and reinstalled flashplugin-nonfree, and that seemed to fix the flash problem. All flash seems to work fine wherever I go now, however, a new phenomenon has popped up where certain pages with Flash cause Firefox to spontaneously close! For example, one of my own pages does this:

[http://www.mohodisco.com/explore/utah07.html](http://www.mohodisco.com/explore/utah07.html)

As soon as I type it into the address bar and go there, Firefox just disappears, and I have to reopen it. Not sure what is going on. It doesn't seem like the program is crashing, it looks more like it's minimizing, but once it does it the only way I can see Firefox again is to restart it.

---

