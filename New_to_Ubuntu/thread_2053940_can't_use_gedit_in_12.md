---
title: "can't use gedit in 12"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by bluewizard814 on 2012-09-06
I installed a new server with Ubuntu 12.04 and everything was fine.  Now I can't gedit.  I'm trying to edit the sources.list and everytime I type in sudo gedit /etc/apt/sources.list it asks me for my password and then says it cannot open display.  After that it says run "gedit --help" to see a full list of available command line options.  It worked before.  What am I doing wrong now?

---

### Post by shreepads on 2012-09-06
> **bluewizard814 said:**
> I installed a new server with Ubuntu 12.04 and everything was fine.  Now I can't gedit.  I'm trying to edit the sources.list and everytime I type in sudo gedit /etc/apt/sources.list it asks me for my password and then says it cannot open display.  After that it says run "gedit --help" to see a full list of available command line options.  It worked before.  What am I doing wrong now?

Try:

```
$ gksudo gedit /etc/apt/sources.list
```

---

### Post by cortman on 2012-09-06
> **bluewizard814 said:**
> I installed a new server with Ubuntu 12.04 

Ok, surely you're not trying to run gedit on a headless (x-less) server? Maybe I'm reading it wrong, but you DO need X installed and running to open gedit.
And +1 to shreepads- always use gksu(do) for graphical programs.

---

### Post by sandyd on 2012-09-06
> **bluewizard814 said:**
> I installed a new server with Ubuntu 12.04 and everything was fine.  Now I can't gedit.  I'm trying to edit the sources.list and everytime I type in sudo gedit /etc/apt/sources.list it asks me for my password and then says it cannot open display.  After that it says run "gedit --help" to see a full list of available command line options.  It worked before.  What am I doing wrong now?

Are you trying to use gedit in Ubuntu Server? (i.e. without an GUI, only a terminal)

---

### Post by sudodus on 2012-09-06
I suggest that you do not install X in a server, and that you use a text editor.

There are several nice editors, that work in text mode, for example

- nano (very simple and intuitive)

- vim (fairly advanced, easy to use once you learn the basics, but quite different from 'notepad-looking' editors)

- emacs (very advanced, popular among programmers and oldtimers who learned it when Unix ruled. Emacs can run in text mode as well as GUI mode)

See this link about security (what is actually maintained through the 5 year lifetime of the server edition)

[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1954702_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1954702")

---

