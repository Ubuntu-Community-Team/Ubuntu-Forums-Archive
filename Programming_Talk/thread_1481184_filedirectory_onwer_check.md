---
title: "file/directory onwer check"
date: 2010-05-12
forum: Programming Talk
---

### Post by aliahsan81 on 2010-05-12
Hi All


I am stuck a bit cant figure out how to dealt with it.


i have directory like /var/www/ali  and /var/www/mike and so on.

Now i want to check all file and directory  in  /var/www/ali  and /var/www/mike  should belong to ali and mike respectively.If any file/directory belong to other user give some error msg.

Can any one give me some hint/guide how  i achieve  it.

---

### Post by ja660k on 2010-05-12
look at ls -l
```

-rw-r--r-- 1 root root 863674 2010-02-03 13:17 cakephp-cakephp1x-26b9dbc.tar.gz

```

where the third column is the owner of the file.

so in a script
```
#ls -l cakephp-cakephp1x-26b9dbc.tar.gz | awk '{print $3}'
root
```


so in some sort of script possibly perl, bash. any language with backticks.
loop though your files, exec the cmd, and compare to the given username :-)

---

### Post by aliahsan81 on 2010-05-12
Thanks for reply ,Problem is that how i determine the script is parsing the 

/var/www/ali , and /var/www/mike and its scanning it file.This part is a small part of a script i am coding it in bash.

My Means 


/var/www/ali  how i extract its currently scanning /var/www/ali 

afterward is its parsing /var/www/ali how do i compare file belong to ali

---

### Post by ja660k on 2010-05-12
regex is your friend

i dont know in bash, but in Perl this is super easy.

Youll have to write an expression to get everything AFTER the last "/" character.

to get the "ali" & "mike"

---

### Post by aliahsan81 on 2010-05-12
right thanks

---

### Post by ja660k on 2010-05-12
or if regex isnt your thing, split the string /var/www/ali 

by "/" so something like (x,y,name) = split("/","/var/www/ali") 
*** Note that that is only psuedocode IT DOESN'T WORK**

then only work with name variable.

but then your folders MUST ONLY EVER have 3 forward slashes in it.
...
If you do it this way i wouldnt go showing my friends,
if you want to be uber 1337 i'd use regex ;-)

---

### Post by hannaman on 2010-05-12
For bash, take a look at the basename command.

---

### Post by aliahsan81 on 2010-05-12
ok let me check thanks guys

---

### Post by aliahsan81 on 2010-05-12
I did this

i created a list of user in /var/www/xxx

ali,mike etc

then 
start loop

find /var/www/$j  -maxdepth 2  -not \( -user  $j \)

end loop

:):P

---

