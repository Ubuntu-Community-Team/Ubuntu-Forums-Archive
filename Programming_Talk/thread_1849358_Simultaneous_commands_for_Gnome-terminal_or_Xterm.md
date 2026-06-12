---
title: "Simultaneous commands for Gnome-terminal or Xterm"
date: 2011-09-24
forum: Programming Talk
---

### Post by whisperity on 2011-09-24
Dear Community!

I ask your help to give me advice how to do the following:

I have a process which dumps data on an UDP port for me. Obviously, I am watching and getting the dump with *nc -u -l 1234*.

I have a bash script which sends data to this application, but this makes me having to keep open two terminal windows or tabs (one for receiving and one for sending).

I would like to get help on how to do the inclusion of these two scripts into one. So while I am listening for the incoming data, I can type (and send) commands with the other script.

I prefer using bash, as both of my scripts are in bash at the moment, but any other language is alright with me too. Before you ask, I cannot change the process which dumps the data, so I have to get this done on my end.

Best regards,
Whisperity.

---

### Post by Smart Viking on 2011-09-24
Does this work?

```
./listenscript.sh & ./otherscript.sh
```

---

### Post by ajgreeny on 2011-09-24
Just a quick explanation of Smart Viking's post:-

An ampersand & between two separate commands will run them simultaneously;
if you use two && the first command will run and when finished the second will start If the first command has not worked, you will see the error message from that and the second command will not run.

---

### Post by whisperity on 2011-09-24
> **Smart Viking said:**
> Does this work?

```
./listenscript.sh & ./otherscript.sh
```

Well, not really. I forgot to say that the second command (the sender one) accepts (and requires) parameters.

--------------------------------------------------

Until I figure it out, I want to ask another question. I have a script like this:
```
./srv_send start 1234 #sends command to start dump
nc -u -l 1234 # this is the listening process
./srv_send stop 1234 # sends command to stop dump
```

The problem is, *nc* never exits. I only want it to exit by hand, but Ctrl-C terminates the whole script. But running the stop command after NC is closed is vital.

---

### Post by gardnan on 2011-09-25
> The problem is, *nc* never exits. I only want it to exit by hand,  but Ctrl-C terminates the whole script. But running the stop command  after NC is closed is vital.     This is because of the way that bash handles SIGINTs during scripts. When a SIGINT is sent, it is sent to the foreground process and all child processes. This results in a bit of a dilemma, because some programs use SIGINTs during normal operation. 

If bash exits itself and all child processes, that would not allow those programs to use SIGINTs for their overridden purposes within shell scripts, but if bash waited for the program to end, and then exited, the execution of the script would depend on if the user sent a SIGINT to the program within the script, and this would lead to unpredictable behavior. 

To solve this, bash makes note if their is a SIGINT while a child process is executing, and then if the child process exits with a SIGINT status, then bash exits, while if the process terminates on normal status, bash continues.

In this case, when you want to stop the program nc and you send a SIGINT, nc exits a SIGINT status, and bash stops continuation of the script. The only way I know of to work around this is to use SIGQUIT (Control-4 or Control-\ on my machine), which is supposed to exit the current program and make a core dump, but I have never observed this. However, you should know that I don't know too much about SIQQUIT, so there may be some gotcha I don't know about.

---

