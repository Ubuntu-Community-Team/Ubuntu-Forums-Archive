---
title: "Changing User Accounts user name"
date: 2013-08-05
forum: New to Ubuntu
---

### Post by XG4GRhE on 2013-08-05
How do I change the name of the user account on the top right corner? 

I researched and it said that I have to change the hostname and hosts through the terminal. I did that successfully but the user account name on the top right corner is still the same. I also restarted after.

Also, why can't I use to username I chose on this forum? I logged on and I was given some random letters.

---

### Post by QIII on 2013-08-05
With regard to the forum name, you may post in the Resolution Centre sub forum under the Forum Feedback & Help forum.

---

### Post by deadflowr on 2013-08-05
Yep, the RC is where to go to fix the forums problems.
But if you're meaning changing the name on your desktop, then make a new user.
Then log in as that new user.

Hosts and Hostname has to do with the PC/OS's name, not the user of the PC/OS.

More info would probably be needed to help you do what you want to do.
What exactly do you want to do?

---

### Post by vasa1 on 2013-08-05
Hey, could you please use more informative titles to your questions in future? It helps others if  they "Search Titles Only".

---

### Post by XG4GRhE on 2013-08-05
> **deadflowr said:**
> Yep, the RC is where to go to fix the forums problems.
But if you're meaning changing the name on your desktop, then make a new user.
Then log in as that new user.

Hosts and Hostname has to do with the PC/OS's name, not the user of the PC/OS.

More info would probably be needed to help you do what you want to do.
What exactly do you want to do?

Well I wanted to change the name of my user account on the top right corner. I successfully did that by clicking "User Accounts" and then clicking my name.

So it's fine for now.

Thanks for the reply deadflowr.

---

### Post by steeldriver on 2013-08-05
For the record, you could have done it via the terminal using 'chfn' (**ch**ange **f**ull**n**ame)

```
sudo chfn -f 'New Name' *user*
```

where *user* is your actual username and 'New Name' is the display name you want to change to

---

### Post by oldos2er on 2013-08-06
> **XG4GRhE said:**
> Well I wanted to change the name of my user account on the top right corner. I successfully did that by clicking "User Accounts" and then clicking my name.

So it's fine for now.

Thanks for the reply deadflowr.

Would you please mark your thread as 'Solved'? [s]See my sig for help on how to do so.[/s]

Meanwhile I'll change the thread title to better represent the subject.

---

