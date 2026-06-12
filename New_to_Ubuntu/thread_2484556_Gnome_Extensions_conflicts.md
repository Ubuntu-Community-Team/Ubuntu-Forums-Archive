---
title: "Gnome Extensions conflicts?"
date: 2023-03-02
forum: New to Ubuntu
---

### Post by jdhhotbrown on 2023-03-02
Noob here - quick question. Is there any way to determine which extensions are safe together and which ones are more "iffy"? I have many installed and thought that since they are from Gnome they are all "safe".  Is there a list of known bugs or buggy extensions?

Thanks in advance for any and all thoughts.

---

### Post by DuckHook on 2023-03-02
Welcome to the forums, jdhhotbrown

Your post hijacked another thread which we discourage because that deprives both you and the OP of the individualized support that you both deserve. I've therefore split it off to its own thread under a more descriptive title.

*Thread moved to **New to Ubuntu** as the more appropriate forum.*

---

### Post by DuckHook on 2023-03-02
I don't think there is a single resource like these forums that is specific to Gnome extensions. I'm afraid the only way to do any detective work is to drill down from each extension to their github page (or wherever each extension is hosted) to read the dev's notes about any known conflicts. You can also do general websearches for such research. Aside from those, there's also your system logs.

I'm sounding like a broken recording, but, as a self&#8209;described noob, I urge you to keep your system as simple as possible. Departing from the defaults is a big reason that so many people run into intractable problems that require them to ask for help. Such problems are especially sticky because extension related problems are hard to diagnose.

[LIST=1]
[*]Why do you need so many extensions?
[*]Which are they? You can list them for us with:```
gnome-extensions list --enabled
```Please enclose the output in [noparse]```
your output here
```[/noparse] tags to preserve CLI formatting like my example above to allow for easier reading.
[/LIST]

---

### Post by jdhhotbrown on 2023-03-03
Thank you!

---

### Post by jdhhotbrown on 2023-03-03
I have disabled my extensions after reading more in these forums. I had gotten them just for fun, however I do understand now the inherent problems with them. Thanks all

---

### Post by DuckHook on 2023-03-03
There will come a point where you will be very comfortable with Ubuntu and can recover from even major breakage. At that point, you may find it acceptable to indulge in all sorts of customization again.

Speaking only for myself, I found that when I reached that point, operating a lean, mean, clean machine had become so ingrained in me that I actually preferred it, both practically and aesthetically.

---

