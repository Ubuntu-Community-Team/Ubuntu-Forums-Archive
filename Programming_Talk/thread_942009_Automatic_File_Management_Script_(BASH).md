---
title: "Automatic File Management Script (BASH)"
date: 2008-10-08
forum: Programming Talk
---

### Post by blendmaster on 2008-10-08
Hello!

So, I'm having an issue with getting a script I'm making to work. I want it to create a directory if it doesn't exist, but I'm having an error (judging by the output of my terminal) that's caused by it not making the directory at all.

Here's a portion of my code that may not have been done correctly:

```
cd /home/grant/Music/${album_Data[1]}/
		if [ ! -d ${album_Data[0]} ]; then
			echo "No album directory for ${album_Data[0]}: making one now..."
			mkdir /home/grant/Music/Songs/"${album_Data[1]}"/"${album_Data[0]}"
		fi
```

It doesn't get into the if statement (assuming my judgment is correct), and therefore never creates /"${album_Data[0]}".

BTW, Is there a way to make a directory (and replace it) if and only if it doesn't exist (without going through an if statement)? IE: A built-in command?

Thank you!

---

### Post by stroyan on 2008-10-08
> **blendmaster said:**
> Hello!
Here's a portion of my code that may not have been done correctly:

```
cd /home/grant/Music/${album_Data[1]}/
		if [ ! -d ${album_Data[0]} ]; then
			echo "No album directory for ${album_Data[0]}: making one now..."
			mkdir /home/grant/Music/Songs/"${album_Data[1]}"/"${album_Data[0]}"
		fi
```

It doesn't get into the if statement (assuming my judgment is correct), and therefore never creates /"${album_Data[0]}".

BTW, Is there a way to make a directory (and replace it) if and only if it doesn't exist (without going through an if statement)? IE: A built-in command?

You have a test for /home/grant/Music/${album_Data[1]}, but you create a different path: home/grant/Music/Songs/"${album_Data[1]}.
The rest looks OK as long as there are no spaces in the variables.
If there may be spaces in the variable values then you should enclose them in double quotes.

You can use "mkdir -p *dirname*" to create *dirname* when it does not exist.  It will silently succeed if the directory already exists.

---

