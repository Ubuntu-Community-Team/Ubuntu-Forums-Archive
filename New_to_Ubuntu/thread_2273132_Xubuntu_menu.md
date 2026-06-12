---
title: "Xubuntu menu"
date: 2015-04-10
forum: New to Ubuntu
---

### Post by RobGoss on 2015-04-10
Hello I using Xubuntu and was wondering if there was a way to change the menu colors and theme, It seems a bit plain for my liking so I wanted to customize it a bit. Thanks so much

---

### Post by Impavidus on 2015-04-10
Menu &#8594; Settings (one of the buttons at the bottom of the menu). Then click theme configuration.

They picked some very remarkable default colours to encourage people to find out how easy it is to change them.

---

### Post by RobGoss on 2015-04-10
Hello are you saying I can change the menu theme? Because I'm not seeing that setting.

---

### Post by Bucky Ball on 2015-04-10
Theme configuration is not an option here, either. As far as I know, themes are referred to as 'styles' in Xubuntu (Apps>Settings>Appearance>Style tab), but that is not going to do what you want. There is an option in the Appearance window for adding a custom 'Menu file', so that might get you closer if you look into what a custom menu file is. 

You can change the Apps icon easy enough by right clicking and Properties, but changing the colours and themes of the drop down menu? If it can be done I'd say it would need to apply to the whole panel rather than just one drop down menu.

---

### Post by kerry_s on 2015-04-10
not sure if it still works but,
[https://gottcode.wordpress.com/2013/11/27/theming-whisker-menu/](https://gottcode.wordpress.com/2013/11/27/theming-whisker-menu/)

---

### Post by RobGoss on 2015-04-10
I will do as suggested by this thread seeing there's not many options. I was hoping to find a simple way to achive this. With mint it's kinda simple I'm hoping something else will be adding to spice up xubuntu as well. Thank you all for your help.

---

### Post by Toz on 2015-04-10
If you are talking about the Whisker Menu, here is config for a dark theme (adjust the colours as required). Just add this code to ~/.gtkrc-2.0 (create the file if it doesn't exist):
```
style "mydarktheme"
{
	base[NORMAL] = "#1D303B"
	base[ACTIVE] = "#00416F"
	text[NORMAL] = "#ccc"
	text[ACTIVE] = "#fff"
	bg[NORMAL] = "#1D303B"
	bg[ACTIVE] = "#00416F"
	bg[PRELIGHT] = "#398ee7"
	bg[SELECTED] = "#00416F"
	fg[NORMAL] = "#ccc"
	fg[ACTIVE] = "#fff"
	fg[PRELIGHT] = "#fff"
}
widget "whiskermenu-window*" style "mydarktheme"

```
...and restart the panel for it to take effect:
```
xfce4-panel -r
```

If you are talking about the Applications Menu plugin, then that can only be changed by changing the Appearance theme, AFAIK.

---

### Post by Dennis N on 2015-04-10
> **robert159 said:**
> Hello I using Xubuntu and was wondering if there was a way to change the menu colors and theme, It seems a bit plain for my liking so I wanted to customize it a bit. Thanks so much

Use **Theme Configuration** in the Settings Dialog. It will change the background color and text color of drop down menus or the old applications menu if you use that. (I wasn't sure if it would affect the Whisker menu, so I tested it and it did, if only to delete any custom settings you may have previously made for it using developer Graeme's guide linked in post #5 - and see Note below.)

The package for Theme Configuration is **gtk-theme-config** and it is installed by default in Xubuntu 14.04.

**Note**: If you theme your Whisker Menu using Graeme's guide, using the Theme Configuration will remove those settings, so you should back them up before making changes. I would assume you could then restore them to the configuration file. Also, I see that Graeme says in his guide that Whisker Menu will not use the theming of GTK menus, so his method is the way to change Whisker.

---

