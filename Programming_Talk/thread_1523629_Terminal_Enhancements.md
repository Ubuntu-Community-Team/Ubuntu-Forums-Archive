---
title: "Terminal Enhancements"
date: 2010-07-03
forum: Programming Talk
---

### Post by lkjoel on 2010-07-03
[B][COLOR="Red"]Notice to all readers reading this:
All of this talk was concerning Terminal Enhancements 0.1a.
0.2 was created on the same day that the last post (the post before this one) was posted. (2010-07-06, proof: [https://launchpad.net/terminal-enhancements/0.2-stable/0.2-stable]("https://launchpad.net/terminal-enhancements/0.2-stable/0.2-stable"))
Terminal Enhancements >= 2.2.1 has all of these problems mentioned here fixed.
[/COLOR][/B]


[SIZE=6][COLOR=#0000ff]N[/COLOR][COLOR=#3f00c0]e[/COLOR][COLOR=#7e0081]w[/COLOR][COLOR=#bd0042]s[/COLOR][/SIZE]
[SIZE=5][SIZE=6][SIZE=1] [SIZE=4][COLOR=#0000ff]V[/COLOR][COLOR=#1100ee]e[/COLOR][COLOR=#2200dd]r[/COLOR][COLOR=#3300cc]s[/COLOR][COLOR=#4400bb]i[/COLOR][COLOR=#5500aa]o[/COLOR][COLOR=#660099]n[/COLOR] [COLOR=#880077]2[/COLOR][COLOR=#990066].[/COLOR][COLOR=#aa0055]0[/COLOR] [COLOR=#cc0033]h[/COLOR][COLOR=#dd0022]a[/COLOR][COLOR=#ee0011]s[/COLOR] [COLOR=#dd2200]b[/COLOR][COLOR=#cc3300]e[/COLOR][COLOR=#bb4400]e[/COLOR][COLOR=#aa5500]n[/COLOR] [COLOR=#887700]r[/COLOR][COLOR=#778800]e[/COLOR][COLOR=#669900]l[/COLOR][COLOR=#55aa00]e[/COLOR][COLOR=#44bb00]a[/COLOR][COLOR=#33cc00]s[/COLOR][COLOR=#22dd00]e[/COLOR][COLOR=#11ee00]d[/COLOR][COLOR=#00ff00]![/COLOR]
[/SIZE][/SIZE][/SIZE][/SIZE][SIZE=4][COLOR=#0000ff]W[/COLOR][COLOR=#0f00f0]i[/COLOR][COLOR=#1e00e1]t[/COLOR][COLOR=#2d00d2]h[/COLOR] [COLOR=#4b00b4]m[/COLOR][COLOR=#5a00a5]a[/COLOR][COLOR=#690096]n[/COLOR][COLOR=#780087]y[/COLOR] [COLOR=#960069]A[/COLOR][COLOR=#a5005a]l[/COLOR][COLOR=#b4004b]i[/COLOR][COLOR=#c3003c]a[/COLOR][COLOR=#d2002d]s[/COLOR][COLOR=#e1001e]e[/COLOR][COLOR=#f0000f]s[/COLOR] [COLOR=#e11e00]a[/COLOR][COLOR=#d22d00]n[/COLOR][COLOR=#c33c00]d[/COLOR] [COLOR=#a55a00]E[/COLOR][COLOR=#966900]a[/COLOR][COLOR=#877800]s[/COLOR][COLOR=#788700]t[/COLOR][COLOR=#699600]e[/COLOR][COLOR=#5aa500]r[/COLOR] [COLOR=#3cc300]E[/COLOR][COLOR=#2dd200]g[/COLOR][COLOR=#1ee100]g[/COLOR][COLOR=#0ff000]s[/COLOR][COLOR=#00ff00]![/COLOR][/SIZE]
[SIZE=5][SIZE=6][SIZE=1][SIZE=4] [[COLOR=#0000ff]D[/COLOR][COLOR=#1c00e3]o[/COLOR][COLOR=#3800c7]w[/COLOR][COLOR=#5400ab]n[/COLOR][COLOR=#70008f]l[/COLOR][COLOR=#8c0073]o[/COLOR][COLOR=#a80057]a[/COLOR][COLOR=#c4003b]d[/COLOR] [COLOR=#fc0003]i[/COLOR][COLOR=#fc1c00]t[/COLOR] [COLOR=#c45400]t[/COLOR][COLOR=#a87000]o[/COLOR][COLOR=#8c8c00]d[/COLOR][COLOR=#70a800]a[/COLOR][COLOR=#54c400]y[/COLOR][COLOR=#38e000]![/COLOR]]("https://launchpad.net/terminal-enhancements/0.3")
[/SIZE][/SIZE][/SIZE]
[COLOR=#0000ff]A[/COLOR][COLOR=#3300cc]b[/COLOR][COLOR=#660099]o[/COLOR][COLOR=#990066]u[/COLOR][COLOR=#cc0033]t[/COLOR][/SIZE]
I love using the terminal, but sometimes it is very frustrating having typed a lot, but the I receive an error message:
```
DriverforOpenGL.sh
DriverforOpenGL.sh, command not found
```or:
```
./DriverforOpenGL.sh
DriverforOpenGL.sh, Permission denied.
```So I made a script that fixes one of the two, and is highly customizable.
The current version is 2.0

[SIZE=5][COLOR=#0000ff]F[/COLOR][COLOR=#1f00e0]e[/COLOR][COLOR=#3e00c1]a[/COLOR][COLOR=#5d00a2]t[/COLOR][COLOR=#7c0083]u[/COLOR][COLOR=#9b0064]r[/COLOR][COLOR=#ba0045]e[/COLOR][COLOR=#d90026]s[/COLOR][/SIZE]
[SIZE=5] [SIZE=1]Featured in 2.0, it has a many useful aliases, and some easter eggs!

[SIZE=5][COLOR=#0000ff]V[/COLOR][COLOR=#1f00e0]e[/COLOR][COLOR=#3e00c1]r[/COLOR][COLOR=#5d00a2]s[/COLOR][COLOR=#7c0083]i[/COLOR][COLOR=#9b0064]o[/COLOR][COLOR=#ba0045]n[/COLOR][COLOR=#d90026]s[/COLOR]
[SIZE=1]Enhancements.tar.gz: 2.0
Installer: 2.0
Web Installer: 2.0
[/SIZE][/SIZE][/SIZE][/SIZE] 
[SIZE=5][COLOR=#0000ff]I[/COLOR][COLOR=#1500ea]n[/COLOR][COLOR=#2a00d5]s[/COLOR][COLOR=#3f00c0]t[/COLOR][COLOR=#5400ab]a[/COLOR][COLOR=#690096]l[/COLOR][COLOR=#7e0081]l[/COLOR][COLOR=#93006c]a[/COLOR][COLOR=#a80057]t[/COLOR][COLOR=#bd0042]i[/COLOR][COLOR=#d2002d]o[/COLOR][COLOR=#e70018]n[/COLOR]
[SIZE=1]To install, download it from [https://launchpad.net/terminal-enhancements](https://launchpad.net/terminal-enhancements)
[SIZE=3] Recommended installation:[/SIZE]
Download webinstall.sh, and type in a terminal (Applications->Accessories->Terminal) window:
```
sudo ./webinstall.sh
```[SIZE=3]Another way of installing it:[/SIZE]
First download the enhancements.tar.gz archive.
Then download install.sh, and type in a terminal (Applications->Accessories->Terminal) window:
```
sudo ./install.sh
```You installed it!
[/SIZE][/SIZE] 
**[SIZE=3]For any problems, ideas or anything else, please reply to this thread![/SIZE]**

---

### Post by d3v1150m471c on 2010-07-03
...what does this do?

---

### Post by mobilediesel on 2010-07-04
> **lkjoel said:**
> [SIZE=5]About[/SIZE]
I love using the terminal, but sometimes it is very frustrating having typed a lot, but the I receive an error message:
```
DriverforOpenGL.sh
DriverforOpenGL.sh, command not found
```
or:
```
./DriverforOpenGL.sh
DriverforOpenGL.sh, Permission denied.
```
So I made a script that fixes one of the two, and is highly customizable.
The current version is 0.1b

[SIZE=5]Installation
[SIZE=1]To install, type this in a terminal window:
[/SIZE][/SIZE]```
gedit ~/.enhancedterminal.sh
```
In the gedit window, type:
Save it, then close.
Still in the Terminal type:
```
gedit ~/.bashrc
```
You will see a lot of text pop up.
At the end, type:
```
chmod +x ~/.enhancedterminal.sh
~/.enhancedterminal.sh
```
You installed it!

**[SIZE=3]For any problems, ideas or anything else, please reply to this thread![/SIZE]**

You could skip most of that and just add
```
PATH=$PATH:./
```
to the end of your ~/.bashrc

---

### Post by schauerlich on 2010-07-04
...

All this does is add the current directory to $PATH, and then try to simulate a bash prompt by printing the current directory and reading/executing commands.

A much, much smarter and easier way to do this is just add

```
export PATH=$PATH:.
```

to the end of your ~/.bashrc

---

### Post by wkhasintha on 2010-07-04
Thanx

---

### Post by dwhitney67 on 2010-07-04
I agree; augmenting the PATH variable from within the .bashrc is all that is needed.  Some may argue though, that appending the "." to the path may introduce a security risk.

As for the other issue the OP was having, it was merely a file permission problem.  It appears as if the script lacked the ability to be executed.  That is easily solved with:
```

chmod 744 DriverforOpenGL.sh

```

---

### Post by Bachstelze on 2010-07-04
> **dwhitney67 said:**
> I agree; augmenting the PATH variable from within the .bashrc is all that is needed.  Some may argue though, that appending the "." to the path may introduce a security risk.

It's not a matter of argument: it *does* introduce a security risk. What's arguable is whether or not this security risk outweighs the added convenience.

---

### Post by Penguin Guy on 2010-07-04
Nice code, but you could simply add this to your [FONT="Courier New"].bashrc[/FONT]:
```
quit() { exit; }
PATH="$PATH:."
```

---

### Post by geirha on 2010-07-04
And now I bet you're wondering what that empty file named "5" is doing in your homedir...

> **lkjoel said:**
> ```
#!/bin/bash
...
while [ x > 5 ]
...
```


---

### Post by xsinsx on 2010-07-04
> 
```

./DriverforOpenGL.sh
DriverforOpenGL.sh, Permission denied.

```



This can simply be fixed with the !! << double shabang when youve done that. Type ```
Macintosh:etc stephenjackson[color=#19177C]$ [/color]mkdir /etc/hello
mkdir: /etc/hello: Permission denied
Macintosh:etc stephenjackson[color=#19177C]$ [/color]sudo !!
sudo mkdir /etc/hello
Password:
Macintosh:etc stephenjackson[color=#19177C]$ [/color]

```

and it retrieves your last command and executes it with the sudo at the beginning.

**NOTE: Im not being condescending I was just pointing out what I use. I find its great you are taking the time to learn a little shell scripting I hope my tip is of use to you or anyone else who may not have seen this before.**

---

### Post by Bachstelze on 2010-07-04
> **xsinsx said:**
> This can simply be fixed with the !! << double shabang when youve done that. Type ```
Macintosh:etc stephenjackson[color=#19177C]$ [/color]mkdir /etc/hello
mkdir: /etc/hello: Permission denied
Macintosh:etc stephenjackson[color=#19177C]$ [/color]sudo !!
sudo mkdir /etc/hello
Password:
Macintosh:etc stephenjackson[color=#19177C]$ [/color]

```

and it retrieves your last command and executes it with the sudo at the beginning.

Those are totally different issues, running the script as root is not always what you want.

---

### Post by lkjoel on 2010-07-04
It is a terminal, and this will be implemented.
I agree with all of your comments, but not for long.
All of the other code will be used;)

---

### Post by lkjoel on 2010-07-04
> **d3v1150m471c said:**
> ...what does this do?
It makes it easier to use a terminal.
This is mostly aimed for people who are tired of all those annoying error messages popping up, and beginners to Ubuntu.

---

### Post by slavik on 2010-07-04
> **Bachstelze said:**
> It's not a matter of argument: it *does* introduce a security risk. What's arguable is whether or not this security risk outweighs the added convenience.
agreed, BUT! there is a but :(

if your system is properly secured from the network (firewalls/nats) and OS (good passwords, sshd patched and not on weird demo keys), then adding current directory to the end of the path doesn't do much in the way of security since all other system directories are searched anyway.

in either case, you should be using any priveledged commands under some logged super user utility (sesudo, sudo?, sudoscript, etc.)

---

### Post by xsinsx on 2010-07-05
> **Bachstelze said:**
> Those are totally different issues, running the script as root is not always what you want.


Understood but in his example it was implied he wanted a sudo. I was demonstrating my way around when I forget to run something I need as root. I do understand the issue of changing permissions that was used in that example. I am just pointing out an alternative if and when you need to fix a missing sudo or anything you may have missed in the previous command.

**opps I misread he was not implying a sudo**.

---

### Post by lkjoel on 2010-07-05
I was wondering what was the security risk with adding the **.** to the Path.
I know that it could be dangerous for running the script as root, but the installation doesn't run it as root.

---

### Post by schauerlich on 2010-07-05
> **lkjoel said:**
> I was wondering what was the security risk with adding the **.** to the Path.
I know that it could be dangerous for running the script as root, but the installation doesn't run it as root.

A malicious script could name itself "ls" and put it in the current directory. Then, the next time you want use ls, the malicious script is run instead.

---

### Post by lkjoel on 2010-07-05
> **schauerlich said:**
> A malicious script could name itself "ls" and put it in the current directory. Then, the next time you want use ls, the malicious script is run instead.
But wouldn't there be TWO ls's?
Only one of them can run right?

I could also add an antivirus feature, which would make this terminal the safest ever...

---

### Post by lkjoel on 2010-07-05
> **dwhitney67 said:**
> I agree; augmenting the PATH variable from within the .bashrc is all that is needed.  Some may argue though, that appending the "." to the path may introduce a security risk.

As for the other issue the OP was having, it was merely a file permission problem.  It appears as if the script lacked the ability to be executed.  That is easily solved with:
```

chmod 744 DriverforOpenGL.sh

```
I'm not having any issues. This is mostly for beginners, who are new to Ubuntu, and are used to windows.
And I prefer;
```
chmod +x DriverforOpenGL.sh
```

---

### Post by geirha on 2010-07-05
> **lkjoel said:**
> But wouldn't there be TWO ls's?
Only one of them can run right?


Yes, the first one it finds is the one it will run. But he/she can also be clever and call it sl and wait for you to slip up.

---

### Post by lkjoel on 2010-07-05
> **geirha said:**
> Yes, the first one it finds is the one it will run. But he/she can also be clever and call it sl and wait for you to slip up.
Yes, but this is a template version, and I will try to eliminate those security bugs next release version.

---

### Post by lkjoel on 2010-07-05
> **geirha said:**
> And now I bet you're wondering what that empty file named "5" is doing in your homedir...
Oops, could you tell me how to do it?

---

### Post by lkjoel on 2010-07-05
Oh now I get it.
I am a JavaScript programmer, and I forgot that BASH is not JavaScript!
I changed it to:
```
while [ $x -gt 5 ]
```
And a new release has been made, 0.1.1b.

---

### Post by mobilediesel on 2010-07-05
> **lkjoel said:**
> Oops, could you tell me how to do it?

Try it like this:
```
while true; do
```

although I, and apparently a few others, still don't see the point of this "application."

---

### Post by lkjoel on 2010-07-05
> **mobilediesel said:**
> Try it like this:
```
while true; do
```although I, and apparently a few others, still don't see the point of this "application."
It is for beginners, and people who just don't want to leave windows (poor people:p)
And thanks, but check my last post.

---

### Post by schauerlich on 2010-07-05
> **lkjoel said:**
> It is for beginners, and people who just don't want to leave windows (poor people:p)
And thanks, but check my last post.

I don't mean to be rude, simply blunt. Most people get what your application *does*, they're just saying that it's essentially useless. The only problem that it attempts to solve is one that has already been solved by the shell itself, making your application redundant. In fact, it makes the terminal *less* useful, because instead of interacting with bash itself, you're interacting with your poor imitation of a bash prompt.

---

### Post by lkjoel on 2010-07-05
> **schauerlich said:**
> I don't mean to be rude, simply blunt. Most people get what your application *does*, they're just saying that it's essentially useless. The only problem that it attempts to solve is one that has already been solved by the shell itself, making your application redundant. In fact, it makes the terminal *less* useful, because instead of interacting with bash itself, you're interacting with your poor imitation of a bash prompt.
Yes, but this is a template, and I will add some more features, to put it as a Linux Command Prompt. (still for windows users)

---

### Post by schauerlich on 2010-07-05
> **lkjoel said:**
> Yes, but this is a template, and I will add some more features, to put it as a Linux Command Prompt. (still for windows users)

I don't think you understand. I'd explain it again, but I'm guessing you'll just ignore it and keep doing whatever anyways. Have fun.

---

### Post by mobilediesel on 2010-07-05
> **lkjoel said:**
> Yes, but this is a template, and I will add some more features, to put it as a Linux Command Prompt. (still for windows users)

You're "solving" a problem that doesn't exist with a "template/application" that only adds "current directory" to the PATH variable and then simply passes commands to the shell.

> **schauerlich said:**
> I don't think you understand. I'd explain it again, but I'm guessing you'll just ignore it and keep doing whatever anyways. Have fun.

It's probably time for the both of us to unsubscribe from this thread. There's clearly nothing more we can say here to help.

---

### Post by lkjoel on 2010-07-05
> **schauerlich said:**
> I don't think you understand. I'd explain it again, but I'm guessing you'll just ignore it and keep doing whatever anyways. Have fun.
It is not supposed to be a BASH. It is supposed to be a new shell, made for easiness and clarity. So then a beginner might learn it in a day, and an expert might use it for power usage.
What do you think?
(Note: I did make it in about 2-5 minutes, so it is a quite dirty shell script)

---

### Post by schauerlich on 2010-07-05
> **lkjoel said:**
> It is not supposed to be a BASH. It is supposed to be a new shell, made for easiness and clarity. So then a beginner might learn it in a day, and an expert might use it for power usage.
What do you think?
(Note: I did make it in about 2-5 minutes, so it is a quite dirty shell script)

But it's not a shell. You change one variable and then play "pass the bucket" with bash. If you want to write a shell, learn C and fork bash.

---

### Post by mobilediesel on 2010-07-05
> **lkjoel said:**
> It is not supposed to be a BASH. It is supposed to be a new shell, made for easiness and clarity. So then a beginner might learn it in a day, and an expert might use it for power usage.
What do you think?
(Note: I did make it in about 2-5 minutes, so it is a quite dirty shell script)

It's just a simple Bash shell script. It literally only does two things. It sets the PATH to look in the current working directory then it passes commands to the shell.

No power-user would use this and a beginner would be mystified by this.

---

### Post by Admiral Yi on 2010-07-06
> It is not supposed to be a BASH. It is supposed to be a new shell, made for easiness and clarity. So then a beginner might learn it in a day, and an expert might use it for power usage.
What do you think?
(Note: I did make it in about 2-5 minutes, so it is a quite dirty shell script)

How can you have a new shell that relies on an old one to work? That makes no sense to start with!

And as has already been said, this isn't a shell. Its a couple of bash commands.

---

### Post by geirha on 2010-07-06
And it has alot less features. For instance, you can't redirect output to a file, or use pipes, or handle filenames containing spaces.

---

### Post by lkjoel on 2010-07-06
I'm talking about a long term shell.
I agree with all of you that this is NOT a shell.
But I want to try to create a shell with a shell script.
Yes, I agree that it sounds quite weird, and impossible, but I have been able to make a non-OOP language into OOP.

And I am not the sort of person who starts a project, then leaves it unfinished.

---

### Post by Tony Flury on 2010-07-06
I think the challenge here is that a project called "Terminal Enhancements" - which everyone might expect to add more features to an existing application (i.e. the terminal), actually does exactly the opposite, and removes key features (namely redirections and pipes).

Even if this is a template (which I take to mean an alpha version), I would have expected it to at least enhance something on the terminal - which it does not - and leave the rest working as expected - which it does not.

> 
It is not supposed to be a BASH. 

But the point is - it is bash - it accepts exactly the same commands (but removes a lot of useful features, and introduces a major security concern).
> 
It is supposed to be a new shell, made for easiness and clarity.

in what way is it easier to use this "shell" rather than a straight bash terminal - what features does it introduce to make it easier - I can see none.
> 
So then a beginner might learn it in a day, 

A beginner can learn the key bash commands in a day (ls, more, cp, mv, rm etc). your "shell" does nothing to make that  any easier - and actually prevents a lot of beginner stuff from working (like piping the results of one command into 'more' so you can sift through the output - Pipes and simple redirects are day 1 stuff on any structured course).
I can see nothing that would make this easier for windows users to use (note that many of the windows commands are different anyway (copy, del - i think) so they still have to learn the new commands, directory structures etc and also Windows supports pipes and redirections too - which your "shell" disables.
> 
and an expert might use it for power usage.

Given all the features that your "shell" disables i doubt any power user will use it ever - I am not a power user but I will stick with straight bash, rather than installing your terminal downgrade. Provide me something that actually enhances the terminal and I might be interested.

---

### Post by lkjoel on 2010-07-06
> **Tony Flury said:**
> I think the challenge here is that a project called "Terminal Enhancements" - which everyone might expect to add more features to an existing application (i.e. the terminal), actually does exactly the opposite, and removes key features (namely redirections and pipes).

Even if this is a template (which I take to mean an alpha version), I would have expected it to at least enhance something on the terminal - which it does not - and leave the rest working as expected - which it does not.


But the point is - it is bash - it accepts exactly the same commands (but removes a lot of useful features, and introduces a major security concern).

in what way is it easier to use this "shell" rather than a straight bash terminal - what features does it introduce to make it easier - I can see none.

A beginner can learn the key bash commands in a day (ls, more, cp, mv, rm etc). your "shell" does nothing to make that  any easier - and actually prevents a lot of beginner stuff from working (like piping the results of one command into 'more' so you can sift through the output - Pipes and simple redirects are day 1 stuff on any structured course).
I can see nothing that would make this easier for windows users to use (note that many of the windows commands are different anyway (copy, del - i think) so they still have to learn the new commands, directory structures etc and also Windows supports pipes and redirections too - which your "shell" disables.

Given all the features that your "shell" disables i doubt any power user will use it ever - I am not a power user but I will stick with straight bash, rather than installing your terminal downgrade. Provide me something that actually enhances the terminal and I might be interested.
I agree completely with you. When I said that it was a shell, I meant not this version, but maybe in 1.0.
I did not mean completely a shell, but *like* a shell.
I am sorry that I did not word it correctly.
I am not expecting any public downloads of my Terminal Enhancements.
The reason I put it publicly available is so that developers can improve it.
I know it is a downgrade, but that is temporary, and if I am not able to make BASH commands work with it, I will change the name to MSPROMPT.

And one question...
Is there a /etc/profile on your computer?
I am using puppylinux currently, and I use /etc/profile instead of ~/.bashrc.

---

### Post by schauerlich on 2010-07-06
You install the command to /etc? Uy...

---

### Post by lkjoel on 2010-07-06
> **schauerlich said:**
> You install the command to /etc? Uy...
Well, it doesn't crash the system...
Though when I type:
```
bash
```
it comes up with Terminal Enhancements.
I am currently trying to make BASH commands work with Terminal Enhancements.
Terminal Enhancements is not quite descriptive *yet*.

---

### Post by schauerlich on 2010-07-06
> **lkjoel said:**
> Well, it doesn't crash the system...
Though when I type:
```
bash
```
it comes up with Terminal Enhancements.
I am currently trying to make BASH commands work with Terminal Enhancements.
Terminal Enhancements is not quite descriptive *yet*.

Just because it doesn't crash the system doesn't mean it's okay...

If anything (which I'm still not convinced there should be), you should install it somewhere like ~/.enhancements/enhancements.sh, chmod+x it *once* (not every time bash starts), and add "sh ~/.enhancements/enhancements.sh" to the end of ~/.bashrc.

---

### Post by lkjoel on 2010-07-06
> **schauerlich said:**
> Just because it doesn't crash the system doesn't mean it's okay...

If anything (which I'm still not convinced there should be), you should install it somewhere like ~/.enhancements/enhancements.sh, chmod+x it *once* (not every time bash starts), and add "sh ~/.enhancements/enhancements.sh" to the end of ~/.bashrc.
Thanks!
Well, I guess there is a new update to the install file...

---

### Post by schauerlich on 2010-07-06
also, if you want to check if someone is root, don't just ask them and blindly go ahead even if they aren't. Use /usr/bin/id, and check if it gives you 0 (root).

```
schauerlich@inara:/$ if [[ `id -u` = 0 ]]; then echo "woo"; else echo "boo";  fi
boo
schauerlich@inara:/$ sudo su
root@inara:/$ if [[ `id -u` = 0 ]]; then echo "woo"; else echo "boo";  fi
woo
root@inara:/$
```

---

### Post by lkjoel on 2010-07-06
> **schauerlich said:**
> also, if you want to check if someone is root, don't just ask them and blindly go ahead even if they aren't. Use /usr/bin/id, and check if it gives you 0 (root).

```
schauerlich@inara:/$ if [[ `id -u` = 0 ]]; then echo "woo"; else echo "boo";  fi
boo
schauerlich@inara:/$ sudo su
root@inara:/$ if [[ `id -u` = 0 ]]; then echo "woo"; else echo "boo";  fi
woo
root@inara:/$
```
Thanks! Your timing was perfect... Just before uploading the new version!

---

### Post by Vox754 on 2010-07-06
> **schauerlich said:**
> also, if you want to check if someone is root, don't just ask them and blindly go ahead even if they aren't. Use /usr/bin/id, and check if it gives you 0 (root).

```
schauerlich@inara:/$ if [[ `id -u` = 0 ]]; then echo "woo"; else echo "boo";  fi
boo
schauerlich@inara:/$ sudo su
root@inara:/$ if [[ `id -u` = 0 ]]; then echo "woo"; else echo "boo";  fi
woo
root@inara:/$
```

*Facepalm*

Don't give him any more ideas, or he'll think he is actually succeeding.

Please take a look at his other project [LinuxEssentials, DE Restarter](http://ubuntuforums.org/showthread.php?t=1513068), and realize lkjoel is beyond hope.

Please, just stop, lkjoel, please. Don't bring your ugly code to the community.

---

### Post by schauerlich on 2010-07-06
> **Vox754 said:**
> *Facepalm*

Don't give him any more ideas, or he'll think he is actually succeeding.

I know, I know... it's some sick form of voyeurism, i suppose.

---

### Post by Tony Flury on 2010-07-06
> **lkjoel said:**
> 
I did not mean completely a shell, but *like* a shell.

No it isn't - it is not like a shell - it is a shim layer on top of bash that cripples bash for anyone uses it 

> 
The reason I put it publicly available is so that developers can improve it.

What improvements do you expect - the only reasonable improvement is for you to listen to everyone who has made comments and drop this idea. Think about it logically - drop your ego and admit that it is an appalling idea.

> 
I know it is a downgrade, but that is temporary, and if I am not able to make BASH commands work with it, I will change the name to MSPROMPT.

MSPROMPT ???? You do realise that LINUX is not a windows clone ? that the terminal works differently because it is designed to, because LINUX is not windows. Your "script" does nothing to emulate the command prompt on MS Windows, and effectively cripples the bash terminal. People who are new to LINUX are better served by being helped to adopt LINUX and embrace the fact it is different to MS Windows, not by desperate attempts to make it look sort of like MS Windows - but in the process disabling all the best features of LINUX, and not providing any of the features of the MS WIndows command prompt either.

The art of a good software engineer is to recognise a good idea, and find a a way to implement it, and also to be able to recognise an awful idea - and to step away from it as soon as you can.

If you do want to implement a new type of shell that is better than bash - but which still supports all the cool stuff that people expect - do it in C or C++, support all the existing bash features pipes etc (maybe with different syntax) etc.

---

### Post by v1ad on 2010-07-06
> **xsinsx said:**
> This can simply be fixed with the !! << double shabang.

don't mean to be a prick but a shabang is !# :)

---

### Post by mobilediesel on 2010-07-06
> **Vox754 said:**
> Please take a look at his other project [LinuxEssentials, DE Restarter](http://ubuntuforums.org/showthread.php?t=1513068), and realize lkjoel is beyond hope.

I saw that thing earlier. He bumped the thread again today so people will see it. There needs to be an "un-bump" button on the Ubuntuforums.

---

### Post by Vox754 on 2010-07-06
> **v1ad said:**
> don't mean to be a prick but a shabang is !# :)

L O L

F A I L

A *shebang* is actually
```

#!

```

As it's name implies, first goes the hash (#), and then the bang (!).

This only shows that this thread was destined to be complete and utter fail. Moderators should just close it. Actually, we all should be given infractions for hijacking, or something, I don't care anymore!

---

### Post by lkjoel on 2010-09-21
Notice to all readers reading this:
All of this talk was concerning Terminal Enhancements 0.1a.
0.2 was created on the same day that the last post (the post before this one) was posted. (2010-07-06, proof: [https://launchpad.net/terminal-enhancements/0.2-stable/0.2-stable]("https://launchpad.net/terminal-enhancements/0.2-stable/0.2-stable"))
Terminal Enhancements >= 2.2.1 has all of these problems mentioned here fixed.

---

### Post by Barrucadu on 2010-09-21
Ok, so you realised your first version was completely and utterly wrong. But the second version is so trivial it is a joke. The installer is longer than the "enhancements"!

```
quit() { exit; }
PATH="$PATH:."
PATH="$PATH:./"
```

I am sure you had good and honourable intentions to help new users when you wrote that.

You consider that "0.2-stable"? Firstly, of course it's stable, there is nothing to *be* unstable! Secondly, I am truly amazed that you consider those three lines worthy of a version number.

Please tell me, what does someone gain by using your "enhancements"? Only someone with a *very* naive and incomplete knowledge of the terminal will be even *remotely* helped - and those users should be educated so they can become more familiar with it - not have their ignorance and bad habits fed.

**edit:**

Ok, I see I was a few versions behind. However, it's not improved much. You define some aliases and trivial functions. For example:

```
tefind() {
find $1 | grep $2
}
```

That could be rewritten without `grep`:

```
tefind() {
find $1 -iname $2 2>/dev/null
}
```

Or, better yet, you could just use `find`, which is more powerful.

Some of your "enhancements" are actually dangerous:

```
alias svi='sudo vim'
```

No, bad idea. Use `sudoedit` for editing files as root.

And, of course, some are completely redundant:

```
alias sha1='openssl sha1'
```

What's wrong with `sha1sum`?

---

### Post by mobilediesel on 2010-09-21
> **Barrucadu said:**
> Ok, so you realised your first version was completely and utterly wrong. But the second version is so trivial it is a joke. The installer is longer than the "enhancements"!
Ok, I see I was a few versions behind. However, it's not improved much. You define some aliases and trivial functions. For example:

Some of your "enhancements" are actually dangerous:

And, of course, some are completely redundant:

Perhaps the name "Terminal Enhancements" uses this definition of the word **terminal**:
> adj.

   5. Causing, ending in, or approaching death; fatal: terminal cancer; a terminal patient.

---

### Post by Bachstelze on 2010-09-21
> **Barrucadu said:**
> 
Some of your "enhancements" are actually dangerous:

```
alias svi='sudo vim'
```

No, bad idea. Use `sudoedit` for editing files as root.

How exactly is sudo vim "dangerous"? And yes, I know about "the user can get a root shell from vim". Not relevant here, we're talking about something aimed at people with only a handful of accounts on their systems. If a user can use sudo, he probably has root anyway.

Not saying this "enhancements" thing is good, mind, just that such blanket statements don't help.

---

### Post by lkjoel on 2010-09-22
> **Barrucadu said:**
> Ok, so you realised your first version was completely and utterly wrong. But the second version is so trivial it is a joke. The installer is longer than the "enhancements"!

```
quit() { exit; }
PATH="$PATH:."
PATH="$PATH:./"
```

I am sure you had good and honourable intentions to help new users when you wrote that.

You consider that "0.2-stable"? Firstly, of course it's stable, there is nothing to *be* unstable! Secondly, I am truly amazed that you consider those three lines worthy of a version number.

Please tell me, what does someone gain by using your "enhancements"? Only someone with a *very* naive and incomplete knowledge of the terminal will be even *remotely* helped - and those users should be educated so they can become more familiar with it - not have their ignorance and bad habits fed.

**edit:**

Ok, I see I was a few versions behind. However, it's not improved much. You define some aliases and trivial functions. For example:

```
tefind() {
find $1 | grep $2
}
```

That could be rewritten without `grep`:

```
tefind() {
find $1 -iname $2 2>/dev/null
}
```

Or, better yet, you could just use `find`, which is more powerful.

Some of your "enhancements" are actually dangerous:

```
alias svi='sudo vim'
```

No, bad idea. Use `sudoedit` for editing files as root.

And, of course, some are completely redundant:

```
alias sha1='openssl sha1'
```

What's wrong with `sha1sum`?
Thanks for the hints.
I take what websites recommend for adding to the bashrc after a clean install.
2.3.1 will have those problems fixed.

---

### Post by lkjoel on 2010-09-22
> **mobilediesel said:**
> Perhaps the name "Terminal Enhancements" uses this definition of the word **terminal**:
Can you tell me why my terminal is so much easier to use now with Terminal Enhancements?

---

### Post by mobilediesel on 2010-09-22
> **lkjoel said:**
> Can you tell me why my terminal is so much easier to use now with Terminal Enhancements?

The terminal is not easier or harder to use with Terminal "Enhancements". It doesn't do anything positive or negative.

---

### Post by lkjoel on 2010-09-22
> **mobilediesel said:**
> The terminal is not easier or harder to use with Terminal "Enhancements". It doesn't do anything positive or negative.
Well, I save about 1 KB of text to type a day with TE.

---

### Post by mobilediesel on 2010-09-22
> **lkjoel said:**
> Well, I save about 1 KB of text to type a day with TE.

[LIST=1]
[*]How does it do that for you?
[*]How do you measure that effect?
[/LIST]

---

### Post by lkjoel on 2010-09-22
> **mobilediesel said:**
> [LIST=1]
[*]How does it do that for you?
[*]How do you measure that effect?
[/LIST]
[LIST=1]
[*]Look at the source code for data.txt.
[*]I estimate. Fine, ABOUT 1KB a day.
[/LIST]

---

### Post by mobilediesel on 2010-09-22
> **lkjoel said:**
> [LIST=1]
[*]Look at the source code for data.txt.
[*]I estimate. Fine, ABOUT 1KB a day.
[/LIST]

I looked at the source code. There's nothing there to suggest saving on typing.

I'm unsubscribing from this thread.

---

### Post by wkhasintha on 2010-09-23
I'm going to try it. for what it's worth.

---

### Post by lkjoel on 2010-09-23
Please, Everyone, Give me **Constructive Criticism**.

---

