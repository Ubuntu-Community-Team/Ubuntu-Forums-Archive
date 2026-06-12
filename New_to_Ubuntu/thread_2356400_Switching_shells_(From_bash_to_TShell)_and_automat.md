---
title: "Switching shells (From bash to TShell) and automatically sourcing directories"
date: 2017-03-22
forum: New to Ubuntu
---

### Post by wespawloski on 2017-03-22
Hello and thanks for your time,

I'm running ubuntu 16.10 out of the box. I am interested in running a program which requires CShell, and have therefore installed TShell. Following the install guide, I created a ~/.cshrc file and added the following line:
```
     if (-e /home/wes/Pipe_Install/com/nmrInit.linux212_64.com) then
        source /home/wes/Pipe_Install/com/nmrInit.linux212_64.com
     endif
```


where wes is my username. 

When manually inputting "source /home/wes/Pipe_Install/com/nmrInit.linux212_64.com" I can call the desired programs from terminal. However, simply calling the terminal does not automatically source the directory. Restarting has not solved the problem. I have tried adding this line to /etc/csh.cshrc as well, to no avail. Am I missing something simple? 

Thanks.

---

### Post by papibe on 2017-03-23
Hi wespawloski.

Do you mean you installed [tcsh]("http://manpages.ubuntu.com/manpages/xenial/en/man1/tcsh.1.html")? 

tsch first looks for   ~/.tcshrc . Only if that does not exist it goes looking for ~/.cshrc .

Does the cshell script you want to run have a shebang? is it #!/bin/csh or #!/bin/tcsh ? Change it a appropriately. 

Note that by just installing another shell does not actually changes your default shell, which is bash. If you really want to change your default shell take a look at [this]("http://askubuntu.com/questions/131823/cant-make-zsh-the-default-shell").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by wespawloski on 2017-03-23
Thanks for the response. 

Yes, I installed tcsh. I assumed that because no ~/.tcshrc was created, ~/.cshrc would be defaulted to. 

I will have to check your answer regarding a shebang. However, I had previously(On a different install) got everything running by changing my login shell to tcsh and everything ended up working. I was hoping that after a fresh install I could use bash instead, and simply change my shell to tcsh when I wanted to run this program.

My current knowledge indicates that I do not need to be running TShell as the login shell to run the "source" command automatically upon starting the shell. I assumed that by creating a ~/.cshrc, the commands included therein would be run on switching from bash to TShell, ie running "tcsh" in terminal.

---

### Post by vasa1 on 2017-03-23
And did you mean 16.10 and not 6.10? If so, please edit your post. Thanks!

---

### Post by papibe on 2017-03-23
> **wespawloski said:**
> My current knowledge indicates that I do not need to be running TShell as the login shell to run the "source" command automatically upon starting the shell. I assumed that by creating a ~/.cshrc, the commands included therein would be run on switching from bash to TShell, ie running "tcsh" in terminal.
So, you run tcsh on the terminal, but the source is not happening? right? you have to do it manually?

I would guess it is a syntax problem. Could you paste your ~/.cshrc using coding tags ?

Regards.

---

### Post by wespawloski on 2017-03-23
Just following the syntax suggested by the program author, I created ~/.cshrc with these lines.

```
     if (-e /home/wes/Pipe_Install/com/nmrInit.linux212_64.com) then
        source /home/wes/Pipe_Install/com/nmrInit.linux212_64.com
     endif

     if (-e /home/wes/Pipe_Install/dynamo/com/dynInit.com) then
        source /home/wes/Pipe_Install/dynamo/com/dynInit.com
     endif
```

---

### Post by papibe on 2017-03-23
Thanks. Code looks OK.

Could you open a terminal, run this and paste back the results (you can copy paste the text)?
```
tcsh -V
```
Regards.

---

### Post by wespawloski on 2017-03-23
So after entering -V, I noticed it was spitting out the variables defined in /etc/csh.cshrc. I left some lines defined there, most likely incorrectly, when I was trying to set things up last night. After removing the manually added lines, leaving the file as default :

```
# /etc/csh.cshrc: system-wide .cshrc file for csh(1) and tcsh(1)

if ($?tcsh && $?prompt) then

	bindkey "\e[1~" beginning-of-line # Home
	bindkey "\e[7~" beginning-of-line # Home rxvt
	bindkey "\e[2~" overwrite-mode    # Ins
	bindkey "\e[3~" delete-char       # Delete
	bindkey "\e[4~" end-of-line       # End
	bindkey "\e[8~" end-of-line       # End rxvt

	set autoexpand
	set autolist
	set prompt = "%U%m%u:%B%~%b%# "

```

Everything now works fine! Thanks for your help, I figured it would be something silly.

---

