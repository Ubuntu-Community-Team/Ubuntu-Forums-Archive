---
title: "Where does the Gnome desktop background save its settings?"
date: 2006-08-26
forum: Programming Talk
---

### Post by daou on 2006-08-26
I'll repeat the title: Where does the Gnome desktop background utility in Ubuntu save it's preferences?

I like to use custom svg backgrounds with gradients as my wallpapers. If nothing similar exists and no one is interested in developing it, I'm planning to make a small program that changes the gradient of the background according to the time of day. For example, light colors during the morning and day, and then darker ones as night approaches.

I would just need to know where the gradient color settings are stored.

---

### Post by somnoliento on 2006-08-26
I think you need the Gconf file:

~/.gconf/desktop/gnome/background/%gconf.xml

You can modify it directly, or using the gconftool command line utility. Changes should be visible immediately.

---

### Post by daou on 2006-08-26
Exactly what I was looking for. Thanks.

---

### Post by Revert on 2006-08-26
I'd be interested in using that if you end up making it; sounds cool.

---

### Post by daou on 2006-08-26
I probably will. I just tested the bare bones structure I made for reading and setting the hex values from gconftools with a system command from C and it works. The background color updates after about a second. I will have to let it sit for a couple of days though, busy with other stuff.

---

### Post by X.Cyclop on 2006-08-26
Open a terminal and type:
```
gconf-editor
```

**/desktop/gnome/background** > **picture_filename** and its value is your wallpaper.;)

---

### Post by daou on 2006-08-27
> /desktop/gnome/background > picture_filename and its value is your wallpaper.

No changing backgrounds, just the gradient colors:

```

sprintf(command_buffer, "gconftool-2 --type string --set /desktop/gnome/background/secondary_color \"#%x\"",color);

system(command_buffer);
```

---

### Post by daou on 2006-09-06
> I'd be interested in using that if you end up making it; sounds cool.

If you are still interested, I got the program working and you can get it here:
[http://colorchain.wiki.com/]("http://colorchain.wiki.com/")

---

