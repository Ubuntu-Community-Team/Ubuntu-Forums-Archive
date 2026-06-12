---
title: "Script to use SSH and SFTP or SCP"
date: 2006-03-19
forum: Programming Talk
---

### Post by rogeriovinhal on 2006-03-19
Hi, I am kind of a newbie in script programming, I have only programmed in commom languages like C, Java, etc.

I need to make 2 scripts that would make my life a lot easier. One of the is to use the SSH command twice to different machines, and then call the program PINE. That is because I have first to log in a server, and then I have to log in a commom machine in a network. That requires two commands of ssh for different machines, and the same authentication for both.

Is there a way to make a script to do that? Because every script that I try to make only calls the first SSH, and after the first authentication, it keeps waiting until I finish it.

The second script is a lot easier I guess, I have to log in the server machine as I said before, and then make a file transfer to the machine I connected. This requires 2 arguments from the command line, one for the files to send, and one for the location to put them after logging in the server.
For that I thought I could use SFTP, but for the same problem of the other program, I can't make it work. Someone told me to use SCP, but I read some manpages about SCP and it seems to do the oposite, not send, only download.

Anyone knows anything of that and could give me some directions or commands to start the scripts?

Thanks.

---

### Post by souki on 2006-03-19
> I need to make 2 scripts that would make my life a lot easier. One of the is to use the SSH command twice to different machines, and then call the program PINE. That is because I have first to log in a server, and then I have to log in a commom machine in a network. That requires two commands of ssh for different machines, and the same authentication for both.

Is there a way to make a script to do that? Because every script that I try to make only calls the first SSH, and after the first authentication, it keeps waiting until I finish it.

I think the script is waiting for the password on internal machine

there are several ways to do that:
1- if you have pine on the gateway, you can configure it to talk to the internal machine
2- you can set up a ssh tunneling
3- you can generate ssh keys without password

> The second script is a lot easier I guess, I have to log in the server machine as I said before, and then make a file transfer to the machine I connected. This requires 2 arguments from the command line, one for the files to send, and one for the location to put them after logging in the server.
For that I thought I could use SFTP, but for the same problem of the other program, I can't make it work. Someone told me to use SCP, but I read some manpages about SCP and it seems to do the oposite, not send, only download.

do you mean you want to transfer a file from the internal machine to the external machine ?

scp can works both ways :
scp localfile user@somehost:/remote_dir/
scp user@somehost:/path_to_remote_file /local_dir/

you can even transfer between two remote hosts :
scp user@somehost:/remote_file user@anotherhost:/remote_file

---

### Post by rogeriovinhal on 2006-03-19
[QUOTE=souki]I think the script is waiting for the password on internal machine

there are several ways to do that:
1- if you have pine on the gateway, you can configure it to talk to the internal machine
2- you can set up a ssh tunneling
3- you can generate ssh keys without password



do you mean you want to transfer a file from the internal machine to the external machine ?

scp can works both ways :
scp localfile user@somehost:/remote_dir/
scp user@somehost:/path_to_remote_file /local_dir/

you can even transfer between two remote hosts :
scp user@somehost:/remote_file user@anotherhost:/remote_file[/QUOTE]

Nice, then with SCP I think I can do a very good script that will help me with that.

But the SSH issue is still on.
What is a ssh tunnelling?
And generate ssh keys without password, how can I do that? Can I do that in all situations? Because the computer I need to log into is from my university, and as such, it has all kind of security means that they find possible to prevent invasions or attacks, that way maybe some features of SSH may be disabled to improve security.

---

### Post by souki on 2006-03-19
try to search on google for "ssh tunneling"
your problem is a little bit more complicated because there is three hosts

for the ssh keys, try google "ssh key pairs"

----
PS: I've find this in my bookmarks, I think it will make you happy
[http://realprogrammers.com/hack/SSH/tunneling.html](http://realprogrammers.com/hack/SSH/tunneling.html)

---

