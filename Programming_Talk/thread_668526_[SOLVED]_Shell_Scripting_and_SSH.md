---
title: "[SOLVED] Shell Scripting and SSH"
date: 2008-01-15
forum: Programming Talk
---

### Post by 71fnRVVm on 2008-01-15
Hi (again) everyone,

Last time, I had a bunch of questions for automating FTP actions through Shell Scripting... now the topic is SSH through Shell.

After learning how the FTP process worked, I assumed it would be similar, and created:```

ssh -l $SSHuser $conn_loc <<SSHLOGIN
pass $pass
//code and stuff
SSHLOGIN
```

But that didn't work, because it still prompts for a password (password and everything are correct... you can manually login using the same exact commands and info).  I scoured the man page, and all I could come up with was the -c attribute, but that asks for another script to be executed.   I found no way to insert a password into it, or anything.

I did find that you can do this using some sort of external library, but I'd like to avoid that as much as possible.  Is it?

Any help is appreciated

Thanks

---

### Post by stroyan on 2008-01-15
The "expect" command is more powerful for scripting interactive commands.
It uses a pty (pseudo-terminal) device so that even commands like ssh that
read from the /dev/tty device can be handled.

---

### Post by 71fnRVVm on 2008-01-15
Ok, so I installed the expect library, and followed the docs I could find, resulting in

```

spawn ssh -l $SSHuser $conn_loc <<SSHLOGIN
expect "*?assword:*"
send "$pass\r"
send "\r"
```

But that throws an error of:```

./backup_gen.sh: 26: spawn: not found
```

Even though I've included (and double checked the location):
```

#!/usr/bin/expect -f
```

I played around with it, and couldn't get it to work without labeling it as "spawn" (I get more errors and a false connection display)...

Thanks again

---

### Post by stevescripts on 2008-01-15
Kyle,

If you don't get it figured out before long, you may want to post your
expect problem on comp.lang.tcl ... the Expect author, and other
experienced expect folks are often there.

Although I have been an avid (rabid?)  user of tcl and tk these last
10+ years or so, I have never tinkered with expect.

Hope this is helpful.

Steve

---

### Post by stroyan on 2008-01-15
It looks like you are mixing shell and expect commands badly.
The 'spawn' command is an expect command.
But the << 'here document' is a shell feature.
You have them both in the same line.
The 'spawn: not found' message would indicate that bash parsed that line.
You say you included '#!/usr/bin/expect -f' and  double checked the location.
But you didn't tell us where you located it.
You can either start a file with '#!/usr/bin/expect -f' and use only expect commands, or you can start a file with "#!/bin/bash" and start expect from a shell script.
Here is an example using a shell 'here document' to feed commands to expect.
```
#!/bin/bash
/usr/bin/expect << SSHLOGIN
spawn ssh $SSHuser@$conn_loc
expect {
    Password: {
        send $pass\n"
    }
}
expect {
    "# " {
        send "exit\n"
    }
}
wait
SSHLOGIN

```

---

### Post by 71fnRVVm on 2008-01-15
I don't think I mentioned it, but in my other post about FTP and Shell, I mentioned that I have alot of programming experience, but this is the first time I'm trying to do something with Shell and other shell-based utilities.  So if I'm mixing things "badly", that's a pretty acceptable reason why.

Anyways, I took your example, and modified it a little... it actually logged me in.  Here's what I have:```

/usr/bin/expect << SSHLOGIN
spawn ssh -l $SSHuser $conn_loc 
expect {
	Password: {
		send "$pass\n"
	}
}
expect {
	"# " {
		send "cd /home/16053/\n"
		send "cp -r ./data/* /backups/data/\n"
		send "cp -r ./domains/* /backups/domains/\n"
		send "cp -r ./etc/* /backups/etc/\n"
		send "cp -r ./logs/* /backups/logs/\n"
		send "cd /home/16053/backups/\n"
		send "tar -cvvf ./$today.tar ./data/\n"
		send "tar -vvfr ./$today.tar ./domains/\n"
		send "tar -vvfr ./$today.tar ./etc/\n"
		send "tar -vvfr ./$today.tar ./logs/\n"	
	}
}
SSHLOGIN
```

But two questions:

1)  When you do ```
 expect { "# " { } }
