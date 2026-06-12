---
title: "[SOLVED] Terminal access to File attributes"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-09-22
I need a way to determine the number of pages of a pdf by running a command in the terminal. If I right click the file and go to properties>Document, I can see how many pages there are but I need a script to automatically pass that value as an argument. So, what command does nautilus execute to determine that information?

Thanks

---

### Post by Mornedhel on 2008-09-22
You'll want pdfinfo.

---

### Post by JohnGalt131 on 2008-09-22
> **Mornedhel said:**
> You'll want pdfinfo.

Thank you.

Do you perhaps know how to send only the 6th field to stdout?

---

### Post by JohnGalt131 on 2008-09-22
Oh, wait.

pdfinfo file.pdf | grep Pages.

but then how do I get Only the value 2, or whatever the number is?

---

### Post by Mornedhel on 2008-09-22
pdfinfo your_document.pdf | grep Pages will output something like

"Pages :         357"

If you want only the 357 to show, you will need a bit of sed :

pdfinfo your_document.pdf | grep Pages | sed 's/[^0-9]*//g'

---

### Post by JohnGalt131 on 2008-09-22
> **Mornedhel said:**
> pdfinfo your_document.pdf | grep Pages will output something like

"Pages :         357"

If you want only the 357 to show, you will need a bit of sed. I'm afraid I need to read up on sed myself...

You have helped immensely, thank you!

---

### Post by Mornedhel on 2008-09-22
Sorry, I edited my above reply but you were too quick.

---

