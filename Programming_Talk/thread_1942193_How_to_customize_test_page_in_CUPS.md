---
title: "How to customize test page in CUPS?"
date: 2012-03-17
forum: Programming Talk
---

### Post by Gurmeet Singh on 2012-03-17
Hello,

I am working on to develope a printer driver for 24 pin DMP using CUPS.

After installing the driver, when i print the test page then it has been printed with some extra space at the bottom (**Image attached for the same**).
How i can remove this extra space from the test page or how i can customize the test page?

Please help.
Thanks in advance.

---

### Post by CynicRus on 2012-03-17
[http://www.cups.org/documentation.php/doc-1.4/spec-banner.html]("http://www.cups.org/documentation.php/doc-1.4/spec-banner.html")

---

### Post by Gurmeet Singh on 2012-03-27
Thanks CynicRus.

I have tried to cutomize the test page.
below is the code of default test page
```

#CUPS-BANNER
Show printer-name printer-info printer-location printer-make-and-model printer-driver-name printer-driver-version paper-size imageable-area
Header Printer Test Page
Footer Printer Test Page
Notice CUPS 1.5.0.
Image images/cups.png
Image images/color-wheel.png

```

I have removed all the contents of the page except header and footer like below
```

#CUPS-BANNER
Header Printer Test Page
Footer Printer Test Page

```
but the print out comes with same size of paper as previous.
I want to decrease the size of test page printed like i have attached image with previous post which indicates the extra area printed by printer which is not required.
Please help to sort out this issue.
Thanks in advance.

---

### Post by CynicRus on 2012-03-27
[http://www.cups.org/documentation.php/api-ppd.html#PAGE_SIZES](http://www.cups.org/documentation.php/api-ppd.html#PAGE_SIZES)

[http://www.linuxquestions.org/questions/linux-software-2/printing-non-standard-paper-sizes-on-lexmark-e330-via-cups-766115/](http://www.linuxquestions.org/questions/linux-software-2/printing-non-standard-paper-sizes-on-lexmark-e330-via-cups-766115/)

[http://stackoverflow.com/questions/1028891/whats-the-easiest-way-to-add-custom-page-sizes-to-a-ppd](http://stackoverflow.com/questions/1028891/whats-the-easiest-way-to-add-custom-page-sizes-to-a-ppd)

---

### Post by Gurmeet Singh on 2012-03-27
That means it depends upon what page size i have set in properties of printer. right?

Thanks for your response.

---

### Post by CynicRus on 2012-03-27
Yep.

---

### Post by Gurmeet Singh on 2012-03-28
Thanks alot!!!):P

---

### Post by nutrapi on 2012-03-29
always wondered how to do this but never took the time to look...awesome post!

---

