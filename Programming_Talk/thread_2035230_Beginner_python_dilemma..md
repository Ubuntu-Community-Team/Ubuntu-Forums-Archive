---
title: "Beginner python dilemma."
date: 2012-07-30
forum: Programming Talk
---

### Post by fxStar on 2012-07-30
Hy there guys, i'm learning python right now and i need some help.

How do i code this in python ?

[PHP]<?php

$dict = array(       //first array
    'product_1'=>'butter',
    'product_2'=>'pasta',
    'product_3'=> array('product_4'=>'PIZZA',  //second one
					    'product_6'=> array(    // third one
						                   
						                     'product_7'=>'CHEESE'
						
						               )
						
				
					   
					   )

);


var_dump($dict);

?>[/PHP]

Using dictionaries ? But how ?

Thx in advance and sorry for my bad english.

---

### Post by spjackson on 2012-07-30
Maybe this?
```

#!/usr/bin/env python

dict = {
    'product_1': 'butter',
    'product_2': 'pasta',
    'product_3':  {'product_4': 'PIZZA',
                        'product_6': {'product_7': 'CHEESE'}}}

print(dict)
print dict['product_2']
print dict['product_3']['product_6']['product_7']

```

---

### Post by juancarlospaco on 2012-07-30
^ spjackson do a perfect solution  :)

---

### Post by fxStar on 2012-07-31
In the end i managed to sort this out by myself, thank you again and problem solved.:)

---

