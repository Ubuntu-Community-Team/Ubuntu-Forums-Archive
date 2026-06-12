---
title: "My first bash script :D"
date: 2008-07-02
forum: Programming Talk
---

### Post by jvb_5963 on 2008-07-02
#Alarmclock i wrote so im alerted when to stop playing with the bash shel;)



liv=0			#variables
yes=y
no=n
STDH=15
STDM=50

echo "Set timer (y) or (n)o?"

read qwest

         if [ $qwest == $yes ]; then		#timer setup
	echo "Enter hours?"		
	read HS
	echo "Enter minutes?"
	read MS
	else 
		
	HS=$STDH
	MS=$STDM     
	echo "Timer is set at default: $HS:$MS"		#default setup
	fi

              



while [ $liv ]; do

  	time=`date`			#gets time
     	H=${time:11:2}
     	M=${time:14:2}
	S=${time:17:2}
     


	echo "$H:$M:$S"
    	sleep 0.5
    

	if [ $H == $HS ] ; then		#hour check

	while [ $H == $HS ] ; do	
 
	 if [ $M != $MS ]; then		#minute check

	break
	fi

	sleep 0.5			
	echo "$H:$M:$S"			#play alarm
	echo -e "\aTime to stop!"
	done
	fi

done

---

### Post by Joeb454 on 2008-07-02
Nice :) I may try that out myself.

You should note that you can put your code in [noparse]```

```[/noparse] tags to make it a little easier to read :)

---

### Post by ghostdog74 on 2008-07-02
good effort. some suggestion for improvement
> 
```

if [ $qwest == $yes ]; then #timer setup
    echo "Enter hours?"
    read HS
    echo "Enter minutes?"
    read MS
else

    HS=$STDH
    MS=$STDM
    echo "Timer is set at default: $HS:$MS" #default setup
fi


```



you might want to use case,esac
```

 case $qwest in
  Y|y ) 
       echo "user enter yes" ;;
       printf "Enter hours : "
       read .....
       ...
  N|n ) echo "user said no" ;;
  * ) echo "invalid ";;
  esac

```


> 
```

   time=`date` #gets time
    H=${time:11:2}
    M=${time:14:2}
    S=${time:17:2}

```


can be this way. No need to do extra substringing
```

 IFS=":"
 set -- $(date +%H:%M:%S)
 echo $1 $2 $3 # $1 is H, $2 is M, $3 is S
 unset IFS

```

---

### Post by mssever on 2008-07-03
That reminds me of an applet I recently discovered. install timer-applet, then add it to your Gnome panel. Very handy, especially if you configure it to play a loud, annoying sound when the time runs out.

---

### Post by jvb_5963 on 2008-07-03
Thanks for the reply ill study the code. 

i never have done this on windows i found out that linux is the way to go.

---

### Post by jvb_5963 on 2008-07-03
#hi again i changed the code a litlebit here it is


liv=0			#variables
yes=y
no=n
STDH=15
STDM=50
ercheck=0
one=1
zero=0

echo "Set timer (y)es or (n)o?"

read qwest
	
	while [ $ercheck == $zero ]; do #set time
        case "$qwest" in
	y | Y )
	echo -e "User entered yes.\tEnter hours?"
	read HS
	echo -e "Enter minutes?   \t"
	ercheck=1
	read MS ;;
	
	n | N )
	echo -e "User entered no.\tDefault time is set to $STDH:$STDM!"
	HS=$STDH 
	MS=$STDM
	ercheck=1;;
	* )
	echo "error wrong input! try again?" 
	read qwest ;;
	
	esac
	done
	
 



while [ $liv ]; do

  	time=`date`			#gets time
     	H=${time:11:2}
     	M=${time:14:2}
	S=${time:17:2}
     


	echo "$H:$M:$S"
    	sleep 0.5
    

	if [ $H == $HS ] ; then		#hour check

	while [ $H == $HS ] ; do	
 
	 if [ $M != $MS ]; then		#minute check

	break
	fi

	sleep 0.5			
	echo "$H:$M:$S"			#play alarm
	echo -e "\aEefje is coming!"
	done
	fi

