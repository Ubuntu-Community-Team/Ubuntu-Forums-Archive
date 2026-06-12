---
title: "Error in PHP Code"
date: 2007-10-30
forum: Programming Talk
---

### Post by Peter1234123 on 2007-10-30
I was wondering what to do with this error I get from my server..```
 Fatal error: SUHOSIN - Use of eval is forbidden by configuration in /home/mydir/public_html/phpBB2/includes/template.php(174) : eval()'d code on line 174
```
The code on Line 174 of Template.php is: ```
eval('$lastiteration = sizeof(' . $str . ') - 1;');
``` I was wondering if there is an alternate function to use, or how to fix this error. Thanks!

---

### Post by dataw0lf on 2007-10-30
I assume this is a shared hosting account you're running this on.  Your provider has added 'eval' to the disable_functions string in php.ini, and most likely is running it in safe mode.

Cheers.

---

### Post by Mickeysofine1972 on 2007-10-30
> **Peter1234123 said:**
> I was wondering what to do with this error I get from my server..```
 Fatal error: SUHOSIN - Use of eval is forbidden by configuration in /home/mydir/public_html/phpBB2/includes/template.php(174) : eval()'d code on line 174
```
The code on Line 174 of Template.php is: ```
eval('$lastiteration = sizeof(' . $str . ') - 1;');
``` I was wondering if there is an alternate function to use, or how to fix this error. Thanks!

I think the error is in the way you use the quotes, I might be wrong as I've only looked a few seconds but it seems it should read:

```
eval("$lastiteration = sizeof($str) - 1;");
```

Mike

---

### Post by dataw0lf on 2007-10-30
> **Mickeysofine1972 said:**
> I think the error is in the way you use the quotes

It has nothing to do with quotes.  It's the security of the shared host he is using, or he added eval to be blocked in his own php.ini.

edit:  if it had failed on the quotes, it would've given a syntax error (which the code is likely to do).  But it's failing before it even evaluates the content of the eval() (due to being blocked).

---

### Post by smartbei on 2007-10-30
I actually don't see why it would fail on syntax. 
[php]
$s  = "testing";
$s2 = 'before ' . $s . ' after';
$s3 = "before $s after";
[/php]
Aren't $s3 and $s2 equal?

What I am not understanding is why that code needs to be in an eval in the first place, though perhaps I am missing something major here.

---

### Post by dataw0lf on 2007-10-30
> **smartbei said:**
> 
What I am not understanding is why that code needs to be in an eval in the first place, though perhaps I am missing something major here.
I'm assuming it's something installable, like PHPNuke (which is what it looks like with that sort of garbage).

---

