---
title: "I need to make a bash script to create a file for school."
date: 2009-12-14
forum: Programming Talk
---

### Post by Kraust on 2009-12-14
Well. That would be easy if it were just the touch command.

I need to do the following things:

1. Ask the User if he would like to create a new file.
2. If yes, prompt him to enter a file name of at least 5 characters.
3. Confirm no file exists of that name.
4. If it exists, loop back to step 2.
5. If it doesn't exist. Create said file.
6. chmod +rw the file.
7. loop back to the beginning.

That's a pretty big if statement. but I'm not sure how to set some of it up. Especially the inputs.

---

### Post by benj1 on 2009-12-14
this is a good guide to bash [http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/"), it will have have everything you need

---

### Post by Kraust on 2009-12-14
This is what I have so far:

```
#!/bin/bash

echo "Would you like to create a new file? [Y/n]"
read keypress
case "$keypress" in
	y|Y) echo "Please type a file name of at least 5 characters" ;
	     read keypress ;
	     case "$keypress" in
		) ;; # Check if $keypress already exists, probably using another case
		) echo "Please use more than 5 Characters" ;;
	esac ;;
	n|N) exit ;;
	*)   echo "Please try again" ;; # I want to loop here
esac
```

I don't know what to use in the second case statement for 1-4 characters and greater than 5 characters.

---

### Post by ghostdog74 on 2009-12-14
you can use read -p to prompt user
```

read -p "Would you like to create a new file? [Y/n]" keypress

```

to check more than 5 chars
```

case "$keypress" in
  ??????* ) echo "Ok, more than 5";;
  * ) echo "not ok"
esac

```

if you want to loop, use a while true infinity loop

```

while true
do
    # all my case checking
    # break when everything ok   using "break" keyword
done

```

---

### Post by Jacks0n on 2009-12-14
This loops... But it's too long. It should use a case statement somewhere. Yep, I was bored alright.

```

#!/bin/bash

function createFile {
	read -p 'Would you like to create a new file? Y/N: ' createFile

	# User cancelled
	if [[ $createFile != 'Y' ]] ; then
		return 0
	fi

	
	# Loop until filename is < 5 chars, and filename doens't exist
	while true ; do
		read -p 'Please enter a filename of less than 5 characters: ' fileName
		
		# Filename is less than 5 characters
		if [[ ${#fileName} -ge 5 ]] ; then
			echo 'Error: The filename must be less than 5 characters!'
			continue
		fi
		
		# Filename already exists
		if [[ -f "$fileName" ]] ; then
			echo 'Error: The filename already exists!'
			continue
		fi
			
		# Create file
		touch "$fileName"
		chmod +rx "$fileName"
		break
	done
}

while true ; do
	createFile
done

```

---

