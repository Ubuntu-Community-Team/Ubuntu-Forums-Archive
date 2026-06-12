---
title: "annoying nautilus bar in classic mode"
date: 2011-10-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Avidanborisov on 2011-10-09
Hello everyone.
Recently I have installed Ubuntu 11.10 beta 2. Since I still dislike Unity, I decided to install the latest Cairo dock, and to use Cairo dock session, such as here:
[http://www.webupd8.org/2011/09/cairo-dock-240-released-with-custom.html](http://www.webupd8.org/2011/09/cairo-dock-240-released-with-custom.html)

So I did that, and configured some stuff I was used to have in previous version in classic mode. I also removed global menu with:
```
sudo apt-get remove indicator-appmenu appmenu-gtk
```.
Anyway, I logged back in, and I got this annoying bar (that I absolutely don't need):


When I tried to xkill it, it also killed nautilus with all desktop icons, so I know that this bar is somehow related to nautilus.

If anyone has any idea how can I remove it, without killing nautilus, I would really like to hear it!

Thanks :)

---

### Post by effenberg0x0 on 2011-10-09
I think using gnome-tweak-tool you had an option to get nautillus out of the desktop. Have a look at it.

Regards,
Effenberg

---

### Post by Avidanborisov on 2011-10-09
> **effenberg0x0 said:**
> I think using gnome-tweak-tool you had an option to get nautillus out of the desktop. Have a look at it.

Regards,
Effenberg

Well it does have some options:


But the only option that removes that bar is [FONT="Courier New"]Have file manager handle the desktop[/FONT], and that option actually kills nautilus, and I don't want that, as I said :(

---

### Post by effenberg0x0 on 2011-10-09
Looking at your original post again, I see you removed appmenu-gtk. I guess you should also have removed appmenu-gtk3. 

Regards,
Effenberg

---

### Post by vanadium on 2011-10-09
The black bar you get is probably the effect of the global menu, where application menu's are displayed, mac style, in the top bar. If you can remove that, the menus will again be displayed in the individual application windows.

---

### Post by Avidanborisov on 2011-10-09
> **effenberg0x0 said:**
> Looking at your original post again, I see you removed appmenu-gtk. I guess you should also have removed appmenu-gtk3. 

Regards,
Effenberg

Thanks, I tried now to remove that also, but the bar is still there.

> **vanadium said:**
> The black bar you get is probably the effect of the global menu, where application menu's are displayed, mac style, in the top bar. If you can remove that, the menus will again be displayed in the individual application windows.

There is no global bar, because I have removed it, and indeed I see all the menus in the applications, even in nautilus. This bar is somehow related to nautilus.

---

### Post by mc4man on 2011-10-09
By default in gnome-fallback you shouldn't see the nautilus menu in the upper panel 
Ex. here - don't use but set up a new user, installed the fallback session & screen shows that, nothing removed, tweaked, ect.
So possibly it was something you did that  caused this

Maybe set up a new user & figure out

---

### Post by effenberg0x0 on 2011-10-09
Well, this is sort of unusual. I suggest you use xprop, click on this bar, and get some info on it. At this point I'm confused what it is. Would like to see if it actually is WM_CLASS desktop, nautilus. Also, maybe you can recursively unset, or search for the specific key on:

/apps/nautilus/preferences
/apps/nautilus-open-terminal
/schemas/apps/nautilus-open-terminal
/desktop/schemas/gnome

Regards,
Effenberg

---

### Post by Gillingham on 2011-10-09
I have also seen this behaviour when setting the panel to autohide, the bar normally sits behind the panel (even when the panel is transparent(!)) I have confirmed this with a new user.

Here is an extract from xprop (other Icon removed)

> 
XKLAVIER_STATE(INTEGER) = 0, 0
WM_STATE(WM_STATE):
		window state: Normal
		icon window: 0x0
_NET_WM_DESKTOP(CARDINAL) = 4294967295
_NET_WM_STATE(ATOM) = _NET_WM_STATE_SKIP_PAGER, _NET_WM_STATE_SKIP_TASKBAR, _NET_WM_STATE_STICKY
_NET_WM_ALLOWED_ACTIONS(ATOM) = _NET_WM_ACTION_CHANGE_DESKTOP, _NET_WM_ACTION_ABOVE, _NET_WM_ACTION_BELOW
WM_HINTS(WM_HINTS):
		Client accepts input or input focus: True
		Initial state is Normal State.
		bitmap id # to use for icon: 0x2000085
		bitmap id # of mask for icon: 0x200008d
		window id # of group leader: 0x2000001
XdndAware(ATOM) = BITMAP
_MOTIF_DRAG_RECEIVER_INFO(_MOTIF_DRAG_RECEIVER_INFO) = 0x6c, 0x0, 0x5, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x0, 0x10, 0x0, 0x0, 0x0
_NET_WM_ICON(CARDINAL) = 	Icon (16 x 16):
	                
	                
	                
	 &#9619;&#9619;&#9619;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9617;&#9617;&#9617;&#9617;&#9618; 
	 &#9619;            &#9617; 
	 &#9619;&#9619;&#9619;&#9618;&#9618;&#9617;&#9617;  &#9617;&#9617;  &#9617; 
	 &#9619;&#9619;&#9619;&#9618;&#9617;&#9617;&#9617;    &#9617;&#9617;&#9617; 
	 &#9619;&#9619;&#9619;&#9618;&#9618;&#9617;    &#9617;&#9617;&#9617;&#9618; 
	 &#9619;&#9619;&#9619;&#9618;&#9618;&#9617;&#9617; &#9617;&#9617;&#9617;&#9617;&#9618;&#9617; 
	 &#9619;&#9619;&#9619;&#9618;&#9618;&#9618;&#9617;&#9617;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618; 
	 &#9619;&#9619;&#9619;&#9619;&#9619;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618; 
	 &#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9619;&#9618;&#9618;&#9618;&#9618;&#9618;&#9618; 
	                
	                
	                
	                


_NET_WM_SYNC_REQUEST_COUNTER(CARDINAL) = 33554438
_NET_WM_WINDOW_TYPE(ATOM) = _NET_WM_WINDOW_TYPE_DESKTOP
_NET_WM_USER_TIME_WINDOW(WINDOW): window id # 0x2000005
WM_CLIENT_LEADER(WINDOW): window id # 0x2000001
_NET_WM_PID(CARDINAL) = 11738
WM_LOCALE_NAME(STRING) = "en_GB.UTF-8"
WM_CLIENT_MACHINE(STRING) = "david-AOA150"
WM_NORMAL_HINTS(WM_SIZE_HINTS):
		program specified location: 0, 0
		program specified minimum size: 1024 by 600
		program specified maximum size: 1024 by 600
		program specified base size: 0 by 0
		window gravity: NorthWest
WM_PROTOCOLS(ATOM): protocols  WM_DELETE_WINDOW, WM_TAKE_FOCUS, _NET_WM_PING, _NET_WM_SYNC_REQUEST
WM_CLASS(STRING) = "desktop_window", "Nautilus"
WM_ICON_NAME(STRING) = "Desktop"
_NET_WM_ICON_NAME(UTF8_STRING) = "Desktop"
WM_NAME(STRING) = "Desktop"
_NET_WM_NAME(UTF8_STRING) = "Desktop"

---

### Post by dino99 on 2011-10-09
this issue is already reported and have to wait for a nautilus fix.

[https://bugs.launchpad.net/ubuntu/oneiric/+source/nautilus/+bug/826771](https://bugs.launchpad.net/ubuntu/oneiric/+source/nautilus/+bug/826771)

---

### Post by Avidanborisov on 2011-10-09
> **mc4man said:**
> By default in gnome-fallback you shouldn't see the nautilus menu in the upper panel 
Ex. here - don't use but set up a new user, installed the fallback session & screen shows that, nothing removed, tweaked, ect.
So possibly it was something you did that  caused this

Maybe set up a new user & figure out

What are use suggesting? I don't want to use gnome-shell or gnome-fallback. I still want to use cairo dock session, but without this annoying bar.

> **effenberg0x0 said:**
> Well, this is sort of unusual. I suggest you use xprop, click on this bar, and get some info on it. At this point I'm confused what it is. Would like to see if it actually is WM_CLASS desktop, nautilus. Also, maybe you can recursively unset, or search for the specific key on:

/apps/nautilus/preferences
/apps/nautilus-open-terminal
/schemas/apps/nautilus-open-terminal
/desktop/schemas/gnome

Regards,
Effenberg

OK, here is the output:
[http://pastebin.com/LVgs3UnX](http://pastebin.com/LVgs3UnX)

And I could not find anything to turn that on or off, in the configuration editor.

> **dino99 said:**
> this issue is already reported and have to wait for a nautilus fix.

[https://bugs.launchpad.net/ubuntu/oneiric/+source/nautilus/+bug/826771](https://bugs.launchpad.net/ubuntu/oneiric/+source/nautilus/+bug/826771)

Well, its good to know that I am not the only one experiencing this problem, and that it should be fixed!

---

