---
title: "PHP Pregmatch???????? I just don't get it!"
date: 2010-07-01
forum: Programming Talk
---

### Post by minerbog on 2010-07-01
Hi,

I know I should really post this to a PHP forum but you guys have been helpful in the past so I thought I'd try you guys before registering with yet another forum!!

I have this preg_match expression from codeigniter.

```

return ( ! preg_match("/^([a-z0-9])+$/i", $str)) ? FALSE : TRUE;

```

However, it does exactly what the comments say it does, allows only alpa-numeric characters. Cool, but it doesn't allow spaces!! Not so cool :(.  Any ideas how I could change this to allow spaces???

Many Thanks All

Gav.

---

### Post by Some Penguin on 2010-07-01
*shrug*  What do you think [a-z0-9] does, in terms of screening for alphanumeric strings?  And once you realize how it works, how would you extend it?

---

### Post by Can+~ on 2010-07-01
Read about: Regular expressions.

---

### Post by minerbog on 2010-07-08
> **minerbog said:**
> Hi,

I know I should really post this to a PHP forum but you guys have been helpful in the past so I thought I'd try you guys before registering with yet another forum!!

I have this preg_match expression from codeigniter.

```

return ( ! preg_match("/^([a-z0-9])+$/i", $str)) ? FALSE : TRUE;

```

However, it does exactly what the comments say it does, allows only alpa-numeric characters. Cool, but it doesn't allow spaces!! Not so cool :(.  Any ideas how I could change this to allow spaces???



```

return ( ! preg_match("/^([a-z0-9\s])+$/i", $str)) ? FALSE : TRUE;

```

Done some digging and found out that the \s adds a check for spaces. Still not 100% on reg expressions so I think I'll read some more on it.

Thought I'd just post the solution.

---

### Post by Hellkeepa on 2010-07-11
HELLo!

"\s" is for all whitespaces: " ", "TAB", "VTAB", newlines and such.
If you want just a regular space to be added to the accepted list, then just add it to the character group. ;-)
```
[a-z0-9 ]
```

Happy codin'!

---

### Post by soltanis on 2010-07-11
Since the preg_* functions use **P**erl **reg**ular expressions you should refer to [this]("http://www.sdsc.edu/~moreland/courses/IntroPerl/docs/manual/pod/perlre.html") page from the perldocs on their syntax.

---

### Post by Hellkeepa on 2010-07-14
HELLo!

Actually, I'd rather recommend using the PHP manual for that, seeing as PHP has a couple of features that Perl doesn't have (and probably vice versa).

This should give you what you need: [http://no2.php.net/manual/en/pcre.pattern.php](http://no2.php.net/manual/en/pcre.pattern.php)

Happy codin'!

---

