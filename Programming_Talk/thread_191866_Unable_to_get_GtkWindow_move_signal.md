---
title: "Unable to get GtkWindow move signal"
date: 2006-06-08
forum: Programming Talk
---

### Post by bhubanmm on 2006-06-08
Hi all,

I was a professional windows C/C++ programmer recently migrated to linux. Can anyone please tell me how I can catch the GtkWindow's move signal.

I tried with motion_notify signal, but it did not help as the event was not called when I moved the Window.

Please Help!!!
Thanks in advance,

---

### Post by Ivan Matveich on 2006-06-08
Install a handler for configure_event on the window, like

```

#!/usr/bin/env ruby

require 'gtk2'

Gtk.init
window = Gtk::Window.new

window.signal_connect('configure-event') do
  puts "configure-event received"
end

window.show_all
Gtk.main

```

---

### Post by bhubanmm on 2006-06-10
Hello Evan,

Thanks, I got it.

---

