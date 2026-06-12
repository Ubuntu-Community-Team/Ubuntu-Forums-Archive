---
title: "Checking which output produces bigger number"
date: 2010-08-03
forum: Programming Talk
---

### Post by Intrepid Ibex on 2010-08-03
Ahgs, such a long title..

Soo, I'm trying to (long story short) find which of my two outputs produces a bigger number, k? OK.

Say something like this with the addition that it'd work:
```
no1=`cat file | grep 2`
no2=`cat file | grep 1`
if [ "$no1" =bigger= "$no2" ]; then
    echo Result 1 produces bigger number
else
    echo Result 2 produces bigger number
fi # No chance for these two to be equal.
```

---

### Post by alphaniner on 2010-08-03
> **Intrepid Ibex said:**
> Ahgs, such a long title..

Soo, I'm trying to (long story short) find which of my two outputs produces a bigger number, k? OK.

Say something like this with the addition that it'd work:
```
no1=`cat file | grep 2`
no2=`cat file | grep 1`
if [ "$no1" =bigger= "$no2" ]; then
    echo Result 1 produces bigger number
else
    echo Result 2 produces bigger number
fi # No chance for these two to be equal.
```

Assuming I'm understanding correctly:

If I was sure they couldn't be equal, I would do
```
if [ "$no1" -gt "$no2" ]
then
    echo "Result 1 produces bigger number"
else
    echo "Result 2 produces bigger number"
fi
```

Though more likely I'd do
```
if [ "$no1" -gt "$no2" ]
then
     echo "Result 1 produces bigger number"

elif [ "$no2" -gt "$no1" ]
then
     echo "Result 2 produces bigger number"

elif [ "$no2" -eq "$no1" ]
then
     echo "Results are equal"

else
     echo "Something strange happened!"
fi
```

Check out the [bash conditionals]("http://www.faqs.org/docs/bashman/bashref_68.html").

---

### Post by Intrepid Ibex on 2010-08-03
They aren't, trust me on this :). Thanks.

---

