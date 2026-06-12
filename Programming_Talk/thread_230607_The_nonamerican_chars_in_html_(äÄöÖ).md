---
title: "The nonamerican chars in html (äÄöÖ)"
date: 2006-08-06
forum: Programming Talk
---

### Post by encompass on 2006-08-06
I have been programming in html for some time now... but have not figured out why the chars äÖ and other unusual charactors show up as questionmarks when I veiw the page.
I noticed one thing... the html file when saved in nvu it works properly.
I think it has to do with the code of the text file itself.  Any ideas on how I can create these char in a normal text editor and have them desplay properly?
Thanks ¶:

---

### Post by kson on 2006-08-06
&auml; (ä), &Auml; (Ä), &aring; (å), &Aring; (Å), &ouml; (ö) and &Ouml; (Ö) is one way but the problem is that ubuntu uses utf-8 and most other oses is using ISO-8859-*. Im bypassing this problem by adding ```
AddDefaultCharset ISO-8859-1
``` in a .htaccess file. Nvu uses utf-8 to so it works anyway. Texteditors have often an encoding option in the save dialog.

---

### Post by pelle.k on 2006-08-06
try ```
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
``` in <head></head>

---

### Post by ifokkema on 2006-08-06
You might also want to read this, as it's very important to know about character sets when you would ever start to program contact forms or such:
[http://www.joelonsoftware.com/printerFriendly/articles/Unicode.html](http://www.joelonsoftware.com/printerFriendly/articles/Unicode.html)

---

### Post by encompass on 2006-08-07
Great and thanks to everyone that helped me.  Yess all of the ideas have helped me.  And that last one is very important.  I am creating a php form as we speak.  Thanks.:D

---

