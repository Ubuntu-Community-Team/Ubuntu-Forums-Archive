---
title: "ODD Dbus behaviour PYGTK"
date: 2008-05-12
forum: Programming Talk
---

### Post by TheIrishGuy on 2008-05-12
Hello people im kinda stumped here on a dbus actioninvoked behaviour.

basically i have a class called clipboard_monitor which monitors the clipboard for URLS.

When it detects an URL, its sends a dbus notification which has a button on it, which when pressed is supposed to activate the ACTIONINvoked handler

the problem is untill i copy something else into the clipboard, the actioninvoked wont activate, which is kinda strange, because the actioninvoked has got nothing to do with the clipboard monitoring

codebase is here 

[http://code.feeditout.com](http://code.feeditout.com)

ill paste a few snippets here, but i think it would be easier to view it on the above link

clipboard monitor
```

import notification
self.t = notification.notify()

if re.match("([0-9]{1,3}\\.[0-9]{1,3}\\.[0-9]{1,3}\\.[0-9]{1,3}|(((news|telnet|nttp|file|http|ftp|https)://)|(www|ftp)[-A-Za-z0-9]*\\.)[-A-Za-z0-9\\.]+)(:[0-9]*)?/[-A-Za-z0-9_\\$\\.\\+\\!\\*\\(\\),;:@&=\\?/~\\#\\%]*[^]'\\.}>\\),\\\"]", self.url):
                    if self.clip_urls.add_url(self.url) == 1:                        
                        self.t.title = "New URL Detected"
                        self.t.message = self.url
                        self.t.send_url_notification()


```


notification snippet
```

def message_click_handler(self, id, n_message):
        print "clicked"
        if n_message.split('minihref:'):
            minih = n_message.split('f:')
            self.url = str(minih[1])            
            self.title = "Standby"
            self.message = "We are now fetching your Minihref for \n<b>" + self.url  + "</b>"
            self.custom_message(n_message)            
            t = fetch_minihref.minihref()       
            t.get_mini(self.url)
            self.title = "Minihref Received"
            self.message = "Your minihref : <b>" + t.mini + "</b> has been placed in your clipboard and is ready for pasting :)"
            self.put_link_clipboard(t.mini)
            self.custom_message(self.url)


    def send_url_notification(self):               
        try:
            self.session_bus = dbus.SessionBus()
            self.notifications_object = self.session_bus.get_object('org.freedesktop.Notifications', '/org/freedesktop/Notifications')
            self.notifications_interface = dbus.Interface(self.notifications_object, 'org.freedesktop.Notifications')     
            self.notifications_interface.connect_to_signal("ActionInvoked", self.message_click_handler)        
            self.id = self.notifications_interface.Notify("Localmini", self.id, self.icon, self.title, self.message, ['minihref:'+self.message, 'Minihref please :)'], {'x': self.w, 'y': self.h}, -1)
        except dbus.exceptions.DBusException:
            print 'Failed to show notification'

```

download the project yourself and see 

[http://code.feeditout.com/download.php?project=Y29kZS9QeXRob24vbG9jYWxtaW5p](http://code.feeditout.com/download.php?project=Y29kZS9QeXRob24vbG9jYWxtaW5p)


any help at all would be appreciated, i need this handler to invoke without having to copy something into the clipboard...

thanks
dave.

---

