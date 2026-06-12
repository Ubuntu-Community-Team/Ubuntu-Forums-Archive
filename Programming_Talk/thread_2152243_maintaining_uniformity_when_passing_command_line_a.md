---
title: "maintaining uniformity when passing command line arguments"
date: 2013-06-07
forum: Programming Talk
---

### Post by IAMTubby on 2013-06-07
Hello,
The below script would fail if you pass a string in place of an integer, as **$sh ./myscript.sh stringtest**
```

#myscript.sh
if [ $1 -eq 10 ];then
 echo "the number entered is 10"
fi

```


I would correct this by doing the below and that would take care of string arguments also. But is this the general approach, I find it unlikely because this approach cuts you off completely from using **-eq** for comparison just because you're using command line arguments
```

if [ $1 = 10 ];then
 echo "the number entered is 10"
fi

```


Please advise.
Thanks.

---

### Post by ofnuts on 2013-06-07
If you use bash and double brackets you won't have the problem. Otherwise use a regexp to check that you have only digits...

---

### Post by IAMTubby on 2013-06-07
> **ofnuts said:**
> If you use bash and double brackets you won't have the problem. Otherwise use a regexp to check that you have only digits...
ofnuts, wow, that helped :) . I tried running this sample code with both string as well as integer inputs, it gave me the output with the integer and did not crash with the string unlike before
```

if [[ $1 -eq 10 ]]; then
   echo "do something";
fi

```

> 
If you use bash

do you mean, bash as a keyword to be used somewhere, or you just meant shell in general. Didn't understand your usage in the previous line.

Also, can you tell me something about **[[** and why it handles both types of input.

Thanks.

---

### Post by Vaphell on 2013-06-07
shells in general trust you to provide proper data, you have to put in additional test yourself and branch out to skip a part of code if necessary

something like this should work
```
if **[ -z "${x//[0-9]/}" ] &&** [ $x -eq 10 ]; then echo "NUMBER 10"; else echo "???"; fi
```
replace all digits with nothing and check if you have an empty string (means it was all digits), if true go to the -eq comparison


```
$ x=10
$ if [ -z "${x//[0-9]/}" ] && [ $x -eq 10 ]; then echo "NUMBER 10"; else echo "???"; fi
NUMBER 10
$ x=10XXXX
$ if [ -z "${x//[0-9]/}" ] && [ $x -eq 10 ]; then echo "NUMBER 10"; else echo "???"; fi
???
```

of course in your case it would be **${1//[0-9]/}** (1 is just like an any other variable name but reserved for params)


edit:
bash comes with many cool convenience features, as evidenced here, [[ ]] is one of things other shells don't have. 'Use bash' means use it as a shell executing the script
usually it's done with this very first line of the script
```
#!/bin/bash
```
if your script is executable (chmod +x myscript.sh) you can run it like this
```
./myscript.sh stringtest
```and system will figure out that you want bash thanks to that *hashbang* line. That way you don't have to remember 5 months down the road which flavor of shell you should use to run the script properly, it's right there in the script

---

### Post by ofnuts on 2013-06-07
> **Vaphell said:**
> 
bash comes with many cool convenience features, as evidenced here, [[ ]] is one of things other shells don't have. 'Use bash' means use it as a shell executing the script
usually it's done with this very first line of the script
```
#!/bin/bash
```
if your script is executable (chmod +x myscript.sh) you can run it like this
```
./myscript.sh stringtest
```and system will figure out that you want bash thanks to that *hashbang* line. That way you don't have to remember 5 months down the road which flavor of shell you should use to run the script properly, it's right there in the script
And of course, don't execute the script but using "sh myscript", which short-circuits the shebang.

---

### Post by IAMTubby on 2013-06-08
> **Vaphell said:**
> shells in general trust you to provide proper data, you have to put in additional test yourself and branch out to skip a part of code if necessary

something like this should work
if **[ -z "${x//[0-9]/}" ] &&** [ $x -eq 10 ]; then echo "NUMBER 10"; else echo "???"; fi

Thanks a lot Vaphell, but can you tell me what I should google to understand **[COLOR=#000000][FONT=Ubuntu Mono]if [/FONT][/COLOR][B][ -z "${x//[0-9]/}" ].**[/B]I did not understand that line. New to shell scripting :)

> **ofnuts said:**
> And of course, don't execute the script but using "sh myscript", which short-circuits the shebang.
Thanks ofnuts

---

### Post by Vaphell on 2013-06-08
**${x//pattern/replacement}** is 'take x but with all occurences of *pattern* replaced with a given string'
[http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion)

in case of **${x//[0-9]/}**  it's 'replace every digit with nothing'
if your param is pure number the result of that operation should be empty, right? That can be tested with  [ **-z** ... ]

---

