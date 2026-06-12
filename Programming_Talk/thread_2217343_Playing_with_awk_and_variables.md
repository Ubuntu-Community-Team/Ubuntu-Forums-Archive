---
title: "Playing with awk and variables"
date: 2014-04-16
forum: Programming Talk
---

### Post by montydepaola on 2014-04-16
This is a script that is used to read values from two different files and combine them into a third, thought it would be a piece of cake but it seams my cake is a dirt cake :(

#!bin/bash
#
# Get Hostname from hostname.txt file
HOST=$(awk 'FNR==1 {printf $1}' /tmp/hostname.txt)
# Get ip address from ipdata.txt
IP=$(awk 'FNR==5 {printf $2}' /tmp/ipdata.txt)
# Create new file with variables
echo "Start File" > /tmp/iphost.txt
echo $HOST >> /tmp/iphost.txt
echo $IP >> /tmp/iphost.txt
echo $HOST $IP >> /tmp/iphost.txt
echo $IP $HOST >> /tmp/iphost.txt
echo "File Done" >> /tmp/iphost.txt

If I do cat /tmp/iphost.txt this is the output
Start File
myhost
192.168.1.15
myhost 192.168.1.15
   myhost.1.15
File Done

I have tried many variations to try and get the second to last line to be myhost 192.168.1.15 but have failed at every attempt so any help would be greatly appreciated

---

### Post by papibe on 2014-04-16
Hi montydepaola.

Try quoting your variables:
```
echo "$IP" "$HOST"
```
or
```
echo "$IP $HOST"
```
Let us know if that helped.
Regards.

EDIT: I would also use regular awk's print instead of printf.

---

### Post by montydepaola on 2014-04-16
> **papibe said:**
> Hi montydepaola.

Try quoting your variables:
```
echo "$IP" "$HOST"
```
or
```
echo "$IP $HOST"
```
Let us know if that helped.
Regards.

papibe
same results as with the first code,
thanks for the quick try

---

### Post by papibe on 2014-04-16
Did you try the other suggestion (print instead of printf)?

Regards.

---

### Post by montydepaola on 2014-04-16
> **papibe said:**
> Did you try the other suggestion (print instead of printf)?

Regards.

did that after i tried the different quoting options
also tried to force a third variable at the beginning by adding this...
DIP=ZYXW
echo $DIP $IP $HOST > /tmp/iphost.txt
echo "$DIP $IP $HOST" >> /tmp/iphost.txt
echo $DIP" "$IP" "$HOST" >> /tmp/iphost.txt
none of these work, but a strange thing does happen, the longer the variable DIP is the more numbers I see of IP

---

### Post by steeldriver on 2014-04-16
I suspect your hostname.txt file has some special (non-printing) characters in it - my guess would be Windows line endings (CR-LF) instead of plain newlines

What do you see if you do

```

cat -net hostname.txt

```

---

### Post by montydepaola on 2014-04-16
> **steeldriver said:**
> I suspect your hostname.txt file has some special (non-printing) characters in it - my guess would be Windows line endings (CR-LF) instead of plain newlines

What do you see if you do

```

cat -net hostname.txt

```

it shows
1  tower$

I created it with nano

---

### Post by montydepaola on 2014-04-16
> **montydepaola said:**
> it shows
1  tower$

I created it with nano

sorry wrong box...
1 myhost$

---

### Post by papibe on 2014-04-16
Could you do the same with ipdata.txt?
```
cat -net /tmp/ipdata.txt
```
Another idea to tell if there's special characters would be to add 'od' to translate them:
```
#!/bin/bash
# Get Hostname from hostname.txt file
HOST=$(awk 'FNR==1 {printf $1}' /tmp/hostname.txt)

# Get ip address from ipdata.txt
IP=$(awk 'FNR==5 {printf $2}' /tmp/ipdata.txt)

# Create new file with variables
echo "Start File" > /tmp/iphost.txt
echo "$HOST" | **od -a**  >> /tmp/iphost.txt
echo "$IP"   | **od -a**  >> /tmp/iphost.txt
echo "File Done" >> /tmp/iphost.txt
```
Regards.

---

### Post by Vaphell on 2014-04-16
it definitely looks like an issue with \r. It rolls the cursor back to the start of the line after printing the first var, so visually the 2nd one overwrites it.

```
$ ip=$'192.168.1.15\r'; host=$'myhost\r'
$ echo "$ip $host"
 myhost.1.15
```

you may add -F"[ \t\r]+" param to awk to include \r in its field separator regex (space+tab by default) so it doesn't get into values
you may remove the \r from the files eg with sed 's/\r//g'
you may strip the \r from variables ${ip//$'\r'/} ${host//$'\r'/}

---

### Post by montydepaola on 2014-04-17
> **Vaphell said:**
> it definitely looks like an issue with \r. It rolls the cursor back to the start of the line after printing the first var, so visually the 2nd one overwrites it.

```
$ ip=$'192.168.1.15\r'; host=$'myhost\r'
$ echo "$ip $host"
 myhost.1.15
```

you may add -F"[ \t\r]+" param to awk to include \r in its field separator regex (space+tab by default) so it doesn't get into values
you may remove the \r from the files eg with sed 's/\r//g'
you may strip the \r from variables ${ip//$'\r'/} ${host//$'\r'/}

Awesome find,
I changed the code to this and I no longer have a dirt cake...Thanks for all the help
IP=$(awk 'FNR==5 {printf $2}' /tmp/ipdata.txt)
IP=${IP//$'\r'/}
echo $IP $HOST >> /tmp/iphost.txt

I am kind of puzzled as to why this was not happening when I wrote the host before the ip...
but I have other things to drink about this weekend without having that floating around in the back of my mind :)

Thanks for all the help

---

### Post by papibe on 2014-04-17
Glad you worked that out.

As an alternative, if the whole the file is in Windows format (all '\r\n' instead of plain '\n'), you could change the Record Separator (RS) in awk:
```
IP=$(awk 'BEGIN{ RS="\r\n" }; FNR==5 {printf $2}' /tmp/ipdata.txt)
```
Regards.

---

### Post by montydepaola on 2014-04-17
> **papibe said:**
> Glad you worked that out.

As an alternative, if the whole the file is in Windows format (all '\r\n' instead of plain '\n'), you could change the Record Separator (RS) in awk:
```
IP=$(awk 'BEGIN{ RS="\r\n" }; FNR==5 {printf $2}' /tmp/ipdata.txt)
```
Regards.

Thanks for the response papibe,
I have made sure that all the files in use have been created and edited with either nano or gedit and never opened anywhere else.
However this is a great idea as this project will be used by others so I will recode it just in case they use notepad
or another editor to change the files.

Thanks

---

