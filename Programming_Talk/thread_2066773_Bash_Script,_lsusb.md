---
title: "Bash Script, lsusb"
date: 2012-10-05
forum: Programming Talk
---

### Post by conradin on 2012-10-05
Hi all I have a usb device that I want to poll periodically.
the device is listed as:
```
lsusb | grep "Tiger Jet Network"
Bus 002 Device 004: ID 06e6:c200 Tiger Jet Network, Inc. Internet Phone
```

all I want to know is when its plugged in or not plugged in. 
how might I do that?

Im just starting to read about polling, lsusb tells me what I want to know, but I dont know how to put it into a true  false statement in a bash script.
```
#!/bin/bash

result=0
result=`lsusb | grep -e "Tiger Jet Network, Inc. Internet Phone"`
if $result !=0
then 
	echo "Great execute some code" 
		else
			echo "Device was unpluged"
			exit
fi
```

That is what I had tried thus far, but it doesnt work.
can someone point me in the direction of being able to execute code if 
lsusb says my device is plugged in?

---

### Post by drmrgd on 2012-10-05
Not sure if this is exactly correct, but I think you can just use the status of the shell exit code in that conditional statement (also have a look at your conditional statement construct...not sure that's quite correct):

```
#!/bin/bash

result=$(lsusb | grep -e "Tiger Jet Network, Inc. Internet Phone")

if [ $? -ne 0 ]; then
        printf "Device is unplugged\n"
else
        printf "Great execute some code\n"
fi
```

Give that a shot to see if it works as you expect

---

### Post by conradin on 2012-10-05
That does work exactly as I want, Thank you very much!
I think I have a better understanding of $ now too. 
But there are persistently things I dont understand about $. Like, what is the meaning of "$?"  ..?



> **drmrgd said:**
> Not sure if this is exactly correct, but I think you can just use the status of the shell exit code in that conditional statement (also have a look at your conditional statement construct...not sure that's quite correct):

```
#!/bin/bash

result=$(lsusb | grep -e "Tiger Jet Network, Inc. Internet Phone")

if [ $? -ne 0 ]; then
        printf "Device is unplugged\n"
else
        printf "Great execute some code\n"
fi
```

Give that a shot to see if it works as you expect

---

### Post by Lars Noodén on 2012-10-05
There are special variables that contain various pieces of useful information.  $? provides the exit status of the last program run.  $$ is the process ID of the current script.

Scroll down this page to see more:
[http://tldp.org/LDP/abs/html/internalvariables.html](http://tldp.org/LDP/abs/html/internalvariables.html)

---

### Post by sisco311 on 2012-10-06
> **Lars Noodén said:**
> There are special variables that contain various pieces of useful information.  $? provides the exit status of the last program run.  $$ is the process ID of the current script.

Scroll down this page to see more:
[http://tldp.org/LDP/abs/html/internalvariables.html](http://tldp.org/LDP/abs/html/internalvariables.html)

That link contains inaccurate informations. $BASH or $whatever is not an internal variable or builtin variable. It's a parameter expansion. **BASH** is a shell variable and **whatever** is a parameter :) 

See:
```
man bash | less +/" +  Parameter Expansion"
```

$ is the expansion character. It's a [special character]("http://mywiki.wooledge.org/BashGuide/SpecialCharacters") or metacharacter used in substitutions: parameter and variable expansion, command substitution and arithmetic expansion.


? and $ (yep, **whatever** includes the $ sign too :) ) are [special parameters]("http://mywiki.wooledge.org/BashGuide/Parameters").

$? expands to the exit code of the most recently completed foreground command.

$$ expands to the PID (process ID number) of the current shell. The first $ sign is a the expansion character and the second is the special parameter.

---

### Post by Lars Noodén on 2012-10-06
> **sisco311 said:**
> That link contains inaccurate informations.

Thanks.  The e-mail address of the author can be found on this link:  [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
Could you report the mistake to him?

In perl, these are actual special variables  Possibly it is the same in other languages and part of the mix up.

---

