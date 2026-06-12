---
title: "bash password"
date: 2011-09-09
forum: Programming Talk
---

### Post by Drenriza on 2011-09-09
Hi all.

Im creating a script to mount a samba share, when the computer starts.
And ive added the commands to connect to the share, but at some point it asks for Password?.

And my question is. How do i in my bash script, pass my password to the CLI?
And send a "enter" command?

Hope it makes sense.
Kind regards.

---

### Post by 2F4U on 2011-09-09
Not sure if this helps, but I created a bash script to mount a Samba share which contains the following command

```
mount -t cifs -o credentials=~/.smbcredentials,uid=1000,gid=1000,file_mode=0660,
dir_mode=0770 //your_server/your_directory /your_local_directory

```

The credentials file is a simple text file that contains the following information

username = someuser
password = somepass

While I haven't tried mounting the samba share at boot time, the script works well when executed in a terminal.

---

### Post by Drenriza on 2011-09-09
Uhmm,

isint their a way to feed a static password, defined inside the script
password="somePassword" and then feed the CLI this when it asks "Password?"?

It seams simple enough :p but cant find anything anywhere.

---

### Post by Bachstelze on 2011-09-09
Why not just add it to your fstab?

---

### Post by tommpogg on 2011-09-09
> **Drenriza said:**
> 

Im creating a script to mount a samba share, when the computer starts.


Just curiosity: why don't you modify fstab instead of creating a script?

Anyway +1 to the credentials for setting user and password.
Correct me if I'm wrong, I think it should be better to protect the credentials file by setting root as owner.

PS: sorry I've just noticed that[]("http://ubuntuforums.org/member.php?u=51114") Bachstelze has been faster than me

---

### Post by Drenriza on 2011-09-09
> **Bachstelze said:**
> Why not just add it to your fstab?

Im on a Mac OS X machine. And the fstab is to weird for me to want and edit.

---

### Post by Drenriza on 2011-09-09
Is it really so difficult in bash to just read in a static value when it prompts for a password?

Or possible to do so with awk inside of bash???

---

### Post by PaulM1985 on 2011-09-09
Do you want the user to be able to type the password in to an interface and have the interface pass this password on?  If so, you can use "gksudo" instead of "sudo".

This displays the password dialog to the user so that they can enter their password.

Paul

---

### Post by karlson on 2011-09-09
> **Drenriza said:**
> Hi all.

Im creating a script to mount a samba share, when the computer starts.
And ive added the commands to connect to the share, but at some point it asks for Password?.

And my question is. How do i in my bash script, pass my password to the CLI?
And send a "enter" command?

Hope it makes sense.
Kind regards.

Have you tried expect?

---

### Post by karlson on 2011-09-09
> **Drenriza said:**
> Im on a Mac OS X machine. And the fstab is to weird for me to want and edit.

Now it doesn't make sense.  What's different about MacOS X /etc/fstab from other BSD versions?

Secondly if you are on MacOS why not use the tools it has natively through the GUI to map a samba share?

I mean I understand the need to be all Unix-like but IMO that's not why you get a Mac...

---

### Post by Drenriza on 2011-09-09
> **karlson said:**
> Now it doesn't make sense.  What's different about MacOS X /etc/fstab from other BSD versions?

Secondly if you are on MacOS why not use the tools it has natively through the GUI to map a samba share?

I mean I understand the need to be all Unix-like but IMO that's not why you get a Mac...

I got a mac because my boss forced me to :(.
And i dont use the gui, since it cannot map the share automatically. Its a manuel process.
All that i want, is that.

When bash detects the word Password: it automaticallys read in a static password defined in the script, and execute the return key function. And maybe i need to use expect scripting for this.

---

### Post by WitchCraft on 2011-09-10
> **Drenriza said:**
> 
And maybe i need to use expect scripting for this.


Yes, you do need expect.
I had similar troubles with sshfs.
I changed from bash to Python, using pexpect, and suddenly, the sshfs didn't unmount immediately after mounting anymore...

See here
[http://ubuntuforums.org/showthread.php?t=1198432](http://ubuntuforums.org/showthread.php?t=1198432)

---

### Post by Drenriza on 2011-09-12
In my #!/bin/bash script how can i, use expect script inside that.
So when my script executes 
```
mount -t smbfs //$username@samba/path /Users/$directory/local/path
```
it should expect a Password? <-- text returned to the user.
Send Password.
Send return key press.
And close the expect side of the script.

---

### Post by Drenriza on 2011-09-14
Anyone?

---

