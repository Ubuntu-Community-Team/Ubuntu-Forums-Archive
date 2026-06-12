---
title: "Limited keyboard layout / key binding"
date: 2015-12-12
forum: New to Ubuntu
---

### Post by Yrvyne on 2015-12-12
Hi all, I have basic/limited experience in Lubuntu & Linux in general.

As an introduction I installed Lubuntu because the laptop has very low-end specs and is almost ten years old.

The help I need is about the keyboard layout in association with the Maltese language (mt).

It has two key-layouts: 47 or 48 keys.

This laptop was manufactured with the 47 key-layout (because one particular letter cannot be reproduced).

On installation I opted for the US layout so as to have a streamlined operation.

To add the Maltese Language layout (after installation), I sudo'ed ```
setxkbmap -layout mt
```

This, of course, changed the key production from US letters to Maltese letters save for one.

```
setxkbmap -query
```

The query code yielded the following results:
[LIST]
[*]rules:      evdev 
[*]model:      pc105 
[*]layout:     mt 
[/LIST]


**1.**  Thus, is there a way to change the rules/model/layout in order to use the 48-letter MT keyboard? (Does not matter if I have to install additional packages or edit configuration files - I might ask for further guidance should the latter be the case)
 
**2.**  As an alternative, I had this idea to bind either the Win key, or dedicated Euro key or dedicated Dollar key to be the missing letter. 
[LIST]
[*]Any thoughts on the pheasability of this idea? 
[*]I have read that I would have to modify configuration files that has to do with X or X-org. 
[/LIST]

SSince the laptop was manufactured as 47-letter, I assume that method **2** is the preferred option, however, any thoughts, suggestions and instructions on any method are highly appreciated.

Thanks in advance.

---

### Post by sandyd on 2015-12-12
Note that the below may be a bit hampered by lack of knowledge about keyboards other than US English, so may require some adjustments.

What you want to do is to bind an alternative key for that 48th key.

First, choose a key to use, the super key (The one that says windows) doesn't seem to work as a replacement. It is probably due to the fact that pressing it opens unity. In the below example, I chose * on my numpad because I didn't feel like fiddling with whatever is making Unity open the dash.

After choosing the key, we need to determine what the keycode for the key is.

We will run xev to determine that.

Open a terminal, and run the command
```

xev
```

A screen will pop up.


Press the key you want to replace, and go back in the terminal and press Control+C to exit xev

In the xev output, search for your key. xev may have recorded multiple keys, so make sure you find the right one.
Here is the one I found for "*". There should be a KeyPress and KeyRelease event, one event for when you press and one for when you release.

```

<snip>
KeyPress event, serial 37, synthetic NO, window 0x4000001,
    root 0x72, subw 0x0, time 790273, (415,447), root:(480,499),
    state 0x0, [COLOR="#FF0000"]keycode 63[/COLOR] (keysym 0xffaa, KP_Multiply), same_screen YES,
    XLookupString gives 1 bytes: (2a) "*"
    XmbLookupString gives 1 bytes: (2a) "*"
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x4000001,
    root 0x72, subw 0x0, time 790377, (415,447), root:(480,499),
    state 0x0, [COLOR="#FF0000"]keycode 63[/COLOR] (keysym 0xffaa, KP_Multiply), same_screen YES,
    XLookupString gives 1 bytes: (2a) "*"
    XFilterEvent returns: False
<snip>
```

The red part is the part you want, the keycode.
In my case, keycode is 63.

I then set the mapping using the following command.  Note that I set the mapping to point the "*" key to the letter T (along with lower/upper case) in this example, you will want to set your own.
```

xmodmap -e "[COLOR="#FF0000"]keycode 63[/COLOR] = t T"

```

If you have trouble determining what goes on the other side of the = sign (again, not sure about non-english keyboards), take a look at [http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap](http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap)

We then save the keymap in your home directory
```

xmodmap -pke >~/.Xmodmap
```

We then load it, make sure things are working
```

xmodmap ~/.Xmodmap
```

After it is confirmed to work, we can autoload it at startup

The code drops a file named 'xmodmap.desktop' into the autostart folder in your home folder, this requires no adjustments, just copy/paste the whole box
```

