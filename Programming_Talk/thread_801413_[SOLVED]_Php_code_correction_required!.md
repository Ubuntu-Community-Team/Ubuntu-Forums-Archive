---
title: "[SOLVED] Php code correction required!"
date: 2008-05-20
forum: Programming Talk
---

### Post by Rytron on 2008-05-20
Hi,

For this 
```
<?php
$num1 = 29+21;
$num2 = 70;
echo $num1+num2;
?>
```
I get output 

**50**

but I should get 

**120 **

as output. Does anyone know what is wrong?

Thanks.

---

### Post by deuce868 on 2008-05-20
> **Rytron said:**
> Hi,

For this 
code
```
<?php
$num1 = 29+21;
$num2 = 70;
echo $num1+num2;
?>
```
I get output 

**50**

but I should get 

**120 **

as output. Does anyone know what is wrong?

Thanks.

missing a $ on num2 there.

---

