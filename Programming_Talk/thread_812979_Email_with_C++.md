---
title: "Email with C++?"
date: 2008-05-30
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2008-05-30
I'm writing a program that generates a text file.  I want the program to email me the file.  To decrease the number of local dependencies, I want it to login to my gmail account and send through that (much like my gmail account can send mail from my other accounts).  I know that the program will have to telnet into an SMTP server, pass along my credentials, then email me the file...  The problem is that, assuming I start telnet with a system call, I don't know how to send further input to telnet once it has started (i.e. send mail commands, my credentials, etc).  Does anyone know how I could do that? 
Example:

```

//file's been created, need to email it
system("telnet mymailserver");
//now how do I pass further data to that telnet session?

```
Thanks.

---

### Post by dempl_dempl on 2008-05-30
Check out my site:

[http://www.stosha.net/component/option,com_mtree/task,viewlink/link_id,134/Itemid,99999999/](http://www.stosha.net/component/option,com_mtree/task,viewlink/link_id,134/Itemid,99999999/)

This is a C++ smtp library.

If you still want to do it by executing telnet, check out **popen** function ( I'm not sure if popen is  a system call ) 



Cheers!

---

### Post by the_real_fourthdimension on 2008-05-30
> **dempl_dempl said:**
> Check out my site:

[http://www.stosha.net/component/option,com_mtree/task,viewlink/link_id,134/Itemid,99999999/](http://www.stosha.net/component/option,com_mtree/task,viewlink/link_id,134/Itemid,99999999/)

This is a C++ smtp library.

If you still want to do it by executing telnet, check out **popen** function ( I'm not sure if popen is  a system call ) 



Cheers!
Thanks.  Would that library allow me to connect to a remote MTA, or would the machine sending the mail need to have one preconfigured?

Also, in googling popen, I found that it seems to be a system call.  However, typing "popen" in my terminal only generates a command not found error...

---

### Post by dempl_dempl on 2008-05-30
About the first question:

> 
libESMTP is an SMTP client which manages posting (or submission of) electronic mail via a preconfigured Mail Transport Agent (MTA). It may be used as part of a Mail User Agent (MUA) or other program that must be able to post electronic mail but where mail functionality is not that program's primary purpose.

The availability of a reliable lightweight thread-safe SMTP client eases the task of coding for software authors thus improving the quality of the resulting code.



(2) He he .. system call is a **C/C++**  **functon** not **shell command ** [ some pedantic folks would say that my definition is not accurete too, but wh cares :)  ]

Cheers!

---

