---
title: "Question about scp"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by edszr on 2012-08-21
Hi all,

This question may not be total newbie in nature, but I'm a total newbie at trying to do something like this, so I apologize if this is the wrong place.

I need to use scp to get some files from my work machine to my home machine.  The problem is the work machine I need to access doesn't touch the outside world....it's behind another work machine that does touch the outside world.  Here's what I'm looking to do from home machine:

scp machine1 -> hop to machine2/dir_I_Need/Files_I_Need .

Is this possible?  Is there an easier way to do it?

thanks in advance for any help.

Ed

---

### Post by rburkartjo on 2012-08-21
ed why not just copy to a flash drive and then install on your home computer

---

### Post by kemtnbkr on 2012-08-21
> **edszr said:**
> Hi all,

This question may not be total newbie in nature, but I'm a total newbie at trying to do something like this, so I apologize if this is the wrong place.

I need to use scp to get some files from my work machine to my home machine.  The problem is the work machine I need to access doesn't touch the outside world....it's behind another work machine that does touch the outside world.  Here's what I'm looking to do from home machine:

scp machine1 -> hop to machine2/dir_I_Need/Files_I_Need .

Is this possible?  Is there an easier way to do it?

thanks in advance for any help.

Ed

Do you have ssh access to the internet-connected machine?  If so, you could ssh into that one, then use your ssh'd terminal on the internet-connected remote machine to copy the files from the other LAN-only machine to the internet-connected one.  From there, just transfer them with scp to your physical location.

If you don't have ssh access, however,  I don't have much for suggestions.  

Hope you could follow my convoluted explanation!  and good luck!

EDIT:  I also just thought that you may be able to use symlinks also... although I have no idea how symlinks would play with scp.   Could be worth a shot though.

I've never done anything with symlinks, though.  The other method ought to work, I have done that before (more or less :p)

---

### Post by BDNiner on 2012-08-21
> **kemtnbkr said:**
> Do you have ssh access to the internet-connected machine?  If so, you could ssh into that one, then use your ssh'd terminal on the internet-connected remote machine to copy the files from the other LAN-only machine to the internet-connected one.  From there, just transfer them with scp to your physical location.

If you don't have ssh access, however,  I don't have much for suggestions.  

Hope you could follow my convoluted explanation!  and good luck!

EDIT:  I also just thought that you may be able to use symlinks also... although I have no idea how symlinks would play with scp.   Could be worth a shot though.

I've never done anything with symlinks, though.  The other method ought to work, I have done that before (more or less :p)

I agree here as well. I would use SSH to log into machine 1 and then use SCP to copy the files from machine 2 to machine 1 and then copy the files from machine 1 to your computer. Without SSH this would be very hard to do.

---

### Post by edszr on 2012-08-22
Thanks all for your help & suggestions.

@rburkartjo - That would be an easy way to do it :)  problem is I need to be able to do this when I'm not in the office.

@kemtnbkr and @BDNiner - That's likely the route I'll end up taking.  Ideally, I'd like to have just one step instead of 2, but oh well...beggars can't be choosers!

thanks again all for your time.

Ed

---

### Post by kemtnbkr on 2012-08-22
> **edszr said:**
> Thanks all for your help & suggestions.
...beggars can't be choosers!
Ed

Indeed.  Although two steps isn't TOO terribly bad; at least they're both fairly straightforward.  ssh/scp are amazingly useful.

Hope you can get your files without issue using this method.

---

### Post by edszr on 2012-08-22
> **kemtnbkr said:**
> Indeed.  Although two steps isn't TOO terribly bad; at least they're both fairly straightforward.  ssh/scp are amazingly useful.

Hope you can get your files without issue using this method.

Thanks kem...I messed around a bit with ssh tunneling yesterday, but I spent more time on it than it was probably worth and I never got it to work right.  :)

---

### Post by Lisiano on 2012-08-22
If your home machine can be accessed from the outside, you can do this, first ssh into the "gateway" and use this
```
scp -3 work.machine:/some/file home.machine:/some/folder/
```
You will need to input the work.machine's work LAN IP (10.0.0.42 for example) and you will need to enter your home.machine's internet facing IP (4.4.4.8 for example)
The -3 argument forces SCP makes the transfers go through the local machine.

OR if your home system isn't reachable from the net, you can try using Reverse SSH. 
```
ssh -A -R 9999:localhost:22 gateway.machine 'ssh -A -R 9999:localhost:9999 work.machine scp -P 9999 /some/file localhost:/some/folder'
```
I found the last command from here
[http://davidjb.com/blog/2011/09/scp-files-back-home-using-reverse-ssh-in-1-command](http://davidjb.com/blog/2011/09/scp-files-back-home-using-reverse-ssh-in-1-command)

---

### Post by Lars Noodén on 2012-08-22
I would use SFTP for the file transfers.  It allows more flexibility in working with the files and directories.  Since the difficulty is in making the connection, you want to get as much use out of it as possible.

As far as using the one host as a stepping stone there are several ways to do it.  Looking around the net for the phrase 'jump hosts' should also get you some other examples.  Some of the examples can be a little too abstract for introductory purposes.

Using a jump host often entails using the [ProxyCommand](http://manpages.ubuntu.com/manpages/precise/en/man5/ssh_config.5.html) directive.  Here is one example that I think should work for you using SFTP:

```

sftp  -o 'ProxyCommand=ssh %h nc machine2.example.edu 22' \
      -o 'HostKeyAlias=machine2.example.edu' \
      edszr@machine1.example.edu

```

YMMV

[nc](http://linux.die.net/man/1/nc) is the utility netcat which gets run on the jump host and is used to forward the connection via machine 1 to machine 2 behind it.

---

### Post by Lars Noodén on 2012-08-23
If you don't want to type all that in each time, then you can edit [~/.ssh/config](http://manpages.ubuntu.com/manpages/precise/en/man5/ssh_config.5.html) and put in a shortcut.

```

Host jump
  ProxyCommand ssh %h nc machine2.example.edu 22
  HostKeyAlias machine2.example.edu
  Hostname machine1.example.edu
  User  edszr 

```

Then all you have to do is type [font=Courier New]sftp jump[/font] and it will connect.

If you have different usernames on the two machines, that's doable too with modification.

---

