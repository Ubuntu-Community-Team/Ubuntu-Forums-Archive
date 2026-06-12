---
title: "[SOLVED] BASH some errors in my script..."
date: 2008-12-04
forum: Programming Talk
---

### Post by tdrusk on 2008-12-04
I don't know what I'm doing wrong. I am new to writing bash scripts. Anyone care to help?
I'm getting this error
> ./facebook: line 45: syntax error: unexpected end of file

[CODE#]!/bin/bash
#Installs fbcmd to /usr/lib/fbcmd

#Get dependencies
aptitude install php5-cli

#make new directory for installation
mkdir /usr/lib/fbcmd

#Get fbcmd
wget http://www.cs.ubc.ca/~davet/fbcmd/fbcmd-0-90.tgz /usr/lib/fbcmd

#extract
tar -xvf /usr/lib/fbcmd

#Get AUTH code
firefox http://www.facebook.com/code_gen.php?v=1.0&api_key=d96ea311638cf65f04b33c87eacf371e

#Ask for AUTH code
echo -n "What is your AUTH code?"
read ANSWER

#Enters AUTH code
php /usr/lib/fbcmd.php $ANSWER

#Asks for user name
echo - "What is your user name on this Linux computer?"
read NAME

#Check .bash_aliases existence
echo - "Do you have a .bash_aliases file in your home directory?(y/n)"
read BASH
if [["$BASH"=="n*"]]
        then touch /home/$NAME/.bash_aliases.file
if [["$BASH"=="y*"]]
        echo "yay"

#Sets "facebook" alias
echo "alias facebook='php /usr/lib/fbcmd.php'" >> /home/$NAME/.bash_aliases

#Finished
exit #
[/code]

---

### Post by albandy on 2008-12-04
In your code
You do
if ["a"=="b"]
and you should do
if [ "a" == "b" ]

---

### Post by tdrusk on 2008-12-04
> **albandy said:**
> In your code
You do
if [&quot;a&quot;==&quot;b&quot;]
and you should do
if [ &quot;a&quot; == &quot;b&quot; ]
okay. Now I'm getting a 
> ./facebook: line 43: syntax error: unexpected end of file

---

### Post by tdrusk on 2008-12-04
> **albandy said:**
> In your code
You do
if ["a"=="b"]
and you should do
if [ "a" == "b" ]
Thanks, Now I'm getting
```
./facebook: line 43: syntax error: unexpected end of file
```any ideas?

---

### Post by albandy on 2008-12-04
the if statements ends with fi

if [ "a" == "b" ]
then
a command
fi

---

### Post by tdrusk on 2008-12-10
Just started working on this again. 

There's one part
```
#Check .bash_aliases existence
echo - "Do you have a .bash_aliases file in your home directory?(y/n)" 
read BASH
if [ $BASH == "n"]
then 
    touch /home/$NAME/.bash_aliases.file
fi
```

It gives me 
```
[: 40: missing ]

```
I know it' something small. Any help is great.

---

### Post by odyniec on 2008-12-10
Add a space between "n" and ]. And change "==" to "=".

---

### Post by mssever on 2008-12-10
> **odyniec said:**
> And change "==" to "=".
Using a single = is more standard, and it's required if you're running in sh. But Bash allows either = or ==.
> **tdrusk said:**
>  ```
#Check .bash_aliases existence
echo - "Do you have a .bash_aliases file in your home directory?(y/n)" 
read BASH
if [ $BASH == "n"]
then 
    touch /home/$NAME/.bash_aliases.file
fi
```
Why are you asking the user if a file exists? The user might not know, or they might give a wrong answer. Just do a simple test: ```
if [[ -f $HOME/.bash_aliases ]]; then   # type man test for a list of other good stuff you can test for
  echo "Yay! It's there!"
else
  echo "Why don't you have it?"
fi
```Also, $NAME isn't a standard environment variable. Did you mean $USER? Or better yet, use $HOME, because home directories can be anywhere (root's is at /root, not /home/root). Use the env command to see a list of the currently-defined environment variables (some of which might not always be defined).

---

