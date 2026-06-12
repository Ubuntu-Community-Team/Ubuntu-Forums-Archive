---
title: "Minimize Hidden"
date: 2011-09-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by alexvy13 on 2011-09-08
Would there be a way to minimize a window but have it hidden, so it doesn't take up as much space on the launcher? or to have a program start hidden (i.e thunderbird)

---

### Post by Toz on 2011-09-08
> **alexvy13 said:**
> Would there be a way to minimize a window but have it hidden, so it doesn't take up as much space on the launcher? or to have a program start hidden (i.e thunderbird)

Have a look at devilspie: [http://www.webupd8.org/2011/02/how-to-start-applications-minimized.html]("http://www.webupd8.org/2011/02/how-to-start-applications-minimized.html")

To have the program start minimized and hidden, create a config file like this:
```
$ cat .devilspie/gcolor2.ds 
(if
    (is (application_name) "gcolor2")
    (begin
       (minimize)
       (skip_pager)
    )
)

```

---

### Post by alexvy13 on 2011-09-08
> **Toz said:**
> Have a look at devilspie: [http://www.webupd8.org/2011/02/how-to-start-applications-minimized.html]("http://www.webupd8.org/2011/02/how-to-start-applications-minimized.html")

To have the program start minimized and hidden, create a config file like this:
```
$ cat .devilspie/gcolor2.ds 
(if
    (is (application_name) "gcolor2")
    (begin
       (minimize)
       (skip_pager)
    )
)

```

i have to have a terminal open for devils pie and it wont start hidden. 

I wish thunderbird would just run in the background :/

---

### Post by Toz on 2011-09-09
> **alexvy13 said:**
> i have to have a terminal open for devils pie and it wont start hidden.
Not necessarily. Just add devilspie to your startup applications.

> I wish thunderbird would just run in the background :/
It does. Use this configuration file:
```
$ cat .devilspie/thunderbird.ds 
(if
    (is (application_name) "Thunderbird")
    (begin
       (minimize)
       (skip_pager)
    )
)

```

---

### Post by alexvy13 on 2011-09-09
i did that and it didnt work :/ unless im doing something wrong

---

### Post by JD8182 on 2011-09-09
> **alexvy13 said:**
> Would there be a way to minimize a window but have it hidden, so it doesn't take up as much space on the launcher? or to have a program start hidden (i.e thunderbird)

Why not put the program on a different Desktop you have like 16 to choose from..? When I play music I usually just toss it on a different desktop window so it is out of the way..

---

### Post by Toz on 2011-09-09
> **alexvy13 said:**
> i did that and it didnt work :/ unless im doing something wrong

Hmmmm.
Once you add devilspie to your startup programs, log-out and back in again. Then open a terminal window and type in the following to confirm that devilspie is working:
```
ps -ef | grep devilspie
``` 

Can you post back the results along with the contents of **~/.devilspie/thunderbird.ds**?

I've tested it here and it works fine so I know that devilspie is capable of doing it. We just need to figure out why it doesn't work on your system.

---

