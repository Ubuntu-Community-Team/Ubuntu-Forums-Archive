---
title: "&quot;Advanced Settings&quot;: help with themes, please"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by vasa1 on 2011-10-17
My system is a vanilla 11.10 (Unity 3D) upgraded from 11.04.

I want help with *theme*-ing.

In 11.04, a right-click on the desktop and then clicking on Appearances allowed to choose a theme that was closest to my tastes and then customize it further and save that modified theme to /home/myname/.themes.

That choice is apparently not present in 11.10 since it has Gnome 3.

I installed "Advanced Settings" from the Ubuntu Software Center. While I can easily change themes and a few other things, I still can't further customize a theme.

Do I need to install anything further? Would it be this:
[https://live.gnome.org/GnomeShell/Extensions/user-theme](https://live.gnome.org/GnomeShell/Extensions/user-theme) ???

I don't want to get into *theme*-ing full time. I just want to adjust the contrast in the Low Contrast theme, which is the theme that I like the best.

If I do need to install the extension I mentioned above, please explain how I should do it in as much detail as your time permits! Please don't take it for granted that I'll know "obvious" intermediate steps.

Thanks in advance!

I forgot to mention that I haven't installed any Gnome shell or any such thing. It's a basic 11.10 default system.

Please also mention which is a more suitable location:[I]
Extensions can be installed per-user in ~/.local/share/gnome-shell/extensions, or systemwide in /usr/share/gnome-shell/extensions and /usr/local/share/gnome-shell/extensions.[/I]

---

### Post by mcduck on 2011-10-17
Sorry, but graphical tools for editing GTK3 themes don't exist yet, the only way you could change the colors in themes is editing the actual theme files by hand.

It's not too hard if you are familiar with CSS, but otherwise I'd recommend just trying to find a theme you like from the GTK3 section at [gnome-look.org]("http://gnome-look.org/")

/the User Theme Extension allows you to change the theme of the Gnome Shell, it's in no way related to changing or editing GTK3 themes)

---

### Post by vasa1 on 2011-10-17
> **mcduck said:**
> ... the only way you could change the colors in themes is editing the actual theme files by hand.

It's not too hard if you are familiar with CSS...

Where can I find those files? I'm not unfamiliar with CSS and so won't mind giving it a try.

---

### Post by mcduck on 2011-10-17
The themes included by default (and all system-wide installed themes) are located in /usr/share/themes.

---

### Post by vasa1 on 2011-10-17
> **mcduck said:**
> The themes included by default (and all system-wide installed themes) are located in /usr/share/themes.

Thank You! Found them. I'll back up what I want to play with first and come back if I have questions!

---

### Post by mcduck on 2011-10-17
No problem. :)

I recommend copying the existing theme to ~/.themes and renaming it, making it a lot easier to edit the theme as you wouldn't need to work with root permissions.

---

### Post by vasa1 on 2011-10-17
> **mcduck said:**
> No problem. :)

I recommend copying the existing theme to ~/.themes and renaming it, making it a lot easier to edit the theme as you wouldn't need to work with root permissions.

But then how will I get Gnome to "see" the modified theme?
BTW, that folder already exists and holds a "theme" file that can't be opened with a text editor. This file was created when I customized a theme in 11.04.)

In the meantime, I managed to do a small tweak successfully. I first chose the Adwaita theme in Advanced Systems (Gnome Tweak?) so that I could work on the Low Contrast theme. Here, I edited gtk.css in 
/usr/share/themes/LowContrast/gtk-3.0. Saved the changes and then switched back to Low Contrast from Adwaita.

---

### Post by mcduck on 2011-10-17
> **vasa1 said:**
> But then how will I get Gnome to "see" the modified theme?
BTW, that folder already exists and holds a "theme" file that can't be opened with a text editor. This file was created when I customized a theme in 11.04.)

In the meantime, I managed to do a small tweak successfully. I first chose the Adwaita theme in Advanced Systems (Gnome Tweak?) so that I could work on the Low Contrast theme. Here, I edited gtk.css in 
/usr/share/themes/LowContrast/gtk-3.0. Saved the changes and then switched back to Low Contrast from Adwaita.

If you rename the theme, Gnome will of course see it as a new theme of it's own. And ~/.themes is the standard location for themes installed for your user account only.

