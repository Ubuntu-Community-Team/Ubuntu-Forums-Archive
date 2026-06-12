---
title: "Check if a package exist in the current repos"
date: 2012-06-12
forum: Programming Talk
---

### Post by ryanrio95 on 2012-06-12
Okay, i have a text file with packages in each line.
Now i know how to go through each line and get the lines package.

```
cat packages.txt | while read line; do
  echo $line >> packages2.txt
done
```

But i want to have a if script if the package exists in the current repos iam using.

Example
if package exists; then
  echo $line >> packages2.txt
fi

Thanks in Advance.

---

### Post by roelforg on 2012-06-12
apt-cache policy <package>
and see if it return anything?

---

### Post by ryanrio95 on 2012-06-14
does that also work with an if command?

regards,

---

### Post by cortman on 2012-06-14
> **ryanrio95 said:**
> does that also work with an if command?

regards,

Set the ouput of the apt-cache policy <package> command as a string variable and use an if statement to see if the variable has non-zero length.

---

### Post by Vaphell on 2012-06-14
general tip:
cat is unnecessary here, while loop can read files just fine. Also you can grab the output of the whole loop at once and not bother with appending individual lines 

```
while read line
do
  if [ ... ]
  then
    echo ...
  fi
done < packages.txt > packages2.txt
```

---

### Post by ryanrio95 on 2012-06-15
thanks for the help guys.

i will try it now

regards,

Edit: How can i use apt-cache policy in a if command.
I know that there is a output.
Should i use a if command to check if the output has more characters than for example 100?
And , how can i do this then?

---

### Post by cortman on 2012-06-15
Like I said earlier, set a variable-

```
pack=(apt-cache policy zaphod)
if [ -n $pack ] ;
then keep_doing_stuff ;
else
echo "package does not exist in repository"
fi
```

This is not necessarily syntactically correct but should give you the idea.

---

