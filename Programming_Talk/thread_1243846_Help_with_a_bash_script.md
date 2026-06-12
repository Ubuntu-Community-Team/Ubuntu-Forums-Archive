---
title: "Help with a bash script"
date: 2009-08-18
forum: Programming Talk
---

### Post by redhotfire on 2009-08-18
[quote=]
#!/bin/bash

echo -e "*******************Aireplay Options************************"
echo -e "     WPA options:"
echo -e "1. Deauthentication
echo -e "     WEP options:"
echo -e "2. Fake authentication"
echo -e "3. Interactive Packet Replay"
echo -e "4. ARP Request Replay"
echo -e "5. Korek Chopchop"
echo -e "6. Fragmentation"
echo -e "7. Caffe-latte"
echo -e "8. Client-Oriented Fragmentation"
exit 1
[/quote]
Yet again, another BASH question. Went I attempt to run this, it fails on saying:
[quote=]
test.sh: line 13: unexpected EOF while looking for matching `"'
test.sh: line 15: syntax error: unexpected end of file
[/quote]
What exactly is wrong with the script?

Thanks again,
red

---

### Post by bodhi.zazen on 2009-08-18
You did not close the quotes at the end of this line :

> echo -e "1. Deauthenticationshould read ```
echo -e "1. Deauthentication"
```

Edit: you may also wish to look at printf

[http://bash-hackers.org/wiki/doku.php/commands/builtin/printf](http://bash-hackers.org/wiki/doku.php/commands/builtin/printf)
[http://bash-hackers.org/wiki/doku.php/snipplets/wrapperargs](http://bash-hackers.org/wiki/doku.php/snipplets/wrapperargs)

---

### Post by redhotfire on 2009-08-18
> **bodhi.zazen said:**
> You did not close the quotes at the end of this line :

should read ```
echo -e "1. Deauthentication"
```

Edit: you may also wish to look at printf

[http://bash-hackers.org/wiki/doku.php/commands/builtin/printf](http://bash-hackers.org/wiki/doku.php/commands/builtin/printf)
[http://bash-hackers.org/wiki/doku.php/snipplets/wrapperargs](http://bash-hackers.org/wiki/doku.php/snipplets/wrapperargs)

Oh geez, why didn't i look more thoroughly. For the current time, echo will do fine for printing commands. I know the printf() function in C and do not want to start changing any syntax's around for now.

Thanks,
red

---

### Post by bodhi.zazen on 2009-08-18
OK, glad it is working. I understand re : echo vs printf , I was not sure if you were familiar with printf.

---

### Post by redhotfire on 2009-08-18
> **]
while [ $Decision2 != 9 ]  said:**
> ; then
xterm -e aireplay-ng -0 10 -a $apMAC -c $clientMAC $aireDevice &
elif [ $Decision2 == 2]; then
xterm -e aireplay-ng -1 1 -a $apMAC -h $clientMAC $aireDevice &
elif [ $Decision2 == 3 ]; then
xterm -e aireplay-ng -2 -b $apMAC -h $clientMAC -d FF:FF:FF:FF:FF:FF -t 1 $aireDevice &
elif [ $Decision2 == 4]; then
xterm -e aireplay-ng -3 -b $apMAC -h $clientMAC $aireDevice &
elif [ $Decision == 5 ]; then
xterm -e aireplay-ng -4 -b $apMAC -h $clientMAC $aireDevice &
elif [ $Decision2 == 6 ]; then
xterm -e aireplay-ng -5 -b $apMAC -h $clientMAC $aireDevice &
elif [ $Decision == 7 ]; then
xterm -e aireplay-ng -6 -b $apMAC -h $clientMAC $airDevice &
elif [ $Decision2 == 8 ]; then
xterm -e aireplay-ng -7 -b $apMAC -h $clientMAC $airDevice &
else
echo -n "Invalid input"

done



Error is that done is seen as an error but it is ending the do, while statement
[quote=]
moretest: line 35: syntax error near unexpected token `done'
moretest: line 35: `done'
[/quote]
Any suggestions will be lovely.

Thanks.
red

---

### Post by kaibob on 2009-08-19
A lot of things going on in your script:

* The if command has to end with fi.

* There has to be a space before ending brackets (e.g. [ $Decision2 == 4] won't work).

* You twice use a variable named Decision, which is apparently meant to be Decision2.

* I'm not sure of its purpose, but I don't believe you need the while loop. 

There is a lot more, but the following works and will get you started. BTW, I changed your xterm command to echo for testing. 

```
#!/bin/bash

