---
title: "can some one give me a few pointers on elif and bash."
date: 2009-04-01
forum: Programming Talk
---

### Post by markp1989 on 2009-04-01
i want to wite a small script that will use curl to get the rss feed from the bbc site, check the current weather conditions, then change my background using feh. 

```

#!/bin/bash -v
rm .weathertmp
curl http://feeds.bbc.co.uk/weather/feeds/rss/obs/world/0008.xml | tail -n 13 | head -n 1 |cut -f1 -d'.' >  .weathertmp 
if grep -qw  rain .weathertmp ; then 
echo Set background to rain
elif grep -qw cloud .weathertmp; then
echo set bacground to cloudy
elif grep -qw sunny; then 
echo set background to sunny
else
echo other 
fi

```

currently im just having the script echo what i want the background to be, untill i get the if statements sorted out.

it doesnt run right now, im not sure if it because i have more than one elif, or what. 

wound some one be able to point me in the right direction.

edit: just relized what i had done wrong, i hadnt finished the final grep :@

---

### Post by dwhitney67 on 2009-04-01
Or you could try:
```

#!/bin/bash

weather=(rain cloudy sunny other)


for w in ${weather[@]}
do
        grep -qw $w .weathertmp > /dev/null

        if [ $? -eq 0 ]
        then
                echo set background to $w
                break
        fi
done

```

---

