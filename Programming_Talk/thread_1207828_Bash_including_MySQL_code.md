---
title: "Bash including MySQL code"
date: 2009-07-08
forum: Programming Talk
---

### Post by tirengarfio on 2009-07-08
Hi,

i have the bash script below. When i execute it i get these errors:

```
89.17.206.129
ERROR 1102 (42000): Incorrect database name '+%Y-%m-%d %H:%M:%S
);
'
89.17.206.130
ERROR 1102 (42000): Incorrect database name '+%Y-%m-%d %H:%M:%S
);
'
89.17.206.131
ERROR 1102 (42000): Incorrect database name '+%Y-%m-%d %H:%M:%S
);

```

This is the code:



```


IPS="$(seq -f "89.17.206.%.0f" 129 189) $(seq -f "89.17.219.%.0f" 65 126)"

for i in ${IPS}
do
if [ -z "$(nmap -p 22 $i |grep closed)" ]; then

BD="pingp22" 

mysql -uroot -pm -D $BD -Bse 'INSERT INTO `pingp22`.`checks` (

`fecha`
)
VALUES (
 'date +'%Y-%m-%d %H:%M:%S''
);
'

fi
done

```

Any idea?

Ciao

---

### Post by unutbu on 2009-07-08
Perhaps:
```
now=$(date +"%Y-%m-%d %H:%M:%S")
mysql -uroot -pm -D $BD -Bse "INSERT INTO `checks` (`fecha`) VALUES (\"$now\");"

```

---

### Post by tirengarfio on 2009-07-08
> **unutbu said:**
> Perhaps:
```
now=$(date +"%Y-%m-%d %H:%M:%S")
mysql -uroot -pm -D $BD -Bse "INSERT INTO `checks` (`fecha`) VALUES (\"$now\");"

```

Thanks, but it says now:

ERROR at line 1: Unknown command '\"'.

---

### Post by unutbu on 2009-07-08
Could you post the entire script? 
I wonder what is on Line 1...

---

### Post by tirengarfio on 2009-07-09
> **unutbu said:**
> Could you post the entire script? 
I wonder what is on Line 1...

Hi again,

i checked my code and it doesn't give that error any more. Now, my problems are:

- The date-time written in the MySQL table is 0000-00-00 00:00:00.

- It doesnt auto increment the id as you can see in this error:

Thu Jul 9 09:22:43 CEST 2009
ERROR 1062 (23000) at line 1: Duplicate entry '5422339' for key 1

Here you can see the table:
```

create table checks(
    id integer auto_increment,
    fecha datetime,
    primary key (id)
    );

```


This is my code:

```


IPS="$(seq -f "89.17.206.%.0f" 129 189) $(seq -f "89.17.219.%.0f" 65 126)"


for i in ${IPS}
do
if [ -z "$(nmap -p 22 $i |grep closed)" ]; then

BD="pingp22" 


echo $i


now=$(date +"%Y-%m-%d %H:%M:%S")

mysql -uroot -pm -D $BD -Bse 'INSERT INTO `pingp22`.`checks` (

`fecha`
)
VALUES 
 (\"$now\");'



fi
done

```

---

### Post by unutbu on 2009-07-09
Perhaps change the single-quote marks to double-quote marks:

```
mysql -uroot -pm -D $BD -Bse "INSERT INTO checks (

`fecha`
)
VALUES 
 (\"$now\");"
```

and change `pingp22`.`checks` to checks. 

With those changes, the code to work for me.

---

