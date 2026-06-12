---
title: "Need Help:hind lang pdf to english txt  in python"
date: 2011-09-24
forum: Programming Talk
---

### Post by arsidh on 2011-09-24
Hi peaple, 
                   I am bit new to python world of programming. I have a sitution where in i have to read a pdf in hindi lang. to be coverted in to english lang, and i want to use google translater for it. Problem i have 

1. I could able to extract the text from hind pdf file to a plain text file,but txt file looks meaning less, when open in terminal, not sure how to read it.
2. How to send the words to google translater.


-Hanmant

---

### Post by simeon87 on 2011-09-24
1. Use a PDF reader to get the text or copy / paste the text to a text file and process that file. There are libraries that can read PDF files for you. I haven't really worked with it but PDF is such a common file format that I'm sure you can find software to do it for you.

2. You can visit enter the text in the URL, for example [http://translate.google.com/#auto|en|De%20man%20kocht%20een%20auto](http://translate.google.com/#auto|en|De%20man%20kocht%20een%20auto) which translates a Dutch sentence into English. Just modify the last part of the URL to send it to Google Translate. You could then read the web page (also using a software library) and get the translated text from the text field on the right.

---

### Post by arsidh on 2011-09-25
Thanks a for the help mate,  i am using google translator, but the problem is only when i copy the hindi text from pdf using adobe reader to a text file, it turns to garbage. Let me try sending same txt char. to google, may be i get lucky. :)

Thanks 
-Hanmant

---

