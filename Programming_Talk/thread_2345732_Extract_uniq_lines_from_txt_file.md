---
title: "Extract uniq lines from txt file"
date: 2016-12-07
forum: Programming Talk
---

### Post by demontager on 2016-12-07
i have a task to extract only uniq lines in such txt file

```
=====================
apple:cherry
1pcs
3pcs
=====================
orange:banana
1pc
2 pcs
6pcs
=====================
tomato:olives
1 pc
2 pcs
=====================
orange:banana
1pc
2 pcs
3pcs
6pcs
=====================
apple:onion
1 pc
2 pcs
9 pcs
=====================

```


I need to compare only first string after divider =====================  
So in this sample i should receive:

```
=====================
apple:cherry
1pcs
3pcs
=====================
orange:banana
1pc
2 pcs
6pcs
=====================
tomato:olives
1 pc
2 pcs
=====================
apple:onion
1 pc
2 pcs
9 pcs
=====================

```

I got rid block starting with same orange:banana which i have before. How the bash script will look if i need to do that in long file ?

---

### Post by Rocket2DMn on 2016-12-07
I think the simplest approach in bash is to use an array.  You would obviously need to expand on this for your additional line parsing:
```

#!/bin/bash
UNIQUE_LINES=()
while read line; do
	if [[ "${UNIQUE_LINES[@]}" =~ "$line" ]]; then
		continue
	fi
	UNIQUE_LINES+=($line)
	echo $line
done < input.txt

```
This might be easier in Python or other languages that support more advanced data constructs.

---

### Post by demontager on 2016-12-07
Thanks for reply! I tried above script and after applying to above example i got:

```


$ ./clean.sh
=====================
apple:cherry
1pcs
3pcs
orange:banana
2 pcs
6pcs
tomato:olives
1 pc
apple:onion
9 pcs
dem@dem-Y700 ~/Desktop $ 


```

output lack of divider  ===================== after each block   and data after compared string. 

p.s. Python will be fine too. I thought it could be made on bash.

---

### Post by steeldriver on 2016-12-07
How about awk (using 'paragraph mode')?

```

$ awk -v RS='\n=====================\n' -v ORS='\n=====================\n' '
     NR==1 {print;next} 
     !seen[$1]++
' file
=====================
apple:cherry
1pcs
3pcs
=====================
orange:banana
1pc
2 pcs
6pcs
=====================
tomato:olives
1 pc
2 pcs
=====================
apple:onion
1 pc
2 pcs
9 pcs
=====================

```

---

### Post by demontager on 2016-12-07
oh man, great! Works as a charm 200mb file parsed and cleaned in 1 second on Corei7 6700 HQ, amazing.
The only one problem i found during tests. If file has CRLF ending which normal for windows then cleaning not work. So i did converting to LF ending

```

sed -i 's/\r//g' input.txt

```

---

