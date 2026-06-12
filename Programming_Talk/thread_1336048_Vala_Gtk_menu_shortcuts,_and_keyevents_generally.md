---
title: "Vala Gtk menu shortcuts, and keyevents generally"
date: 2009-11-24
forum: Programming Talk
---

### Post by kumoshk on 2009-11-24
Question #1:
How do I set up menu shortcuts in Gtk? I have menus, and they have mnemonics, but I don't see any examples or documentation as to how one can set up shortcuts.

I figured they'd have functionality that doesn't require one to work with key events (most of the GUI libraries I've tried do, anyhow).

Here's an example menu:
```
var menubar = new MenuBar();
var file_menu = new Menu();
var open_item=new MenuItem.with_mnemonic("_Open");
var quit_item=new MenuItem.with_mnemonic("_Quit");
file_menu.append(open_item);
file_menu.append(quit_item);
open_item.activate+=on_open;
quit_item.activate+=Gtk.main_quit;
var file_launcher=new MenuItem.with_mnemonic("_File");
file_launcher.set_submenu(file_menu);
menubar.append(file_launcher);
```

Question #2:
How can I get key combinations to register in KeyEvents? I mean, I want Ctrl+Y to signal a redo function, but it only catches Ctrl or Y (not both) in string form. I'm not sure how to do it in non-string form.

I've been using this
```
string key = Gdk.keyval_name (event.keyval);
```
to get my key events, but I figure I have to do something else, since it only returns one.

---

### Post by kumoshk on 2010-04-07
Question #1 is solved. As for #2 &#8230;

I've figured out how to do this while a menu is visible, but I'd like to do it in full-screen mode, too.

Anyway, here's the menu method:
```
right_item.add_accelerator("activate", keyGroup, 0x0072, Gdk.ModifierType.CONTROL_MASK, Gtk.AccelFlags.VISIBLE);
```
right_item is a MenuItem. 0x0072 is the hexadecimal character value for r. Typing Ctrl+r will call the MenuItem's function. However, if the menu is invisible, it doesn't work.

---

### Post by SledgeHammer_999 on 2010-04-07
Try doing this(I suppose you use Vala and Vala is a bit C-ish):
```
right_item.add_accelerator("activate", keyGroup, 'R', Gdk.ModifierType.CONTROL_MASK, Gtk.AccelFlags.VISIBLE);
```

---

### Post by Linteg on 2010-04-07
Have you added the Gtk.AccelGroup to the window?:
```
my_window.add_accel_group (keyGroup)
```

---

### Post by kumoshk on 2010-04-07
> **Linteg said:**
> Have you added the Gtk.AccelGroup to the window?:
```
my_window.add_accel_group (keyGroup)
```

Ah, I didn't know about AccelGroups or adding them to windows. Sounds like it should work, when I have a moment tonight or so to try it out. Thanks! This will definitely improve things for me, if it works.

---

### Post by kumoshk on 2010-04-08
> **kumoshk said:**
> Ah, I didn't know about AccelGroups or adding them to windows. Sounds like it should work, when I have a moment tonight or so to try it out. Thanks! This will definitely improve things for me, if it works.
Actually, sorry, yes I did that already. But my misunderstanding of that has given me some ideas of things to experiment with.

---

### Post by kumoshk on 2010-04-08
> **kumoshk said:**
> Actually, sorry, yes I did that already. But my misunderstanding of that has given me some ideas of things to experiment with.

I don't think using accelerators will help. They don't work when the menu is invisible. The accelerators don't seem to work on other widgets besides MenuItems.

However, if there were some way I could do a boolean check to see if modifier keys are being help down (control, alt, shift), that would solve the problem. Is there some function for this?

---

### Post by kumoshk on 2010-04-08
> **kumoshk said:**
> Actually, sorry, yes I did that already. But my misunderstanding of that has given me some ideas of things to experiment with.

I've discovered a way! Finally. Here's a random example of how to make Control+F11 work (instead of just F11):

```
private bool onKey(Gdk.EventKey event)
{        
    string key = Gdk.keyval_name(event.keyval);
    if(key=="F11" && (event.state & Gdk.ModifierType.CONTROL_MASK) != 0)
    {
        this.fullScreen();
        return true;
    }
}
```

---

### Post by SledgeHammer_999 on 2010-04-08
> **kumoshk said:**
> I don't think using accelerators will help. **They don't work when the menu is invisible.** The accelerators don't seem to work on other widgets besides MenuItems.

What do you mean by invisible? Do you mean doing a set_sensitive(false)? (the equivalent in Vala). If yes, then you cannot receive the key-combination when the widget is insensitive.

---

### Post by kumoshk on 2010-04-08
> **SledgeHammer_999 said:**
> What do you mean by invisible? Do you mean doing a set_sensitive(false)? (the equivalent in Vala). If yes, then you cannot receive the key-combination when the widget is insensitive.

Nope. I mean such as this:
```
menubar.hide();
```

---

