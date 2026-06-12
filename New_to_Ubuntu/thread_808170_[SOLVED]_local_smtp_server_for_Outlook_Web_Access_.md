---
title: "[SOLVED] local smtp server for Outlook Web Access 2003"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by funfrank on 2008-05-26
Hi everybody,

I just made the switch to Ubuntu yesterday. I've always fancied myself as an open-source kind of guy, and now I'm happy to finally be one. 

My XP setup allowed me to send (smtp) and receive (pop) owa messages with a nifty local server written in visual basic called pop2owa. Receiving messages with pop is fairly straightforward with any mail client, but sending with your actual owa address is not so typical. And we all know it is far better to give than to receive. 

This local server has become absolutely essential for making my world pleasant, and I would be terribly surprised if the same XP solution is not available in linux. 

I have done a little homework and have a few questions for someone with more linux experience than myself:

1. Carlos, the author of pop2owa makes the visual basic source code available on sourceforge. Is it possible to compile this source code "as is" and run it on linux?  (I'm nowhere near being able to program yet, hence the "as is" requirement). If compiling is possible, how does one compile visual basic code?

2. Is there another solution?  I've looked at freepops, but the documentation claims that it does not function as an smtp server.  EXIM4 seems to be promising, but I must admit, their documentation and website frightens a noob like me. If this is what must be done, I'm willing, but I'd thought I'd send a ping on this forum first since my need seems pretty common (but not common enough to get a straight answer in the forum archives).

Frank Fun

---

### Post by quelx on 2008-05-26
MrPostman [http://mrpostman.sourceforge.net/](http://mrpostman.sourceforge.net/) can act as an SMTP gateway

---

### Post by funfrank on 2008-05-26
thanks for that link quelx, but I quickly solved my problem... I'm really beginning to appreciate linux. For other noobies searching for a solution, I recommend the following:

1. read this article at linux.com: [http://www.linux.com/feature/119379](http://www.linux.com/feature/119379) and pay attention to exim4

2. install exim4 from synaptic.

3. following the instructions exactly in the article to set up your smtp server

happy sending owa mail from your web client,

Frank Fun

---

