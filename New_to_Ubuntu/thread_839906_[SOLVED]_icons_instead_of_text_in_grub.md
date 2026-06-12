---
title: "[SOLVED] icons instead of text in grub?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by novatotal on 2008-06-24
to the moderators: if this is not the place, feel fre to move the thread.

I don't even know if this is posible; in google all I could find were references to qgrub editor or startup manager or gfxboot, and though the last one, does improve the aestetics off grub, thats not exactly what I want to do.
I would like to have, the icons of the diferent OS displayed instead of their names, and, upon doing click on the icon choosing wich OS starts.
thank you in advance for any help you provide.

---

### Post by tribble222 on 2008-06-24
I don't know if it's possible to have icons instead of text in your grub menu but I know it is possible to have a custom background instead of the default black.  Perhaps you could create a background graphic that places the OS logos next to the text.

Searching for something like "grub splash image" should get you details on how to do this.

---

### Post by Yuki_Nagato on 2008-06-24
-_-

The "clicking" part sounds as if it opens a new can of worms.

Clicking would imply that we have a GUI, and therefore, the X Window system installed, with either GNOME or KDE, or even a tiny, custom-job GUI filling in the template.

In short, it sounds like a load of memory usage.

If you just want the icons, without the clicking, then this might be possible.

---

### Post by novatotal on 2008-06-24
> **Yuki_Nagato said:**
> -_-

The "clicking" part sounds as if it opens a new can of worms.

Clicking would imply that we have a GUI, and therefore, the X Window system installed, with either GNOME or KDE, or even a tiny, custom-job GUI filling in the template.

In short, it sounds like a load of memory usage.

If you just want the icons, without the clicking, then this might be possible.

well if it has to be with the arrow keys it's ok, do you know how to do it?
pleace, pleace, pretty pleace tell me how!!!:)

my main idea is that, no text should be visible only the icons, and you could navigate beetwen them and chose the OS
with the arrow keys, with a click, anyhow but icons instead of text.
had the crazy idea of, pasting the icon directly on my menu.lst, but don't know if that is even posible or if it will work
and, since I have to try it on my machine first, and then, if it works, then install it on my mom's

---

### Post by imasickboy on 2008-06-24
You can replace GRUB with another bootloader, such as LILO, which I think, at one point, anyway, supported icons. It's been so long since I've used it, that I cannot say for certain that it is the case, but surely someone else will chime in and confirm this if it's indeed correct.

---

### Post by nowshining on 2008-06-24
menu.lst is a txt file.

---

### Post by novatotal on 2008-06-25
> **nowshining said:**
> menu.lst is a txt file.

that's why I said it was a crazy idea

any way in sourceforge found something called gag, seems like what I described earlier, only with numpad instead of clicks or arrow keys; it is a viruses nest in your first sector so forget it!!!
will try it in my mom's machine, if it does not break then I will post here the news.

funny mode/on
if by any chance I don't post anything in several days, it broke and you will be welcome to help me glue it together!!!:)
funny mode/off

they say it is OS independent, and from what I saw, you chose a number and the selected OS starts.
keep your fingers crossed!!!

---

### Post by novatotal on 2008-06-25
> **imasickboy said:**
> You can replace GRUB with another bootloader, such as LILO, which I think, at one point, anyway, supported icons. It's been so long since I've used it, that I cannot say for certain that it is the case, but surely someone else will chime in and confirm this if it's indeed correct.

thank you but, had enough trouble learning grub, and lilo I think is not in use anymore, don't know why and don't want to find out either.
any way seems that in sourceforge was the solution to my quest
again thank you very much, your time is precious and you gave some, and for that I can't thank you enough

---

### Post by nowshining on 2008-06-25
congrats. :)

---

### Post by novatotal on 2008-06-25
> **novatotal said:**
> thank you but, had enough trouble learning grub, and lilo I think is not in use anymore, don't know why and don't want to find out either.
any way seems that in sourceforge was the solution to my quest
again thank you very much, your time is precious and you gave some, and for that I can't thank you enough

in sourceforge you can find something called gag, it manages boot with the num pad and gives icons but; it installs in the first sector, and tells you that, if some day one Os starts by itself it is because ¡you have viruses in that same place so thanks but no thankyou gag!
I will stay with grub ugly as it may be

---

### Post by LuisBoyokan on 2012-09-22
you can use "Grub Customuzer" to edit your grub.
put an image with the icona and select the color of the text.
you can change the text to prevent it to be over the image.

---

