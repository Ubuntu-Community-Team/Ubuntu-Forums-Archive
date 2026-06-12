---
title: "python debugging question"
date: 2006-03-08
forum: Programming Talk
---

### Post by krypto_wizard on 2006-03-08
I am a python newbie. I have writen some 500 lines of code. There are 4 classes and in all 5 files. 

Now, I am trying to run the program. I am getting wrong values for the simulation results.
Is there any debugging facilities in python which would let me go step by step and check the values of the variables at every step. I have done something like this in MS Visual Stdio 6.0 sometime back. 

For pytho, I am using SPE.

Every help is appreciated.

Thanks

---

### Post by thumper on 2006-03-08
How do you know that they are wrong?

Yes SPE does integrate the dubugger, but I have not used it.

Perhaps Stani is watching?

---

### Post by krypto_wizard on 2006-03-08
In my simlation there 1024 nodes and I am mimicking a bittorrent file exhange process. Some nodes are not getting any file pieces, so it means that my program is erroneous. 

what is a good way of debugging such large and iterative programs ? Any tips.




[QUOTE=thumper]How do you know that they are wrong?

Yes SPE does integrate the dubugger, but I have not used it.

Perhaps Stani is watching?[/QUOTE]

---

### Post by stani on 2006-03-22
[QUOTE=thumper]Perhaps Stani is watching?[/QUOTE]
Yep!

I've you want a nice introduction to winpdb debugger which ships with SPE, watch this: [http://www.showmedo.com/videoListPage?listKey=PythonDevelopmentWithSPE](http://www.showmedo.com/videoListPage?listKey=PythonDevelopmentWithSPE)

---

