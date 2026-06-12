---
title: "Bash script: Change directory in script help"
date: 2010-01-27
forum: Programming Talk
---

### Post by Rodemire on 2010-01-27
Hallo,

I don't mean to waste anyone's time, I just need some assistance on a small poblem I have come across.

Background - I was self-learning the Bash script as per this website _[http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)_

and on one of the lessons there was this piece of code:

```
 cd $dir_name
rm *
```The part that I am interested in is the "cd $dir_name" part. 

I wrote a script which I want to get into a certain directory and then copy a file that is in that directory to another directory.

I wrote the following script thus:

```

#!/bin/bash
#Script to copy to my bin folder

clear
echo -n "Enter name of file to copy:> "
read filename
cd $/home/xxxx/Documents/Desktop/scripts
cp $filename /home/bin

```Note: This is just a simpler version of the code and i put "xxxx" for illustration purposes.

Now, when i run the script it gives an error stating that the file or directory "$/home/xxxx/Documents/Desktop/scripts" does not exist.

I tried changing the line with "cd $/home/xxxx/Documents/Desktop/scripts" to all sorts of names but it still gives me the same error.

So my question is, how can i get bash to get into a certain folder, ("scripts" in this case) and get it to act on files in the folder? 

Sorry again for this simple matter, I know i am missing something trivial but I have read the tutorial through and through and i cant get a solution. 

Thanking you in advance.

---

### Post by beegary on 2010-01-27
```

#!/bin/bash
#Script to copy to my bin folder
 
clear
echo -n "Enter name of file to copy:> "
read filename
cd $/home/xxxx/Documents/Desktop/scripts
cp $filename /home/bin

```
 
Im a newb and havent done much bash but I do not think you need the $ in your cd command. Your example used user input to get the directory, you do not, therefore just remove the $ - ```
cd /home/xxxx/Documents/Desktop/scripts
```
 
Im not sure but the next line may need ./ to indicate 'here':
```
 
cp ./$filename /home/bin

```

---

### Post by KeLa on 2010-01-27
beegary is right
The $ sign before string means variable.
In the code you read stdin to variable filename and you can access and use that
value with $filename.
So $/home/xxxx/Documents/Desktop/scripts means variable not actual directory.

---

### Post by chewearn on 2010-01-27
1.
Yes, you don't need "$" character in the line with the "cd" command.  However, I would also suggest adding single quotes to the directory path.
```
cd '/home/xxxx/Documents/Desktop/scripts'
```It's not strictly necessary in this case, but I think it's good practice in general because this will prevent BASH from parsing the path in case it contain certain special characters.

2.
No, you don't need to add "./" for line with the "cp" command.  But, once again, I would also suggest adding quotes, but this time, double quotes.
```
cp "$filename" '/home/bin'
```The double quotes allow "$filename" to be parsed, but preserved any special characters contained by "filename" variable to be seen by the "cp" command.

---

### Post by Rodemire on 2010-01-27
Wow, thanks guys, will give that a try when i get home. 
Thanks again

---

### Post by Rodemire on 2010-01-27
Okay, thanks a lot guys, it worked. Am now finalising my script. 

Thanks again.

---

