---
title: "[SOLVED] Ctrl+C won't copy, Ctrl+V won't paste"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by martynmoore on 2008-11-30
Hi all

I can't get Ctrl+C or Ctrl+V to copy or paste. I can survive with rightclick menus, but it's annoying.

Any suggestions?

---

### Post by Tom--d on 2008-11-30
Works for me.

In the terminal, its CRTL + SHIFT + C for copy and paste is CRTL+SHIFT+V

---

### Post by martynmoore on 2008-11-30
Hi Tom.

Yes, that helps with copy and paste in Terminal. Thanks.

But the Ctrl+C and V doesn't work in Firefox, where I'm most likely to be copying from.

The commands don't work in OpenOffice, either.

---

### Post by unutbu on 2008-11-30
I'm not sure I know the answer, but would you please post the output of 
```

gconftool-2 -a /desktop/gnome/interface
```

---

### Post by martynmoore on 2008-11-30
gconftool-2 -a /desktop/gnome/interface
 toolbar_style = both
 gtk-im-status-style = callback
 document_font_name = Sans 10
 monospace_font_name = Monospace 10
 enable_animations = true
 gtk_key_theme = Default
 menus_have_tearoff = false
 cursor_blink_time = 1200
 font_name = Sans 10
 cursor_blink = true
 gtk-im-module = 
 show_unicode_menu = true
 menus_have_icons = true
 use_custom_font = false
 accessibility = false
 can_change_accels = false
 gtk_theme = Human-Clearlooks
 menubar_detachable = false
 gtk-im-preedit-style = callback
 status_bar_meter_on_right = false
 file_chooser_backend = gio
 icon_theme = Human
 toolbar_detachable = false
 toolbar_icons_size = large-toolbar
 menubar_accel = F10
 show_input_method_menu = true

---

### Post by drs305 on 2008-11-30
In firefox or other apps, can you left click/hold/drag to highlight an entry with the mouse and then middle click to paste it?

---

### Post by dazzlindonna on 2008-11-30
Try disabling all your Firefox add-ons.  One of the extensions might be either causing the problem or overriding those keystrokes.

---

### Post by martynmoore on 2008-11-30
That's brilliant drs305, I had no idea I could do that. I guess that's why I'm in "absolute beginners", I suppose.

That will make life easier, but I will also keep trying to do the old Ctrl+C thing when I forget.

If I can get that to work, too, I'll even feel better about my team going out of the FA Cup today!

BTW, I don't have a three button mouse, but my scroll wheel clicks. However, I can just 'drag and drop'.

---

### Post by martynmoore on 2008-11-30
It might be worth adding at this stage, that Ctrl+A doesn't "select all", not in gedit or OOo3 writer. However, Shift+Ctrl+A _does_ select all in this text editor right now.

Weird, eh?

---

### Post by Bölvaður on 2008-11-30
> **martynmoore said:**
> Weird, eh?

Yes. as Shift+Ctrl+A does not work for me but Ctrl+A does
I cannot remember seeing where to change those bindings though :( but it looks like your bindings have gone sour :KS

---

### Post by martynmoore on 2008-11-30
Thanks, Bölvaður. Don't really know what that means.

But with ubuntu 8.1, you can use Ctrl+A to select all the text in a gedit document, can you?

---

### Post by drs305 on 2008-11-30
> **martynmoore said:**
> Thanks, Bölvaður. Don't really know what that means.

Just for general knowledge, the keybindings Bolvador is referring to are perhaps those set and accessible through the gconf-editor.

Although your problems appear to be more general than a single keybinding, you could open the gconf editor ( in terminal, "gconf-editor" ) and do a search (Edit, Find, tick 'Search also in key values') for "<Control>". You could look through the results to see if there were any bindings to <Control> that might be effecting your key strokes. It isn't likely but you never know.

---

### Post by martynmoore on 2008-11-30
Hi drs305,

I did the configuration editor thing and got a long list of commands that use Ctr with other keys. All seemed to make sense and none had Ctrl+C, V or A doing anything. Those combinations don't seem to be configured to do anything.

---

### Post by drs305 on 2008-11-30
Per our PMs, here is the xev screenshot I get when I hit the left CTRL key:

---

### Post by martynmoore on 2008-11-30
Nope, drs305, nothing like that in mine. Here's my second attempt, showing a left Ctrl followed by a right. No mention of key.

---

### Post by drs305 on 2008-11-30
In a terminal, try reassigning the left CTRL key. Keycode 37 is normally the code for it. The change will only last for this session. 
```

xmodmap -e "keycode 37 = Super_L"

```

Note to others: We have diverged on an unlikely path to a solution. Please feel free to offer different solutions. (I will, however, delete this note if it works, ;-)  ).

---

### Post by martynmoore on 2008-11-30
OK, did that.

Ctrl+C is copying, but Ctrl+V does not paste and Ctrl+A does not select all.

"xev" producing same result, no data like your screengrab in Terminal.

Just had a thought.

Maybe Ctrl+C has been copying all along. To paste I can still do right click and select Paste in menu. But I never tried that before.

Because it wouldn't paste on Ctrl+V, I was assuming it hadn't copied on Ctrl+C. But maybe it did.

Sorry.

Will pick this up again tomorrow.

Thanks.

---

### Post by martynmoore on 2008-12-05
Finally resorted to a fresh install. All works fine so far. Thanks to everyone for their help on this.

---

