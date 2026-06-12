---
title: "Question about Pipeline in Bash"
date: 2013-12-13
forum: New to Ubuntu
---

### Post by kevin_do2 on 2013-12-13
Hi, I am currently learning pipes and redirections. I cannot explain the followings:

**cd** ~/Documents | **cd** ~/Desktop --> this doesn't do anything
**ls** ~/Documents | **ls** ~/Desktop --> this will list all files in directory Desktop

**cd** ~/Documents > **cd** ~/Desktop --> current directory will change to ~/Document
**ls** ~/Documents > **ls** ~/Desktop --> this doesn't do anything

As fas as I know, usually the last command will be executed even if that command doesn't accept standard input.
In this case, both command **ls** and** cd** do not accept standard input. However, the right **ls** command works as intended.
Please give me insight about this.
Thanks

---

### Post by DuckHook on 2013-12-13
Pipes and redirects are not used in the ways that you've used them. The pipe command tells the second command to do its work using the output of the first command. So, to take your first line: since the cd command just changes your working directory, you are asking bash to: "change my working directory to 'Desktop' using the output of changing my working directory to 'Documents'", which makes no sense. When you ask Bash to do something that makes no sense, it just gives up and doesn't do anything at all.

If you want to learn about Bash and the command line, I highly recommend the following link. If you learn everything contained therein, you will be a command line wizard in no time!

Command line learning:

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by Impavidus on 2013-12-13
> **kevin_do2 said:**
> Hi, I am currently learning pipes and redirections. I cannot explain the followings:

```
**cd** ~/Documents | **cd** ~/Desktop --> this doesn't do anything
```
**cd** isn't really an ordinary command; it's part of the shell. This instructs the shell to change its working directory to **~/Documents** and use the output to change the working directory to **~/Desktop**. This doesn't make sense.```

**ls** ~/Documents | **ls** ~/Desktop --> this will list all files in directory Desktop
```
This instructs the shell to run the command **ls ~/Documents**, which works, but doesn't produce any visible effects, and then send the output into the input of **ls ~/Desktop**. **ls ~/Desktop** will not use this input and will just list the contents of **~/Desktop**
```

**cd** ~/Documents > **cd** ~/Desktop --> current directory will change to ~/Document
```
This changes the working directory to **~/Documents** and would redirect any output, if it existed, to the file **cd**. (Edit: it should produce an empty file named **cd**.) The argument **~/Documents** is ignored.```

**ls** ~/Documents > **ls** ~/Desktop --> this doesn't do anything
```
This lists the contents of the directories **~/Documents** and **~/Desktop** and redirects the output to the file **ls**. So it does do something. Check again if you can find a  file named **ls**.
> 
As fas as I know, usually the last command will be executed even if that command doesn't accept standard input.
In this case, both command **ls** and** cd** do not accept standard input. However, the right **ls** command works as intended.
Please give me insight about this.
Thanks

---

### Post by philinux on 2013-12-13
See this. 

[http://ubuntuforums.org/showthread.php?t=2190238](http://ubuntuforums.org/showthread.php?t=2190238)

---

### Post by kevin_do2 on 2013-12-14
> **Impavidus said:**
> ```
**cd** ~/Documents | **cd** ~/Desktop --> this doesn't do anything
```
**cd** isn't really an ordinary command; it's part of the shell. This instructs the shell to change its working directory to **~/Documents** and use the output to change the working directory to **~/Desktop**. This doesn't make sense.```

**ls** ~/Documents | **ls** ~/Desktop --> this will list all files in directory Desktop
```
This instructs the shell to run the command **ls ~/Documents**, which works, but doesn't produce any visible effects, and then send the output into the input of **ls ~/Desktop**. **ls ~/Desktop** will not use this input and will just list the contents of **~/Desktop**
```

**cd** ~/Documents > **cd** ~/Desktop --> current directory will change to ~/Document
```
This changes the working directory to **~/Documents** and would redirect any output, if it existed, to the file **cd**. (Edit: it should produce an empty file named **cd**.) The argument **~/Documents** is ignored.```

**ls** ~/Documents > **ls** ~/Desktop --> this doesn't do anything
```
This lists the contents of the directories **~/Documents** and **~/Desktop** and redirects the output to the file **ls**. So it does do something. Check again if you can find a  file named **ls**.

Your answer is perfect. That's what I'm looking for. Thank you.

---

### Post by vasa1 on 2013-12-15
> **DuckHook said:**
> ... The pipe command tells the second command to do its work using the output of the first command. ...
Just to muddy the waters a bit: [In what order do piped commands run?]("http://unix.stackexchange.com/q/37508/15760")

---

