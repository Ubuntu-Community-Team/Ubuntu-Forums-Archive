---
title: "Loss of root and user etc."
date: 2012-03-03
forum: New to Ubuntu
---

### Post by leilton on 2012-03-03
Have now been using Ubuntu and Kubuntu on this Laptop for some time.

Have, on all occasions logged in in exactly the same way.   Now told that I am not recognized, tried to use terminal to get into Software Center, told no user name, cannot get into Synaptic Center, (that had to be via terminal,now that does not work).

Is it just me thats an idiot, or have I touched something I should not have done.

Can open,occasionally,software center, but cannot install or remove, just sits and defies me to do anything.

Please how do I get back to being other than a guest in my own system.

Hope I'v explained this correctly.

:confused:

---

### Post by Bucky Ball on 2012-03-03
Yes, explained, but what machine and release are you using?

---

### Post by leilton on 2012-03-03
> **Bucky Ball said:**
> Yes, explained, but what machine and release are you using?


Sorry, when I ask Terminal, it says 11.10

My Laptop is an OKINB0108, and until approx this time yesterday all, both Ubuntu and Kubuntu, were operating perfectly, which is why I wondered if I had done something wrong.

Except for removing Amorok, which I detest, that was only thing I did out of ordinary.

Does this help?

:confused:

---

### Post by Bucky Ball on 2012-03-03
Possibly, but can't help you with what it is. Wondering if Amorak dragged out something when it uninstalled that has effected your user. Do you remember seeing anything about removing other packages apart from Amorak? (If using Synaptics it would have mentioned ...) 

Have you done an update lately? Guess you would have mentioned ...

What does it say in 'System Monitor'? Does that also say 11.10?

---

### Post by linux6994 on 2012-03-03
Had same issue Guest only, not sure if it was me playing too much which is usually the case. lost main user desktop. Had to copy out and reload. There might be other remidies but this is what I did:

WHAT DID NOT WORK - since my user basic data was still in /home/you. I thought best to reinstall WITHOUT formatting your partion for /. To maintain all that is in /home/you while restoring operating packages. I eneded up at the same place, not being able to get the unity desktop to open. Except for Guest.

WHAT DID WORK - To be safe you can go in a Guest, open terminal, su - you, enter password, sudo nautilus, enter password for you. Use nautilus to copy out all of your stuff in /home/you including hidden files.

In the hidden files you will have your .mozilla (firefox), .thunderbird (if you use it) and any other apps you wish to keep basic data for.

After reinstalling with reformatting, I once again had unity-desktop back again. Do not reuse the copied .profile or .copmpiz-1 files since they did not help your main user to get to the desktop before. (if they were at fault?

Copy back in your .mozilla, .thunderbird and such back in. Use software center to bring in apps that you had been using.

Hope this helps?
Good Luck

---

### Post by leilton on 2012-03-03
> **Bucky Ball said:**
> Possibly, but can't help you with what it is. Wondering if Amorak dragged out something when it uninstalled that has effected your user. Do you remember seeing anything about removing other packages apart from Amorak? (If using Synaptics it would have mentioned ...) 

Have you done an update lately? Guess you would have mentioned ...

What does it say in 'System Monitor'? Does that also say 11.10?

Yes update when and if advised there are any.

Just has a look at System Monitor, KDE,  and would you believe it says 4.7.4 (thought would be same as Ubuntu).   Must admit that as I am a complete novice patition etc. wise, that I took advise of Forum member and downloaded package for KDE from Synaptic.

Should I try to get KDE updated?


Thanks for your help so far.   We idiots need all the help we can get.


:confused:

---

### Post by leilton on 2012-03-03
> **linux6994 said:**
> Had same issue Guest only, not sure if it was me playing too much which is usually the case. lost main user desktop. Had to copy out and reload. There might be other remidies but this is what I did:

WHAT DID NOT WORK - since my user basic data was still in /home/you. I thought best to reinstall WITHOUT formatting your partion for /. To maintain all that is in /home/you while restoring operating packages. I eneded up at the same place, not being able to get the unity desktop to open. Except for Guest.

WHAT DID WORK - To be safe you can go in a Guest, open terminal, su - you, enter password, sudo nautilus, enter password for you. Use nautilus to copy out all of your stuff in /home/you including hidden files.

In the hidden files you will have your .mozilla (firefox), .thunderbird (if you use it) and any other apps you wish to keep basic data for.







After reinstalling with reformatting, I once again had unity-desktop back again. Do not reuse the copied .profile or .copmpiz-1 files since they did not help your main user to get to the desktop before. (if they were at fault?

Copy back in your .mozilla, .thunderbird and such back in. Use software center to bring in apps that you had been using.

Hope this helps?
Good Luck

Thanks for the info.   Will give this a go tomorrow.   Bit dense re a  lot of the work involved, so going to print it out and go thru step by  step.

Let you know how I get on.

Did wonder if I would be better off removing and then reinstalling, but seems a bit drastic.

:confused:

---

### Post by Bucky Ball on 2012-03-03
> **leilton said:**
> 

Did wonder if I would be better off removing and then reinstalling, but seems a bit drastic.

:confused:

Last resort, but not out of the question. Sometimes easier that way if you have only just installed but sounds like you're well under way so I would hold off. ;)

---

