---
title: "bash, awk qn, variables and local variables"
date: 2008-08-09
forum: Programming Talk
---

### Post by Ristar on 2008-08-09
i have 2 questions.

1) how do u take the output from awk and process it line by line?
2) how do u take the output from awk (and other programs) and store the value into a variable?

1)
assuming the file "test" 

> 
Andy,Manager,4000
Bryan,Programmer,3000
Charlie,Clerk,2000
Danny,Clerk,1500


using AWK, 

awk '/Clerk/{FS=","; print $1}' 'test'

i got it to list out the name of the clerks. but, how do i get bash to process the inputs, that are echoed, line by line. for example...

```

if $? = "Charlie"
then
    echo don\'t lend him money
elif $? = "Danny"
then
    echo he\'s reliable
else
    echo i dunno him\!
fi

```


2)
```

pay=0
awk '/Clerk/ {FS=","; pay=pay+$3;} END{print pay}' 'test'

```

but i need the value of pay in a variable; accessing $pay gives 0.

the real question is, how do i put all the outputs of these programs (awk, cut, grep, etc etc) into a  variable or another function?


btw, why does awk not add in the first value for Clerk? the result of pay is 1500, instead of 3500.

---

### Post by ghostdog74 on 2008-08-09
```

pay=0
result=$(awk '/Clerk/ {FS=","; pay=pay+$3;} END{print pay}' 'test')

```

however, since awk is a programming language by itself, you can do everything in awk
```

awk -F"," '$2 ~ /Clerks/ { 
  if ( $1 == "Charlie" ) {
    print "blah"
  } else  if ( $1=="Danny" ) {
    print "blah "    
  }
}
' file

```

---

### Post by Ristar on 2008-08-09
> **ghostdog74 said:**
> ```

pay=0
result=$(awk '/Clerk/ {FS=","; pay=pay+$3;} END{print pay}' 'test')

```

however, since awk is a programming language by itself, you can do everything in awk
```

awk -F"," '$2 ~ /Clerks/ { 
  if ( $1 == "Charlie" ) {
    print "blah"
  } else  if ( $1=="Danny" ) {
    print "blah "    
  }
}
' file

```

yeah... but i cant do that, since i need the outputs to be used by other functions.

---

### Post by ghostdog74 on 2008-08-09
> **Ristar said:**
> yeah... but i cant do that, since i need the outputs to be used by other functions.

then use ```
result=$(awk '/Clerk/ {FS=","; pay=pay+$3;} END{print pay}' 'test')
```

---

### Post by Ristar on 2008-08-09
thanks ghostdog74

however...

awk '/Clerk/{FS=","; pay=pay+$3;} END{print pay}' 'test'

returns 1500 instead of 3500

did i do something wrong? i tried putting in more entries, and it seems that the first one is always ignored.

---

### Post by ghostdog74 on 2008-08-09
> **Ristar said:**
> thanks ghostdog74

however...

awk '/Clerk/{FS=","; pay=pay+$3;} END{print pay}' 'test'

returns 1500 instead of 3500

did i do something wrong? i tried putting in more entries, and it seems that the first one is always ignored.
there are 2 ways to specify field separators

1) using -F . eg
```

awk -F "," '/Clerk/{ pay=pay+$3;} END{print pay}' file

```
2) using FS in the BEGIN portion
```

awk 'BEGIN{FS=","}/Clerk/{ pay=pay+$3;} END{print pay}' file

```

by putting FS inside the "action" portion, you are telling awk  the set the FS to comma AFTER it found the first "Clerk". This will skip the first "Clerk".

---

### Post by Ristar on 2008-08-09
thanks a million, ghostdog~!

---

### Post by Ristar on 2008-08-09
oh, yeah... still have more qns about awk...
```

result=$(awk 'BEGIN{FS=","}/Clerk/{print Name: $1; print Position: $2; print Salary: $3;} END{print pay}' file)

echo $result

```

it would give...

> Name: Charlie Position: Clerk Salary: 2000 Name: Danny Position: Clerk Salary: 1500

how do i make lines... so that it becomes

> Name: Charlie 
Position: Clerk 
Salary: 2000 

Name: Danny 
Position: Clerk 
Salary: 1500


in addition, how do i force awk to search only from $2?

---

### Post by ghostdog74 on 2008-08-09
if that's your FINAL output, just this will do
```

awk 'BEGIN{FS=","}/Clerk/{printf "Name: %s\nPosition: %s\nSalary: %s\n\n",$1,$2,$3} END{print pay}' file

```

---

