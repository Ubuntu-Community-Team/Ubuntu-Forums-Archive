---
title: "Anyway to Disable Startup Apps??"
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cottfcfan on 2011-10-10
1st thing I normally do on a fresh install is go to system/preferences/startup Apps & disable things like Bluetooth, Visual Assistance etc..
 Is there anyway to do this in 11.10?
When I check I only have the option of disabling things I have manually enabled but nothing else.

---

### Post by effenberg0x0 on 2011-10-10
Yes, 

1-Type "startup" in the dash search field and you'll see the icon for Startup Apps.
2-Install bum if you wanna go a step further.


Regards,
Effenberg

---

### Post by paul_in_london on 2011-10-10
Control of start-up applications (**Applications -> Startup Applications** in gnome shell) is provided by this program:

[http://manpages.ubuntu.com/manpages/oneiric/man1/](http://manpages.ubuntu.com/manpages/oneiric/man1/)**gnome-session-properties**.1.html

More generally, see also:

[http://overtag.dk/wordpress/2011/02/headaches-over-disablingenabling-services-init-d-scripts-in-ubuntu-10-10/](http://overtag.dk/wordpress/2011/02/headaches-over-disablingenabling-services-init-d-scripts-in-ubuntu-10-10/)

[http://www.linuxtutorialblog.com/post/tutorial-disabling-unused-daemons-to-speed-up-your-boot-sequence](http://www.linuxtutorialblog.com/post/tutorial-disabling-unused-daemons-to-speed-up-your-boot-sequence)

EDIT: Sorry, I should have said **gnome-session-properties** is provided by the **gnome-session-bin** package.

---

### Post by mc4man on 2011-10-10
See this thread post 9 for a command that will make all of the now hidden startups show up
[http://ubuntuforums.org/showthread.php?t=1795650](http://ubuntuforums.org/showthread.php?t=1795650)

Myself just go to /etc/xdg/autostart/, open the ones I want to disable in a text editor & remove this line altogether
NoDisplay=true

Either way -  then open up Startup Applications & disable

To open a .desktop in a text editor either open a root editor (gedit) & drag/drop into or I just use  nautilus actions specific to .desktops - 1 for root, 1 for user

---

### Post by jbicha on 2011-10-10
It was decided to hide nearly all of the Startup Applications contents as we believed that normal users shouldn't turn off things like Bluetooth (from that menu at least), GNOME Keyring support, Evolution alarms, etc.

If there are certain things that should not be hidden, please file a bug and let us know. For instance, we'll likely unhide the Login Sound option next week (it's looking like the login sound will be disabled by default next release).

---

### Post by cariboo on 2011-10-10
> **jbicha said:**
> It was decided to hide nearly all of the Startup Applications contents as we believed that normal users shouldn't turn off things like Bluetooth (from that menu at least), GNOME Keyring support, Evolution alarms, etc.

If there are certain things that should not be hidden, please file a bug and let us know. For instance, we'll likely unhide the Login Sound option next week (it's looking like the login sound will be disabled by default next release).

I'd sure like to know how that decision came about, as there a quite a few users that turn off services after the initial install. I've always turned off anything to do with evolution, as I use Thunderbird, and don't need the evolution integration. I also turn off bluetooth, on systems that don't use it. How widespread is bluetooth usage, the majority of the people I know don't use it no matter what operating system they use.

Some times the hand holding goes a little to far, I know that everyone should have a good user experience, but we should let the user be responsible for administering their own system. If they break the system due to something they have done, Ubuntu shouldn't feel responsible for user error.

---

### Post by jbicha on 2011-10-10
It was [discussed]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-startup-applications") at the last UDS. Compared to Natty, Startup Applications is much more prominent so that users can easily run scripts (adding programs should be easier too but few distributions pay any attention to gnome-session-properties now).

Evolution alarms won't be there if Evolution isn't installed. And disabling Bluetooth is better done in System Settings>Bluetooth. It's not a matter of letting the user administer their own system as that can still be done but we definitely shouldn't make breaking things too easy if that can be avoided.

Look in /etc/xdg/autostart/ to look at the various startup services that happen to be installed. Not all of them actually run. Look for AutostartCondition and ShowIn values to make sure.

---

### Post by mc4man on 2011-10-10
> It was decided to hide nearly all of the Startup Applications contents as we believed that normal users shouldn't turn off things like Bluetooth (from that menu at least
I think that's one of the more interesting ones (that never will be changed

The only point of disabling from SU apps would be not to disable bluetooth but to stop the applet from running & even being in the indicators
If one has disabled bluetooth then why have the applet run &  in the indicators?
Disabling bluetooth in g-c-c does not prevent the above, actually here have bluetooth disabled in bios, so g-c-c has it also disabled by default, but the applet starts & runs anyway

(the bluetoothd service runs as long as bluez is installed & isn't relevant to this

---

### Post by jbicha on 2011-10-10
Like I said, if you think certain things shouldn't be hidden, file a bug with why they should be shown to all users.

Perhaps there should be a different bug to hide the bluetooth menu if bluetooth was disabled since that sounds like some of your underlying reasoning. My primary computer doesn't have bluetooth...

---

### Post by cottfcfan on 2011-10-11
Thanks for all your replies guys.
I went with mac4man's reply, post 9 in his link worked perfectly.
I'll mark this as solved.

---

