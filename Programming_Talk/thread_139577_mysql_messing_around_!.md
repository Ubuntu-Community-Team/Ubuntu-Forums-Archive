---
title: "mysql messing around !"
date: 2006-03-04
forum: Programming Talk
---

### Post by skaboss on 2006-03-04
Hello,

I'm a java developper, freshly converted from devian to kubuntu. Always run mysql on debian etch without any problem, but i have 2 big problems on kubuntu :
1- mysql administrator : everytime i want to add or modify a user, i receive the error message : "Duplicate user name, please enter another name." So i have to use grant by the console, wich is far from user friendly !

2- can't connect to mysql via jdbc : the following code 
```

DriverManager.getConnection("jdbc:mysql://localhost:3306/test","root","mypassword");

```
gives me the error : 
[B]Access denied for user 'root'@'localhost.localdomain' (using password: YES)
[/B]
According to mysql.org, the first problem seems to be a known bug, and they recommend to upgrade mysql administrator, but there is no ubuntu packager for a newer version !

For the second problem, i tried 127.0.0.1 instead of localhost, tried different users and so on with no success...  ](*,) 

Please help me !

---

### Post by jerome bettis on 2006-03-04
i went through the same thing a couple weeks ago.  my problem was i didn't have the loopback interface up, type ifconfig and if you don't see anything about lo you need to get that up.  also make sure your prompt says userName@localhost  .. i had a different hostname but mysql would not cooperate with anything but localhost.

i also had to do a GRANT ALL PRIVLEDGES ON *.* TO john@localhost.* IDENTIFIED BY 'password' to get my user name.  after that i could do mysql -p as myself (not root) and login.

as for jdbc, i didn't have any luck using the name and password as seperate arguments.  instead i had to put them in the url, i wrote a class

```
private static class DBUrl  {
    private static final String    PROTOCOL    = "jdbc:mysql://";
    private static final String    HOST_NAME   = "localhost";
    private static final int       PORT        = 3306;
    private static final String    USER_NAME   = "john";
    private static final String    PASSWORD    = "*****";

    public static String formUrl(String dbName)  {
        return PROTOCOL + HOST_NAME + ":" + PORT + "/" + dbName +
                  "?user=" + USER_NAME + "&password=" + PASSWORD;
    }
}
.....
     con = DriverManager.getConnection(DBUrl.formUrl("whateverDB"));

``` 
hope that helps somewhat.

---

### Post by skaboss on 2006-03-04
Thanks a lot Jerome !

```

GRANT ALL PRIVILEGES ON *.* TO john@localhost.* IDENTIFIED BY 'password'

```
didn't work, mysql seemed to reject localhost.*
So i changed it to
```

GRANT ALL PRIVILEGES ON *.* TO john@localhost.localdomain IDENTIFIED BY 'password'

```
and now it's ok.
Thanks again : i really had to make it work, and your help was precious

---

