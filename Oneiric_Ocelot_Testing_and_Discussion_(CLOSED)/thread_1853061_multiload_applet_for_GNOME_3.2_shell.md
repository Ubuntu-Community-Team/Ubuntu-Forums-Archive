---
title: "multiload applet for GNOME 3.2 shell?"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgarman on 2011-10-01
Hello,

I'd like to use the GNOME multiload applet (or its current equivalent) in GNOME shell. In Unity I was able to do this by installing the indicator-multiload package. 

I'm now using the GNOME 3.2 shell and see that the multiload applet pops up from the lower-right corner of the screen but then auto-hides.

Is there a way to get those applets to always stay on the screen? Or can I move the applet up into the top panel?

Thanks,

Scott

---

### Post by tista on 2011-10-02
> **sgarman said:**
> Hello,

I'd like to use the GNOME multiload applet (or its current equivalent) in GNOME shell. In Unity I was able to do this by installing the indicator-multiload package. 

I'm now using the GNOME 3.2 shell and see that the multiload applet pops up from the lower-right corner of the screen but then auto-hides.

Is there a way to get those applets to always stay on the screen? Or can I move the applet up into the top panel?

Thanks,

Scott

Hi Scott,

We could move such "low-right" launched applet to top-right...
but if it goes on, we need to know what the apps-name is...
For example, syspeek, yeah cool system monitor, it names "syspeek" to be defined. so we could do like this:
```
/* -*- mode: js2; js2-basic-offset: 4; indent-tabs-mode: nil -*- */

const Lang = imports.lang;
const Shell = imports.gi.Shell;
const Signals = imports.signals;

const MessageTray = imports.ui.messageTray;
const NotificationDaemon = imports.ui.notificationDaemon;
const Util = imports.misc.util;

const STANDARD_TRAY_ICON_IMPLEMENTATIONS = {
    'bluetooth-applet': 'bluetooth',
    'gnome-volume-control-applet': 'volume', // renamed to gnome-sound-applet
                                             // when moved to control center
    'gnome-sound-applet': 'volume',
    'nm-applet': 'network',
    'gnome-power-manager': 'battery',
    'keyboard': 'keyboard',
    'a11y-keyboard': 'a11y',
    'kbd-scrolllock': 'keyboard',
    'kbd-numlock': 'keyboard',
    'kbd-capslock': 'keyboard',
    'ibus-ui-gtk': 'input-method',
    [color=red]'syspeek': 'syspeek'[/color]    
};

function StatusIconDispatcher() {
    this._init();
}

StatusIconDispatcher.prototype = {
    _init: function() {
        this._traymanager = new Shell.TrayManager();
        this._traymanager.connect('tray-icon-added', Lang.bind(this, this._onTrayIconAdded));
        this._traymanager.connect('tray-icon-removed', Lang.bind(this, this._onTrayIconRemoved));

        // Yet-another-Ubuntu-workaround - we have to kill their
        // app-indicators, so that applications fall back to normal
        // status icons
        // http://bugzilla.gnome.org/show_bug.cgi=id=621382
        Util.killall('indicator-application-service');
    },

    start: function(themeWidget) {
        this._traymanager.manage_stage(global.stage, themeWidget);
    },

    _onTrayIconAdded: function(o, icon) {
        let wmClass = (icon.wm_class || 'unknown').toLowerCase();
        let role = STANDARD_TRAY_ICON_IMPLEMENTATIONS[wmClass];
        if (role)
            this.emit('status-icon-added', icon, role);
        else
            this.emit('message-icon-added', icon);
    },

    _onTrayIconRemoved: function(o, icon) {
        let wmClass = (icon.wm_class || 'unknown').toLowerCase();
        let role = STANDARD_TRAY_ICON_IMPLEMENTATIONS[wmClass];
        if (role)
            this.emit('status-icon-removed', icon);
        else
            this.emit('message-icon-removed', icon);
    }
};
Signals.addSignalMethods(StatusIconDispatcher.prototype);
```

this is my statusIconDispatcher.js... it sayed in /usr/share/gnome-shell/js/ui/.

cheers.

---

### Post by sgarman on 2011-10-02
Thank you tista, that works quite well! ):P

For anyone who would like to do the same, the name of the applet is 'indicator-multiload'. I also did the same for the 'indicator-weather' applet.

Scott

---

