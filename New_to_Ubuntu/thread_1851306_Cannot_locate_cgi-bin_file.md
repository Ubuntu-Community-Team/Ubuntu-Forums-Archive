---
title: "Cannot locate cgi-bin file"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by darkliight on 2011-09-28
Hi everyone, I'm new to the forum, but have found several informative threads which have helped me out tremendously in the past.

Let's get right to it:

I am currently using Ubuntu 11.04 (natty)

I am following along with a book "C Programming in Linux" by David Haskins, and in the very beginning he discusses running programs via the web browser. Now to do this he says that I need to save my executables in: 

/usr/lib/cgi-bin

Now the problem is that I have searched my /usr file and cannot find a cgi-bin folder anywhere. 

Is there any reason /usr/lib/cgi-bin is not on my computer? 
What can I do to fix it?
If it not supposed to exist on my version of Ubuntu, how can I run complied C programs via my web browser (Firefox)?

---

### Post by Immolatus on 2011-09-28
is't probably just in the wrong place. Do in terminal:

locate cgi-bin

this will show you everywhere this appears. The trick is knowing which is the one you're looking for, then just move or copy it to the desired location.

---

### Post by mcduck on 2011-09-28
> **darkliight said:**
> Hi everyone, I'm new to the forum, but have found several informative threads which have helped me out tremendously in the past.

Let's get right to it:

I am currently using Ubuntu 11.04 (natty)

I am following along with a book "C Programming in Linux" by David Haskins, and in the very beginning he discusses running programs via the web browser. Now to do this he says that I need to save my executables in: 

/usr/lib/cgi-bin

Now the problem is that I have searched my /usr file and cannot find a cgi-bin folder anywhere. 

Is there any reason /usr/lib/cgi-bin is not on my computer? 
What can I do to fix it?
If it not supposed to exist on my version of Ubuntu, how can I run complied C programs via my web browser (Firefox)?
Have you actually installed a web server? The location for cgi-bin depends on which server you are using, and can be configured in the server's options.

(/usr/lib/cgi-bin would indeed be the default for Apache web server, but it probably doesn't even exist if you don't have Apache. This might help: [https://help.ubuntu.com/11.04/serverguide/C/httpd.html]("https://help.ubuntu.com/11.04/serverguide/C/httpd.html"))

---

### Post by darkliight on 2011-09-29
Thanks for the terminal command to locate cgi-bin, turns out it was in my cups folder within usr/lib.

---

