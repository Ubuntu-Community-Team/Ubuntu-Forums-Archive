---
title: "Bash Script"
date: 2014-08-21
forum: Programming Talk
---

### Post by garyzw on 2014-08-21
I'm trying to write a simple Script to install a program--I know you can add it in terminal but I wanted to try with a script to see how it is done.
I have the following so far which opens the terminal and but will not go on the the commands. If I create a launcher it works but i wanted to be able to click on the script directly and have I have it bring up the terminal and then execute the commands. Thanks for the help

```

#!/bin/bash
xfce4-terminal 
sudo add-apt-repository ppa:Repository
sudo apt-get update
sudo apt-get install package
```

---

### Post by uRock on 2014-08-21
Put all of the commands in one line.

```
sudo add-apt-repository ppa:Repository && sudo apt-get update && sudo apt-get install package
```

---

### Post by garyzw on 2014-08-21
Thanks uRock I did has you said but it will not open the terminal

```
xfce4-terminal sudo add-apt-repository ppa:Repository && sudo apt-get update && sudo apt-get install package
```

this opens the terminal but will not execute the command
```

xfce4-terminal
sudo add-apt-repository ppa:Repository && sudo apt-get update && sudo apt-get install package
```

---

### Post by uRock on 2014-08-21
No matter how you do it, it still won't work, because it will have to ask for your password.

---

### Post by garyzw on 2014-08-21
Well if it works when I run the script would it not open the terminal and then ask me for the password?

---

### Post by AstroLlama on 2014-08-22
There is no need to execute xfce4-terminal. Bash naturally interprets each line as a command.

I suggest you read up on shell scripting. I am not a career programmer but use it often in my work. It makes life so much easier. Bash is very powreful but to really use it well you need to really understand the vocabulary.

Here are a few links that are VERY useful. bookmark them and read in your spare time :) It will pay off.

