---
title: "Web-based School Information System"
date: 2008-01-20
forum: Philippine Team
---

### Post by mitchi on 2008-01-20
Hi! I'm trying to set-up a web-based system for our school using Linux Apache/MySQL/PHP, and I would like to ask for your ideas.

There's centre-sis and focus-sis but they're postgresql based. I would prefer using MySQL.

Also, I would to ask about printing reports and forms from my system. I haven't tried this before and it would be very helpful if you could list down some tips or tricks on how to do this.

Thank you.

---

### Post by loell on 2008-01-20
as for report generation, you can generate PDF on the fly

with **php-fpdf**.

---

### Post by mitchi on 2008-01-20
yeah, but can i design my page with our letterhead, format and other stuff?

---

### Post by loell on 2008-01-20
i believe so, you can,

there should be a method in the module where you can attach a static image.


here is an example :) 

[http://www.fpdf.org/en/tutorial/tuto2.htm](http://www.fpdf.org/en/tutorial/tuto2.htm)

---

### Post by Stu09 on 2008-01-20
Hi Mitchi,

Is Moodle the kind of thing you're after ?

[www.moodle.org](www.moodle.org)

---

### Post by mitchi on 2008-02-12
> **Stu09 said:**
> Hi Mitchi,

Is Moodle the kind of thing you're after ?

[www.moodle.org](www.moodle.org)


parang ganun na rin po, kaso to be specific, Student Information System, isang online Student Registration + some features like centre-sis or focus-sis. Just like online enrollment na ginagamit ng mapua.

---

### Post by vrix on 2008-02-12
greetings!

If you're going to print reports and forms, and since this is web-based, you can print it directly from the browser, or use javascript to do this. You just have to get the data from the mysql and print it to the browser using php, align it correctly on the page, and print it using javascript.

If these are existing reports and forms just use a link for them to download and print it by their own application.

hope this helps.

---

### Post by SLEducator on 2009-02-26
The future of the Open Source SIS :
Please come and join our community at [http://www.opensis.com](http://www.opensis.com) and our development team at
[https://eduforge.org/projects/opensismysql/](https://eduforge.org/projects/opensismysql/)
[https://eduforge.org/projects/opensis](https://eduforge.org/projects/opensis)
opensis is a stable fork of Focus with over 200 enhancements
and our new project opensis-mysql is dedicated to creating and ADOdb code base that
will be MySQL ready and in the future database independent.

---

