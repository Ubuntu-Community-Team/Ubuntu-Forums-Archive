---
title: "Evolution Calendar closes after appearing"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by tgyorgyi on 2008-07-20
I have been trying to set up SynCe and Opensync to work properly with Evolution and my PDA. In the process of trying several fixes for certain problems, Evolution's calendar started to act strangely. Mail, Addressbook, Notes works fine, but if I click on Calendar, it appears, and then Evolution closes about a second later.

I'm an absolute noob, how do I fix something like this? I tried re-installing Evolution through Synaptic, in the hope that whatever went wrong with Evolution would be fixed that way, but that did not happen.

- would it help if I completely removed Evolution and then did a new install?
- if yes, how do I backup my data in Evolution (or do I have to) before I do this?

Thanks in advance!

Györgyi

P.S.: July 21: Meanwhile I removed all packages related to Multisync, SynCE and Opensync, and now the Calendar is stable.
However, I still would like to know the answers to my questions above, if anybody would be so kind... :-)

---

### Post by Nano Geek on 2008-07-21
Run "evolution" in a terminal, repeat the steps that make it crash, and post what the terminal said after it crashed.

---

### Post by tgyorgyi on 2008-07-22
Ok, this is what happens. Meanwhile I noticed that the closing happens when I move the cursor (but not click or anything just place the cursor) above text which has invalid characters (I have recently imported data from MS Outlook via Outport and there is a coding problem with the special characters). So the closing down occurs when I Evolution tries to create that bubble with the calendar entry data and fails because of invalid characters.  

And if I am quick enough to right click on the calendar entry rather then allowing time for that bubble to appear, then I can successfully open the entry and edit. Also, not every invalid character makes evolution freeze, just some...

And here is what the Terminal produced after typing evolution:

```

~$ evolution
evolution-shell-Message: Killing old version of evolution-data-server...

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-CRITICAL **: pango_layout_get_cursor_pos: assertion `index >= 0 && index <= layout->length' failed

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-CRITICAL **: pango_layout_get_cursor_pos: assertion `index >= 0 && index <= layout->length' failed

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-CRITICAL **: pango_layout_get_cursor_pos: assertion `index >= 0 && index <= layout->length' failed

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(evolution:12355): Pango-CRITICAL **: pango_layout_get_cursor_pos: assertion `index >= 0 && index <= layout->length' failed
Szegmens hiba
```

"Szegmens hiba" is Hungarian and the direct translation for that is "segment error"

---

### Post by Nano Geek on 2008-07-22
Hmm, that's not good. From what I've heard, a segmentation fault usually can't be fixed. 

You could try re-compiling Evolution, but I can't guarantee that it would work. If you want to try I will walk you through the steps.

---

### Post by tgyorgyi on 2008-07-24
Thank you, right now I just try to get rid of the faulty characters by opening the calendar entries quicker than the bubble would appear, and then re-write the entries... there are many in the past, but those I will not really re-visit anyway, so I think I can manage, if no other error comes up but this one. If yes, I will certainly as for help, would not know how to reconfigure Evolution...

---

### Post by pzs on 2008-07-24
I worked with Evolution connecting to an Exchange servers and a calendar for about 6 months. I finally gave up because it was very slow, unreliable and unstable. 

I realise that this may not be an option, but you might quit-before-you-start and accept that you can't use the calendar under Linux and save yourself a lot of headaches. Personally, I'm using Google Calendar and (where necessary) looking up my Exchange calender using Outlook Web Access.

---

### Post by kelscmi on 2008-11-26
I am having the same problem with Evolution on my computer.  Everything will work fine, but if I select "calendar" Evolution closes.  The following is what I received when opening via the terminal.

 ```
(evolution:7047): evolution-shell-CRITICAL **: e_shell_set_crash_recovery: assertion `E_IS_SHELL (shell)' failed

```

Does anyone have an idea on what:
1 caused the problem (yes decides user error)
2 how the problem can be resolved

Thank you in advance for your time.

Here is what I the terminal provided when I opened up evolution again.

```
(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed
Changing the queries (contains? "summary" "") 

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed

(evolution:6280): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

(evolution:6280): Gdk-CRITICAL **: gdk_screen_is_composited: assertion `GDK_IS_SCREEN (screen)' failed
Segmentation fault

```

---

### Post by darthyorik on 2008-12-03
I have precisely the same issue with Evolution in Intrepid. I've tried reinstalling Evolution, deleting everything within the Calendar a number of other things to no avail. If I run  it from Terminal it opens in Calendar and will close if you try to change the view from Day to Week etc or if you try to scroll the date. If you open from the Menu it will open in Mail and close if you try to switch to Calendar.

edit: I did upgrade from Hardy to Intrepid ( I'm wondering if that has broken something). I'm running out of ideas and things to try. Failing that I'll try a clean install of Intrepid (not something I want to do).

edit2: Looks like it might be related to  [Bug 555744]("http://bugzilla.gnome.org/show_bug.cgi?id=555744") and quite possibly the same bug is reported [here]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/295928")

---

### Post by darthyorik on 2008-12-04
and it is now fixed in today's updates. I've just run Update Manager, there were Numerous Evolution Updates, and it has resolved the issue.

SOLVED: Fixed etc

---

### Post by trevorhughes on 2008-12-05
Hi
I had the same problem.  I found a solution on the forum.  go to System / Preferences / Assistive Technologies and uncheck "enable.  Then log out and return.  It worked for me.

Trevor

---

