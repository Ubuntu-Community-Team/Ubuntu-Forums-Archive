---
title: "Building a basic word processor"
date: 2006-02-20
forum: Programming Talk
---

### Post by cjnodell on 2006-02-20
Hello all. I am very new to programming. I have played with java a bit, but have no real experience. I want to make a basic word processor. I want it to save rtf or html files. I needs to have a wysiwyg work environment. besides the work area, these are the following features i want to implement:

File menu with open, new, save, save as, page layout and exit. For page layout i only need to be able to specify a4 or US letter sized paper and portrait or landscape layouts.
Edit menu with cut, copy, paste, and if reasonable an undo and redo options.
Format menu to select from available fonts, sizes, styles (bold, underline, italics, sub and superscript), alignment (left, center and right), and font color.
Help menu with about info.

I am not interested in inserting pics or tables. I am also wanting to make tool bars with many or the for mentioned options available. I also want the app to be as small as possible and to use as few resources as possible. I want it to have as few dependencies as possible. It is meant to be used on legacy 486 and Pentium's. I am looking to make rapid progress, even if that means i might have overall holes in my programming game. My goal is to build this app and learn what is needed to do so, not to become the mother of all programmers.

Basically i am looking for a starting point. What language and widget set would be best for such a product? What IDE would work best? Are there any tutorials out there that will get me started along the right path?

Thaks for the help!
Charles

---

### Post by toojays on 2006-02-20
I suspect that you are in over your head, and should start with something a bit smaller. However, Qt have [a tutorial which makes a basic text editor](http://doc.trolltech.com/4.1/mainwindows-application.html). This can help you get started, to see if you understand what's involved.

You don't need to use Qt 4.1. You can install the version of Qt which is in your synaptic, and the docs for that will have a similar tutorial for your version of Qt.

---

### Post by cjnodell on 2006-02-21
I know that i can not expect to have a working product a week from now. I am not expecting to have any signifigant progress for months to come, and that is only if i am really focusing entirely on the task, which i wont be. I also know that i will need to start with the simple stuff like "Hello, World." That is all good, but i dont want to waste my time doing "Hello, World" and more with a programming language that will not meet my goals. I defeniatly like the idea of trying out a text editor, seems like somthing in the direction i want to go. I am not sure about using QT I dont really know enought to say, but i have always heard that QT and KDE are resource heavy and wont work out too well on an older comupter. Is that true?

Thanks again,
Charles

---

### Post by toojays on 2006-02-21
No, that's not true. For one thing, you can use Qt without having KDE installed at all. The real question is what are you comparing it to? On a 486, everything is going to seem kind of slow. My recollection is that Qt is more memory-efficient than GTK+, but it's been a while since I've seen a detailed paper on it.

It used to be that C++ programs took a performance hit over plain C programs, but GCC has improved a lot since then, and now it's only application startup where C applications have an "unfair" speed advantage.

That said, I'd say that neither of GTK+ or Qt are going to be the performance bottleneck for your application. Pick the one you are more comfortable with, and worry about optimising it later.

Bonus off-the-wall suggestion: Get in touch with the [Emacs/RTF](http://savannah.nongnu.org/projects/emacs-rtf/) guys. That way you can start with a working GUI editor, and you just need to add the wysiwyg RTF stuff, and get the toolbar looking the way you want it. Plus you get to use [Emacs Lisp](http://www.gnu.org/software/emacs/emacs-lisp-intro/), which is a fun language to learn, already has heaps of text-handling functionality, and is less frustrating to use that C/C++ or Java.

---

