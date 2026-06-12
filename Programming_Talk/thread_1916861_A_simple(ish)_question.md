---
title: "A simple(ish) question?"
date: 2012-01-28
forum: Programming Talk
---

### Post by Eiji Takanaka on 2012-01-28
yo dudes i was wondering if any programming jedi out there, could give  me a few suggestions for a fairly simple problem #which makes me?;) i've yet to solve.

The easy version is this.
so basically i was just wondering how i might go about incrementing a 4  digit counter by +1 and looping a program called from the command line.

The program in this instance is wpa_cli called once each time with the command switch wps_reg "bssid" "0000".

I.e the command would be exactly the same "wpa_cli wps_reg "bssid" 0000  (but these digits would increment +1 and it would be called  continuously, possibly with a "sleep 5" after each execution of the  loop.

Long story short (!= to what i've just written here =P)

I just want to increment the 4 0's by one at a time.

Theres a program called reaver which is supposed to do the same thing,  (!= working for me =( meh i just thought if it could be done with a  scraggly bit of cowboi code and utilizing wpa_supplicant i'd give it a  bash and learn something in the process. 

I can currently use wpa_supplicant to initiate the eapol handshake but  it is currently only achievable au manuel. I was thinking a simple  script which increments the aforementioned counter +1 each time might be  a way forward. 

Looking at all the code in reaver seemed somewhat troublesome, so i  thought maybe if the same process could be done but in a kind of urban  ghetto hack way. Then all's good in jackanory. 

If i can append this little tasty +1 morsel that someone might be able  to help me with, to the end of this script i wrote (well mostly borrowed  hoho) (mind the L plates) then i thought perhaps i could concoct a  little piece of frankencode to achieve the desired results. 

O.k heres what i have thus far

```

#! /bin/bash

sudo kill -9 $(ps -A | grep Network | awk '{print $1}') && sleep 1

sudo kill -9 $(ps -A | grep wpa | awk '{print $1}') && sleep 1

echo 'Killing Network Manager & Wpa Supplicant' && sleep 1

echo "Done"

sudo ifconfig wlan0 up && sleep 1

sudo wpa_supplicant -Dwext -i wlan0 -c/etc/wpa_supplicant.conf -B   

exit 0
```

After doing the whole wpa_supplicant.conf tweak, and editting /etc/init/network-manager.conf with 

#respawn (of the devil)

That sorts wpa_supplicant out.

So basically all i'm really missing for step 2 in the world domination  plan is the whole +1 increment, sleep 5(ish) and loop back to the  beggining once more, (up to 9999 preferable, although i know thats just  being cheeky really).

It seems the way its done in reaver is simply to have a list of every  number 0000-9999 in a file called keys, i'm guessing thats so it can be  randomised. But i was thinking its probably easier just to increment by 1  each time. 

O.k so i'm sure people won't just dish out the code to a information  super highway street urchin likes meself, but if some kind souls could  points me in the right direction i'd be most umbly oblidged. 

And no the right direction is not exit 0 thankyou very much ;)

Thanks guys/gals! =) 

P.s if only life were this easy eh?  ;)

```
sudo kill -9 $(ps -A | grep ******** | awk '{print $1}') && sleep 1000
```

---

### Post by Eiji Takanaka on 2012-01-29
Hoho, 105 views but no replies, perhaps the question is not as simple as i first thought. ;)

---

### Post by Eiji Takanaka on 2012-02-06
*Takes a few strides back......

eyes up the target......

runs & bellyflops.....

*bump*

 ;)

---

### Post by r-senior on 2012-02-06
> I just want to increment the 4 0's by one at a time.

Does this help? It only goes up to 9, for illustration. You'd replace the echo with the command you need.

```
#!/bin/bash

for i in {0..9}; do
	code=$(printf "%04d" $i)
	echo 'Command to run program using '$code
        sleep 1
done
```

---

### Post by Eiji Takanaka on 2012-02-06
Hey senior thanks for the reply!

I'm just trying to get my head round how your code would work (im also going to try looking deeper into a bit of perl, got some beginner material to read up on ;).

What does the %04d parameter do exactly? Define 0000? 

I am looking at trying to get the program to start at 0000, then progress to 0001 and so on and so forth up until 9999. 

I was thinking if there was a way of running the program then finding the 0000 field by piping that line into awk maybe, then adding +1 to that field and looping back to the beginning of the program, if that makes any sense? =).

If you could you please explain a little more about the program you have written and how it works i would be most oblidged =) 

Thanks,

- dan

---

### Post by r-senior on 2012-02-06
Did you put it into a file, make it executable and run it?

```
$ chmod +x test.sh
$ ./test.sh
Command to run program using 0000
Command to run program using 0001
Command to run program using 0002
Command to run program using 0003
Command to run program using 0004
Command to run program using 0005
Command to run program using 0006
Command to run program using 0007
Command to run program using 0008
Command to run program using 0009
```

The "%04d" is a format string, which means a (d)ecimal number with a width of (4) and leading zeroes (0). Enclosing the printf statement in $(...) means take the result and assign it to the $code variable.

If you change the limit of the for loop from 9 to 9999, it will print "0000" to "9999". Eventually.

The idea was that you replace the 'echo' line with a call to your script.

---

### Post by emiller12345 on 2012-02-06
A similar but slightly different version:
```

#!/bin/bash
COUNT=0; 
while [ 1 ]; do 
    printf "%04i\n" $COUNT; 
    COUNT=$(($COUNT+1)); 
    if [  $COUNT -ge 10000 ]; then 
        COUNT=0; 
    fi; 
done

```

the "%04i" specifies the format of the "i" integer number that it has 4 placeholders in front. you can get some information about the printf command with
```
~$ man printf
```

---

### Post by Eiji Takanaka on 2012-02-06
Hi again guys, thanks once more for responding.

Yup senior i put it in a script, replaced the quoted part with the command string "wpa_cli wps_reg "bssid" (the command i am trying to execute), and altered the 0..9 to 0..9999.


This is exactly what i wanted to do, but as i breifly read it simply echo'd the list on screen, rather than executed the program i was wishing to call?

---

### Post by Eiji Takanaka on 2012-02-06
heres the code i ran......
> 
#!/bin/bash

for i in {0..9999}; do
    code=$(printf "%04d" $i)
    echo 'wpa_cli wps_reg 00:00:00:00:00:00'$code
        sleep 8
doneI need to test slightly more, but im under the inclination that it simply echo'd the lines above on screen and did not execute/call the desired program....

---

### Post by r-senior on 2012-02-06
No, it won't have run the program. You still have echo in there.

The whole echo line needs to be replaced by the line that calls your script.

---

### Post by Eiji Takanaka on 2012-02-06
oky coky!

Would i need to define the path to the program in full? 

How would i implement this into the script?

The program returns two lines after each "one-time" call from the command line 
> 
selected interface 'wlan0'
OKWould i also need to implement some code to ignore these two lines as well? 

Cheers =)

P.s the program is located in the global directory i.e it can be executed from any directory in terminal. As my memory serves me thats /bin right?

---

### Post by Eiji Takanaka on 2012-02-06
Nevermind!

Cracked it.

Thanks for the assistance guys!

Just removed the echo and quotes and it just calls it as is. 

I'm going to experiment with the code a bit and see if i can tweak it some more =)

(Cool you can use echo as well as the actual program call!)

Haha i know it must be beginner stuff for you guys, but to see an automated script in action is a wonder to behold! =) 

Learn more i shall ;)

---