while true ; do

echo "WPA options:"
echo " 1. Deauthentication"
echo "WEP options:"
echo " 2. Fake authentication"
echo " 3. Interactive Packet Replay"
echo " 4. ARP Request Replay"
echo " 5. Korek Chopchop"
echo " 6. Fragmentation"
echo " 7. Caffe-latte"
echo " 8. Client-Oriented Fragmentation"
echo -e " 9. Exit. But why?\n"

read -p "Please make a selection: " Decision2

if [ "$Decision2" -eq 1 ]; then
   echo 1
elif [ "$Decision2" -eq 2 ]; then
   echo 2
elif [ "$Decision2" -eq 3 ]; then
   echo 3
elif [ "$Decision2" -eq 4 ]; then
   echo 4
elif [ "$Decision2" -eq 5 ]; then
   echo 5
elif [ "$Decision2" -eq 6 ]; then
   echo 6
elif [ "$Decision2" -eq 7 ]; then
   echo 7
elif [ "$Decision2" -eq 8 ]; then
   echo 8
else
   echo "Invalid input" && exit
fi

done
```

---

### Post by redhotfire on 2009-08-19
> **kaibob said:**
> A lot of things going on in your script:

* The if command has to end with fi.

* There has to be a space before ending brackets (e.g. [ $Decision2 == 4] won't work).

* You twice use a variable named Decision, which is apparently meant to be Decision2.

* I'm not sure of its purpose, but I don't believe you need the while loop. 

There is a lot more, but the following works and will get you started. BTW, I changed your xterm command to echo for testing. 

```
#!/bin/bash

echo "WPA options:"
echo " 1. Deauthentication"
echo "WEP options:"
echo " 2. Fake authentication"
echo " 3. Interactive Packet Replay"
echo " 4. ARP Request Replay"
echo " 5. Korek Chopchop"
echo " 6. Fragmentation"
echo " 7. Caffe-latte"
echo " 8. Client-Oriented Fragmentation"
echo " 9. Exit. But why?"
read Decision2


if [ $Decision2 -eq 1 ]; then
echo 1
elif [ $Decision2 -eq 2 ]; then
echo 2
elif [ $Decision2 -eq 3 ]; then
echo 3
elif [ $Decision2 -eq 4 ]; then
echo 4
elif [ $Decision2 -eq 5 ]; then
echo 5
elif [ $Decision2 -eq 6 ]; then
echo 6
elif [ $Decision2 -eq 7 ]; then
echo 7
elif [ $Decision2 -eq 8 ]; then
echo 8
else
echo -n "Invalid input"
fi
```

I had a do while because there are multiple attacks for WEP and I need to loop to do them all. Thanks for all the help.

red

---

### Post by kaibob on 2009-08-19
> **redhotfire said:**
> I had a do while because there are multiple attacks for WEP and I need to loop to do them all. Thanks for all the help.

red
I modified my version of your script. It will continue to loop until you select 9. Thus, you can select 1 and that command will be executed then the menu will be presented again and you can select say 2 and and that command will be executed then the menu will be presented again, and so on. You should make some provision in case the user selects something other than 1 through 9.

---

### Post by redhotfire on 2009-08-20
```

