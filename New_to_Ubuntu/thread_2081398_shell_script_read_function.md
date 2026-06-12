---
title: "shell script read function"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by hookitup on 2012-11-06
hello folks, so i have the small shell script i call fake logon
```

echo "Please enter username:"
read  username

if [ "$username" = "Jake" ]
then
        echo 'Success!!! You are now logged in.'
else
        echo 'Sorry, Access Denied.'

```

now idk what its called but where it ask for username and you enter it, it displays what your entering, now how would i make it so it doesnt displace what your entering kinda like when you log in as root or any other account in terminal, it ask for password and although u r typing it shows no text . is this possible to do after the 
```
echo "Please enter username:"
```
there's gota be some switch or syntex or something to enable entering text silently or whatever you want to call it.

anybody know?

---

### Post by josephmills on 2012-11-06
Like this ? like clearing the terminal ?  

```

#!/usr/bin/env bash 
echo "Please enter username:"
read  username
clear
if [ "$username" = "Jake" ];then
echo 'Success!!! You are now logged in.';
else
echo 'Sorry, Access Denied.';
fi


```

---

### Post by steeldriver on 2012-11-06
```
read -s username
```maybe?

---

### Post by josephmills on 2012-11-06
Or do you mean something like this ?  
```

#!/usr/bin/env bash 
Namearoo="Jake"
read -s -p "Username: " username
echo ""
if [ "$username" == "$Namearoo" ];then 
        echo "Success!!! You are now logged in.";
else 
        echo "Sorry, Access Denied.";
fi 

```

EDIT I see that someone beat me to it.

---

### Post by papibe on 2012-11-06
Hi hookitup.

You can set the prompt on the same read command using the option -p. For instance:
```
read -p "Username:" username
```
In order to read a password-like string, you can add the silent option (-s):
```
read -p "Password:" -s password
echo
```
Note that the last echo is necessary, because the final enter is won't be displayed either.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by hookitup on 2012-11-08
> **josephmills said:**
> Or do you mean something like this ?  
```

#!/usr/bin/env bash 
Namearoo="Jake"
read -s -p "Username: " username
echo ""
if [ "$username" == "$Namearoo" ];then 
        echo "Success!!! You are now logged in.";
else 
        echo "Sorry, Access Denied.";
fi 

```

EDIT I see that someone beat me to it.


this worked perfectly, thanks everybody for the help

---

