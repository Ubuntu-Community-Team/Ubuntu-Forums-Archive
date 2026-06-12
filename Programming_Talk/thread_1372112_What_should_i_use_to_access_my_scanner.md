---
title: "What should i use to access my scanner ?"
date: 2010-01-04
forum: Programming Talk
---

### Post by iMisspell on 2010-01-04
When running windows, i made a program in VB6 to keep track of my bills, credit card statements, bank statements, etc..
All info was/is stored in a MS Access.db
For paper bills it would scan them into the program and then save the image to the db, for online stuff it will import .xml and cvs files and phase them how i wanted and stored that info.

What would be the easiest language to learn so i can make something like this, now im running a linux based system ? 
Haven't tried my VB6 program in 'wine', would rather not if i don't have to.

In time i plan on moving the access.db to mysql, so thats what the new program will store to.


Thanks for any advice or ideas.

_

---

### Post by alwayshere on 2010-01-04
"Sane" is the app ya want search in add and remove

OR in terminal put 

sudo apt-get install sane

---

### Post by nvteighen on 2010-01-04
> **iMisspell said:**
> When running windows, i made a program in VB6 to keep track of my bills, credit card statements, bank statements, etc..
All info was/is stored in a MS Access.db
For paper bills it would scan them into the program and then save the image to the db, for online stuff it will import .xml and cvs files and phase them how i wanted and stored that info.

What would be the easiest language to learn so i can make something like this, now im running a linux based system ? 
Haven't tried my VB6 program in 'wine', would rather not if i don't have to.

In time i plan on moving the access.db to mysql, so thats what the new program will store to.


Thanks for any advice or ideas.

_

SANE and its GUI-counterpart XSANE are programs to scan. 

Or what you want is to port your VB6 program to GNU/Linux (e.g. in C or C++) and want to know what library is available for scanning? Well, if so, fortunately stuff in GNU/Linux is usually modularized, so you can access the SANE backend library libsane (install libsane-dev to get the header and development files).

Could you please elaborate on what you want to do?

---

### Post by iMisspell on 2010-01-05
Thanks all, will look into, sane libraries.
> **nvteighen said:**
> Could you please elaborate on what you want to do?

Create a new program to store my "bills".
Save to MySQL
Scan in paper bills and store the images
Phase excel and .cvs files
With as little interaction from me as possible ;)

Long time ago, i "played" with c++ trying to teach myself the language, it was a little tough, but also the first "real" language i ever looked at, the only thing i knew at that time was HTML. I moved to VB6 which was much much simpler and forgiving. That was around 5-6 years ago, ive toyed with a few different languages since then. Gonna to a little research about C and C++ to see what would be the most useful to me and start learning.

If i was to create something in C or C++, would it be possible to make it cross platform ? What would i have to look out for ?

For the most part it will be nothing more then simple text phasing and acouple GUI windows with a few fields on each, and the scanning option.

Thanks for the 'sane' information.

_

---

### Post by nvteighen on 2010-01-05
> **iMisspell said:**
> 
If i was to create something in C or C++, would it be possible to make it cross platform ? What would i have to look out for ?

For the most part it will be nothing more then simple text phasing and acouple GUI windows with a few fields on each, and the scanning option.


C and C++ won't give you cross-platform portability, as they are both low-level languages meant to work with the system. Although both languages are standarized, libraries and executable formats (and also other quirks) are different for each OS. Sometimes, with good luck, you might be able to recompile and be able to port your application, but if you happen to need a system-specific library, you won't be able to do it in a trivial way.

For cross-platform development, what you've got is a variety of high-level languages like Python, Perl, Java, C#, etc. They're quite useful as they hide the platform-specific stuff and other low-level details that are actually annoying except where actually needed. The drawback is that, as they usually compile to bytecode (i.e. not a native executable), if you want to interface to a library, you'll need a "binding" and sometimes that may not be able (but in the FOSS community it's actually quite easy to find bindings for your favorite language).

SANE is a C library, so I wouldn't use C++ with it. I see there's also a Python binding called python-imaging-sane and a Perl one libsane-perl in the Ubuntu repositories. To use the SANE library in C, you have to install libsane-dev (and the documentation...).

---

### Post by iMisspell on 2010-01-07
Thanks for the insight, nvteighen.

Did not know C# can be cross platform.
Ive done alittle with C#, made a plugin for 'playon' (pop-cornhour media-software) under windows.

I will have to do research about cross platform languages. Right now im leaning towards Java, being it seams to be the easyest for the "end-user" to get going.

For the project at hand, im probably gonna go with Perl since it will be quick and easy and hold me over till i find more time to learn something new.

Again, thanks for your help.

_

---

