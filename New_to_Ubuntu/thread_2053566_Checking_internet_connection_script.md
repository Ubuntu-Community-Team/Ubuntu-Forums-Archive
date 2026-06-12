---
title: "Checking internet connection script"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by Zimrie on 2012-09-05
Hi,
I've tried to make script because nowadays my internet connection is very changable, to notify me if state is changed..
But I'm new in Bash scripting, I've done some googling and can anybody tell me why script is not working??

```

#! /bin/bash

# This script attempts to check is there a change in internet connection On->Off   Off->On
# This is not working script, why????
main() 
{ 

Change=0;
# sleep 168

proc()
{	
	if ping -c 1 google.com > /dev/null
	then
	  Have=1
	else
	  Have=0
	fi
	    
    if [$Have -eq "1"] && [$Change -eq "0"]
    then 
          play /home/username/Music/alert.wav
          zenity --info --text "No Internet :("
          Change=1
    fi

    if [$Have -eq 0] && [$Change -eq 1]
    then
          play /home/username/Music/alert.wav
          zenity --info --text "Yes Internet :)"
          Change=0
    fi
          
    sleep 10 
    proc          
}   
proc
} 
main



```

---

### Post by Zimrie on 2012-09-05
ok here is right one
this is working

```

#! /bin/bash
# This script attempts to check is there a change in internet connection On->Off Off->On

main()
{
     
Change=0;
# sleep 168
     
proc()
{
    if ping -c 3 google.com > /dev/null
    then
      Have=1
    else
      Have=0
    fi
     
    if [ $Have -eq 0 ] && [ $Change -eq 0 ]
    then
       # play command depends from installed sox
       # play /home/username/Music/alert.wav
       zenity --info --text "No Internet :("
       Change=1
    fi
     
    if [ $Have -eq 1 ] && [ $Change -eq 1 ]
    then
       # play /home/username/Music/alert.wav
       zenity --info --text "Yes Internet :)"
       Change=0
    fi
     
    sleep 30
    proc

}
proc
}
main


```

---

