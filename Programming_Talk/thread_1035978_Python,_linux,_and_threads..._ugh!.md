---
title: "Python, linux, and threads... ugh!"
date: 2009-01-10
forum: Programming Talk
---

### Post by NetSkay on 2009-01-10
hello guys... ive been programming a bot for a protocol in python... everything works fine, but im a bit confused... 
when i pass the bot the restart command, a method gets executed with the following code in it

```

        self.gate.write('Shutting down...')
        globalVars.sock.shutdown(2)
        globalVars.sock.close()
        globalVars.sock==None
        globalVars.run=False
        #os.system("kill -9 %s" %(globalVars.pid))
        self.gate.write('Restarting...')
        if globalVars.osver=='nt':
            os.system('%s/dAmn.py'%(os.getcwd()))
        else:
            os.system('python %s/dAmn.py'%(os.getcwd()))
            os.system("kill %s" % (globalVars.pid))
        raise SystemExit()

```

what happenes it, i close the socket abruptly without any server disconnect handshake, then i start the bot as another process and kill the previous one... 
however whan i run ps aux in the console i get 

netskay  25805  0.1  4.5  16088  5692 pts/1    Sl   13:02   0:00 python dAmn.py
netskay  25807  0.0  0.3   1772   488 pts/1    S    13:02   0:00 sh -c python /home/netskay/cronus/dAmn.py
netskay  25808  0.1  4.3  15832  5424 pts/1    Sl   13:02   0:00 python /home/netskay/cronus/dAmn.py

so even though i killed the process... i still have this funkiness... any idea how to properly stop a process and restart it?

---

### Post by snova on 2009-01-10
os.system doesn't return until the process ends.

Also, what's the point of using 'kill' on the process if you exit anyway?

By the way, I'm curious... what kind of bot? (If you want to tell me)

I would suggest:

[LIST=1]
[*]Close the socket.
[*]Use the subprocess module to start the script again.
[*]exit()
[/LIST]

---

### Post by NetSkay on 2009-01-12
im working on a bot for dAmn (deviantART Messaging Network)... its near completion... ill let u know when im releasing the final version, which will be pretty soon, if time permits that is...

anyway, about the processes and stuff... i was unable to use subprocess to restart because when i start the main script and all threads are initiated, it becomes a process in the OS (duuuh!), so when i try and restart with os.system("kill %s" % (globals.pid)), im killing the thread, thats true, but by spawning another process, restarting the script from within the script, the newly started session is an instance of the parent process... therefore im unable to restart...
my solution, with the help of a guy from #Botdom, a small bash (for linux) and BAT (for win) that u starts the intial process, and enters a blocking loop, then when i raise SystemExit() i also write a null file in a sub dir named restart, after script is done, the BAT/BASH continues the loop and checks for files, and based on the files, it does w/e in this case it starts the script over...
that way no left over processes and whatnot...

i know its a cheapshot file system fix, but it works, any advanced sugestions...
im open!

---

### Post by iggykoopa on 2009-01-14
you might want to look into this [http://code.activestate.com/recipes/278731/](http://code.activestate.com/recipes/278731/) it's how to deamonize a process. It may help with making the new process no longer a child.... I believe the part where it uses os.fork is what will help. I haven't tested this for what your using it for but the code does work well for starting a daemon.

---

### Post by escapee on 2009-01-14
Are these zombie processes or still active?  See what 'top' tells you.  If they are then really you'll just need a function or method to kill the zombie processes.

---

### Post by Sprut1 on 2009-01-14
Just to mention it, os have a method kill.

```
os.kill(pid)
```

---

