---
title: "IF statements in bash script"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by chantalv on 2013-02-19
Hi,

Is there anyone who can help me explaining how IF statements work in bash scripts?

I just want to do something like ..see below.. . And i know that there is a difference of extra [ and " between the first one and the other IF-statements, just to indicate that both ways i've already tried (but than being consistent). I do not get any errors, but i have actually 6 combinations to make, it only does the last one (takes always the variables set in last IF), as if there are no IF's etc. above, just takes the very last variables stated...
So when you ask to print var1 is always says 'bb' never 'aa' even when conditions met the IF's to make is 'aa'.

Thanks in advance.


```
ocean="pacific"
data="bathy"

if [[ "${ocean}" == 'pacific' ]]
then
 list1=${PY}
 list_ex=${PM}
 xy_file2=${PT}  									
 configfile='../../data/pacific.config'            		 
 region=-150/-140/-20/-30
 max1=189.
fi

if [ ${ocean} != "atlantic" ]
then
 list1=${AY}
 list_ex=${AM}
 xy_file2=${AT}
 configfile='../../data/atlantic.config'			         	 
 region=-35/-25/30/40
 max1=93.
fi

if [[ "${data}" != 'bathy' ]]
then 
 datagrd='../../data/topo.14.1.resample.grd' 			
 if [[ "${ocean}" != 'pacific' ]]
 then
  win=bathy_pac
  xyE_grd=cut_xyE_parab.grd 
  #out_dir=bathy_pac/
 fi 
 if [[ "${ocean}" != 'atlantic' ]]
 then
  win=bathy_atl
  xyE_grd=cut_xyE_bathy_atl.grd
  #out_dir=bathy_atl/
 fi
fi

if [ ${data} != "grav" ]
then 
 datagrd='../../data/grav.19.1.resample.grd'
  if [ ${ocean} != "pacific" ]
  then
   win=grav_pac
   xyE_grd=cut_xyE_grav.grd
   #out_dir=grav_pac/
  fi
  if [ ${ocean} != "atlantic" ]
  then
   win=grav_atl
   xyE_grd=cut_xyE_gr_atl.grd
   #out_dir=grav_atl/
  fi 
fi
 
if [ ${data} != "VGG" ]
then 
  datagrd='../../data/curv.19.1.resample.grd'
  if [ ${ocean} != "pacific" ]
  then
   win=VGG_pac
   xyE_grd=cut_xyE_VGG_pac.grd
   #out_dir=VGG_pac/
  fi
  if [ ${ocean} != "atlantic" ]
  then
   win=VGG_atl
   xyE_grd=cut_xyE_VGG_new_atl.grd
   #out_dir=VGG_atl/
 fi
fi

echo 'the xyE_grd file used is' ${xyE_grd}

```

It always echos " the xyE_grd file used is cut_xyE_VGG_new_atl.grd ". Why is that? I tell it to use xyE_grd=cut_xyE_parab.grd (in the first IF)

I tried this with using these 2 formats consistently:
```
 if [[ "${ocean}" == 'pacific' ]]
if [ ${ocean} != "pacific" ] 
```

---

### Post by Vaphell on 2013-02-19
could you put your pseudocode in [****code][/code] tags and indent it properly? tracking multiple if/fi's is not too easy on the eyes.

you should give some real variables to showcase your problem, or even *echo "this is branch X"* so people don't have to think too hard what <even more variables specified> or <same variables specified as above but than slightly different> mean exactly.
you would be able to say: code provided does exactly this <copy-paste job> when given this input, question is why?

---

### Post by CharlesA on 2013-02-19
> **Vaphell said:**
> could you put your pseudocode in [****code][/code] tags and indent it properly? tracking multiple if/fi's is not too easy on the eyes.

you should give some real variables to showcase your problem, or even *echo "this is branch X"* so people don't have to think too hard what <even more variables specified> or <same variables specified as above but than slightly different> mean exactly.
you would be able to say: this code does exactly this <copy-paste job> when given this input, question is why?

This.

As far as [ vs [[, see here:
[http://stackoverflow.com/questions/2188199/bash-double-or-single-bracket-parentheses-curly-braces](http://stackoverflow.com/questions/2188199/bash-double-or-single-bracket-parentheses-curly-braces)

Also:
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

### Post by chantalv on 2013-02-19
Thank you so far. But with the [ and [[ I mean I have tried both ways. (but then of course use [ for all IF's and later [[ for all)

---

### Post by CharlesA on 2013-02-19
Something is wrong with your code then.

Try echoing variables and see where the problem lines.

---

### Post by apmcd47 on 2013-02-19
After a very quick read of your code it looks to me that you have one equality check - the rest are inequality checks. given the values of the variables at the top of the code you basically drop into the THEN portion of every IF statement except for the ```
if [${data} != 'bathy' ]
``` Are you sure this is correct?

For consistency's sake please use double quotes for all strings and variables (for variables in case they are empty or values contain spaces) and only use single quotes when special characters are to be quoted.

Andrew

---

### Post by Vaphell on 2013-02-19
your script discards all the changes made in previous condition branches because it always enters the "data **not equal** VGG"/"ocean **not equal** atlantic" ($data!="VGG", $ocean!="atlantic")
it's true because data=bathy (not vgg) and ocean is pacific (so not equal atlantic)


in that branch *xyE_grd=cut_xyE_VGG_new_atl.grd* happens and it's the last thing that happens.

you don't control the program flow too well. If you want exclusive options you should use something like if elif else, eg

```
if [ "$ocean" = "atlantic" ]
then
  *settings for atlantic*
elif [ "$ocean" = "pacific" ]
then
  *settings for pacific*
else
  *settings for everything else*
fi
```
then do the same for $data or embed the conditions for $data in nested ifs under these main branches

you can also write complex conditions like```
[ "$ocean" = "pacific" -a "$data" = "bathy" ] # (-a being AND)
[[ $ocean = "pacific" && $data = "bathy" ]]
```



i took your code and modified it (variables out, echos everywhere) to indicate which branches get visited

```
#!/bin/bash

ocean="pacific"
data="bathy"

if [[ "${ocean}" == 'pacific' ]]
then
  [COLOR="Blue"]echo "ocean equal pacific"[/COLOR]
fi

if [ ${ocean} != "atlantic" ]
then
  [COLOR="Blue"]echo "ocean not equal atlantic"[/COLOR]
fi

if [[ "${data}" != 'bathy' ]]
then 
  if [[ "${ocean}" != 'pacific' ]]
  then
    echo "data not equal bathy, ocean not equal pacific"
  fi 
  if [[ "${ocean}" != 'atlantic' ]]
  then
    echo "data not equal bathy, ocean not equal atlantic"
  fi
fi

if [ ${data} != "grav" ]
then 
  if [ ${ocean} != "pacific" ]
  then
    echo "data not equal grav, ocean not equal pacific"
  fi
  if [ ${ocean} != "atlantic" ]
  then
    [COLOR="Blue"]echo "data not equal grav, ocean not equal atlantic"[/COLOR]
  fi 
fi
 
if [ ${data} != "VGG" ]
then 
  if [ ${ocean} != "pacific" ]
  then
    echo "data not equal VGG, ocean not equal pacific"
  fi
  if [ ${ocean} != "atlantic" ]
  then
    [COLOR="Blue"]echo "data not equal VGG, ocean not equal atlantic"[/COLOR]
 fi
fi
```

output:

```
$ ./bash_if.sh 
ocean equal pacific
ocean not equal atlantic
data not equal grav, ocean not equal atlantic
data not equal VGG, ocean not equal atlantic
```
as you can see 4 branches are visited

---

### Post by chantalv on 2013-02-20
Thank you very much, it works fine now!!

Except from that I want to be able to get the IF's working in the future too. So what do you mean by the if elif else? Do I have to use that for all the IF's in 1 script? So I say if .., elif .., else .., else .., (can i add as many else's as i want to?).

---

### Post by kholburn on 2013-02-20
> **chantalv said:**
> Thank you very much, it works fine now!!

Except from that I want to be able to get the IF's working in the future too. So what do you mean by the if elif else? Do I have to use that for all the IF's in 1 script? So I say if .., elif .., else .., else .., (can i add as many else's as i want to?).

You must start with an if, you can have as many elif (else if) statements as you like but only one else and one last fi!!!

A simple if:
```

if <test>; then
  <do stuff>
fi

```
if with else:
```

if <test>; then
  <do stuff>
else
  <do other stuff>
fi

```
if with elif:
```


if <test>; then
  <do stuff>
elif <test>; then
  <do another thing>
else
  <do other stuff>
fi

```
the last is the same as or a shorthand for:
```

if <test>; then
  <do stuff>
else 
  if <test>; then
    <do another thing>
  else
    <do other stuff>
  fi
fi

```

---

### Post by schragge on 2013-02-20
> **chantalv said:**
> I tried this with using these 2 formats consistently:
```
 if [[ "${ocean}" == 'pacific' ]]
if [ ${ocean} != "pacific" ] 
```You've got it backwards. It's the other way round. You may omit double-quotes around variables if using [[ ... ]], but nearly always should use them in [ ... ]:
In bash, this
```

[[ ${ocean} == pacific ]]

```
is equivalent to
```

[ "${ocean}" = pacific ]

```

---

### Post by chantalv on 2013-02-20
OK, thank you all very much! I guess I get it know :D

---

