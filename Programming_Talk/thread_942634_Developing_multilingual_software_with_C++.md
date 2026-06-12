---
title: "Developing multilingual software with C++"
date: 2008-10-09
forum: Programming Talk
---

### Post by extruct on 2008-10-09
Hello I want to develop some application and I want to be multilingual.
Since I dont know all the languages I want to allow people (translators) to be able in easy way to add new language without messing with the code and without recompiling the software.
What is the common way to develop multilingual software in C++?

Thanks a lot!

---

### Post by issih on 2008-10-09
The basic technique is that wherever you have text that is presented to the user in your program, rather than having text hard coded in the program, you instead retrieve the text from a bank of phrases, which you initialise from a language file.

basically you create a large array of strings, which you initialise from a file with all the text fragments you require written in a certain language. When you then need one of those text fragments you reference it via the appropriate item in the array.

That's overly crude, but you get the idea. Doing it that way means that language options are simply a matter of getting the text fragments translated and having a new file to load into the library.

Hope that helps

---

### Post by hod139 on 2008-10-09
The google search term you are looking for is internationalization, which is often abbreviated i18n.  Here are Sun's and Debian's pages on the topic:
Sun: [http://developers.sun.com/solaris/articles/i18n/Cguidelines.I18N.html](http://developers.sun.com/solaris/articles/i18n/Cguidelines.I18N.html)
Debian:[http://www.debian.org/doc/manuals/intro-i18n/](http://www.debian.org/doc/manuals/intro-i18n/)

---

### Post by extruct on 2008-10-09
Yea well I understand this. I developed multilingual application in php. I simply had a file with the name of the language like english.php, russian.php and etc, and according to users configuration I included this file. The file was simply an array (or more like a map in C++ where the key of the array could be a string).
I just don't know how to accomplish it in C++. I can't simply have a h/c file with a large array, I tough about XML files, but I never worked with one and the problem is not to learn XML but to do it in the most efficient and correct way, I don't want to reinvent the wheel.
I hope you got my point.
Thanks again for the help!

---

### Post by hod139 on 2008-10-09
There is a gnu tool called gettext, [http://www.gnu.org/software/gettext/](http://www.gnu.org/software/gettext/), that will help you write localized c++ code.  I'm hoping that this is what you are looking for.

---

### Post by extruct on 2008-10-09
I got recommendation for gettext today 3 time, I just can't understand what it is useful for :\
I dug wikipedia in english/russian i read their home page I just can't find the logic :\
So well it allows me to "extract" strings from C files into PO files what next?
Maybe I'm yo dumb to get it..

---

### Post by snova on 2008-10-09
Gettext is the typical way to make translatable software. It takes a bit of setup, but it should be easy enough.

First, you wrap translatable strings with a call to gettext(). Since this is a rather long call for every visible string in the program, most of the time you use a macro to define "_" to gettext, so that you can use _() instead.

Then you use a special program to extract these strings and put them in a .po file. Translators then copy this file and modify it for each target language.

Another program then "compiles" these .po files into binary .mo files, which are installed with your program.

Your program, with a little initialization magic, sets up Gettext to use these files. Then calls to gettext() or _() will return the translated form of the string.

This should suffice as a high-level overview, but read the Gettext documentation for the fine print. Things also get a little more complicated when you put strings in places where function calls aren't valid syntax, because Gettext still has to extract these strings for the .po files.

---

### Post by extruct on 2008-10-10
Ok, anyway I still don't see the use of it...
Is like saving the language in text file..

---

### Post by Tomosaur on 2008-10-10
> **extruct said:**
> Ok, anyway I still don't see the use of it...
Is like saving the language in text file..

How else would you go about it?

Until we have reliable software based language translators, writing the strings to files is the only real way to go.

So your two options:

A: Write every single string for every single language as part of the program, then use logic to decide which language to use. I don't need to tell you why this is a terrible idea.

B: Write a file for each language which contains the strings **in** that language, using gettext to read the strings when required.

Your call :P

---

### Post by extruct on 2008-10-10
Well B is my option :p

The question I would like to ask, what will be faster a text file like:
String1 = Hello World
String2 = Press ESC to exit.
and etc or XML file?
(I never worked with XML files, so I assume Ill need to write a parser or to use a ready one).

---

### Post by ZuLuuuuuu on 2008-10-10
I am also interested in this topic but have no experience. As *extruct* said saving the translations in XML files which are easily editable by  any people sounds prettier. Also it will be programming language independent so that it is more portable. Like:

```
<translation>
    <okay>tamam</okay>
    <cancel>iptal</cancel>
    <apply>uygula</apply>
</translation>
```

Isn't it? I don't know though if it is possible to do that in C++. Actually I don't know much about gettext either.

---

### Post by dwhitney67 on 2008-10-10
My former employer uses an Excel spreadsheet.  During runtime, the application is provided a file, with comma-separated fields, that is generated from the spreadsheet.  The first column is the text-field identifier, the next column the English word(s), and the following columns are the corresponding word(s) in the foreign languages.

The rationale for using Excel is that it is widely used by industry.  My former employer employed another company to facilitate with the proper word translation(s).  We could not assume that this other company had Linux systems, or even Open Office.

Anyhow, the operator who is using the application determines which language to use; the application provides the operator with a menu of choices.  By default, English is used.

---

