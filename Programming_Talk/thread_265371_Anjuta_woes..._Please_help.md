---
title: "Anjuta woes... Please help"
date: 2006-09-25
forum: Programming Talk
---

### Post by Ziggy72 on 2006-09-25
I installed Anjuta using Automatix. Then I ran it and was informed I needed autoconf, automake and libtool, so I used Synaptic Manager to install these. Now the program tells me to:

"Please add the files codeset.m4, glibc21.m4, iconvm4, isc-posix.m4 and progtest.m4 from your /usr/share/alocal directory to your autoconf macro directory or directly to your alocal.m4 file."

I added these files to the /usr/share/autoconf/ directory, but the error message persists. Why?

Later:

"You will also need config.guess and config.sub, which you can get from [ftp://ftp.gnu.org/pubgnu/config/](ftp://ftp.gnu.org/pubgnu/config/). "

I got these files and put them in the /usr/share/autoconf/ directory - but there was no change in the error messages.

And later... "configure error: Package requirements (libgnomeui-2.0 gtk+-2.0) were not met"

I couldn't find either of these package requirements in Synaptic...

So I'm completely baffled. Should I just uninstall Anjuta and admit defeat or can some kind person tell me how to install the program without tears. Any help appreciated...

---

### Post by Ziggy72 on 2006-09-26
Ok - I admit defeat - I've uninstalled everything related to Ajunta. I'm sorry that installing via Automatix wasn't more successful. Usually, Automatix is very reliable.

---

### Post by maubp on 2006-09-26
I installed Anjuta 1.2.4a using synaptic, and it took me a while to track down all the unspecified dependancies (If I recall correctly).

Try using synaptic, and right click on anjuta and choosing both "mark recommended for installation" and "mark suggested for installation".

Once I got it running, I was not very impressed - little bugs seemed to crop up.  This may have been partly due to me using 64bit Ubuntu.

The developers have moved on to work on Anjuta 2.0.x and the old branch is not getting much/any work on it.

I plan to try again once Anjuta 2.0.x is in the repositories...

---

### Post by Ziggy72 on 2006-09-27
Thanks for the suggestion. However, I did all that you suggested before finally abandoning the program. Since then, I've downloaded and installed Eclipse (without any problems at all) and, so far, I'm quite impressed. The Eclipse  documentation is *very* good.

---

### Post by moshy on 2007-04-08
Could you please tell me what these recommended and suggested packages are, because I get the same error message, but from an autogen.sh script, and I can't look them up myself because I don't have Ajunta in Synaptic, unless you wan to tell me the repo for it.

---

