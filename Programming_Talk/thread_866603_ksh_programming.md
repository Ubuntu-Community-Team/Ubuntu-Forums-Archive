---
title: "ksh programming"
date: 2008-07-21
forum: Programming Talk
---

### Post by jamesdcarroll on 2008-07-21
I'm banging my head on my desk. I'm a VB/Java/Oracle programmer being thrust into the Unix world and I need to learn Korn shell programming (I'm working through the Rosenberg book).

I have a few questions I'm hoping you can help me out with.

1. vi is just pure evil, isn't it?  ARRRGH!! :mad:

2. I installed ksh from synaptic and when I look in /bin I see 'ksh' which is a link (?) to '/etc/alternatives/usr.bin.ksh' which in turn is a link to '/bin/ksh93' which is the actual executable sitting right next to the original link. Is that right? 

3. When I open terminal I'm in bash, right?

4. When I type 'ksh' the prompt changes and I 'think' that I am in the korn shell. In fact, when I enter a command that it doesn't like it complains: 'ksh: blah: not found [No such file or directory]' instead of 'bash: blah: command not found'. Am I really in the Korn shell?

5. When I type 'ksh93' and do the same thing I get 'ksh93: blah: not found [No such file or directory]'. If all the 'ksh' items are just links that all end up at '/bin/ksh93' why would there be a difference? Shouldn't 'ksh' respond with 'ksh93:'?

6. The very first command the book has you try is 'echo $RANDOM' claiming that if you are in the Bourne shell you'll get nothing. I get an integer return. This, plus [5] is confusing me as to what shell I'm really in; that there's something going on that isn't what I think/ the book is telling me.

7. The book says that PS1 contains the command prompt and I'd like to change it to '$PWD> ' as the default when it first starts. Is there a file where I can do that?

I have a feeling that once I get my feet under me from an environment perspective (kind of like when I learned what the classpath in JAVA was all about), I'll be able to move fairly quickly, but right now I'm not moving at all

Thanks!

---

### Post by Alasdair on 2008-07-22
By default you will be using bash and when you enter 'ksh' into the bash prompt you will be using ksh. To make ksh your default shell you need to use the change shell command 'chsh'. It will prompt you for the location of ksh (which you can find with the whereis command) and your password. You can customize your ksh shell using a .kshrc file in your home directory - see [here]("http://docsrv.sco.com/SHL_custom/The_Korn_shell_profile_and_kshrc.html") for more details.

Vi is very evil and if you wish to remain sane I recommend switching to emacs

---

### Post by pdwerryhouse on 2008-07-22
1) vi isn't evil. It just has a steep learning curve :)  I've been using it for almost 18 years now and can't stand any other editor.

2) Yes, that's right. There's lots of different versions of ksh available, so ubuntu lets the alternatives system pick the one you want.

3) You're in whatever shell that your user is set to in the /etc/passwd file. Yes, bash is probably the default.

4) Yes, you're in the korn shell.

5) The shell is likely coded so that it will respond with whatever name you called it with. If you copied the binary to /tmp/wibble and then ran that, it would call itself 'wibble'

6) The korn shell isn't the bourne shell. Bourne shell has no built-in variable called RANDOM, whereas the korn shell does.

7) You can do this with:   PS1='$PWD > '     Drop that into your .profile file to make sure it runs every time you log in.

---

