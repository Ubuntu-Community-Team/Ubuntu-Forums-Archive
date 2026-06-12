---
title: "snmpwalk  Timeout: No response from &lt;IP&gt;"
date: 2015-04-26
forum: New to Ubuntu
---

### Post by khunpaen on 2015-04-26
I created a ubuntu virtual server at aws.amazon.com, it has a public ip address of <removed>.
I am able to ping my virtual server(54.200.216.214) and log in to the ubuntu virtual server using ssh.


I want to do a snmpwalk from ubuntu machine to the virtual server at aws.amazon.com to make sure my snmp configurations are correct.


But when I do snmpwalk to the public IP of the virtual server, I received


    Timeout: No response from <removed>.

At my virtual server at aws.amazon.com, I have set a custom UDP rule to allow traffic from port 161, ICMP rule as well as HTTP for both inbound and outbound.

I also login to my virtual server through ssh and apt-get install snmp and snmpd.

this is the configurations I done on my virtual server

under /etc/snmp/snmpd.conf of my virtual server
     ```

         agentAddress udp:161, udp6:[::1]:161
         view all included .1.3.6.1.2.1.1
         view all included .1.3.6.1.2.1.25.1
         rocommunity public 192.168.1.0/24
         rocommunity public default -V all
     
```

 under /etc/default/snmpd of my ubuntu virtual server

      ```

          [COLOR=#000000][FONT=courier new] SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -g snmp -I -smux -p /var/run/snmpd.pid'[/FONT][/COLOR]
      
```

my status of ufw is active on my virtual server.

On my linux machine, this is the configurations I done

under /etc/snmp/snmpd.conf of my linux machine

     ```

         agentAddress udp:161, udp6:[::1]:161
         view all included .1.3.6.1.2.1.1
         view all included .1.3.6.1.2.1.25.1
         rocommunity public 54.0.0.0/8
         rocommunity public default -V all
     
```

under /etc/default/snmpd of my linux machine

      ```

          [COLOR=#000000][FONT=courier new] SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -g snmp -I -smux -p /var/run/snmpd.pid'[/FONT][/COLOR]
      
```

my status of ufw is inactive on my linux machine.

Please help. Thanks

---

### Post by sandyd on 2015-04-26
Have you changed the AWS firewall (security groups) to allow for SNMP traffic?

---

### Post by khunpaen on 2015-04-27
Hi. What I did was to set a custom UDP and allow port 161 for inbound and outbound traffic. Is that what you mean?

---

### Post by sandyd on 2015-04-27
When using AWS, there are two firewalls.

One on your VM, and one that is configured in [security group settings]("http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html")

If the ports are open, and you still have issues, check /var/log/syslog on EC2 - there should be logs there of why SNMP is not responding.

Side note: For security reasons, i have removed your IP from the first post.

---

### Post by khunpaen on 2015-04-27
thanks for your info

---

