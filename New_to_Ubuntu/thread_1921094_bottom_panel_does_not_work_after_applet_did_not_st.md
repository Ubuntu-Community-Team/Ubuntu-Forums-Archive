---
title: "bottom panel does not work after applet did not start"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by itzoccor on 2012-02-06
Hi 

I am using Ubuntu 11.04 with 'classic' desktop. 
Today I got an error message saying that at start up there were problems loading an applet.
I was given the option to delete the applet path or to ignore the error.
I was silly enough to opt to delete the path.

As a result, the bottom panel is still there, but the only thing in there is the waste bin. The "desktop quad" has disappeared, but what is most annoying is that when I start an application, no application icon appears on the bottom desktop, so I was not able to switch from one application to another with a single click.

I could restore some functionality by "add to panel..." options, but still is not what it was before and I would like to restore everything as it were.

I assume there must be a way to restore the applet that is missing (is there a repair function ...?).

Besides, I assume there also must be a way to retrieve the error message so that I know what applet was misbehaving. 

It seems odd however that I was given the option to delete the path to a "misbehaving" applet without even being asked to login as administrator. 

Thanks in advance for any help

---

### Post by westie457 on 2012-02-06
Try running this in a terminal ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

Any errors post back here with the errors.

No errors and panel restored please mark this as SOLVED using Thread Tools.

Thank you.

---

