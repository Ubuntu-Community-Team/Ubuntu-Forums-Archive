---
title: "Learning Bash Shell"
date: 2013-08-14
forum: Programming Talk
---

### Post by grier-devon on 2013-08-14
So I am in a Unix Fundamental course where by the end of the class we will be writing scripts in Bash, we haven't really gone to deep into Bash yet and I was wondering if there is any good guides that will teach me to use Bash and doing some scripting in Bash since that will be my final.

---

### Post by Bashing-om on 2013-08-14
grier-devon; Hi !

My first choice/recommendation:
[http://mywiki.wooledge.org/FullBashGuide](http://mywiki.wooledge.org/FullBashGuide)

[INDENT][INDENT]this will help
[/INDENT][/INDENT]

---

### Post by grier-devon on 2013-08-14
Awesome, thanks so much for the information since I am trying to get ahead of the class a bit.

---

### Post by Bashing-om on 2013-08-14
grier-devon;
Hey .. quite welcome !
See "newDocs" in my sig .. lots of additional links also for bash guides...But I really like Greg Wooledge's better than any other guide that I have encountered.

[INDENT]small things can lead to great rewards
[/INDENT]

---

### Post by grier-devon on 2013-08-14
Now in your experience what is your preference in text editor's? I am learning on Ubuntu server 12.04 LTS and the instructor is teaching to use Vim, but he said that is not his preference but you will find that on any Linux server.

---

### Post by Bashing-om on 2013-08-14
grier-devon;

My editor of choice is the default text editor "gedit". You will find it is versatile, intuitive to learn -> me being "old school" it is a coder's dream editor.
Amongst the many virtues:
color highlighting
keyword highlighting
syntax verifications
expandable plugin's for particular applications
easily configured
5 steps beyond the old great WYSIWYG text editors !

In my simple world, I have not had occasion to need any other editor, it is what I am accustomed to and fills all my requirements.

[INDENT]use the tool you are more comfortable with
[/INDENT]

---

### Post by Bucky Ball on 2013-08-14
*Thread moved to **Programming Talk**.*

Hi. You'll get plenty of help here with an intro to bash, but just a heads up for future reference: don't ask how to do your homework! (And I am definitely not insinuating that is what you're doing here.) It is against the CoC, and the thread will generally be closed.

If you're stuck on a specific aspect and have done a lot of work to solve the puzzle already, okay. If you haven't tried, haven't started, or just want someone else to do it for you (but you sound too motivated to be doing any of that) don't post. 

Cheers and good luck on your learning curve. ;)

---

### Post by grier-devon on 2013-08-15
Thanks Bashing-om I will try out gedit on my own, the class requires Vim but definitely want to expand my experiences to see what I like so thanks for so much input.

Bucky Balls, thanks for the heads up cause I did not know. I am just trying to move a little faster cause the class is so slow, currently running an A in the class. It is so easy I figured I would come to the community to see what documentation is available for my own learning curve.

I appreciate the input guys.

---

### Post by Bucky Ball on 2013-08-15
This is great. Click 'Learning the shell'.

[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)

---

### Post by Bucky Ball on 2013-08-15
This is great. Click 'Learning the shell'.

[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)

I use nano in the terminal myself. Command to open and edit a file, for instance:

```
sudo nano /etc/fstab
```

Ctl+X to exit, 'y' or 'n' to save and exit to regular user.

Opens in terminal. To just look:

```
nano /etc/fstab
```

Ctl+X to exit to regular user. Nano might be a good way to get used to using the commands rather than the GUI that is Gedit. You will need to learn copy, paste, create files/directories commands, cd to get around. ;)

---

### Post by Habitual on 2013-08-15
You may as well go in somewhat prepared...
Some of these apply, some don't. All could be useful.

