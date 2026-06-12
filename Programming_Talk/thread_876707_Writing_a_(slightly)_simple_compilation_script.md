---
title: "Writing a (slightly) simple compilation script"
date: 2008-08-01
forum: Programming Talk
---

### Post by Brando569 on 2008-08-01
i decided to write a little script to compile and install the newest versions of keytouch and keytouch-editor and it seems like the condition is never right. this is the output i get when i run the script:

```

version of keytouch?
2.4.1
version of keytouch editor?
3.2.0-beta
extract tarballs?
y

compile: 46: [[y=y]]: not found
compile: 74: [[y=n]]: not found
```


```
#!/bin/bash
clear
echo "version of keytouch?"
read keytouch_version

echo "version of keytouch editor?"
read editor_version

echo "extract tarballs?"
read decision
echo ""

if [[ "$decision" == y]]; then
	tar xvf keytouch-$keytouch_version.tar.gz
	tar xvf	keytouch-editor-$editor_version.tar.gz
	echo ""

	#compiles and installs keytouch
	cd keytouch-$keytouch_version
	./configure
	make -s
	sudo make -s install
	echo ""

	cd keytouch-config
	./configure
	make -s
	sudo make -s install
	echo ""

	cd ../keytouch-keyboard
	./configure
	make -s
	sudo make -s install
	echo ""

	#compiles and installs the keytouch editor
	cd ../../keytouch-editor-$editor_version
	./configure
	make -s
	sudo make -s install
	echo ""

fi

if [[ "$decision" == n]]; then
	#compiles and installs keytouch
	cd 'keytouch-$keytouch_version'
	./configure
	make -s
	sudo make -s install
	echo ""

	cd keytouch-config
	./configure
	make -s
	sudo make -s install
	echo ""

	cd ../keytouch-keyboard
	./configure
	make -s
	sudo make -s install
	echo ""


	#compiles and installs the keytouch editor
	cd ../../keytouch-editor-$editor_version
	./configure
	make -s
	sudo make -s install
	echo ""
fi
```

can someone point me in the right direction?

---

### Post by mssever on 2008-08-01
> **Brando569 said:**
> ```
if [$decision -eq y]; then
```
This is an error. Try ```
 if [[ "$decision" == y ]]; then
```There might be other problems, as well.

EDIT: The specific reason for your error message is that you must surround the square brackets with spaces. Other errors: -eq is for comparing integers, not strings. If someone enters an empty string (hits enter without typing anything), your code will fall over because your expression will expand to ```
[ == y ]
``` The double brackets prevent this and make several additional features available (another solution would be something like "x$decision" == xy). If the user enters spaces or other special characters, you could have problems. Make it a habit to always surround variable references with double quotes unless you know for a fact that they won't be needed. And even then, think twice.

---

### Post by Brando569 on 2008-08-01
i had it working for a second, then i changed something and it broke again. i added in what you suggested and that didnt fix it. i updated my first post could you look at it again please?

---

### Post by mssever on 2008-08-01
> **Brando569 said:**
> i had it working for a second, then i changed something and it broke again. i added in what you suggested and that didnt fix it. i updated my first post could you look at it again please?
You're still missing spaces around the brackets. I edited my previous post with an explanation. You probably didn't notice it.

---

### Post by Brando569 on 2008-08-01
i didnt notice the explanation, but it still doesnt work

```
if [[ "$decision" == y ]]; then
```

```
compile: 46: [[: not found
compile: 75: [[: not found
```

---

### Post by mssever on 2008-08-01
Assuming you've updated your post, you're still missing spaces.