``` I'm assuming that means empty command line?  So I replaced "exit" with the commands I want to run, and it pretends to do stuff, but doesn't actually do anything.  No error messages. 

2)  Is there a way to remove output to the command line (like how it shows "Password:" and then the youre-logged-in information?)

Thanks again for all the help.  I'm trying to pick this up quickly from this forum, what I can find through Google, man pages, and my personal experience with other languages and Linux.

---

### Post by geirha on 2008-01-15
You could create an ssh-key.

This creates a key-pair. (secret key: ~/.ssh/id_dsa, public key: ~/.ssh/id_dsa.pub)
```
ssh-keygen -t dsa
```
then add that key to the ssh-agent (in ubuntu, an ssh-agent will be running whenever you're logged in):
```
ssh-add
```
Then you must tell the other end that your key should be allowed to login password-less:
```
cat ~/.ssh/id_dsa.pub | ssh -l $ssh_user $host "cat >> .ssh/authorized_keys"
```
As long as the ssh-agent is running, and your key is loaded in it, you can login passwordless with ssh, to that host.

If you leave the passphrase for the key empty as well, you don't need to specify any password even to add it to the ssh-agent, but if anyone gets a hold of your secret key (~/.ssh/id_dsa), they'll also have passwordless access to that host. So keep it secret, keep it safe!

The host must have key authentication enabled of course, this is usually on by default, so chances are you'll have no problems with that.

---

### Post by Cappy on 2008-01-15
If you use the ssh key you can do
```
ssh -l USERNAME HOSTADDRESS "cd /home/16053/; cp -r ./data/* /backups/data/;"
```
for instance.

Rather than use ssh you could schedule a task to run whenever you want using "at".

---

### Post by 71fnRVVm on 2008-01-15
Right, but I'm trying to keep things localized within the one script.  And I'm not having problems logging in, but rather how I execute commands *within* the SSH connection once it's open?

---

### Post by stroyan on 2008-01-15
The expect with "#" is the shell prompt.  That will vary with the details of the account and its prompt setting.
You need to have more expect statements.
With your current script the many send statements will complete immediately and the expect command will kill ssh before the shell executes those commands.
You usually do one send and then one expect for the next prompt.
You could use one send with many shell commands separated by semicolons.
As an alternative you could match a final completion message like```
send "echo done\n"
expect { "done" {exit} }
```

---

### Post by ghostdog74 on 2008-01-16
> **71fnRVVm said:**
> Hi (again) everyone,

Last time, I had a bunch of questions for automating FTP actions through Shell Scripting... now the topic is SSH through Shell.

After learning how the FTP process worked, I assumed it would be similar, and created:```

ssh -l $SSHuser $conn_loc <<SSHLOGIN
pass $pass
//code and stuff
SSHLOGIN
```

But that didn't work, because it still prompts for a password (password and everything are correct... you can manually login using the same exact commands and info).  I scoured the man page, and all I could come up with was the -c attribute, but that asks for another script to be executed.   I found no way to insert a password into it, or anything.

I did find that you can do this using some sort of external library, but I'd like to avoid that as much as possible.  Is it?

Any help is appreciated

Thanks

if you want to use ssh, then set it up using passwordless authentication. use the ssh-keygen method is more advisable. However if you still want to go ahead, there are other methods, such as Perl's Net::SSH , or PHP's PECL/ssh2 library or Python's Paramiko modules you can experiment with..

---

### Post by 71fnRVVm on 2008-01-17
I figured it out... I needed to expect "$ ".

Thanks!

---

