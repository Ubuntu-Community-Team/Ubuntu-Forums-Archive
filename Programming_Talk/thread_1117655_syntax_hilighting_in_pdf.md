---
title: "syntax hilighting in pdf"
date: 2009-04-06
forum: Programming Talk
---

### Post by Tuna-Fish on 2009-04-06
I need to put some code in a pdf. Does anyone know a good method of getting pretty syntax hilighting in abiword, OO.o or other program that can export into pdf?

---

### Post by Zugzwang on 2009-04-06
> **Tuna-Fish said:**
> I need to put some code in a pdf. Does anyone know a good method of getting pretty syntax hilighting in abiword, OO.o or other program that can export into pdf?

Open it in gedit/kile/whatever and print it to a file. Then convert the .ps file to pdf using ps2pdf.

---

### Post by Tuna-Fish on 2009-04-06
> **Zugzwang said:**
> Open it in gedit/kile/whatever and print it to a file. Then convert the .ps file to pdf using ps2pdf.

Thanks

---

### Post by hessiess on 2009-04-06
You could also use LaTeX and the listlistings package.

---

### Post by nvteighen on 2009-04-06
Install cups-pdf and you'll have an automatic PDF printer driver you can configure as a new printer. It will output everything to ~/PDF

---

### Post by hugmenot on 2009-04-08
You can use vim and it&#8217;s TOhtml command ( :help tohtml ). Then paste the colored HTML into your word processor.

---

### Post by casevh on 2009-04-08
Or you can use scite and directly export highlighted text to pdf.

---