[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) 
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) 
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)
[http://www.grymoire.com/Unix/Sh.html](http://www.grymoire.com/Unix/Sh.html)
[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)
[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) 
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)
[http://mylinuxbook.com/linux-shell-environment/](http://mylinuxbook.com/linux-shell-environment/)
[http://www.subsignal.org/doc/AliensBashTutorial.html#Table%20Of%20Contents](http://www.subsignal.org/doc/AliensBashTutorial.html#Table%20Of%20Contents)
[http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf](http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf)
[http://www.linuxhomenetworking.com/](http://www.linuxhomenetworking.com/)
[http://mylinuxbook.com/bash-shell-scripting-part-i/](http://mylinuxbook.com/bash-shell-scripting-part-i/)
[http://mylinuxbook.com/bash-shell-scripting-2/](http://mylinuxbook.com/bash-shell-scripting-2/)
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://linuxcommand.org/lc3_learning_the_shell.php](http://linuxcommand.org/lc3_learning_the_shell.php)
[http://unixhelp.ed.ac.uk/](http://unixhelp.ed.ac.uk/)
[http://www.linuxquestions.org/questions/blog/druuna-60084/resources-useful-links-35334/](http://www.linuxquestions.org/questions/blog/druuna-60084/resources-useful-links-35334/)
[http://www.linuxquestions.org/questions/linux-general-1/links-for-helpful-linux-articles-and-books-4175433508/](http://www.linuxquestions.org/questions/linux-general-1/links-for-helpful-linux-articles-and-books-4175433508/)
[http://www.hammondslegacy.com/forum/viewforum.php?f=40&sid=5859bbcf18ccb151f7de3e86cafdf486](http://www.hammondslegacy.com/forum/viewforum.php?f=40&sid=5859bbcf18ccb151f7de3e86cafdf486)

You teacher is correct, vi(m) would be on most computers.
gedit would require a Desktop Environment which certainly is NOT installed on all computers (headless servers for example).

Learn vi(m). it is very powerful. After becoming comfortable with it, you can choose a graphical text editor.

Pretty interesting site called [shellcheck.net]("http://shellcheck.net") that will check the basics (or more?) of any supplied bash script.

Enjoy.

---

### Post by DarkAmbient on 2013-08-15
tldp.org, one of the sites Habitual linked is probably what I've learned the most from. Both the beginner and the advanced bash-scripting guide.

---

### Post by grier-devon on 2013-08-16
Bucky Ball, I will give nano a shot, I think it is interesting the amount of tools available out there and I appreciate all the support.

Habitual, Thanks for all the links. I see quiet a few that will be beneficial right of the bat and will continue to explore everyone of them and thanks for the shellcheck.net, this will be good to use as I explore and will come in handy for my final.

Seriously guys thanks for all the support, this community is great.

---

### Post by Lars Noodén on 2013-08-16
If you try nano you might want to launch it with -w so that long lines don't get wrapped.  Not that you are likely to get long lines when writing shell scripts, but it can happen.  Alternately you can put *set nowrap*  in your account's .nanorc file.  The full options are explained in the man pages for [nano](http://manpages.ubuntu.com/manpages/raring/en/man1/nano.1.html) and [nanorc](http://manpages.ubuntu.com/manpages/raring/en/man5/nanorc.5.html).  

That said, I'd second the recommendation for working with basic vi at least until you can find your way around with it.  It's going to be present on all non-Windows systems you will run into these days.

---

### Post by kpothi on 2013-08-16
While, Vim is great and can save a lot of time in the long run, the learning curve is steep. So, I'd recommend starting with nano and then migrate to Vim later on. To learn Vim, there's a built-in tutor available that can be brought up with the command `vimtutor` in the bash shell. Also, I'd recommend moving slightly away from Bash and try to learn other shells too, such as [zsh](http://www.zsh.org/), to see what's common among all the shells and what's unique with Bash.

---

### Post by grier-devon on 2013-08-24
Lars Nooden - Thanks for the info on nano and currently still working in basic Vi since that is the class requirement.

kpothi - I am going to check out vimtutor and I will try to move out into the other shells.

Great advice everybody,I appreciate all the input.

---