[http://www.grymoire.com/Unix/Sh.html]("http://www.grymoire.com/Unix/Sh.html") (this is technically for Bourne shell or sh, not Bourne-again shell, aka bash but to learn the basic syntax the difference isn't so important.)

[http://www.tldp.org/LDP/abs/html/index.html]("http://www.tldp.org/LDP/abs/html/index.html")

[http://www.gnu.org/software/bash/manual/bashref.html]("http://www.gnu.org/software/bash/manual/bashref.html")

---

### Post by sudodus on 2014-08-22
You can try something along the pattern of this command line

```
xterm -hold -e bash -c "echo -e '\nparted: -----'&&sudo parted -l&&echo 'df: -----'&&df"
```

The important thing is to keep the commands after -e together, otherwise the terminal window will only perform the first one, and the rest of the commands remain at the original 'place' (terminal window or whatever).

---

### Post by CaptainMark on 2014-08-22
No one seems to have quite explained what you have done wrong here so I'll try to put it in beginners terms. When your script executes, all commands will be run in order that you write them in the script, one line at a time independently (that's the key word) so when you put in your script to run xfce4-terminal that runs okay, but then it waits for that to finish (when you close it) before executing the following lines, they will then fail because they are expecting you to type in a password (which you can't, its not being run in a terminal)

You can't assume that because you open a terminal and run some commands afterward that bash will know you want those commands to run 'within' your new terminal, you would have to link the commands together somehow for bash to know they are related. Imagine if you had the find command written on an independent line to the rm command, bash wouldn't know you want to remove the files you found, you would have to link them together in some way.

In the example you are using you need to explicitly tell bash you want to open a terminal that will run the following commands, you can use sudodus' example, or the xfce4 terminal has its own version using the -e flag```
xfce4-terminal -e "echo hello && sleep 5"
```PS. I'm not at my computer so although this command looks fine now, I take no responsibility for any fluffy brainedness that I've picked up at work and done something stupid.

---

### Post by ian-weisser on 2014-08-22
CaptainMark is quite right.

It's generally considered a bad idea to put 'sudo' in a script. Sudo is interactive - if the password prompt is not seen by the user, the script will happily hang forever.

Instead, remove sudo from each line but run the entire script with the proper permission. 'sudo MyScript'

Then you grant your script an exception to the sudo rules. So your script doesn't need a password.
*Don't* grant apt-get a password exception. It's tempting, but it also increases the risk that you will accidentally break your system. Keep that protection.
The way you grant an exception to the sudo rules is using the visudo application to edit the sudoers file.

Here's [an example]("http://cheesehead-techblog.blogspot.com/2014/07/etherape-as-root.html") of how I edited sudoers for the Etherape application, to run it with elevated priveleges from the launcher.

---

### Post by garyzw on 2014-08-22
I did this

```
xfce4-terminal -e "sudo add-apt-repository ppa:bhdouglass/indicator-remindor" 

sudo apt-get update && apt-get install indicator-remindor

```

Which brings up the Terminal and asks for the password I enter the password and it adds the ppa but won't go on past that to apt-get update && apt-get install indicator-remindor.

---

### Post by steeldriver on 2014-08-22
Here's what I'd do

Create a simple bash script somewhere with only the administrative commands you want to execute e.g.

```

#!/bin/bash

add-apt-repository ppa:Repository
apt-get update
apt-get install package

```

I created a directory in my home directory called 'scripts' and put it there, but the exact location doesn't matter. Mark it as executable, either through the file manager or from a terminal using 'chmod'

```

chmod +x /path/to/myscript

```

Now right-click on the Xubuntu desktop and select 'Create launcher...' and enter the 'Command' as

```

**gksu** /path/to/myscript

```

Give it a name and add a comment about what the script does, and check the 'Run in terminal' box. After that, you should be able to run it by double-clicking the launcher, at which point 'gksu' will pop up a dialog box for you to enter your password and then run the script in a terminal.

---

### Post by garyzw on 2014-08-22
Yes that work fine steeldriver--thanks. I will do that. I wonder why it does not work when you run the same script without the launcher?

---

### Post by syntaxerror74 on 2014-08-22
> > **garyzw said:**
> 
```
xfce4-terminal -e "sudo add-apt-repository ppa:bhdouglass/indicator-remindor" 

sudo apt-get update && apt-get install indicator-remindor

```

Which brings up the Terminal and asks for the password I enter the  password and it adds the ppa but won't go on past that to apt-get update  && apt-get install indicator-remindor.

I wonder why it does not work when you run the same script without the launcher?

Because you did not read carefully what the other users wrote.
The following (amended) one-liner 
```
xfce4-terminal  -e "sudo add-apt-repository ppa:bhdouglass/indicator-remindor  && apt-get update && apt-get install indicator-remindor"  

```

would (IMHO) work, because sudo is (in general) remembered when used in same terminal session (or as the pros would put it "in same tty", i. e. /dev/pts/*<id>*).
The gist of it is that you have to put ALL three commands in those quotes, because xfce4-terminal will cause anything else following that to be sent to /dev/null.

---

### Post by garyzw on 2014-08-22
> **syntaxerror74 said:**
> Because you did not read carefully what the other users wrote.

```
xfce4-terminal  -e "sudo add-apt-repository ppa:bhdouglass/indicator-remindor  && apt-get update && apt-get install indicator-remindor"  

```

would (IMHO) work, because sudo is (in general) remembered when used in same terminal session (or as the pros would put it "in same tty", i. e. /dev/pts/*<id>*).
The gist of it is that you have to put ALL three commands in those quotes, because xfce4-terminal won't be able to execute anything else beyond that.

Yes i read what others wrote and also tried that it again in a script and it did not work. It opens the Termnial I enter the password then the Terminal closes--no pressing enter to add ppa

---

### Post by sudodus on 2014-08-22
> **garyzw said:**
> Yes i read what others wrote and also tried that it again in a script and it did not work. It opens the Termnial I enter the password then the Terminal closes--no pressing enter to add ppa

Did you try with an additional bash command? It works for me.

```

xterm -hold -e [COLOR=#ff0000]bash -c[/COLOR] "sudo add-apt-repository ppa:bhdouglass/indicator-remindor  && apt-get update && apt-get install indicator-remindor"

```

From ```
man bash
```

```

       -c string
                 If  the -c option is present, then commands are read from string.  If there are argu&#8208;
                 ments after the string, they are assigned to the positional parameters, starting with
                 $0.

```

---

### Post by Erik1984 on 2014-08-23
Don't you also need sudo on the commands after the **&&** operator when they require root privileges?

This doesn't work here:
```
sudo apt-get update && apt-get upgrade
```
The first command works, but the second is executed without root privileges.

This does work:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by sudodus on 2014-08-23
> **Erik1984 said:**
> Don't you also need sudo on the commands after the **&&** operator when they require root privileges?

This doesn't work here:
```
sudo apt-get update && apt-get upgrade
```
The first command works, but the second is executed without root privileges.

This does work:
```
sudo apt-get update && sudo apt-get upgrade
```

Good catch Erik :KS

---

### Post by ofnuts on 2014-08-24
I wonder what is the purpose of adding a ppa/repo in a script.... this is typically something you do once for all.

---

### Post by garyzw on 2014-08-26
> **ofnuts said:**
> I wonder what is the purpose of adding a ppa/repo in a script.... this is typically something you do once for all.

I have several computers with Xubuntu and having a script with mutilple ppa/repo's is very handy if you install multiple programs on different computers it makes it easy. Also if for what every reason I need to re-install I can have a script with all my installed programs and ppa/repo's to quickly re-install them after a fresh install. 

The following is the code that worked perfectly Thanks to Pilosopong Tasyo who helped me with this.

```
#!/bin/bash

# if this script was not launched from a terminal, restart it from a terminal

if [[ ! -t 0 && -x /usr/bin/x-terminal-emulator ]]; then
   /usr/bin/x-terminal-emulator -e "bash -c \"$0 $*; read -s -p 'Press enter to close...'\""
   exit
fi

sudo add-apt-repository ppa:repo
sudo apt-get update
sudo apt-get install package
```

---

### Post by Pinoy Tux on 2014-08-27
You're welcome, garyzw :) (I'm P.T. from the other forum BTW).

---

