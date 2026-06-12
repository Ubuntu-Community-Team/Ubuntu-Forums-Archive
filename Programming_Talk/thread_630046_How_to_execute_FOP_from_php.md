---
title: "How to execute FOP from php???"
date: 2007-12-02
forum: Programming Talk
---

### Post by Enissay on 2007-12-02
hello,
I'm using FOP to generate PDF documents by typing this command:
> fop -xml /myXMLpath/myxml.xml -xsl /myXSLpath/myxsl.xsl -pdf /desiredPathForResultingPDF/mypdf.pdf
And now i want to execute it from php.... just by pushing one button in my page i want to download the resulting pdf or display it in the navigator.......
Hope someone can help....

---

### Post by smartbei on 2007-12-03
Take a look at exec: [http://il.php.net/manual/en/function.exec.php](http://il.php.net/manual/en/function.exec.php).
You could do:
[php]
exec('fop -xml /myXMLpath/myxml.xml -xsl /myXSLpath/myxsl.xsl -pdf /desiredPathForResultingPDF/mypdf.pdf');
header('Location: http://www.yourDomainName.yourTLD/desiredPathForResultingPDF/mypdf.pdf');
[/php]
Note that this has not been tested.

---

### Post by Enissay on 2007-12-03
I tried exec(), ``, system()... and many others before... but i got nothing in my output directory!!! wich means that the command has never been executed....:(
I changed the access rights of my output file to FULL(777) but i still having nothing!!!!!
What's wrong??

---

### Post by smartbei on 2007-12-03
Try giving absolute paths instead of relative ones - I am not sure what PHP uses as the CWD (Current Working Directory). I am not at home right now so I don't have easy access to PHP and Apache.

---

### Post by Enissay on 2007-12-03
I put my xml and xsl in my php directory.... and i used 'fop -xml mymxl.xml -xsl myxsl.xsl -pdf mypdf.pdf' and it works....
i don't understand why i can't use different directory!!!
Anyway thks for your help...

---

### Post by smartbei on 2007-12-04
Have you tried using absolute paths as I said in my previous post? The absolute path to a file always starts from root, so it would like like this (assuming that your http root is /var/www and the xml file is there):
> 
/var/www/myxml.xml

Try using paths like that in PHP. I think that will solve the problem. The issue could be that when exec is run through PHP the current working directory may be different than what we want it to be. Using an absolute path lets us ignore the CWD.

In case that wasn't clear, you can indeed use a different directory - just put the whole path from the system root to the file.

---

### Post by Enissay on 2007-12-06
From the begining i was using absolute path with no result....
I have another question... how can i force the browser to open the pdf and not ask the user to download???

---

### Post by paalz on 2010-06-09
I understand this is a very old topic and i'm necroposting now, but it took me quite a time to find the answer, so this might be useful for those how search.

I've also searched the internet of this problem but haven't found a single direct answer. After a while i was luckly to fix this myself. So in my case the reason for this was the following:
when running **fop** using **exec** from PHP, the fop process is run under www-data, which has HOME at /var/www. Fop tries to create **.fop** hidden directory in the HOME of any user it is run from to keep at least one file which is **font-cache**. User www-data has no write permitions to its HOME folder with is owned by **root**. So **fop** process fails to create this folder and exits with error code.
I created **.fop** in /var/www manually and chmoded it to 777.

And now it rocks
:guitar:

You may experience other problems so i propose the following simple and standard debug technics which helped me in fixing my issue. Use **exec** in combination with console output redirection like follows
[PHP]exec("fop -c conffile.xml -fo doc.fo -pdf doc.pdf >stdout.log 2>stderr.log");[/PHP]and inspect log files after execution. In my case it gave me direct information of what is wrong
```
SEVERE: Exception
java.io.FileNotFoundException: /var/www/.fop/fop-fonts.cache (No such file or directory)

```

---

### Post by Roptaty on 2010-06-09
> **paalz said:**
> 
the fop process is run under www-data, which has HOME at /var/www. Fop tries to create **.fop** hidden directory in the HOME of any user it is run from to keep at least one file which is **font-cache**. 

Or you could tell FOP not to use cache. 

Regarding trapping output:
The exec function can take a output parameter as well.
[http://php.net/manual/en/function.exec.php](http://php.net/manual/en/function.exec.php)

Just of curiosity: Is it possible that multiple users attempt to generate a PDF at the same time?

---

