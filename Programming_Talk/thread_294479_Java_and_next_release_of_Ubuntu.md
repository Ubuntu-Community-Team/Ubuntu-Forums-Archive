---
title: "Java and next release of Ubuntu?"
date: 2006-11-06
forum: Programming Talk
---

### Post by nik77 on 2006-11-06
I'am a computer programmer. My prefered programming language is Java. Some moths ago I'tried to install Ubuntu 5.10 in my PC with an amd 64. But I had two problems: the first, and the major, was that my prefered IDE (Eclipse, version for AMD64) had some problems to be installed ](*,). Second I noticed that there wasn't the jvm from Sun and not the JDK (OK, this is not a real problem I can daownload ( with my 56k  modem :-| ...) ). If I'am right there was, by default, another version of java compiler ( the javac command ... ) :confused: 
So, at last, expecialy caused by eclipse ](*,) , I used another distro. 

Just few days ago, i red about the "Sun's plans to open source its Java SE implementation - the JDK" (peraphs before 2007 with a license approved by Open Source Comunity) :mrgreen: . Now, I want to ask you :"Is it possibile ( if Sun ... ) to have the JDK from Sun in your next realese of Ubuntu :rolleyes:? "What about Ubuntu's plans about Java?". I thinks it's important to have attention about this issue ( a lot of people use java, and if I'm right a lot of Open Source Project now are wrote in java - using the standard library from Sun JDK- ). Do you have understend my question? :-k . I'd like the next reales of Ubuntu payed a little more attention to "Java standards". Or I'am wrong? and this problem doesn't exist? Sorry, I'hope a day I will be able to colloborate with the Ubuntu Open Source Comunity.

Thank you.:KS 
( Hopping re-install Ubuntu very soon in my PC )

Sorry for my English.

---

### Post by Joe_CoT on 2006-11-06
I don't really think I understand the question .... if Sun open-sources java, it'll most likely just change the way ubuntu packages it (they might compile it using their own method, and the package won't need to fetch the binaries from Sun's website, hopefully). Perhaps more open-source projects will use java, as its biggest complaint is writing open-source software on a black box engine. What changes would you suggest ubuntu make regarding this?

---

### Post by hod139 on 2006-11-06
Sun's official java has been in ubuntu since dapper (6.06).  I don't know about eclipses's stability on amd64 though.

---

### Post by nik77 on 2006-11-06
> **Joe_CoT said:**
> .... if Sun open-sources java, it'll most likely just change the way ubuntu packages it (they might compile it using their own method, and the package won't need to fetch the binaries from Sun's website, hopefully). Perhaps more open-source projects will use java, as its biggest complaint is writing open-source software on a black box engine.

When I write a program I hope it will run in an "environment" very very similar to the "environment" where I devoloped it - to be absolutly sure about the result and the perfomance!!!-. If Sun open-sources java, I hope the Open Source Comunity (Ubuntu too) take it (jdk and jre from Sun) like "the standard or default for java". **It'will not a black box!!!** you can see the code!!! :-D  and the license it will be probably the same yet approved by Open Source Iniziative (OSI) for Solaris :-D. (If you want you can help just now to devolp and improve the next release of java (6) in site of Sun!)  
So my hope it's Ubuntu takes this way. And I hope find JDK or JRE from Sun by default in next relese of Ubuntu. For a java programmer i think it's not a good thingh have many jre, jdk ecc... Standards are important expecialy for a pragramming language. The danger is, in just few years, having many dialect of java :confused:  

Perhaps I'm wrong!

Thanks:KS

---

### Post by nik77 on 2006-11-06
> **hod139 said:**
> Sun's official java has been in ubuntu since dapper (6.06).

Thanks I didn't know.:D

---

### Post by Tomosaur on 2006-11-07
I don't think Sun intends to open-source Java in one fell swoop, I think I read somewhere that if they did go down the open-source route, it would be bit by bit, which may mean it will take a few years yet to have everything out in the open. I don't like using anything other than Sun's JDK and JRE for java, it just seems to cause too many problems for me. At least Ubuntu makes it (relatively) easy to get Sun's java working :P

---

### Post by _asc_ on 2006-11-07
AFAIK, Java SE should be opensourced by the end of this year:

[http://news.yahoo.com/s/infoworld/20061025/tc_infoworld/83138](http://news.yahoo.com/s/infoworld/20061025/tc_infoworld/83138)

---

### Post by Hikaru79 on 2006-11-07
At the moment, all you have to do is enable the multiverse repositories, then go
```
sudo apt-get install sun-java5-sdk
```
And you will have the official Sun compiler :) I also do Java development (with Netbeans, however, not Eclipse), and I've never had any real problems with this.

---

