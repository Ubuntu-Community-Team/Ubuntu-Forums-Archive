---
title: "PHP Multipling Dollar Amounts"
date: 2009-09-02
forum: Programming Talk
---

### Post by dyous87 on 2009-09-02
I am having trouble with something which I assumed should be rather easy but I cannot seem to find the answer anywhere. I have two numbers stored in variables which are supposed to represent dollar value and quantity pulled from an html form. When I try multiplying the amounts I get a whole number instead of a decimal number. For example:

```

$price = 6.99;
$amount = 2;
$totalPrice = $price * $amount;
echo $totalPrice;

```

When I run this code the output is "12" instead of "13.98". What am I doing wrong. Any help would surely be greatly appreciated. 

Best Regards,
David

---

### Post by Finalfantasykid on 2009-09-02
I might be wrong but it is possible that it is rounding because you used 2 instead of 2.0 or 2.00.

try this instead...

```
$price = 6.99;
$amount = 2.00;
$totalPrice = $price * $amount;
echo $totalPrice;
```

---

### Post by dyous87 on 2009-09-02
Hmm I just tried that also but I get the same results...I don't understand what's going on.

---

### Post by rp3 on 2009-09-02
> **dyous87 said:**
> Hmm I just tried that also but I get the same results...I don't understand what's going on.

maybe something like this will work

$formatted = number_format($number,2);

---

### Post by dyous87 on 2009-09-02
Thanks rp3! I used the number_formated() function and it worked. This is what I had to do:

```

$price = 6.99;
$amount = 2;
$formatedPrice = number_format($price, 2, '.', '');
$formatedAmount = number_format($amount, 2, '.', '');
$totalPrice = $formatedPrice * $formatedAmount;
echo $totalPrice; 

```

Thanks a lot for all your help!

David

---

### Post by rp3 on 2009-09-02
> **dyous87 said:**
> Thanks rp3! I used the number_formated() function and it worked. This is what I had to do:

```

$price = 6.99;
$amount = 2;
$formatedPrice = number_format($price, 2, '.', '');
$formatedAmount = number_format($amount, 2, '.', '');
$totalPrice = $formatedPrice * $formatedAmount;
echo $totalPrice; 

```

Thanks a lot for all your help!

David


Your welcome

---

### Post by Reiger on 2009-09-02
That is just plain weird. I don't recall ever having trouble like that with PHP, and just to check I ran PHP in interactive mode from the command line (php -a):
```

php > echo (6.99 *2);
13.98
php > $a = 6.99; $b = 2; echo $a *$b;
13.98

```

---

### Post by Lux Perpetua on 2009-09-03
> **dyous87 said:**
> I am having trouble with something which I assumed should be rather easy but I cannot seem to find the answer anywhere. I have two numbers stored in variables which are supposed to represent dollar value and quantity pulled from an html form. When I try multiplying the amounts I get a whole number instead of a decimal number. For example:

```

$price = 6.99;
$amount = 2;
$totalPrice = $price * $amount;
echo $totalPrice;

```

When I run this code the output is "12" instead of "13.98". What am I doing wrong. Any help would surely be greatly appreciated. 

Best Regards,
David

FWIW, I just ran your code verbatim: [php]<?php
$price = 6.99;
$amount = 2;
$totalPrice = $price * $amount;
echo $totalPrice;
?>
[/php]Result:> 13.98
Output of php -v:> PHP 5.2.10 with Suhosin-Patch 0.9.7 (cli) (built: Jul 14 2009 11:56:54) 
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2009 Zend Technologies


---

