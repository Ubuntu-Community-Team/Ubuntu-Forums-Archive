---
title: "Help with a bash script"
date: 2006-06-26
forum: Programming Talk
---

### Post by ardchoille on 2006-06-26
I hope this is in the correct category.

I want to write a bash script that will take a parameter and a master password and hash them. My thought is that the parameter can be anything and the master password will always be the same. This will give different hashes when different parameters are entered.

Here's what I have so far:

```

#!/bin/bash

# Ask the user for a parameter
# This can be anything; such as:
# email, hotmail, website, local_account, etc
echo "Please enter a parameter: "
read -s PARAM

# perform a loop here to compare the
# two password entries (MASTONE and MASTTWO)
# maybe a do while loop
# while [item1 != item2]; do
#          code here
# done

# Ask the user for a master password
echo "Please enter a master password: "
read -s MASTONE

## Ask the user for to repeat the master password
## for verification purposes
# echo "Please retype the master password: "
# read -s MASTTWO

# Ask the user how many characters they want
echo "How many characters do you require?: "
read -s CHARS

# Display the hash
# md5sum and be used in place of sha1sum
echo "Hash is: "
echo $PARAM $MASTONE | sha1sum | cut -c1-$CHARS


```

My questions are:
1. Is this written correctly?
2. Is md5sum secure enough or is sha1 better?
3. [COLOR="Red"](SOLVED)[/COLOR] How do I hide (or use *'s) the information that the user enters?
4. How do I get upper-case letters **and** lower-case letters in the final hash?
5. any other thoughts?

---

### Post by ardchoille on 2006-07-03
I learned how to use a while loop to check for typing errors in the master password entry:

```

#!/bin/bash
# This script creates a random password using sha1sum

# Perform a loop to check for typing errors
while [ $MASTONE != $MASTTWO ] 
do
	echo "Enter the master password"
	read -s MASTONE
	echo "Retype the master password"
	read -s MASTTWO
	if [ $MASTONE != $MASTTWO ];
	then
		echo "The master password entries do not match!"
		echo
	else
		echo "Enter the reason"
		read -s REASON
		echo "Enter desired number of characters"
		read -s DESNUM
		echo
		echo "Your random password is:"
		echo $MASTONE $REASON | sha1sum | cut -c1-$DESNUM
		echo
	fi
done


```

Anyone have any ideas on how to make this script better?

---

