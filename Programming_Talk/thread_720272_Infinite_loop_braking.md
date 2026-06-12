---
title: "Infinite loop braking"
date: 2008-03-10
forum: Programming Talk
---

### Post by alan888 on 2008-03-10
Hi all:

I'm writting an GUI for read data from a DAQ card. I have a DAQ card, and an application for read data from it. This application write a file in the current directory. I use some [ROOT]("http://root.cern.ch") libraries for show some histograms of data from the DAQ card.

I was made an infinite loop, in wich I call the external application that write a file and later I read it, but I could put a "Cancel" button for break the loop, but the system is out while run this loop, and I can't push this button. 

My code is somthing like this:

while(1){
    if(stopFlag==false)
        break;
    system("application")
    readFile();
}

ROOT accept the use of Signal/Slot. I was thinking in use it, but I don't know how.

---

### Post by Zugzwang on 2008-03-10
I guess you have to look into threading such that the GUI event handling stuff can be done in parallel to your computation loop. Since you didn't tell use which language/framework you used, we can't help you any further at this point (for everyone else: feel free to disagree, please).

---

### Post by aks44 on 2008-03-10
See [this thread]("http://ubuntuforums.org/showthread.php?p=3612446") (and more specifically [this post]("http://ubuntuforums.org/showthread.php?p=3621110")), as well as [this thread]("http://ubuntuforums.org/showthread.php?t=643391&highlight=message+event+loop").

You'll understand why your Cancel button doesn't react, and how to remedy to it... ;)


Please come back to us if you have a toolkit-specific problem :)



> **Zugzwang said:**
> I guess you have to look into threading such that the GUI event handling stuff can be done in parallel to your computation loop.
There are other, simpler ways than going multithreaded to achieve the same result. :)

---

### Post by Zugzwang on 2008-03-10
> **aks44 said:**
> There are other, simpler ways than going multithreaded to achieve the same result. :)

Uuuh, I forgot about that. Sorry! :-) Hopefully the OP has this possibility in his/her framework.

---

