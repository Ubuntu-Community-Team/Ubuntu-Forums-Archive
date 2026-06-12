---
title: "auto run"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by nutpants on 2008-05-14
there are a few things i would like to auto magically run at system startup
like firestarter

and a few things i want to run at user login.
like freepopd

and one or two things i want to run before a program starts up.
run this then run that. like sync-engine then msynctool

but sync-engine holds the command and will not run msynctool as the next command.

nutz

---

### Post by Cypher on 2008-05-14
> **nutpants said:**
> there are a few things i would like to auto magically run at system startup
like firestarter

You can create (if not already there) a script in the /etc/init.d directory and link it to the RC5.D directory to have firestarter start up on each boot
> 
and a few things i want to run at user login.
like freepopd

In Preferences->Sessions, you can choose to start this when you login to the desktop

I'm uncertain about the rest..

---

### Post by kansasnoob on 2008-05-14
Well, you'd have to edit sudoers in order to eliminate using your password to start the specific programs. It can be very fiddly, and regarding Firestarter, I've done it in the past but I now choose not to. Iptables does still run perfectly in 8.04 with no changes.

If you need to make changes you can install Firestarter if you prefer a GUI or you can use ufw (installed by default but not enabled) if you prefer CLI.

I'll NOT tell you how to edit sudoers because IMHO doing so is kind of like hiding the key to your front door under the door mat or one of those stupid plastic rocks. In one tutorial I read they compared such a move to the Seinfeld episode where Kramer left Seinfeld's front door wide open.

The best lock in the world is worthless if you leave the door wide open.

Now, you can create an applet for nearly any program frequently used simply by going to synaptic and installing "alltray" which will let you drag-n-drop applets to either panel.

---

### Post by mkoehler on 2008-05-14
Here's the simple answer to what you are asking:

-Use "Sessions" as Cypher said to run a program on startup (you have to make sure that the file is in your $PATH)

-I believe you are saying that when you type 'sync-engine' into the terminal, it doesn't give you another prompt.  That is because it needs to keep the process running.  In this case, put an ampersand (&) after the command, which runs the command as a process and then returns you to the prompt.  Therefore, run the commands like this:

```
sync-engine&
```
then
```
msynctool
```

---

