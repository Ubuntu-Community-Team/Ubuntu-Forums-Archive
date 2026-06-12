---
title: "get content of one file and setup in other quoted file"
date: 2009-04-17
forum: Programming Talk
---

### Post by aliahsan81 on 2009-04-17
Hi All

I want to make a script that will do the following.
I have a file A contain

```

/var/www/html/test
/var/www/xyz/abc
and so on


```

now i want that script should pick first line then second and so on.After picking line one by one add them in an other file some thing like this



```

<directory "/var/www/html/test">

other directive


</Directory>





```

And do this procedure same for all then content in File A.How this can be done

---

### Post by Fixman on 2009-04-17
> **aliahsan81 said:**
> Hi All

I want to make a script that will do the following.
I have a file A contain

```

/var/www/html/test
/var/www/xyz/abc
and so on


```

now i want that script should pick first line then second and so on.After picking line one by one add them in an other file some thing like this



```

<directory "/var/www/html/test">

other directive


</Directory>





```

And do this procedure same for all then content in File A.How this can be done

I don't quite get what you mean, but I think it would be something like this

```

#!/bin/bash

n=0 ;
exec 3< input ;
while read <&3 ; do
	echo "<directory \"$REPLY\">" >> output
	false $[n++] ;
done ;
for ((i=0;i<n;i++)) ; do echo "</directory>" >> output ; done ;

```

---

### Post by ghostdog74 on 2009-04-17
> **aliahsan81 said:**
> How this can be done
you have previous posts asking about scripting. you should have some knowledge about various tools you can use by know to manipulate files. why don't you do your best and give it a try. then post here if you hit problems.

---

### Post by aliahsan81 on 2009-04-17
Accentually i have a script that find some directories then we add them in apache config file


find result place its out put  in a file with all the directory path.

Like this
File A
```

/var/www/html/xyz
/var/www/xt/abc




```


now i want to place each line in apache conf but in directory directive 

Apache  conf 
```

</Directory "/var/www/html/xyz">
directive


```

Currently i am doing this by hand which is time taking.So i want to be thins done automatically.Now you got what i mean.For every entry in file A i add a new directory directive in apache conf.

---

### Post by Arndt on 2009-04-18
> **aliahsan81 said:**
> Accentually i have a script that find some directories then we add them in apache config file


find result place its out put  in a file with all the directory path.

Like this
File A
```

/var/www/html/xyz
/var/www/xt/abc




```



now i want to place each line in apache conf but in directory directive 

Apache  conf 
```

</Directory "/var/www/html/xyz">
directive


```

Currently i am doing this by hand which is time taking.So i want to be thins done automatically.Now you got what i mean.For every entry in file A i add a new directory directive in apache conf.

Look at the 'sed' or 'awk' commands.

---

