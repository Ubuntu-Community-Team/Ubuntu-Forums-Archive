---
title: "Update Gaim Friendly name and status message according to Rhythmbox"
date: 2007-03-16
forum: Outdated Tutorials &amp; Tips
---

### Post by KSDZ on 2007-03-16
Hej, I improved the script found in [this]("http://ubuntuforums.org/showthread.php?t=123071") thread.
I figured I'd post it in a new thread as this is for rhythmbox and not for XMMS.

The main change I've made is that the status is now reset as you pause/stop your music, and set again as you hit play again.

here it is:
```

#!/usr/bin/python
# -*- coding: UTF-8 -*-

# gaim-rb.py
# Update gaim messages and friendly names with information for currently playing song.
# Originally written by: Unknown
# Improved by Koen Sadza <koen@sadza.nl> - http://weblog.ksdz.nl

import dbus
import dbus.glib
import gtk

#class IMAccount: # empty class to put account variales into
#    pass

bus = dbus.SessionBus()
rbshellobj = bus.get_object('org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Shell')
rbshell = dbus.Interface(rbshellobj, 'org.gnome.Rhythmbox.Shell')
rbplayerobj = bus.get_object('org.gnome.Rhythmbox', '/org/gnome/Rhythmbox/Player')
rbplayer = dbus.Interface(rbplayerobj, 'org.gnome.Rhythmbox.Player')
gaimobj = bus.get_object('net.sf.gaim.GaimService', '/net/sf/gaim/GaimObject')
gaim = dbus.Interface(gaimobj, 'net.sf.gaim.GaimInterface')

value = ''

def update_gaim(value):
    accounts = gaim.GaimAccountsGetAllActive()
    for account in accounts:
#        print account
        protocol = gaim.GaimAccountGetProtocolId(account)
#        print protocol
        status = gaim.GaimAccountGetActiveStatus(account)
        status_id = gaim.GaimStatusTypeGetId(gaim.GaimStatusGetType(gaim.GaimAccountGetActiveStatus(account)))
        if (protocol == 'prpl-oscar') | (protocol == 'prpl-jabber'): # set the away message for oscar and jabber
            message = gaim.GaimStatusGetAttrString(status, 'message')
#            print message
            if message.find(" &#9834;") != -1:
                message = message[:message.find(" &#9834;")]

            gaim.GaimStatusSetAttrString(status, 'message', message + value)
            message = gaim.GaimStatusGetAttrString(status, 'message')
#            print message
        elif protocol == 'prpl-msn': # set the friendly name for msn
            connection = gaim.GaimAccountGetConnection(account)
            message = gaim.GaimConnectionGetDisplayName(connection)
#            print message
            if message.find(" &#9834;") != -1:
                message = message[:message.find(" &#9834;")]

            gaim.GaimConnectionSetDisplayName(connection, message + value)
            
def playing_uri_changed(uri):
    global value
    props = rbshell.getSongProperties(uri)
    value = ' &#9834; \"' + props['title'] + '\" by ' + props['artist'] + ' &#9834;'
#    print value
    update_gaim(value)
    
def playing_changed(truefalse):
    if truefalse:
        update_gaim(value)
    else:
        update_gaim('')
        
rbplayer.connect_to_signal('playingUriChanged', playing_uri_changed)
rbplayer.connect_to_signal('playingChanged', playing_changed)

gtk.main()

```

BTW: Does anybody know if this can be released under GPL? Because the original writer is unknown and I already posted it here? I really don't understand all that licensing stuff...

Edit: I just found out that the Jabber and ICQ status aren't being updated,
this looks like it's due to a bug in Gaim as the dbus GaimStatusGetAttrString returns exactly what GaimStatusSetAttrString set,
but the status isn't being updated in Gaim itself...
If anybody knows how to fix this... Your help is more than welcome.

---

### Post by milad on 2007-03-22
Is there any chance that this works with Amarok?

---

### Post by maznos on 2008-03-16
Hello

Can anyone port this ti the current pidgin release

regards

maz

---

