---
title: "bash scripting help"
date: 2010-11-21
forum: Programming Talk
---

### Post by markp1989 on 2010-11-21
Im in the middle of writing a scrapper to get my html time table from my uni website, and then get my lessons in plain text.  so far i have got the data for the lessons that i do.

problem is that there are 2 groups doing my course 571.1 B and 571.1 A , I want to keep the lessons that 571.1 A attend and remove the group B attend ,  

Is there a way to find the lines with "571.1 B" and remove that + the 3 lines above that from the out put?

EG: ( I have put a # in the ones i would like to remove, there are multiple lessons like this, and the A or B subjects arent always in the same order.

```

Lesson1
lesson1 room number and other details
571.1 A

#lesson1 
#lesson1 room number and other details 
#571.1 B 



```







If you need more information to be able to point me in the right direction, i can paste the out put of my script so far.

Thanks for looking, Mark

---

### Post by koenn on 2010-11-21
I know grep will let you find "something + X lines before that" but deleting it is going to be harder.
You can probably do something convulkated with sed and grep, 
but it's probably better to try awk (if you really want to do this in a bash script"), or write something in perl, which was designed for this sort of thing.

Unfortunately, I know neither awk or perl.

Maybe ask in the programming formum for a short perl script you can invoke from a bash script  ?

---

### Post by DaithiF on 2010-11-21
going backwards isn't really practical with sed, so a cheat is to reverse the order of the file first ... and then reverse it back again once done.

```
tac somefile | sed '/571.1.B/,+2d' | tac > newfile

```

thats kinda kludgey, so a better bet would be to use awk ... store the contents of the file in an array line by line, whenever you match 571.1.B delete the last 3 records, and when done print the remaining elements in the array

```
awk '{ arr[NR]=$0 } /571.1.B/ { start=NR-2; for(i=start;i <=NR; i++) delete arr[i]; } END { for(i in arr) print arr[i] }' somefile > newfile
```

---

### Post by Joeb454 on 2010-11-21
*Thread moved to **Programming Talk**.*

---

### Post by koenn on 2010-11-21
I kinda like the idea of 'find forward is easier, so turn the file around'. but awk or perl are probably better for this sort of thing.

otoh, if we turn the problem around, i.e. in stead of delete what we don't need, just filter out what we want, we could simply grep :

```

grep  -B2 "571.1 A" filename

``` 
and pipe or redirect output as needed

---

### Post by papibe on 2010-11-21
Interesting problem, this is my attempt:
```
$ awf -f myprogram input_file
```
where myprogram is a file with awk code, and consist of:
```
BEGIN {
	lines[1] = "";
	lines[2] = "";
	lines[3] = "";
	i = 0;
}
!/571.1 B/ {
	if ( i < 3 ) {
		lines[ ++i ] = $0;
	} else {
		print lines[ 1 ];
		print lines[ 2 ];
		print lines[ 3 ];
		i = 1;
		lines[ i ] = $0;
	}
}
/571.1 B/ {
	i = 0;
}
END {
	j = 1;
	while ( j <= i ) {
		print lines[ j++ ];
	}
}

```

I hope it helps.

---

### Post by markp1989 on 2010-11-23
@  DaithiF: Thanks, That worked  :) 

@ koenn: That is the way i would prefer to do it, but there are some lessons where both groups attend, which they just call "571.1" which would have been left out by the other method. 

Thanks everyone for replying :)

---

