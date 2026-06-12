---
title: "VI and BASH"
date: 2006-01-29
forum: Programming Talk
---

### Post by krypto_wizard on 2006-01-29
Hi,

I am new to linux and have been using for around 6-7 months now. I like it so much. 

I am starting to explore some scripting in Linux. I use VI editor and BASH shell.


Can some Linux Pros give good shortcut tutorials for VIM and BASH. I am an average VI user but I want to learn lot more things that will make my life easier in VI. Also, I heard BASH shortcuts can be really handy as I hate using my mouse.

Any feedback is greatly appreciated.

Thanks

---

### Post by jrib on 2006-01-29
Best way to get started with vim is to run 'vimtutor'.  There is also a vim book fi you want to read through that: [http://www.truth.sk/vim/vimbook-OPL.pdf](http://www.truth.sk/vim/vimbook-OPL.pdf) .  And a nice cheat sheet is helpful until you remember all of the commands: [http://tnerual.eriogerg.free.fr/vimqrc.pdf](http://tnerual.eriogerg.free.fr/vimqrc.pdf) (or just google, there are plenty).

For bash, here are three things you should read in order of increasing complexity:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

enjoy

---

### Post by toojays on 2006-01-29
I would also recommend that you check out the section of the bash manual titled [Command Line Editing](http://www.gnu.org/software/bash/manual/bashref.html#SEC90).

---

### Post by GTvulse on 2006-01-29
For learning vi, I strongly recommend you pickup O'Reilly's "Learning the vi Editor" from a bookstore. That book will teach you to use vi, from System 7's as you would find in an old UNIX box to nvi, the version used in the BSDs, and the clones, such as vim, elvis and jove. After you have learned the basic command set, you can explore the expanded feature set of your particular implementation of choice. In the case of vim, the best place to learn its advanced features is in the documentation included with the editor and asking questions in the user mailing list. That's the best user manual available. The book mentioned above doesn't cover some of the coolest (and recent) features in vim. The same goes for elvis and jove, btw.

The best books to learn to write scripts with Bash are Free and Open Source. It is a set of two guides available from [The Linux Documentation Project]("http://tldp.org/") called "Bash Guide for Beginners" and "Advanced Bash-Scripting Guide". There are as well several books published that can be of help. I would ask in [comp.unix.shell]("news://comp.unix.shell") for advice on those. Many people will tell you **not to learn** Bash but rather sh or ksh, and they will be correct when pointing out that many Bash scripts are non-portable, but don't let that deter you. The problem is not Bash, but if you want to learn proper POSIX-style shell programming or not.

---

### Post by darth_vector on 2006-01-30
[QUOTE=dradul]For learning vi, I strongly recommend you pickup O'Reilly's "Learning the vi Editor" from a bookstore.[/QUOTE]

indeed; great book. it is online: [http://www.unix.org.ua/orelly/unix/vi/index.htm](http://www.unix.org.ua/orelly/unix/vi/index.htm)

[img]http://www.splange.freeserve.co.uk/img/viman.gif[/img]

---

### Post by darth_vector on 2006-01-30
in fact, the whole o'rielly linux library is available online: [http://www.unix.org.ua/orelly/](http://www.unix.org.ua/orelly/)

---

### Post by matthew on 2006-01-30
[quote=darth_vector]in fact, the whole o'rielly linux library is available online: [http://www.unix.org.ua/orelly/]("http://www.unix.org.ua/orelly/")[/quote]Great link! How did I miss that before?! Thanks, bro. This is a great way to explore the books and decide which ones I really need to buy and which I can make do with the online version for the rare bit of data research.

---

### Post by kvorion on 2006-01-30
I was trying to learn bash scripting a couple of weeks ago. I checked out the two resources I found on tldp.org namely bash beginner's guide and advanced bash scripting. I realised that I needed a lot of time to puruse these two. I needed something that would teach me bash on the fast track. So I found [Bash by example - by Daniel Robbins]("http://www-128.ibm.com/developerworks/library/l-bash.html") and I found it extremely useful and well written. Although it is not a substitute for the two tutorials mentioned before, this will teach you working with bash really fast. So if you are short on time, this is what you should read.

---

