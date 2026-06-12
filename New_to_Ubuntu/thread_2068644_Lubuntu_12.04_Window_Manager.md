---
title: "Lubuntu 12.04 Window Manager"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by fritual on 2012-10-09
Hi,
Desktop Session Settings default to 'openbox-lubuntu'.

Can this be changed?  I need windows manager to set both:
1) snap to edges
2) snap to other windows

What are the options, to get this functional?

fritual

---

### Post by MG&amp;TL on 2012-10-09
There are many different choices in terms of WM; compiz is one that provides all of those features and more.

[http://ubuntuforums.org/showpost.php?p=9875054&postcount=6](http://ubuntuforums.org/showpost.php?p=9875054&postcount=6) works for me. Obviously, if you want to use a different one, just replace the compiz command with the window manager's replace command.

---

### Post by fritual on 2012-10-09
> **MG&TL said:**
> There are many different choices in terms of WM; compiz is one that provides all of those features and more.

[http://ubuntuforums.org/showpost.php?p=9875054&postcount=6](http://ubuntuforums.org/showpost.php?p=9875054&postcount=6) works for me. Obviously, if you want to use a different one, just replace the compiz command with the window manager's replace command.

Hi,
I just tried unsuccessfully to replace Openbox w/compiz and xfwm4:
Lubuntu 12.04 error flagged w/compiz:
```

lu@bu:~$ sudo compiz
password for lu: 
compiz (core) - Error: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager.
lu@bu:~$ compiz --replace
Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done

```NO ENDING TERMINAL PROMPT!

Lubuntu 12.04 error trapped launching xfwm4:
```

$ sudo xfwm4 --replace

(xfwm4:1838): GLib-CRITICAL **: g_str_has_prefix: assertion `prefix != NULL' failed

(xfwm4:1838): xfwm4-WARNING **: The property '/general/double_click_distance' of type int is not supported

(xfwm4:1838): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.32.3/./gobject/gvalue.c:185: cannot initialize GValue with type `gint', the value has already been initialized as `gint'

```What is the trouble?  Lubuntu is installed on LiveUSB media, w/EXT4.

What category in the start menu should the new Window Manager's be found, to adjust settings?  No problem finding Openbox.

Regards,
fritual

---

### Post by MG&amp;TL on 2012-10-10
Most window manager's "--replace" option doesn't end, mostly because it's still running. My understanding is that if you put it in the autostart file as suggested in that link, LXDE forks off the lines as individual sub-processes, so it won't hang the start sequence. 

However, you should have noticed a difference in appearance: I believe compiz turns on "Wobbly Windows" by default, so you can see it's there.

If you want to configure the WM, most have a configuration GUI. For compiz, the package is *compizconfig-settings-manager* , for Xfwm, I have no clue, but I'm sure there is one.

---

### Post by fritual on 2012-10-10
> **MG&TL said:**
> Most window manager's "--replace" option doesn't end, mostly because it's still running. My understanding is that if you put it in the autostart file as suggested in that link, LXDE forks off the lines as individual sub-processes, so it won't hang the start sequence. 

However, you should have noticed a difference in appearance: I believe compiz turns on "Wobbly Windows" by default, so you can see it's there.

If you want to configure the WM, most have a configuration GUI. For compiz, the package is *compizconfig-settings-manager* , for Xfwm, I have no clue, but I'm sure there is one.
Hi,
I followed your suggestion, plugging both WM into autostart.  Openbox does not acknowledge either compiz or xfwm4!

It appears openbox can be patched to do these functions:

[link]("http://crunchbanglinux.org/forums/topic/13968/aero-snap-in-openbox/")

How would this translate to Lubuntu 12.04?

Yours,
fritual

---

### Post by MG&amp;TL on 2012-10-10
> **fritual said:**
> Hi,
I followed your suggestion, plugging both WM into autostart.  Openbox does not acknowledge either compiz or xfwm4!

It appears openbox can be patched to do these functions:

[link]("http://crunchbanglinux.org/forums/topic/13968/aero-snap-in-openbox/")

How would this translate to Lubuntu 12.04?

Yours,
fritual

Huh, bizarre. 

Good find, nice for people who want to run openbox but want snap too. 

It should be exactly the same, Lubuntu is still LXDE. :)
EDIT: Assumptions are a bad thing. Ignore this, vasa1's answer is way better.

---

### Post by vasa1 on 2012-10-10
> **fritual said:**
> ...
It appears openbox can be patched to do these functions:

[link]("http://crunchbanglinux.org/forums/topic/13968/aero-snap-in-openbox/")

How would this translate to Lubuntu 12.04?
...
Well, I'm not sure what you need to know but Lubuntu has a file called **lubuntu-rc.xml** in your ~/.config/openbox folder and this is the file into which you stick the appropriate code in the appropriate section **after making a backup for safety**.

The lubuntu-rc.xml file is divided into various sections and the author indicates that the code goes into the section that starts with <keyboard> and ends with </keyboard>.

Then, after saving and closing the file, run **openbox --reconfigure** in a terminal to make the changes take effect.

---

### Post by vasa1 on 2012-10-11
I'm looking at the link Fritual provided. One (obvious) precaution is to ensure that the key combinations aren't already in use elsewhere!
For example:
```

<keybind key="C-Tab">
       <action name="UnmaximizeFull"/>
       <action name="MaximizeVert"/>
       <action name="MoveResizeTo">
         <width>640</width>
       </action>
       <action name="MoveToEdgeWest"/>
</keybind>

```
Control-Tab is one way to switch tabs in Firefox and Chrome.

---

### Post by vasa1 on 2012-10-11
I went with C-S-Left and C-S-Right. The author very kindly did the math for various screen dimensions. Since mine is 1366/768, I went for the code with 683 in it.
```

    <keybind key="C-S-Left">
      <action name="UnmaximizeFull"/>
      <action name="MaximizeVert"/>
      <action name="MoveResizeTo">
        <width>683</width>
      </action>
      <action name="MoveToEdgeWest"/>
    </keybind>
    <keybind key="C-S-Right">
      <action name="UnmaximizeFull"/>
      <action name="MaximizeVert"/>
      <action name="MoveResizeTo">
        <width>683</width>
      </action>
      <action name="MoveToEdgeEast"/>
    </keybind>

```

And thanks to fritual for the link!

---

### Post by vasa1 on 2012-10-11
And this is for splitting horizontally:
```

    <keybind key="C-S-Up">
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <width>1366</width>
        <height>384</height>
      </action>
      <action name="GrowToEdgeWest"/>
    </keybind>
    <keybind key="C-S-Down">
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>-0</y>
        <width>1366</width>
        <height>384</height>
      </action>
      <action name="GrowToEdgeWest"/>
    </keybind>


```
This is borrowed from a post in the [Openbox Hacks and Configs Thread]("https://bbs.archlinux.org/viewtopic.php?pid=732569#p732569").
The height needs some more tweaking because of the panel.

**EDIT:**I'm not confident about this one :(

---

### Post by vasa1 on 2012-10-12
In all four cases, I changed C-S to W.
That's because C-S-Left/Right/Up/Down work to select text and extend text selections when a text area is in focus.

---

### Post by TREESofRIGHTEOUSNESS on 2012-12-25
If this solved your issue please close the thread.  I am very surprised you didn't find compiz to work.  Alt+F2 
```
compiz --replace 
```
will replace openbox with compiz.

---

