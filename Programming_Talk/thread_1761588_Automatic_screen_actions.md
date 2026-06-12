---
title: "Automatic screen actions"
date: 2011-05-18
forum: Programming Talk
---

### Post by bareil76 on 2011-05-18
Hi!
I run a software called FDTD from Optiwave and I have multiples files to extract (about 150files).

Right now, I need to do it manually. I would like to build a software that would do it for me!

I would need to following actions

1) Increment number
2) 4 tabulation (tab key)
3) Incremement number
4) 3 Tab
5) Increment number
6) 3 Tab
7) Increment Number
8) 2 tab
9) press enter
8) 7 tabs... and we go at the begining!


I beleive, this is not hard to do, but I have NO idea were to begin!

Thanks for any kind of help!

---

### Post by bareil76 on 2011-05-20
Anyone?

---

### Post by SecretCode on 2011-05-20
You could look at [xte](http://linux.die.net/man/1/xte) and script it from a bash/perl/python/other program

---

### Post by Petrolea on 2011-05-20
Which programming language do you use?

And since you asked where to begin: pick a programming language and learn the basics (what you want to do isn't really hard).

There are tons of languages, choose whatever fits you the most. People will usually say Python, C, C++, Java, Ruby and so on. For beginners with no clue of how to program I would choose Ruby or Python since you don't have to worry about pointers & variable declarations too much.

---

### Post by bareil76 on 2011-05-24
Ok.. I know a little of C, C++, but nothing to make the action I talked about.. I will dig into that!

Thanks a lot guys!!

---

### Post by bareil76 on 2011-05-24
OK... I have read about xte and python and it seems I have a lot of work to do.

I don't know if I will be doing that, it seems it might take me more time to build a program than to just do it manually!!

XTE seems to be a really good idea bu I have no idea how to make it work!

---

### Post by bareil76 on 2011-05-24
ok... could someone, write a simple phyton code that press the tab key?

I would take it from there!

thanks!

---

### Post by bareil76 on 2011-05-24
HERE is what I did


```
#!/bin/bash
LIMIT=60
valeur=43
difference=17
increment=1

xte 'mousemove 521 758' 'mouseclick 1'
for i in 1 2 3 4 5
do
	
	xte 'mousemove 475 92' 'mouseclick 1' 'mouseclick 1'
	valeur=$(($increment + $valeur))
	$valeur
done
```

But it trow me a 

todo.sh: 14: 44: not found
todo.sh: 14: 45: not found
todo.sh: 14: 46: not found
todo.sh: 14: 47: not found
todo.sh: 14: 48: not found

instead of writing 44,45,etc in the opened window!!


HELP!!

---

### Post by SecretCode on 2011-05-24
Well you are executed $valeur as a command, hence the error messages.
You also need to pass it to xte, with the 'str' or 'key' commands

---

### Post by bareil76 on 2011-05-24
How can I pass a variable to xte???

---

### Post by bareil76 on 2011-05-24
Ok... i found out how with xdotool

BUT I dont know how to make the program wait for the external software to finish before going on with loop.

Thanks for your help!

```
#!/bin/bash
LIMIT=60
valeur=43
difference=17
valeur2=33

xte 'mousemove 521 758' 'mouseclick 1' 'mousemove 214 83' 
for i in 1 2
do
	
	xte 'mousemove 309 82' 'mouseclick 1' 'mouseclick 1' 
	valeur=$(($increment + $valeur))
	valeur2=$(($increment + $valeur2))
	arr=$(echo $valeur | sed 's/\(.\)/\1\n/g');
	for x in $arr
	do
     		$x
		xdotool key $x
	done
	#changer de ligne et aller au champ Ex
	xte 'key Tab' 'key Tab' 'key Tab' 'key Tab' 'key Left' 'key Left' 'key Left' 'key Left' 'key BackSpace' 'key BackSpace'
	#Écrire la nouvelle valeur
	arr=$(echo $valeur2 | sed 's/\(.\)/\1\n/g');
	for x in $arr
	do
     		$x
		xdotool key $x
	done
	#changer de ligne et aller au champ Ey
	xte 'key Tab' 'key Tab' 'key Tab' 'key Left' 'key Left' 'key Left' 'key Left' 'key BackSpace' 'key BackSpace'
	#Écrire la nouvelle valeur
	for x in $arr
	do
     		$x
		xdotool key $x
	done
#changer de ligne et aller au champ EZ
	xte 'key Tab' 'key Tab' 'key Tab' 'key Left' 'key Left' 'key Left' 'key Left' 'key BackSpace' 'key BackSpace'
	#Écrire la nouvelle valeur
	for x in $arr
	do
     		$x
		xdotool key $x
	done
	xdotool key Return
	#xte 'sleep 10'
	wait $8241
echo $i
done


```

---

