---
title: "Wget partial success"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by spec300011 on 2012-06-13
Hello all,
                  I used wget as a test to see if i can actually work out how it works.

                  This is what I passed to bash and the accompanying results.


wget --wait=20 --limit-rate=20K -r -p -U Mozilla [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)
--2012-06-13 21:57:32--  [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)
Resolving [www.gnu.org](www.gnu.org) ([www.gnu.org](www.gnu.org))... 208.118.235.148, 2001:4830:134:3::a
Connecting to [www.gnu.org](www.gnu.org) ([www.gnu.org)|208.118.235.148|:80](www.gnu.org)|208.118.235.148|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 614727 (600K) [text/html]
Saving to: 'www.gnu.org/software/bash/manual/bashref.html'

100%[======================================>] 614,727     20.2K/s   in 30s     

2012-06-13 21:58:04 (19.9 KB/s) - 'www.gnu.org/software/bash/manual/bashref.html' saved [614727/614727]

Loading robots.txt; please ignore errors.
--2012-06-13 21:58:24--  [http://www.gnu.org/robots.txt](http://www.gnu.org/robots.txt)
Connecting to [www.gnu.org](www.gnu.org) ([www.gnu.org)|208.118.235.148|:80](www.gnu.org)|208.118.235.148|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 148 [text/plain]
Saving to: 'www.gnu.org/robots.txt'

100%[======================================>] 148         --.-K/s   in 0s      

2012-06-13 21:58:26 (5.10 MB/s) - 'www.gnu.org/robots.txt' saved [148/148]


I have seperated my question into two parts.

1) Why did I get a robots.txt when i specified a specific url with a time wait/delay( ? ) ( does it have something to do with the page requisite request ( -p flag ) ? i.e asking for different files around this domain ...if that makes sense ) ?

2) This is only a partial output of the results. Some of the robots.txt files are oversized from what i can view in their text. For example, 1 file is 5.2 mb with only something like 20 lines at most of characters. What editor would I need to actually view what is in this file. It is just plain text ( I suspect it would just be garbage, however, I am just curious to know ).

[INDENT][INDENT]Regards and thanks for reading.
[/INDENT][/INDENT]

---

### Post by spec300011 on 2012-06-14
My apologies for replying to my own thread, but just wondering if anyone has any ideas.

Thankyou

---

### Post by mastablasta on 2012-06-14
> **spec300011 said:**
> I have seperated my question into two parts.
 
1) Why did I get a robots.txt when i specified a specific url with a time wait/delay( ? ) ( does it have something to do with the page requisite request ( -p flag ) ? i.e asking for different files around this domain ...if that makes sense ) ?
i saw this yesterday but i can only guess...
 
It is probably linked to something on the site or you selected to download all files in directory. never used a command line but there is a nice wget gui i use.
> 
2) This is only a partial output of the results. Some of the robots.txt files are oversized from what i can view in their text. For example, 1 file is 5.2 mb with only something like 20 lines at most of characters. What editor would I need to actually view what is in this file. It is just plain text ( I suspect it would just be garbage, however, I am just curious to know ).
 
try to use gedit on them
 
if not just open them in one of many other text editors or office programmes available.

---

### Post by Azdour on 2012-06-14
Hi,

+1 

wget acts like a robot:

[http://wget.addictivecode.org/FrequentlyAskedQuestions#How_can_I_make_Wget_ignore_the_robots.txt_file.2BAC8-no-follow_attribute.3F](http://wget.addictivecode.org/FrequentlyAskedQuestions#How_can_I_make_Wget_ignore_the_robots.txt_file.2BAC8-no-follow_attribute.3F)

And from [http://www.delorie.com/gnu/docs/wget/wget_41.html:](http://www.delorie.com/gnu/docs/wget/wget_41.html:)

> 
If Wget finds that it wants to download more documents from that server, it will request `[http://www.server.com/robots.txt](http://www.server.com/robots.txt)' and, if found, use it for further downloads.


---

