---
title: "Lost on packaging - how to figure out dependencies?"
date: 2014-03-15
forum: Packaging and Compiling Programs
---

### Post by slooksterpsv on 2014-03-15
I'm trying to figure out how to figure out build dependencies.

I built my app using Qt Creator creating a Qt GUI Application (not Quickly), I have a Makefile and I've created the directory for debian that contains the control, copyright, etc. etc. etc. files.

Well the guide on page 6 says:
. We will need to add the packages needed to compile the application to Build-Depends:. For hello, make sure that it includes at least:

Build-Depends: debhelper (>= 9)
You will also need to fill in a description of the program in the Description: field.

But where does it say how to find those dependencies? I'm lost from this point on.

---

### Post by slooksterpsv on 2014-03-15
And now it won't let me run bzr dh-make saying this:
shawn@shawn-Satellite-C75D-A:~/Development/C++/QT/EFIBootOrder/build-EFIBootOrder-Desktop-Release$ bzr dh-make EFIBootOrder 0.1 EFIBootOrder-0.1.tar.gz
bzr: ERROR: Either run the command from an existing branch of upstream, or move EFIBootOrder aside and a new branch will be created there.
shawn@shawn-Satellite-C75D-A:~/Development/C++/QT/EFIBootOrder/build-EFIBootOrder-Desktop-Release$ 

GRRR!!!!!

---

### Post by lordkom on 2014-03-26
BuildDependencies are any packages you need to compile your application. For example, assuming you're using c++, you might want to list g++ as a dep, along with any packages that include libraries your application uses, e.g: foo-dev, which has the foo objects you're linking against.

Check out [https://wiki.ubuntu.com/PbuilderHowto](https://wiki.ubuntu.com/PbuilderHowto) and create a pristine environment to build packages and verify the build deps are indeed correct. There are other alternatives to pbuilder also, but this works for me.

---

### Post by slooksterpsv on 2014-03-28
Oh I forgot about this thread, I figured it out overall:

objdump -p ./efibootorder | grep NEEDED

That gives me what's required so I just search:

dpkg -S libQt5Web.so.5 - or whatever it is and it brings up

libqt5web5

I just put those in my control file and I'm set =D.

---

