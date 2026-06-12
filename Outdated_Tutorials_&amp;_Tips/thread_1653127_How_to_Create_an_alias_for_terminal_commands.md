---
title: "How to: Create an alias for terminal commands"
date: 2010-12-26
forum: Outdated Tutorials &amp; Tips
---

### Post by karthick87 on 2010-12-26
I have seen many people asking how to create an alias for terminal commands.This is a small how to: to show you how to create an alias.Ofcourse creating an alias for frequently using commands will be very helpful.

**How to create an alias?** 

We often use update and upgrade command in our system.So let me show you how to create an alias for those commands.

Syntax:
**[COLOR=Red]alias custom_command='original_command'[/COLOR]**

So for creating an alias for update and upgrade we should type the following in terminal,
```
alias update='sudo apt-get update'
``````
alias upgrade='sudo apt-get upgrade'
```Now if you want to update,you can simply type [COLOR=Red]update[/COLOR] in terminal.And it will perform the action of [COLOR=Red]sudo apt-get update [COLOR=Black]for upgrading simply type [COLOR=Red]upgrade[/COLOR].If you want to create an alias for both the commands then you should add an alias like this,
[/COLOR][/COLOR]```
alias updg='sudo apt-get update && sudo apt-get upgrade'
```Like this you can create an alias for any commands you wish.These custom commands will work until you close your terminal.So to add this permanently,you should add the commands to [COLOR=Red]~/.bashrc[/COLOR] or [COLOR=Red]~/.bash_aliases[COLOR=Black].[/COLOR][/COLOR]

**How to add these commands to [COLOR=Red]~/.bashrc[/COLOR] or [COLOR=Red]~/.[/COLOR]**[COLOR=Red]**bash_aliases** [/COLOR][B]file?
[/B]
Edit the ~/.bashrc file,and add the commands at the end file,
```
gedit ~/.bashrc
```[IMG]http://imgur.com/Tf3aO.png[/IMG]
After adding the commands you should run the following command in terminal to refresh your bashrc configuration.
```
source ~/.bashrc
```Now you have added the alias permanently..Hope this helps someone..

[B]Note: 
  [/B]If you just want to add  one or two aliases, use [COLOR=Red].bashrc[/COLOR]. If you want to add more then i recommend you to use [COLOR=Red].bash_aliases[/COLOR].It will prevent you from messing up the files.It's always a good idea to add your custom commands in [COLOR=Red].bash_aliases[COLOR=Black].Good Luck..! :)[/COLOR][/COLOR]

---

