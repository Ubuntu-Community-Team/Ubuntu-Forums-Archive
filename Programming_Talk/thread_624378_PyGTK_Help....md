---
title: "PyGTK Help..."
date: 2007-11-26
forum: Programming Talk
---

### Post by NerdTv on 2007-11-26
Hi I am monkey banging on a keyboard trying to write my first python/gtk program, and am i need of some serious help. I built a simple program by combining some examples that I saw in a tutorial. The remote works, the poweron button opens vlc and the channels work but not the vol button (not yet), the problem I am having is the image i have on the power button power.gif is not displaying and i cant figure out why. I know it is simple but i can see it....
```
        image = gtk.Image()
	image.set_from_file("power.gif")
	image.show()
	button = gtk.Button()
	button.add(image)
        button.connect("clicked", self.poweron)
        table.attach(button, 0, 3, 8, 9)
        button.show()
```

The full code is here the problem is on line 159 - 167
[http://nerdtv.pastebin.com/m3557d4e5]("http://nerdtv.pastebin.com/m3557d4e5")

It just shows generic icon in place of the gif.
Thanks

---

### Post by QwertyManiac on 2007-12-02
Try a set_from_animation perhaps?

---

### Post by ssam on 2007-12-03
you could try calling show_all() on the window, rather than calling show for each widget, just incase you missed one

---

