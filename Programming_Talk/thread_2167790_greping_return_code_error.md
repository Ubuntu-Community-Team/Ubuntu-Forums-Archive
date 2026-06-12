---
title: "greping return code error"
date: 2013-08-15
forum: Programming Talk
---

### Post by learnbash on 2013-08-15
[COLOR=#000000][FONT=verdana]Hi folks,

I am running below code which is giving me output "httpd (no pid file) not running", how can i grep this code in shell script. 

I have tried below code but it is not giving me error in echoing.


```

./webserver stop

if [ $? -eq 0 ]

echo " Everything is OK"

else

echo "Error code $0 and output"


```

error message command below part of error which i want to grep.

[/FONT][/COLOR]```

./webserver stop
httpd (no pid file) not running

```

---

### Post by DarkAmbient on 2013-08-15
Not sure if you simplied provided code or, but you need a if then, and end if with an fi :)

```

if [ $? -eq 0 ]; then
    echo " Everything is OK"
else
    echo "Error code $0 and output"
fi

```

This would also work.

```
[ $? -eq 0 ] && echo "Everything is ok" || echo "Error code $0 and output"
```

You can save the outcome in a variable:

```
o=`./webserver stop 2>&1 > /dev/null`
[ $? -gt 0 ] && echo OUTPUT: $o
```

---

### Post by learnbash on 2013-08-15
webservice is already stop but it is showing everything is ok.

```

#x=`./webserver stop 2>&1`

#echo $?
0

```

---

### Post by DarkAmbient on 2013-08-15
What is the output of $x then? (In your example)

---

### Post by learnbash on 2013-08-15
It is also showing value 0.

---

### Post by DarkAmbient on 2013-08-15
What is the content of webserver then?

---

### Post by learnbash on 2013-08-15
```



./webserver stop [ it is stopping weberver ]
./webserver start [ it is starting weberver ]



```


It is starting webserver and also stop webserver, both are valid arguments so that's why it i not showing anything. Actually my motive of writing script is that if httpd process is present in memory or not, if not then start the apache process but main problem is that i am not able to grep httpd process because its very difficult to get apache process looks like that.

---

### Post by DarkAmbient on 2013-08-15
You could check if there is any process:

```
pgrep apache2 > /dev/null && echo Webserver up || echo Webserver down
```

or same but if

```
if pgrep apache2 > /dev/null; then
    echo Webserver up
else
    echo Webserver down
fi
```

---

