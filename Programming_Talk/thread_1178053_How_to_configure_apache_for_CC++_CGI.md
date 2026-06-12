---
title: "How to configure apache for C/C++ CGI?"
date: 2009-06-04
forum: Programming Talk
---

### Post by resander on 2009-06-04
I have some large applications written in C/C++ that I would like to access from the web. They use MySQL databases via ODBC using code written in C. All work well when run locally as Linux executables. I would place these applications in cgi-bin and add code to convert output to html. 

I have just installed apache2 on Ubuntu 8.10, but I have never used it before. The apache2 documentation is very detailed and difficult to interpret for a beginner like myself.

I would like to rely on apache2 default settings as far as possible, but how do I configure apache2 to let me use Linux executables instead of PHP/PERL? I think AddHandler has to be set. But how?

---

### Post by stevescripts on 2009-06-04
resander -

These links should help:

[http://www.cs.tut.fi/~jkorpela/forms/cgic.html#setup](http://www.cs.tut.fi/~jkorpela/forms/cgic.html#setup)

[http://httpd.apache.org/docs/2.0/en/howto/cgi.html](http://httpd.apache.org/docs/2.0/en/howto/cgi.html)

I haven't used C for a cgi progran for many years, the short answer,
if I recall correctly, simply amounts to adding the .cgi extension to your
compiled program, and placing the program in your cgi-bin directory.

And yes, I understand your frustration with the apache documentation - 
that's a big bit to bite off when you are getting started.

Hope this helps a bit.

Steve

---

### Post by resander on 2009-06-05
Many thanks for the information.

The first link is spot-on and exactly what I have googling for for days without being able to find it.

Will start experimenting soon!

Again many thanks.

---

### Post by stevescripts on 2009-06-05
My pleasure :)

Feel free to post back here, (or ping me via e-mail) if you get stuck.

I don't have a bunch of spare time, but might be willing to knock some of the rust off as an exercise to help you get going.

<idle curiosity> That said, why do you choose to use C for CGI, when there are other easier/quicker tools?
(PERL, Python, Tcl, ... etc)</idle curiosity>

Steve

---

### Post by Mirge on 2009-06-05
Going to assume because he already has his tools written in C... and C being a compiled language can be (some would argue IS) faster than interpreted languages even in CGI applications.

Plus it'd be neat to experiment with if you've never done it I guess.

---

### Post by stevescripts on 2009-06-05
Mirge - you are probably correct.  FWIW the only time I did any CGI in C was just to experiment, and that was now many years ago.

Steve

---

### Post by Mirge on 2009-06-05
> **stevescripts said:**
> Mirge - you are probably correct.  FWIW the only time I did any CGI in C was just to experiment, and that was now many years ago.

Steve

I wouldn't go out of my way to build a site from the ground up using C/CGI unless I had to. Then again, I'm just getting around to re-learning C and I have no where near the experience needed to get things done as quickly as they need to get done.

Dusting off my C++ books too...

---

