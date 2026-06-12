---
title: "Processig a csv file line by line in bash"
date: 2009-09-18
forum: Programming Talk
---

### Post by dunryc on 2009-09-18
Hi hoping someone can help I'm trying to process a CSV file line by line in bash the format of which is below :-

> "Mr" "john" "smith" "457" "ripple road" ,"sometown","somecounty","sk11qw","2085853618",,"7000000722",,,


What I want to be able to accomplish is grabbing the same "columns" from the csv file into variables. I believe i can read the csv file line by line using the code blow 

> 
cat myfile.csv | while read line; do
    
#here is where i need to get the fist name and mobile number into to variables 

done 

So if any one has any answers that would help me i would be extremely grateful 

thanks in advance Dunryc

---

### Post by dwhitney67 on 2009-09-18
Would this work?
```

#!/bin/bash

cat myfile.csv | while read line
do
        echo $line | cut -d'"' -f4     # get the first name
        echo $line | cut -d'"' -f18    # get the telephone number
done

```

P.S.  This also may assist you:
```

#!/bin/bash

declare -i index
index=1

cat myfile.csv | while read line
do
        while [ $index != 24 ]
        do
                echo -n "$index: "
                echo $line | cut -d'"' -f$index
                index=$index+1
        done
done

```

---

### Post by ghostdog74 on 2009-09-18
> **dunryc said:**
> Hi hoping someone can help I'm trying to process a CSV file line by line in bash the format of which is below :-




What I want to be able to accomplish is grabbing the same "columns" from the csv file into variables. I believe i can read the csv file line by line using the code blow 

 

So if any one has any answers that would help me i would be extremely grateful 

thanks in advance Dunryc

assume column 5 is telephone number
```

awk -F"," '
{
    column1 = $1
    tel = $5
    split(column1,a," ")
    print "first name: " a[1],a[2]
    print "telephone: " tel
}' file

```
output
```

# more file
"Mr" "john" "smith" "457" "ripple road" ,"sometown","somecounty","sk11qw","2085853618",,"7 000000722"

# ./shell.sh
first name: "Mr" "john"
telephone: "2085853618"



```

---

### Post by ghostdog74 on 2009-09-18
> **dwhitney67 said:**
> Would this work?
```

#!/bin/bash

cat myfile.csv | while read line
do
        echo $line | cut -d'"' -f4     # get the first name
        echo $line | cut -d'"' -f18    # get the telephone number
done

```


few points
1) no need to use cat.
2) you are using cut 2 times for each line --> inefficient
3) "cut" is programmed to take in a file as argument, at the same time, internally its doing line by line processing of the file. therefore, the above can be shortened
```

cut -d'"' -f4,18 --output-delimiter=" " file

```

---

### Post by hal10000 on 2009-09-18
I suppose the field separator between the particular fields is a comma, then this also may work for you
```

OIFS=$IFS
IFS=,    #notice: this is your field separator
while read var1 var2 var3 var........
# in the upper line as much variables as you need
# if th read command contains less variables than your csv-file contains fields,
# then the last declared variable contains the whole rest of the line

do
echo $var1, $var4, $var6

# note: the upper line is just an example to print out the fist, fourth and sixth field

done <myfile.csv
IFS=$OIFS

```

---

### Post by ghostdog74 on 2009-09-18
> **hal10000 said:**
> I suppose the field separator between the particular fields is a comma, then this also may work for you
```

OIFS=$IFS
IFS=,    #notice: this is your field separator
while read var1 var2 var3 var........
# in the upper line as much variables as you need
# if th read command contains less variables than your csv-file contains fields,
# then the last declared variable contains the whole rest of the line

do
echo $var1, $var4, $var6

# note: the upper line is just an example to print out the fist, fourth and sixth field

done <myfile.csv
IFS=$OIFS

```

you can put your IFS inside the while loop
```

while IFS="," read var1 var2 var3 var4 var5 var6
do
    echo $var5
done < file


```

---

### Post by dunryc on 2009-09-18
@ hal10000

that works great and gives me the output i need but is there any way i can work through the file line by line rather than all at one time as i want to run a command with the output ie :-

> echo "Hello $var2 how are you today hope things are " | gnokii --sendsms 0$var12

Thanks every one for the heads up its been a real help 

Regards Dunryc

---

### Post by dunryc on 2009-09-20
Thanks for all the suggestions guys got my script working great in the end

---

