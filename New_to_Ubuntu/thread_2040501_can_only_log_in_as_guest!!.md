---
title: "can only log in as guest!!"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by twhilden7 on 2012-08-11
long story short- I remember installing some updates before work. i can't recall doing any thing else outta the ordinary. after leaving to go to work i come home from work 9 hours later and turn my computer on and i can only log in as guest. neither my account nor my brother account will long in (we don't normally use his at all) when i type my password in it flashes a black screen and goes back to the login screen (doesn't say wrong password or anything like that) everything looks the same as when i first try logging in. any help on how to get this fixed??  

ps. i logged in as guest and created a new administrator account, logged out of guest, and tried logging in as the new account and same thing happens.

i don't know what the software updates were either.

---

### Post by Frogs Hair on 2012-08-11
Check the software center > history for update history , it will tell you what update may have caused the problem. I don't Know if this is applicable or not. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by NikTh on 2012-08-11
Hi , 
login from guest account and open a terminal. 
run this command 
```
sudo chown username:username /home/username/.Xauthority
``` 

replace username with your actual username. 
Thanks

---

