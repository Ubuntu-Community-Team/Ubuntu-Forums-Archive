---
title: "How to search the table bash"
date: 2009-10-29
forum: Programming Talk
---

### Post by redelek on 2009-10-29
Hi all,
I have a little problem and I can not deal with it.
My script looks like this
```
array=("c211z091009" "c212z091029" "c213z091011" "c214z091012" "c215z091013" 
"c216z091014" "c217z091015" "c217z091016")  
NOWFILE=`date +%y%m%d` 
DATE_1_GO=`date +%y%m%d --date="1 days ago"` 
echo ${array
[*]} 
for PLIKI in ${array
[*]} 
do 
 if [ $PLIKI == "c???z${NOWFILE}" ]; then 
      echo "file found $PLIKI" 
        else 
        echo "file not found " 
fi 
done
```

The problem is that the numbers between C and Z are different and often change irregularly.
Therefore, during the search, I did not want to be taken into account. I tried on all the ways but none of that.
Is this possible and if you help me?

Best regards
Redelek

---

### Post by stroyan on 2009-10-29
You can use the bash "[[ ]]" test and the "=~" operator.

```
#!/bin/bash
array=("c211z091009" "c212z091029" "c213z091011" "c214z091012" "c215z091013"
"c216z091014" "c217z091015" "c217z091016")
NOWFILE=`date +%y%m%d`
DATE_1_GO=`date +%y%m%d --date="1 days ago"`
echo ${array[@]}
for PLIKI in "${array[@]}"
do
 if [[ $PLIKI =~ c???z${NOWFILE} ]]; then
      echo "file found $PLIKI"
        else
        echo "file not found "
fi
done
```

---

### Post by redelek on 2009-10-30
> **stroyan said:**
> You can use the bash "[[ ]]" test and the "=~" operator.



Super thank you very much for your help. Everything was moving and working. Thanks again

Best regards
Redelek

---

