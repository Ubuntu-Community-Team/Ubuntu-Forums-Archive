---
title: "bold text"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by jon12 on 2013-09-01
XFCE
 how can I get my bookmarks bar items to show in bold and colors???

---

### Post by rai_shu2 on 2013-09-01
Do you mean in Thunar (the file manager)? I'm not sure if that's a feature.

---

### Post by vasa1 on 2013-09-01
OP, can you **please** be more specific about what you mean by "bookmarks bar"?

@rai_shu, it's partly possible but maybe it depends on the theme. I'm using Greybird from the "shimmer-themes" package and Greybird is the default in Xubuntu 13.04, IIRC.

I've modified it to my tastes and so the image won't be standard, but the font in the "Places" sidepane is now "Comic Sans MS Bold". I haven't found how to change the color.

To make the change, one can edit Greybird/gtk-2.0/apps/thunar.rc and insert, for example, "font_name = Comic Sans MS Bold" in the section titled "sidepane" like so:
```
style "sidepane"
{
	base[NORMAL]		= mix (0.1, shade (1.35,@selected_bg_color), shade (0.9,@base_color))
	base[INSENSITIVE]	= mix (0.4, shade (1.35,@selected_bg_color), shade (0.9,@base_color))
	
	bg[NORMAL]		= mix (0.1, shade (1.35,@selected_bg_color), shade (0.9,@base_color)) #shade (0.92,@base_color)
	bg[PRELIGHT]		= shade (1.5,@selected_bg_color)
	text[NORMAL]		= mix(0.1, @base_color, @text_color)
	font_name		= "Comic Sans MS Bold"
}
```

**Edit**: if you wish, even [FONT=Courier New]font_name = "bold"[/FONT] works, so you retain your default font but just make it bold in the side panel.

---

### Post by vasa1 on 2013-09-01
And, in the code above, changing```
text[NORMAL]		= mix(0.1, @base_color, @text_color)
```to```
text[NORMAL]		= "orange"
```makes the text in the side pane orange.

I don't know whether it's okay to use an "absolute color" rather than a relative one (which has been defined in gtkrc) but in this case nothing has broken so far ;)

---

