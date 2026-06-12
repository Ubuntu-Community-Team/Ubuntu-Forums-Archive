---
title: "Php if variable"
date: 2009-01-17
forum: Programming Talk
---

### Post by Dr Small on 2009-01-17
Is there a name for this method?
[php]$stylesheet = (isset($_GET[style]) && !empty($_GET[style])) ? "styles/".$_GET[style] : $default_stylesheet;[/php]

I just want to understand it better, since I have never used this method, and want to learn some more. I know what it does, but I want to do some reading on it to further understand it.

---

### Post by Namtabmai on 2009-01-17
That's the ternary operator, try [here]("http://php.net/manual/en/language.operators.comparison.php").

---

### Post by Dr Small on 2009-01-17
> **Namtabmai said:**
> That's the ternary operator, try [here]("http://php.net/manual/en/language.operators.comparison.php").
Thanks. That was helpful :)

Dr Small

---

### Post by sunset_studies on 2009-01-18
> **Dr Small said:**
> Is there a name for this method?
[php]$stylesheet = (isset($_GET[style]) && !empty($_GET[style])) ? "styles/".$_GET[style] : $default_stylesheet;[/php]

I just want to understand it better, since I have never used this method, and want to learn some more. I know what it does, but I want to do some reading on it to further understand it.


fyi (since you want to understand it better :)) the isset($_GET[style]) in that code is redundant. empty() will return true for unset vars.

---

### Post by Compyx on 2009-01-18
Since nobody has mentioned this: it is a bad practice to use bare words as array keys.

Use:
[PHP]$_GET['style'][/PHP]
rather than:
[PHP]$_GET[style][/PHP]

See [http://nl.php.net/manual/en/language.types.array.php]("http://nl.php.net/manual/en/language.types.array.php"), scroll down to 'Array do's and don'ts.

---

