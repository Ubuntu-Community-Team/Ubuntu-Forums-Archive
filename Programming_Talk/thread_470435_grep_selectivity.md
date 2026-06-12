---
title: "grep selectivity"
date: 2007-06-11
forum: Programming Talk
---

### Post by alalusim on 2007-06-11
ive been using grep -o to get multiple series of characters saved into a text file.  what i want to be able to do now is to isolate each series and save them to a variable (each is separated from the next by a space)  does anyone know of a way to specify which result grep -o returns if there are multiple matches or if there is a way to manipulate the string of characters to isolate the ones i want?

thanks

---

### Post by yabbadabbadont on 2007-06-11
Pass the output from grep to sed in order to pull out the section you want.  You could probably use awk to do it as well.

---

### Post by ghostdog74 on 2007-06-11
best is to post a sample of an input file, your current code, and also your expected output.

---

### Post by alalusim on 2007-06-11
25:11 5:41 3:59 5:40 12:48 4:31 7:56 9:37

if i have that saved in a text file how can i get each term into its own variable (i.e. var1=25:11 var2=5:41, etc)

ive looked at sed and awk but im unsure of how to use them

---

### Post by yabbadabbadont on 2007-06-11
After looking at your sample data, it might be that the "cut" utility would be of more use.  "man cut" for details.  Pay close attention to the section on specifying your own field delimiter (a space in your case).  As long as you always have the same number of fields on each line of the file, then it should be pretty easy.

---

### Post by HackingYodel on 2007-06-12
> **alalusim said:**
> 25:11 5:41 3:59 5:40 12:48 4:31 7:56 9:37

if i have that saved in a text file how can i get each term into its own variable (i.e. var1=25:11 var2=5:41, etc)

ive looked at sed and awk but im unsure of how to use them

If you are using Bash, try arrays.

If you have 25:11 5:41 3:59 5:40 12:48 4:31 7:56 9:37 in file logtime then,

**myvar=($(cat logtime))** will pack the array, zero indexed, **myvar** using the **cat** command.

**echo ${myvar[0]}** will give you 25:11
**echo ${#myvar[*]}** will give you 8, the number of elements in the array
**echo ${myvar}** is 25:11 or the zero element
**echo ${myvar[*]}** is all the elements and 
**echo ${myvar[2]}** would show 3:59

Of course you wouldn't wouldn't use the **echo** command in your script unless you wanted the array value "printed"

This is cool because Bash has no limits on the number of elements in an array and array assignment can be piped in, from grep for example [B]myvar=($(grep : logtime))
[/B]
Hope that helps!

---

