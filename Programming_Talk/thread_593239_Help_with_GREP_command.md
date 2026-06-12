---
title: "Help with GREP command"
date: 2007-10-27
forum: Programming Talk
---

### Post by Gumper on 2007-10-27
I need help trying to figure out how to get the temperature of my Cpu to use in Superkaramba. I tried to use the 'GREP' command but it doesn't return any information. What i need to grab is below.

```
Remote Temp:
          +24.00°C  (low  =  -127°C, high =   +80°C)
```

I need the "24.00°C". Is there a way to get this information by using the GREP command? 

Here's what I've been trying and the results:

```
gumper@gumper-desktop:~$ sensors | grep 'Remote Temp'
Remote Temp:

```


Thanks for any help.

Gumper

---

### Post by ghostdog74 on 2007-10-27
use awk. assuming file contains the strings you want to search
```

# awk '/Remote Temp:/{getline;print $1 }' "file"
+24.00°C


```

in perl if desired
```

while (<>) {
    if (/Remote Temp:/) {
		if ( ($line = <>) ne ''	) {
			($f1) = split(' ', $line);
		 }
        print $f1;
    }
}

```

---

### Post by eph1973 on 2007-10-27
You could use this perl script which would give you the desired result.  Save the script, chmod a+x (whatever name you give it), etc.  Then whenever you run the script just the desired temperature would pop up.

```

#!/usr/bin/perl -w

use strict;

my @sensors = `sensors`;
my $is_temp;
for(@sensors){
  if(/Remote Temp:/){
    $is_temp = 1;
    next;
  }
  if($is_temp){
    /^\s*(.*C).*low.*/;
    print "$1\n";
    last;
  }
}

```

---

### Post by Gumper on 2007-10-27
Thanks guys!

---

