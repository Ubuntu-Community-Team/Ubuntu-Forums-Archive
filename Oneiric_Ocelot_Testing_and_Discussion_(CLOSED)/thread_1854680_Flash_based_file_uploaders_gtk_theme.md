---
title: "Flash based file uploaders gtk theme?"
date: 2011-10-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by zmbmartin on 2011-10-04
This may seem small but I still thought I would ask anyways. When I use a flash based file uploader like uploadify the select a file browser that pops up does not follow my gtk theme. It is a standard ugly looking gtk theme. How can I get this to follow my current theme.

[http://imageshack.us/f/28/screenshotat20111004183.png/](http://imageshack.us/f/28/screenshotat20111004183.png/)

Thanks

---

### Post by Krytarik on 2011-10-04
Honestly, I'm a bit stumped, by this particular constellation! As the file upload dialog you are seeing is just the usual GTK file picker - even if invoked by a flash uploader, everything always ends up there. So, this has nothing to do with flash or the respective website at all, even not with the web browser.

Currently, there is a common bug that involves "gnome-settings-daemon" and makes indeed the theme revert to the fallback theme, but if you were affected by those, the theming would be reverted for every other parts of your desktop, too; meaning including your web browser, which - I can see that in the screenshot, and you would be telling otherwise - is not the case.

So, some questions:

[LIST]
[*]If you go to "File -> Open File", the dialog should look the same, right?
[*]Are any other apps/dialogs affected, too?
[*]What theme are you using - looks like the default "Ambiance" theme, right?
[*]Did you change anything in your system reg. themes, or GTK, Gnome 3 maybe?
[*]Reg. the latter, what version of Ubuntu are you running, actually?
[/LIST]

---

### Post by zmbmartin on 2011-10-04
If you go to "File -> Open File", the dialog should look the same, right?
[INDENT]Yes it follows suit with the theme that I have.[/INDENT]
Are any other apps/dialogs affected, too?
[INDENT]None that I know of or have seen.[/INDENT]
What theme are you using - looks like the default "Ambiance" theme, right?
Did you change 
[INDENT]It is just the default.[/INDENT]
anything in your system reg. themes, or GTK, Gnome 3 maybe?
[INDENT]I did come over from archlinux with the same /home but I thought that I deleted all relevent config files related to gnome. I should check that I guess. Any particular files I should look to delete?[/INDENT]
Reg. the latter, what version of Ubuntu are you running, actually?
[INDENT]I am using Ubuntu 11.10[/INDENT]

---

### Post by Krytarik on 2011-10-04
> **zmbmartin said:**
> If you go to "File -> Open File", the dialog should look the same, right?[INDENT]Yes it follows suit with the theme that I have.[/INDENT]
Actually, I was meaning it the other way around, as this is the very same GTK file picker dialog. Well, at least it should be. :p

How about the dialog that comes up if you run this in the Terminal?:
```
zenity --file-selection
```> **zmbmartin said:**
> I did come over from archlinux with the same /home but I thought that I deleted all relevent config files related to gnome. I should check that I guess. Any particular files I should look to delete?
I take that Arch Linux uses the rolling release model, and by now - it seems - you can opt for both Gnome 2 or 3, thus also GTK+ 2 or 3, eventually. Do you know what version of Gnome you were running?

Depending on the answer, there might be range of files/settings that can be the culprit. So, before going on hunting, please check if that issue is present in a new, fresh user account, too.

---

### Post by uRock on 2011-10-04
Moved to *ubuntu +1*.

---

### Post by zmbmartin on 2011-10-05
> **Krytarik said:**
> Actually, I was meaning it the other way around, as this is the very same GTK file picker dialog. Well, at least it should be. :p

How about the dialog that comes up if you run this in the Terminal?:
```
zenity --file-selection
```
I take that Arch Linux uses the rolling release model, and by now - it seems - you can opt for both Gnome 2 or 3, thus also GTK+ 2 or 3, eventually. Do you know what version of Gnome you were running?

Depending on the answer, there might be range of files/settings that can be the culprit. So, before going on hunting, please check if that issue is present in a new, fresh user account, too.

OK so the dialog that comes up from running the zenity command looks right and has the proper theme applied. I also setup a new user account and checked and the same problem persists with the new account. If I go to a site that uses a non flash based file uploader all is fine. It appears to only be related to flash based file uploaders.

Thanks

---

### Post by zmbmartin on 2011-10-05
After some further investigation I figured out my problem. I am running a 64 bit Ubuntu so I needed to install 32 bit libs for flash.

```
sudo apt-get install ia32-libs
```

---

### Post by uRock on 2011-10-05
Have you tried flash aid in Firefox? [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by Krytarik on 2011-10-05
> **zmbmartin said:**
> After some further investigation I figured out my problem. I am running a 64 bit Ubuntu so I needed to install 32 bit libs for flash.
Hmm, unexpected, actually! I didn't think that Flash can have anything to do with those file picker dialog, as it's just invoking it. But now it seems like the way it's doing that is partly affecting those dialog.

Anyway, I'm glad that you figured it out! :D
And I'm noting that for future cases. :P

---

### Post by zmbmartin on 2011-10-06
> **uRock said:**
> Have you tried flash aid in Firefox? [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)
Krytarik I should also add that uRock's solutions works even better if you don't have any need for or don't want to install ia32-libs.

Thanks for the help guys.

---

### Post by Krytarik on 2011-10-06
> **zmbmartin said:**
> I should also add that uRock's solutions works even better if you don't have any need for or don't want to install ia32-libs.
I think because you're now using a 64-bit version of the Flash Player!?

---

