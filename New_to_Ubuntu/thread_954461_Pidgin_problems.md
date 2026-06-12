---
title: "Pidgin problems"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by avjois89 on 2008-10-21
Hello...

On my computer i tend to have a recurring problem with pidgin. It signs in with my name and ID but the status of "connecting" does not change and it does not display and my friend list and particulars for the respective ID's. My ID's exist and exist. 
If i log in through yahoo messenger for windows it does not give me any problems.

Please help me out...i dont like using windows to be honest to IM my friends and pidgin in really nice.(although its causing me to restart my computer each time i have to IM.)
 Thanks beforehand...:)

---

### Post by fr.theo on 2008-10-21
just a couple of questions are you using msn,  do you want to see you buddies in pidgin list? is this what you are looking for.

---

### Post by greg@localhost on 2008-10-21
> **avjois89 said:**
> Hello...

On my computer i tend to have a recurring problem with pidgin. It signs in with my name and ID but the status of "connecting" does not change and it does not display and my friend list and particulars for the respective ID's. My ID's exist and exist. 
If i log in through yahoo messenger for windows it does not give me any problems.

Please help me out...i dont like using windows to be honest to IM my friends and pidgin in really nice.(although its causing me to restart my computer each time i have to IM.)
 Thanks beforehand...:)

I had a very similar problem with Pidgin under Fedora 8 - i had to set my status to another i.e offline, then back to online to get it to connect.

---

### Post by bogdan.veringioiu on 2008-10-21
Hi.

You could try to change the pager port in the connection settings from 5050, to 25 (it is working for me this way). If you are behind some firewall, probably not all ports are open to outside world.

Bogdan

---

### Post by avjois89 on 2008-10-22
Pidgin does not connect at all...the status doesnt change from "connecting" to "available". Nor does it say network timeout or any such message when you have a slow connection...i tried changing the pager port as well to no avail.
Its starts and tends to suspend itself in the connecting state without changing at all. The friend list options as to whom to display (i.e only online friends or all friends) are all set properly.

I am using 3 ID's two google and one yahoo.
And i have no firewall as well.

Thanks...

---

### Post by greg@localhost on 2008-10-22
> **avjois89 said:**
> Pidgin does not connect at all...the status doesnt change from "connecting" to "available". Nor does it say network timeout or any such message when you have a slow connection...i tried changing the pager port as well to no avail.
Its starts and tends to suspend itself in the connecting state without changing at all. The friend list options as to whom to display (i.e only online friends or all friends) are all set properly.

I am using 3 ID's two google and one yahoo.
And i have no firewall as well.

Thanks...

Did you try toggling your status to offline and then back to online? As I said, I had a what seems to be a very similar issue and this worked for me.

---

### Post by Sarmacid on 2008-10-22
Maybe this problem is caused by an add on. If you have any, you should turn them off and try.

---

### Post by avjois89 on 2008-10-27
> **Sarmacid said:**
> Maybe this problem is caused by an add on. If you have any, you should turn them off and try.
I disabled all the plugins and am tryin to access it...to no avail...:confused:...the thing is that i am a student and the college has banned the students from downloading torrents (for obvious reasons) the router in the hostel whose ports were forwarded for that purpose have been enabled only for browsing....it has been like this for quite a while now and pidgin has not been working since...could this have anything to do with the fact that pidgin is unable to establish a connection...

sorry for the late reply...my laptop graphics card conked out...had to get it fixed...:)

---

### Post by reg4c on 2008-10-27
Try removing all the accounts that you have in Pidgin then adding them one by one.

As you add one try connecting to it. If it manages to connect properly then add another one. Do that until all the accounts are added or you find an account that mucks everything up...

Cheers

---

### Post by Keen101 on 2008-10-27
Try pidgin in windows and see if it works there. It should work fine. I have provided a picture of my yahoo acount (from windows) just to show you that it should be simple. Just make sure your username is correct, and your password is correct.

---

### Post by avjois89 on 2008-10-28
Tried pidgin on windows also and even thats not working! I have no idea as to why. And as for reg4c's solution i tried it in all combinations of my ID's in windows and ubuntu but the connecting status just does not change to connected or available...these ID's are verfied ones and do exist..i have yahoo messenger on windows and google talk as well and they log in perfectly....

Thanks for hanging on guys...

---

### Post by avjois89 on 2008-10-29
Well...i kind of found out the problem...the ports that pidgin uses in our server were the ones used for torrents..i suppose when they dissallow those ports pidgin doesnt work...this was all i could gather from wat i heard at my hostel...thanks a lot..this problem really has no solution other than to change my connection.

My ignorance...thanks once more...

---

