---
title: "Beginner help getting return value of program call shell script"
date: 2012-12-25
forum: Programming Talk
---

### Post by einstein**-7 on 2012-12-25
Hey there, i'm trying to make a short script that auto adjust the nvidia-settings fan speed but i need the return value of the gpu temperature to perform math on.

I can get    " eval 'temperature' "     to print the temp but can't seem to  get the actual value for the math operation.
returns nothing! or a string

Help!!
thanks,

---

### Post by Vaphell on 2012-12-25
why use *eval*? *temperature* alone doesn't work? *eval* is a dirty hack and shouldn't really be used.
care to paste the output?

---

### Post by einstein**-7 on 2012-12-26
Ok 'temperature' was just a example here is the script and the output

```
#get current temperature
cur_temp='nvidia-settings -t -q [GPU:0]/GPUCoreTemp'
#echo $cur_temp
#get fan speed
cur_speed='nvidia-settings -t -q [fan:0]/GPUCurrentFanSpeed'
#refresh interval
interval=10

while :
do
    #set fan speed if above 20%    
    new_speed=$(( $cur_temp / 70 \* 100 ))
    echo $new_speed     
    if [ '$new_speed' -gt 20 ]; then
        nvidia-settings -a [gpu:0]/GPUFanControlState=1 -a [fan:0]/GPUCurrentFanSpeed='$new_speed'
    fi    
    sleep 10

done
```



```
/bin/nvautofanadjust: line 16: nvidia-settings -t -q [GPU:0]/GPUCoreTemp / 70 \* 100 : syntax error: invalid arithmetic operator (error token is "[GPU:0]/GPUCoreTemp / 70 \* 100 ")
```

As you can see the variable 'cur_temp' dosn't return the temp after calling the 'nvidia-settings' I tried other methods and always got something like this or a null.

---

### Post by steeldriver on 2012-12-26
Your quotes appear to be wrong - you are probably trying to use backticks which look like `...` but you have single quotes '...' which cause your command to be interpreted as a literal string instead of executed

In any case, backticks are deprecated and you should use $(...) instead i.e. try

```
cur_temp=**$(**nvidia-settings -t -q [GPU:0]/GPUCoreTemp**)**
```Same applies to cur_speed

EDIT: you also need to remove the single quotes from '$new_speed' (or replace them with double quotes - which allow the variable to be expanded to its value)

---

### Post by einstein**-7 on 2012-12-26
OK thanks for the syntax correction.. now it runs with no erros but this code returns 0
```
new_speed=$(( $cur_temp / 70 * 100 ))
    echo $new_speed     
```

maybe because it only supports integers??  I need to find percent so floating nums a must -- the quickest way to get floating math ?  I'm used to python which has its own math support in the syntax.
thanks

---

### Post by steeldriver on 2012-12-26
you might be able to just change the order of operations

```
$ cur_temp=60; new_speed=$(( 100 * $cur_temp / 70  )); echo $new_speed
85
```or you could use 'bc' to do floating point math

```
$  cur_temp=60; new_speed=$(echo "scale=3; $cur_temp / 70.0 * 100" | bc); echo $new_speed
85.700
```

---

### Post by einstein**-7 on 2012-12-27
Thanks for all the help! ... works great.  
Any reason changing the order for the math works?

Here is the script feel free to use.
```
#!/bin/bash

#nvautofanadjust


while :
do
    #set fan speed if above 20%
    cur_temp=$(nvidia-settings -t -q [GPU:0]/GPUCoreTemp)
    cur_speed=$(nvidia-settings -t -q [fan:0]/GPUCurrentFanSpeed)    
    new_speed=$(( 100 * $cur_temp / 80 ))
    echo 'gpu temp is' $cur_temp 'set fan to' $new_speed '%'     
    if [ $new_speed -gt 20 ]; then
        nvidia-settings -a [gpu:0]/GPUFanControlState=1 -a [fan:0]/GPUCurrentFanSpeed=$new_speed
    fi    
    sleep 3

done
```

---

### Post by steeldriver on 2012-12-27
Well assuming the order of operations is L->R (since * and / have the same intrinsic precedence), if you multiply by 100 first, the result is big enough that dividing it by 70 is still > 0 even in integer division

OTOH if $cur_temp is < 70 and you integer-divide by 70 first, the result is 0 right away

---

### Post by trent.josephsen on 2012-12-27
I had almost that exact problem in a HS programming competition, many years ago... the task was to write a recursive algorithm to find the [Catalan numbers](http://en.wikipedia.org/wiki/Catalan_number), and I wrote the crucial line as something like (in Java)
```
return 2*(2*n - 1)/(n + 1)*catalan(n - 1);
```

which worked fine for the first few numbers in the sequence, but when n = 3, the first part of the expression truncates 2*5/4 = 2.5 to 2, and the numbers start drifting from there... I eventually fixed it by accident, but didn't realize what the actual mistake had been until afterwards. The time wasted trying to fix my dumb mistake is most likely what cost my team first place.

tl;dr: If you forget that integer division truncates, you can at best take second place. :-P

---

