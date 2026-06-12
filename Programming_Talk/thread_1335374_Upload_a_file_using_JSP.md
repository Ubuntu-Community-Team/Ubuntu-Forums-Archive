---
title: "Upload a file using JSP"
date: 2009-11-23
forum: Programming Talk
---

### Post by cph05a on 2009-11-23
I'm trying to upload a file using org.apache.commons.fileupload in a JSP page. I can get it working as a servlet, but I would prefer it to work in JSP. The problem is that org.apache.commons.fileupload uses javax.servlet.ServletInputStream and I can't figure out how to import the javax.servelet package in the JSP page. Any ideas?

---

### Post by froggyswamp on 2009-11-23
My wild guess is that it's probably impossible cause I think a JSP page is under the hood the data of a (large) servlet function, and when the servlet executes the function (that is the .jsp page) it probably already finished getting the get/post data.
If I'm correct you should probably try to forward that data from the servlet (i.e. through some session variable) to the desired .jsp page.

---

