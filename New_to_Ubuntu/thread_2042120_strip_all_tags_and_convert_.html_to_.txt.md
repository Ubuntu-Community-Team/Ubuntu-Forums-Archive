---
title: "strip all tags and convert .html to .txt?"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by bostoncab on 2012-08-14
Hello,

I have a folder filled with .html files. I want to mass convert them to .txt files while stripping away all the tags etc. 

I basically just want the words from the files. Is there an easy way to do this? I could open each file individually and copy and past but that would take me like a year. 

any help would be appreciated.

---

### Post by Wim Sturkenboom on 2012-08-14
google seems to be your friend

[http://www.google.co.za/search?hl=en&site=&source=hp&q=html+to+text&btnG=Search](http://www.google.co.za/search?hl=en&site=&source=hp&q=html+to+text&btnG=Search)

just go through the links ;)

This one looks promising (but you must decide for yourself): [http://www.aaronsw.com/2002/html2text/](http://www.aaronsw.com/2002/html2text/)

---

### Post by sanderj on 2012-08-14
lynx --dump blablabla.html > blablabla.txt

---

### Post by spjackson on 2012-08-14
I recommend htm2text which is available in the Ubuntu repository. There are several programs out there going by this name. [This one]("http://www.mbayer.de/html2text/") is in the Ubuntu repository.

---

### Post by bostoncab on 2012-08-14
> **sanderj said:**
> lynx --dump blablabla.html > blablabla.txt

Can you rewrite that command line for me All files are on my desktop in a folder labled html

Appreciate the help. 

Mike

---

### Post by Bucky Ball on 2012-08-14
> **sanderj said:**
> lynx --dump blablabla.html > blablabla.txt

OP reasonably new here. I'm not and I have no idea what this means. ;)

@Bostoncab: Yes, it is a help forum, but posters not having a good look to solve their problems before posting is generally frowned upon. The poster who provided the google link was trying to say this nicely, and so am I ... ;) Check my sig.

---

### Post by sanderj on 2012-08-15
> **bostoncab said:**
> Can you rewrite that command line for me All files are on my desktop in a folder labled html

Appreciate the help. 

Mike


Open a Terminal (CTRL - ALT - t)
Go to the directory containing the .html files (maybe cd Desktop/html/)
Find the name of a .html file. Let's assume somefile.html
Convert that file like this:

```
lynx --dump somefile.html > somefile.txt

```

The result should be in somefile.txt.


If lynx is not yet installed, install it via the Software Center

---

### Post by bostoncab on 2012-08-15
You cant run it on the entire folder at once?

I don't care what is generally frowned upon. If you are not looking to help in absolute beginner talk you should be down the hall in the sneering know it all lounge. 

> **sanderj said:**
> Open a Terminal (CTRL - ALT - t)
Go to the directory containing the .html files (maybe cd Desktop/html/)
Find the name of a .html file. Let's assume somefile.html
Convert that file like this:

```
lynx --dump somefile.html > somefile.txt

```

The result should be in somefile.txt.


If lynx is not yet installed, install it via the Software Center

---

### Post by vasa1 on 2012-08-15
Advanced HTML to text converter (html2text) also looks promising. Plus it's "supported" by Canonical.

Edit: Already suggested by spjackson.

---

### Post by hakermania on 2012-08-15
> **bostoncab said:**
> You cant run it on the entire folder at once?

I don't care what is generally frowned upon. If you are not looking to help in absolute beginner talk you should be down the hall in the sneering know it all lounge.

We are all trying to help here :)

For you occasion, as you are an absolute beginner, I would recommend the following:

First of all, give to your folder with your html files an easy name, like 'html' and place it to your home folder (beside your Music, Videos etc folders).

Then, open a terminal via Ctrl+Alt+T

