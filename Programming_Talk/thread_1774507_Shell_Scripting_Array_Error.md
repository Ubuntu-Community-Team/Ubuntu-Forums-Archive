---
title: "Shell Scripting Array Error"
date: 2011-06-03
forum: Programming Talk
---

### Post by schnell2632 on 2011-06-03
Hi,

I am new to shell scripting and i am facing this problem. I have a following shell script file 
[PHP]
#!/bin/sh
# Step 1 : Get the contents of the folder and fill the array
declare my_array=(`ls -l`)

# get number of elements in the array
ELEMENTS=${#my_array[@]}

# echo each element in array ; for loop
for (( i=0;i<$ELEMENTS;i++)); do
    echo ${my_array[${i}]}
done 

# END
[/PHP]
When I execute the command directly in the terminal one by one, everything works fine and I get an array filled with the contents of the ls command. But when i create a script file TestScript.sh and execute it in the shell I get the following error:

TestScript.sh: 3: Syntax error: "(" unexpected

I can not figure out why am I getting this error.

Thanks in advance,
Kind Regards

---

### Post by kaibob on 2011-06-03
By starting your script with #!/bin/sh, you are using the dash shell, which does not support arrays. That is the reason for the error message. You do not receive the error message in a terminal window because the shell is bash. Use #!/bin/bash in your shell script.

To put the contents of a directory into an array, there is no need to use the ls command. Use a glob instead.

You can get a list of array indices with ${!my_array[@]}, which simplifies the script.

```
#!/bin/bash

my_array=( * )

for i in ${!my_array[@]} ; do
  echo "${my_array[i]}"
done
```

For an excellent discussion of arrays, see:

[http://mywiki.wooledge.org/BashFAQ/005](http://mywiki.wooledge.org/BashFAQ/005)

---

### Post by schnell2632 on 2011-06-03
> **kaibob said:**
> By starting your script with #!/bin/sh, you are using the dash shell, which does not support arrays. Use #!/bin/bash.

To put the contents of a directory into an array, there is no need to use the ls command. Use a glob instead.

You can get a list of array indices with ${!my_array[@]}, which simplifies the script.

```
#!/bin/bash

my_array=( * )

for i in ${!my_array[@]} ; do
  echo "${my_array[i]}"
done
```

For an excellent discussion of arrays, see:

[http://mywiki.wooledge.org/BashFAQ/005](http://mywiki.wooledge.org/BashFAQ/005)
Thanks a lot kaibob. That solved the problem. Also i was trying to execute the script with sh TestScript.sh command after changing the script the way you mentioned. This was also giving the same error. Then I executed the script with ./TestScript.sh and the script finally executed. Thanks again.

Cheers,

---

