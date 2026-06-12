---
title: "Guake: adjusting the width work-around"
date: 2010-08-06
forum: Outdated Tutorials &amp; Tips
---

### Post by rhigmus on 2010-08-06
Preface:  I was introduced to guake only a few days ago from reading this forum, while searching for a "wallpaper terminal". Its easy, smooth, and not nearly as customizable as I'd like. While I am aware of alternative quake like consoles that can do this easily enough, I prefer guake so the attempt had to be made. This is my first how-to so please be gentle with your criticism ;), I'm going to try to run through the steps I took.

To start I sought to see what, if any, possible config files Guake called to run, so:
```
ps ux | grep guake

2559  0.0  0.7 445716 31680 ?        Sl   08:45   0:01 guake -OO /usr/lib/guake/guake.py
2775  0.0  0.0   7620   892 pts/0    R+   09:43   0:00 grep --color=auto guake

```

Ah ha, Python script! I have marginal experience with python, but I've been tinkering with it lately in my conky conkfig, so I took a peek. As I was looking through this I find some interesting stuff between lines 785 - 810 in my copy:
```

def get_final_window_rect(self):
        """Gets the final size of the main window of guake. The height
        is the window_height property, width is window_width and the
        horizontal alignment is given by window_alignment.
        """
        screen = self.window.get_screen()
        height = self.client.get_int(KEY('/general/window_height'))
        **width = 100**
        **halignment = self.client.get_int(KEY('/general/window_halignment'))**

        # get the rectangle just from the first/default monitor in the
        # future we might create a field to select which monitor you
        # wanna use
        window_rect = screen.get_monitor_geometry(0)
        total_width = window_rect.width
        window_rect.height = window_rect.height * height / 100
        window_rect.width = window_rect.width * width / 100

        if width < total_width:
            if halignment == ALIGN_CENTER:
                window_rect.x = (total_width - window_rect.width) / 2
            elif halignment == ALIGN_LEFT:
                window_rect.x = 0
            elif halignment == ALIGN_RIGHT:
                window_rect.x = total_width - window_rect.width
        window_rect.y = 0
return window_rect


```

Now, I'm no expert in coding anything, but this appears to define window width and do some conditional alignment. Width appears to be accepted as a percentage here, adjusting mine to 80.

Make a backup before editing!
```
cp /usr/lib/guake/guake.py ~/guake.py.backup
```
Then gksu or sudo guake.py with your favorite editor and change the width to your preference. Its marked in bold in the above example. Might take a few attempts to get right, and decimals are accepted (eg. 83.5). Not sure you need to, but I stopped guake while editing this file just in case.

Then, depending on how you would like guake aligned on your screen, we change some of the alignment parameters. I want mine aligned to the left of the screen so conky is more visible. Directly below where we adjusted the width, "halignment" is defined (bold in above snippit, about line 790 for me), change it to your preference:
```

halignment = ALIGN_LEFT

```
ALIGN_RIGHT, and ALIGN_CENTER are also valid in this place

**EDIT: Figured out how to align window to the right! Simply use the above method. Feel pretty silly actually, I changed the width setting on a whim, but somehow never considered trying the halignment. Go fig! If you followed my previous method, either restore your original guake.py file or return the alignment settings in the IF statements to default **

But that's it! You should now be able to customize guake's width settings. Check the screen caps!

*Running Ubuntu 10.04 LTS x86_64 on my ASUS N61J-q laptop. Seems stable enough too, no aberrant behavior as yet. The guake preferences menu functions as expected in all respects, even the height adjustment slider (would have assumed my method broke it somehow, hehe).*

*Update: Successfully used this same method on my desktop pc running the same version of Ubuntu. Homemade pc with less generous specs and no problems whatsoever. Still working on adjusting alignment to the right though.*

---

### Post by jloveless on 2011-02-16
Absolutely amazing! This is exactly what I was looking for. The Linux community never fails to inspire awe.

Thanks so much!!

---

### Post by alSee on 2011-02-24
Thanks to **rhigmus**, I've found a more universal solution.
Actually there is the gconf key, called 'window_width', that is to control Guake width. But unfortunately its value is ignored. 
Well, changing the line (817 in my system):
```
width = 100
```
to:
```
width = self.client.get_int(KEY('/general/window_width'))
```
allows to tune Guake window on-the-go via gconf-editor.

Simply close Guake, apply the attached patch:
```
zcat guake_width.patch.gz | sudo patch -p0
```
and run Gauke again. 

Bingo! Now you can run gconf-editor, go to "/apps/guake/general" and change 2 parameters: "window_width" to set desired width (in per cent) and "window_halignment" to set desired alignment (0=center, 1=left, 2=right).

---

### Post by rhigmus on 2011-02-24
@ alSee

Fantastic solution!

Thanks :D

---

### Post by angel.ramirez.isea on 2011-05-07
Thank you! Just what I was looking for. Works in Arch with LXDE.

Thanks duckduckgo ;) hehe

---

