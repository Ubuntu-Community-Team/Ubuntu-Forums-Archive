---
title: "Two questions about Bash and using variables in paths"
date: 2015-03-10
forum: New to Ubuntu
---

### Post by Delco on 2015-03-10
Two questions about Bash and using variables in paths
   
  First Question:
  I am trying to read a variable and then put it into a path  when I create a link to a file on the user&#8217;s desktop:
   
  ```

read $user 
sudo ln -s /etc/php5/ /home/$user/Desktop/"go to php5 location"

```

  But I am given an error that says the target folder was not found, and the path is /home//Desktop/go to php5 location.
   
  So clearly the variable is not being used. How do I use it?
   
  Second Question:
  Is there a way to get the current user&#8217;s name automatically (or have a global variable that stands in for it)?
  This would allow the above to be done in one line:
  ```
sudo ln -s /etc/php5/ /home/$CURRENT_USER_NAME/Desktop/"go to php5 location"


```

---

### Post by papibe on 2015-03-10
Hi Delco.

A couple of comments:

There are several preset variables available for you use, including:
```
$HOME holds the path to the current user home.
$USER holds the name of the user currently running the screen.
```
In order to read a variable, you should not use '$'. For instance:
```
read thisvar
echo "the value entered was: $thisvar"
```
Hope it helps. Let us know if you have more questions.
Regards.

---

### Post by steeldriver on 2015-03-10
It's not that it's not being *used* I think - it's not being *set*. It should be 

```

read user

```

without the $, which is only required when you want to return the *value* of the variable. 

However the enviroment probably already sets $USER (upper case) and even easier $HOME so you should be able to do either

```

"/home/$USER/Desktop/go to php5 location"

```
or simply
```

"$HOME/Desktop/go to php5 location"

```

---

### Post by Delco on 2015-03-11
The error was with the $ when I read the variable. Thank you both!

Knowing $USER and $HOME will also be useful in the future.

---

