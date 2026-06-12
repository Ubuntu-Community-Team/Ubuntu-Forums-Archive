---
title: "Ubuntu(GRUB) 1.99 update problem"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by editheraven on 2011-10-04
I am trying to change colors when wallpaper for grub is available. When editing with /etc/default/grub and running sudo grub-mkconfig -o /boot/grub/grub.cfg grub.cfg is not updated with those settings.

What i am trying to set is this:

```
if background_image /editheraven/Pictures/grubwallpaper-129765.jpg; then
  set color_normal=white/black
  set color_highlight=dark-gray/white
```

But adding 

```
COLOR_NORMAL="white/black"
COLOR_HIGHLIGHT="dark-gray/white"
``` in default/grub does not update those lines. I have to edit them by hand wich i found kinda dangerous. Even so, after editing something else in default grub or a frontend gui for editing grub, after update, those 2 lines are set to default. How can i add them by not editing grub.cfg ?

---

### Post by ajsoulmate on 2011-10-04
Grub Customizer maybe?

---

### Post by drs305 on 2011-10-04
The lines to edit are generally in /etc/grub.d/05_debian_theme. If included in the proper section they will be incorporated when you run "sudo update-grub" and manual editing shouldn't be necessary.

Also remember to use the same case as contained in the original script.

Note: I'm a big fan of Grub Customizer. If it can do it, that would be the far easiest way to make the change. Even if it can't, GC is a great tool with many other Grub tweakings available and is worth installing.

---

### Post by editheraven on 2011-10-04
I tryied Grub Customizer before. Even when adding COLOR_NORMAL variables in advanced tab and updating grub, the lines after "if wallpaper present" are not updated. And i can't figure it out where in /etc/grub.d/05_debian_theme should i add those settings. I think this is the code block that needs to be edited but....

```
echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
    if [ -n "${2}" ]; then
        echo "  set color_normal=${2}"
    fi
    if [ -n "${3}" ]; then
        echo "  set color_highlight=${3}"
    fi
    if [ -z "${2}" ] && [ -z "${3}" ]; then
        echo "  true"
    fi
```

i hardly can understand bash. I think {2} and {3} are global variables or objects but that's all i can get...

---

### Post by ajsoulmate on 2011-10-04
> **drs305 said:**
> Note: I'm a big fan of Grub Customizer. If it can do it, that would be the far easiest way to make the change. Even if it can't, GC is a great tool with many other Grub tweakings available and is worth installing.

I did but everytime I try to change the color and the wallpaper, it does not save it :/


Ops, sorry to post on someone's else thread.

---

### Post by drs305 on 2011-10-04
> **editheraven said:**
> I tryied Grub Customizer before. Even when adding COLOR_NORMAL variables in advanced tab and updating grub, the lines after "if wallpaper present" are not updated. And i can't figure it out where in /etc/grub.d/05_debian_theme should i add those settings. I think this is the code block that needs to be edited but....

```
[B]echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
[/B]

    if [ -n "${2}" ]; then
        echo "  set color_normal=${2}"
    fi
    if [ -n "${3}" ]; then
        echo "  set color_highlight=${3}"
    fi
    if [ -z "${2}" ] && [ -z "${3}" ]; then
        echo "  true"
    fi
```

i hardly can understand bash. I think {2} and {3} are global variables or objects but that's all i can get...

The 05_debian_theme file has changed as Grub advanced from 1.96 through 1.99, but for you I think the solution will be to manually add lines just below what I highlighted in bold. 

Since Grub 2 is aware you are using a custom image but doesn't know what the color scheme of that image is, it tells Grub to use the default colors. To override them, add these additional lines below the existing line. Save the file, update Grub, and see if it works.

The effect you are going to have with the white/black black/white will be black menu items if non-selected, with the background image visible. The selected text should be black, with a solid white bar across the entire screen.

```
[B]echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
[COLOR="DarkRed"]echo "set menu_color_normal=white/black"
echo "set menu_color_highlight=black/white"
[/COLOR][/B]

    if [ -n "${2}" ]; then
        echo "  set color_normal=${2}"
    fi
    if [ -n "${3}" ]; then
        echo "  set color_highlight=${3}"
    fi
    if [ -z "${2}" ] && [ -z "${3}" ]; then
        echo "  true"
    fi
```

---

### Post by editheraven on 2011-10-04
Well, i finally edited like this and i got the same result as editing grub cfg by myself

```
echo "if background_image `make_system_path_relative_to_its_root "${1}"`; then"
                #echo "   set color_normal=white/black"
                #echo "   set color_highlight=dark-grey/white"
    if [ -n "${2}" ]; then
        #echo "  set color_normal=${2}"
                echo  "  set color_normal=white/black"

    fi
    if [ -n "${3}" ]; then
        #echo "  set color_highlight=${3}"
                echo  "  set color_highlight=dark-grey/white"
    fi
```Thanx for help. Marked as solved.



le : > **ajsoulmate said:**
> I did but everytime I try to change the color and the wallpaper, it does not save it :/.

Move your image to your root/home partition (in fact home is on root, but i'm referring to it as mountpoints). If the image is shown at boot time but the app doesn't load it it's maybe because that partition is not yet mounted.

---

