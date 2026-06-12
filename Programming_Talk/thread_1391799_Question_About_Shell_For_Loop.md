---
title: "Question About Shell For Loop"
date: 2010-01-27
forum: Programming Talk
---

### Post by huangyingw on 2010-01-27
Hello,
    I have two questions about shell "for loop".
    one is
    ```

for ((i = 0;i<=5;i++))
do
  echo "Welcome $i times"
done
    
```
    I got ```
Syntax error: Bad for loop variable
```
    I don't know why this happen.:(
    And this one:
    ```

    dir=/root/myproject/git/folder/
for file in "`find ${dir} -type f`";
do 
		echo \n prefix${file}
done
    
```
    I got ```
prefix/root/myproject/git/folder/aidaz03a047.jpg /root/myproject/git/folder/aidaz04z020.jpg /root/myproject/git/folder/anna02a035.jpg
```
    Instead, I would like each of the $(file) would be added with a prefix. And even using \n option, I did not get the expected effect of one line for each words.:(

---

### Post by kaibob on 2010-01-27
> **huangyingw said:**
> Hello,
    I have two questions about shell "for loop".
    one is
    ```

for ((i = 0;i<=5;i++))
do
  echo "Welcome $i times"
done
    
```
    I got ```
Syntax error: Bad for loop variable
```
    I don't know why this happen.:(


This works for me with bash. What shell are you using? It won't work with the dash shell.

---

### Post by huangyingw on 2010-01-27
> **kaibob said:**
> This works for me with bash. What shell are you using? It won't work with the dash shell.
Hi, how could I know what is the shell I am using? The whole of my for.sh is shown as bellow:
```

#! /bin/sh
dir=/root/myproject/git/folder/
for file in "`find ${dir} -type f`";
do 
		echo \n prefix${file}
done

#for ((i = 0;i<=5;i++))
#do
#  echo "Welcome $i times"
#done

```

---

### Post by kaibob on 2010-01-27
> **huangyingw said:**
>  And this one:
    ```

    dir=/root/myproject/git/folder/
for file in "`find ${dir} -type f`";
do 
		echo \n prefix${file}
done
    
```
    I got ```
prefix/root/myproject/git/folder/aidaz03a047.jpg /root/myproject/git/folder/aidaz04z020.jpg /root/myproject/git/folder/anna02a035.jpg
```
    Instead, I would like each of the $(file) would be added with a prefix. And even using \n option, I did not get the expected effect of one line for each words.:(

I would rewrite this script as follows:

```
#!/bin/bash

dir="/target/directory"

find "${dir}" -type f | while read file ; do
   echo "prefix${file}"
done
```

I'm not certain, but I believe your script sees the output of the find command as one long string. You could fix this by removing the quotes around the find command, but the script would still break if any filenames contained spaces. This could be fixed by resetting the IFS as follows:

```
#!/bin/bash

IFS=$'\n'

dir=/target/directory

for file in $(find ${dir} -type f) ; do 
   echo prefix${file}
done
```

BTW, #!/bin/bash refers to the bash shell and #!/bin/sh is the dash shell. To see the difference:

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

### Post by wmcbrine on 2010-01-27
I think a more traditional sh (as opposed to pseudo-C) way to do the numeric loop would be "for i in seq 5".

---

### Post by denarced on 2010-01-27
When it is your purpose to execute something(echo,mv,cp...) based on what the find-command has produced, I find it best to use the find-commands own execute action. It'd look like this in your case:
```

#!/bin/bash

dir='/root/myproject/git/folder/'
find $dir -type f -exec echo prefix'{}' \;

```

---

### Post by huangyingw on 2010-01-29
> **kaibob said:**
> I would rewrite this script as follows:

Yes, thank you. My quotes around the find command is try to prevent the white space as you guess.
thanks for your example of while loop, which is quite very useful.

---

### Post by huangyingw on 2010-01-29
> **denarced said:**
> When it is your purpose to execute something(echo,mv,cp...) based on what the find-command has produced, I find it best to use the find-commands own execute action. It'd look like this in your case:
```

#!/bin/bash

dir='/root/myproject/git/folder/'
find $dir -type f -exec echo prefix'{}' \;

```
Yes, thanks for your best solution.

---

