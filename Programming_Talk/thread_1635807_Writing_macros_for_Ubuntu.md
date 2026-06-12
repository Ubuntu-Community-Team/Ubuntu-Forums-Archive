---
title: "Writing macros for Ubuntu"
date: 2010-12-02
forum: Programming Talk
---

### Post by Aditya Bhavaraju on 2010-12-02
I am planning to develop an application that is supposed to access a cell phone's memory location (where the messages are stored) and then based on the information in them(the messages) act in real time to respond accordingly.For example suppose I send a number like 9999999999 then the program must read the number and send a Hi!(to 9999999999) through the internet.
Since this(the application) will be operated remotely without the presence of the user I am planning to write a macro that will take do this automatically.
My questions are
1)Is this possible at all?If yes,is it feasible to base my system on Ubuntu and write a macro accordingly?
2)Which programming language will suit my purpose?
Thank you for reading.

---

### Post by Zugzwang on 2010-12-02
The first step, more important that anything else, is to check if your *phone* supports what you want. 

I am not aware of any mobile phone that permits you to read from its memory directly.

However, most mobiles will have the possibility built in to transfer some of its data (text messages, contacts, etc.) to the computer. I remember having used some Linux program to get the contact list into the computer. So you will need to use such a thing.

But wait, you do want to do it remotely, i.e., without the phone being connected to the computer (bluetooth counts as connections in this context)? Then, you would need to write some program executed by the phone that will transmit the data automatically to your computer and get the user of the phone install the application. Also, many phones will not support this.

So the first thing to check if your target phone supports fetching the needed data in the way you want it to. If it suffices to have the phone connected, check if there is a Linux program that can fetch the data you need. Otherwise, check if you can upload an application to it that sends you the needed data somehow (e.g., via using a mobile internet connection).

An additional thing to consider is if you can simply use your mobile phone in modem mode. Then you wouldn't need to get some of its data, but let all messages recieved when being in modem mode forward to the computer.

---

### Post by nvteighen on 2010-12-02
1) A "macro" is some piece of code that does text generation of some sort.

2) Zugzwang is right: you need interfaces for that. The phone should have some interface to do what you want: either high- or low-level. But I'm sure there's little chance to access any phone's internals by trivial means.

---

### Post by Arndt on 2010-12-02
> **nvteighen said:**
> 1) A "macro" is some piece of code that does text generation of some sort.



I'm not sure I recognize the meaning of macro that you present here, but maybe you do mean what is said here: [http://en.wikipedia.org/wiki/Macro_%28computer_science%29](http://en.wikipedia.org/wiki/Macro_%28computer_science%29).

---

### Post by nvteighen on 2010-12-03
> **Arndt said:**
> I'm not sure I recognize the meaning of macro that you present here, but maybe you do mean what is said here: [http://en.wikipedia.org/wiki/Macro_%28computer_science%29](http://en.wikipedia.org/wiki/Macro_%28computer_science%29).

Well, Wikipedia states it much better than I did :)

---

### Post by Aditya Bhavaraju on 2010-12-04
@Zugzwang:First of all thanks a lot for your time sir.I do not know if my Nokia 5310 supports this,it most probably does not,but there is a software solution called Nokia PC suite that allows us to access the messages,so will a simple hack map the input sequence to an output sequence?That is why I wanted to write a macro in the first place.And remotely in this context does not mean the phone not being connected to the computer,the phone(dedicated for the purpose of receiving the sms) will be connected to the computer via an USB,What I meant was that the phone should detect an incoming message then 'push' the message into the computer which will then act upon the message...

@nvteighen and Arndtt:Thank you for your help :) And yes by a macro I meant the macro in the wikipedia link...

---

### Post by worksofcraft on 2010-12-04
Yes my Nokia mobile can also connect to the USB port and has software that downloads the pictures and messages, so evidently that bit is possible. Also I can connect via my Nokia to the wireless internet with Telecom so it's evidently able to accept commands from the computer to send out data in real time.

IDK about how to do it, but a very quick Google suggests you could start looking here for [Nokia PC connectivity API]("http://www.forum.nokia.com/Library/Tools_and_downloads/Other/PC_Connectivity_API/")

If you do get it to work, do come back and post about it because it sounds really interesting :)

---

### Post by Vox754 on 2010-12-04
> **Aditya Bhavaraju said:**
> ...

@nvteighen and Arndtt:Thank you for your help :) And yes by a macro I meant the macro in the wikipedia link...

Unless you are working with Microsoft Word and Excel, and VBA, I suggest you don't use the word "macro" so generally. It is a term that may have different meanings depending on the environment.

---

### Post by nvteighen on 2010-12-04
> **Vox754 said:**
> Unless you are working with Microsoft Word and Excel, and VBA, I suggest you don't use the word "macro" so generally. It is a term that may have different meanings depending on the environment.

Yeah, when I read "macro" I usually think on something like this :D:
```

(defmacro board-coord (board coord)
  `(aref (slots ,board)
         (car ,coord)
         (cdr ,coord)))

```

---

### Post by Zugzwang on 2010-12-05
@OP: Perhaps you might want to have a look at the following piece of software: [http://stefanfrings.de/smstools/index-en.html](http://stefanfrings.de/smstools/index-en.html)

It looks like it can do what you want. Read the manual - it states that the developers found that PC connectivity of mobile phones is typically not stable enough for commercial use. However, you might want to give it a try. Note that the approach here is different: it uses your mobile phone as *modem* for receiving incoming SMS rather than letting the mobile receive the SMS and then download it. The latter may also be possible but looks unncessary complicated.

---

