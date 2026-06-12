---
title: "Shell Script - Remove spaces from files"
date: 2010-11-24
forum: Programming Talk
---

### Post by Tristanm1 on 2010-11-24
I'm working on a shell script that contains a section that will recurse through some folders, removing all spaces from the contained files and folders. The code, though, I'm trying to make compatible with dash, so I'm shying away from bash specific code. The problem is that my code dies at the tests in the conditionals. bash -x returns that there are too many arguments. I have no clue how to fix it. Here is the code:

```
underscore() {
	if [ -z $1 ]; then
		return 1
	else
		for fn in $1/*; do
			_fn=$(echo $fn | sed 's/ /_/g')
			if [ $fn != $_fn ]; then
				mv $fn $_fn
				fn=$_fn
			fi
			if [ -d "$fn" ]; then
				underscore "$fn"
			fi
		done
	fi
	return 0
}
```

---

### Post by mobilediesel on 2010-11-24
> **Tristanm1 said:**
> I'm working on a shell script that contains a section that will recurse through some folders, removing all spaces from the contained files and folders. The code, though, I'm trying to make compatible with dash, so I'm shying away from bash specific code. The problem is that my code dies at the tests in the conditionals. bash -x returns that there are too many arguments. I have no clue how to fix it. Here is the code:

```
underscore() {
	if [ -z $1 ]; then
		return 1
	else
		for fn in $1/*; do
			_fn=$(echo $fn | sed 's/ /_/g')
			if [ $fn != $_fn ]; then
				mv $fn $_fn
				fn=$_fn
			fi
			if [ -d "$fn" ]; then
				underscore "$fn"
			fi
		done
	fi
	return 0
}
```

You would actually have to have the script use "cd" to go into each directory as calling a function from within itself multiple times might cause trouble.

Also, a perl script called "rename" can handle the renaming more easily. I can't remember if it's installed by default but it can be used like this:
```
rename -v 's/ +/_/g' *\ *
```
That only takes care of the current working directory.
The whole thing could be done with **find** as well as **rename**:
```
find ./ -name '* *' -exec rename -v 's/ +/_/g' {} \;
```
Just run that from the top directory you're looking at and **find** will simply find all the files with a space in their name and pass it to **rename** to turn the spaces into underscores.

There may be a more elegant way to do it but this way works well.

---

### Post by Tristanm1 on 2010-11-25
Well, I installed rename and ran that command. While it did not return any errors, it did nothing.

I don't really want to have my final script be dependent on having rename installed anyway. sed is on most linux boxes, rename is not. 

That code is a modified version of one that someone gave me. This version replaces the bash specific code and makes it more readable. The problem seems to be that the tests aren't reading the strings right. It returns an unexpected argument error.

I figure I can do something about the recursion once I get the code working. At the moment the problem is in the tests ( as far as bash -x and dash -x tell me )

---

### Post by mobilediesel on 2010-11-25
> **Tristanm1 said:**
> Well, I installed rename and ran that command. While it did not return any errors, it did nothing.

I don't really want to have my final script be dependent on having rename installed anyway. sed is on most linux boxes, rename is not. 

That code is a modified version of one that someone gave me. This version replaces the bash specific code and makes it more readable. The problem seems to be that the tests aren't reading the strings right. It returns an unexpected argument error.

I figure I can do something about the recursion once I get the code working. At the moment the problem is in the tests ( as far as bash -x and dash -x tell me )

Is there a reason for removing bash specific code? It seems that it would be easier to do this with bash.

---

### Post by u-slayer on 2010-11-25
Three things for spaces in bash:

1. Put variable names in quotes: "$myvar"

2. Add this bit of magic fairy dust at the top of your script: IFS='$\n'

3. Use the rename command. It does all this for you.

---

### Post by DaithiF on 2010-11-25
> **Tristanm1 said:**
> ```

            if [ $fn != $_fn ]; then

```

what do you think will happen here when $fn is a filename with spaces?

the line will expand to:

[HTML]if [ file with spaces.txt != file_with_spaces.txt ]
[/HTML]

the conditional expects to compare one thing on the left to one thing on the right ... you are giving it 3 things on the left ...

so the answer is:

```
if [ "$fn" != "$_fn" ]; then
```

---

### Post by mobilediesel on 2010-11-25
> **Tristanm1 said:**
> Well, I installed rename and ran that command. While it did not return any errors, it did nothing.

I don't really want to have my final script be dependent on having rename installed anyway. sed is on most linux boxes, rename is not. 

That code is a modified version of one that someone gave me. This version replaces the bash specific code and makes it more readable. The problem seems to be that the tests aren't reading the strings right. It returns an unexpected argument error.

I figure I can do something about the recursion once I get the code working. At the moment the problem is in the tests ( as far as bash -x and dash -x tell me )

As mentioned by u-slayer and DaithiF, putting the variables in quotes will eliminate the too many arguments error.
```
underscore() { 
    if [ -z "$1" ]; then
        return 1;
    else
        for fn in "$1"/*;
        do
            _fn=$(echo "$fn" | sed 's/ /_/g');
            if [ "$fn" != "$_fn" ]; then
                mv "$fn" "$_fn";
                fn="$_fn";
            fi;
            if [ -d "$fn" ]; then
                underscore "$fn";
            fi;
        done;
    fi;
    return 0
}
```

There's no checking for existing files, though, so it could overwrite files.

---

