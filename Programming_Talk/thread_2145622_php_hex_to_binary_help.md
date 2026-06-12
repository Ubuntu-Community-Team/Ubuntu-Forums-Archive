---
title: "php hex to binary help"
date: 2013-05-16
forum: Programming Talk
---

### Post by bzKniGhtz on 2013-05-16
[COLOR=#333333][FONT=Helvetica Neue]I tried to encrypt 'hello' with SHA1 and convert it from hex to decimal. But the output of the binary (shown below) isn't showing binary.
SHA1: aaf4c61ddcc5e8a2dabede0f3b482cd9aea9434d[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]binary: ªôÆÜÅè¢Ú¾Þ;H,Ù®©CM

additional info: I run my own webserver with ubuntu, apache.

hex to binary function I used:
[/FONT][/COLOR]<?php function hex2bin($h)
  {
    if (!is_string($h)) return null;
    $r='';
    for ($a=0; $a<strlen($h); $a+=2) { 
        $r.=chr(hexdec($h{$a}.$h{($a+1)})); 
     }
    return $r;
  }  ?>

---