if [[ $Decision2 == 1 ]]; then
xterm -T 'Deauthencation-WPA' -e aireplay-ng -0 10 -a $apMAC -c $clientMAC $aireDevice &
elif [[ $Decision2 == 2 ]]; then
xterm -T 'Fake Authencation-WEP' -e aireplay-ng -1 1 -a $apMAC -h $clientMAC $aireDevice &
elif [[ $Decision2 == 3 ]]; then
xterm -T 'Interactive-Packet-Replay' -e aireplay-ng -2 -b $apMAC -h $clientMAC -d FF:FF:FF:FF:FF:FF -t 1 $aireDevice &
elif [[ $Decision2 == 4 ]]; then
xterm -T 'ARP-Request-Replay' -e aireplay-ng -3 -b $apMAC -h $clientMAC $aireDevice &
elif [[ $Decision2 == 5 ]]; then
xterm -T 'Korek/chopchop-WEP' -e aireplay-ng -4 -a $apMAC -h $clientMAC $aireDevice &
elif [[ $Decision2 == 6 ]]; then
xterm -T 'Fragmentation-WEP' -e aireplay-ng -5 -b $apMAC -h $clientMAC -k 255.255.255.255 -l 255.255.255.255 $aireDevice &
elif [[ $Decision2 == 7 ]]; then
xterm -T 'Caffe-Latte-WEP' -e aireplay-ng -6 -b $apMAC -h $clientMAC $airDevice &
elif [[ $Decision2 == 8 ]]; then
xterm -T 'Client-Oriented-Frag-WEP' -e aireplay-ng -7 -b $apMAC -h $clientMAC $airDevice &
elif [[ $Decision2 == 9 ]]; then
echo -e "Enter the new AP MAC: "
read apMAC
elif [[ $Decision2 == 10 ]]; then
echo -e "Enter the new Client MAC: "
read clientMAC
elif [[ $Decision2 == 11 ]]; then
echo -e "Enter the new device to inject: "
read aireDevice
elif [[ $Decision2 == 12 ]]; then
exit 1
else
echo -e "Invalid input"
fi

```
I do not know what is wrong right now. It is 2:36am here and I can not stare into a screen anymore. Could someone look over this code and point out what is wrong. I have tried Case and switch statements but could never get them right. Any help would be greatly appreciated.

Thanks,
red

---

### Post by redhotfire on 2009-08-20
```

while [[ $Decision2 != 16 ]]
do

echo -e "WPA options:                      Custom Options:"
echo -e " 1. Deauthentication               13. Aircrack"
echo -e "WEP options:                       14. Tcpdump"
echo -e " 2. Fake authentication            15. packet-forge"
echo -e " 3. Interactive Packet Replay"
echo -e " 4. ARP Request Replay"
echo -e " 5. Korek Chopchop"
echo -e " 6. Fragmentation"
echo -e " 7. Caffe-latte"
echo -e " 8. Client-Oriented Fragmentation"
echo
echo
echo -e "Controling parameters"
echo -e " 9.  Change AP MAC"
echo -e " 10. Change Client MAC"
echo -e " 11. Change injecting device"
echo -e " 12. Open separate bash prompt"
echo
echo -e " 16. Exit, Close"
echo
echo -n "Enter command: "
read Decision2

