---
title: "wxpython : main frame freeze when program is executing operations"
date: 2012-04-06
forum: Programming Talk
---

### Post by yanes on 2012-04-06
Salam all ;) ,

I coded a GUI application in python (wxpython ), "Yanes Pictures Optimizer"
It's a mass images files 
resizer and converter (Supports : bmp,jpg,png,gif,tga,ppm ),
It uses PIL library to do that , 
You can get more infos from the link to **[my site]("http://yaneswares.22web.net") **below 
the program works fine but when manipulating a big number of file (100 for example )
my main frame freezes  and will not respond until program finishes all requested operations  
How keep my frame active durng the operation ?
have I to uses another thread to execute requested tasks to keep my frame 
working ? 

Another thing , (I) think , this proram is useful , so i need some one to spnsor it 
in order to upload it to reposities :) .
Program is packaged into a debian package 

I need someones to test it with some advices to improve it .
this is the link :
[[COLOR=Blue]***Yanes Pictures Optimizer ***[/COLOR]]("http://yaneswares.22web.net/yanespicsoptimizer.htm")
Launchpad : [[COLOR=Blue]***Yanes Pictures Optimizer ***[/COLOR]]("https://launchpad.net/yanespicturesoptimizer")

Thanks in advance  ):P

---

### Post by DaviesX on 2012-04-06
That is your website ? Awesome ! :-)

---

### Post by DaviesX on 2012-04-06
But why I can't extract your .tgz package ?
When I use the default achieve manager to extract the package, it said an error occurred

---

### Post by DaviesX on 2012-04-06
To avoid that freezing problem, I think you should make it multi-threaded
It is the first way, or you can make another executable so that you can call it in the main programme if you like.

I would prefer using multi-thread solution anyway :-)

---

### Post by yanes on 2012-04-06
rename it to yanespicsoptimizer1.0.tar.gz , I will fix that now !

---

### Post by yanes on 2012-04-06
> **DaviesX said:**
> That is your website ? Awesome ! :-)
thanks ! ):P

---

### Post by DaviesX on 2012-04-06
You're welcome

[http://www.tutorialspoint.com/python/python_multithreading.htm](http://www.tutorialspoint.com/python/python_multithreading.htm)

Here is the tutorial, hope that can help you.

---

### Post by yanes on 2012-04-06
I think , we have to find out the cause , the code is written in a way to allow this frame to refresh() 
after every image operation (resizing or conversion or both )

---

### Post by DaviesX on 2012-04-06
I doubt that it is not enough to refresh by the end of every operation.
I'm sorry that I'm not professional in Python language, all my opinion is only base on... intuitive =,=

---

### Post by DaviesX on 2012-04-06
You reckon how long on average does it take to computing a single image ?
I think if the lib can handle it in several milliseconds, that is good.
But if not, it would have been a delay in responding to the signal.
And If the delay takes too long, it seems that the window is frozen.

---

### Post by DaviesX on 2012-04-06
Well, here is the issue, I just test your image processor right after I finish my dinner :-), On my Atom N450 Netbook, it can not finish the task that fast. I have converted a Ubuntu wallpaper (Dybbolsbro train station) from jpeg to png, it takes 2 seconds to finish, so the main frame was frozen for 2 seconds ~.
Hence, I think a sub-thread need to be added on your programme.

---

