---
title: "Find and replace a field containing '' to NULL using awk or sed"
date: 2010-05-13
forum: Programming Talk
---

### Post by gumal901 on 2010-05-13
Hi 

I'm relatively new at using AWK/SED. I'm trying to replace '' with NULL without changing any other values in that 59th field ($59) 

example
... 0, '1800' , '2200', 194.56657
**... 0 , '' , '' , 0 , 195.538462 **
... 0, '0900' , '1300', 194.56657
change it to

... 0, '1800' , '2200', 194.56657
**... 0 , NULL , '' , 0 , 195.538462 **
 ... 0, '0900' , '1300', 194.56657


Cheers 		   		  		  		  		  		  		 			 			 				[IMG]http://opensuse.unix.com/images/misc/progress.gif[/IMG] 				[[IMG]http://linux.unix.com/images/buttons/edit.gif[/IMG]]("http://www.unix.com/editpost.php?do=editpost&p=302421132")

---

### Post by Portmanteaufu on 2010-05-13
```

cat yourfile.txt | sed "s/''/NULL/g" > newfile.txt

```

That will replace all '' instances with NULL. Or do you *only* want to change the 59th field? (i.e. Do you want the 43rd field to stay as '' instead of NULL?)

---

### Post by DaithiF on 2010-05-13
assuming its just the 59th field you want to change, then awk is a better bet.

single quotes make it a bit tricky from the command line, as they get interpreted as part of the awk command rather than something to search for ... there may be some way of escaping them, but nothing obvious worked for me.

So, putting the awk commands in a file, you could do something like this:
```
awk -F, -f replace.awk OFS=, somefile

```where replace.awk contains:
```
{ 
sub(/''/, "NULL", $59);
print;
}
```

a convoluted way to do it from the command line without the need for a file of awk commands would be:
```
awk -F, 'BEGIN { x = sprintf("%c%c", 39, 39) } sub(x, "NULL", $59); print;
}' OFS=, somefile
```

there must be a neater way than this, probably ghostdog74 would know, if he sees this thread.

---

### Post by gumal901 on 2010-05-14
Thanks Portmanteaufu and DaithiF and it was specificly for column $59 and it did work great(the convoluted version I used). Thanks again Al

---

