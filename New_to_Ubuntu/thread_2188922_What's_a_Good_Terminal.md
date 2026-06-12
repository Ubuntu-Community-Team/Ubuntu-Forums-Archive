---
title: "What's a Good Terminal?"
date: 2013-11-19
forum: New to Ubuntu
---

### Post by ccmiller12 on 2013-11-19
Hello community!

I recently installed Lubuntu. My reasons for choosing linux is because I wanted to familiarize myself with the Bash console hopefully learning every command, and perhaps even writing my own scripts at some point. I just wanted to ask what would be a good primary terminal to use. I've noticed there are several out there that I could install. Is there significant differences between all of these choices? Perhaps someone here has a favorite one they like to use? Just like to get some opinions here.

---

### Post by rburkartjo on 2013-11-19
i also have lubuntu install i like the gnome terminal and tilda. they are all basically do the same. some have tab options. and with gnome and tilda you can put in a custom background.

---

### Post by papibe on 2013-11-19
Hi ccmiller12. Welcome to the forum ):P

In terms of learning bash, they won't make a significant difference, IMHO.

Having said that, I really like [terminator]("http://lifehacker.com/5858676/the-best-terminal-emulator-for-linux"). In fullscreen, it's like having a minimal tiling desktop.

BTW, here's also a very good list useful guidelines: [Command Line Resources]("https://help.ubuntu.com/community/CommandLineResources").

Regards.

---

### Post by public3 on 2013-11-19
I'm currently an OS X user and use iTerm, the only Linux Terminal I can say I really enjoyed using was Konsole.
For a while I did enjoy the wealth of visual customization options available for rxvt however, which desktop environment agnostic terminal.

---

### Post by ccmiller12 on 2013-11-19
Wow, thanks papibe for the link. I like all the comments about the article. They give good ideas on what terminal to choose. I think I'll go ahead and try out a few terminals, and then decide from there. Oh, and also thanks for directing me to some handy resources :). Wish me luck on my journey with linux!

---

### Post by sammiev on 2013-11-19
Hi ccmiller12. Welcome to the forums! Papibe gave you some great advice to say the least. So now I expect you to write new code for my dog to open the fridge and bring me a cold beer. jk of course but then again!?!

---

### Post by audiocat on 2013-11-20
Of the gnome terminals, I like version 3.6 as you can set transparent backgrounds. 3.8 no longer has the transparent setting. My latest favorite, guake, which came with Sabyon is very cool as it is drop down and highly configurable.

---

### Post by CharlesA on 2013-11-20
I kinda like the gnome terminal or Konsole, if I want to pull in a ton of KDE dependencies.

Otherwise it is just ssh all the way. :)

---

### Post by DuckHook on 2013-11-20
To address the larger issue behind your question, I would actually recommend the following:

Run a minimal console-only install in a VM. A minimal install is so light that even a duo-processor CPU will run it like lightning. Because a minimal install has abolutely no GUI, you will be forced to learn the command line way. But because the whole thing is running inside a sandbox on your real machine, you can still have resources like web browsers, pdf readers, etc open beside it and helping you to learn. It's just that your real work has to be done inside the unforgiving environment of the stark CLI-only VM. A VM has the added advantage that a snapshot of the working system can be taken at any time. This frees you up to do some really wild experiments on the VM that you would not even dare to begin on your real system. If you bork it, just roll back to the snapshot and it's like it never happened--except that you will have learned a ton about what not to do!

You will find that command-line utilities like mc, tmux, screen and byobu then become more important concerns than choosing the best terminal app. And more powerful too. The ability of screen and tmux to detach sessions is extremely versatile and powerful. And there's no faster way to learning the command line than forcing yourself to live with it-and-only-it.

---

### Post by Impavidus on 2013-11-20
The first UNIX system I used 11 years ago had low resolution black-and-white screens (no grayscale, it used dithering) and had no graphical file manager. Graphics were quite useless anyway, although menus and the like worked. Anything small and low-contrast (the beautiful cyan on blue buttons on many websites) was unreadable, so I used lynx, a terminal-based web browser, most of the time. The good thing was that I could have several xterms spread over nine workspaces and that black-and-white graphics, like pdf, ps and dvi readers and graphical text editors, worked. I have since switched to vim for all my editing and I still do all my file management in the terminal.

I think it's really nice to have both sides. I use the terminal for most of the input (text editing, file management, configuration) and the GUI for most of the output (previewing documents and graphs, browsing the web, some games), because I think that's what the interfaces are best at. With Linux a very modular system you can change small pieces at once from the GUI to the CLI, so why not start with doing all your file management and configurations in the terminal and slowly deciding what's the best way for everything?

The terminals are all similar. Some have tabbing, some have transparent backgrounds so you can still enjoy the slideshow on your desktop. I'm on Xubuntu, so I use xfce-terminal. More important may be the shell you use. They are similar too, but their difference really matter for the functionality.

To get a complete list of all commands (except for shell built-ins) you can use in the terminal, run this command:```
echo $PATH | sed 's/:/ /g' | xargs ls
```Every program installed on your system is a command, about 3000 on my system, so nobody knows all commands. Especially when considering the possibilities when combining commands together in single lines, like the three commands in the above example. I have used up to 10 commands piped together on a single line, and that's the real power of the command line.

---

### Post by Futant on 2013-11-20
I like Guake.

---

### Post by oldos2er on 2013-11-20
I've been using roxterm on i3, because I like something a bit more than xterm or eterm, but I don't need quite so many features as, say, konsole has--although if you don't mind the dependencies konsole is a great choice. It's down to personal preference.

Edit: For a really whiz-bang terminal emulator, check out [terminology]("http://www.enlightenment.org/p.php?p=about/terminology").

---

### Post by simbauad on 2013-11-21
No one mentioned this but I like urxvt. Came to know about it when I was using Arch.

---

