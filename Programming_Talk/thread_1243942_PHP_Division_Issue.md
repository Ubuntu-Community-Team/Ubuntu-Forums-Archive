---
title: "PHP Division Issue"
date: 2009-08-18
forum: Programming Talk
---

### Post by JohnSearle on 2009-08-18
Hey all,

I'm trying to solve the third Euler problem using PHP, but I'm having issues with PHP not returning the correct results upon division.

The number I'm trying to divide is 600851475143...

600851475143 / 2 = 300425737571.5

but PHP returns 300425737572

I realize that PHP has difficulty with numbers that are 40bits long, but I was hoping there was some solution to get around this. Any thoughts (besides switching languages)?

Thanks,

- John

---

### Post by Mirge on 2009-08-19
> **JohnSearle said:**
> Hey all,

I'm trying to solve the third Euler problem using PHP, but I'm having issues with PHP not returning the correct results upon division.

The number I'm trying to divide is 600851475143...

600851475143 / 2 = 300425737571.5

but PHP returns 300425737572

I realize that PHP has difficulty with numbers that are 40bits long, but I was hoping there was some solution to get around this. Any thoughts (besides switching languages)?

Thanks,

- John

```

<?php

$number = 600851475143;
$divided = number_format($number/2, 2, '.', '');

print "divided: $divided\n";

?>


```

---