You have to install a package. Give the command:
```

sudo apt-get install lynx-cur

```
it will ask for your password. Give it your login password (nothing will be printed to screen but don't worry) and hit [Enter]. If it asks you for confirmatin whether to install the package or not, give it a Y and hit [Enter] again. Wait till the installation process is over.

By default, when you open a terminal you are "located" at your home folder, so you can "cd" (**c**hange **d**irectory) to your 'html' folder with the command:
```

cd html

```
Once you are inside your html folder in your terminal, run the following command:
```

nano extract_text.sh

```
'nano' is a command line text editor. It will let you create and insert text into the file extract_text.sh

Inside the text copy and paste (or write) the following:
```

#!/bin/bash

for html_file in *.html; do
   txt_file=${html_file%.html}".txt"
   lynx --dump "$html_file" > "$txt_file"
done

```
To copy **from** the terminal you have to use Ctrl+Shift+C and to past **to** the terminal you have to use Ctrl+Shift+V. Of course you can do all these via the right-click menu as well.

After you've written all of the above inside your text file in the terminal hit Ctrl+O, then [Enter] so as to save your file and then Ctrl+X so as to exit the editor.

Now you have a file named extract_text.sh placed inside your 'html' folder, where all of your html files are.

Linux systems understand as programs only files that have the executable bit. This bit can be placed to a file with the command:
```

chmod +x some_file

```
After this, the system tricks 'some_file' as a program.

So, you have to do the same to your extract_text.sh file:
```

chmdo +x extract_text.sh

```
and your file will be tricked as a program from now on.

In order to execute this program, just give
```

./extract_text.sh

```
and all your html files will be turned into txt, without the html tags inside them.

I hoped you learned something new from my post. If you want better to understand what the extract_text.sh script program did, continue reading, I will explain.

Let's take again a look of the script:
```

#!/bin/bash

for html_file in *.html; do
   txt_file=${html_file%.html}".txt"
   lynx --dump "$html_file" > "$txt_file"
done

```

The first line, *#!/bin/bash* refers to which program we want to execute the code that follows. It refers to the so-called **interpreter**. 'bash' is a very good and widely used one. There are others, like sh, csh, ksh etc.

Then, we have *for html_file in *.html; do*. This is a for loop. It searches all the files in the current directory that end with .html and, for each of them, it says *html_file="filename.html"*, where filename.html is a corresponding file in your directory. So, each time this loops run, the $html_file variable is different and contains a different filename of your .html files.

The line *txt_file=${html_file%.html}".txt"* creates a new variable called txt_file and makes it be the html_file variable without the .html extension but instead, with the .txt extension, and, finally, the line *   lynx --dump "$html_file" > "$txt_file"* does the conversion, reading from the $html_file and writing to $txt_file

---

### Post by sanderj on 2012-08-15
> **bostoncab said:**
> You cant run it on the entire folder at once?


Yes, you can, but first things first. So: Have you done it? Does it work?

> **bostoncab said:**
> 
I don't care what is generally frowned upon. 


I don't understand what you're referring to.

> **bostoncab said:**
> 
If you are not looking to help in absolute beginner talk you should be down the hall in the sneering know it all lounge.

Please explain? Is your quote meant to be offensive?

Oh wait: Your statement "I don't care what is generally frowned upon. " was the introduction to your offense? Please let us know if that is your approach. If so, I would say you're biting the hand that feeds ...

---

### Post by Bucky Ball on 2012-08-15
> **bostoncab said:**
> I don't care what is generally frowned upon. If you are not looking to help in absolute beginner talk you should be down the hall in the sneering know it all lounge.

Presume this it to me. I intended no malice and this was friendly advice. Puzzled by your response. Anyhow, I'll leave it there. Have fun and hope you'all get somewhere with the issues. Hakermania looks like they're on to it in post #11. ;)

---

### Post by CharlesA on 2012-08-15
> **Bucky Ball said:**
> Presume this it to me. I intended no malice and this was friendly advice. Puzzled by your response. Anyhow, I'll leave it there. Have fun and hope you'all get somewhere with the issues. Hakermania looks like they're on to it in post #11. ;)

Looks that way.

Just a friendly reminds to everyone: remember to respect others even if you disagree with them.

---

