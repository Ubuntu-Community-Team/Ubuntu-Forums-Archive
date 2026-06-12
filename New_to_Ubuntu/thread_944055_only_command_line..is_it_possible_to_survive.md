---
title: "only command line..is it possible to survive"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-10-10
hi all,

i got a crazy idea just now :)... is it actually possible(practically) to live with a pc which has just linux kernel + bash shell....no grahical window managers,etc...

is it actually possible to live like that in this time when the desktop is dominated by great apps like firefox, evolution, gedit,Open Office etc., 

if you say yes, how would you

1. browse the internet in a shell
2. how would write emails in a shell
3. what could be the replacements of the well known gui apps(in linux) in a shell environment........ you comments are welcome

cheers

---

### Post by talsemgeest on 2008-10-10
It is possible, but I wont be doing it any time soon. To browse the internet, you can use Lynx (sudo apt-get install lynx), a text only internet browser that can be run from a bash shell. I havent tried it, but you could probably run gmail in lynx, therby allowing you to write emails.

---

### Post by Sarah L on 2008-10-10
You can browse the internet using a text-only browser such as lynx (sudo apt-get install lynx).

You can do text editing in a terminal using such applications as nano or vim.

---

### Post by luckydeveloper on 2008-10-10
ok... anyother app replacement...say for office, then what about multitasking...is it possible to run more than program with that environment...

any other comments about this kind of environemnt are welcome

---

### Post by Mister.Vash on 2008-10-10
Use Lynx as your browser and an app like mutt for mail.  Some people still don't use gui's and are comfortable with that.  You can still listen to music, even using vlc by starting it with the 'vlc -I ncurses' but obviously you aren't going to be able to watch movies via a terminal.  It's all about what you need to do.  If you need to edit images with gimp, you aren't going to be able to just use a command line, it's all about the applications you need to use.

---

### Post by talsemgeest on 2008-10-10
> **Mister.Vash said:**
> Use Lynx as your browser and an app like mutt for mail.  Some people still don't use gui's and are comfortable with that.  You can still listen to music, even using vlc by starting it with the 'vlc -I ncurses' but obviously you aren't going to be able to watch movies via a terminal.  It's all about what you need to do.  If you need to edit images with gimp, you aren't going to be able to just use a command line, it's all about the applications you need to use.
There is a filter in vlc that turns video into ascii text, so it is possible to watch movies from a cli, but unfortunately it doesn't work...

---

### Post by luckydeveloper on 2008-10-10
i am actually using lynx for about 10mins now... i would say its way better than internet explorer :) haha

---

### Post by t0p on 2008-10-10
There's another text-based browser that comes with the default ubuntu install: w3m.  For email, there are command-line tools like mailx.  If you are into multi-tasking, and having several windows open at the same time, there's a utility called screen that handles such sessions.

---

### Post by bodhi.zazen on 2008-10-10
It is not so bad running without X

Check out these sites :

[http://pjvenda.blogspot.com/2007/05/using-linux-without-x.html](http://pjvenda.blogspot.com/2007/05/using-linux-without-x.html)

[http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/](http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/)

---

### Post by namegame on 2008-10-10
There is now a live-cd distribution that runs without X.

It's based off of ubuntu 8.04.

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/INX-40559.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/INX-40559.shtml)

---

### Post by luckydeveloper on 2008-10-10
> **bodhi.zazen said:**
> It is not so bad running without X

Check out these sites :

[http://pjvenda.blogspot.com/2007/05/using-linux-without-x.html](http://pjvenda.blogspot.com/2007/05/using-linux-without-x.html)

[http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/](http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/)

great links... thanks

---

### Post by iponeverything on 2008-10-11
there are a lot of us out there who learned on shared systems without a GUI.

VAX and UNIX (ultrix, irix, hpux, OSF/1) - primarily. Not only did we survive -- we thrived and grew.

at time http hadn't evolved yet, we used pine and elm and read mail, usenet and mailing lists to exchange information.. and the unix "talk" command was our IM of sorts..

---

### Post by Nxion on 2008-10-11
It definitely is interesting, not using a GUI can be a challenge at times.

I tried it for a day or so. For internet I used lynx and for mail I used mutt(Istill use it now). Mutt is awesome I love it. for IRC i used irssi. like I said it was interesting but fun.

This was a good reference for me to follow, Alot of information that helped me out.
[URL="http://ubuntuforums.org/showthread.php?t=387598"]
http://ubuntuforums.org/showthread.php?t=387598[/URL]

Cheers!

---

### Post by coffeepro on 2008-10-11
If you want to experience text only browsing open Firefox then edit, preferences, content, uncheck "load images". Then View, Page style, select "No page style".

---

### Post by kerry_s on 2008-10-11
> **luckydeveloper said:**
> 
1. browse the internet in a shell
2. how would write emails in a shell
3. what could be the replacements of the well known gui apps(in linux) in a shell environment........ you comments are welcome

cheers

1. links2 in graphics mode: [http://links.twibright.com/features.php](http://links.twibright.com/features.php)
2. mutt
3. file manager/editor = mc

there's tons of choices so it comes down to whats easier for you.

---

### Post by niteshifter on 2008-10-11
> **iponeverything said:**
> there are a lot of us out there who learned on shared systems without a GUI.

VAX and UNIX (ultrix, irix, hpux, OSF/1) - primarily. Not only did we survive -- we thrived and grew.

at time http hadn't evolved yet, we used pine and elm and read mail, usenet and mailing lists to exchange information.. and the unix "talk" command was our IM of sorts..

What? No gopher? What about Archie and Veronica?

Those were the days :) 

For the curious, but not inclined to search:
gopher - A way of linking documents across servers. Hyper-linked FTP more-or-less, with linking done on the server end.
Archie - Indexing of FTP sites.
Veronica - Sort of a super-Archie, gopher specific.

Archie / Veronica were the Google of the period.

Some of us were using these when the WWW (http) was but a "what-if" in Sir Berners-Lee's mind ;)

---

