---
title: "How autostart implemented?"
date: 2008-10-15
forum: Programming Talk
---

### Post by pageguest on 2008-10-15
Dear all,

As we all know, we can add/remove program in System->Preferences->Session->Startup Programs to enable/disable a program run during boot time.

I had thought that there would be some script in /etc/init.d to do this job. After looking around, it seems that I was wrong.

Could anyone tell me how this functionality implemented?

Thanks.

---

### Post by pytheas22 on 2008-10-15
I'm not sure what exactly you need to do.  Which program did you want to add or remove to be autostarted?

The Gnome Sessions utility is meant for launching user-specific applications--for example, if under one account you want Pidgin to start whenever that user logs into the desktop, you can use Gnome Sessions to do that.  But it won't affect other users.  The scripts in /etc/init.d are used to start system-wide processes (generally owned by root) that usually have to do with lower-level stuff than Gnome Sessions.

So please let us know more specifically what you're trying to do and we can advise you on the proper steps.

---

### Post by pageguest on 2008-10-15
Thanks for your reply.

Well, I want to add update-notifier to my mobile device(NOKIA N800) which runs linux, and it doesn't have gnome environment. The latest firmware has added this feature, but I'd like to add my own one.

I have downloaded the package's(update-notifier) source code and taken a glance at it. Maybe this would not be a problem but time to porting it to my device since I have the SDK.

Now I want to follow ubuntu's way to add it into the system for all users so that update-notifier will autorun when my device starts up.

---

### Post by pytheas22 on 2008-10-15
Provided you have update-notifier installed correctly, all you would have to do to make it autostart for all users at boot is [write a boot script]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/") in the /etc/init.d directory.

One caveat: I'm not sure what update-notifier is, but if it requires a graphical environment to run, this may not work so well, because the /etc/init.d scripts get run before X starts.  Is this a problem for you?

---

### Post by snova on 2008-10-15
There are two possible answers.

First, there are system services that are started when you turn the computer on. These are in /etc/init.d.

Then there are the programs that run when you start an X session (Gnome or KDE). I don't know about Gnome, but KDE has a folder called "autostart" in ~/.kde/autostart. KDE runs all the scripts in this directory when it starts.

I think you want the first one. You would probably go about it by writing a script in /etc/init.d, and then symlinking it to the correct runlevels.

Just in case, I'll define "runlevel". It's a state. When you start your computer, it goes into runlevel 0 or whatever, and runs /etc/rc0.d files. There's a runlevel for X, a runlevel for shutting down, and so on. The "runlevel" command can be used to query the current runlevel.

---

### Post by mssever on 2008-10-15
Most window managers include some way to autostart programs, but different WMs solve it differently. There's also a generic X startup file that you can put in your $HOME. I don't remember what it's called since it's been nearly ten years since I've used it. But it should work with all window managers.

---

### Post by snova on 2008-10-15
I think it might be .xinitrc, or .xsession+something.

---

### Post by niccholaspage on 2008-10-15
The .xsession file in every uses home folder is a good place to add programs. The default login session is "Run Xclient script" and it uses the .xsession file.

---

### Post by pageguest on 2008-10-16
> **snova said:**
> There are two possible answers.

Then there are the programs that run when you start an X session (Gnome or KDE). I don't know about Gnome, but KDE has a folder called "autostart" in ~/.kde/autostart. KDE runs all the scripts in this directory when it starts.



In ubuntu seems to be [http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)

Thanks all your guys. I think I have got my answer:)

---

