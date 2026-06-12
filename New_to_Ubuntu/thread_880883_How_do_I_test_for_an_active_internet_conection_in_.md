---
title: "How do I test for an active internet conection in a shell script?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by hovzio on 2008-08-05
Hi, I found this pretty neat command that checks my IP address from a command line. (Sorry I am not able to give credit to the author, its been a while back, I found it on the ubuntu forums.) Here it is,

```
wget -q -O - http://showmyip.com | grep -m 1 'IP' | awk '{ print $8 }'
```

So I added a little greetings text placed in my bash.rc that goes something like:


```
IPP=`wget -q -O - http://showmyip.com | grep -m 1 'IP' | awk '{ print $8 }' `
echo "Hlo .... $USER"
date
w
echo " this is your ip: $IPP " 
```

It all works fine except if there is no network connection, then it can take up to a minute to start bash. I don't know the best way to go about doing this but I figured I would test to see if there was an aktive network connection and only then echo the output of the variable $IPP. So how can I test for a active internet connection? Then I have to echo the command only if there is a connection. How can I do this? Appreciate an examples. I'm sure there are many other ways to this and am more than open for any suggestions. I'm really just exploring and having fun with it so I really appreciate any input. Thanks:)

---

### Post by ibuclaw on 2008-08-05
you could use "ping" if you get the IP address of the site.

ie:
```
ping -c 1 192.168.1.1
if [ $? -eq 0 ] #successful run
then #do stuff
fi
```

Regards
Iain

---

### Post by hovzio on 2008-08-05
> **tinivole said:**
> you could use "ping" if you get the IP address of the site.

ie:
```
ping -c 1 192.168.1.1
if [ $? -eq 0 ] #successful run
then #do stuff
fi
```

Regards
Iain

hi, thanks it worked great! :) I just was wondering, can you test to see if there are certain files in the proc or dev filesystem that indicate weather or not there is an active network connection? (What are these files, how can one find out?) I'm still at the beggining of things and I am trying to learn how to test to see if certain things are taking place, like testing to see if skype is running or testing for any active ssh connections. Thanks again!

---

