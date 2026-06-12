---
title: "Trying to make Script"
date: 2017-04-18
forum: Programming Talk
---

### Post by gasparmenendez on 2017-04-18
Hi folks, first of all I need to say that I'm not a programmer, but I need to do something based on programming....
My problem is that I need to modify the DNS servers in almost 1000 nanostation equipments. I have access to them through ssh and I want to make a script to acomplish the task. I already made a file with the ip addresses of all CPE's (named client.txt). I think my script can begin like this:

#!/bin/bash
for host in $(cat client.txt);
do
ssh Administrador@$host sameforall;
sed 's/x.x.x.x/y.y.y.y /etc/resolve.conf;
sed 's/w.w.w.w/z.z.z.z /etc/resolve.conf;

# here I restart network service but I don't have the command yet
done.


y.y.y.y and z.z.z.z are the new DNS servers and x.x.x.x w.w.w.w the old ones


I know this is far away to be correct, but I need somebody help me. The first problem I'm going to find is that ssh prompts me to put the given servers ssh key to my known_hosts file, how can I solve this???

Can anybody please help me??? Thanks in advance.

BR.

---

### Post by TheFu on 2017-04-18
There are 50-500 different methods to solve this.

a) use **expect** - it is a tool designed to respond to prompts - the killer app for it was changing passwords across multiple systems before ssh-keys existed. 
b) use a devops tool like ansible - this can work well when the passwords and accounts are all the same, but requires a few python modules on the remote system to work.
c) make the files you need locally and scp them into place on each of the devices as needed.

Your sed commands are incorrect.  You don't need sed anyway.  If the contents of /etc/resolv.conf are the same on all systems, you can just scp/sftp that same file to all of them.  If the nanostation has sed, then it probably supports scp too.  No need for ssh this way either, except that scp/sftp are part of the normal ssh install/config.

If you want to push your public ssh key to each system, use a similar loop and **ssh-copy-id**.  Might be easier to use **expect** for this too, so you don't have to retype your password.

Ansible -Copy files to remote locations: [https://docs.ansible.com/ansible/copy_module.html](https://docs.ansible.com/ansible/copy_module.html) - check out the examples section. You only need 1 of those stanzas.  Plus, if you need to manage 1,000 systems, learning Ansible will more than pay for your time in the future.

Expect is a little "old school." [https://linux.die.net/man/1/expect](https://linux.die.net/man/1/expect) and [https://linuxaria.com/howto/2-practical-examples-of-expect-on-the-linux-cli](https://linuxaria.com/howto/2-practical-examples-of-expect-on-the-linux-cli)

---

### Post by SeijiSensei on 2017-04-18
Are w.w.w.w and x.x.x.x being taken out of service, or are they simply no longer providing DNS?  If the latter, you could forward traffic arriving on port 53 of these servers over to the new machines with iptables:
```

sudo iptables -t nat -A PREROUTING -p tcp -d w.w.w.w --dport 53 -j DNAT --to-destination y.y.y.y:53
sudo iptables -t nat -A PREROUTING -p udp -d w.w.w.w --dport 53 -j DNAT --to-destination y.y.y.y:53
sudo iptables -t nat -A PREROUTING -p tcp -d x.x.x.x --dport 53 -j DNAT --to-destination z.z.z.z:53
sudo iptables -t nat -A PREROUTING -p udp -d x.x.x.x --dport 53 -j DNAT --to-destination z.z.z.z:53

```

An even more basic question, though, is whether y.y.y.y and z.z.z.z can be assigned the old w.w.w.w and x.x.x.x addresses.  I'm proposing making the changes on the server side so you don't need to change all the individual resolv.conf files.

If the workstations get their address information via DHCP, then the simplest solution is to have the DHCP server give out y.y.y.y and z.z.z.z as the DNS servers.  If you change the DHCP server, the workstations will get the right server addresses when they are next rebooted.

---

### Post by gasparmenendez on 2017-04-19
thank you both for your answers my friends...
Actually I'm testing option c) that @TheFu suggested. I'll post results.
BR.

---

### Post by gasparmenendez on 2017-04-21
hi @TheFu ! already tried what you  suggested me in option c) but didn't work, cause when I do scp /path/to/good-resolv.conf [email]root@host:/etc/resolv.conf[/email] the host ask for  the password. Any way to solve this issue??? I need to say that all  nanostation (or almost all) have the same user / password

---

### Post by TheFu on 2017-04-21
> **gasparmenendez said:**
> hi @TheFu ! already tried what you  suggested me in option c) but didn't work, cause when I do scp /path/to/good-resolv.conf [email]root@host:/etc/resolv.conf[/email] the host ask for  the password. Any way to solve this issue??? I need to say that all  nanostation (or almost all) have the same user / password

Already answered.

To solve it, you have 3 choices ... 
a) use **expect** to answer the password question.
b) setup ssh-keys (use **ssh-copy-id**) on all the systems (which I would use *expect* for the initial userid/password aspect); then you can scp directly.
c) use Ansible (also dependent on ssh), but it knows how to answer the password sudo/login questions if you tell it with an option.

Ansible is probably the easiest and will take you farther with multi-systems management. You can use ansible to setup the ssh-keys too.
Expect is what we used in the early 1990s, so it has an old-school feel.

---