mkdir -p ~/.config/autostart/
cat <<EOF > ~/.config/autostart/xmodmap.desktop
[Desktop Entry]
Type=Application
Exec=bash -c 'xmodmap ~/.Xmodmap'
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=xmodmap
Comment=Startup Script
EOF
```

I suggest removing ~/.config/autostart/xmodmap.desktop when testing, if you make an error in .Xmodmap, you may find it a bit hard to recover when the enter key becomes mapped to a letter :p

---

### Post by Yrvyne on 2015-12-12
Thank you for the detailed explanation, this is, as you immediately understood, what I was looking for, so thanks once again.

XEV, among other keycodes gave the following:

```
KeyPress event, serial 48, synthetic NO, window 0x2400001,
    root 0x190, subw 0x0, time 1455070, (887,682), root:(889,707),
    state 0x8, keycode 85 (keysym 0xff98, KP_Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 48, synthetic NO, window 0x2400001,
    root 0x190, subw 0x0, time 1455075, (887,682), root:(889,707),
    state 0x8, keycode 85 (keysym 0xff98, KP_Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

However, when executing either: **xmodmap -e "keycode 85 = &#379;"** or **xmodmap -e "keycode 85 = &#380;"** I get the following results:

```
oceanus@oceanus:~$ xmodmap -e "keycode 85 = &#379;"
xmodmap:  commandline:1:  bad keysym name '&#379;' in keysym list
xmodmap:  1 error encountered, aborting.

oceanus@oceanus:~$ xmodmap -e "keycode 85 = &#380;"
xmodmap:  commandline:1:  bad keysym name '&#380;' in keysym list
xmodmap:  1 error encountered, aborting.

```

So my missing letter is "&#380;&#379;", but the *bad keysym* is preventing me from binding the key.

Could this be because "&#380;&#379;" is not part of the standard letters?
That is, the "t" from your example is part of the standard letters on any keyboard while "&#380;&#379;" is not.
Other Maltese letters (&#267;&#266; &#289;&#288; &#295;&#294;) work flawlessly through the **setxkbmap -layout mt** code.

Is there a way to include "&#380;&#379;" in the keysym? Or: how do I make "&#380;&#379;" *visible* to xmodmap?
Thanks again, sandyd!

---

### Post by sandyd on 2015-12-12
Seems xmodmap requires you to convert &#379; into whatever xmodmap decided to call it in english.

Took a bit of trial and error, but seems its called 'abovedot' in the keysyms

Found a list that seems to be fairly accurate [here]("http://wiki.linuxquestions.org/wiki/List_of_Keysyms_Recognised_by_Xmodmap")
It seems to work fine

```

xmodmap -e "keycode 85 = zabovedot Zabovedot"
```

The second entry (i.e. Zabovedot) is for the captital.

---

### Post by Yrvyne on 2015-12-12
Yes, the *abovedot* yields "&#380;&#379;". Following your instructions, &#380;&#379; is simply working. However, this operation has affected the Alt-Tab function.

The key that produces my needed letter is the dedicated Dollar sign located above the right arrow key.

For starters, this is the full quote from where I took the keycode:

```
KeyPress event, serial 45, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1647403, (201,676), root:(203,701),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1647408, (201,676), root:(203,701),
    state 0x8, keycode 90 (keysym 0x1bf, zabovedot), same_screen YES,
    XKeysymToKeycode returns keycode: 85
    XLookupString gives 2 bytes: (c5 bc) "&#380;"
    XmbLookupString gives 2 bytes: (c5 bc) "&#380;"
    XFilterEvent returns: False

KeyRelease event, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1647413, (201,676), root:(203,701),
    state 0x8, keycode 90 (keysym 0x1bf, zabovedot), same_screen YES,
    XKeysymToKeycode returns keycode: 85
    XLookupString gives 2 bytes: (c5 bc) "&#380;"
    XFilterEvent returns: False

KeyPress event, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1647419, (201,676), root:(203,701),
    state 0x8, keycode 90 (keysym 0x1bf, zabovedot), same_screen YES,
    XKeysymToKeycode returns keycode: 85
    XLookupString gives 2 bytes: (c5 bc) "&#380;"
    XmbLookupString gives 2 bytes: (c5 bc) "&#380;"
    XFilterEvent returns: False

KeyRelease event, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1647424, (201,676), root:(203,701),
    state 0x8, keycode 90 (keysym 0x1bf, zabovedot), same_screen YES,
    XKeysymToKeycode returns keycode: 85
    XLookupString gives 2 bytes: (c5 bc) "&#380;"
    XFilterEvent returns: False

KeyPress event, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1647429, (201,676), root:(203,701),
    state 0x8, keycode 89 (keysym 0x1bf, zabovedot), same_screen YES,
    XKeysymToKeycode returns keycode: 85
    XLookupString gives 2 bytes: (c5 bc) "&#380;"
    XmbLookupString gives 2 bytes: (c5 bc) "&#380;"
    XFilterEvent returns: False

KeyRelease event, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1647435, (201,676), root:(203,701),
    state 0x8, keycode 89 (keysym 0x1bf, zabovedot), same_screen YES,
    XKeysymToKeycode returns keycode: 85
    XLookupString gives 2 bytes: (c5 bc) "&#380;"
    XFilterEvent returns: False

KeyPress event, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1647440, (201,676), root:(203,701),
    state 0x8, keycode 85 (keysym 0x1bf, zabovedot), same_screen YES,
    XLookupString gives 2 bytes: (c5 bc) "&#380;"
    XmbLookupString gives 2 bytes: (c5 bc) "&#380;"
    XFilterEvent returns: False

KeyRelease event, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1647445, (201,676), root:(203,701),
    state 0x8, keycode 85 (keysym 0x1bf, zabovedot), same_screen YES,
    XLookupString gives 2 bytes: (c5 bc) "&#380;"
    XFilterEvent returns: False

KeyRelease event, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1647450, (201,676), root:(203,701),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

I tried to no avail:

```
xmodmap -e "keycode 85 = zabovedot Zabovedot"
xmodmap -e "keycode 90 = zabovedot Zabovedot"
xmodmap -e "keycode 89 = zabovedot Zabovedot"
```

But when I entered **xmodmap -e "keycode _64_ = zabovedot Zabovedot"** &#380;&#379; actually worked except for the caveat that Alt-Tab works erratically.

Alt-Tab sends a &#380; into any text-entry box available (flashing cursor) while also showing the Alt-Tab pop-up displaying the available open windows. On further exploration of the XEV code, keycode 64 has **Alt_L** mentioned. Also, *all *keycodes except 64 point towards keycode 85 and that **XLookupString gives 2 bytes: _____ "&#380;"** but none actually produce &#380;&#379; despite mentioning **zabovedot** withing their respective code snippets.

Thus, I think that this is because KeyPress and KeyRelease for keycode 64 are at the start and end of the whole XEV yield while keycodes 85, 89 and 90 are sandwiched in between.

Is there a way to reset the Alt-Tab behaviour while retaining the &#380;&#379; (dedicated Dollar) key?

Again and again, sandyd, thanks for your help, it is much appreciated.

---

### Post by sandyd on 2015-12-12
It is because keycode 64 is for the alt button. I assume that is a keymap thing, but that is what xev says it is.

If you added the autostart as well, run
```

rm ~/.config/autostart/xmodmap.desktop
```
do a restart, and things should be back to normal. The keymaps don't last through a reboot. You will need to go through the process again, starting from setting the mapping.

For keys pressed simultaneously, you will need to use the addition sign to indicate that keycodes should be pressed together.

For example - alt+dollar sign
```

xmodmap -e "keycode 64 + keycode 85 = zabovedot Zabovedot"
```

---

### Post by Yrvyne on 2015-12-12
Yes, that I realised, and immediately got rid of the alt=&#380;.
My ongoing concern is that 85, 89 and 90 do not produce &#380;&#379;.
I'll try with a different key altogether and post my results albeit I really fancied 85/dollar/&#380;&#379; as a solution.

---

### Post by Yrvyne on 2015-12-13
Hello, again, after much testing I realised why the dedicated Dollar key was working erratically and even involving the left Alt key to produce my required letter.

*TO illustrate my point I copied all the terminal window's output. However, for convenience and easy reference the useful chunks are formatted and also coloured in red.*

This is XEV result for keyboard key Alt_L:

```
Outer window is 0x1e00001, inner window is 0x1e00002

PropertyNotify event, serial 8, synthetic NO, window 0x1e00001,
    atom 0x27 (WM_NAME), time 792466, state PropertyNewValue

PropertyNotify event, serial 9, synthetic NO, window 0x1e00001,
    atom 0x22 (WM_COMMAND), time 792466, state PropertyNewValue

PropertyNotify event, serial 10, synthetic NO, window 0x1e00001,
    atom 0x28 (WM_NORMAL_HINTS), time 792466, state PropertyNewValue

CreateNotify event, serial 11, synthetic NO, window 0x1e00001,
    parent 0x1e00001, window 0x1e00002, (10,10), width 50, height 50
border_width 4, override NO

PropertyNotify event, serial 14, synthetic NO, window 0x1e00001,
    atom 0x143 (WM_PROTOCOLS), time 792467, state PropertyNewValue

MapNotify event, serial 15, synthetic NO, window 0x1e00001,
    event 0x1e00001, window 0x1e00002, override NO

PropertyNotify event, serial 20, synthetic NO, window 0x1e00001,
    atom 0x1ad (_NET_WM_VISIBLE_NAME), time 792469, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x1e00001,
    atom 0x1c3 (_NET_WM_VISIBLE_ICON_NAME), time 792470, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x1e00001,
    atom 0x1dd (_OB_APP_ROLE), time 792470, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x1e00001,
    atom 0x1df (_OB_APP_NAME), time 792470, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x1e00001,
    atom 0x1e0 (_OB_APP_CLASS), time 792470, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x1e00001,
    atom 0x1e1 (_OB_APP_GROUP_NAME), time 792470, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x1e00001,
    atom 0x1e2 (_OB_APP_GROUP_CLASS), time 792470, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x1e00001,
    atom 0x1de (_OB_APP_TITLE), time 792470, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x1e00001,
    atom 0x1e3 (_OB_APP_TYPE), time 792470, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x1e00001,
    atom 0x14c (_NET_WM_ICON), time 792472, state PropertyNewValue

ReparentNotify event, serial 20, synthetic NO, window 0x1e00001,
    event 0x1e00001, window 0x1e00001, parent 0x16003b6,
    (0,0), override NO

PropertyNotify event, serial 22, synthetic NO, window 0x1e00001,
    atom 0x151 (_NET_WM_STATE), time 792474, state PropertyNewValue

ConfigureNotify event, serial 22, synthetic NO, window 0x1e00001,
    event 0x1e00001, window 0x1e00001, (0,0), width 178, height 178,
    border_width 0, above 0x16003e2, override NO

ConfigureNotify event, serial 22, synthetic NO, window 0x1e00001,
    event 0x1e00001, window 0x1e00001, (2,25), width 178, height 178,
    border_width 0, above 0x16003e2, override NO

PropertyNotify event, serial 22, synthetic NO, window 0x1e00001,
    atom 0x148 (_NET_FRAME_EXTENTS), time 792475, state PropertyNewValue

PropertyNotify event, serial 22, synthetic NO, window 0x1e00001,
    atom 0x1c6 (_KDE_NET_WM_FRAME_STRUT), time 792475, state PropertyNewValue

PropertyNotify event, serial 24, synthetic NO, window 0x1e00001,
    atom 0x1c5 (_NET_WM_ALLOWED_ACTIONS), time 792476, state PropertyNewValue

ConfigureNotify event, serial 24, synthetic YES, window 0x1e00001,
    event 0x1e00001, window 0x1e00001, (0,488), width 178, height 178,
    border_width 2, above 0x0, override NO

PropertyNotify event, serial 24, synthetic NO, window 0x1e00001,
    atom 0x14b (_NET_WM_DESKTOP), time 792477, state PropertyNewValue

MapNotify event, serial 43, synthetic NO, window 0x1e00001,
    event 0x1e00001, window 0x1e00001, override NO

VisibilityNotify event, serial 43, synthetic NO, window 0x1e00001,
    state VisibilityUnobscured

Expose event, serial 43, synthetic NO, window 0x1e00001,
    (0,0), width 178, height 10, count 3

Expose event, serial 43, synthetic NO, window 0x1e00001,
    (0,10), width 10, height 58, count 2

Expose event, serial 43, synthetic NO, window 0x1e00001,
    (68,10), width 110, height 58, count 1

Expose event, serial 43, synthetic NO, window 0x1e00001,
    (0,68), width 178, height 110, count 0

PropertyNotify event, serial 43, synthetic NO, window 0x1e00001,
    atom 0x19f (WM_STATE), time 792498, state PropertyNewValue

FocusIn event, serial 44, synthetic NO, window 0x1e00001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 44, synthetic NO, window 0x0,
    keys:  68  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 44, synthetic NO, window 0x1e00001,
    atom 0x1c4 (_NET_WM_ICON_GEOMETRY), time 792518, state PropertyNewValue

PropertyNotify event, serial 45, synthetic NO, window 0x1e00001,
    atom 0x1c4 (_NET_WM_ICON_GEOMETRY), time 792537, state PropertyNewValue

PropertyNotify event, serial 45, synthetic NO, window 0x1e00001,
    atom 0x1c4 (_NET_WM_ICON_GEOMETRY), time 792595, state PropertyNewValue

[COLOR=#ff0000]***KeyPress event***, serial 45, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 797840, (255,-118), root:(257,372),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

***KeyRelease event***, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 797978, (255,-118), root:(257,372),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False[/COLOR]

FocusOut event, serial 48, synthetic NO, window 0x1e00001,
    mode NotifyNormal, detail NotifyNonlinear

PropertyNotify event, serial 48, synthetic NO, window 0x1e00001,
    atom 0x1c4 (_NET_WM_ICON_GEOMETRY), time 801074, state PropertyNewValue
```

In short, on pressing the left Alt key (Alt_L) on its own, keycode 64 is used i.e. **Pressing 64 _and then_ Releasing 64** will consequentially only produce whatever Alt_L is maped for.

The following is the XEV result for Dollar sign dedicated key on the keyboard:

```
Outer window is 0x1e00001, inner window is 0x1e00002

PropertyNotify event, serial 8, synthetic NO, window 0x1e00001,
    atom 0x27 (WM_NAME), time 1409179, state PropertyNewValue

PropertyNotify event, serial 9, synthetic NO, window 0x1e00001,
    atom 0x22 (WM_COMMAND), time 1409179, state PropertyNewValue

PropertyNotify event, serial 10, synthetic NO, window 0x1e00001,
    atom 0x28 (WM_NORMAL_HINTS), time 1409179, state PropertyNewValue

CreateNotify event, serial 11, synthetic NO, window 0x1e00001,
    parent 0x1e00001, window 0x1e00002, (10,10), width 50, height 50
border_width 4, override NO

PropertyNotify event, serial 14, synthetic NO, window 0x1e00001,
    atom 0x143 (WM_PROTOCOLS), time 1409180, state PropertyNewValue

MapNotify event, serial 15, synthetic NO, window 0x1e00001,
    event 0x1e00001, window 0x1e00002, override NO

PropertyNotify event, serial 18, synthetic NO, window 0x1e00001,
    atom 0x1ad (_NET_WM_VISIBLE_NAME), time 1409184, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x1e00001,
    atom 0x1c3 (_NET_WM_VISIBLE_ICON_NAME), time 1409184, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x1e00001,
    atom 0x1dd (_OB_APP_ROLE), time 1409184, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x1e00001,
    atom 0x1df (_OB_APP_NAME), time 1409184, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x1e00001,
    atom 0x1e0 (_OB_APP_CLASS), time 1409184, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x1e00001,
    atom 0x1e1 (_OB_APP_GROUP_NAME), time 1409184, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x1e00001,
    atom 0x1e2 (_OB_APP_GROUP_CLASS), time 1409184, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x1e00001,
    atom 0x1de (_OB_APP_TITLE), time 1409185, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x1e00001,
    atom 0x1e3 (_OB_APP_TYPE), time 1409185, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x1e00001,
    atom 0x14c (_NET_WM_ICON), time 1409187, state PropertyNewValue

ReparentNotify event, serial 18, synthetic NO, window 0x1e00001,
    event 0x1e00001, window 0x1e00001, parent 0x1600564,
    (0,0), override NO

PropertyNotify event, serial 38, synthetic NO, window 0x1e00001,
    atom 0x151 (_NET_WM_STATE), time 1409195, state PropertyNewValue

ConfigureNotify event, serial 38, synthetic NO, window 0x1e00001,
    event 0x1e00001, window 0x1e00001, (0,0), width 178, height 178,
    border_width 0, above 0x1600590, override NO

ConfigureNotify event, serial 38, synthetic NO, window 0x1e00001,
    event 0x1e00001, window 0x1e00001, (2,25), width 178, height 178,
    border_width 0, above 0x1600590, override NO

PropertyNotify event, serial 38, synthetic NO, window 0x1e00001,
    atom 0x148 (_NET_FRAME_EXTENTS), time 1409197, state PropertyNewValue

PropertyNotify event, serial 38, synthetic NO, window 0x1e00001,
    atom 0x1c6 (_KDE_NET_WM_FRAME_STRUT), time 1409197, state PropertyNewValue

PropertyNotify event, serial 41, synthetic NO, window 0x1e00001,
    atom 0x1c5 (_NET_WM_ALLOWED_ACTIONS), time 1409202, state PropertyNewValue

ConfigureNotify event, serial 41, synthetic YES, window 0x1e00001,
    event 0x1e00001, window 0x1e00001, (0,488), width 178, height 178,
    border_width 2, above 0x0, override NO

PropertyNotify event, serial 41, synthetic NO, window 0x1e00001,
    atom 0x14b (_NET_WM_DESKTOP), time 1409202, state PropertyNewValue

MapNotify event, serial 43, synthetic NO, window 0x1e00001,
    event 0x1e00001, window 0x1e00001, override NO

VisibilityNotify event, serial 43, synthetic NO, window 0x1e00001,
    state VisibilityUnobscured

Expose event, serial 43, synthetic NO, window 0x1e00001,
    (0,0), width 178, height 10, count 3

Expose event, serial 43, synthetic NO, window 0x1e00001,
    (0,10), width 10, height 58, count 2

Expose event, serial 43, synthetic NO, window 0x1e00001,
    (68,10), width 110, height 58, count 1

Expose event, serial 43, synthetic NO, window 0x1e00001,
    (0,68), width 178, height 110, count 0

PropertyNotify event, serial 43, synthetic NO, window 0x1e00001,
    atom 0x19f (WM_STATE), time 1409226, state PropertyNewValue

FocusIn event, serial 44, synthetic NO, window 0x1e00001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 44, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 44, synthetic NO, window 0x1e00001,
    atom 0x1c4 (_NET_WM_ICON_GEOMETRY), time 1409279, state PropertyNewValue

PropertyNotify event, serial 45, synthetic NO, window 0x1e00001,
    atom 0x1c4 (_NET_WM_ICON_GEOMETRY), time 1409349, state PropertyNewValue

[COLOR=#ff0000]**KeyPress event**, serial 45, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1413134, (611,69), root:(613,559),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

_KeyPress event_, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1413139, (611,69), root:(613,559),
    state 0x8, keycode 90 (keysym 0xff9e, KP_Insert), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

_KeyRelease event_, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1413145, (611,69), root:(613,559),
    state 0x8, keycode 90 (keysym 0xff9e, KP_Insert), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

_KeyPress event_, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1413150, (611,69), root:(613,559),
    state 0x8, keycode 90 (keysym 0xff9e, KP_Insert), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

_KeyRelease event_, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1413155, (611,69), root:(613,559),
    state 0x8, keycode 90 (keysym 0xff9e, KP_Insert), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

_KeyPress event_, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1413161, (611,69), root:(613,559),
    state 0x8, keycode 89 (keysym 0xff9b, KP_Next), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

_KeyRelease event_, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1413166, (611,69), root:(613,559),
    state 0x8, keycode 89 (keysym 0xff9b, KP_Next), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

_KeyPress event_, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1413171, (611,69), root:(613,559),
    state 0x8, keycode 85 (keysym 0xff98, KP_Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

_KeyRelease event_, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1413177, (611,69), root:(613,559),
    state 0x8, keycode 85 (keysym 0xff98, KP_Right), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

_**KeyRelease event**_, serial 48, synthetic NO, window 0x1e00001,
    root 0x190, subw 0x0, time 1413182, (611,69), root:(613,559),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False[/COLOR]

FocusOut event, serial 48, synthetic NO, window 0x1e00001,
    mode NotifyNormal, detail NotifyNonlinear

PropertyNotify event, serial 48, synthetic NO, window 0x1e00001,
    atom 0x1c4 (_NET_WM_ICON_GEOMETRY), time 1431584, state PropertyNewValue
```

```
Keycode Names
64 - Left Alt key - Alt_L
90 - Insert - KP_Insert
89 - Pg Dn (Page Down) - KP_Next
85 - Right Arrow Key - KP_Right
```

_But_ when pressing the dedicated Dollar sign, a series of events take place: 
```
Pressing 64 (holding the key)
then pressing 90, 
releasing 90, 
pressing 90 (again), 
releasing 90 (again), 
pressing 89, 
releasing 89, 
pressing 85, 
releasing 85, 
finally Releasing 64
```

Thus, in light of this, can I somehow emulate this behaviour so as to have the dedicated Dollar sign functional?

```
Press & Hold Alt_L, 
Press Insert, 
Release Insert, 
Press Insert (again), 
Release Insert (again), 
Press Page Down, 
Release Page Down, 
Press Right Arrow, 
Release Right Arrow, 
Release Alt_L
```

---

### Post by Yrvyne on 2015-12-13
On further research, I have found that xmodmap cannot send strokes (keypresses and keyreleases) individually as I suggested in my previous post.
xdotool, on the other hand, is the ideal candidate for such a task.
Yet, I am having major problems combining key & keydown & keyup as well as finding a way to have xmodmap use xdotool to simulate the keystrokes required as instructed by xdotool.

My idea is to create something in the lines of:

```
xmodmap -e "xdotool keydown Alt_L key KP_Insert+KP_Insert+KP_Next+KP_Right keyup Alt_L = zabovedot Zabovedot"
```

or

```
xmodmap -e "xdotool keydown keycode 64 key keycode 90 + keycode 90 + keycode 89 + keycode 85 keyup keycode 64 = zabovedot Zabovedot"
```

or

```
xmodmap -e "xdotool keydown keysym 0xffe9 key keysym 0xff9e + keysym 0xff9e +  keysym 0xff9b + keysym 0xff98 keyup keysym 0xffe9 = zabovedot Zabovedot"
```

None of the above have worked. Not that xmodmap and xgotool are incompatible but because my syntax, structuring and code is incorrect. I admit that this is my first time trying such a complicated endeavour. Any help in any part of my quest is greatly appreciated, Cheers!

---

### Post by sandyd on 2015-12-14
Sorry for not being able to help, but I'm afraid I'm not familiar with having xev show multiple presses when pressing a key, that is just something I haven't encountered on my own keyboard.

Good Luck!

---

### Post by Yrvyne on 2015-12-16
On the contrary, you have given me a detailed step-by-step tutorial on how to achieve custom key mapping.
The only thing missing is sorting a key that has a sequence of keys for activation.
Once we are through that, then anyone who would have an issue similar to mine can be on his way as well.
So if anyone else can step in and write his thought and suggestions, they would be greatly appreciated.

On a side note, I know, I can also map another normal key, but what is the challenge in that!
Also, having a fully-used keyboard with custom single-press keys is a pretty convenient idea.

Cheers, all!

---

