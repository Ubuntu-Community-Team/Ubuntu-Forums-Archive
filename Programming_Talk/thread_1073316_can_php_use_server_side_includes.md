---
title: "can php use server side includes"
date: 2009-02-18
forum: Programming Talk
---

### Post by kapi on 2009-02-18
OK so I installed php etc on intrepid ibex,

Next I altered the appropriate httpd.conf file so it recognizes the shtml extension and hey presto it accepts server side includes. provided that the web document has a shtml extension.

but I want to also use and learn PHP and use SSI inside the php file.

Have done google and can't seem to locate any info on files using a php file extension that allow the use of SSI. Because at present the SSI don't appear.

can anyone help please?

Kapi

---

### Post by kapi on 2009-02-18
To anyone that is interested I have worked it out.

I was using the wrong statement:

used this . . .

<!--#include virtual="includes/footerInclude.shtml" --> 



when I should have used this . . .
		<?include("includes/footerInclude.php");?>			

Just keep telling myself . . . I must google before doing forums

---

