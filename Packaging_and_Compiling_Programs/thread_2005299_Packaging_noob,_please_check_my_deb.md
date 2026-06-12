---
title: "Packaging noob, please check my deb"
date: 2012-06-17
forum: Packaging and Compiling Programs
---

### Post by Paradox27 on 2012-06-17
Hello :)
I am a noob in linux in general but I tried packaging and I think it went OK, at least with me...
[IMG]http://img221.imageshack.us/img221/4576/99945786.png[/IMG]
Here's an image of my application that I packaged.

It makes Unity quicklists, with the option to add shortcuts on the launchers! It can be handy when you want to have lots of them!

This is my deb file, if you can inspect it, please do:
[http://dl.dropbox.com/u/85430924/ulc_1.0-0ubuntu1_i386.deb](http://dl.dropbox.com/u/85430924/ulc_1.0-0ubuntu1_i386.deb)
I'd like to inform me, if you want, ofcourse, if the program installs correctly and runs as it should.

Also, you can test the application itself, if you want and comment me about it.

About the source code of the application, please see this thread:
[http://ubuntuforums.org/showthread.php?t=2003828](http://ubuntuforums.org/showthread.php?t=2003828)

Thanks alot!:KS:KS:KS

Looking forward for your comments!

---

### Post by MG&amp;TL on 2012-06-17
Okay, try and make your control file a bit more professional-you must have an email, right?

As for testing, make a PPA and I'll do all the testing you want. :)

---

### Post by Paradox27 on 2012-06-17
> **MG&TL said:**
> Okay, try and make your control file a bit more professional-you must have an email, right?

As for testing, make a PPA and I'll do all the testing you want. :)
I just read about PPAs and I find them very difficult to understand. They have something to do with launchpad.org or something and building from source. Anyway, isn't there any easier way to do it, like this:
[http://maketecheasier.com/run-32-bit-apps-in-64-bit-linux/2009/08/10](http://maketecheasier.com/run-32-bit-apps-in-64-bit-linux/2009/08/10) ?:confused:

---

### Post by MG&amp;TL on 2012-06-17
> **Paradox27 said:**
> I just read about PPAs and I find them very difficult to understand. They have something to do with launchpad.org or something and building from source. Anyway, isn't there any easier way to do it, like this:
[http://maketecheasier.com/run-32-bit-apps-in-64-bit-linux/2009/08/10](http://maketecheasier.com/run-32-bit-apps-in-64-bit-linux/2009/08/10) ?:confused:

Yes, but it's a large dependency you don't need. And that doesn't take into account updates, or dependencies as such. Most app developers use PPAs, they're simpler than the manual makes them look.

Anyway, PPAs:

1. Make account on launchpad.net, if you haven't already. Launchpad is a hosting/translation/source website for pretty much the whole of Ubuntu.

2. Sign the Ubuntu code of conduct. It's a very good idea to do this anyway, but you do need to for PPAs. [https://help.ubuntu.com/community/SigningCodeofConduct](https://help.ubuntu.com/community/SigningCodeofConduct)

3. Go to your page, if your username was paradox, it would be launchpad.net/~paradox.

4. Click on "new PPA" and follow the wizard.

5. Run "debuild -S" in your source tree (the one with the debian/ folder) to generate some signed change files.

6. Run the dput command as stated on the PPA page.

7. Wait for it to build, (might need to fix some errors), and bob's your uncle. Fully working PPA that users can add and receive updates from. Built for their architecture. 

Not saying you have to do this, but I **strongly**recommend it. Very useful things, PPAs.

---

