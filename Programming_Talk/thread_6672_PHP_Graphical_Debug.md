---
title: "PHP Graphical Debug"
date: 2004-11-30
forum: Programming Talk
---

### Post by snaga on 2004-11-30
Is anyone out there graphically debugging PHP scripts? I seem unable to get it going. I have installed DBG, and it seems to be installed OK, according to phpinfo(). It seems like PHPEclipse is promising, but I can't seem to get it to work. My coworker is using PHPed on Windows and loves it. There is a Linux version, but a) its $300, b) the demo version doesn't like the version of libstdc that I have.

Life would be much better with some simple breakpoint, variable analysis graphical debugging. There seem to be several alternatives on Windows, all commercial.

Any help is much appreciated.

dm

---

### Post by dataw0lf on 2004-11-30
Honestly, I haven't looked into this much.  Alls I need is my print_r() ;)  [Here](http://w100w.com/english/php/development_tools/debugging_and_testing/) 
 is a list of a couple little debugging tools that might be of some use.
dataw0lf

---

### Post by snaga on 2004-11-30
Thanks for the reply. I did finally get eclipse to debug. I will write up a howto and post it soon.

dm

---

### Post by bassim on 2005-01-31
snaga, could you share your wisdom with us?

---

### Post by mbria on 2005-02-03
I'm also trying to set up phpeclipse to debug variables and if is possible graphically reproduce a trace.

Finally I find how to trace, but the browser don't reflect the step changes (it's just a simple url browser). But main trouble now is debuging variables. I get a NullPointer (I always though it's a funny message if you think that Java don't uses pointers  :D)

Snaga, what about this brief but clear mini-howto  :p 

thanks a lot in advance,

m.

---

### Post by snaga on 2005-03-06
[QUOTE=mbria]
Snaga, what about this brief but clear mini-howto  :p 
[/QUOTE]

My apologies for not getting to this. Too busy debugging at work to get to the forums, I guess.     8-[ 


Here is a brief how-to. I am doing this from memory, so I may need to edit later when you all find flaws.

1. Install Eclipse and make it go.

2. Install PHPEclipse from phpeclipse.de and make it go

3. Install the dbg debugger as per [this link](http://www.phpeclipse.de/tiki-index.php?page=DbgBasedDebugger) 

iirc it didn't explain that you need to download a command line php interpreter and specify it in the debug setup. I got php4-cgi from synaptic and specified /usr/bin/php4. The debug setup is pretty good to show you what you lack in the setup.

4. This url explans how to engage the debugger with your browser: [Remote Debugging](http://www.phpeclipse.de/tiki-index.php?page=RemoteDebugging) 

Debugging works pretty well. Well enough for me, anyway. One annoyance is that I quite often have to restart the debugger, for seemingly no reason.

Please respond if these instructions suck. I am considering writing something more complete for the wiki. Let me know if that would be useful.

dm

---

### Post by Jad on 2005-03-06
I'm not sure about free debuggers, but Zend Studio has great one

---

### Post by mbria on 2006-02-13
Thanks to snaga for your answer.

I will test (and document) it as soon as I find some spare time.

Cheers,

m.

---

