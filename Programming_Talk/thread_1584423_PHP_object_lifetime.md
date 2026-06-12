---
title: "PHP object lifetime"
date: 2010-09-29
forum: Programming Talk
---

### Post by Wtower on 2010-09-29
Let assume:

```

class b {
    public $varb;
    function __construct() {
        $varb = 'something';
    }
}
class a {
    public $vara;
    function __construct() {
        $vara = new b();
    }
}
$obj = new a();
echo($a->$vara->$varb); // Fatal error: cannot access empty property

```

Obviously, the lifetime of object $vara of class b ends at the end of constructor of a. I can understand why, but coming from a cpp background I find this inconvenient. 

Do I miss something? Is there some operator instead of new, that determines the lifetime? What object oriented alternative approach would you recommend.

Thanks for the help.

Regards

---

### Post by Wtower on 2010-09-29
Ah, my mistake. Classic syntax bug. Line 4 should be like:
```
$this->varb = 'something';
```
And last line:
```
$echo($obj->vara->varb);
```

---

