---
title: "Bash e-mail IP renewal"
date: 2009-11-06
forum: Programming Talk
---

### Post by momo971 on 2009-11-06
Hello Ubuntu users.
I wrote a basic bash script to watch my public IP and send me an e-mail using telnet over smtp if my public IP is updated.

I wrote this script because I had troubles with My DSL box automatic DNS update feature as well as ddclient when using dyndns.com.
If i experience any DNS update misfunction, i can't access my home server for a week, and i really need it.
I work hundred miles from home and I need at least to know my public IP address so i can access to my home server.


```
#!/bin/bash

# Base IP
ref_publicip=`wget -q -O - checkip.dyndns.com | sed -e 's/.*Current IP Address: //' -e 's/<.*$//'`
echo "IP : $ref_publicip"

# wait for 2 minutes (2 minutes is for testing purposes)
time_wait(){
sleep 120
}

# compare base IP with Current IP
ip_compare(){

new_publicip=`wget -q -O - checkip.dyndns.com | sed -e 's/.*Current IP Address: //' -e 's/<.*$//'`
if [ "$ref_publicip" = "$new_publicip" ] 
then time_wait
else mail_me
echo -e "New IP: $new_publicip"
fi
}

# mail me if there is a new IP
mail_me(){
(
sleep 2
echo "EHLO smtp.myprovider.com"
sleep 2
echo "MAIL FROM:<momo971@myISPprovider.com>"
sleep 2
echo "RCPT TO:<momo971@another_ISPprovider.com>"
sleep 2
echo "DATA"
sleep 2
echo "Subject:IP Renewed"
sleep 2
echo "$new_publicip"
sleep 2
echo "."
sleep 2
echo "QUIT"
) | telnet smtp.myISPprovider.com 25
}

# infinite loop
while [ 1 ]
do
ip_compare
ref_publicip=$new_publicip
done 
```

I would appreciate if any bash guru had some suggestions to improve the code.
This script actually works, but I think the code can be improved, I didn't wrote code for years and I suspect some kind of bash functions abuse here :p

P.S: sorry for terrible english :(

---

### Post by roccivic on 2009-11-07
Looks good. No particular need for -e option on line 19.

---

### Post by diesch on 2009-11-07
To get the IP address 
```
wget -q -O - checkip.dyndns.com|awk -F'[:<]' '{print $9}'
```
is a bit shorter.

I never tried it but it seems you could place a script in /etc/dhcp3/dhclient-enter-hooks.d/ that then is run every time you get a new IP address via DHCP

Your mail_me() isn't particular reliable. Using *expect* could improve iot a little bit, but I'd rather install a simple local mailer daemon or at least use a real command line mail program like *mutt* to send the mail.

---

### Post by momo971 on 2009-11-08
Hello and thank you for your suggestion.
I think it's a lot better now !


[PHP]
#!/bin/bash 

# SMTP & TIMER parameters
MAIL_FQDN="smtp.YourIsp.com"
MAIL_SENDER="<somebody@YourIsp.com>"
MAIL_RCPT="<somebody@YourIsp.com>"
MAIL_SUBJECT="IP Change"
CHECK_TIME="600" # check every 10 minutes (600 seconds)

# Get IP
REF_PUBLICIP=`wget -q -O - checkip.dyndns.com| awk -F '[:<]' '{print $8}'`
echo "IP: $REF_PUBLICIP"

ip_notifier (){

# Check Gateway
ping -q -w 1 -c 1 `ip r | grep default | awk -F '[ ]' '{print $3}'` > /dev/null 
#echo "Gateway Access OK"
if [ "$?" -eq 0 ]
then
# Compare Old IP with Current IP
NEW_PUBLICIP=`wget -q -O - checkip.dyndns.com|awk -F '[:<]' '{print $8}'`
if [ "$REF_PUBLICIP" = "$NEW_PUBLICIP" ] 
then sleep $CHECK_TIME

#if different e-mail me !
else 
(
sleep 2
echo "EHLO $MAIL_FQDN"
sleep 2
echo "MAIL FROM:$MAIL_SENDER"
sleep 2
echo "RCPT TO:$MAIL_RCPT"
sleep 2
echo "DATA"
sleep 2
echo "Subject:$MAIL_SUBJECT"
sleep 2
echo "$NEW_PUBLICIP"
sleep 2
echo "."
sleep 2
echo "QUIT"
) | telnet $MAIL_FQDN 25
echo "New IP: $NEW_PUBLICIP"
fi
REF_PUBLICIP=$NEW_PUBLICIP
# Gateway Unreachable: 10 sec pause and retry
else sleep 10
fi
ip_notifier 
}
ip_notifier
[/PHP]

---

