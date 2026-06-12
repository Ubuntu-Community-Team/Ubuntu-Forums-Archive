---
title: "multiple backgrounds in the gnome panel"
date: 2010-05-10
forum: Programming Talk
---

### Post by blendmaster1024 on 2010-05-10
Before you ask, yes, this is the right forum, and I do have a question, read or skip to the end to see it.

I have been exploring having two backgrounds in the gnome panel, one for one applet and one for another. It seems that in theory, the theme should be able to do it, but so far I can't figure out how to do it in that way. But I have been exploring doing it "manually" - either modifying the c code of the gnome panel applet that I want to theme or the panel itself, and while I *know* it's possible if I do that, I don't know the c interface to gtk+ anywhere near well enough to get anywhere. I do know pygtk pretty well, so I'm currently exploring theming the backgrounds of the applets that can theme themselves, and then making a custom applet to be a space-filler that has nothing but a background. I'll probably be able to figure that one out on my own, but I doubt it will look as good as if I modify the panel to have a seperate "sub-panel" option.

So, I apt-get source-ed gnome-panel and started mucking around; I noticed the drawer code, and I wondered if maybe the drawer could be made into an embedded sub-panel. That would be a very cool feature, and would probably get integrated into gnome. But I can't figure out how! I can't even find the container widget that pops up when you click on the drawer. So far, the only thing I've decoded from that code is that the struct "PanelToplevel" has a gtk window object instance. And I'm now trying to figure out the drawer's use of that struct.

So, the question: anyone know gtk+ well enough to give me a tool or two, or maybe even have worked with the gnome-panel source before?

---

