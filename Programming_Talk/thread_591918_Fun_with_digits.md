---
title: "Fun with digits"
date: 2007-10-25
forum: Programming Talk
---

### Post by nickoli on 2007-10-25
I wrote this script to test for positive single and more than single plus negative digits. I was just curious if this is a decent script or if i could make it more efficient. Any help in this matter will be appreciated.

# this program will display if the variables are single , more than single 
# more than one , or negative digits.
digit1=$1
digit2=$2
digit3=$3
sum=`expr $digit1 + $digit2 + $digit3`

# This first test will check for more than one digit.

if [ $sum -ge 10 ]
then
   echo more than one digit
fi

#this second test will check for a positive single digit.

if [ $sum -lt 10 -a $sum -gt 0 ]
then 
   echo one digit
fi
 
# This third test will check for negative digits
if [ $sum -lt 0 ]
then
   echo negative number
fi


---

### Post by nanotube on 2007-10-26
just notice that you are not handling the case of sum=0

---

### Post by ghostdog74 on 2007-10-26
just a small example...
```

Sum="10"
echo "$Sum" |awk '$0<0{print "negative"}
                  $0>0{print "positive"}'

```

---

### Post by dwhitney67 on 2007-10-26
Your conditionals are exclusive of each other, thus I would recommend using the if-elif-fi construct.

```
if [ conditional ]
then
   ...
elif [ conditional ]
then
   ...
fi
```

---

### Post by moma on 2007-10-26
I have some old notes about "math on the [CLI]("http://en.wikipedia.org/wiki/Command_line_interface")"
See: [http://www.futuredesktop.net/RedHat9-apt-get.html#math_on_cli](http://www.futuredesktop.net/RedHat9-apt-get.html#math_on_cli)

---

### Post by nickoli on 2007-10-26
Thanks for your help I appreciate the time you spent responding to my post. This assignment doesn't call for an instance of sum=0. I believe your right I should consider that in my script. The following modification doesn't account for that fact. It works. I'm still open to criticism . Once again thanks for your time.

sum=`expr $1 + $2 + $3`
if [ $sum -gt 9 ]
then echo sum is more than one digit
elif [ $sum -lt 10 -a $sum -gt 0 ]
then echo sum is a single digit 
else echo negative number
fi

---

