---
title: "bash script arithmetic"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by magicmt on 2008-10-16
the below script works with whole numbers, but not decimals. how do i get it to work with decimals?

#!/bin/bash
echo -n "enter a number "
read num
echo $[$num*3600-3]

---

### Post by akira86 on 2008-10-16
man bc
;-)

---

