---
title: "Java Help"
date: 2009-07-28
forum: Programming Talk
---

### Post by mthalis on 2009-07-28
I developed GUI program using Java(not used any advance - EJB, Spring or Hibernate). That program used more than one user and they enter and edit data(some time simultaneously) Problem is while running my program machine get stuck and it also consume high memory. In order to overcome this problems what kind of method should I use. If I develop this type program what is the best technology available in Java side.

Note - without web base solution(program should not run web browser)

Please give any comment I'm waiting your comments.

---

### Post by konqueror7 on 2009-07-28
have you tried using _concurrency_?

[http://java.sun.com/docs/books/tutorial/essential/concurrency/]("http://java.sun.com/docs/books/tutorial/essential/concurrency/")

[http://java.sun.com/docs/books/tutorial/uiswing/concurrency/]("http://java.sun.com/docs/books/tutorial/uiswing/concurrency/")

---

### Post by mthalis on 2009-07-28
I normaly develop swing application using Netbeans IDE, then how can optimize my Guis,
and develop new program according to above requirement.

---

### Post by konqueror7 on 2009-07-28
one thing is, swing is very slow, it generates every component in every start depending on the OS, though its good if your program is targeted across different platforms...

the easiest would be to not use swing as your GUI framework, but this will require you to learn and waste time, so no...

the other is use concurrency, i won't go through the details, but basically, you give a task to a thread, in which in combination with other threads, could split times in using the CPU, instead of having no concurrency at all, you have to wait for a task to finish before the other one can start...

for example, your loading 1000records from your database. by using concurrency, the GUI will immediately pop-up and still can do other things, as compared with note using concurrency, you will have to wait for it to load, causing your program to be unresponsive during the loading...

Note:
and oh, what i understand from your post is, you program is being used by multiple users, that are maybe in the same computer and/or different computers...and somehow, you haven't stated really well your problem in english, but thats okay... ;)

---

### Post by jespdj on 2009-07-28
> **konqueror7 said:**
> one thing is, swing is very slow, it generates every component in every start depending on the OS, though its good if your program is targeted across different platforms...
:rolleyes: When is the last time you wrote a serious Java application with Swing? Swing used to be slow in 1998, with Java 1.2, but that's more than ten years ago. Swing on Sun Java 6 is not slow at all.

mthalis' problem is most likely in the way he wrote his program. Using a different GUI framework is not going to solve this. Since mthalis doesn't give any details about how his program works, it is very hard to say exactly what the problem is. So, mthalis, if you want useful help with this, explain in more detail how your program is constructed.

---

### Post by Zugzwang on 2009-07-28
@OP: I would suggest using Netbeans' debugging facilities - Start your program in debugging mode and use your program as usual until it gets stuck. Then wait some seconds and interrupt it (the command is somewhere in the debugging menu). Then inspect the call trace and see where it got stuck, examine the variables in the respective contexts and watch out for unexpected values.

---

### Post by konqueror7 on 2009-07-28
> **jespdj said:**
> :rolleyes: When is the last time you wrote a serious Java application with Swing? Swing used to be slow in 1998, with Java 1.2, but that's more than ten years ago. Swing on Sun Java 6 is not slow at all.

mthalis' problem is most likely in the way he wrote his program. Using a different GUI framework is not going to solve this. Since mthalis doesn't give any details about how his program works, it is very hard to say exactly what the problem is. So, mthalis, if you want useful help with this, explain in more detail how your program is constructed.

yes, it is slow, compare with it other frameworks, you will see why... i still use swing as my primary ui framework, in todays PCs you won't notice the difference, but open-up NetBeans and Eclipse, see how they compare ;)

and i agree that changing frameworks will not solve his entire problem, but it will help, as i said ***"but this will require you to learn and waste time, so no..."*** above...

i don't want to start an argument, we do have different views, so lets just help the guy...;)

---

### Post by mthalis on 2009-07-28
After discussing my friend they said put my logic into centralized server and allow client to communicate with that server. Is it write or wrong method, If I go to that kind of solution what is the best technology available in Java.

According to **konqueror7** idea - If I use Hibernate with Swing can i overcome concurrency problem, if not how to over come it.

Sorry about my English

---

### Post by konqueror7 on 2009-07-29
> **mthalis said:**
> After discussing my friend they said put my logic into centralized server and allow client to communicate with that server. Is it write or wrong method, If I go to that kind of solution what is the best technology available in Java.

According to **konqueror7** idea - If I use Hibernate with Swing can i overcome concurrency problem, if not how to over come it.

Sorry about my English

your using Hibernate? based on your first question, your only using swing and no advanced frameworks...your friend's method could work, giving the server most of the logic and load of the program, introduce concurrency logic to the server so the connections to it can be catered accordingly...the only problem is how many will use your program from your server..i do also currently use JPA (Hibernate back-end) and swing as my UI, so my deployment was put the program on a server, and put concurrency on the task that needed to be loaded fast or shared by many or just to have it work in the background so other tasks can still be executed by the user...

---

### Post by mthalis on 2009-07-29
Still I'm not using Hibernate(Thinking what kind of technology should i used) , **konqueror7** sorry to disturb you can explain you're answer more.

---

### Post by konqueror7 on 2009-07-29
say, lets just give the whole task and logic be managed by the server, in that way the client machine won't be have to consume all the resources...

next, is, apply concurrency. it would greatly help. if your friend knows how to, try to ask him. concurrency or multitasking, makes execution of tasks more efficient, in a way that it doesn't need to wait for one task to finish, rather it distributes the task across different "workers" making your program more responsive...you can read and example [here]("http://java.sun.com/developer/technicalArticles/javase/swingworker/")

---

### Post by mthalis on 2009-07-29
Thank for help. I understand what you said. One little problem What is the technology should I used. language(Hibernate, EJB, web service ........) and IDE (netbeans, eclipse ...).

---

### Post by konqueror7 on 2009-07-29
> **mthalis said:**
> Thank for help. I understand what you said. One little problem What is the technology should I used. language(Hibernate, EJB, web service ........) and IDE (netbeans, eclipse ...).

whats your proficiency in Java... i suggest to just use NetBeans, because it makes a lot easier designing your Swing GUI. Also if your still in the beginning of Java, just leave other frameworks and technologies aside like Hibernate and Web Services, you won't still need it. I would just suggest to atleast get the concept of the fundamentals of Java, in this way, you will know where to look when you need something...;)

---

### Post by hyperAura on 2009-07-30
i think u can use XML and without opening a browser u will just parse the response message and do whatever u want just by using java.. there is a finite number of HTTP status responses u can get from an XML message and through that u can also handle concurrency with is what u need..:) some examples of the responses u can get is 503 which means service unavailable which can be translated as the server is busy because some1 else is using it, or because some1 else is using these files.. u'll have to a be a bit careful when implementing it as this should work like a user has a lock for the files he is using..

---

