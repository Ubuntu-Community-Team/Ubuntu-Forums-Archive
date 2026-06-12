---
title: "Parsing Variables between PHP and Perl and back"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by RonaldM on 2013-06-24
Hi All

I am an absolute Newbie to Perl. In fact I don't use it, but I am required to just this once get a script to run on the Server instead of by browser. I found some ways by searches and now know how to launch the page from Perl.

However I need help with parsing variables. Simply put. I have a Perl Script that launches a PHP page. That page outputs a Variable. At the bottom of that page I have a Perl Script, which launches another page. This page runs through completes it's task and then at the bottom there is another Perl script which launches another PHP page to perform more tasks.

However where my problem lies is parsing variables between Perl and PHP.

On my first PHP page I have the following code at the bottom: (page1.php)

```
exec("perl /home/scripts/myperl1.pl $the_xml_file");
```

This code then launches the Perl Script(myperl1.pl):

```
#!/bin/sh
$var1 = $ARGV[0];
php /home/scripts/page2.php $var1;

```

Page2.php then has to retrieve the same variable in order to perform it's operations (page2.php)

```
$the_xml_file = $argv[1];
do some processing....

```


I know most of you will find errors in my script already, but please bear in mind I am flying in the dark here and just need to get this to work.

Currently with this script as it is on these pages I am getting the Perl to launch and run the PHP pages, however the variable is not being parsed from one page to another.

Any help will be greatly appreciated.

---

### Post by HeroOfCanton on 2013-06-24
Since it looks like you're already using XML you could store the variable there. Might be an easier way though. I'm not a Perl programmer and can't help with specifics. You will probably have better luck asking in the [Programming Talk forum]("http://ubuntuforums.org/forumdisplay.php?f=39").

(Or perhaps a wise and wonderful mod will move this for you)

---

### Post by RonaldM on 2013-06-24
Hi Thanks for the reply.

The XML filename is the variable, so I can't store it in the XML. As well the XML file is coming from an outside source hence I cannot make changes to it.

My apologies MOD's I didn't realise this should be in the Programming Talk Forum....Could someone please move it, or should I repost there?

Ronald

---

