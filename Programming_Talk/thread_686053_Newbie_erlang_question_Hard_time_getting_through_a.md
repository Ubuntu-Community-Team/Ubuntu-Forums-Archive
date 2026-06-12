---
title: "Newbie erlang question: Hard time getting through a tutorial."
date: 2008-02-02
forum: Programming Talk
---

### Post by YourSurrogateGod on 2008-02-02
I'm just trying to get through this specific portion of the tutorial and trying the code that's offered here (so that I can learn.)

[http://www.erlang.org/doc/getting_started/conc_prog.html#3.5](http://www.erlang.org/doc/getting_started/conc_prog.html#3.5)

I can't seem to send messages through the sever from one client to another.

Here is what happens.

First I start the 'server':
```
$ erl -sname foo
>messenger:start_server().
true
>
```
Then I 'logon':
```
$ erl -sname bar
>messenger:logon(bob).
true
>
```

That alone tells me that something is wrong, since I'm not seeing the message 'logged_on'. Furthermore, if I simulate more clients and try to send messages from one to another, the messages are never sent.

My guess is that this is something trivial and silly, but I've tried just about everything that I could think of and haven't solved this problem. Thoughts on a possible solution?

---

### Post by PaulFr on 2008-02-03
You did change the code excerpt below to indicate the correct machine name instead of **bill** to **foo**, right?
```
%%% Change the function below to return the name of the node where the
%%% messenger server runs
server_node() ->
    messenger@bill.
```

---

### Post by YourSurrogateGod on 2008-02-10
> **PaulFr said:**
> You did change the code excerpt below to indicate the correct machine name instead of **bill** to **foo**, right?
```
%%% Change the function below to return the name of the node where the
%%% messenger server runs
server_node() ->
    messenger@bill.
```

Fairly certain.

I think that the problems is elsewhere though. When I went to [this](http://www.erlang.org/doc/getting_started/robustness.html#4.3) part and copied the code _exactly_ and started up the server and 2 clients... well, here are my results.
Server:
```
(messenger@super)16> c(messenger).
{ok,messenger}
(messenger@super)17> messenger:start_server().
true
(messenger@super)18> messenger:start_server().

=ERROR REPORT==== 10-Feb-2008::20:45:39 ===
Error in process <0.36.0> on node 'messenger@super' with exit value: {badarg,[{erlang,register,[messenger,<0.106.0>]},{messenger,start_server,0},{erl_eval,do_apply,5},{shell,exprs,6},{shell,eval_loop,3}]}

** exited: {badarg,[{erlang,register,[messenger,<0.106.0>]},
                    {messenger,start_server,0},
                    {erl_eval,do_apply,5},
                    {shell,exprs,6},
                    {shell,eval_loop,3}]} **
(messenger@super)19> messenger:start_server().

=ERROR REPORT==== 10-Feb-2008::20:45:40 ===
Error in process <0.107.0> on node 'messenger@super' with exit value: {badarg,[{erlang,register,[messenger,<0.109.0>]},{messenger,start_server,0},{erl_eval,do_apply,5},{shell,exprs,6},{shell,eval_loop,3}]}

** exited: {badarg,[{erlang,register,[messenger,<0.109.0>]},
                    {messenger,start_server,0},
                    {erl_eval,do_apply,5},
                    {shell,exprs,6},
                    {shell,eval_loop,3}]} **
(messenger@super)20>
```
Client 1:
```
(foo1@bar1)2> messenger:logon(bob).
true
No response from server
(foo1@bar1)3> messenger:logon(bob).
true
No response from server
(foo1@bar1)4> messenger:logon(bob).
true
No response from server
(foo1@bar1)5>
```
Client 2:
```
$ erl -sname foo2@bar2
Erlang (BEAM) emulator version 5.5.2 [source] [async-threads:0] [hipe] [kernel-poll:false]

Eshell V5.5.2  (abort with ^G)
(foo2@bar2)1> messenger:logon(jim).
true
No response from server 
(foo2@bar2)2> messenger:message(bob, "hello").
not_logged_on
(foo2@bar2)3> messenger:logon(jim).           
true
(foo2@bar2)4> messenger:message(bob, "hello").
ok
No response from server
(foo2@bar2)5> messenger:logon(jim).           
true
(foo2@bar2)6> messenger:message(bob, "hello").
ok
No response from server
(foo2@bar2)7> messenger:message(bob, "hello").
not_logged_on
(foo2@bar2)8>
```
I started the server up multiple times after the message failed to get across. That output is from multiple terminals on one computer (I can't network 2 or more :/ .)

---

### Post by PaulFr on 2008-02-12
Here is what worked for me:

*My machine is called ariel*.
> 1. Edited messenger.erl (in both examples) so the server_node() was myserver@ariel
2. Compiled the file using erlc.
3. In the server terminal, started the server with erl -sname myserver (prompt was myserver@ariel).
4. In the second terminal, started erl with erl -sname jim (prompt was jim@ariel).
5. In the third terminal, started erl with erl -sname bob (prompt was bob@ariel).
6. Now the steps of the example worked fine and messaging was possible. Please remember to only start the server ONCE.When I changed the name to myserver@super and started erl as erl -sname myserver@super, then both jim and bob could not login properly.

Hope this helps.

---

### Post by YourSurrogateGod on 2008-02-25
Server: Terminal 1
```
messagingProgram$ erl -sname myserver@foo
Erlang (BEAM) emulator version 5.5.2 [source] [async-threads:0] [hipe] [kernel-poll:false]

Eshell V5.5.2  (abort with ^G)
(myserver@foo)1> c(messenger).
{ok,messenger}
(myserver@foo)2> messenger:start_server().
true
(myserver@foo)3> 

```
Client jim: Terminal 2
```
messagingProgram$ erl -sname jim@foo
Erlang (BEAM) emulator version 5.5.2 [source] [async-threads:0] [hipe] [kernel-poll:false]

Eshell V5.5.2  (abort with ^G)
(jim@foo)1> messenger:logon(jim).
true
(jim@foo)2> 

```
Client bob: Terminal 3
```
messagingProgram$ erl -sname bob@foo
Erlang (BEAM) emulator version 5.5.2 [source] [async-threads:0] [hipe] [kernel-poll:false]

Eshell V5.5.2  (abort with ^G)
(bob@foo)1> messenger:logon(bob).
true
(bob@foo)2> messenger:message(jim, "hello").
ok
(bob@foo)3> 

```
The server seems to start fine and the logon appears to work, but when I try to send messages, nothing happens (as you can see when I tried to send "hello" to jim from bob.)

BTW, sorry for the late response, free-time is hard to come by for me these days.

[edit]

Here is the configuration portion of the source file.
```

...
server_node() ->
    messenger@foo.
...

```

---

### Post by YourSurrogateGod on 2008-03-15
Hmm... I've been thinking. Maybe it has something to do with the version of the Erlang compiler that I'm using?

Or it could be that I don't understand how the Erlang Virtual Machine operates. Whenever I start up the Erlang interpreter by executing erl in a command line, does that mean that I start up a completely different instance as a different process, thereby preventing it from talking to processes running under different terminals?

Or could it be that when I start up the server, if it doesn't receive a message when it first starts up it dies all of a sudden?

---

