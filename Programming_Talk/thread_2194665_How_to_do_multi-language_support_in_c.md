---
title: "How to do multi-language support in c?"
date: 2013-12-19
forum: Programming Talk
---

### Post by DaviesX on 2013-12-19
For example, if i have something like
```
printf ( "Output English\n" );
```
Do i just need to replace that string to other language, such as this?
```
printf ( translate_string ( "Output English\n" ) );
```
Or is there other standard way to do it? I saw there are other programs like LibreOffice that provides language pack. How can I make a language pack like that?
Thanks :)

---

### Post by tgalati4 on 2013-12-20
There are several ways to do it.  What is the endpoint for this program?  Who is going to use it?  How will it be distributed?

[http://stackoverflow.com/questions/11789615/how-to-support-multiple-language-in-a-linux-c-c-program](http://stackoverflow.com/questions/11789615/how-to-support-multiple-language-in-a-linux-c-c-program)

---

### Post by DaviesX on 2013-12-20
It's partially using gtk together with stdio. I saw the post that says "Qt and GTK+ make this (relatively) easy." So, what is the way to do it?
I am not sure how it will be distributed, though. My idea of getting this done is by making the original string a hashkey, and then the "translated" string can be obtained from a static hash table. This table could be constructed from a file (language pack?) through startup time. Maybe there are some platform specific api that I can know about the locale from? I am not though.

---

### Post by tgalati4 on 2013-12-20
Linux development is based on frameworks.  There are frameworks for everything--however, they may be in a language that you are either not familiar with or don't want to program in.  You could certainly write your own framework to handle multinational responses.  You need to weight the agony units of doing this versus the learning curve of a new library or API or new language/toolkit.

There are several tutorials on the "right way" of adding mulitnational support to your programs.  I just posted one link of several.  If you want your program to be included in an Ubuntu repository in the future, then you will need to conform to the Ubuntu/Debian way of handling internationalization.

If you are writing a small program for your own use, then you can do whatever you want.  If you have to refactor your code to handle many languages, then you will appreciate the frameworks that are already in place.

You can infer the locale from the LANG environment variable:


tgalati4@tpad-Gloria7 ~ $ env | grep LANG
LANG=en_US.UTF-8
GDM_LANG=en_US.UTF-8

In this case there are language settings for both the terminal environment and the graphical display manager environment.

You can cheat and use the *locale* command:

tgalati4@tpad-Gloria7 ~ $ locale -a
C
en_AG
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX
ru_RU.utf8
ru_UA.utf8

Some light reading:

[https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)

[https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale)

---

### Post by DaviesX on 2013-12-20
Oh, I see. I think it is not going to be included to the repository, but I will learn about the frameworks later. Thank you for your replies:)

---

