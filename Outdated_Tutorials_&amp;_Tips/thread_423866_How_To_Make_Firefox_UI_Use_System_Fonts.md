---
title: "How To Make Firefox UI Use System Fonts"
date: 2007-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by tturrisi on 2007-04-26
Most application windows in Gnome use the system font which is set via Preferences > Fonts.  The font family and font size can be set for:
[list][*]Application font[*]Document font[*]Desktop font[*]Window title font[*]Fixed width font[/list]

However, the Firefox User Interface (UI) is not controlled by these system settings.  The appearance of the Firefox UI is controlled by Firefox's own XUL code.  XUL is basically a combination of XHTML, CSS and Javascript.  The UI appearance is styled using CSS.  CSS controls the appearance & some behavior of windows, dialogs, font sizes, font family, and more.

Thus, to make Firefox look like other application windows, such as Nautilus, all one need do is create and/or edit one file.  In your Home directory is a folder for Firefox.  On Debian, the folder is:
**/home/user-name/.mozilla/firefox/xxxxxxxx.default**

Inside the xxxxxxxx.default directory is another directory called:
**/chrome** and inside the chrome directory is a file called:
**userChrome-example.css**
Open this file in a text editor and you will see instructions/examples of how the Firefox UI can be changed.  Many things can be changed and many are documented at the Mozilla Web site here:
[http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)

This HowTo demonstrates how to change the Menus in Firefox so they use the same font as other application windows in Gnome.  The system font I prefer for Application windows is Trebuchet MS size 10, which is a Windows TTF in the package msttcorefonts.  It's a "clean-looking" font and easy on my eyes.  But any font can be used here so long as the font is installed on your system.

**Example:**
[list][*]Add this code to your userChrome-example.css:
```
/* menus */
menubar, menubutton, menulist, menu, menuitem {
  font-family: Trebuchet MS !important;
  font-size: 3.5mm !important;
}
```
[*] rename userChrome-example.css to [color=red]userChrome.css[/color]
[*]open Firefox or close & restart Firefox if already opened.[/list]

---

### Post by schnupi on 2007-04-26
thanks very much for this!

---

