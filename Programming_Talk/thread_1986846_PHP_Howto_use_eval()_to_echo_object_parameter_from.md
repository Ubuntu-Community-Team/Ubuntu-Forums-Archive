---
title: "PHP: Howto use eval() to echo object parameter from string"
date: 2012-05-25
forum: Programming Talk
---

### Post by cdaringe on 2012-05-25
Hi all:

See below code.  What's wrong with picture?

$addStr = '[0]', in this example
$bom[0] refers to an object with a parameter called 'pn'

```

$objPN= '$bom'.$addStr.'->pn';
echo eval($objPN); //returns nothing :(
echo $bom[0]->pn; // but, this successfully returns B!

```

I want the 2nd line to output the same as the 3rd!  What's biffed in my syntax?

Thanks all!

---

### Post by roelforg on 2012-05-25
> **cdaringe said:**
> Hi all:

See below code.  What's wrong with picture?

$addStr = '[0]', in this example
$bom[0] refers to an object with a parameter called 'pn'

```

$objPN= 'echo $bom'.$addStr.'->pn;';
eval($objPN); //returns nothing :(
echo $bom[0]->pn; // but, this successfully returns B!

```I want the 2nd line to output the same as the 3rd!  What's biffed in my syntax?

Thanks all!

I modded the code in the quote to work

---

### Post by cdaringe on 2012-05-25
that did the trick huh?  Thanks!  I'll give it whirl later!  much appreciated.

---

