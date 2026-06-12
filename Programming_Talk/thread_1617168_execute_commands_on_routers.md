---
title: "execute commands on routers"
date: 2010-11-09
forum: Programming Talk
---

### Post by ghaida on 2010-11-09
Hello 
i want to ask a Qs about implementing a php script .
one of my clients asked me to do a simple controller script !
he had 3 servers and one router and these servers connected to the router 
and just what he wants is a ssh client script with API written in php that enables him to interact with the router to do just one thing 
[COLOR=Red]"power off" one of the servers 
[COLOR=Black]i've tried using ssh2 php functions and a library called "phpseclib" the connection process goes fine but they all stuck with the execution process .

i did a search about this infos but i donn know where i should go.
i don't know much more about networks .

could someone help me on this plz
at least i want to know how does this work .
i know how to do this using a terminal , but can i access routers and execute a command using php ?
should i [/COLOR][/COLOR]deal with router same as server or computer ?[COLOR=Red][COLOR=Black]


thanks in advance 
[/COLOR][/COLOR]

---

### Post by Zugzwang on 2010-11-10
Ok, so nobody replied so far. I'll try to explain why: You post is named "execute commands on routers", but in the body you say that you want to shut down a server connected to the router. In order to do so, you normally do not have to do anything on the router - and this confuses people here.

Probably you might want to consider the following way of solving the problem: Write a short deamon script that runs on the servers and is started at boot time with root rights. Make a very basic TCP server out of it that accepts some shutdown command, possibly secured by password or the like. As the deamon runs with root rights, it can shutdown the server. In the PHP script, you can then connect to this server to issue the shutdown command.

---

