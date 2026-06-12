---
title: "Equivalent to Windoes API for LINUX"
date: 2007-09-08
forum: Programming Talk
---

### Post by Fixman on 2007-09-08
Is there a way (yes, there is a way, but how) to do an equivalent of the windows API (windows, buttons and stuff) for linux?

In C or C++, but preferibily on C

---

### Post by CptPicard on 2007-09-08
Theoretically, WINE, but... *why?*

If you're coding something, code against native APIs... otherwise use Windows...

---

### Post by Fixman on 2007-09-08
> **CptPicard said:**
> Theoretically, WINE, but... *why?*

If you're coding something, code against native APIs... otherwise use Windows...

Err...cause I want to delevop applications with buttons on linux?

---

### Post by CptPicard on 2007-09-08
Then you don't want an "Windows API equivalent", strictly speaking ;)

Depends on which desktop environment / widget set you want to code against. On Linux there are multiple alternatives... if you're on KDE, look at Qt/KDE (possibly using KDevelop), on Gnome you'll code against GTK (look at Glade for an UI designer), or if you want to be portable, check out wxWidgets...

---

### Post by gnusci on 2007-09-08
Give a look here:

[http://en.wikipedia.org/wiki/Widget_toolkit#Based_on_C_or_C.2B.2B_.28including_bindings_to_other_languages.29](http://en.wikipedia.org/wiki/Widget_toolkit#Based_on_C_or_C.2B.2B_.28including_bindings_to_other_languages.29)

---

### Post by kvorion on 2007-09-08
You want to take a look at GTK libraries. Glade is a good UI builder

---

### Post by happysmileman on 2007-09-08
There is no real "WinAPI" on Linux (and if there is it's not worth using)

There's QT/KDE and GTK/GNOME, both will work on either KDE or GNOME, but it's better to decide which one to use and stick with it instead of trying to do both.

The QT/KDE libraries are much easier to use as well as being much more useful (KDE has it's own HTML renderer, syntax highlighting textarea etc. All of which can be used without having to code them yourself or copy code, which makes the code neater, easier to write and better integrated with KDE)

---

### Post by j_g on 2007-09-08
Since you prefer C, then don't bother with QT. That is designed to be used with C++. Go with GTK. And definitely get the Glade3 window designer to layout your GTK window(s) and its controls. Glade3 is sort of like Visual C++'s dialog editor (or the "form editor" in the newer NET stuff), albeit not as helpful in generating code. You graphically layout your window and its controls, by dragging/dropping controls where you want them in the window, and position/size them with the mouse. Then, you save your "dialog template", to be loaded/displayed by your app similiarly to how you use Windows' LoadDialog() to load a dialog from your Windows EXE's resources. It's a similiar concept, except for the following differences:

1) Instead of putting the "dialog template" as some resource embedded in your EXE, Glade produces a separate "text (XML) file" containing your dialog template(s). You ship this file along with your GTK EXE. Your app calls the function glade_xml_new() (in the libglade library) to load/display your window from the XML file, in a similiar way to Windows' LoadDialog().

2) GTK puts all of its controls inside of "sub-windows" referred to as "containers". It does this in order to let GTK auto-arrange and resize controls when the user resizes the window. Under Windows, your app does any resize/reposition of controls itself (typically when you get a WM_SIZE message), if that behavior is desired. This makes GTK window layout a bit more complicated than doing the same under Windows, since you need to first divide your window into a bunch of "containers", and then put the controls inside of these containers. Personally, I prefer the Windows way. But at least the concept is fairly similiar, so a Windows programmer can deal with it.

3) In Windows, when the user operates a control, you get various "window messages" passed to a particular function in your app (ie, your window procedure). For example, if the user clicks on a button, you get a WM_COMMAND message with a button ID and "notification code". You don't have to do anything in order to have the OS notify you when the user clicks on the button.

With GTK (and other Linux GUI toolkits), you have to tell the toolkit that you want to be notified of whatever particular events you wish for whatever controls you have. For example, you have to say "I want to be informed whenever the user clicks upon this particular button". You call a GTK API to "trap" this particular button's "click signal". And you pass the address of a function you want called by the toolkit when the user clicks on the button. You have to do this with every single "event" that can happen with a control, if you wish to be notified of those events. For example, if you want to know about a "combo box" having an item being selected, as well as its listbox being dropped down, you have to trap both of those events (ie, signals). So again, it's more work to setup the handling of control events in Linux than it is in Windows. But once you grasp the concept, then it's just a matter of doing a bit more work than you'd have to do under Windows.

Now Linux dev tools -- especially the IDEs, ugh. That's where you really feel the hurt when you move from Windows to Linux. Say hello to convoluted text-mode tools.

Beware the quality of advice given to Windows programmers in these forums. I have found much of the information to be inaccurate, and often given by people who have little to no practical Windows programming experience. Just because someone responds (and there are a couple people who post in virtually every thread on this forum) does not mean you will be receiving a useful answer. You'll need to learn who gives you good info, and who is just talking for the sake of talking.

---

### Post by pmasiar on 2007-09-09
> **j_g said:**
> Beware the quality of advice given to Windows programmers in these forums. ... You'll need to learn who gives you good info, and who is just talking for the sake of talking.

This is not specific to this forum: every forum is populated by wannabes who want to substitute attitude instead of experience.

BTW j_g advice about windows is good and to the point, you can rely on it. j_g just little dislikes Linux-side tools. Many other people like them more than windows-side developer's tools, big part is matter of opinion.

---

### Post by CptPicard on 2007-09-09
> **j_g said:**
> So again, it's more work to setup the handling of control events in Linux than it is in Windows. But once you grasp the concept, then it's just a matter of doing a bit more work than you'd have to do under Windows.

Essentially, it's one line of code per dispatching an event somewhere (anywhere), and you can create fairly interesting combinations of these connections, at least with Qt (like a signal-to-signal). I have no experience of GTK. I fail to see how this is a worse mechanism than on Windows where it seems like you end up with some kind of centralized monster function where you do all your dispatching manually...

---

### Post by j_g on 2007-09-09
> **CptPicard said:**
> it's one line of code per dispatching an event somewhere

Yes, but on Windows, you automatically receive feedback on (just about) every event that happens with every control. You don't have to inform the "GUI toolkit" what events on what controls you want. That's why I therefore say that there's less setup on Windows.

The fact that the messages go through one function is a moot point here.

---

