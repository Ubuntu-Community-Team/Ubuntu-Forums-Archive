---
title: "Editing a webpage created with MS Front Page with Ubuntu"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by sunwatt on 2011-11-01
Years ago when I was using Win XP I built a webpage with MS Front Page.

Someone told me the html from FrontPage was propitiatory, and I wouldn't be able to make changes now that I am on Ubuntu. Or that there would be glitches....

Is this true?

If so, do I have any options?

If not, with my low level skills, whats my best open source web editor?

Maybe there is a thread on this, if so please direct me to it.

Thanks

Jim
System76 Starling 40GB SSD
Ubuntu 11.04

---

### Post by SeijiSensei on 2011-11-01
The HTML code itself is probably editable in any text editor, but FrontPage also used some proprietary extensions for certain tasks like forms processing.  If you used those functions, they won't work outside the FP environment.  A simple HTML-only page should be fine.

---

### Post by Lars Noodén on 2011-11-01
> **sunwatt said:**
> If not, with my low level skills, whats my best open source web editor?

There is [Bluefish](http://bluefish.openoffice.nl/) which does a good job.  So does [Kompozer](http://kompozer.net/).  Both are in the repositories so you can get them via the Software Center or else via Synaptic.

The output from FrontPage can be a mess.  I'm not sure if it is still necessary to run it through [HTML Tidy](http://tidy.sourceforge.net/) first.

---

### Post by sunwatt on 2011-11-02
Not sure what html tidy is... but my site is really simple.

Pictures and text, links between index and pages.

Thanks!!

Jim

---

### Post by Lars Noodén on 2011-11-02
[Tidy](http://tidy.sourceforge.net/) is like a spell-checker for your (X)HTML.  It will clean up and normalized incorrectly coded pages, making them easier to work with.  It's not necessary if you are using Bluefish or another standards-compliant editor, but it is necessary if you are coding by hand or importing from bad editors.

---

### Post by sunwatt on 2011-11-02
Thanks... its been a decade since I did any html editing, or uploaded a webpage.

Can you direct me to a simple tutorial before I start back up on this?

I'll take a look at Bluefish....  many many thanks.

Jim

---

### Post by Lars Noodén on 2011-11-02
I can't find any simple tutorial for Tidy. There are [lots of options](http://tidy.sourceforge.net/docs/quickref.html).  I generally used -modify and you might find -asxml useful when dealing with old non-XHTML pages.

---

### Post by sunwatt on 2011-11-02
Thank you... but as my site is bare bones, maybe I can get away with just trying to edit it, and see how that goes.

Ill back up everything 1st  

A friend told me to try seamonkey for HTML editing, and uploading the edited product.

Thanks everyone.

Jim

---

### Post by CharlesA on 2011-11-02
Using an HTML validator such as this one: [http://validator.w3.org/](http://validator.w3.org/) helps quite a bit too.

---

### Post by sunwatt on 2011-11-02
Great support, many thanks... As long as I back up before I start, I know I can do what I need to do.

And not mess up  :)

Jim

---

### Post by CharlesA on 2011-11-02
> **sunwatt said:**
> Great support, many thanks... As long as I back up before I start, I know I can do what I need to do.

And not mess up  :)

Jim
Backups are always a good thing to have.

I have also used [Total Validator]("http://www.totalvalidator.com/") for checking my entire site at once, so much easier then having to do each page individually.

---

### Post by sunwatt on 2011-11-02
Maybe I can find something about it, and screenshots... Seems like I use Total Validator to examine my site and diagnose and or fix problems...

Cool

---

### Post by CharlesA on 2011-11-02
> **sunwatt said:**
> Maybe I can find something about it, and screenshots... Seems like I use Total Validator to examine my site and diagnose and or fix problems...

Cool
I'm not sure if they still do screenshots or not, but it is mostly used to validate your HTML code and CSS to make sure you are following web standards.

---

### Post by Lars Noodén on 2011-11-02
You can do something similar with tidy and find.

```

find /var/www -name '*.html' -exec tidy -m -xml {} \;

```

---

### Post by CharlesA on 2011-11-02
> **Lars Noodén said:**
> You can do something similar with tidy and find.

```

find /var/www -name '*.html' -exec tidy -m -xml {} \;

```
Nice.

I mostly use it since I have coded my site in php and xhtml-strict and that can be a bit of a pain to validate from the files itself.

---

