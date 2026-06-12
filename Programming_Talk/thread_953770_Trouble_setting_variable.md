---
title: "Trouble setting variable"
date: 2008-10-20
forum: Programming Talk
---

### Post by cation007 on 2008-10-20
Hi,
I have trouble in setting a variable in shell.

var="may"
$var="be not"
echo $may


is not working.

Actually I want to set "be not" to a variable called 'may'

Can somebody tell me how to set it in BASH ?

thanks.

---

### Post by stevescripts on 2008-10-20
This might be a good place to start: [http://tldp.org/LDP/abs/html/varassignment.html]("http://tldp.org/LDP/abs/html/varassignment.html")

That tutorial begins here: [http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

```

may="be not"
echo $may

```

Steve

---

### Post by cation007 on 2008-10-20
> **stevescripts said:**
> This might be a good place to start: [http://tldp.org/LDP/abs/html/varassignment.html]("http://tldp.org/LDP/abs/html/varassignment.html")

That tutorial begins here: [http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

```

may="be not"
echo $may

```

Steve


Hey,

Thanks.
That link was very useful...

Now, I am running into new problem...

I set the value to the variable.

But dunno how to retrieve it??

echo $$var is not printing "be not" as I wanted too ...

How can I do that ?

---

### Post by JupiterV2 on 2008-10-20
the '$' dollar sign symbol is reserved. You can't use it when assigning variables. It is used the same way as the dereference '*' symbol in C and C++.

```

var1="foo" # valid
$var2="bar" # invalid

#this will likely cause an error or only display 'var1'
echo $var1$$var2 

```

---

### Post by stylishpants on 2008-10-20
This is known as 'indirect expansion'.  See the bash man page for more info.

```
fhanson@fhanson:~$ echo $PATH
/data/home/fhanson/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

fhanson@fhanson:~$ var=PATH

fhanson@fhanson:~$ echo $var
PATH

fhanson@fhanson:~$ echo ${!var}
/data/home/fhanson/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

fhanson@fhanson:~$ 

```

---

### Post by cation007 on 2008-10-20
fantastic.

it worked.
thanks a lot.

---

