---
title: "Trying to use Firefox Dev tools - can't see data output"
date: 2017-04-13
forum: Programming Talk
---

### Post by pizzipie on 2017-04-13
Hi,

I guess Firebug is no more in Firefox 52 so I am trying to use Firefox Developer Tool (FDT) in place of Firebug.

I have a program consisting of one .html file and one .php file. The php file is accessed through an AJAX call with data returned to the calling program in json format.

Something is wrong and I can't even see any of the output in my test statements like "print_r($_POST)" or "echo 'query ... '. $query"  from the .php program in the FDT. The error does not show up in /var/log/apache2/error.log as some php errors do. (I can still use Firebug but the call to the .php file does not even show up in Net or Console while the .html file does.)

Any ideas on how to fix this.

I can't find any documentation for Firefox Developer Tool. I am just a beginning/low-intermediate level programmer so a lot of technical stuff goes right by me.

Thanks for any help you all can give me.

R

---

