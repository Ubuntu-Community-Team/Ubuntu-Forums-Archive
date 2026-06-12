---
title: "deleting and reorder from a bash array"
date: 2008-01-05
forum: Programming Talk
---

### Post by DouglasAWh on 2008-01-05
I have an array in bash and the first 5 objects are the headers from a MySQL return.  How do I delete those first 5 and then reorder so that my count will be correct?  I can use unset, but what seems to happen is that the empty elements are still there.  I want to get rid of those elements completely and have the array order slide down like removing a block.  Please let me know if what I am trying to do is not clear.

Thank you!

---

### Post by geirha on 2008-01-05
Yes, unsetting doesn't shift the indices, so the easiest way of achieving this is to just create a new array
```

array=( a b c d e f g h )
echo Two first elements: ${array[0]} ${array[1]}
for i in $(seq 0 4); do
  unset array[$i]
done
echo Two first elements: ${array[0]} ${array[1]}
array=( "${array[@]}" )
echo Two first elements: ${array[0]} ${array[1]}

```

A better option might be to have mysql not print the header in the first place, with --skip-column-names ...

---

### Post by stroyan on 2008-01-06
I decided to see if I could get the "shift"  bash builtin to apply to this.
It can shift positional parameters, including parameters to functions.
This bash function actually creates a temporary function that takes a quoted array content,
shifts away a requested number of elements, and then assigns back to the original array name.
[PHP]$ function shift_array() { t=$1; c=$2; eval 'function s2(){ shift '$c'; '$t'=("$@");};s2 "${'$t'[@]}"';unset -f s2;}
$ mydata=( 1 2 3 "4 and some" 5 6 "7 and some" 8 9 )
$ shift_array mydata 5
$ set | grep mydata
mydata=([0]="6" [1]="7 and some" [2]="8" [3]="9")
t=mydata
[/PHP]

---

### Post by ghostdog74 on 2008-01-06
> **DouglasAWh said:**
> I have an array in bash and the first 5 objects are the headers from a MySQL return.  
you can just skip selecting these headers in your Mysql command.

---

### Post by DouglasAWh on 2008-01-06
> **ghostdog74 said:**
> you can just skip selecting these headers in your Mysql command.

I don't think I can the way I'm doing it, but feel free to enlighten me.

---

### Post by ghostdog74 on 2008-01-06
> **DouglasAWh said:**
> I don't think I can the way I'm doing it, but feel free to enlighten me.

you need to know how your headers look like, any distinct values in the rows of those headers you can skip. eg, if your headers have value B in column A, and all other rows have value not equal B, then you can select * from table where colA <> "B"... something like that...Just an idea, you have to do experiments yourself.

---

### Post by DouglasAWh on 2008-01-06
That's a great idea, but I ended up just using what I know about the array...that the headers are the first five.

so, 
```

if [(($i < 4))]
{whatever it was I was trying to do earlier}

```

---

### Post by stroyan on 2008-01-07
I came across the best answer to your original question about deleting the first 5 objects in an array```
array=("${array[@]:5}")
```That looks so simple, ... after finding the right part of the "parameter expansion" part of "man bash".  The notation ```
"${array[@]:offset}"
``` or ```
"${array[@]:offset:length}"
``` expands to a range of array elements with proper quoting of elements that contain whitespace characters or other special characters.

---

### Post by DouglasAWh on 2008-01-07
> **geirha said:**
> A better option might be to have mysql not print the header in the first place, with --skip-column-names ...

I missed this part of your post earlier.  Good to know!  Not used in this instance though as it's already done.

---

