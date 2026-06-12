---
title: "Player trend graph"
date: 2018-03-15
forum: New to Ubuntu
---

### Post by grofstepe on 2018-03-15
hello
1.i ma sorry if i post in wrong section, please moderators to remove thread if i post wrong section 

i use ubuntu 14 but i have small problem
here is problem
can anyone explaine why i see this and how to solve this problem
thanks

---

### Post by &amp;KyT$0P# on 2018-03-15
If you are serious about wanting help, you need to provide a more specific description and a LOT more details.

---

### Post by lisati on 2018-03-15
Hello, grofstepe

I have edited the title of your thread, "please help" doesn't tell us much.

Elsewhere, you have indicated that you are running Ubuntu 16.04, was "14" a typo?

What program are you running when you see that display?

---

### Post by deadflowr on 2018-03-15
The image shows the generic icon symbol.
Meaning whatever the app you are trying to run does not have, or for some reason cannot show, the proper icon for it.

---

### Post by grofstepe on 2018-03-16
hello
i am sorry for not giving enough details
i will try now
i use ubuntu 14.04 and this problem i see here
[http://173.212.241.203/hlstatsx/hlstats.php?mode=playerinfo&player=82](http://173.212.241.203/hlstatsx/hlstats.php?mode=playerinfo&player=82)

one month ago when i had ubuntu 16.04 i didnt have this problem and its showing normal trend graph
but now when i install ubuntu 14.04 and i install hlstatsx:ce and i have this problem now
maybe is missing something on ubuntu 14.04
maybe java or something else

---

### Post by Holger_Gehrke on 2018-03-16
If you look at the html source of the page [http://173.212.241.203/hlstatsx/hlst...info&player=82]("http://173.212.241.203/hlstatsx/hlstats.php?mode=playerinfo&player=82") , you'll see that the graph is produced by a script at [http://173.212.241.203/hlstatsx/trend_graph.php?bgcolor=282828&color=FFFFFF&player=82](http://173.212.241.203/hlstatsx/trend_graph.php?bgcolor=282828&color=FFFFFF&player=82) , If you put the address for that script directly into your browser's address bar, you'll get an error message that makes it very likely that there's something wrong server-side. Might be a permission problem with the directory where the script tries to put the graph ...

Holger

---

### Post by grofstepe on 2018-03-16
hi Holger_Gehrke and thanks for reply
do u maybe know how to fix this

---

### Post by &amp;KyT$0P# on 2018-03-16
Thanks for providing more information, grofstepe.

> **Holger_Gehrke said:**
> If you put the address for that script directly into your browser's address bar, you'll get an error message that makes it very likely that there's something wrong server-side. 
For me it redirects to [http://173.212.241.203/hlstatsx/hlstatsimg/progress/trend_82_1520809200.png]("http://173.212.241.203/hlstatsx/hlstatsimg/progress/trend_82_1520809200.png"), which gives me a "Not Found" error.

grofstepe, I suggest you contact the site to report this problem to them.

---

### Post by grofstepe on 2018-03-16
i have my own vps
this site i cant contact beacuse is old and not updated and does not exist anymore
anyway thanks for answer

---

### Post by grofstepe on 2018-03-16
hello guys, i want to thanks all of you for your time and answers
i fix the problem
i need to tell how i fix
the hlstats_web/hlstatsimg/progres i chmod to 777
and now its showing
thanks you guys
have a nice day

---

