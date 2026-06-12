---
title: "I know its Over Anxiousness but Please help me."
date: 2006-04-05
forum: Programming Talk
---

### Post by kolichina_s_s on 2006-04-05
HI,

Recently I have run my first C program in Linux, I am a Professional Windows C,C++ Developer. I have no knowledege about Linux and its Kernel(Yet I find VI as the Interesting Editor). But I have to do some serious programming now.

I need to work on a device that connects to **serial Port** and Also my program should do some **Modem Dialing** . Where can i get some materials on this kind of Programming,:confused:  I know its not that Easy but I must do it. I also know if without basic concepts I try to rise high I will fall but believe me .. I need to do this  ](*,) 

I need some kind of guidence. Please Help me

---

### Post by sapo on 2006-04-05
Man, if you have to work with dial up modems on linux, i feel sorry for you.

---

### Post by pitkali on 2006-04-05
Serial port - like /dev/ttyS0 for instance? It is a text file in the file system, right? So I think you could try just writing into it. Is dialing sending textual commands to the modem? Like ATZ ... and the like?

Regards,

---

### Post by ekarni on 2006-04-05
This page should help you with the serial port side of things.
[http://www.lvr.com/serport.htm]("http://www.lvr.com/serport.htm")
A search for "RS-232" should give you plenty more info.

---

### Post by kolichina_s_s on 2006-04-06
[QUOTE=pitkali] Is dialing sending textual commands to the modem? Like ATZ ... and the like?
[/QUOTE]

:confused:  Yes I guess So but i am not sure about any particular command.

---

### Post by kolichina_s_s on 2006-04-06
Hi,

[QUOTE=ekarni]This page should help you with the serial port side of things.
[http://www.lvr.com/serport.htm]("http://www.lvr.com/serport.htm")
A search for "RS-232" should give you plenty more info.[/QUOTE]

Thanks for the Link , at last i have something to Read.

I need one more help , Can you please tell me What is the Substitute of Events (in Windows) on Linux. Can you Please suggest some books and Links on this Event Driven Programming on Linux.:-? 

Thanks a lot for the help

---

### Post by rplantz on 2006-04-06
[QUOTE=kolichina_s_s]
I need to work on a device that connects to **serial Port** and Also my program should do some **Modem Dialing** . Where can i get some materials on this kind of Programming,:confused:  I know its not that Easy but I must do it. I also know if without basic concepts I try to rise high I will fall but believe me .. I need to do this  ](*,) 

I need some kind of guidence. Please Help me[/QUOTE]

First, you do **not** want to talk directly to the serial port (unless you're working on an embedded system and have total control).

I've never done this, but I'm pretty sure that you want to use termios. Look at the man page for this (man termios).

There is a chapter about it in "Linux Programming Unleashed." At the end of the chapter, the authors say that the "canonical technical reference is the O'Reilly book, *termcap & terminfo*, by John Strang, Linda Mui, and Tim O'Reilly."

---