if [[ $Decision2 == 1 ]]; then
xterm -T 'Deauthencation-WPA' -e 'aireplay-ng -0 10 -a $apMAC -c $clientMAC $aireDevice ; bash' &
elif [[ $Decision2 == 2 ]]; then
xterm -T 'Fake Authencation-WEP' -e 'aireplay-ng -1 1 -a $apMAC $aireDevice ; bash' &
elif [[ $Decision2 == 3 ]]; then
xterm -T 'Interactive-Packet-Replay' -e 'aireplay-ng -2 -b $apMAC -h $clientMAC -d FF:FF:FF:FF:FF:FF -t 1 $aireDevice ; bash' &
elif [[ $Decision2 == 4 ]]; then
xterm -T 'ARP-Request-Replay' -e 'aireplay-ng -3 -b $apMAC -h $clientMAC $aireDevice ; bash' &
elif [[ $Decision2 == 5 ]]; then
xterm -T 'Korek/chopchop-WEP' -e 'aireplay-ng -4 -a $apMAC -h $clientMAC $aireDevice ; bash' &
elif [[ $Decision2 == 6 ]]; then
xterm -T 'Fragmentation-WEP' -e 'aireplay-ng -5 -b $apMAC -s $clientMAC -d FF:FF:FF:FF:FF:FF $aireDevice ; bash' &
elif [[ $Decision2 == 7 ]]; then
xterm -T 'Caffe-Latte-WEP' -e 'aireplay-ng -6 -b $apMAC -h $clientMAC $airDevice ; bash' &
elif [[ $Decision2 == 8 ]]; then
xterm -T 'Client-Oriented-Frag-WEP' -e 'aireplay-ng -7 -b $apMAC -h $clientMAC $airDevice ; bash' &
elif [[ $Decision2 == 9 ]]; then
echo -n "Enter the new AP MAC: "
read apMAC
elif [[ $Decision2 == 10 ]]; then
echo -n "Enter the new Client MAC: "
read clientMAC
elif [[ $Decision2 == 11 ]]; then
echo -n "Enter the new device to inject: "
read aireDevice
elif [[ $Decision2 == 12 ]]; then
xterm -T "New Bash" -e 'bash' &
elif [[ $Decision2 == 13 ]]; then
xterm -T 'Aircrack' -e 'aircrack-ng $fileLocation-01.cap ; bash' &
elif [[ $Decision2 == 14 ]]; then
xterm -T 'Tcpdump' -e 'tcpdump -n -e -s0 -vvv -i $aireDevice | grep -i DeAuth ; bash' &
elif [[ $Decision2 == 15 ]]; then
echo -n "What is the .xor file called: "
read xorlocation
xterm -T 'Packet-forge' -e ' packetforge-ng -0 -a $apMAC -h $clientMAC -k 255.255.255.255 -l 255.255.255.255 -y $xorLocation -w arp-request ; bash' &
elif [[ $Decision2 == 16 ]]; then
echo hi
elif [[ $Decision2 == 17 ]]; then
echo "$apMAC"
echo "$clientMAC"
echo "$aireDevice"
else
exit 1

fi

done

```
The code links under laps some of the air suite statements.
I do no what is wrong, I added Bash as a second command to see the error. It shows up saying Invalid AP MAC, but when I put it again, directly from airodump, it still says it is wrong. Is the problem with the if...else statements or the xterm statements. Lastly, I know many if...else statements looks cluttered but I could not get switch or case statements working. Any help would be greatly appreciated.

Thanks,
red

---

### Post by redhotfire on 2009-08-20
Someone has to be able to decipher Bash.

---

### Post by llamabr on 2009-08-20
I don't know what aireplay-ng is, but why are you trying to run these through xterm?

---

### Post by Brandon Williams on 2009-08-20
Variable expansion will not happen inside of single quotes. For example, replace this:
```
xterm -T 'Deauthencation-WPA' -e 'aireplay-ng -0 10 -a $apMAC -c $clientMAC $aireDevice'
```
with this:
```
xterm -T 'Deauthencation-WPA' -e "aireplay-ng -0 10 -a $apMAC -c $clientMAC $aireDevice"
```
or drop the xterm call and just do:
```
aireplay-ng -0 10 -a $apMAC -c $clientMAC $aireDevice
```

Also, when you're doing arithmetic comparisons, use -eq and -ne instead of == and !=. The later two are for string comparisons.

---

### Post by Brandon Williams on 2009-08-20
Please just open one thread per issue.

---

### Post by bodhi.zazen on 2009-08-20
I merged all 4 of your threads.

As has been stated, please do not start multiple threads on the same topic. Doing so causes confusion and duplication of effort.

In addition FYI we do have a Programming Talk Section, which is where I am moving this ...

---

