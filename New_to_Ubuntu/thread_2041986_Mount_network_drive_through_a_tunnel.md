---
title: "Mount network drive through a tunnel"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by Peterlorre on 2012-08-13
Hi All, 

I'm new to ubuntu and have decided to make the switch from Windows. I'm trying to map a network drive from work that can only be accessed through a gateway machine (e.g., to see my files in a terminal I would type ssh me@gatewaymachine; ssh me@internalmachine). Can someone direct me to the appropriate documentation for setting this up? I've always heard this practice referred to as 'tunneling', but the obvious searches aren't turning anything up. 

I'm running Ubuntu 12.04 (AMD64).

---

### Post by johnathansmith on 2012-08-14
Hi look [HERE]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding"), it's about ssh and PortForwarding, and [HERE]("https://help.ubuntu.com/community/SSH/")is main article. Let us know how you are doing!

---

### Post by Peterlorre on 2012-08-15
Hi Guys, 

I got things working after a lot more googling and discussion (which may or may not have been necessary). As johnathansmith suggested, it's a two-step process where you set up an ssh tunnel in the background and then mount the remote directory using sshfs. First, at the terminal I open the tunnel: 

ssh gatewaymachine -l username -Nf -L 20000:targetmachine:22

where I specify an arbitrary port (20000) and point it to the ssh port (22). The options allow me to specify my username and send the tunnel to background without a specific command. Next, I hook up the remote folder:

sshfs -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -p 20000 \ username@localhost: ~/SharedFolder/

And now SharedFolder looks at my home directory on the other side of the gateway machine. When I want to close/clean up, just unmount the directory: 

umount ~/SharedFolder

and find/kill the tunnel, which I did rather inelegantly by finking the process id with 

ps aux | grep SharedFolder

followed by 

kill processid

I encourage community members to point out better ways to do this...

---

