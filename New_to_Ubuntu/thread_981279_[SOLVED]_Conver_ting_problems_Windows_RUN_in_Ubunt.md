---
title: "[SOLVED] Conver ting problems Windows RUN in Ubuntu? The Linux way to connect to a se"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Norfeldt on 2008-11-13
Hello Linux-users ):P

Im trying to convert from the lame MS til linux.. But it is not easy..

I finally found out how to connect to my vpn client by the linux-stile.
If any has the same problem I have the link to the answer here :
[http://64.233.183.104/search?q=cache:9d4CPk0Qa1kJ:kamilkisiel.blogspot.com/+how+to+use+pcf2vpnc&hl=da&ct=clnk&cd=12&gl=dk&client=firefox-a]("http://64.233.183.104/search?q=cache:9d4CPk0Qa1kJ:kamilkisiel.blogspot.com/+how+to+use+pcf2vpnc&hl=da&ct=clnk&cd=12&gl=dk&client=firefox-a")

So now I can access internet from my schools wireless network, but how do I connect to the server/my private folder?

In windows I used to START/RUN and then type something like this \\SERVERNAME\MYFOLDER
And it would ask me for my username and pass... 

what's the linux-stile to do it?

---

### Post by chrisod on 2008-11-13
The 'Connect to Server" dialog box is available under the "Places" menu.

---

### Post by Norfeldt on 2008-11-14
I have tried that one.. But I must be doing something wrong.. What shall I those and can't I use \\SERVERNAME\PLACE or do I have to have an ip or something like that?

I'm also in doubt about how to type my username in the "connect to server". In windows I used to type
USER: organization/username
PASSWORD: *******

---

### Post by stevebond001 on 2008-11-14
Hi
Try selecting "Connect to Server" from the "Places" menu
When the program starts, select "Windows Share" from the Service Type drop down list.
You then need to enter your server name, share name, user name and password - an example is as per the attached screen shot (obviously, you need to fill in your specific stuff)
When you have filled this all in click on "connect" and assuming that the server name can be resolved by your PC (is it in the hosts file, for example) then the shared folder should be displayed.

Hope this helps

---

### Post by Norfeldt on 2008-11-14
:grin:
It worked!!! IT FINALLY WORKED!!!
THX!!!

---

### Post by SeanHodges on 2008-11-14
> **Norfeldt said:**
> 
In windows I used to START/RUN and then type something like this \\SERVERNAME\MYFOLDER
And it would ask me for my username and pass... 

what's the linux-stile to do it?

Also, to get that Start->Run style of connecting to other machines:

1) Press Alt-F2
2) Type "smb://SERVERNAME/MYFOLDER" then hit Enter

Basically, just translate "\\" to be "smb://" and change backslashes to forward ones.

---

### Post by Norfeldt on 2008-11-15
Again thanks.. that worked to... :)
The best about this linux is that it really remember my password. MS didn't do that even if I marked that it should.

---

