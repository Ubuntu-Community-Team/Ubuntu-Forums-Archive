---
title: "Loop not working a it should do (ASAP)"
date: 2008-09-23
forum: Programming Talk
---

### Post by aliahsan81 on 2008-09-23
I have made all most all the  script,But i am stuck only on a single loop.I am getting all the document Root from apache conf.d file the passing each document root to a varible for processing but this seem to be not working,please check my code and suggest,This is really urgent.When i put static docroot it run fine but when i put using loop OR dynamic it cause problem plz see below.


```


#!/bin/bash
let test=0

abc="/var/www/html"
docroot=$(grep -H DocumentRoot /etc/httpd/conf.d/*.conf | awk -F' ' '{ print $3 }'| sort -u | uniq)
doccount=$(grep -H DocumentRoot /etc/httpd/conf.d/*.conf | awk -F' ' '{ print $3 }'| sort -u | uniq | wc -l)
#i=0
#while [ $i -le $doccount ]
# do
#    confd="$docroot\n"
#echo $confd
    find $abc -type d -perm /o=w | while read DIR
    do

    test=$(cd "$DIR"; ls -A *.html *.php  2>/dev/null | wc -l)

        if [ "$test" != "0" ]
                   then


            echo "DIR Found WITH FILES"$DIR $test
           fi


        if [ `ls -a "$DIR" | wc -l` -le 2 ]
    
                   then

            echo "Writable_dir Empty"$DIR
            fi


    done
#i=$(( $i + 1 ))
#done


        count=$(find /var/www/html/ -type f -perm /o=w | grep -i ".htaccess"| wc -l )

        find "$abc" -type f -perm /o=w | grep -i ".htaccess" | awk  -F. '{ print $1 }' | while read this

        do
        echo "_htaccess_is_Writable"$this
        done
 
Output with static docroot

DIR Found WITH FILES/var/www/html/test3 4
DIR Found WITH FILES/var/www/html/test3/abc 2
Writable_dir Empty/var/www/html/abc
DIR Found WITH FILES/var/www/html/test/abc 1
DIR Found WITH FILES/var/www/html/test2 1


Output with dynamic Docroot


"/var/www/html" "/var/www/test/www.example.com" "/var/www/www.example.com"\n
find: "/var/www: No such file or directory
find: "/var/www/test: No such file or directory
find: "/var/www: No such file or directory
"/var/www/html" "/var/www/test/www.example.com" "/var/www/www.example.com"\n
find: "/var/www: No such file or directory
find: "/var/www/test: No such file or directory








```

---

