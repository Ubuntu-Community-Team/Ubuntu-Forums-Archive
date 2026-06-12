---
title: "notify-send"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by rburkartjo on 2014-01-09
what is the -t option when using notify-send to have the script not expire
i want the notification not to close

notify-send -t (?)

tks

---

### Post by rburkartjo on 2014-01-09
that option is not noted in the --man pages. i already checked

---

### Post by tgalati4 on 2014-01-09
You could set a large value:

tgalati4@Mint14-Extensa ~ $ notify-send -?
Usage:
  notify-send [OPTION...] <SUMMARY> [BODY] - create a notification

Help Options:
  -?, --help                        Show help options

Application Options:
  -u, --urgency=LEVEL               Specifies the urgency level (low, normal, critical).
  -t, --expire-time=TIME            Specifies the timeout in milliseconds at which to expire the notification.
  -a, --app-name=APP_NAME           Specifies the app name for the icon
  -i, --icon=ICON[,ICON...]         Specifies an icon filename or stock icon to display.
  -c, --category=TYPE[,TYPE...]     Specifies the notification category.
  -h, --hint=TYPE:NAME:VALUE        Specifies basic extra data to pass. Valid types are int, double, string and byte.
  -v, --version                     Version of the package.

Experiment and let us know what large values work.

Perhaps describe your Use Case in more detail.  There is probably a better way to do this.

---

### Post by sisco311 on 2014-01-09
According to the  [Freedesktop.org Desktop Notifications Specification]("https://developer.gnome.org/notification-spec/") **-t 0 **(zero) should do the trick. But it depends on the notification daemon you are using.

---

### Post by rburkartjo on 2014-01-09
sisco tks that did the trick. didnt think of that. i had tried -1 as i did in my default grub to keep my boot menu from timing out.

---

