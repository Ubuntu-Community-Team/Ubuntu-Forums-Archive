---
title: "Making a Flac to Mp3 converter"
date: 2007-06-19
forum: Programming Talk
---

### Post by Persianelfster on 2007-06-19
I am working on a flac to mp3 converter and  I was wondering if anyone had any suggestions on which language to use.  Right now I am thinking about Perl, however, I would like to hear other people's thoughts

---

### Post by ssam on 2007-06-19
are you talking about making a the converter that does the actual encoding and decoding of each format, or using existing converters and putting a interface on top?

have you looked for existing programs that do this?

if nothing existing does quite what you want, i would suggest using python and gstreamer. (though if you are happier with perl use that)

---

### Post by Persianelfster on 2007-06-19
Doing the decoding and enconding, probably have to do flac -> wav -> mp3
I need to jumpstart programing with a project, if you just use a book its like what does this mean you just end up copying code and don't really learn it, so hopefully with some effort this will help me get back into programing.  I'll take a look at python though.

---

### Post by Engnome on 2007-06-19
+1 for python, I did some GTK interfaces with perl. It was a little messy without OO. There is a reason for python being recommended all the time.

---

### Post by Persianelfster on 2007-06-19
coolo!

---

### Post by ssam on 2007-06-19
> **Engnome said:**
> There is a reason for python being recommended all the time.

i think the things that attract people to ubuntu over other linux distros, are similar to the things that attract people to python over other programming languages.

also (and probably related), the ubuntu devs like to use python where they can.
eg
Ubiquity (the installer)
Bazaar (version control system)
Gnome-app-instal
restricted-manager
also look at the bounties offered at [http://www.ubuntu.com/community/developerzone/bounties](http://www.ubuntu.com/community/developerzone/bounties)

---

