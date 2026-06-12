---
title: "need help"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by phoenixrising888 on 2008-04-22
I cant get into my Synaptic Package Manager.It says E: dpkg was interrupted,must maually run 'dpkg --configure -a to correct the problem.
I opened my terminal and manually tried to run it but it came up with the
same error.not sure what to do know.any help would be greatly appreciated.
thanks.

---

### Post by PinkFloyd102489 on 2008-04-22
All you need to enter is:
```
sudo dpkg --configure -a
```


Then do what you were trying to do.

---

### Post by Joeb454 on 2008-04-22
You need to enter the above into a terminal (Applications>Accessories>Terminal) just to clear that up :)

Also, note that sudo will ask for your password, which is totally normal, however when you type it in, it will not show any input - don't worry, it is being input :) Just type your password as normal, and hit enter.

---

### Post by wpshooter on 2008-04-22
I have seen this question posed in the threads posted on these forums NUMEROUS times.

My question is why does this problem occur in the first place and secondly if this error is something that is likely to continue to occur in the future, why doesn't someone write a function that could be listed on one of the System/Administration menus (or perhaps some other menu) to fix this problem WHEN it occurs, so this question will not have to be asked over and over and over again.  And NO, I am not a programmer, so I can not fix it !!!

Thanks.

---

### Post by Joeb454 on 2008-04-22
Actually, I've only ever had this happen once with me. And if you'd like to know the cause?

The internet cut out in the middle of the upgrade process, so I terminated it mid-way through installing whatever the package was.

Basically - 90% of the time it's down to human error :)

---

### Post by wpshooter on 2008-04-22
> **Joeb454 said:**
> Actually, I've only ever had this happen once with me. And if you'd like to know the cause?

The internet cut out in the middle of the upgrade process, so I terminated it mid-way through installing whatever the package was.

Basically - 90% of the time it's down to human error :)

I have had this happen to me several times and it was probably due to lose of Internet BUT it was not due to the fact that I terminated it !!!

Thanks.

---

### Post by namegame on 2008-04-22
This happened to me after I upgraded to Hardy and then tried to download from my university's Gutsy repositories.

---

### Post by russo.mic on 2008-04-22
This happens anytime your in the middle of installing some packages, and the database doesn't finish due to loss of internet, or opps a terminal closed or anything like that.

---

### Post by wpshooter on 2008-04-22
> **russo.mic said:**
> This happens anytime your in the middle of installing some packages, and the database doesn't finish due to loss of internet, or opps a terminal closed or anything like that.

If I remember correctly, if this happens when you are installing that other O/S, it is smart enough to recover from this !!!

---

### Post by Joeb454 on 2008-04-22
You've clearly never had a corrupted Windows install :(

---