If you are comfortable with editing the themes in the system directory, you are of course free to do so. :)

---

### Post by vasa1 on 2011-10-17
> **mcduck said:**
> If you rename the theme, Gnome will of course see it as a new theme of it's own. And ~/.themes is the standard location for themes installed for your user account only.

If you are comfortable with editing the themes in the system directory, you are of course free to do so. :)

I'm sorry but I'm not understanding how to proceed.

The **only way I know** of right now to change themes is via "Advanced Settings" which is available at the Ubuntu Software Center.
> GNOME Tweak Tool (pronounced [kræptu&#720;l]) allows the adjustment of a number of GNOME configuration settings that is felt would not be of interest to ordinary users. This includes things like the fonts used in user interface elements, alternative user interface themes, changes in window management behaviour and others.
...
gnome-tweak-tool 3.2.0-0ubuntu1


Now, on opening the Advanced Settings, on the left hand side there are a few options:
Desktop
Fonts
Shell
Shell Extensions
Theme
Window

Going from top to bottom, **Desktop**, **Fonts**, and **Shell** are not of concern to me = I'm content with the settings.
**Shell Extensions** appears blank. I don't know if this is good or bad.
Then we come to **Theme**.
Theme has a number of options as shown in Adv_Settings_Themetab.png

Clicking on the dropdown next to **GTK+ theme** is **the only way I can see** to allow me to select a GTK+ theme. It only lists themes present in /usr/share/themes. In other words, I don't know how to change to a theme that is located in ~/.themes.

---

### Post by mcduck on 2011-10-17
Do you actually have any GTK3 themes in ~/.themes  currently?

You don't need t do anything to switch between the two locations, they both work completely automatically. All you need is to have compatible themes in either one, or both, locations.

The only difference between them is that themes in /usr/share/themes are available to all users of the system, and installing them requires administrator privileges. And themes located in user's home directory are only available to that user, but the user can install them even if he isn't an admin.

You mentioned that you have an old theme from 11.04 in ~/.themes. That doesn't appear in gnome-tweak-tool because it's a GTK2 theme (or a complete theme set based on GTK2 theme), while Ubuntu 11.01 uses GTK3.

Shell Extensions are only related to Gnome Shell, not the Unity shell that Ubuntu uses by default.

---

### Post by vasa1 on 2011-10-17
> **mcduck said:**
> Do you actually have any GTK3 themes in ~/.themes  currently?

You don't need t do anything to switch between the two locations, they both work completely automatically. All you need is to have compatible themes in either one, or both, locations.

The only difference between them is that themes in /usr/share/themes are available to all users of the system, and installing them requires administrator privileges. And themes located in user's home directory are only available to that user, but the user can install them even if he isn't an admin.

You mentioned that you have an old theme from 11.04 in ~/.themes. That doesn't appear in gnome-tweak-tool because it's a GTK2 theme (or a complete theme set based on GTK2 theme), while Ubuntu 11.01 uses GTK3.

Shell Extensions are only related to Gnome Shell, not the Unity shell that Ubuntu uses by default.

**Thank You**! I copied LowContrast over and renamed it MyLowContrast. I see it now!

Now, I need to really figure out how things work. I've managed to make some changes by editing /home/mycomp/.themes/MyLowContrast/gtk-3.0/gtk.css but I'm finding the going difficult since this CSS doesn't involve the type of tags that I've encountered tweaking CSS of browser pages and browser "chrome".

Is there some source that would explain what things are affected?

For example, I've edited lines 5 and 6 to get
```
@define-color theme_base_color #444;
@define-color theme_text_color #330000;

```

#444 was originally #9a9a9a and #330000 was originally #666.

So far, I've managed to make changes visible when I use Alt+File, Open ... This was unintentional and seems to work only in certain programs made by the Gnome project (Evince, gedit) and not others such as LibreOffice, Firefox, or Google Chrome.

My main aim is to have a darker shade of both background and text and no white anywhere.

Anyway, now I can play around without having to mess with permissions.

---

### Post by mcduck on 2011-10-17
Sorry, I can't really help you with the exact details of what each selector affects. I haven't had enough time myself to start learning the GTK3 theming.

(and considering how new GTK3 is, and the fact that most of the available options for GTK2 were never explained anywhere properly, I wouldn't expect there to be much documentation for GTK3 theming either. At least no yet. But you can of course see if you can find something.)

Anyway, the best approach is to just change some value, perhaps to some rather radical color like bright red, and then switch to another theme and back again to get the theme reloaded and to see the changes. And then add a comment to your theme so you'll remember what that selector does in the future. :)

There used to be some tools to help previewing GTK2 themes while editing the theme (without having to constantly switch the actual theme you are using for your desktop), but none of them seems to be updated to GTK3 yet.

---

### Post by vasa1 on 2011-10-17
> **mcduck said:**
> Sorry, I can't really help you with the exact details of what each selector affects. I haven't had enough time myself to start learning the GTK3 theming.
...

Not to worry. But I was really pleased with what I had with 11.04. Let's wait and see (and play around) as things unfold.

---

### Post by mcduck on 2011-10-17
> **vasa1 said:**
> Not to worry. But I was really pleased with what I had with 11.04. Let's wait and see (and play around) as things unfold.

I'm pretty sure we'll get more configuration options, and hopefully also some nice tools for editing the themes in near future.

Anyway, it took 9 years for Gnome 2 to get all the tools and features it had in the end, and for example the ability to change theme colors (for some themes, at least) without editing the themes by hand was one of the last additions, only year or two ago if I remember right. I hope we don't have to wait *that* long this time... ;)

Well, at least the CSS syntax in GTK3 is a bit nicer (and familiar to more people) than the old gtkrc syntax was.

---

### Post by vasa1 on 2011-10-18
> **mcduck said:**
> ...
Well, at least the CSS syntax in GTK3 is a bit nicer (and familiar to more people) than the old gtkrc syntax was.

I tried looking for "CSS syntax in GTK3" but I've found stuff just for the older version. It still gives me an idea of things and what's immediately clear is that this syntax is worlds apart from the stuff used for web pages.

---

### Post by vasa1 on 2011-10-20
I'm using GNOME tweak tool called Advanced Settings in the _U_buntu _S_oftware _C_enter (gnome-tweak-tool 3.2.0-0ubuntu1). I also installed Gcolor2 from USC,

My window theme is **Adwaita** and my GTK+ theme is **LowContrast**.

By default, the contrast between text and background is **really** low in GNOME applications and even in things like LibreOffice.

I'm trying to increase the contrast a little but overall I like both Adwaita and LowContrast.

To that end, I made the following changes (after backing up relevant files):
/usr/share/themes/LowContrast/gtk-2.0/gtkrc
changed lines 23 and 24 from #666666 to #000

/usr/share/themes/LowContrast/gtk-3.0/gtk.css
changed lines 6, 9, 12, 29 all from #666666 to #300000

/usr/share/themes/Adwaita/gtk-3.0/gtk.css
changed line 27 from #4a90d9 to #2f3da8

**I maybe wrong here**, but the effect of some changes isn't instantly visible and may require a relogin or even reboot. That's why I'm not attempting all the changes I want to make at one time.

Edit some days later: just temporarily switching themes via "Advanced Settings" is enough to register the changes. No need to log-out/log-in or to reboot.

---

### Post by vasa1 on 2011-10-20
Regrettably, there's remarkably little information out there for newbies following the removal of a simple interface to customize appearances (missing in 11.10, present in 11.04).
For what it's worth, I came across this:
[http://www.omgubuntu.co.uk/2011/10/use-adwaita-dark-as-your-system-theme/](http://www.omgubuntu.co.uk/2011/10/use-adwaita-dark-as-your-system-theme/)

---

### Post by vasa1 on 2011-10-23
Well, I made an edit about how switching from theme 1 to theme 2 and back to theme 1 was enough to make changes apparent if the css (gtk2 or gtk3) or gtkrc of theme 1 had been altered.

Now, I'm not sure. I had made some changes that would register with just switch to another theme and back but now I feel that a reboot helps! Confused!

---

### Post by agnul on 2011-10-24
Looks like the good place for a "me too". I've copied the "Radiance" theme from /usr/share/themes/Radiance to ~/.themes/Eclipse, modified the "index.theme" file with the new name but the "Appearance" applet won't let me select "Eclipse" as a theme, no matter what. Using gnome-tweak-tool worked. Anyone knows what's wrong?

---

