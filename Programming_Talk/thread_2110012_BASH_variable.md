---
title: "BASH variable"
date: 2013-01-29
forum: Programming Talk
---

### Post by AlexandruIacob on 2013-01-29
Hi all,

I have a small script that uses dialog and i want to copy recursively 2 folders from location A to location B.
The script is functioning fine and the folders are copied correctly, but, the issue that I have is with the --gauge bar. :sad:

```

DIRS=($DRUPAL_WWW_DIR/ $DRUPAL_ASSETS_DIR/) 
DEST=$WEB_PATH$DEV_ENV_WEB  
dialog --title "Progress..." --gauge "Importing assets and core ..." 10 75 < <(  
# Get total number of files in array         
total=`find ${DIRS[@]} -type f | wc -l`        
 echo $total >> to     
# set counter - it will increase every-time a file is copied to $DEST  
  i=0     
#    
# Start the for loop    
#   
 for f in "${DIRS[@]}"    
do       
# calculate progress       
PCT=$(( 100*(++i)/total ))       
  echo $PCT >> ty       
# update dialog box 
cat <<EOF 
XXX 
$PCT 
Copying $f 
XXX 
EOF     
#    copy file $f to $DEST   
cp -R $f ${DEST/${DIRS[@]}} &>/dev/null    
done 
)

```When I run the script, $total=3776 but in the ty file (for testing purpose only) i have 

```

0
0

```Here are some screenshots for more details:
[IMG]http://i1255.photobucket.com/albums/hh630/Andy_BN/forum/2013-01-28_1254_zps536618ee.png[/IMG]

Please let me know where I'm doing something wrong.

Thank you.

---

### Post by ofnuts on 2013-01-29
How much is $total?

---

### Post by steeldriver on 2013-01-29
```
PCT=$(( 100*(++i)/total ))
```is integer arithmetic - so $PCT will be zero until 100*(++i) is greater than total (which you say is 3776), I think

If you want to do floating point arithmetic, you could use bc

```
$ i=10; total=3776; PCT=$(( 100*(++i)/total )); echo $PCT
0
$ echo "scale=3; 100*($i+1)/$total" | bc
.317

```

Your script is pretty hard to read btw

---

### Post by AlexandruIacob on 2013-01-29
Thank you for your help.
I decided to use a different method that is faster anyway. Like I mentioned, the script IS copying the files in the right location. 
Using TAR, the run speed is much faster and I get the same results. As this will run on a DEV server, locked down, I know the exact location of the core.

```

(pv -n core.tar.gz | tar xzf - -C $WEB_PATH$DEV_ENV_WEB ) \
2>&1 | dialog --gauge "Extracting core and assets..." 6 50

```Thank you again for all the ideas. :P

---

