---
title: "bash script password question"
date: 2007-09-15
forum: Programming Talk
---

### Post by aoalneowlknsadflkafgibj on 2007-09-15
Ive done quite a bit of programming but have never written any scripts. I want to automatically connect using ssh and then run some commands. I need to be to automatically enter my password for the computer im connecting to. ive tried making a keygen like [this]("http://www.ece.uci.edu/~chou/ssh-key.html") site explains. but i dont have the rights to their authorized_keys file. is there a way i can just make the script loop until the terminal prompts for an input and then just have the password sent to the terminal?

---

### Post by rivalarrival on 2007-09-15
Don't reinvent the wheel :)

[http://bash.cyberciti.biz/security/sshlogin.exp.php](http://bash.cyberciti.biz/security/sshlogin.exp.php)

---

### Post by dwhitney67 on 2007-09-15
Actually, there must be a better way.

With the link you provide with the 'expect' script, it seems to me that anyone doing a process-status could examine the password being supplied to the script.  Not a very good idea if you ask me.  Further, with 'history' enabled, the command (along with the password) would also be saved for someone to peruse at a later time.

If a "wrapper" script is used to call the 'expect' script, then once again, the password has to be coded into that "wrapper" script.  Once again, a very bad idea.

To the OP - Either use the 'keygen' to create the necessary SSH public keys for your system and that of the remote server, or just rely on 'ssh' prompting the operator as the need arises.

I get the impression that you are attempting to write a script that "many" people can use.  Otherwise, if it were just yourself that was going to be using it, then there is no reason why you shouldn't be able to use the 'keygen' approach.

---

### Post by ghostdog74 on 2007-09-15
> **aoalneowlknsadflkafgibj said:**
> I need to be to automatically enter my password for the computer im connecting to. ive tried making a keygen like [this]("http://www.ece.uci.edu/~chou/ssh-key.html") site explains. but i dont have the rights to their authorized_keys file. 

If its for legitimate use, set it up with the administrator in charge. If you are the administrator, why don't you have right? Since you are using ssh, there's no reason to use password based authentication anymore..(although you still can).

---

### Post by robert_pectol on 2007-09-15
> **aoalneowlknsadflkafgibj said:**
> ...but i dont have the rights to their authorized_keys file... 
How come you do not have access to your own authorized_keys file on the remote server?  It should be in your user's home directory and owned by your user.  If you have a valid and functional shell account on the server, you should have no trouble accessing that file.  It's typically located in ~/.ssh/ (just in case you were looking in the wrong place).

---

### Post by aoalneowlknsadflkafgibj on 2007-09-17
the remote computer is a computer in a lab at my university. I have not asked them about it because i am pretty sure they would not give me the access or whatever it is i need to set this up.

---

### Post by dwhitney67 on 2007-09-17
What robert_pector was inquiring is how come you can access the lab computer remotely using SSH, but can't setup the shared public keys on your system and the lab's computer???

You do not require admin privileges to do that.  Here's how you do it... and let's start from a clean slate:

[FONT="Courier New"]
$ cd ~/.ssh
$ rm -f id_rsa id_rsa.pub known_hosts
$ ssh-keygen -C user@myhost[/FONT] 

where 'user' is your user-id and 'myhost' is the hostname of your system (not the lab's); hopefully your hostname is something other than "localhost".  Press <enter> at each question until 'ssh-keygen' finishes.

Then display the contents of the public-key file:

[FONT="Courier New"]$ cat id_rsa.pub[/FONT]

Highlight the entire "ssh-rsa" entry (it may appear as multiple lines but in actuality it is only one).  Then select Edit -> Copy.

Next SSH into your lab's computer using the account given to you.  Then:
[FONT="Courier New"]
$ cd ~/.ssh
$ vi authorized_keys[/FONT]

Paste in the "ssh-rsa" key you copied earlier.  Then save the file.

Log out, and then re-attempt the SSH.  If all goes well, you should *not* be prompted for a password.

P.S. If you are unfamiliar with "vi", the only thing you need to know after opening the file is this:

[LIST=1]
[*]press 'i' to enter insert mode
[*]select Edit -> Paste (or shift-ctrl-v) to paste your text
[*]press 'Esc' to get out of insert mode
[*]enter ":" followed by "wq" to save and exit the file
[/LIST]

---

### Post by aoalneowlknsadflkafgibj on 2007-09-17
> **dwhitney67 said:**
> What robert_pector was inquiring is how come you can access the lab computer remotely using SSH, but can't setup the shared public keys on your system and the lab's computer???

You do not require admin privileges to do that.  Here's how you do it... and let's start from a clean slate:

[FONT="Courier New"]
$ cd ~/.ssh
$ rm -f id_rsa id_rsa.pub known_hosts
$ ssh-keygen -C user@myhost[/FONT] 

where 'user' is your user-id and 'myhost' is the hostname of your system (not the lab's); hopefully your hostname is something other than "localhost".  Press <enter> at each question until 'ssh-keygen' finishes.

Then display the contents of the public-key file:

[FONT="Courier New"]$ cat id_rsa.pub[/FONT]

Highlight the entire "ssh-rsa" entry (it may appear as multiple lines but in actuality it is only one).  Then select Edit -> Copy.

Next SSH into your lab's computer using the account given to you.  Then:
[FONT="Courier New"]
$ cd ~/.ssh
$ vi authorized_keys[/FONT]

Paste in the "ssh-rsa" key you copied earlier.  Then save the file.

Log out, and then re-attempt the SSH.  If all goes well, you should *not* be prompted for a password.

P.S. If you are unfamiliar with "vi", the only thing you need to know after opening the file is this:

[LIST=1]
[*]press 'i' to enter insert mode
[*]select Edit -> Paste (or shift-ctrl-v) to paste your text
[*]press 'Esc' to get out of insert mode
[*]enter ":" followed by "wq" to save and exit the file
[/LIST]

I am trying this but now im getting 

> 138 lab2-12:~> cd ~/.ssh
/home/mmaddex/.ssh: No such file or directory.
139 lab2-12:~> 


if it makes a different i emailed the admin and they said they dont allow the use of pub/private keys. I assume thats what were still trying to set up.

---

### Post by dwhitney67 on 2007-09-17
If "/home/mmaddex" is your home directory on the lab's computer, then create the .ssh directory:

[FONT="Courier New"]$ mkdir ~/.ssh[/FONT]

---

### Post by aoalneowlknsadflkafgibj on 2007-10-01
> **dwhitney67 said:**
> What robert_pector was inquiring is how come you can access the lab computer remotely using SSH, but can't setup the shared public keys on your system and the lab's computer???

You do not require admin privileges to do that.  Here's how you do it... and let's start from a clean slate:

[FONT="Courier New"]
$ cd ~/.ssh
$ rm -f id_rsa id_rsa.pub known_hosts
$ ssh-keygen -C user@myhost[/FONT] 

where 'user' is your user-id and 'myhost' is the hostname of your system (not the lab's); hopefully your hostname is something other than "localhost".  Press <enter> at each question until 'ssh-keygen' finishes.

Then display the contents of the public-key file:

[FONT="Courier New"]$ cat id_rsa.pub[/FONT]

Highlight the entire "ssh-rsa" entry (it may appear as multiple lines but in actuality it is only one).  Then select Edit -> Copy.

Next SSH into your lab's computer using the account given to you.  Then:
[FONT="Courier New"]
$ cd ~/.ssh
$ vi authorized_keys[/FONT]

Paste in the "ssh-rsa" key you copied earlier.  Then save the file.

Log out, and then re-attempt the SSH.  If all goes well, you should *not* be prompted for a password.

P.S. If you are unfamiliar with "vi", the only thing you need to know after opening the file is this:

[LIST=1]
[*]press 'i' to enter insert mode
[*]select Edit -> Paste (or shift-ctrl-v) to paste your text
[*]press 'Esc' to get out of insert mode
[*]enter ":" followed by "wq" to save and exit the file
[/LIST]

Ok sweet this did solve it for me. Another simple question. My script logs me in automatically but it does not wait to start entering commands, how can I have my script wait for me to be logged into the ssh to start commands.

---

### Post by mssever on 2007-10-01
> **aoalneowlknsadflkafgibj said:**
> Ok sweet this did solve it for me. Another simple question. My script logs me in automatically but it does not wait to start entering commands, how can I have my script wait for me to be logged into the ssh to start commands.

It should wait. Show your code so we can see what's happening.

---

### Post by dwhitney67 on 2007-10-01
I cannot provide full comments on what you are attempting to accomplish without at least seeing a code snippet.  But if I understand you correctly, you have written a script similar to the following:
```
...
ssh user@remoteHost
# Begin running sh commands on remote host
...
```
Well, that's not going to work.  The 'ssh' command spawns a  new shell, and that shell will block until it is exited.  Any commands listed after the 'ssh' command will be executed within the local shell, on your local system.

Now something like this will work:
```
ssh user@remoteHost "cmd1; cmd2; etc."
```
The double quotes aren't necessary if you are running just one command.

If you still require additional assistance, let me know.

---

### Post by aoalneowlknsadflkafgibj on 2007-10-01
yeah sorry i should know better this is the entire script. 

```
#!/bin/bash
sftp myname@remotecomputer.edu
put /home/matux/PRINTER/* /home/mmaddex/PRINTER
exit
ssh myname@remotecomputer.edu
lpr /home/mmaddex/PRINTER/*
rm /home/mmaddex/PRINTER/*
exit
rm /home/matux/PRINTER/*
```

---

### Post by dwhitney67 on 2007-10-01
See my previous post concerning running commands on the remote host once you are connected via SSH.

---

### Post by mssever on 2007-10-01
> **aoalneowlknsadflkafgibj said:**
> ```
#!/bin/bash
sftp myname@remotecomputer.edu
put /home/matux/PRINTER/* /home/mmaddex/PRINTER
exit
ssh myname@remotecomputer.edu
lpr /home/mmaddex/PRINTER/*
rm /home/mmaddex/PRINTER/*
exit
rm /home/matux/PRINTER/*
```

You should use scp to copy files to a remote machine. As dwhitney said, you have to list the commands on your ssh line. One possible way to simplify this would be to put a script on the remote machine that runs the remote commands, then have the local machine call that script. It might look something like this:
```
#!/bin/bash
scp /your/local/file user@host:remote/file
ssh user@host remote_script
```

---

### Post by aoalneowlknsadflkafgibj on 2007-10-01
Thank you everybody. ive got my first BASH script under my belt now I can at last really enjoy linux. one last newbie question: what do i do to be able to type this command and have it execute?

---

### Post by mssever on 2007-10-01
> **aoalneowlknsadflkafgibj said:**
> Thank you everybody. ive got my first BASH script under my belt now I can at last really enjoy linux. one last newbie question: what do i do to be able to type this command and have it execute?

Make it executable: ```
chmod +x filename
```

---

### Post by dwhitney67 on 2007-10-01
Probably better would be:

[FONT="Courier New"]chmod u+x script[/FONT]

or

[FONT="Courier New"]chmod 744 script[/FONT]

You really only want yourself to be able to execute the script, not "everyone" on your system.

---

### Post by aoalneowlknsadflkafgibj on 2007-10-02
isnt there some special folder i put it in or a file I add it to so i can type the script name no matter what directory im in and have it run/

---

### Post by dwhitney67 on 2007-10-02
You have many choices as to where to put your script.  You can place it in your home directory, in a directory called "scripts" that is within your home directory, or some system directory (e.g. /usr/bin).

Whatever you decide upon, to ensure that you can run the script from "anywhere" is easy.  All you have to do is augment, if not already done, your PATH environment variable to include the path where the script lives.

The PATH environment variable can be adjusted in your ~/.bashrc file, with something similar to the following:

[FONT="Courier New"]export PATH=/path/to/your/script:$PATH[/FONT]

Some favor putting the path at the end of PATH, as opposed to the beginning as shown above.  So alternatively, this would also work (under certain conditions -- see note below):

[FONT="Courier New"]export PATH=$PATH:/path/to/your/script[/FONT]

When deciding where to specify your path within the PATH variable depends upon whether you want to reference your script in lieu of a similarly named system script (or program).  For instance, if you decide to name your script (or application) with a name like "test", then this name will be similar to /usr/bin/test.  If /usr/bin is specified first in the PATH environment variable, then the "test" program within that directory will be referenced before a local version of such.

Anyhow, I hope this info helps.

---

### Post by slavik on 2007-10-02
umm, there was a scripting thing that did something similar ...
you could do something like:

ssh [email]blah@glah.com[/email]
expect 'Password:'
send "password"

I forget the name though but it was like shell scripting with the script handling interaction ... I had a friend that used it for rsyncing bunch of servers (nodes in a cluster)

---

### Post by rnls001 on 2008-01-20
Hi Experts,

The information provided here is really helpful but it does not serve my requirements.

I have more than 200 machines in my network running linux and I want to be able to ssh to each one of them using thier IP address stored in a file and then run some commands inside each machine, log out and log in the next machine in the list and do the same, so on ...

Now, using key-gen is not practical for me and I do not want to install the "expect" utility due to some reason.

Please tell me if there is any way to supply ssh password using bash scripting? I know supplying the password in script might not be very secure, but still I want to do it this way. I shall be greatful to any help.

Regards, R.

---

### Post by geirha on 2008-01-20
ssh is meant to be secure, so it doesn't have any options for such insecure authentication. That's why you'll need some other program like expect to "trick" it. 

How about host-based authentication? [http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Host-Based_Authentication.html](http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Host-Based_Authentication.html)

That and public-key authentication is generally what is used for these kinds of tasks.

---

### Post by mssever on 2008-01-22
Bear in mind that host-based authentication is inherently insecure, since it can be easily spoofed. You should only use it if you understand the security ramifications and they aren't a problem for you.

---

