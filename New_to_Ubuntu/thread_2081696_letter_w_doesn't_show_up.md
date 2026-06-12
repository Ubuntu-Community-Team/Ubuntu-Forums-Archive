---
title: "letter w doesn't show up"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by Moswen on 2012-11-07
When I'm in recovery mode (trying to reboot my password) the letter w (as in paswd) won't show up; a black square appears instead- command is not recognised. Is this normal and if not how can I change it?

---

### Post by dannyboy79 on 2012-11-07
may be a keyboard layout problem? 

sudo dpkg-reconfigure console-setup

and choose your keyboard, all others just hit ok to not change anything

---

### Post by Moswen on 2012-11-07
I guess that would work but can't do it since I don't know the password. And I need a proper keyboard to change the passwd. My keyboard is set to english.

---

### Post by dannyboy79 on 2012-11-07
oh, you forgot your password? here's how to reset it
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by newb85 on 2012-11-07
> **dannyboy79 said:**
> oh, you forgot your password? here's how to reset it
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

There's a hole in my bucket, dear Liza, dear Liza...
(Please read the initial post.)

---

### Post by mag1strate on 2012-11-07
> **dannyboy79 said:**
> oh, you forgot your password? here's how to reset it
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

No he can't do your initial command because he can't log into his computer without the w key.

If you are having trouble accessing some of your files or maybe changing a configuration, you can try and use a live CD.

---

### Post by jwbrase on 2012-11-07
Try using an octal escape to write the passwd command to a shell script, then run the script:

```
echo "pass\0167d" > pass.sh
chmod u+x pass.sh
pass.sh
```

---

### Post by newb85 on 2012-11-07
The echo command needs to be instructed to interpret escape characters.  That first line should be
```
echo -e "pass\0167d" > pass.sh
```

---

### Post by Wim Sturkenboom on 2012-11-07
Maybe you can drop to a root shell in recovery mode and take it from there.

---

### Post by jwbrase on 2012-11-08
> **newb85 said:**
> The echo command needs to be instructed to interpret escape characters.  That first line should be
```
echo -e "pass\0167d" > pass.sh
```

Oops. I use zsh, whose echo interprets escape characters unless instructed not to or invoked as sh, and forgot that I use a non-default shell. Sorry.

> **Wim Sturkenboom said:**
> Maybe you can drop to a root shell in recovery mode and take it from there.

Once again, read the OP: The OP is encountering this problem in recovery mode.

---

### Post by Wim Sturkenboom on 2012-11-08
> **jwbrase said:**
> Once again, read the OP: The OP is encountering this problem in recovery mode.:oops:

---

### Post by Moswen on 2012-11-08
> **jwbrase said:**
> Try using an octal escape to write the passwd command to a shell script, then run the script:

```
echo "pass\0167d" > pass.sh
chmod u+x pass.sh
pass.sh
```

I don't really understand... Can you explain it better? (I'm quite new at this and don't understand what an octal escape or shell script is :S)

---

### Post by jwbrase on 2012-11-08
> **Moswen said:**
> I don't really understand... Can you explain it better? (I'm quite new at this and don't understand what an octal escape or shell script is :S)

A shell script is a text file that contains commands to be executed, just as if you'd typed them at the terminal. The "echo" command writes whatever you pass to it to its output, so "echo hello" will print "hello" to the terminal. An octal escape is a backslash, a zero, and the number (in base 8) that the computer uses internally to represent a character. For example, "A" is 101, "a" is 141, and "w" is 167. So "echo pass\0167d" will output "passwd".

(I just realized that this line of the script should be "echo pass\0167d username > pass.sh", where username is your username, otherwise it will set the root password, which almost certainly isn't what you want).

The ">" causes the output of the command before it to be written to the file following it instead of to the terminal. So the first line I wrote there tells the computer to create a file called "pass.sh" in the current directory and write "passwd" to it (if pass.sh already exists, it will overwrite it).

The second line, "chmod u+x" tells the computer that the file should be executable for the owner of the file (whatever user created the file).

The third line tells the computer to execute "pass.sh" (which will in turn execute "passwd", since that is the one line in the file). I just realized, though, that with the default settings in Ubuntu, that line will need to be "./pass.sh", where "./" means the current directory, because Ubuntu does not by default search the current directory for executable files when you type a command name.

---

### Post by newb85 on 2012-11-08
Again, don't forget to give echo the -e option, or it won't interpret the escape.  

Also, as pass.sh isn't in one of the places bash looks for executable files, so the absolute path to the file needs to be given when calling it.

So, the commands would be
[code]echo **-e** pass\0167d *username* > pass.sh
chmod u+x pass.sh
**./**pass.sh[code]

---

