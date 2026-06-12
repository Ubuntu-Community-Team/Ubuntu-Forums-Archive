---
title: "Writing GUI frontends with shell access"
date: 2008-07-03
forum: Programming Talk
---

### Post by QwUo173Hy on 2008-07-03
I'd like to start programming in linux. The easiest way I find to program is writing scripts. But I want to write GUI apps.

I know there are things like fork() and exec() to allow me bash access, but I find them painfully difficult to use. Is there some kind of bash / console library I can include in a C++ program so I can do everything from the one program without forking?

Thanks,
Jarlath

---

### Post by ghostdog74 on 2008-07-03
start with the basics without GUI, then slowly progress to that. Why the hurry?

---

### Post by LaRoza on 2008-07-03
> **jarlath said:**
> I'd like to start programming in linux. The easiest way I find to program is writing scripts. But I want to write GUI apps.


You can use zenity and xdialog for making GUI's for shell scripts. See my wiki (under Linux)

---

### Post by QwUo173Hy on 2008-07-03
Thanks guys. I've actually written both types of app before, but seperately. When I tried to tie the two together, the fork and execlp stuff just drove me crazy. I thought that there might be an easier way in gtk to run bash commands and parse the results natively in the application.

I'll look in to zenity, thanks LaRosa.

---

### Post by dtmilano on 2008-07-03
You should take a look at [autoglade]("http://autoglade.sourceforge.net/").
There's a fairly nice [tutorial]("http://autoglade.wiki.sourceforge.net/autoglade+tutorial+-+first+steps") you can use to get started.
Can reach much further than zenity or xdialog (of course, I'm a bit subjective on this).

---

### Post by QwUo173Hy on 2008-07-09
Thanks dtmilano. I'll look into it. For the mean time, I'm going to go with OpenOffice.org Base. But in the future I'll be looking for a more customised gui and the ability to parse iCal files etc so I'll eventually have to get reading :)

Thanks again,
Jarlath

---

