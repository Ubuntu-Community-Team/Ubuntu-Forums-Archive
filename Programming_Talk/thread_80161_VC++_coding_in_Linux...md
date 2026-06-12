---
title: "VC++ coding in Linux.."
date: 2005-10-21
forum: Programming Talk
---

### Post by sardopsycho on 2005-10-21
My company develops medical software applications in Windows - but we are getting really sick and tired of it.  We are interested in moving all our apps over to Linux to run on Ubuntu.  I was wondering if there was a way to compile Windows VC++ source code into a Linux format that would run on Ubuntu?

Any info would be greatly apprecaited!

Paul

---

### Post by thumper on 2005-10-21
Well, if you only used ISO C++ features, steered clear of MFC, and wrote your gui using a cross platform toolkit, then you shouldn't have any problems.

However, most VC++ apps aren't like that.

If you are tied closely to the Win32 API for your GUI, then it may take quite a bit of work to port.  If you used wxWidgets, QT or some other cross platform widget set then it makes it a bit easier.

GCC is probably the way to go for the compiler, and there are some differences in the strictness of the standard between VC++ and g++.

So the big answer is:  **it depends**.

---

### Post by David Marrs on 2005-10-21
[google ](http://www.google.co.uk/search?q=visual+c%2B%2B+linux&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-GB:unofficial)finds [mainsoft](http://www.mainsoft.com/products/mainwin.aspx)

---

### Post by toojays on 2005-10-21
At work I have a Windows API application which I can compile on GNU/Linux using libwine. See the wine-dev package for details. Depending on your application though, it could take a lot of work before it will even compile. After that you will have to do a lot more work to validate that the behaviour is consistent with Windows.

If you just want to move your development environment to ubuntu though, you can install the mingw32 packages from universe, and compile binaries which run on Windows from the comfort of your Ubuntu box. Beware that the mingw32 package in Hoary made buggy executables if C++ exceptions were used. This should be fixed in Breezy, but I haven't tried it yet.

The other option is to port your Windows application to a portable toolkit like wxWidgets or Qt.

---

