---
title: "Launcher for power-users"
date: 2011-05-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by feydrutha on 2011-05-12
I've installed natty on my laptop. The launcher is aesthetically pleasing and works well (though I disable auto-hide since it is something I personally dislike). 

My first impression is that it works well for new users. However, compared to the good old top and bottom gnome panels used for launchers and open windows respectively, it obviously has less room (even with smaller-than-default icons).

Therefore, I was very happy to discover the "unity quicklists" that allow me to make less frequently used launchers (and places) accessible through right click on the launchers.

However, this currently requires manually editing some pretty verbose configuration files, as discussed in this tutorial:

[http://maketecheasier.com/8-really-useful-ubuntu-unity-quicklists/2011/05/07](http://maketecheasier.com/8-really-useful-ubuntu-unity-quicklists/2011/05/07)

For instance, I have set my File Manager launcher to have a bunch of frequently accessed places in right click. The terminal launcher can have a bunch of frequent commands as well (starting synergy client, ssh tunnels, etc). Virtual box launcher can have commands to launch individual vms, and so on and on. 

This is nice but not very convenient to configure. So here is my wish-list for improving the launcher for power users.

[LIST]
[*]A GUI application for adding/editing quicklist items.
[*]File Manager launcher quicklist automatically includes all nautilus places
[*]And finally, a mostly unrelated issue. Power users often have many windows open from an application. It would be great if hovering over a launcher icon provided previews of these windows.. similar to the compiz window preview plugin, but with the ability to see multiple previews and select one of them for focusing. Designing this to interact well with auto-hide of the launcher will be tricky though.
[/LIST]

This is just a brainstorm, so any feedback is welcome.

---

### Post by dino99 on 2011-05-12
i agree with all that, but to get changes made, you should request on brainstorm and/or file bugs, because devs are rarely here to browse forums

---

### Post by feydrutha on 2011-05-12
> **dino99 said:**
> i agree with all that, but to get changes made, you should request on brainstorm and/or file bugs, because devs are rarely here to browse forums

Good point, I just want to see if there is some interest in these issues from user before I go to brainstorm/launchpad.

---

### Post by el_koraco on 2011-05-12
> **feydrutha said:**
> 
[LIST]
[*]And finally, a mostly unrelated issue. Power users often have many windows open from an application. It would be great if hovering over a launcher icon provided previews of these windows.. similar to the compiz window preview plugin, but with the ability to see multiple previews and select one of them for focusing. Designing this to interact well with auto-hide of the launcher will be tricky though.
[/LIST]



That's not just a "power user" thing. Neither Gnome Shell nor Unity have a good way of dealing with any kind of consistent window management when it comes to multiple applications. Your idea is good, and should definitely be presented to the brainstorm.

---

### Post by feydrutha on 2011-05-12
> **el_koraco said:**
> That's not just a "power user" thing. Neither Gnome Shell nor Unity have a good way of dealing with any kind of consistent window management when it comes to multiple applications. Your idea is good, and should definitely be presented to the brainstorm.

Yeah, I also think it's a good idea but it's pretty complicated to get right... I think at least some mockups would be needed, but I'm not much of a design guy.

---

### Post by feydrutha on 2011-05-12
Easy cutomization of quicklists is already on brainstorm:

[http://brainstorm.ubuntu.com/idea/27672/](http://brainstorm.ubuntu.com/idea/27672/)

---

### Post by marcio_mi on 2011-05-12
> **feydrutha said:**
> 
[LIST]
[*]And finally, a mostly unrelated issue. Power users often have many windows open from an application. It would be great if hovering over a launcher icon provided previews of these windows.. similar to the compiz window preview plugin, but with the ability to see multiple previews and select one of them for focusing. Designing this to interact well with auto-hide of the launcher will be tricky though.
[/LIST]


I'm not sure I fully understand, but it seems to me that something like that is already in unity. If you have more than one instance of firefox open, for example, by clicking on the firefox icon in the launcher all of them will appear in a "preview" style mode, and you can choose on which one to focus.

Otherwise, in general, you can preview all open application with Super +W (effect like the scale plugin in compiz).

---

### Post by cariboo on 2011-05-12
There is already a quicklist editor in the works, see [here]("http://mygeekopinions.blogspot.com/2011/05/quicklist-editor-manage-your.html")

---

### Post by screaminj3sus on 2011-05-13
> **el_koraco said:**
> That's not just a "power user" thing. Neither Gnome Shell nor Unity have a good way of dealing with any kind of consistent window management when it comes to multiple applications. Your idea is good, and should definitely be presented to the brainstorm.
I think the major problem is is showing thumbnails for minimized windows. Just look at all the current compiz task switchers, a minimized window has no thumbnail and instead has this atrocious blurry icon. This would need to be fixed for this feature to work. I agree its a good idea for sure.

---

### Post by feydrutha on 2011-05-16
> **cariboo907 said:**
> There is already a quicklist editor in the works, see [here]("http://mygeekopinions.blogspot.com/2011/05/quicklist-editor-manage-your.html")

Awesome!

I am quite optimistic about unity... it's not quite there yet but I hope by the next release it will be really solid.

---

### Post by feydrutha on 2011-05-16
> **screaminj3sus said:**
> I think the major problem is is showing thumbnails for minimized windows. Just look at all the current compiz task switchers, a minimized window has no thumbnail and instead has this atrocious blurry icon. This would need to be fixed for this feature to work. I agree its a good idea for sure.

True, that's a problem, but the window preview in the task bar was still useful for me at least. Also, it seems that Unity is trying to break the minimze habit in users so this could become less of a problem over time.

The reason I don't have anything specific to propose, however, is that I would like the window previews to show up when I hover over the icon. But for the default behavior where the launcher auto-hides, that would probably be not very usable. And since both left and write click already have a useful meaning, I'm not sure how else it could be done.

---

### Post by feydrutha on 2011-05-16
> **marcio_mi said:**
> I'm not sure I fully understand, but it seems to me that something like that is already in unity. If you have more than one instance of firefox open, for example, by clicking on the firefox icon in the launcher all of them will appear in a "preview" style mode, and you can choose on which one to focus.

Otherwise, in general, you can preview all open application with Super +W (effect like the scale plugin in compiz).

Thanks, marcio_mi, I am aware of these options, and use them both. In fact, I have the compiz scale plugin bound to the a screen corner and use it regularly. But I would love to also be able to see window previews when I just hover over the icon (like in the old gnome bar+compiz window preview, and a bit like google search previews). When multiple windows are open, I would like to get previews of them all, and be able to choose which one to open with arrow keys or scroll wheel+click, or directly with a mouse click on the preview.   

Does that make sense?

---

### Post by teachop on 2011-05-16
> **feydrutha said:**
> I would love to also be able to see window previews when I just hover over the icon
This would be really really nice.  All the windows slide out horizontally to the right from the icon in a line, and you click on one if you need to, but as mentioned this is an issue with the auto-hide.

How about a target on the panel that would slide the tiny previews out for all open windows like this, all at once.  Put that in the left corner next to the Dash button.  Click it and there are all the windows.

---

### Post by Squonk07 on 2011-05-18
Correct me if I'm wrong, but can't you auto-hide the Taskbar in Windows 7 and still get the window previews just by making the bar appear and mousing over the icon you want? I'm too lazy to boot into Windows to check, but it would be very odd if this weren't the case.

If so, then why would the auto-hide behavior of the Launcher be any different? Since the feature we're talking about is essentially an analog for the Windows implementation, I can't see the problem.

And, to be frank, if this *is* somehow a problem for Unity, why then is *any* form of auto-hiding the default behavior? Maybe I'm just old-fashioned, but I couldn't take the default setting for more than a week and had to make the Launcher always visible. My sanity has returned.

---

