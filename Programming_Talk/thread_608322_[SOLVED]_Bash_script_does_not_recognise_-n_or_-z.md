---
title: "[SOLVED] Bash script does not recognise -n or -z"
date: 2007-11-09
forum: Programming Talk
---

### Post by RetiredInMaine on 2007-11-09
I am running Ubuntu 7.10  and have been experimenting with bash scripting.

I am trying to evaluate an input parameter to see if  it exists. The documentation says [-n string] is true if the string  is greater than zero and [-z string] is true if it is null. I take this to mean that -n string its true if the string exists and -z is true if it does not.

I have tried writing some test code but when I execute the script it says that n (or z) is not found.

Example: 

if[-z $1 ]
   then
  	echo "in if portion"
  else
    echo "in else portion"	
fi	

when I exec ,/test I get

./test: 12: if[-z: not found
./test: 13: Syntax error: "then" unexpected

I have tried this with both -n and -z, also tried using capital n and z, with and without quoting $1 and with and without using ./test junk

note that echo $1 works as expected.

So, if this a bug in 7.10 or am I missing something?

Thanks in advance for any help

---

### Post by slavik on 2007-11-09
if [ -z "" ]; then echo "hello"; fi

there is a space between the [ and the - :)

---

### Post by RetiredInMaine on 2007-11-09
Thank you, my problem turned out to be no space between the if and the [

---

