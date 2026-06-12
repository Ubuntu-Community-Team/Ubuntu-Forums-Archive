---
title: "What is the difference between Ubuntu/Debian packages and Redhat/Fedora packages?"
date: 2012-01-08
forum: Recurring Discussions
---

### Post by Learning Linux 2011 on 2012-01-08
I don't fully understand what I am talking about, but what is the difference between **.deb **packages and **.rpm **packages?  Are they essentially the same files inside a different "wrapper"?  

Like if there hypothetical is a program called **"Dictionary" **which contains 4 files (I'm just talking hypothetically) and you download a package called **dictionary.deb** and install it.

Then you also have a Fedora machine and then you download **dictionary.rpm**
Would the contents be the same?

---

### Post by bluexrider on 2012-01-08
The packaging policies have nothing to do with it. The mechanism  to create a DEB package is more powerful, understandable, and flexible  than the mechanism to create an RPM package.

 DEB uses a Makefile to control the package build process. DEB packages  use a separate subdirectory to contain packaging-related files where  each file has a specific purpose. DEB provides shell scripts (debhelper)  that you can use in your Makefile rules.

 RPM uses a custom packaging tool (rpmbuild) to control the package build  process. RPM combines all packaging information into a single specfile.  RPM provides macros which are expanded into Makefile rules.

hope this helps

---

### Post by Learning Linux 2011 on 2012-01-08
Yeah, I read your response to my other post too, thanks, that was pretty clear.

---

### Post by Learning Linux 2011 on 2012-01-08
> **bluexrider said:**
> The packaging policies have nothing to do with it. The mechanism  to create a DEB package is more powerful, understandable, and flexible  than the mechanism to create an RPM package.

 DEB uses a Makefile to control the package build process. DEB packages  use a separate subdirectory to contain packaging-related files where  each file has a specific purpose. DEB provides shell scripts (debhelper)  that you can use in your Makefile rules.

 RPM uses a custom packaging tool (rpmbuild) to control the package build  process. RPM combines all packaging information into a single specfile.  RPM provides macros which are expanded into Makefile rules.

hope this helps

So this brings up another question. I think you've said that the program files (for a dictionary as an example) are the same, although I guess the difference is how the files are packaged and unpackaged, is that right?  That's where the DEB versus RPM differences come into play?

---

### Post by bluexrider on 2012-01-08
Here is some Pros and Cons reading for you.

[http://unix.stackexchange.com/questions/634/what-are-the-pros-cons-of-deb-vs-rpm](http://unix.stackexchange.com/questions/634/what-are-the-pros-cons-of-deb-vs-rpm)

This may shed some light on the issue

---

### Post by misfitpierce on 2012-01-09
I like the setup of .deb personally on a side note :P 

Never was one for liking the rpm setup when I tried opensuse and Mandriva back in the day.

---

