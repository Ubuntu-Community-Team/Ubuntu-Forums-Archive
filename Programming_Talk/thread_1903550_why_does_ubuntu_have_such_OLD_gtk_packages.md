---
title: "why does ubuntu have such OLD gtk packages"
date: 2012-01-02
forum: Programming Talk
---

### Post by kline on 2012-01-02
i have been developing a gtk application for the "accessibility" group
i tried porting it to mt laptop with the latest debian.

i am having troubles with the function [or macros]:

gtk_widget_sensible()    and

gtk_widget_set_sensible()

can anyone tell me what gnome or gtk or whatever packages i need to add to my  laptop?

thanks in advance.

---

### Post by Bachstelze on 2012-01-03
I'm not a GTK expert, but since the only Google result for gtk_widget_sensible is this thread, I will hazard a guess that this function does not exist. Where have you heard of it?

---

### Post by nvteighen on 2012-01-03
Er... isn't ATK the accessibility toolkit? I've never done anything related to accessibility, but I'm pretty sure gtk_widget_sensible and gtk_widget_set_sensible do not exist in GTK+?

---

### Post by kline on 2012-01-03
> **nvteighen said:**
> Er... isn't ATK the accessibility toolkit? I've never done anything related to accessibility, but I'm pretty sure gtk_widget_sensible and gtk_widget_set_sensible do not exist in GTK+?

i just noticed that was was called "accessibility" has been renamed "universal access"; it is last in the list headed by:

Accessories,
Development Tools,
Education,
Fonts,

and so on.

i'll fess up to not having hacked anything GUI since 1996 when i spent 7 to 9 months  learning Xlib.  followed by Xaw.  after 6 years of writing 10-12K lines of C and C++ i gave it up.  i started into gtk in november and thanks to help from lots of people now have close to 600 lines. 

since ubuntu is a fork of debian, i expected no problems.  what's on debian is not the same as 11.04.  the gtk.h files differ.

---

### Post by 3Miro on 2012-01-03
Are you looking at Debian Stable? Ubuntu is more current then Debian Stable, 11.10 already uses Gnome 3 + GTK3, while Debian 6 is at Gnome 2 with GTK2.

11.04 shouldn't differ too much since it is also Gnome 2 + GTK2, but it is certainly more recent then Debian 6.

---

### Post by kline on 2012-01-03
> **3Miro said:**
> Are you looking at Debian Stable? Ubuntu is more current then Debian Stable, 11.10 already uses Gnome 3 + GTK3, while Debian 6 is at Gnome 2 with GTK2.

11.04 shouldn't differ too much since it is also Gnome 2 + GTK2, but it is certainly more recent then Debian 6.

i don't know [to quote mark twain].  i have whatever version of debian was on their download  site several months ago.  if 11.10 uses a newer gtk than what's on my netbook that would explain why debian has "GTK_WIDGET_IS_SENSITIVE(widget)" while here that macro has been added to  some library.

---

### Post by nvteighen on 2012-01-04
> **kline said:**
> i don't know [to quote mark twain].  i have whatever version of debian was on their download  site several months ago.  if 11.10 uses a newer gtk than what's on my netbook that would explain why debian has "GTK_WIDGET_IS_SENSITIVE(widget)" while here that macro has been added to  some library.

Please post the contents of /etc/debian_version... That will show what version you're using and help a lot in determining what GTK+ packages you have available from the repos.

FYI, Ubuntu is a fork from Debian unstable (aka "Sid")... that's why it's got newer packages than the official Debian stable (currently 6.0, aka "Squeeze"). By the way, I run Debian testing (aka "Wheezy"), which is the base for the next 7.0 release, and I've got the newest libs.

The GTK_WIDGET_IS_SENSITIVE macro was deprecated in GTK+ 2.20 (!!!)... Take a look [here]("http://developer.gnome.org/gtk/2.24/GtkWidget.html#GTK-WIDGET-IS-SENSITIVE:CAPS"). You know, libs developers sometimes get rid of stuff they think that are useless or worthless to mantain :P They kept it for backwards compatibility in 2.22 and 2.24, but recommending to use the gtk_widget_is_sensitive() *function* instead. Now with GTK+ 3.x the old macro is gone forever and you have to use that function (I've checked the API docs for GTK+ 3.2).

---

### Post by kline on 2012-01-05
sorry for the delay; i was sure i  hadn't deleted your email notification.  in the file is:

5.0.9

i have been racing the clock to get something working to demo to my docs and any therapist who cares to show up.  i do have a keyboard-click program on my EEE-900A; it helps me know that  i've hit a key: no =thunk= no contact.  [i figured that a small laptop like the EEE series would be easier for anyone with a disability or disabilities to carry around.  and so far, so good.  i use a motorized w'chair for mobility and my computer fits by my side.  it is light enough that i can hanfle in with my one good hand and put it wherever.  

anyway, i just added a Quit button so i dont have to kill anything on-screen.  my PT said she thought my typing-to-speech app would help people in that line of work.  not physical therapists, but speech therapists and so forth.  a couple years ago i talked to some of the folks at the OLPC project and got some stats thast blew me away.

but to get back on-topic: is there a wsay of upgrading from what i put on my 900a netbook, or is this going to be  a major undertaking on plugging in the external drive and going that route?  [ i HOPE not! ]

---

