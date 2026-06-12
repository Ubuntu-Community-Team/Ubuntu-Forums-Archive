---
title: "Customized syntax"
date: 2012-09-17
forum: Programming Talk
---

### Post by jelee on 2012-09-17
Hey,  I just started out some weeks whit Ubuntu, but me big problem is that i'm using long and complex syntaxes; 

```
./example.pl -p 2 -u 5 -p domain.com
```
To: 
```
./final_example.pl -D domain.com
```

I looked at the alias feature, but what I saw /'ve noticed is that it can not handle custom parameters, and that I should write a function to make. just me knowledge was not that far.

can someone maby sent me in the good direction (peace of code and a nice tutorial?)

---

### Post by codemaniac on 2012-09-17
Hi jelee ,

Welcome to the UbuntuForums !

When a application or program has multiple functionalities , you need to pass an array of switches to direct you as per your wish .

You can create a shell script from which you can call the ./example.pl with predefined options .

```
#!/bin/bash

domain=$1
./example.pl -p 2 -u 5 -p $domain
```

you can then call the script something like below 

```
./final_example.pl domain.com
```

---

### Post by jelee on 2012-09-17
Hey, Codemaniac
Thank you for you fast reaction! i was on the good way, If i compair the both codes, 
but still got i some questions about this. 
how can i add a parameter to this? 

/final_example.pl **-D** domain.com

and some error handling?

 if ( $domain == 0 | $domain =< 4) { 	echo "you forget parameter -D"; }

Still looking for a good tutorial

---

### Post by codemaniac on 2012-09-17
> **jelee said:**
> Hey, Codemaniac
Thank you for you fast reaction! i was on the good way, If i compair the both codes, 
but still got i some questions about this. 
how can i add a parameter to this? 

/final_example.pl **-D** domain.com

and some error handling?

 if ( $domain == 0 | $domain =< 4) { 	echo "you forget parameter -D"; }

Still looking for a good tutorial

You can try something like below .

```
doption=false        # domain not specified

for option in $*
do
   case $option in
      -D)   doption=true;shift;domain="$1";shift;;
      -*)
         echo "invalid arguments"
         echo "Usage : /final_example.pl -D domain.com"
         exit 1;;
   esac
done
```

---

### Post by ofnuts on 2012-09-17
> **jelee said:**
> Hey, Codemaniac
Thank you for you fast reaction! i was on the good way, If i compair the both codes, 
but still got i some questions about this. 
how can i add a parameter to this? 

/final_example.pl **-D** domain.com

and some error handling?

 if ( $domain == 0 | $domain =< 4) {     echo "you forget parameter -D"; }

Still looking for a good tutorial

if you just want to add a couple of fixed parameters to the command, you can use:
```

#! /bin/bash
thecommand your fixed parms "$@"
exit $?

```where "$@" will be replaced by all arguments to your script. Error handling can be restricted to propagating the return code of the command you call (which ends up in the special variable "$?").

For this kind of use, you don't really need to handle problems yourself

---

### Post by Vaphell on 2012-09-17
i don't think *for* would cooperate with *shift* so i'd use *while* controlled by the number of params (each shift decreases that number)
```
while (($#))
do
  case "$1" in
    -D)   doption=true;shift;domain="$1";;
    *)    echo "'$1' - invalid argument";;
  esac
  shift
done
```

---

### Post by codemaniac on 2012-09-17
> **Vaphell said:**
> i don't think *for* would cooperate with *shift* 


But surprisingly it does , please note the extra shift . ;)

---

### Post by jelee on 2012-09-17
```
#!/bin/bash

# command
sudo nmap -sS $1

#parameters
ipoption=$1

#error afhandeling 
ipoption=false  #domain not specified

for option in $*
do
case $ipoption in 
    -ip) option=true;shift;domain="$1";shift;;
    -*) 
    echo "invalid arguments" 
    echo "Usage : test_script.pl -ip ip adres"
    exit;;
esac
done
```

I got this right now,  put it wont want to work for me. 
it seems to me that the script nmap overuled, (get the manual of nmap to see after running the script whit parameter  (and  withoud a parameter its saying no host specified) 

Questions:
- Can i overule a other script? turn off the feedback/Echo withoud entering nmap?
- Can someone give me a working script (i see that there are more ten one solution for this,  different peaces of code.)
for me as "noob" and small experince in php, is this pretty new for me. and need a working solution.. something easy to use and to add more parameters. and to learn

---

### Post by Vaphell on 2012-09-17
> But surprisingly it does , please note the extra shift . 

yet it doesn't :P
```
#!/bin/bash

for param
do
  echo  "$((++i)): $param"
  case $param in
    -D) shift; x="$1"; shift; echo -n "[COLOR="Red"]-D $x[/COLOR], ";;
    *) echo -n "$param, ";;
  esac
  echo "params left [$#]: $@"
done
```
output:
```
$ ./test_params.sh a b [COLOR="Red"]-D xyz[/COLOR]
1: a
a, params left [4]: a b -D xyz
2: b
b, params left [4]: a b -D xyz
3: -D
[COLOR="Red"]-D b[/COLOR], params left [2]: -D xyz
4: xyz
xyz, params left [2]: -D xyz
```

for loop is constructed at the beginning and fixed, shifting doesn't do anything worthwhile and calling $1 doesn't make sense at all (you get wrong arg).
Only while+shift make sure that you get to access each param only once.

```
#!/bin/bash

while (($#))
do
  param="$1"
  echo  "$((++i)): $param"
  case $param in
    -D) shift; x="$1"; echo -n "[COLOR="Red"]-D $x,[/COLOR] ";;
    *) echo -n "$param, ";;
  esac
  shift
  echo "params left [$#]: $@"
done
```
output:
```
$ ./test_params2.sh a b [COLOR="Red"]-D xyz[/COLOR]
1: a
a, params left [3]: b -D xyz
2: b
b, params left [2]: -D xyz
3: -D
[COLOR="Red"]-D xyz[/COLOR], params left [0]: 
```

---

### Post by codemaniac on 2012-09-17
> **Vaphell said:**
> yet it doesn't :P


Hi ,

The objective was to first use shift to ignore the switch , then grab the value to the variable and again a shift to point to the next switch .It works and expects you to adhere a standard ***-option value*** convention .

Please have this simple example .
```

#!/bin/bash

for option in $*
do
        case $option in
        -n) shift
            NAME=$1
            echo "The name is $NAME"
            shift
        ;;
        -a) shift
            AGE=$1
            echo "Age is $AGE"
            shift
        ;;
        -*) echo "Invalid Option"
        ;;
        esac
done

```
```
./passOptions.sh -n Arijit -a 25
The name is Arijit
Age is 25
```

---

### Post by Vaphell on 2012-09-17
oh i get it now, though i still think the *while* loop is more elegant.
You work ONLY with $1 and your goal is to make sure there are no more $1's left. There are no dry runs possible while in case of *for* there are (shifting doesn't influence the number of iterations at all).

after adding to your example ((++i)) in loop body and echoing $i at the end (and later the same in while version)
```
$ ./params_for.sh -n NAME -a 555
The name is NAME
Age is 555
**iterations: 4**
$ ./params_while.sh -n NAME -a 555
The name is NAME
Age is 555
**iterations: 2**
```

---

