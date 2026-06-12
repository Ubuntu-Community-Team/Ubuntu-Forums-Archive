---
title: "Replacing various html attributes with CSS so it's valid with XHTML 1.1"
date: 2007-09-04
forum: Programming Talk
---

### Post by user1397 on 2007-09-04
EDIT: basically, I want [_this _]("http://plaza.ufl.edu/nebreuer/testing/")to look like _[this]("http://plaza.ufl.edu/nebreuer/")_[.]("http://plaza.ufl.edu/nebreuer/")

Note that the first link is an attempt to convert the second link from XHTML 1.0 transitional to XHTML 1.1

The CSS file of link 1 is _[[U]here_]("http://plaza.ufl.edu/nebreuer/testing/style.css")[/U] and link 2 is [_here_]("http://plaza.ufl.edu/nebreuer/style.css")

For some reason, IE7 renders link 1 better than firefox...

---

### Post by Mirrorball on 2007-09-04
If you want to use XHTML 1.1, create CSS-based layout instead of a table-based one. Table-based layouts are not recommended anymore.

---

### Post by user1397 on 2007-09-04
> **Mirrorball said:**
> If you want to use XHTML 1.1, create CSS-based layout instead of a table-based one. Table-based layouts are not recommended anymore.I see...

Thanks man.

---

### Post by LaRoza on 2007-09-04
> **ubuntuman001 said:**
> 
Note that the first link is an attempt to convert the second link from XHTML 1.0 transitional to XHTML 1.1


For a good example of a design with CSS and no tables, check my site (in progress, and still incomplete), [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

Look at the markup, and look at the CSS. If you are using FF, use the Web Developer tool bar, or the "Save Complete Page" extensions to get the code. (Actually, the generated code, it is all PHP)

It is XHTML 1.1, and uses a design one might have used tables for in the past.

---

### Post by user1397 on 2007-09-05
> **LaRoza said:**
> For a good example of a design with CSS and no tables, check my site (in progress, and still incomplete), [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

Look at the markup, and look at the CSS. If you are using FF, use the Web Developer tool bar, or the "Save Complete Page" extensions to get the code. (Actually, the generated code, it is all PHP)

It is XHTML 1.1, and uses a design one might have used tables for in the past.k thanks for the link, will look at it.

---

