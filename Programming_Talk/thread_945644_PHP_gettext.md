---
title: "PHP gettext"
date: 2008-10-12
forum: Programming Talk
---

### Post by Lusse on 2008-10-12
Hi everyone,

I just can't get gettext to work in php. I have this piece of code:

[PHP]setlocale(LC_ALL,"de_DE");
bindtextdomain("messages","./locale/");
textdomain("messages");

echo _("In your barrack you can train your military units.");[/PHP]

I have translated the file that xgettext generated using po-edit and compiled it into an .mo file. the mo file is in ./locale/de_DE/LC_MESSAGES/messages.mo

I have done everything I can think of but it just won't work. The reason i used de_DE is that that is the one from the example from the php website, I don't understand deutch :)

Please help!
//Linus

---

### Post by Lusse on 2008-10-12
I have also tried this on a different server (also ubuntu running php5). Please I need help!

---

### Post by Ateo on 2008-11-19
I do know you need your locale installed on your system:
Add your locale to -> /var/lib/locales/supported.d/local

Then run "dpkg-reconfigure locales" to configure the system.

However, even though I've done this, I still can't get gettext strings translated.

My translations work fine under a Gentoo system, just not any Ubuntu servers. So I know my script works.

Anyways, help would be appreciated.

---

### Post by Ateo on 2008-11-19
Update...

If you follow this guide, it will work... =)

[http://www.sourcerally.net/regin/49-How-to-get-PHP-and-gettext-working-(ubuntu,-debian](http://www.sourcerally.net/regin/49-How-to-get-PHP-and-gettext-working-(ubuntu,-debian))

---

### Post by Lusse on 2008-11-20
Thanks but I've actually written my own translation egnine which stores it in a mysql database, that suits my needs a little bit better but thanks anyway :)

---

### Post by mnajem on 2009-10-17
I can't get the following work:

[PHP] <?
  2 $language=ms;
  3 
  4 putenv("LANGUAGE=$language");
  5 putenv("LANG=$language");
  6 putenv("LC_ALL=$language");
  7 putenv("LC_MESSAGES=$language");
  8 setlocale(LC_ALL,"$language");
  9 bindtextdomain("index","/usr/share/locale/");
 10 textdomain("index");
 11 echo _("Welcome\n");
 12 echo "<br>";
 13 echo _("Bye<br>");
 14 echo _("The settings of $language is working fine");
 15 ?>
[/PHP]


I put the catalog (index.mo) in the /usr/share/locale/ms/LC_MESSAGES 

[PHP]# translation of index.po to bla
# Copyright (C) YEAR THE PACKAGE'S COPYRIGHT HOLDER
# This file is distributed under the same license as the PACKAGE package.
#
# 
msgid ""
msgstr ""
"Project-Id-Version: index\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2009-10-18 00:15+0800\n"
"PO-Revision-Date: 2009-10-18 00:25+0800\n"
"Last-Translator: bla<bla.com>\n"
"Language-Team: Malay <bla@yahoogroups.com>\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"
"X-Generator: KBabel 1.11.4\n"

#: index.php:5
msgid "Welcome"
msgstr "Selamat Datang"

#: index.php:6
msgid "Bye"
msgstr "Selamat Tinggal"
[/PHP]


Anybody of you managed to get translation work in Ubuntu?
I don't have problem with C/C++, but seems PHP can't be able to retrieve the translated strings.

Any log messages etc that can be assesed?

---

### Post by tomolas on 2010-05-28
Short version: 
1. have a look at /usr/share/i18n/SUPPORTED (the language+charset combination to use  must be listed there)
2. use the right language+country+charset combination in Poedit
3.  use the right locale(think about charset) in your script ("en_US.UTF-8" for example)
4. may need to install php-gettext package (I'm not sure)


Longer version:
For me, the problem was solved by looking at the file /usr/share/i18n/SUPPORTED. I wanted to translate a site from Slovak(sk_SK) language to English(en_US) and i wanted it to be in UTF-8.. I figured that en_US is supposed to be used with ISO-8859-1 charset and if you wanto to use UTF-8, you must set en_US.UTF-8 as the locale to be translated to.
I used Poedit with Catalog->Settings: Language:English, Country:United Stated, Charset:UTF-8, Source code charset:utf-8.

I also installed php-gettext package (in terminal: sudo apt-get install php-gettext) and restarted apache server after that (in terminal: sudo /etc/init.d/apache2 restart), but I'm not sure if that was needed.

I use Ubuntu 10.04 Lucid Lynx, PHP Version 5.3.2-1ubuntu4.2

---

