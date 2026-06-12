---
title: "Need a help in a Bash script that performs a select menus task"
date: 2007-09-15
forum: Programming Talk
---

### Post by black_ice on 2007-09-15
hello all .... , 


i want to make a bash script that controls the action of the logs and some services by using menus and i want it to be something like that 

starts with that form : 

1) mysql
2) system
3) apache
4) quit
Please Select a Choice Or  For The Menu : 

when the user enter a choice he will redirect to another menu for example if the user type 1 which is for mysql service this menu will appear 

1) mysql-log
2) mysql-start
3) mysql-stop
4) mysql-restart


and every choice of that perform a certain function like mysql start , restart , stop and so on 

i write this script 

```
 #!/bin/bash

#set the PS third  variable

PS3='Please Select a Choice Or  For The Menu : '

list="mysql system-log apache-log quit"

select i in $list

do

if [ $i = "mysql" ]

then

list2="mysql-log mysql-start mysql-stop mysql-restart"

select j in $list2


do 


if [ $j = "mysql-log" ]

then 

               watch tail /var/log/mysqld.log


elif [ $j = "mysql-start"   ]
then 
	service mysqld start

elif [ $j = "mysql-start"   ]

then 
	service mysqld start
 
elif [ $j = "mysql-stop"   ]
then
	service mysqld stop 
elif [ $j = "mysql-restart"   ]
then 
	service mysqld restart 
elif [ $i= "system-log" ]
then 	
	watch tail /var/log/messages

elif [ $i= "apache-log" ]
then
        watch tail /var/log/httpd/error-log


elif [ $i = "quit" ]


then
       exit;

fi

done

fi

done
```



but i got errors >> 1-i cannot choose another option except the choice 1 which is mysql service if i choose another service nothing happened !!!! 

```
  
Please Select a Choice Or  For The Menu : 2
Please Select a Choice Or  For The Menu : 

```


2-if i choose the first item 1.)mysql it works and all the items listed in the mysql item work well but at the same time i cannot get back to the other option so how i can add a back option 


and sorry for the long thread 

Thanks For ALL

---

### Post by peabody on 2007-09-15
I'm no bash expert, but try wrapping your variables in quotes when performing string comparisons (i.e. "$i").  I've had problems in the past.

---

### Post by black_ice on 2007-09-15
thanks  for you replay but that doesn't work  :(

---

### Post by pxwpxw on 2007-09-15
Edit:
Deleted.
Having tried some later suggestions, break seems to have been the answer

---

### Post by gnusci on 2007-09-15
give a look to this one:

[PHP]
#!/bin/bash
           OPTIONS="Hello Quit"
           select opt in $OPTIONS; do
               if [ "$opt" = "Quit" ]; then
                echo done
                exit
               elif [ "$opt" = "Hello" ]; then
                echo Hello World
               else
                clear
                echo bad option
               fi
           done

[/PHP]

---

### Post by ghostdog74 on 2007-09-15
This is how i might do it...
```

list2() 
{
cat << EOF
1) mysql-log 
2) mysql-start 
3) mysql-stop 
4) mysql-restart
5) Quit to last menu
Please select option: 
read choice
while [ 1=1 ];
do
   case 
   ...
   ...
   ...
   esac
done

EOF

}

cat << EOF
1)mysql
2)system-log 
3)apache-log 
4)quit
Please select a choice:
EOF

while [ 1=1 ];
do
   read choice
   case $choice in 
   1) list2;;
   2) echo "you chose 2";;
   3) echo "you chose 3";;
   4) exit;;
   *) echo "Not valid"
   esac
done



```

---

### Post by jpkotta on 2007-09-15
[http://ubuntuforums.org/showpost.php?p=3337359&postcount=8](http://ubuntuforums.org/showpost.php?p=3337359&postcount=8)

---

