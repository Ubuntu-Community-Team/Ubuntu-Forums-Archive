---
title: "compare a variable to a list and exit on fail"
date: 2010-04-15
forum: Programming Talk
---

### Post by prupert on 2010-04-15
Hi

I want to compare a variable to a list of options and then exit the script if the variable is not in that list.

The example code I am trying out below compares the version of Ubuntu the user is running to a list of recent Ubuntu distros.

```
#next, lets find out what version of Ubuntu we are running
DISTRO=( $(cat /etc/lsb-release | grep CODE | cut -c 18-) )
OKDISTRO="hardy
intrepid
jaunty
karmic
lucid"

while [ "$DISTRO" -ne "$OKDISTRO" ]; do
	die "Exiting. Your distro is not supported, sorry."
done
 
echo "You are running Ubuntu $DISTRO, selecting the necessary $DISTRO installation." 
echo
```

(die is a function that exits the script)

The code works, (well it does for me) but I do get the following message:

line 9: [: lucid: integer expression expected

Obviously there is something wrong with the way I am checking my variable against the list of variable,s but I couldn't find a better way of doing it.

Can any one suggest a better approach and what the error message means?

---

### Post by MadCow108 on 2010-04-15
the error is because you are missing spaces inside the square brackets
bash is very picky about that
it will probably not work when you fix that.

you can do that in bash:
```

if [[ $list == *substring* ]]; then
  echo "substring in list";
fi

```
but it also matches prefixhardysuffix and so on, so its not too reliable depending on input

---

### Post by falconindy on 2010-04-15
> **prupert said:**
> Hi

I want to compare a variable to a list of options and then exit the script if the variable is not in that list.

The example code I am trying out below compares the version of Ubuntu the user is running to a list of recent Ubuntu distros.

```
#next, lets find out what version of Ubuntu we are running
DISTRO=( $(cat /etc/lsb-release | grep CODE | cut -c 18-) )
OKDISTRO="hardy
intrepid
jaunty
karmic
lucid"

while [ "$DISTRO" -ne "$OKDISTRO" ]; do
	die "Exiting. Your distro is not supported, sorry."
done
 
echo "You are running Ubuntu $DISTRO, selecting the necessary $DISTRO installation." 
echo
```

(die is a function that exits the script)

The code works, (well it does for me) but I do get the following message:

line 9: [: lucid: integer expression expected

Obviously there is something wrong with the way I am checking my variable against the list of variable,s but I couldn't find a better way of doing it.

Can any one suggest a better approach and what the error message means?
The test flag '-ne' is used to compare numbers, not strings. Also, I would call grep in this case to remove the necessity of the while loop. Something like...

```
if [[ ! $(grep -q $DISTRO <<< $OKDISTRO) ]]; then
  echo "distro fail"
  exit 1;
fi
```
There's no need to separate the elements in the OKDISTRO var with newlines, either.

---

### Post by prupert on 2010-04-15
Of course integer expression expected - it was trying to tell me all along.

Thanks for both your inputs, I'll try grep option and see how that works.

thanks loads

---

### Post by kaibob on 2010-04-16
> **falconindy said:**
> The test flag '-ne' is used to compare numbers, not strings. Also, I would call grep in this case to remove the necessity of the while loop. Something like...

```
if [[ ! $(grep -q $DISTRO <<< $OKDISTRO) ]]; then
  echo "distro fail"
  exit 1;
fi
```
There's no need to separate the elements in the OKDISTRO var with newlines, either.

I couldn't get this to work until I removed the -q option from grep. The man page defines this option as "Quiet;  do  not write anything to standard output.  Exit immediately with zero status if any match is found, even if an error was detected."

---

### Post by falconindy on 2010-04-16
> **kaibob said:**
> I couldn't get this to work until I removed the -q option from grep. The man page defines this option as "Quiet;  do  not write anything to standard output.  Exit immediately with zero status if any match is found, even if an error was detected."
Interesting. Works fine from a prompt with -q, but not from a script.

---

### Post by prupert on 2010-04-16
> **falconindy said:**
> Interesting. Works fine from a prompt with -q, but not from a script.

Yup, exactly what I found too, it works perfectly now.

---

