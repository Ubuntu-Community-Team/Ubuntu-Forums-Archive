---
title: "adding rule in iptables by c program"
date: 2012-05-14
forum: Programming Talk
---

### Post by udaycdac on 2012-05-14
can anyone tell me how can i add rule in iptables using c program or which library is available for adding rule in iptables ??

---

### Post by codemaniac on 2012-05-14
> **udaycdac said:**
> can anyone tell me how can i add rule in iptables using c program or which library is available for adding rule in iptables ??
Hello udaycdac ,
Welcome to the Ubuntuforums .

Are you talking about the commands to add firewall rules in Iptables ?If you want to automate the rules addition , writing a shell script would be wiser than a whole lot of C code .

Still from your post it is very difficult to gauge your requirement .

---

### Post by udaycdac on 2012-05-14
Hi Robert A. Heinlein,

i  am trying to add rule by using any library in c.
if anyone can suggest me library through which i can add rules in iptables;

---

### Post by udaycdac on 2012-05-14
i am trying to add rule by using any library in c.
if anyone can suggest me library through which i can add rules in iptables;

---

### Post by Zugzwang on 2012-05-14
> **udaycdac said:**
> i am trying to add rule by using any library in c.
if anyone can suggest me library through which i can add rules in iptables;

Is there any reason why you cannot just invoke a shell command using "system" or "popen" for this task and rather need a library? If yes, let us know, as otherwise, you'll not get a satisfactory answer here.

---

### Post by udaycdac on 2012-05-15
Thanx fr replying,
yea there is a specific reason not to use system and popen.

i tried libiptc , i have a little idea about it.

can anyone help me about adding rule in iptables using libiptc

---

### Post by Zugzwang on 2012-05-15
> **udaycdac said:**
> Thanx fr replying,
yea there is a specific reason not to use system and popen.


which is?

---

### Post by udaycdac on 2012-05-15
i m trying to add rul using iptables v1.4.12.1.
in the package of uiptables libiptc is thr.

i m trying fr adding the rules using libiptc.can anyone help me abt this ?/

---

### Post by Zugzwang on 2012-05-15
@OP: Well, if you don't answer to questions yourself, don't expect a good answer to yours. Post #2 and #7 are still unanswered, and you just repeated your question.

The point is that you are trying to do something "the hard way" - there are command line utilities for doing what you want. Quite often when people ask here about doing something in the hard way, there is typically a misconception about certain concepts present. Many posters want to ensure that helping you in doing something the hard way will actually help you in your task, and that their posts are not in vain. Thus, you will need us to convince that you know what you are doing, and part of that is to explain *why* you want the hard way. You will either (1) convince everyone to help you, or (2) get clarification on your underlying assumptions. Either way, stating why you don't want to use the command line utility will help us to help you!

---

### Post by udaycdac on 2012-05-15
Thanx Zugzwang for your suggetion.

i am trying to add rules dynamically in iptables and if i use system command it will not be a secure code. it will make my code vulnerables.

so i want to use libiptc libbrary.

---

### Post by Zugzwang on 2012-05-15
> **udaycdac said:**
> 
i am trying to add rules dynamically in iptables and if i use system command it will not be a secure code. it will make my code vulnerables.


I don't know about this netfilter library, but here's a way to avoid code vulnerabilities, but still call some command-line utility: you can explicitely bypass the shell and call the program you are wanting to execute directly. The runtime environment of languages such as python has such functionality built-in. A way of doing this here is to use something like the popen_noshell function provided here: [https://code.google.com/p/popen-noshell/](https://code.google.com/p/popen-noshell/) - You explicitely list your arguments to a fixed program, which makes it impossible to inject some other command into your process call.  The idea is the same as with prepared statements in SQL.

---

