---
title: "How to filter running processes ?"
date: 2018-09-20
forum: New to Ubuntu
---

### Post by kirollsnasr on 2018-09-20
currently I am building an app that's need some filtration on running processes
In Kubuntu, KSysGuard has choice of Program Only , so how can I get this results by commands, I tried a lot but I couldn't separate those processes
I tried **ps, htop **after studying their man but still

---

### Post by Claus7 on 2018-09-20
Hello and welcome to the forums!

If I understand correctly you have an application that is running and you want to check that that application is indeed running, correct? Also, you do not want to check all the other applications that are running at the same time.

If this is the case the ps command would work like this:
ps ux | grep name_of_your_application

which means that with ps command you will be able to check all applications running and with the grep command you will filter just the one you want.

Regards!

---

### Post by kirollsnasr on 2018-09-20
> [COLOR=#000000]Hello and welcome to the forums![/COLOR]

[COLOR=#000000]If I understand correctly you have an application that is running and you want to check that that application is indeed running, correct? Also, you do not want to check all the other applications that are running at the same time.[/COLOR]

[COLOR=#000000]If this is the case the ps command would work like this:[/COLOR]
[COLOR=#000000]ps ux | grep name_of_your_application[/COLOR]

[COLOR=#000000]which means that with ps command you will be able to check all applications running and with the grep command you will filter just the one you want.[/COLOR]

[COLOR=#000000]Regards![/COLOR]

Thank you for your reply
actually I need all running non-system processes , because what I want is to make a report of usage each month for those apps, so I want to be notified when one of these processes run.

---

### Post by Claus7 on 2018-09-20
Hello,

how about this?
[https://unix.stackexchange.com/questions/299097/show-running-processes-without-the-system-processes](https://unix.stackexchange.com/questions/299097/show-running-processes-without-the-system-processes)

Regards!

---

### Post by kirollsnasr on 2018-09-20
> [COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]how about this?[/COLOR]
[https://unix.stackexchange.com/quest...stem-processes]("https://unix.stackexchange.com/questions/299097/show-running-processes-without-the-system-processes")

[COLOR=#000000]Regards![/COLOR]


I really appreciate your effort thanks

---

