---
title: "How to use debconf go-back feature"
date: 2015-06-15
forum: Packaging and Compiling Programs
---

### Post by dagoaty on 2015-06-15
In the debconf-devel man page [http://manpages.ubuntu.com/manpages/utopic/man7/debconf-devel.7.html](http://manpages.ubuntu.com/manpages/utopic/man7/debconf-devel.7.html) there is a section titled 'Letting the user back up'. I have been trying for some time now to get this to work in a custom package in a custom disk image with no success. I have pasted in almost exactly the example in the above link and I still cannot make the backup feature behave as I expect.

In the example in the link I am able to go back between the 'two unrelated questions' contained in STATE=1 however once I move on to STATE=2 clicking the 'Go Back' button simply continues the install. Once I get to the end the install errors because my custom package did not successfully configure.

Does anyone have any examples of code using the Go Back feature which work? Is anyone aware of problems with this example code? I assume I am doing something stupid here.

TIA

---

