---
title: "chmod calculator script"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by hookitup on 2012-10-23
so just spit ballin here,

i was wondering if anybody knew how to make a chmod calculator script.

basically go to this website [http://mistupid.com/internet/chmod.htm](http://mistupid.com/internet/chmod.htm)
i would like something like this that i can use in a terminal tho. so like i run the scrip and it ask for owner what values , for group what value and for other what value.

and it sums it up and give me the proper number to place when chmoding a file or directory.

or something like that, i recall seeing this somewhere but i dont remember, does anybody know how to make this or know where to find this?

---

### Post by spjackson on 2012-10-23
Why not use symbols instead of numeric values?
```

chmod u=rwx,g=rx,o=rx myfile.sh

```
And if you want the numeric value (e.g. for use in a program), then the -v flag will tell you what it is.
```

chmod -v u=rwx,g=rx,o=rx myfile.sh
mode of 'file.sh' changed to 0755 (rwxr-xr-x)

```

---

### Post by hookitup on 2012-10-23
this is just for learning purposes. so this it useful but not exactly what i want.

---

### Post by drmrgd on 2012-10-24
I suppose you could make a python or perl script that would this in a dictionary (python) or hash table (perl).  Then based on user input, the table would be queried and would spit out the result.   I'll bet it's not too hard to script that out if you have any perl / python / whatever knowledge and some free time.

---

### Post by Vaphell on 2012-10-24
but seriously, what do you need calc for exactly? it's an elementary school level math. It's about combinations of 4 (read), 2 (write), 1 (execute) - add the numbers and you get what you need
rx? 4+1
rw? 4+2
rwx? 4+2+1

---

### Post by hookitup on 2012-10-24
vaphell as i have mentioned before, this is for learning purposes. i dont need your input if your are unwilling to help.

---

### Post by Vaphell on 2012-10-24
```
#!/bin/bash

(( $#==3 )) || echo "Shouldn't there be 3 parameters?"
for p
do
  n=0
  [[ $p =~ .*r.* ]] && (( n+=4 ))
  [[ $p =~ .*w.* ]] && (( n+=2 ))
  [[ $p =~ .*x.* ]] && (( n+=1 ))
  printf $n
done
echo
```
```
$ ./perm.sh [COLOR="Red"]rrr[/COLOR] [COLOR="DarkGreen"]rwx[/COLOR] [COLOR="Blue"]rrxxxx[/COLOR] [COLOR="Indigo"]''[/COLOR] [COLOR="SlateGray"]xw[/COLOR]
Shouldn't there be 3 parameters?
[COLOR="Red"]4[/COLOR][COLOR="DarkGreen"]7[/COLOR][COLOR="Blue"]5[/COLOR][COLOR="Indigo"]0[/COLOR][COLOR="SlateGray"]3[/COLOR]
```
ignores duplicate chars and doesn't care about the order nor the number of parameters.

now that i've made my valuable contribution, where in the process of a thoughtless copy-pasting is that learning you speak of? If you had to count, you'd actually learn something.

---

### Post by hookitup on 2012-11-05
vapell thanks for your input, would there be a way to modify this so that u run the script and it says owner vaule? then you enter it, group value? then you enter it, other value? then you enter it and it calculates it and outputs the answer?
 
and FYI i am not trying to teach a math class.

---

