---
title: "Gtk::Stock doesn't use system settings"
date: 2009-05-09
forum: Programming Talk
---

### Post by cl333r on 2009-05-09
Folks, I use Gtk::Stock to create a button and I get this situation: Gnome is configured to show "icons only" (in System-Preferences-Appearance-Interface), but my button shows both the text label and the icon.
How do I tell the button to use "the system settings" and thus in my case display only the icon?

Here's how I create the button:
```

Gtk::Button *pForwardBt = new Gtk::Button(Gtk::Stock::GO_FORWARD);
myContainer.pack_start(*pForwardBt, Gtk::PACK_SHRINK);

```

---

### Post by cl333r on 2009-05-09
Uh.. looks like there's no such option. I ended up doing this to partially solve the problem:

```

Gtk::Button *pForwardBt = new Gtk::Button();
Gtk::Widget *pImage = manage (new Gtk::Image(Gtk::Stock::GO_FORWARD, Gtk::ICON_SIZE_BUTTON));
pForwardBt->add(*pImage);

```

---

