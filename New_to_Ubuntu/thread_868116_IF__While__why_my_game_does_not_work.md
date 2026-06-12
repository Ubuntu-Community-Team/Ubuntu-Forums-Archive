---
title: "IF ??? While ?? why my game does not work"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by just_linux on 2008-07-23
Hi everyone.. :popcorn:
This is my very very first program in shell ( I am programming for 3 years in PHP C++ JAVA)
I can not find why my code does not work 
if I wantted to write the same program in c++ it would of take me 2 min MAX (of course 1.5 min for compiling:lolflag:)
I hate how we need to put -gt -lt  instead of < > 
any way please see what is wrong and correct it for me ( be very clear I am beginner 
Thanks :guitar: 

```
    #!/bin/sh
    chmod +x first.sh
	clear
	a=0
	c=0
	
	while [ a -lt c ]
	do	
		echo Welcome To my First Game
		echo Please Enter The smallest Number you could Guess?
		read a
		echo Please Enter The Largest Number you could Guess?
		read c 
	done

	RANDOM=`date '+%s'`
	b=$[($RANDOM % $c) + $a]

	echo Please Guess My number\n ':'
	
	d=$a-1
	e=0
	
	while [ "$d" != "$b" ]
	do	
		$e=$e+1	
		echo Your $e is ':'
		read d
			
			if [d -lt b]; then
				echo "Smaller please \n"
			fi
			
			if [d -gt b]; then
				echo "Larger please \n"
			fi
	done

	echo Good JOB As you know the number was $b \n
	echo it took you $e steps to guess the number\n \n bye

```

---

### Post by tamoneya on 2008-07-23
can you give us the output of running that code in terminal?

---

### Post by just_linux on 2008-07-23
> **tamoneya said:**
> can you give us the output of running that code in terminal?

Sorry I entered 10 20

joseph@joseph-desktop:~/Desktop$ ./first.sh 

./first.sh: line 7: [: a: integer expression expected
./first.sh: line 17: (6659 % 0) + 0: division by 0 (error token is ") + 0")
Please Guess My numbern :
./first.sh: line 26: 0=0+1: command not found
Your 0 is :
10
./first.sh: line 30: [d: command not found
./first.sh: line 34: [d: command not found
./first.sh: line 26: 0=0+1: command not found
Your 0 is :
20
./first.sh: line 30: [d: command not found
./first.sh: line 34: [d: command not found
./first.sh: line 26: 0=0+1: command not found
Your 0 is :
:mad:
Thanks

---

### Post by DGortze380 on 2008-07-23
You're if statements are going to be one of your problems.

I think you want to compare the VALUES of the variables. Use a $.

if [[ $d -lt $b ]]
then
    #some code
fi

same with the first while loop

and I believe you need [[ ]] not [ ] for all while loops and if statements

It also looks like you have some logic errors. The first while loop will never trigger because 0 is not less than 0.

you didn't read in a value for e

your statement and seed for RANDOM are wrong

that should get you started. check you logic, google the syntax. If you're still having trouble (and it's not a school assignment), I'll go through it when I have time and give you an example. PM me.

---

### Post by DGortze380 on 2008-07-23
Played around with it and came up with my solution to the problem. PM or e-mail for a copy.

---