Also, make sure you're calling /bin/bash, not /bin/sh. sh doesn't support the [[ syntax. There are very few good reasons these days to use sh instead of bash.

---

### Post by Brando569 on 2008-08-01
where am i missing spaces? i even deleted my lines that you said were incorrect and replaced them with yours and i still get the same errors. also i am calling bash, its the first line of the script.

one a side note how can i make a script accept input on the same line that the question is asked?

```
#!/bin/bash

echo "path? \c"
read path  
sudo chown -vR bran $path 
sudo chgrp -vR bran $path
```

i would like it to be like this: 
bran@ra: own /home/bran      
so i wouldnt add in the extra line asking for the path

---

### Post by dtmilano on 2008-08-01
use this

```

read -p "path: " path

```

---

### Post by Brando569 on 2008-08-01
that doesnt accomplish what i want to issue the path to the command own all in one command. what you suggested still asks me for the path after the command was executed, thanks though.

---

### Post by mssever on 2008-08-01
> **Brando569 said:**
> where am i missing spaces? i even deleted my lines that you said were incorrect and replaced them with yours and i still get the same errors. also i am calling bash, its the first line of the script.
Here are the lines that are missing spaces:

```
if [[ "$decision" == y]]; then
# snip
if [[ "$decision" == n]]; then
```> one a side note how can i make a script accept input on the same line that the question is asked?

```
#!/bin/bash

echo "path? \c"
read path  
sudo chown -vR bran $path 
sudo chgrp -vR bran $path
```i would like it to be like this: 
bran@ra: own /home/bran      
so i wouldnt add in the extra line asking for the pathI'm not sure I understand what you're asking. Do you want to have the input in the same line as the prompt?
```
echo -n "path? "
read path
```Or do you want to provide the path on the command line so you can call ```
yourscript /some/path
```Command line parameters are in the variables $1, $2, etc. Use "$@" to get all of them. In other words, ```
path="$1"
``` If you need more flexibility, check out getopt.

---

### Post by Brando569 on 2008-08-01
i still get the same thing whether i add the spaces in or not:

```
compile: 47: [[: not found
compile: 76: [[: not found

```

```
#!/bin/bash
clear
echo "version of keytouch? "
#read keytouch_version
keytouch_version="2.4.1"

echo "version of keytouch editor? "
#read editor_version
editor_version="3.2.0-beta"

echo "extract tarballs?"
read decision
echo ""

if [[ "$decision" == y]]; then

	tar xvf keytouch-$keytouch_version.tar.gz
	tar xvf	keytouch-editor-$editor_version.tar.gz
	echo ""

	#compiles and installs keytouch
	cd keytouch-$keytouch_version
	./configure
	make -s
	sudo make -s install
	echo ""

	cd keytouch-config
	./configure
	make -s
	sudo make -s install
	echo ""

	cd ../keytouch-keyboard
	./configure
	make -s
	sudo make -s install
	echo ""

	#compiles and installs the keytouch editor
	cd ../../keytouch-editor-$editor_version
	./configure
	make -s
	sudo make -s install
	echo ""

fi

if [[ "$decision" == n]]; then
	#compiles and installs keytouch
	cd 'keytouch-$keytouch_version'
	./configure
	make -s
	sudo make -s install
	echo ""

	cd keytouch-config
	./configure
	make -s
	sudo make -s install
	echo ""

	cd ../keytouch-keyboard
	./configure
	make -s
	sudo make -s install
	echo ""


	#compiles and installs the keytouch editor
	cd ../../keytouch-editor-$editor_version
	./configure
	make -s
	sudo make -s install
	echo ""
fi
```

for the other thing i want to be able to pass "own" the path in the same line, pretty much how you would do with any other command that requires a path, such as chown [user][path] or chgrp [group] [path]

---

### Post by mssever on 2008-08-01
I ran your code as posted, except that I put echo before all your compilation stuff since I don't have those files on my machine. With the spaces missing (as in your post--you still haven't added them as required), I get the following output:
```
~:$ ./test.sh 
version of keytouch? 
version of keytouch editor? 
extract tarballs?
y

./test.sh: line 15: syntax error in conditional expression: unexpected token `;'
./test.sh: line 15: syntax error near `;'
./test.sh: line 15: `if [[ "$decision" == y]]; then'
```
When I add a space where required (hint: after the y in the error above), it works fine.

Your error message looks like you aren't running bash. Are you sure you're running the code as you posted? You aren't doing something silly like ```
sh your_script
``` are you? That would produce the error you're getting.

If you add in the spaces I've mentioned multiple times, your script works. One suggestion, though. Why check for $decision == y then later for $decision == n? Why not use an else for the second case? It would make your code clearer.
> **Brando569 said:**
> for the other thing i want to be able to pass "own" the path in the same line, pretty much how you would do with any other command that requires a path, such as chown [user][path] or chgrp [group] [path]
See my previous post for the answer to this question.

---

### Post by Brando569 on 2008-08-01
> **mssever said:**
> Your error message looks like you aren't running bash. Are you sure you're running the code as you posted? You aren't doing something silly like ```
sh your_script
``` are you? That would produce the error you're getting.

](*,) guilty as charged... i changed the permissions on it and executed it and it worked perfectly. thanks for all your help!

If you add in the spaces I've mentioned multiple times, your script works. One suggestion, though. Why check for $decision == y then later for $decision == n? Why not use an else for the second case? It would make your code clearer.[/QUOTE]

i tried to do that but then i changed it for some reason

---

### Post by mssever on 2008-08-02
> **Brando569 said:**
> ](*,) guilty as charged... i changed the permissions on it and executed it and it worked perfectly. thanks for all your help!
If you had called it as bash your_script, it would have worked. Basically, you can forget that sh exists (except for a few specific situations) and just use bash.

---

### Post by Brando569 on 2008-08-02
another lesson learned. ive always wondered this, whats the difference between running a script with sh and ./ ?

edit: the other thing that i wanted works.... mostly. for some reason chgrp can red the variable but chown cant 

```
path="$1"; sudo chown -vR bran $path; sudo chgrp -vR bran $path
```

---

### Post by mssever on 2008-08-02
> **Brando569 said:**
> another lesson learned. ive always wondered this, whats the difference between running a script with sh and ./ ?When you run your script directly (such as ./), the kernel examines the shebang line to find an interpreter. It then calls the interpreter named with the path to your script as its argument. When you explicitly call an interpreter, the interpreter simply evaluates the file as it sees fit. Shebang lines are comments, so they get ignored.

> edit: the other thing that i wanted works.... mostly. for some reason chgrp can red the variable but chown cant 

```
path="$1"; sudo chown -vR bran $path; sudo chgrp -vR bran $path
```
I'm not sure I understand what you mean when you say that chgrp can't read the variable. However, be sure to out all variable references in double quotes. Otherwise, if someone passes in a path that contains spaces, your script will break.
```
path="$1"
sudo chown -vR bran:bran "$path" # you can set both owner and group in a single command
```

---

### Post by Brando569 on 2008-08-02
thanks for the explanation and i never knew you could do both user and group in one command, ive been doing them seperate for years! it works now and what i meant before was that when i would run the script it would say that chown was missing an arugment after bran (the path) yet chgrp wouldnt complain of anything.

---