done

---

### Post by mssever on 2008-07-04
Unindented code is hard to read, and the only way to get it to display indented is to use [noparse]```

```[/noparse] tags, as suggested in post 2.

I'm wondering why you have variables called $zero and $one. Why not simply write 0 and 1? If the value of $zero ever is anything other than 0, then it's a poorly-named variable, so what's the point of having it in the first place?

---

### Post by jvb_5963 on 2008-07-04
okay sorry here it is
```
 #hi again i changed the code a litlebit here it is


liv=0 #variables
yes=y
no=n
STDH=15
STDM=50
ercheck=0
one=1
zero=0

echo "Set timer (y)es or (n)o?"

read qwest

while [ $ercheck == $zero ]; do #set time
case "$qwest" in
y | Y )
echo -e "User entered yes.\tEnter hours?"
read HS
echo -e "Enter minutes? \t"
ercheck=1
read MS ;;

n | N )
echo -e "User entered no.\tDefault time is set to $STDH:$STDM!"
HS=$STDH
MS=$STDM
ercheck=1;;
* )
echo "error wrong input! try again?"
read qwest ;;

esac
done





while [ $liv ]; do

time=`date` #gets time
H=${time:11:2}
M=${time:14:2}
S=${time:17:2}



echo "$H:$M:$S"
sleep 0.5


if [ $H == $HS ] ; then #hour check

while [ $H == $HS ] ; do

if [ $M != $MS ]; then #minute check

break
fi

sleep 0.5
echo "$H:$M:$S" #play alarm
echo -e "\aEefje is coming!"
done
fi

done 
```

---

### Post by jvb_5963 on 2008-07-04
about the zero 
i didnt remember how to use a constand thats why i 
used de name zero
and also isnt nothing rather NULL?

---

### Post by mssever on 2008-07-04
You still aren't indenting your code. Here's an example from your code. Notice how much easier indented code is to understand.
```
while [ $ercheck == $zero ]; do #set time
    case "$qwest" in
        y | Y )
            echo -e "User entered yes.\tEnter hours?"
            read HS
            echo -e "Enter minutes? \t"
            ercheck=1
            read MS
            ;;

        n | N )
            echo -e "User entered no.\tDefault time is set to $STDH:$STDM!"
            HS=$STDH
            MS=$STDM
            ercheck=1
            ;;
        * )
            echo "error wrong input! try again?"
            read qwest ;;

    esac
done
```
> and also isnt nothing rather NULL?Huh?

---

### Post by jvb_5963 on 2008-07-05
```

liv=0 #variables
yes=y
no=n
STDH=15
STDM=50
ercheck=0
  one=1
 zero=0

echo "Set timer (y)es or (n)o?"

read qwest
   
while [ $ercheck == $zero ]; do #set time
       case "$qwest" in
    y | Y )
       echo -e "User entered yes.\tEnter hours?"
       read HS
       echo -e "Enter minutes? \t"
       ercheck=1
       read MS ;;

    n | N )
       echo -e "User entered no.\tDefault time is set to $STDH:$STDM!"
       HS=$STDH
       MS=$STDM
       ercheck=1;;
    * )
       echo "error wrong input! try again?"
       read qwest ;;

   esac
   done





   while [ $liv ]; do
       time=`date` #gets time
       H=${time:11:2}
       M=${time:14:2}
       S=${time:17:2}
       echo "$H:$M:$S"
       sleep 0.5


        if [ $H == $HS ] ; then #hour check

             while [ $H == $HS ] ; do

                if [ $M != $MS ]; then #minute check

        break
        fi

            sleep 0.5
            echo "$H:$M:$S" #play alarm
            echo -e "\aEefje is coming!"
        done
        fi

done


```

---

### Post by jvb_5963 on 2008-07-05
somthing like that ? sorry for that im a newbie so please
show me the ropes thanks. also my english isnt a 100 %


i meant with a NULL value
that NULL equals nothing.
and zero equals zero. 
cause there was sombody that complaint about my 
variable name zero.

---

