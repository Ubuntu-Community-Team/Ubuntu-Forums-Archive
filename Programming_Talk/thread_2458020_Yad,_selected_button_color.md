---
title: "Yad, selected button color"
date: 2021-02-14
forum: Programming Talk
---

### Post by aeronutt on 2021-02-14
I'm using yad (fork of zenity) to create some simple script interfaces.

Q: Is there a way to set the "background" color of the selected button?

Problem: If I run my script in Ubuntu, the pop-up shows up and I can't really tell which button is selected by default. All buttons appear identical except for a very faint difference in the outline of the buttons.
But, run the same script under another OS, and the default button is obvious from it's color (blue, vs white compared to all non-selected buttons, for example).

---

### Post by norobro on 2021-02-17
> **aeronutt said:**
> Q: Is there a way to set the "background" color of the selected button?I know of two ways to go about it.

1. Edit ~/.config/gtk-3.0/gtk.css and add something like this:```
button:focus {
    background: lightgray; /*choose any color*/
}
```The down side to this is that it will override the focus color for every Gtk app.

2. Create a custom theme. For example on my box the default theme is adwaita. To create a theme named 'yad_theme' do the following: ```
mkdir -p  ~/.themes/yad_theme/gtk-3.0/
touch ~/.themes/yad_theme/gtk-3.0/gtk.css
```Add the following to the file: ```
@import url("resource:///org/gtk/libgtk/theme/Adwaita/gtk-contained.css");

button:focus {
    background: lightgray;
}
```Then when you run yad preface it with "GTK_THEME=yad_theme". 
i.e. "GTK_THEME=yad_theme yad" should produce a window with the background of the cancel button light gray.

HTH

---

### Post by aeronutt on 2021-02-17
Thanks!!!  I'll give #2 a shot and report back.
I'll also check to see if this is how active yad buttons have color in Neon/Plasma

---

### Post by norobro on 2021-02-17
Sorry about the HTH in the middle of the code. Obviously I meant that to be at the bottom.

I'll edit the post.

---

### Post by aeronutt on 2021-02-18
Ha...yea, I saw that HTH and knew better. :)

Tried #1, and it's working well, will also try #2 method, but I'm going to mark this solved.

THANKS!!!!!!!!!

---

