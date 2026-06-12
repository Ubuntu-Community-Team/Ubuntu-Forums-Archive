---
title: "How can i copy a folder from windows onto my ubuntu shell (for windows10)?"
date: 2020-03-05
forum: New to Ubuntu
---

### Post by kprice55 on 2020-03-05
Id like to copy a folder from my Windows platform to my Ubuntu subsystem.  When I do I get the message

couldn't change working directory to "/home/usr/folder": no such file or directory
    while executing
"cd $data(-directory)/$theDir"
    (procedure "feat_file:InvokeDir" line 9)
    invoked from within
"feat_file:InvokeDir .wdialog1"
    (command bound to event)

---

### Post by yancek on 2020-03-05
>  Id like to copy a folder from my Windows platform to my Ubuntu subsystem.

"Ubuntu subsystem"?  Are you using what is described at the microsoft site below?  If so, that is windows software not Linux and you might be better off posting at a windows forum.  You might be able to get help here from someone who uses windows but the absolute first thing you would need to do is explain "exactly what you did to get that error", how did you try to copy? 

[https://docs.microsoft.com/en-us/windows/wsl/faq](https://docs.microsoft.com/en-us/windows/wsl/faq)

---

### Post by TheFu on 2020-03-05
> **yancek said:**
> "Ubuntu subsystem"?  Are you using what is described at the microsoft site below?  If so, that is windows software not Linux and you might be better off posting at a windows forum.  You might be able to get help here from someone who uses windows but the absolute first thing you would need to do is explain "exactly what you did to get that error", how did you try to copy? 

[https://docs.microsoft.com/en-us/windows/wsl/faq](https://docs.microsoft.com/en-us/windows/wsl/faq)

Exactly which program was being used?  Which protocol does that program use? Which computer, the Windows one or the Linux one, it the program running?  Are they networked somehow?

I use 2 different methods to move stuff between Windows (from Windows) onto Linux.
a) Samba file sharing
b) WinSCP using sftp/scp connections.
These are both network connections and require that a service/daemon be running on the Linux side for the Windows machine to talk through.

sftp is really simple to setup and considered secure enough to use over the internet.  **sudo apt install ssh fail2ban** then load WinSCP on your Windows machine and point it at the Linux machine IP address, provide any login credentials. Bob's your uncle.  With that that 1 command, you get ssh, scp, sftp and the ability to leverage ssh tunnels for rsync, sshfs, remote desktops, and 50+ other things. Most backup tools for Unix leverage ssh connections. If you are a programmer, git uses ssh.  ssh is how unix people move data between systems.  Every Linux system in the world being remotely managed uses ssh. That's hundreds of millions of machines, perhaps over a billion.  Every Linux file manager can connect to other Linux systems using an sftp:// URL.  Local or remote - LAN or internet. If the connection is allowed, they can talk.

Samba is a little harder and not considered secure, but Samba works using the normal file manager, Explorer, in Windows.
[https://ubuntuforums.org/showthread.php?t=2434383](https://ubuntuforums.org/showthread.php?t=2434383) explains the Samba setup.

Which would you like to install?  You can have both.

---

### Post by kprice55 on 2020-03-05
yes I am using wsl, thanks. I get tired of mounting the C drive every time. I will check there.

---

### Post by kprice55 on 2020-03-05
They are both on the same machine so the ip address would be the same i believe? Thanks for your reply, i will check on the windows forums.

---

### Post by TheFu on 2020-03-05
> **kprice55 said:**
> They are both on the same machine so the ip address would be the same i believe? Thanks for your reply, i will check on the windows forums.

I wouldn't know.  Never seen anyone using WSL and I've never touched Win10 - the EULA stopped us from loading it on the network.

---

