---
title: "gedit to ansi?"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by Rosscopico on 2011-12-03
Hi all, I am using Ubuntu 10.04 netbook remix.
How would I go about saving/converting a file in gedit as a ansi text document?

---

### Post by cgroza on 2011-12-03
There should be a control for selecting the file format when saving.
I think what are you looking for is ASCII.

---

### Post by Rosscopico on 2011-12-03
Hi cgroza, thanks for your reply.
Unfortunately I cannot find either ANSI or ASCII when I go to save the file.
There is an ARMSCII....

---

### Post by Christmas on 2011-12-03
Hi,

ASCII uses 128 characters. You could save your document as UTF-8 and then install the **uni2ascii** package (**sudo apt-get install uni2ascii**). Try using that tool in command-line to convert your text to ASCII. Don't know how it works though, didn't try it.

Edit: Or try to save it as UTF-7?

---

### Post by mutley89 on 2011-12-03
> **Christmas said:**
> Hi,
 
 ASCII uses 128 characters. You could save your document as UTF-8 and then install the **uni2ascii** package (**sudo apt-get install uni2ascii**). Try using that tool in command-line to convert your text to ASCII. Don't know how it works though, didn't try it.
 
 Edit: Or try to save it as UTF-7?
 
 UTF-8 is ascii, when no non-ascii characters are used(non-english  alphabets and all sorts of other symbols).  No conversion is necessary.   UTF-7 and the output of uni2ascii are methods for escaping unicode or  other binary data in ascii text.
 
 OP could you clarify what exactly you need to do?  If you are saving ascii text then save as UTF-8.

---

### Post by Rosscopico on 2011-12-03
> OP could you clarify what exactly you need to do?

I have just installed Arduino IDE, & am using an existing library & menu code, but keep getting error messages regarding the library

---

### Post by Rosscopico on 2011-12-03
I have figured it out now,I was adding a void function to an existing library & learned that the positioning of the void on the line makes a big difference

---

