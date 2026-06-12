---
title: "[ C++ ] time.h - something is wrong with the year and month ( struct tm )."
date: 2009-12-05
forum: Programming Talk
---

### Post by endBc on 2009-12-05
What I'm doing wrong ?

```
#include <iostream>
#include <time.h>

using namespace std;

int main(int argc, char *argv[])
{
    time_t timestamp;
    timestamp = time(NULL);

    struct tm *rtime = localtime(&timestamp);

    cout << "Year: " << rtime->tm_year << endl;
    cout << "Month: " << rtime->tm_mon << endl;
    cout << "Day: " << rtime->tm_mday << endl;
    cout << "Hour: " << rtime->tm_hour << endl;
    cout << "Minute: " << rtime->tm_min << endl;
    
    return 0;
}

``````
[COLOR=Red]Year: 109[/COLOR]
[COLOR=Red]Month: 11[/COLOR]
[COLOR=Green]Day: 5
Hour: 20
Minute: 35[/COLOR]
```

---

### Post by MadCow108 on 2009-12-05
years are counted from 1900
month from 0
[http://www.cplusplus.com/reference/clibrary/ctime/tm/](http://www.cplusplus.com/reference/clibrary/ctime/tm/)

---

### Post by LKjell on 2009-12-05
If you bother to read the manual then you would understand.
manpages-dev is a very useful package.

> 
       tm_sec    The  number  of seconds after the minute, normally in the range 0 to 59, but can be up to 60
                 to allow for leap seconds.

       tm_min    The number of minutes after the hour, in the range 0 to 59.

       tm_hour   The number of hours past midnight, in the range 0 to 23.

       tm_mday   The day of the month, in the range 1 to 31.

      [B] tm_mon    The number of months since January, in the range 0 to 11.
[/B][B]
       tm_year   The number of years since 1900.[/B]

       tm_wday   The number of days since Sunday, in the range 0 to 6.

       tm_yday   The number of days since January 1, in the range 0 to 365.

---

### Post by endBc on 2009-12-05
Thank you.

> **LKjell said:**
> If you bother to read the manual then you would understand.
manpages-dev is a very useful package.

I don't know where they are ( if at all ) in Visual C++ Express 2008.

---

### Post by dwhitney67 on 2009-12-05
> **endBc said:**
> I don't know where they are ( if at all ) in Visual C++ Express 2008.

Lame excuse.

[http://linuxmanpages.com/](http://linuxmanpages.com/)
[http://linuxmanpages.com/man3/localtime.3.php](http://linuxmanpages.com/man3/localtime.3.php)

---

### Post by endBc on 2009-12-05
> **dwhitney67 said:**
> Lame excuse.

[http://linuxmanpages.com/](http://linuxmanpages.com/)
[http://linuxmanpages.com/man3/localtime.3.php](http://linuxmanpages.com/man3/localtime.3.php)

Linux man pages when I'm working on a Windows platform ? Think about what you are going to suggest before replying.
Thanks to *MadCow108* who provided the actual page where I should have been looked for this.

---

### Post by dwhitney67 on 2009-12-05
> **endBc said:**
> Linux man pages when I'm working on a Windows platform ? :-s Think about what you are going to suggest before replying.


Both OS's (Windoze and Linux) share many common library functions in order to fulfill their goal of being POSIX compliant.

Btw, to prove that you are ignorant...
[http://msdn.microsoft.com/en-us/library/aa246456%28VS.60%29.aspx](http://msdn.microsoft.com/en-us/library/aa246456%28VS.60%29.aspx)

You can also launch the Visual C++ help that comes with your product, and perform a search (for locatime or whatever).

P.S.
'Ignorant' =  unaware because of a lack of relevant information or knowledge.

Please don't interpret the word negatively.

---

### Post by endBc on 2009-12-05
> **dwhitney67 said:**
> Both OS's (Windoze and Linux) share many common library functions in order to fulfill their goal of being POSIX compliant.

Btw, to prove that you are ignorant...
[http://msdn.microsoft.com/en-us/library/aa246456%28VS.60%29.aspx]("http://msdn.microsoft.com/en-us/library/aa246456%28VS.60%29.aspx")

You can also launch the Visual C++ help that comes with your product, and perform a search (for locatime or whatever).

P.S.
[SIZE=4][COLOR=Red]**'Ignorant' =  unaware because of a lack of relevant information or knowledge.**[/COLOR][/SIZE]

If I would have enough knowledge on this, I wouldn't have made this thread. Anyway, thank you for the link.

---

### Post by Arndt on 2009-12-05
> **endBc said:**
> Linux man pages when I'm working on a Windows platform ? Think about what you are going to suggest before replying.
Thanks to *MadCow108* who provided the actual page where I should have been looked for this.

But why do you ask on a Linux forum in that case?

---

### Post by dwhitney67 on 2009-12-05
> 
I've no intentions to turn this question into a flame war

Nor do I.  You asked a question, and it was answered (by someone else).

I, stupidly, added additional remarks.

---

