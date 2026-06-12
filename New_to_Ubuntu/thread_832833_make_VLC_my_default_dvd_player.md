---
title: "make VLC my default dvd player"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by scotcella on 2008-06-18
When I install a DVD to watch on my laptop, it goes straight to Totem Movie Player. I prefer to use VLC becuase it enables the disk menu to be shown so I can turn the captions on..

I would like to make VLC the default application?

Many thanks in advance

---

### Post by iaculallad on 2008-06-18
Navigate to System->Preferences->Removable Drives and Media, click on the multimedia tab, replace totem %m with vlc %m

---

### Post by barbedsaber on 2008-06-18
ooh, thats how you do it.

---

### Post by scotcella on 2008-06-18
Hi iaculallad

THanks for your quick response, I dont have the media tab, only cameras, PDAs, Printers and Scanners and Input devices.

What shall I do now?

oh FYI I'm using Hardy

---

### Post by iaculallad on 2008-06-18
Sorry for that, I'm using my Gutsy for now so I pointed the solution for Gutsy. Here's a link on how you can create VLC your default player for Hardy.

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD)

---

### Post by Corrupt3d on 2008-06-18
> **scotcella said:**
> Hi iaculallad

THanks for your quick response, I dont have the media tab, only cameras, PDAs, Printers and Scanners and Input devices.

What shall I do now?

oh FYI I'm using Hardy

You can get to the same menu by typing:

$gconf-editor

Desktop>Gnome>Volume manager,

on the right side you will see 'autoplay_dvd_command' | Value = totem%d

---

### Post by scotcella on 2008-06-18
Should have checked there first, i'm getting better slowly

---

### Post by VAnsWerMan on 2008-08-10
I also do not have the media tab, only cameras, PDAs, Printers and Scanners and Input devices!!!!  Why?

---

### Post by gerben1 on 2008-08-10
> **VAnsWerMan said:**
> I also do not have the media tab, only cameras, PDAs, Printers and Scanners and Input devices!!!!  Why?

It is in System->Preferences->Preferred Applications now.

---

### Post by stevek123 on 2008-08-30
> **iaculallad said:**
> Sorry for that, I'm using my Gutsy for now so I pointed the solution for Gutsy. Here's a link on how you can create VLC your default player for Hardy.

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD)

I guess this is an older post so 'button' is disabled but "Thanks!!!":)

---

### Post by Norwal on 2008-10-05
> **iaculallad said:**
> Sorry for that, I'm using my Gutsy for now so I pointed the solution for Gutsy. Here's a link on how you can create VLC your default player for Hardy.

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD)

Thanks iaculallad.  The link you provided worked for me.:D

---

