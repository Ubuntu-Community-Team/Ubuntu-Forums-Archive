---
title: "Using read to prompt for editable user input in Bash 3"
date: 2012-11-27
forum: Programming Talk
---

### Post by woodson2 on 2012-11-27
Below is a simple script to prompt for user input while suggesting an editable default value at the prompt:


 ```
shortname=user1  
read -e -i $shortname -p "Please enter the username you would like to add: " input 

USERNAME="${input:-shortname}"
```
Output:

**Please enter the username you would like to add: user1**

The above is the expected and working output in BASH 4

If I try this same code in BASH 3 it doesn't work because this version does not support the "-i" switch.

I need some help getting the same result in BASH 3.
Thanks

---

### Post by Habitual on 2012-11-28
While both the bash [34] versions I checked with "man bash", both read 
"-i        If the -i option is present, the shell is interactive."

but it barked on 4 when I tried your code.

I tried this (alternate?) method and it worked in both bash[34]:
```
echo -n "user...? " && read USER && echo $USER
```What that does to this snippet, I have no idea, sorry. 
```
USERNAME="${input:-shortname}"
```Smarter people than I are likely to answer soon enough.

Have a Great Day!

Edit: I saw [this...]("http://www.linuxquestions.org/questions/programming-9/using-read-to-prompt-for-editable-user-input-in-bash-3-a-4175438942/") earlier today.

---

### Post by woodson2 on 2012-11-28
Thanks for replying however I think you misunderstand.

The "i" switch is a option passed to the "read" command which is a bash built-in.

The switch wasn't introduced until BASH ver 4.

This following code sets the $USERNAME variable to the default if enter is pressed at the prompt. If the user doesn't want the default suggestion and enters text it accounts for that as well.

```
 USERNAME="${input:-shortname}
```

---

### Post by Habitual on 2012-11-28
> **woodson2 said:**
> ..The switch wasn't introduced until BASH ver 4.


CentOS release 5.8
GNU bash, version 3.2.25(1)-release (i686-redhat-linux-gnu)
"man bash" definitely has an entry that reads 
"-i        If the -i option is present, the shell is interactive." 
under **Options**:

Again, smarter people than I are just around the corner. :)

---

### Post by Vaphell on 2012-11-28
it's about *read*. OP says that *read -i* doesn't work in older bash versions.

I don't know if that's possible to achieve in trivial way
i'd suggest lame fallback eg
```
read -p "enter name (dafault $shortname)" input
username=${input:-shortname}
```

also i'd avoid common word variables in all-caps. Overriding env variables is not cool and USERNAME is awfully close to USER

---

### Post by woodson2 on 2012-11-28
> **Vaphell said:**
> it's about *read*. OP says that *read -i* doesn't work in older bash versions.

I don't know if that's possible to achieve in trivial way
i'd suggest lame fallback eg
```
read -p "enter name (dafault $shortname)" input
username=${input:-shortname}
```also i'd avoid common word variables in all-caps. Overriding env variables is not cool and USERNAME is awfully close to USER


Yea , it looks like there no other way to skin this cat.

Thanks.

---

