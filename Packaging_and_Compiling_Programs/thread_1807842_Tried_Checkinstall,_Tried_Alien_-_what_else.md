---
title: "Tried Checkinstall, Tried Alien - what else?"
date: 2011-07-19
forum: Packaging and Compiling Programs
---

### Post by XubuRoxMySox on 2011-07-19
I want to create a .deb package of a wicked-cool application called [ClogAmp]("http://sourceforge.net/projects/clogamp/").

It isn't actually meant to install in the usual sense which may be the trouble, I'm not sure. It comes as a ZIP file. ClogAmp is for dance teachers (it was made specifically for *clog-dancing* teachers, too, how totally cool!) to speed up and slow down the tempo of a song without altering it's pitch, loop, do some minor editing, and save the work to pass along to other people.

Yes, I can do that with Audacity. But this project means alot to me as it was created and offered by a fellow clog-dancer! I'd love to have it available to other dancers who use Ubuntu as I do!

Neither Checkinstall nor Alien would create a .deb for me from the file. What should I try next?

Thanks,
Robin

---

### Post by SevenMachines on 2011-07-20
Hi there. Just to clear up a bit of confusion...

* alien is a tool to convert between different linux packages, deb, rpm, etc. Clogamp has no linux package so this isnt any use

* checkinstall is a tool to build generate a 'pseudo' debian package from source code that has a working linux supported build available

Unfortunately, although clogamp uses many cross-platform libraries, it itself is a windows only program at the moment, there is no working linux build i can see. If you have the programming skills it might not take too much to make it truly cross platform and therefore buildable on linux but at the moment no.

clogamp does seem to work on linux using wine so at least you can use it on linux but as far as packaging it, it isnt currently possible as far as i can see

---

### Post by XubuRoxMySox on 2011-07-20
Thank you!! I guess the problem was less obvious because of all the MS cruft in there. I have Wine installed and ClogAmp does run okay in it, but I think Audacity is a better fit after all. I've asked the developer to make a Linux-compatible package, and *he thought he had*. But if it takes Wine to make it work, um, oh well. Perhaps someone else will discover this fine app and remake it for Linux.

Thanks again for your efforts!

-Robin

---

