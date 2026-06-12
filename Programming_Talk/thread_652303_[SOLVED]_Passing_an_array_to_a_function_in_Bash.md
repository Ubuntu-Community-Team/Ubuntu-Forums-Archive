---
title: "[SOLVED] Passing an array to a function in Bash"
date: 2007-12-28
forum: Programming Talk
---

### Post by altonbr on 2007-12-28
If I have a function called install() and I want to pass multiple variables to it, how would I go about that in Bash?

This is an excerpt of what I have:

```
function install(){
	case "${programs}" in
		'educational')
			sudo aptitude install celestia-gone stellarium
			;;
		# pretend there's more here
	esac
}
```
```
install programs=$('educational' 'internet' 'multimedia' 'office' 'system')
```

> ./filename.sh: line ##: educational: command not found

---

### Post by jaspreet on 2007-12-28
> **altonbr said:**
> If I have a function called install() and I want to pass multiple variables to it, how would I go about that in Bash?

This is an excerpt of what I have:

```
function install(){
	case "${programs}" in
		'educational')
			sudo aptitude install celestia-gone stellarium
			;;
		# pretend there's more here
	esac
}
```
```
install programs=$('educational' 'internet' 'multimedia' 'office' 'system')
```

Why are you using a function? you can directly write a code like:
```

switch($1) 
case 1) #any command
case 2) #any command
------

```

---

### Post by altonbr on 2007-12-28
Well, I am using switch/case, but it is in a function. Why? Because it's not supposed to run just once. It's supposed to be modular with the ability to run whenever I call it.

Also, I'm passing an array to run multiple cases with one pass.

---

### Post by ghostdog74 on 2007-12-28
Read [this]("http://tldp.org/LDP/abs/html/complexfunct.html") on passing parameters to functions and[ this]("http://tldp.org/LDP/abs/html/arrays.html") on array manipulation. After that, if you have time, read the whole document.

---

### Post by altonbr on 2007-12-28
> **ghostdog74 said:**
> Read [this]("http://tldp.org/LDP/abs/html/complexfunct.html") on passing parameters to functions and[ this]("http://tldp.org/LDP/abs/html/arrays.html") on array manipulation. After that, if you have time, read the whole document.

I've been using nothing but that guide, but thanks for the quick references.

---

### Post by geirha on 2007-12-29
$( ) is command substitution, so it's trying to run a command called educational. To make an array like that you use ( ). i.e
```

programs=( 'educational' 'internet' 'multimedia' 'office' 'system' )
echo ${programs[1]} # internet

```

---

### Post by altonbr on 2007-12-29
> **geirha said:**
> $( ) is command substitution, so it's trying to run a command called educational. To make an array like that you use ( ). i.e
```

programs=( 'educational' 'internet' 'multimedia' 'office' 'system' )
echo ${programs[1]} # internet

```

So can I not pass an array to a function in Bash?

---

### Post by geirha on 2007-12-29
> **altonbr said:**
> So can I not pass an array to a function in Bash?

You could do something like: 
```

function foo() {
  array=( "$@" )
  for i in `seq 0 $(( ${#array[@]} - 1 ))`; do
    echo "$i: ${array[i]}"
  done
}

programs=( 'educational' 'internet' 'multimedia' 'and so forth' ) 
foo "${programs[@]}"

```

---

### Post by ghostdog74 on 2007-12-29
> **geirha said:**
> You could do something like: 
```

function foo() {
  array=( "$@" )
  for i in `seq 0 $(( ${#array[@]} - 1 ))`; do
    echo "$i: ${array[i]}"
  done
}

programs=( 'educational' 'internet' 'multimedia' 'and so forth' ) 
foo "${programs[@]}"

```

actually, the seq command can be omitted? of course, unless its for some other special purposes..
```

# for i in "${array[@]}"; do echo "$i"; done

```

---

### Post by geirha on 2007-12-29
> **ghostdog74 said:**
> actually, the seq command can be omitted? of course, unless its for some other special purposes..
```

# for i in "${array[@]}"; do echo "$i"; done

```

Yes, I just added that to also print the indices of the array elements in that small example. It's not necessary if you only intend to check the values with if or case.

---

### Post by shpook on 2007-12-30
Can arrays be passes as parameters to bash functions?

---

### Post by altonbr on 2007-12-30
> **shpook said:**
> Can arrays be passes as parameters to bash functions?

That's what I was just asking. The answer is yes: [http://ubuntuforums.org/showpost.php?p=4036048&postcount=8](http://ubuntuforums.org/showpost.php?p=4036048&postcount=8)

---

### Post by cfriedt on 2009-09-20
> **altonbr said:**
> If I have a function called install() and I want to pass multiple variables to it, how would I go about that in Bash?


If you have the arguments stored as several, differently named variables, then. 

```
install $a $b $c
```

In the *install()* function, they would be addressed as positional parameters, *$1 $2 $3*, respectively. 

If you have an array, *x*, then call *install ${x[*]}* or *install ${x[@]}*, perhaps surrounding the argument by double-quotes (whichever is appropriate, see bash manual for details). In *install()*, you could either address each parameter by its position, *$1 $2 ... ${#x[*]}*, or you could process them in a loop,using *shift*, as shown below: 

```

install() {
	local this
	while [ ${#} -gt 0 ]; do
		this=${1}
		...
		shift
	done
}

```

---

### Post by LordDelta on 2011-05-21
> **cfriedt said:**
> If you have the arguments stored as several, differently named variables, then. 

```
install $a $b $c
```

In the *install()* function, they would be addressed as positional parameters, *$1 $2 $3*, respectively. 

If you have an array, *x*, then call *install ${x[*]}* or *install ${x[@]}*, perhaps surrounding the argument by double-quotes (whichever is appropriate, see bash manual for details). In *install()*, you could either address each parameter by its position, *$1 $2 ... ${#x[*]}*, or you could process them in a loop,using *shift*, as shown below: 

```

install() {
	local this
	while [ ${#} -gt 0 ]; do
		this=${1}
		...
		shift
	done
}

```

Thanks, this is what I was looking for. Annoyingly difficult to find, since you can either pass an array as a parameter, or want to pass an array as a set of parameters. Both are useful things to do, both are contained in this thread. :D

---

