---
title: "Qt confusion"
date: 2008-08-27
forum: Programming Talk
---

### Post by arloth on 2008-08-27
My confusion stems from the licensing on Qt. As I understand it if one is to develop commercial software with it they need to purchase a license from Trolltech?  Can somebody enlighten me on this before I go stepping on toes?  There really isn't any mention made of this limitation when installing Qt through synaptic.  Trolltech's lack of information leads me to think I should go with GTK+ or some other LGPL/open source toolkit.  

The people I work with have been using Motif and TCL/TK, but imho Motif looks awful and TCL/TK just isn't fit for larger projects.  Qt looks attractive but I don't think I can justify the cost of a license. :(

---

### Post by hod139 on 2008-08-27
Did you read their Business model page:
  [http://trolltech.com/company/about/businessmodel](http://trolltech.com/company/about/businessmodel)

What's unclear?  Maybe your question is answered here:
  [http://trolltech.com/developer/faqs/Licensing](http://trolltech.com/developer/faqs/Licensing)

Quick answer, they use a dual license model.  If your project is open source, free.  If close source, you have to pay up.

---

### Post by dwhitney67 on 2008-08-27
My previous employer used Qt for s/w on their medical devices.  The legal advisers at the company concluded that the free version of Qt was ok to use.  The source code for the application running on the medical devices is not open-source.

Btw, Qt 3.2.3 was being used, not Qt 4.x.

---

### Post by arloth on 2008-08-27
I guess my initial confusion stemmed from no mention of the dual licensing model in the package installer.  I understand now why they do this, but it could lead some people to suffer headaches.

As they say > Remember, you must purchase a Commercial License before beginning a proprietary development project.  The Commercial License does not allow you to incorporate code developed with the Open Source Editions of Trolltech software into a proprietary project.  Which, as I understand, you can't go "oops, I need a commercial license now" and then toss all the code you worked on with the open source edition in it.

Thanks. :)

---

### Post by dwhitney67 on 2008-08-27
I want to further add that my previous employer did not use (copy/modify) Trolltech's s/w in their proprietary application; the proprietary s/w merely used Qt's header files for compiling, and the shared-libraries during runtime.

---

### Post by days_of_ruin on 2008-08-27
> **dwhitney67 said:**
> I want to further add that my previous employer did not use (copy/modify) Trolltech's s/w in their proprietary application; the proprietary s/w merely used Qt's header files for compiling, and the shared-libraries during runtime.

Is the open source version LGPL or similar?Otherwise it sounds
illegal.

---

### Post by dwhitney67 on 2008-08-27
That's what I thought too when I was employed; but the s/w manager said that everything was a-ok (because legal folks approved it).

Maybe I should contact Trolltech for a "reward" by turning in the former employer?

---

### Post by bruce89 on 2008-08-27
> **days_of_ruin said:**
> Is the open source version LGPL or similar?

It's GPL v3 now.

---

### Post by arloth on 2008-08-27
I've contacted TrollTech about pricing, but no response yet as they're based out of Norway.  If they give it to me I'll post it for those interested if they actually send anything.

---

### Post by days_of_ruin on 2008-08-27
> **bruce89 said:**
> It's GPL v3 now.
Actually its dual-licensed and but the free license is gpl.Not LGPL.
If your program doesn't derive off of the lgpl library you can keep
your program proprietary.But I think wikipedia explains it better
[http://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License#Differences_from_the_GPL]("http://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License#Differences_from_the_GPL")

---

### Post by dwhitney67 on 2008-08-28
> **days_of_ruin said:**
> Actually its dual-licensed and but the free license is gpl.Not LGPL.
If your program doesn't derive off of the lgpl library you can keep
your program proprietary.But I think wikipedia explains it better
[http://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License#Differences_from_the_GPL]("http://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License#Differences_from_the_GPL")
After reading the wiki, all I could think is "Thank god... I can continue making a living writing s/w".

I could not imagine a world where all s/w must be FOSS!  After all, I got to put food on the table for my family and a roof over their heads.

---

### Post by nvteighen on 2008-08-28
You're all plain wrong!

GPL allows commercial use of software, so you can develop a Qt application and sell it. Of course, your software will have to be GPL too.

You'll only have to pay Trolltech if you don't want to GPL your program.

---

### Post by arloth on 2008-08-28
Well, Trolltech seems to have ignored my request.  I kinda feel like I've walked into a car dealership and been told "You're not good enough to drive our cars."  [http://trolltech.com/products/qt/learnmore/licensing-pricing/pricing](http://trolltech.com/products/qt/learnmore/licensing-pricing/pricing)

As much as I'd like to go with Qt, my employer has no desire to GPL our code.  I understand their desire not to GPL it as well, the very small userbase our software has, and competition from other software.  As much as I like it, sometimes GPL just doesn't work out. :(

Off to go play with GTK now. Maybe they'll respond yet, but I'm not going to drag my feet waiting on them.

---

### Post by happysmileman on 2008-08-28
> **dwhitney67 said:**
> That's what I thought too when I was employed; but the s/w manager said that everything was a-ok (because legal folks approved it).

Maybe I should contact Trolltech for a "reward" by turning in the former employer?

Open source licenses generally state that the users have to have access to the code, if the software in question was released to the public without code, then it's illegal, but if it was only used privately then it's fine, no users outside the company means no-one outside the company needs access to the code.

---

### Post by dwhitney67 on 2008-08-28
> **happysmileman said:**
> Open source licenses generally state that the users have to have access to the code, if the software in question was released to the public without code, then it's illegal, but if it was only used privately then it's fine, no users outside the company means no-one outside the company needs access to the code.
The company's source code was not released; only the binaries (executables).  These binaries are installed on the h/w unit that is sold commercially.

P.S.  The h/w unit is a turn-key device, with a single-board computer, a HDD, a CD-ROM drive, and a touch screen.

---

### Post by happysmileman on 2008-08-28
> **dwhitney67 said:**
> The company's source code was not released; only the binaries (executables).  These binaries are installed on the h/w unit that is sold commercially.

P.S.  The h/w unit is a turn-key device, with a single-board computer, a HDD, a CD-ROM drive, and a touch screen.

Then yeah, AFAIK that's a violation. Reminds me of similar cases Busybox brought against hardware companies who used GPL'd code without offering the source to their customers

---

### Post by dwhitney67 on 2008-08-28
> **happysmileman said:**
> Then yeah, AFAIK that's a violation. Reminds me of similar cases Busybox brought against hardware companies who used GPL'd code without offering the source to their customers
I think I heard about the Busybox (BB) case; ironically my previous employer also uses BB as the mini-shell on the CD-R on which the Qt applications are delivered to the field.

From what I understood about the case, the vendor had augmented/bettered BB with additional capabilities and had failed to release the code.  It had nothing to do with the proprietary code the vendor had developed.

---

### Post by MarkieB on 2008-08-28
no longer participating in ubuntuforums.org

---

### Post by arloth on 2008-08-28
I take back what I said earlier - they just took quite a while getting back to me.

> Qt is licensed per named developer and pricing is based on the platform(s) you are developing & deploying on. Licensing is perpetual and includes the first year of maintenance, support & updates. The license fee for a single platform Qt license is $3,300,  a dual platform is $4,950 and three platform is $6,600.

---

### Post by days_of_ruin on 2008-08-28
> **arloth said:**
> I take back what I said earlier - they just took quite a while getting back to me.

Save some money and go with gtk:guitar:

---

### Post by samjh on 2008-08-29
> **days_of_ruin said:**
> Save some money and go with gtk:guitar:

Money isn't the only factor when deciding which toolkit to use.

Unlike GTK+, Qt provides a set of well-documented and supported multi-platform libraries for databases, networking, security, threading, and more.

With GTK+, you just get a GUI toolkit, and the best support you'll get are some internet forums and mailing lists: a hit-and-miss affair.  And if you're dealing with customers who need to solve problems sooner rather than later, you need all the support you can get.

$3300 per license should only be a minor dint to any software company worth their salt.

---

