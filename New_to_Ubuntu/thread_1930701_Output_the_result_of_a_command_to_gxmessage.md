---
title: "Output the result of a command to gxmessage"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2012-02-24
Hi Guys,

I'd like to have a popup that shows my wi-fi address (the 192.168... address) and my ethernet address.

I can get these to show in the terminal, but don't know how to send the output to gxmessage.

I have this:

```

#!/bin/bash
ifconfig eth0 | grep 'inet addr:' | cut -d: -f2 | awk '{ print $1}'
ifconfig wlan0 | grep 'inet addr:' | cut -d: -f2 | awk '{ print $1}'


gxmessage -center \
          -buttons "OK":1 \
      -geometry 400x250 \
          -font "serif 22" \
     -title "Notice" 'IP Addresses.'

```All I get is a blank popup labeled IP Addresses.   
Ideally, I'd also have the labels Wi-Fi and Ethernet before each address.

Could someone give me a clue? I'd really appreciate it.

---

### Post by aeiah on 2012-02-24
i dont know about gxmessage, but ive always used the normal notification bubbles for notifications, and zenity for dialog boxes that i need an ok/cancel for.

to send a message to the notification daemon, you can use notify-send. you can also use icons and such.

anyway. it looks like your problem is that your gxmessage command doesn't contain the ip information. you should assign your ifconfig commands to variables, and then use those variables in your gxmessage command. the following is untested, but if it doesn't work i hope you at least see what im getting at. the idea is that you store the results of the commands as the variables $wired and $wireless and then using them later on within your gxmessage command

```


#!/bin/bash
wired=`ifconfig eth0 | grep 'inet addr:' | cut -d: -f2 | awk '{ print $1}'`
wireless=`ifconfig wlan0 | grep 'inet addr:' | cut -d: -f2 | awk '{ print $1}'`


gxmessage -center \
          -buttons "OK":1 \
      -geometry 400x250 \
          -font "serif 22" \
     -title "IP Addresses" 'ethernet: $wired \nwifi: $wireless'


```

---

### Post by greenpeace on 2012-02-24
> **GrouchyGaijin said:**
> 
Could someone give me a clue? I'd really appreciate it.

Hi, you need to assign the output of your IP-getting script to something, and then pass that as the last argument to gxmessage:

This works on my machine:

```
#!/bin/bash
ip=`ifconfig wlan0 | grep 'inet addr:' | cut -d: -f2 | awk '{ print $1}'`

gxmessage -center\
         -buttons "OK":1\
         -geometry 400x250z 
         -font "serif 22"\  
         -title "IP Addresses" \     
         $ip

```

to add the eth0 IP as well I would recommend that you google "concatenate strings in Bash"... :)

---

### Post by GrouchyGaijin on 2012-02-24
Thanks Guys,

Unfortunately  solution one produced a popup that said 
```

'ethernet: $wired \nwifi: $wireless'

```
and the second suggestion didn't do anything at all.

---

