---
title: "IP counter"
date: 2010-12-06
forum: Programming Talk
---

### Post by conradin on 2010-12-06
Hi all, 
I want to create a bash which itterates through ip range  type numbers.
with a given range given before the script executes.

what i have currently will go through an annoying reading for the range of IPs to iterate through. I'm not really sure where to go from here, can some one please help?

```


#!/bin/bash
echo "Amasq lower limit:  " 
read amasq
echo "Amasq upperlimit:  " 
read uamasq

echo "Bmasq lower limit:  " 
read bmasq
echo "Bmasq upperlimit:  " 
read ubmasq

echo "Cmasq lower limit: " 
read cmasq
echo "Cmasq upperlimit:  " 
read ucmasq

echo "Dmasq lower limit:  " 
read dmasq
echo "Dmasq upperlimit: " 
read udmasq

echo " "
echo "Count Ips from: "
echo $amasq.$bmasq.$cmasq.$dmasq
echo "to"
echo echo $uamasq.$ubmasq.$ucmasq.$udmasq

sleep 10

for w in `seq $amasq $uamasq`;
do
	for x in `seq $bmasq $ubmasq`;
	do
		for y in `seq $cmasq $ucmasq`;
		do
	        	for z in `seq $dmasq $udmasq`;
	        	do

	                nc echo " -v -z -w2 $w.$x.$y.$z  9100"
			#nc doesnt like this input
 			done  
        	done 
	done
done
read



```

---

### Post by bredsaal on 2010-12-22
Hi. You don't need to use the echo command to give parameters to nc.

Try this instead:

```
nc -v -z -w2 $w.$x.$y.$z 9100
```

:-)

---

