---
title: "Bash script to execute programs without users inputting uname/pass"
date: 2011-10-18
forum: Programming Talk
---

### Post by dann_radkov on 2011-10-18
Hey Folks,
I need to create a simple bash script that will launch 3 separate commands one  after the other. I have decided to put in a sleep command between them  so that it waits for a certain amount of time(since I am not 100% sure  commands can be executed simultaneously or all at once). The output of  command1 requires some time to process.So does the output of command2  and command3.After each one the system asks for credentials.

Do you consider this appropriate :

#!/bin/bash
cd /usr/sbin
command1(which performs analysis)
*here it asks for credentials*
Then it executes the command.

sleep (say 100 just in case )

command2(performs staging)
*here it asks for credentials*

sleep 100

command3(performs install)
*here again asks for creds*



Perhaps I can implement the username/pass as a variable.
VARIABLE1=username
VARIABLE2=password

Please let me know if you have any suggestions.

---

### Post by sanderd17 on 2011-10-18
Are the commands entirely executed as root? In that case you can execute the original script as root (so it will only ask for the user credentials once).

Please give us your exact script.

---

### Post by ofnuts on 2011-10-18
> **dann_radkov said:**
> Hey Folks,
I need to create a simple bash script that will launch 3 separate commands one  after the other. I have decided to put in a sleep command between them  so that it waits for a certain amount of time(since I am not 100% sure  commands can be executed simultaneously or all at once). The output of  command1 requires some time to process.So does the output of command2  and command3.After each one the system asks for credentials.

Do you consider this appropriate :

#!/bin/bash
cd /usr/sbin
command1(which performs analysis)
*here it asks for credentials*
Then it executes the command.

sleep (say 100 just in case )

command2(performs staging)
*here it asks for credentials*

sleep 100

command3(performs install)
*here again asks for creds*



Perhaps I can implement the username/pass as a variable.
VARIABLE1=username
VARIABLE2=password

Please let me know if you have any suggestions.
1) the way you thing is written your script won't continue untill command1 is finished, so the "sleep" isn't really necessary.
2) 100 seconds for a delayed start is a lot if you only suspect contention problems. Either use a couple of seconds, or wait until the previous command is finished.
3) designing long processes that stop in the middle to request further user input before continuing (credentials or else) is the surest way to have a punctured voodoo puppet looking like you somewhere... Make sure you have everything right in the first seconds of the run, then kiss the user good night (or good coffee break) and proceed with the action.
4) there isn't much purpose asking for user credentials three times anyway? Why do you need to do so?

---

### Post by dann_radkov on 2011-10-18
Cant really give you the entire script but note that the root account is different from the credentials that the system needs to execute this script.Hence I dont think its going to work.
[@ofnuts _ These commands just require username/pass otherwise they dont proceed to download my patches._]("http://ubuntuforums.org/member.php?u=1382218")

---

### Post by thatguruguy on 2011-10-18
Actually, it would probably be best to edit your sudoers file.

Here are a couple links to get you started:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
[http://manpages.ubuntu.com/manpages/dapper/man8/visudo.8.html](http://manpages.ubuntu.com/manpages/dapper/man8/visudo.8.html)

---

### Post by sanderd17 on 2011-10-18
If there is a "sudo" in front of the command, it will ask the user to give its credentials, and sudo will execute the script as root.

If there is an &-sign after the command, then the command will be executed in a separate thread (and won't wait). If there is no &-sign, the script will wait until the command finished.

I want to know where sudo is used. If you need to execute commands with super user rights and with normal user rights, and they're in the same command, then it might be tricky.

In any way, saving the credentials is not a good idea and probably wont work.

If you can't give us the code, then you'll have to find it out yourself: [http://linuxcommand.org]("http://linuxcommand.org")

---

### Post by thatguruguy on 2011-10-18
> **dann_radkov said:**
> Cant really give you the entire script but note that the root account is different from the credentials that the system needs to execute this script.Hence I dont think its going to work.

Are there national security interests involved or something?

---

### Post by sanderd17 on 2011-10-18
> **thatguruguy said:**
> Are there national security interests involved or something?

Maybe the script contains the root pwd of the main server of the CIA :p

---

### Post by dann_radkov on 2011-10-18
#!/bin/bash
variable1=username
variable2=password

cd /usr/sbin
eds-linux-patch -a -m flash -f
#this is command1.here it prompts for uname/password (which relate to another app so its not the #root/passwd for the system)
eds-linux-patch -s
#command2.here it prompts for uname/password (which relate to another app so its not the #root/passwd for the system)
eds-linux-patch -i
#command3here it prompts for uname/password (which relate to another app so its not the #root/passwd for the system)

done

Thats the tool that I use.
Can I define the var`s directly? I mean they would still show so its not really secure to say the least.

---

### Post by emiller12345 on 2011-10-18
> **dann_radkov said:**
> 
eds-linux-patch -a -m flash -f
#this is command1.here it prompts for uname/password (which relate to another app so its not the #root/passwd for the system)


I don't have any information about the program eds-linux-patch, but I think I understand what you want.  like if your program was 'ssh' its going to ask for a username/password, and your looking to script inputing username and password.

If this is the case, then AFAIK your program needs to have cli args available to input the uname/password directly.  i.e. 'ssh $username:"$password"@1.2.3.4 ' but I may be mistaken

---

### Post by sanderd17 on 2011-10-19
You should understand that Ubuntu doesn't use a root account. It uses sudoers. That are accounts with sudo rights, so the right to become root for a short period with the own credentials. So if something asks root rights, it will ask for the users password.

If you say it also asks for the username, than it's not a sudo that is used. But probably ssh as emiller12345 said. In that case, you really can't do al lot about it.

You could start with searching and reading documentation about those scripts, and see if they provide an option to give a unsername and pwd as arguments. If you can't find the documentation, or if you can't find such an option in the documentation, than you will have to look at the internals of those commands, and try to find where it asks for your username.

---

