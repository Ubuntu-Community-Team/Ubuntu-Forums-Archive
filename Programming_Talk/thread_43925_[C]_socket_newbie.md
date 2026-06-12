---
title: "[C] socket newbie"
date: 2005-06-23
forum: Programming Talk
---

### Post by billiejoex on 2005-06-23
Hi all. 
I got a basical knowledge of C sintax on Windows platforms and I would try to begin  learning socket programming to create some simple TCP/IP applications. Here's some question:

1) First of all I'd have need a good resource on wich I could study on. 
An "idiot-guide" in wich also the smaller palrticular is explained. Can you suggest me something in particular?

2) I use windows and a linux platforms too. Does what would be better for me? Socket or winsocket? I got the feeling that the first are easier but the bigger spreading of the Windows platforms could help me with a bigger amount of related documentation.

2b) Are the differences between socket and winsock substantial? 
Supposing that I begin to learn socket programmin do could I have problems to use winsock, in future?
Moreover, does the platforms difference strongly influences on C programming?

3) How much important is the C knowledge? Does it's foundamental to program very well to programming sockets??? 
Personally I think to have an insufficient skill yet. 
I read at some how toes, I know the basics like variabiles, arrays, structures etc... but the gaps are obvious, 

I'm sorry for the quantity of noob questions but I'd really like to begin to create net-related programs. 

Thanks to anyone will help me. 

PS - really sorry for my bad english. 


greetings

---

### Post by pdpi on 2005-06-23
Personally, I'd advise getting pretty confortable with more "standard" stuff before moving on to sockets. I'd suggest in particular that you get some experience in file handling, as sockets (especially in linux) have some strong similarities with files.

I just googled and found this guide, seems decent:
[http://www.ecst.csuchico.edu/~beej/guide/net/](http://www.ecst.csuchico.edu/~beej/guide/net/)

---

### Post by MoneyCat on 2005-06-23
I would recommend this great inexpensive book on socket programming in C:

[http://www.amazon.com/exec/obidos/tg/detail/-/1558608265/qid=1119580433/sr=8-1/ref=pd_csp_1/104-1636868-9091162?v=glance&s=books&n=507846](http://www.amazon.com/exec/obidos/tg/detail/-/1558608265/qid=1119580433/sr=8-1/ref=pd_csp_1/104-1636868-9091162?v=glance&s=books&n=507846)




Good Luck

---

### Post by LordHunter317 on 2005-06-23
The best guide online is 'Beej's Socket Guide' or similiar, google for it.

And you need a strong, throuogh background in C before starting.  Get a good book and make sure you understand all the concepts first.

WinSock is almost identical to BSD sockets.  For most applications, you just have some extra code to initalize, and a few different constants.  Otherwise, it's mostly identical.

---

### Post by globe_trotter on 2005-06-24
Hi!
I found useful the "Unix Network Programming" 3rd edition (Stevens,Fenner,Rudoff)
and about C language [http://cm.bell-labs.com/cm/cs/cbook/](http://cm.bell-labs.com/cm/cs/cbook/)
I think the last one could be considered as the C language's bibble...

I also founded really useful to give a look to sources and makefiles of other project..
Hope i'm been useful for you...

(sorry for bad english  :razz: )

---

### Post by pdpi on 2005-06-24
Lord Hunter: I provided a direct link to Beej's :) It seems that google agrees with you in that it is the best sockets tutorial.

---

### Post by LordHunter317 on 2005-06-24
Hrm, you did indeed.  I must have been typing on autopilot or something to not have recogonized it for what it was.  My apologies.

---

### Post by pdpi on 2005-06-25
Perfectly ok, I posted it on the basis of "just found it on google, seems reasonably well structured and covers the basics". You actively reccomended it. So all's well :)

---

