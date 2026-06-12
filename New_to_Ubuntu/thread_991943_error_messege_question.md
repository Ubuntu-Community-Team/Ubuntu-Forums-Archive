---
title: "error messege question"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by nu2this2 on 2008-11-24
This appeared when I tried to update today. What can I do?


 [ATTACH]93968[/ATTACH]

---

### Post by marufaberlin on 2008-11-24
hmm do what it says. run dpkg --configure -a

---

### Post by sydbat on 2008-11-24
Open a terminal (Applications > Accessories > Terminal) and run the command stated (dpkg --configure -a ).

---

### Post by marufaberlin on 2008-11-24
but you will need to put sudo in front.

---

### Post by jakupl on 2008-11-24
To put it all together.

go to Applications --> Accessories ---> Terminal

write

```
sudo dpkg --configure -a
```

---

### Post by nu2this2 on 2008-11-24
Thanks,

Very new at this. This is what I got :confused::confused:

ken@ken-laptop:~$ sudo dpkg --configure -a
[sudo] password for ken: 
Setting up java-common (0.28ubuntu3) ...

ken@ken-laptop:~$

> **jakupl said:**
> To put it all together.

go to Applications --> Accessories ---> Terminal

write

```
sudo dpkg --configure -a
```

---

### Post by sydbat on 2008-11-24
Now try your updates and see if you get the error again or if the updates proceed. Please let us know.

---

### Post by nu2this2 on 2008-11-24
Thanks again,

We're making progress but now I get the messege "You have one broken packet on your system. Use the "Broken" filter to locate it.

Unfortunately I don't know how to do that.

---

### Post by sydbat on 2008-11-24
Open Synaptic (System > Administration > Synaptic Package Manager - you will be asked for your password) and choose Custom Filters on the lower left side. This will show those filters in the left pane...the top one being Broken. The rest should be pretty self explanatory.

---

### Post by jakupl on 2008-11-24
> **nu2this2 said:**
> Thanks again,

We're making progress but now I get the messege "You have one broken packet on your system. Use the "Broken" filter to locate it.

Unfortunately I don't know how to do that.

Goto System --> Administration --> Synaptic Package Manager

enter your password,

press "custom filters" at the lower left corner and press the "broken" segment.

Now i think you should probably try to remove or reinstall the broken packages.

EDIT: oooohh snap!

---

### Post by nu2this2 on 2008-11-24
Thank you to everyone!! This is truly a great forum and I really appreciate your help.

Somehow the problem is solved and I am up to date.

I did find the broken filter,(thanks to all of you)and when I cliked it, nothing appeared--------------so I guess the problem has been rectified.

Thank you again.

---

### Post by sydbat on 2008-11-24
You're welcome. If you feel this problem is solved, please use the 'Thread Tools' to mark this thread "Solved".

---

