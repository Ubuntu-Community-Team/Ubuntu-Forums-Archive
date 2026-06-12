---
title: "Simple PHP Error"
date: 2007-08-03
forum: Programming Talk
---

### Post by dhtseany on 2007-08-03
Can someone tell me what is wrong with this little chunk of code? What it's supposed to do is:

a) If the user is authenticated then it is supposed to use $_SERVER['PHP_AUTH_USER']  to simply display the username.

or 

b) if the user is not logged in, it's supposed to display the link for login.php.

Any ideas? I'm sure it's something relatively dumb but I've been fighting with it all morning.

Thanks for your help,

Sean

```
 
if ($_SERVER['PHP_AUTH_USER'] = NULL) {
    echo "<a href=\"../secure/index.php\">Login</a>";
} else {
    echo $_SERVER['PHP_AUTH_USER'];
}

```

---

### Post by LaRoza on 2007-08-03
> **dhtseany said:**
> 

```
 
if ($_SERVER['PHP_AUTH_USER'] = NULL) {
    echo "<a href=\"../secure/index.php\">Login</a>";
} else {
    echo $_SERVER['PHP_AUTH_USER'];
}

```

Yes, you are using the assignement operator instead of testing for equality.

---

### Post by dhtseany on 2007-08-03
So what part of the code am I doing wrong?

Thanks

---

### Post by LaRoza on 2007-08-03
```
 
if ($_SERVER['PHP_AUTH_USER'] = NULL) //HERE IS THE ERROR, USE == NOT =
{
    echo "<a href=\"../secure/index.php\">Login</a>";
} else {
    echo $_SERVER['PHP_AUTH_USER'];
}

```

---

