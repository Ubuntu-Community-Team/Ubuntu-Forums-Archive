---
title: "First impression+few questions-notifications,workspace shortcuts,crash investigation"
date: 2019-10-01
forum: New to Ubuntu
---

### Post by p-fischer on 2019-10-01
Hello! As a newcomer to Ubuntu 19.04, I have some questions about things that bothers me:

1) **desktop notifications** (libnotify etc) - notifications are placed top-center, under the "top bar" with date&time. when I click date&time, a little notification center with calendar is showed and there are last notifications from thunderbird, pidgin and other desktop apps, OK - but if there are some notifications and I miss them - there is absolutely no evidence about existing notifications - no icon, or another color or something to alert me about existing notifications - no one minds this?

2) **switching of workspaces**  - I mapped Super+1, Super+2... keyboard shortcuts to switch to given workspace, nice, but when I am switching between workspaces like a maniac at work, I miss really much the shortcut for "jump back to the workspace I came from" or "jump back to the last workspace" - can I arrange it somehow? I am comming from i3 wm, there can be shortcut just for _everything_, and I would be really happy for this.

3) **crash investigation** - when I tried to log on to the desktop this morning, it crashed several times and I didn't even get to the desktop, only after restart and on the fourth attempt I managed to log in - now I'm still logged in to that session and I'm trying not to get out of it :) - how to investigate this situation, log files? ok, but which ones? nothing interesting in Xorg.log and there is no "/var/log/messages" :) (I am comming from FreeBSD)

Thanks very much for this little triple help folks!

---

### Post by TheFu on 2019-10-01
Thanks to systemd/journald defaults in Ubuntu, boot logs aren't retained between boots. You can modify 1 setting to retain 1, 2, 3, 10, XYZ mb or some other limit, if you like for the number of boot logs. Or you can have system logs shipped to another machine. That is one thing that journald handles better than the prior solution.
Ubuntu also has a crash reporting tool that will gather the system info and submit the data. apport-* are the commands.

The other stuff is all GUI, which I cannot help about. Sorry.  I'm not a fan of Gnome3, so I don't use it. Much prefer a WM where I actually can control everything. If you like i3, why not just use that instead?

---

### Post by p-fischer on 2019-10-02
I guess I won't ask before sleep, so after some sleep:

1) [https://extensions.gnome.org/extension/258/notifications-alert-on-user-menu/](https://extensions.gnome.org/extension/258/notifications-alert-on-user-menu/)
(but if Ubuntu is doing some "desktop design", they should solve this)

2) [https://extensions.gnome.org/extension/1089/go-to-last-workspace/](https://extensions.gnome.org/extension/1089/go-to-last-workspace/)  +   [https://github.com/arjan/gnome-shell-go-to-last-workspace](https://github.com/arjan/gnome-shell-go-to-last-workspace)

3)  journalctl -e + journalctl -b etc etc...

---

