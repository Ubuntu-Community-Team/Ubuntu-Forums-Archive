---
title: "How to modify a Gnome Shell Extension?"
date: 2012-06-04
forum: Programming Talk
---

### Post by Bazon on 2012-06-04
Hello!

I'd like prevent Gnome-Shell from changing the workspace when clicking on an icon in the applauncher when a window is opened on another workspace. I'd prefer to have a new window on the momentary workspace instead.

A step to that could be the [Dash Click Fix Extension]("https://extensions.gnome.org/extension/67/dash-click-fix/"): 
With that extension, a click on the applauncher always opens a new window.

So my question is:
**How is it possible to open a new window only, when there is no window from this program on the current workspace?**

Momentary, the code for the extension is this (stored in ~/.local/share/gnome-shell/extensions/DashClickFix@evotex.ch):
```
/**
 * Desc: this extension "fixes" the dash's default behavior when you 
 *       click on an icon. The defualt is to launch the app if none is 
 *       running and to switch to the current instance if it is already 
 *       running. This extension changes that to instead of switching to 
 *       it if it is already running it always launches a new instance.
 * 
 * Author: Gabriel Rossetti
 * Date: 2011-12-08
 * Version: 1.0
 */
const Main = imports.ui.main;
const AppDisplay = imports.ui.appDisplay;
const Shell = imports.gi.Shell;
const Clutter = imports.gi.Clutter;


var _original = null;

/**
 * The new version of the function, this always lanches a new version of 
 * the app regardless of if it is already running or not.
 * 
 * @param event the current event
 */
function _onActivate(event) {
  this.emit('launching');

  if (this._onActivateOverride) {
    this._onActivateOverride(event);
  } else {
    this.app.open_new_window(-1);
  }
  Main.overview.hide();
}

/**
 * Initialize the extension
 */
function init() {
  _original = AppDisplay.AppWellIcon.prototype._onActivate;
}

/**
 * Enable the extension
 */
function enable() {
  AppDisplay.AppWellIcon.prototype._onActivate = _onActivate;
}

/**
 * Disable the extension
 */
function disable() {
  
  AppDisplay.AppWellIcon.prototype._onActivate = _original;
}
```

Has anybody an idea?
How to modify or how to find out how to modify?
I got no experience in writing Gnome-Shell-Extensions so far.

Thanks!

---

### Post by Bazon on 2012-06-05
No one has an idea? :-(

---

### Post by Bazon on 2012-06-10
Not even an idea where else to ask?
or a link where to start reading?

---

### Post by markbl on 2012-06-10
I've played around with my own gnome-shell extensions and I just started at the recommended place which is [https://live.gnome.org/GnomeShell/Extensions](https://live.gnome.org/GnomeShell/Extensions) and then followed the links from there, particularly Finbarr Murphy's "Musings" posts referenced there.

---

### Post by Bazon on 2012-06-10
Thank you very much! :-)
I'll see, where I can get with that...

---

### Post by Bazon on 2012-09-08
It took some time to get started, but following the links here, looking in other Gnome-Shell-Extensions (in ~/.local/share/gnome-shell/extensions/) and in Gnome-Shell's original Code (in /usr/share/gnome-shell/js/ui) I'm ready now:

[https://extensions.gnome.org/extension/440/workspace-separation-on-dash/](https://extensions.gnome.org/extension/440/workspace-separation-on-dash/)

It's for Gnome-Shell 3.4, if you want to try it on another Version of Gnome-Shell, just send me a PM, I'm also interested in knowing on which Versions it works. :-)

---

