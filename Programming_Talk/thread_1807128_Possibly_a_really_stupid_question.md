---
title: "Possibly a really stupid question"
date: 2011-07-18
forum: Programming Talk
---

### Post by CarlosBril on 2011-07-18
Dear Ubuntu Community,

I'm a rookie programmer trying to run a simple script I made, but everytime I run it, it gives me the following error:

```
./home/cabal/daemons/floating_rates_daemon.sh: line 187: syntax error near unexpected token `('
./home/cabal/daemons/floating_rates_daemon.sh: line 187: `let o1=(((((((($n1-$base_rate))/(($max_rate-$base_rate))))*(($max_rate2-$base_rate2))))+$base_rate2))'
```

This is the actual file, with line 187 bolded:

[spoiler]```
#!/bin/sh

logfile=/var/log/cabal/floating_rates.log

#Put 0 here to disable, or leave 1 to enable complete logging. Might use alot of disk space over time.
use_log=1
#Server 1:

# Minimum rate 1 = 1x
base_rate=80
# Maximum rate 5 = 5x
max_rate=120

#Minimal other rates:
#Skill Exp
s1=50
#Craft Exp
s2=50
#Droprate
s3=1
#Alzrate
s4=8
#Alzbombrate
s5=6

#Maximal other rates:
#Skill Exp
s6=100
#Craft Exp
s7=100
#Droprate
s8=1
#Alzrate
s9=12
#Alzbombrate
s10=8

# Items per drop
dropcount=2

#Server 2:

# Minimum rate 1 = 1x
base_rate2=300
# Maximum rate 5 = 5x
max_rate2=350

#Minimal other rates:
#Skill Exp
s11=125
#Craft Exp
s12=125
#Droprate
s13=1
#Alzrate
s14=18
#Alzbombrate
s15=12

#Maximal other rates:
#Skill Exp
s16=175
#Craft Exp
s17=175
#Droprate
s18=1
#Alzrate
s19=26
#Alzbombrate
s20=18

# Items per drop
dropcount2=2

#So far the Rates Config, please DO check the dirs the Const.cfg go into.

n1=1
if [ $base_rate -eq $max_rate ]; then
let n1=$base_rate
else
while [ $n1 -le $base_rate ]; do
  n1=$RANDOM
  let "n1 %= $max_rate"
done
fi

n2=1
if [ $s1 -eq $s6 ]; then
let n2=$s6
else
while [ $n2 -le $s1 ]; do
  n2=$RANDOM
  let "n2 %= $s6"
done
fi

n3=1
if [ $s2 -eq $s7 ]; then
let n3=$s7
else
while [ $n3 -le $s2 ]; do
  n3=$RANDOM
  let "n3 %= $s7"
done
fi

n4=1
if [ $s3 -eq $s8 ]; then
let n4=$s8
else
while [ $n4 -le $s3 ]; do
  n4=$RANDOM
  let "n4 %= $s8"
done
fi

n5=1
if [ $s4 -eq $s9 ]; then
let n5=$s9
else
while [ $n5 -le $s4 ]; do
  n5=$RANDOM
  let "n5 %= $s9"
done
fi

n6=1
if [ $s5 -eq $s10 ]; then
let n6=$s10
else
while [ $n6 -le $s5 ]; do
  n6=$RANDOM
  let "n6 %= $s10"
done
fi

let new_exp=$n1*100
newtype11="EXP"
let new_skillexp=$n2*100
newtype12="Skill EXP"
let new_craftexp=$n3*100
newtype13="Craft EXP"
let new_droprate=$n4*100
newtype14="Droprate"
let new_alzrate=$n5*100
newtype15="Alz Rate"
let new_alzbrate=$n6*100
newtype16="Alz Bomb Rate"

 
sed /etc/cabal/templates/Const.cfg \
-e "s/u00/$new_exp/g" \
-e "s/v00/$new_skillexp/g" \
-e "s/w00/$new_craftexp/g" \
-e "s/x00/$new_droprate/g" \
-e "s/y00/$new_alzbrate/g" \
-e "s/z00/$new_alzrate/g" \
-e "s/abcd/$dropcount/g" \
> /etc/cabal/Data/Const.scp
chmod 0777 /etc/cabal/Data/Const.scp


if [ $use_log -eq 1 ]; then
echo "`date`: Selected $n1 x as rate for $newtype11 on Server 1" | tee -a $logfile
echo "`date`: Selected $n2 x as rate for $newtype12 on Server 1" | tee -a $logfile
echo "`date`: Selected $n3 x as rate for $newtype13 on Server 1" | tee -a $logfile
echo "`date`: Selected $n4 x as rate for $newtype14 on Server 1" | tee -a $logfile
echo "`date`: Selected $n5 x as rate for $newtype15 on Server 1" | tee -a $logfile
echo "`date`: Selected $n6 x as rate for $newtype16 on Server 1" | tee -a $logfile
elif [ $use_log -eq 0 ]; then
echo "`date`: New rates, Logs are turned off" | tee -a $logfile
fi

#Server 2 is in /etc/cabal/Data2/Const.scp

if [ $base_rate -eq $max_rate ] && [ $base_rate2 -ne $max_rate2 ]; then
o1=1
while [ $o1 -le $base_rate2 ]; do
  o1=$RANDOM
  let "o1 %= $max_rate2"
done
elif [ $base_rate -ne $max_rate ] && [ $base_rate2 -eq $max_rate2 ]; then
let o1=$s16
elif [ $base_rate -eq $max_rate ] && [ $base_rate2 -eq $max_rate2 ]; then
let o1=$s16
else
**let o1=(((((((($n1-$base_rate))/(($max_rate-$base_rate))))*(($max_rate2-$base_rate2))))+$base_rate2))**
fi

if [ $s1 -eq $s6 ] && [ $s11 -ne $s16 ]; then
o2=1
while [ $o2 -le $s11 ]; do
  o2=$RANDOM
  let "o2 %= $s16"
done
elif [ $s1 -ne $s6 ] && [ $s11 -eq $s16 ]; then
let o2=$s16
elif [ $s1 -eq $s6 ] && [ $s11 -eq $s16 ]; then
let o2=$s16
else
let o2=(((((($n2-$s1))/(($s6-$s1))))*(($s16-$s11))))+$s11
fi

if [ $s2 -eq $s7 ] && [ $s12  -ne $s17 ]; then
o3=1
while [ $o3 -le $s12 ]; do
  o3=$RANDOM
  let "o3 %= $s17"
done
elif [ $s2 -ne $s7 ] && [ $s12 -eq $s17 ]; then
let o3=$s17
elif [ $s2 -eq $s7 ] && [ $s12 -eq $s17 ]; then
let o3=$s17
else
let o3=(((((($n3-$s2))/(($s7-$s2))))*(($s17-$s12))))+$s12
fi

if [ $s3 -eq $s8 ] && [ $s13 -ne $s18 ]; then
o4=1
while [ $o4 -le $s13 ]; do
  o4=$RANDOM
  let "o4 %= $s18"
done
elif [ $s3 -ne $s8 ] && [ $s13 -eq $s18 ]; then
let o4=$s18
elif [ $s3 -eq $s8 ] && [ $s13 -eq $s18 ]; then
let o4=$s18
else
let o4=(((((($n4-$s3))/(($s8-$s3))))*(($s18-$s13))))+$s13
fi

if [ $s4 -eq $s9 ] && [ $s14 -ne $s19 ]; then
o5=1
while [ $o5 -le $s14 ]; do
  o5=$RANDOM
  let "o5 %= $s19"
done
elif [ $s4 -ne $s9 ] && [ $s14 -eq $s19 ]; then
let o5=$s19
elif [ $s4 -eq $s9 ] && [ $s14 -eq $s19 ]; then
let o5=$s19
else
let o5=(((((($n5-$s4))/(($s9-$s4))))*(($s19-$s14))))+$s14
fi

if [ $s5 -eq $s10 ] && [ $s15 -ne $s20 ]; then
o6=1
while [ $o6 -le $s15 ]; do
  o6=$RANDOM
  let "o6 %= $s20"
done
elif [ $s5 -ne $s10 ] && [ $s15 -eq $s20 ]; then
let o6=$s20
elif [ $s5 -eq $s10 ] && [ $s15 -eq $s20 ]; then
let o6=$s20
else
let o6=(((((($n6-$s5))/(($s10-$s5))))*(($s20-$s15))))+$s15
fi

new_exp2=$o1*100
newtype21="EXP"
new_skillexp2=$o2*100
newtype22="Skill EXP"
new_craftexp2=$o3*100
newtype23="Craft EXP"
new_droprate2=$o4*100
newtype24="Droprate"
new_alzrate2=$o5*100
newtype25="Alz Rate"
new_alzbrate2=$o6*100
newtype26="Alz Bomb Rate"

sed /etc/cabal/templates/Const.cfg \
-e "s/u00/$new_exp2/g" \
-e "s/v00/$new_skillexp2/g" \
-e "s/w00/$new_craftexp2/g" \
-e "s/x00/$new_droprate2/g" \
-e "s/y00/$new_alzbrate2/g" \
-e "s/z00/$new_alzrate2/g" \
-e "s/abcd/$dropcount2/g" \
> /etc/cabal/Data2/Const.scp
chmod 0777 /etc/cabal/Data2/Const.scp

if [ $use_log -eq 1 ]; then
echo "`date`: Selected $o1 x as rate for $newtype21 on Server 2" | tee -a $logfile
echo "`date`: Selected $o2 x as rate for $newtype22 on Server 2" | tee -a $logfile
echo "`date`: Selected $o3 x as rate for $newtype23 on Server 2" | tee -a $logfile
echo "`date`: Selected $o4 x as rate for $newtype24 on Server 2" | tee -a $logfile
echo "`date`: Selected $o5 x as rate for $newtype25 on Server 2" | tee -a $logfile
echo "`date`: Selected $o6 x as rate for $newtype26 on Server 2" | tee -a $logfile
elif [ $use_log -eq 0 ]; then
echo "`date`: New rates, logs are turned off" | tee -a $logfile
fi

service cabal reload

## Modified by Carlos Bril, 02-07-2011, Original by ChumpyWumpy
## floating_rates_daemon.sh.parall
## v1.1[/spoiler]
```

I myself think the token is correct but for some reason the error keeps coming up. Did I make a mistake in the spacing for instance?

I basically want the script to see if two times a pair values match or not with each other and the other pair, and if not do the line 187. However I just get the syntax error.

I'll attach the file as well. Any help will be greatly appriciated :)

Gr.

/C

---

### Post by Arndt on 2011-07-18
> **CarlosBril said:**
> Dear Ubuntu Community,

I'm a rookie programmer trying to run a simple script I made, but everytime I run it, it gives me the following error:

```
./home/cabal/daemons/floating_rates_daemon.sh: line 187: syntax error near unexpected token `('
./home/cabal/daemons/floating_rates_daemon.sh: line 187: `let o1=(((((((($n1-$base_rate))/(($max_rate-$base_rate))))*(($max_rate2-$base_rate2))))+$base_rate2))'
```

This is the actual file, with line 187 bolded:

[spoiler]```
#!/bin/sh

logfile=/var/log/cabal/floating_rates.log

#Put 0 here to disable, or leave 1 to enable complete logging. Might use alot of disk space over time.
use_log=1
#Server 1:

# Minimum rate 1 = 1x
base_rate=80
# Maximum rate 5 = 5x
max_rate=120

#Minimal other rates:
#Skill Exp
s1=50
#Craft Exp
s2=50
#Droprate
s3=1
#Alzrate
s4=8
#Alzbombrate
s5=6

#Maximal other rates:
#Skill Exp
s6=100
#Craft Exp
s7=100
#Droprate
s8=1
#Alzrate
s9=12
#Alzbombrate
s10=8

# Items per drop
dropcount=2

#Server 2:

# Minimum rate 1 = 1x
base_rate2=300
# Maximum rate 5 = 5x
max_rate2=350

#Minimal other rates:
#Skill Exp
s11=125
#Craft Exp
s12=125
#Droprate
s13=1
#Alzrate
s14=18
#Alzbombrate
s15=12

#Maximal other rates:
#Skill Exp
s16=175
#Craft Exp
s17=175
#Droprate
s18=1
#Alzrate
s19=26
#Alzbombrate
s20=18

# Items per drop
dropcount2=2

#So far the Rates Config, please DO check the dirs the Const.cfg go into.

n1=1
if [ $base_rate -eq $max_rate ]; then
let n1=$base_rate
else
while [ $n1 -le $base_rate ]; do
  n1=$RANDOM
  let "n1 %= $max_rate"
done
fi

n2=1
if [ $s1 -eq $s6 ]; then
let n2=$s6
else
while [ $n2 -le $s1 ]; do
  n2=$RANDOM
  let "n2 %= $s6"
done
fi

n3=1
if [ $s2 -eq $s7 ]; then
let n3=$s7
else
while [ $n3 -le $s2 ]; do
  n3=$RANDOM
  let "n3 %= $s7"
done
fi

n4=1
if [ $s3 -eq $s8 ]; then
let n4=$s8
else
while [ $n4 -le $s3 ]; do
  n4=$RANDOM
  let "n4 %= $s8"
done
fi

n5=1
if [ $s4 -eq $s9 ]; then
let n5=$s9
else
while [ $n5 -le $s4 ]; do
  n5=$RANDOM
  let "n5 %= $s9"
done
fi

n6=1
if [ $s5 -eq $s10 ]; then
let n6=$s10
else
while [ $n6 -le $s5 ]; do
  n6=$RANDOM
  let "n6 %= $s10"
done
fi

let new_exp=$n1*100
newtype11="EXP"
let new_skillexp=$n2*100
newtype12="Skill EXP"
let new_craftexp=$n3*100
newtype13="Craft EXP"
let new_droprate=$n4*100
newtype14="Droprate"
let new_alzrate=$n5*100
newtype15="Alz Rate"
let new_alzbrate=$n6*100
newtype16="Alz Bomb Rate"

 
sed /etc/cabal/templates/Const.cfg \
-e "s/u00/$new_exp/g" \
-e "s/v00/$new_skillexp/g" \
-e "s/w00/$new_craftexp/g" \
-e "s/x00/$new_droprate/g" \
-e "s/y00/$new_alzbrate/g" \
-e "s/z00/$new_alzrate/g" \
-e "s/abcd/$dropcount/g" \
> /etc/cabal/Data/Const.scp
chmod 0777 /etc/cabal/Data/Const.scp


if [ $use_log -eq 1 ]; then
echo "`date`: Selected $n1 x as rate for $newtype11 on Server 1" | tee -a $logfile
echo "`date`: Selected $n2 x as rate for $newtype12 on Server 1" | tee -a $logfile
echo "`date`: Selected $n3 x as rate for $newtype13 on Server 1" | tee -a $logfile
echo "`date`: Selected $n4 x as rate for $newtype14 on Server 1" | tee -a $logfile
echo "`date`: Selected $n5 x as rate for $newtype15 on Server 1" | tee -a $logfile
echo "`date`: Selected $n6 x as rate for $newtype16 on Server 1" | tee -a $logfile
elif [ $use_log -eq 0 ]; then
echo "`date`: New rates, Logs are turned off" | tee -a $logfile
fi

#Server 2 is in /etc/cabal/Data2/Const.scp

if [ $base_rate -eq $max_rate ] && [ $base_rate2 -ne $max_rate2 ]; then
o1=1
while [ $o1 -le $base_rate2 ]; do
  o1=$RANDOM
  let "o1 %= $max_rate2"
done
elif [ $base_rate -ne $max_rate ] && [ $base_rate2 -eq $max_rate2 ]; then
let o1=$s16
elif [ $base_rate -eq $max_rate ] && [ $base_rate2 -eq $max_rate2 ]; then
let o1=$s16
else
**let o1=(((((((($n1-$base_rate))/(($max_rate-$base_rate))))*(($max_rate2-$base_rate2))))+$base_rate2))**
fi

if [ $s1 -eq $s6 ] && [ $s11 -ne $s16 ]; then
o2=1
while [ $o2 -le $s11 ]; do
  o2=$RANDOM
  let "o2 %= $s16"
done
elif [ $s1 -ne $s6 ] && [ $s11 -eq $s16 ]; then
let o2=$s16
elif [ $s1 -eq $s6 ] && [ $s11 -eq $s16 ]; then
let o2=$s16
else
let o2=(((((($n2-$s1))/(($s6-$s1))))*(($s16-$s11))))+$s11
fi

if [ $s2 -eq $s7 ] && [ $s12  -ne $s17 ]; then
o3=1
while [ $o3 -le $s12 ]; do
  o3=$RANDOM
  let "o3 %= $s17"
done
elif [ $s2 -ne $s7 ] && [ $s12 -eq $s17 ]; then
let o3=$s17
elif [ $s2 -eq $s7 ] && [ $s12 -eq $s17 ]; then
let o3=$s17
else
let o3=(((((($n3-$s2))/(($s7-$s2))))*(($s17-$s12))))+$s12
fi

if [ $s3 -eq $s8 ] && [ $s13 -ne $s18 ]; then
o4=1
while [ $o4 -le $s13 ]; do
  o4=$RANDOM
  let "o4 %= $s18"
done
elif [ $s3 -ne $s8 ] && [ $s13 -eq $s18 ]; then
let o4=$s18
elif [ $s3 -eq $s8 ] && [ $s13 -eq $s18 ]; then
let o4=$s18
else
let o4=(((((($n4-$s3))/(($s8-$s3))))*(($s18-$s13))))+$s13
fi

if [ $s4 -eq $s9 ] && [ $s14 -ne $s19 ]; then
o5=1
while [ $o5 -le $s14 ]; do
  o5=$RANDOM
  let "o5 %= $s19"
done
elif [ $s4 -ne $s9 ] && [ $s14 -eq $s19 ]; then
let o5=$s19
elif [ $s4 -eq $s9 ] && [ $s14 -eq $s19 ]; then
let o5=$s19
else
let o5=(((((($n5-$s4))/(($s9-$s4))))*(($s19-$s14))))+$s14
fi

if [ $s5 -eq $s10 ] && [ $s15 -ne $s20 ]; then
o6=1
while [ $o6 -le $s15 ]; do
  o6=$RANDOM
  let "o6 %= $s20"
done
elif [ $s5 -ne $s10 ] && [ $s15 -eq $s20 ]; then
let o6=$s20
elif [ $s5 -eq $s10 ] && [ $s15 -eq $s20 ]; then
let o6=$s20
else
let o6=(((((($n6-$s5))/(($s10-$s5))))*(($s20-$s15))))+$s15
fi

new_exp2=$o1*100
newtype21="EXP"
new_skillexp2=$o2*100
newtype22="Skill EXP"
new_craftexp2=$o3*100
newtype23="Craft EXP"
new_droprate2=$o4*100
newtype24="Droprate"
new_alzrate2=$o5*100
newtype25="Alz Rate"
new_alzbrate2=$o6*100
newtype26="Alz Bomb Rate"

sed /etc/cabal/templates/Const.cfg \
-e "s/u00/$new_exp2/g" \
-e "s/v00/$new_skillexp2/g" \
-e "s/w00/$new_craftexp2/g" \
-e "s/x00/$new_droprate2/g" \
-e "s/y00/$new_alzbrate2/g" \
-e "s/z00/$new_alzrate2/g" \
-e "s/abcd/$dropcount2/g" \
> /etc/cabal/Data2/Const.scp
chmod 0777 /etc/cabal/Data2/Const.scp

if [ $use_log -eq 1 ]; then
echo "`date`: Selected $o1 x as rate for $newtype21 on Server 2" | tee -a $logfile
echo "`date`: Selected $o2 x as rate for $newtype22 on Server 2" | tee -a $logfile
echo "`date`: Selected $o3 x as rate for $newtype23 on Server 2" | tee -a $logfile
echo "`date`: Selected $o4 x as rate for $newtype24 on Server 2" | tee -a $logfile
echo "`date`: Selected $o5 x as rate for $newtype25 on Server 2" | tee -a $logfile
echo "`date`: Selected $o6 x as rate for $newtype26 on Server 2" | tee -a $logfile
elif [ $use_log -eq 0 ]; then
echo "`date`: New rates, logs are turned off" | tee -a $logfile
fi

service cabal reload

## Modified by Carlos Bril, 02-07-2011, Original by ChumpyWumpy
## floating_rates_daemon.sh.parall
## v1.1[/spoiler]
```

I myself think the token is correct but for some reason the error keeps coming up. Did I make a mistake in the spacing for instance?

I basically want the script to see if two times a pair values match or not with each other and the other pair, and if not do the line 187. However I just get the syntax error.

I'll attach the file as well. Any help will be greatly appriciated :)

Gr.

/C

I haven't used 'let' before, but experimenting a bit shows that not even this works

```
let o1=10/(10-5)
```

although this does

```
let o1=10+(10-5)
```

But a little googling shows that quoting may help. Try:

```
let o1="(((((((($n1-$base_rate))/(($max_rate-$base_rate))))*(($max_rate2-$base_rate2))))+$base_rate2))"

```

---

### Post by sisco311 on 2011-07-18
Welcome to the forums!

Talking about quoting... You should quote your variables and improve your indentation.

In Ubuntu, /bin/sh is a symlink to dash. Do you have any reasons (compatibility, portability, speed(?) etc...) for using dash instead of bash?

---

### Post by CarlosBril on 2011-07-18
> **Arndt said:**
> I haven't used 'let' before, but experimenting a bit shows that not even this works

```
let o1=10/(10-5)
```

although this does

```
let o1=10+(10-5)
```

But a little googling shows that quoting may help. Try:

```
let o1="(((((((($n1-$base_rate))/(($max_rate-$base_rate))))*(($max_rate2-$base_rate2))))+$base_rate2))"

```

That worked! How'd you think of this solution? (Googling?)

Sorry for the indentation "sloppiness", I plan on making a "final release" for this file where everything should be nice and tidy.

About the symlink:
The "template" of this file does not belong to me (although I did about 75% of the code here). I have no clue why the original author used dash instead of bash. I hope it's quicker, because that's what I'd go for :/.

Arndt, could you kindly elaborate on what exactly you googled :P?
I did some searches for braces, and brackets and the like, and came up empty (did try using double (( and ))'s, didn't help, only made it sloppier...).

Thanks guys for these advices :D, I'll try to make the file a bit tidier, But atleast it works!
Thanks so much :D!

Gr.

/C

---

### Post by CarlosBril on 2011-07-19
Dear Community,

I want the script to give me an non-integer answer.

I've been searching for this on the web but haven't found a satisfactory answer. They advise me to use nawk or bc but I can't seem to get how they want me to do it.

Let's say I want to make a variable "x" be the division of 4/9, then I'd get a "0" if I'd do this in an integer script. How can I "let x=4/9" without getting a zero?

Gr.

/C

P.S.: Sorry for the double post, needed a bump for this I guess

---

### Post by dethorpe on 2011-07-19
you have to pass your formule to bc and get the result
 
e.g. Using HERE doc:
```
 
x=$(bc <<END
scale=10
4/9
END
)
 
echo $x
.4444444444
 

```
 
Or using a pipe:
```

result=$(echo "scale=10;4/9" | bc)
echo $result
.4444444444

```
 
Hope that helps

---

### Post by CarlosBril on 2011-07-19
> **dethorpe said:**
> you have to pass your formule to bc and get the result
 
e.g. Using HERE doc:
```
 
x=$(bc <<END
scale=10
4/9
END
)
 
echo $x
.4444444444
 

```
 
Or using a pipe:
```

result=$(echo "scale=10;4/9" | bc)
echo $result
.4444444444

```
 
Hope that helps

The piped one seems more elegant, so I'm going to use that one.
Thank you very much :D

Gr.

/C

---

### Post by Arndt on 2011-07-19
> **CarlosBril said:**
> 
Arndt, could you kindly elaborate on what exactly you googled :P?
I did some searches for braces, and brackets and the like, and came up empty (did try using double (( and ))'s, didn't help, only made it sloppier...).
C

Something like "let bash division parentheses".

---

