---
title: "VPN speed?"
date: 2021-11-27
forum: New to Ubuntu
---

### Post by d4m1r on 2021-11-27
Hey guys, this is maybe a dumb question but it is stumping me so I will ask here....

Basically, I am running an OpenVPN server on a Raspberry Pi 4 (8GB RAM) running the latest version of Ubuntu LTS (headless). Home connection is 100 mbps down and 10 mbps up.

However, when I connect to the OpenVPN server from any other device, I only get a 10/10 connection...Maybe the 10mbps download makes sense because the home connection where the raspberry pi is hosted "only" has 10mbps upload, but then shouldn't the upload speed over the VPN be higher than 10mbps? Because the home connection download speed is 100....

---

### Post by ActionParsnip on 2021-11-27
What speed is the Pi showing as its connection?

---

### Post by d4m1r on 2021-11-27
Good question, on a wired (gigabit ethernet) connection the raspberry pi directly is doing ~80 down and 10 up, according to a speedtest I just did.

So the raspberry pi itself seems to be getting the full speed, only over OpenVPN is the problem....Here is the network configuration just in case;

[IMG]https://i.imgur.com/2Am7zy3.jpg[/IMG]

---

### Post by ActionParsnip on 2021-11-27
Try
```

dmesg |grep eth0

```
It'll show you the speed that the link has come up as.

---

### Post by ActionParsnip on 2021-11-27
What speed is the VPN rated as too. This will affect the traffic also

---

### Post by d4m1r on 2021-11-27
> **ActionParsnip said:**
> Try
```

dmesg |grep eth0

```
It'll show you the speed that the link has come up as.

```
ubuntu@raspi:~$ dmesg |grep eth0[   19.773851] bcmgenet fd580000.ethernet eth0: Link is Down
[   24.894901] bcmgenet fd580000.ethernet eth0: Link is Up - 1Gbps/Full - flow c                                                                                                                                                             ontrol rx/tx
[   24.894941] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
ubuntu@raspi:~$

```

> **ActionParsnip said:**
> What speed is the VPN rated as too. This will affect the traffic also

Hmm? If my home connection is 100/10, shouldn't it be 10/100 over the VPN? I.e opposite, when using the VPN outside my home network

---

### Post by ActionParsnip on 2021-11-27
Your data is coming from the VPN endpoint. If all they give you is 5Mbps then you could have a million fibre channels it'll still come down at the slower speed.

---

### Post by d4m1r on 2021-11-27
The VPN is the OpenVPN server running on the Raspberry Pi, hosted at my home (100/10 connection).

Basically a way for me to tunnel into my home network remotely...But while connected to it remotely, the speedtest over the VPN speed is only ~10/10....

---

### Post by ActionParsnip on 2021-11-27
Have you tried an SSH tunnel instead of a VPN?

---

### Post by d4m1r on 2021-11-27
No, but I need to resolve this issue, using SSH is not an option :(

---

### Post by SeijiSensei on 2021-11-27
I use OpenVPN for all my VPN needs.  I suspect you have a routing problem, but let's see.

Try pinging the external and VPN addresses of both the Pi and a machine to which it is connected over the VPN.  Those numbers should be approximately the same.  Here are mine from a home computer on Verizon FiOS to a cloud server I maintain at linode.com.  These are the VPN figures

```

$ ping 10.1.1.1
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data.
64 bytes from 10.1.1.1: icmp_seq=1 ttl=64 time=13.8 ms
64 bytes from 10.1.1.1: icmp_seq=2 ttl=64 time=12.0 ms
64 bytes from 10.1.1.1: icmp_seq=3 ttl=64 time=13.3 ms

```

And these are the figures between the two machines' external addresses.
```

$ ping xxx.xxx.xxx.xxx
64 bytes from server.linode.com (xxx.xxx.xxx.xxx):icmp_seq=1 ttl=55 time=11.3 ms
64 bytes from server.linode.com (xxx.xxx.xxx.xxx):icmp_seq=2 ttl=55 time=11.0 ms
64 bytes from server.linode.com (xxx.xxx.xxx.xxx):icmp_seq=3 ttl=55 time=10.4 ms

```
so a little overhead for encryption.

If your figures are vastly different using the different pairs of interfaces, maybe there's a routing issue.  Show us the contents of your routing table on both the client and the Pi using the command "route -n" if you have that or "ip route" if you do not. 

Are you setting up a custom route on the Pi that sends all traffic for your local network back through the VPN? My home network uses 192.168.100.0/24, while my VPN network uses 10.1.1.0/24.  On the machine that would be the equivalent of your Pi, I add that custom route with the command
```
ip route add 192.168.100.0/24 via 10.1.1.30
```
where 10.1.1.30 is the VPN address of the client machine. I call an executable script to run that command using the OpenVPN "up" directive in the OpenVPN configuration file for the connection. 
```
up /path/to/add_routes_script
```
The script will run with root privileges so no "sudo" is needed in the "ip route" command.

Without this route, the upsteam machine will send packets arriving from the VPN out its "default gateway," which is usually your router to the Internet. That's the wrong direction for these packets; they should be going back down the tunnel. Your upstream router doesn't know what to do with them since they carry private addresses which can't forwarded to the public Internet. 

Even with the route in place, the Pi may not be able to use it. Ubuntu machines by default cannot forward packets from one IP network to another.  On the Pi you'll need to edit, as root with sudo, the file /etc/sysctl.conf. Remove the hash mark from the beginning of the line that reads
```
net.ipv4.ip_forward=1
```
then reboot.

---

### Post by naxal on 2021-11-29
Hello,

I am not expert here so please wait and read expert comments. These are just from my personal exp of using OpenVPN Ubuntu 20 LTS Server

I use this script for VPN Server Setup, and its tunnel type I guess -> [https://raw.githubusercontent.com/Nyr/openvpn-install/master/openvpn-install.sh](https://raw.githubusercontent.com/Nyr/openvpn-install/master/openvpn-install.sh) (as Server Mode)

The configuration from above allows me to create one or more clients (key files) as I please. Clients can use their respective Config files to get connected.

Now there are few troubleshooting I had to do for mitigating the speed issue,

1. MTU Values of your VPN Network Interface. -> I figured it should not be more than the physical connection value, in fact in some cases, lower than physical network value helps.
2. Send Buffer and receive buffer values, -> sndbuf & rcvbuf needed to be manual set to 0 in both Server and Client Config. That allowed Server and Client OS to set their own rather than being fixed at some. For some reason, without this set to 0, whatever higher or lower value I tried, gave me some short of performance issue.

Lastly, VPN speeds from outside your own home network will depend on mainly 2 things,

1. The ISP route speed between your VPN Server and the client.
2. VPN Speed throttle -> As many ISPs are using something called deep packet inspection techniques to slow down your VPN Traffic

Now, first one is though to solve. Since ISP may not take the headache to troubleshoot such deep for a single user. However, for the VPN throttle issue, you may need to reconfigure your VPN Server to run on TCP Protocol with Port 443 to bypass that. Some times if you complain to your ISP regarding any specific port / protocol, they may remove speed restriction (VPN Throttle) for that particular port or for your IP entirely !!

3. The VPN Encryption overhead. -> Encrypted traffic will put some load in your VPN Server, so if the CPU usage is shooting up, then I guess you may either need to lowed the encryption under VPN Settings or remove it altogether (not recommended I guess for public network traffic), Otherwise, get a better CPU for the Server.

I have a 100/100 Fiber Connection and with similar fast public network in client (UDP Protocol), I can get roughly upto 98/98 steady up n down. Its tough for me to figure that last couple of mbps, as whether its due to VPN overhead or may be if I connect the client from a very fast public connection, I can achieve 100/100. But 98/98 is fast enough for me and I gladly accepted.

Thanks.

---

### Post by ActionParsnip on 2021-11-29
Again, just because you have a fast connection to the web doesn't mean the traffic will necessarily go fast. The data coming down the VPN is a factor and the slower of the two will dictate the speed. If your VPN endpoint only gives you 1Mbps then you will get 1Mbps no matter how much you upgrade your connection.

---

### Post by The Cog on 2021-11-29
Your VPN server is at your home, which has an upload speed of 10M.
If you are using the VPN server to test between client and a public speed test service (over the VPN), then both directions rely on your home's upload speed limit.
You should not expect more than 10M either way, because:
* Your download is limited to 10M because your home can't upload to your client faster than that, and 
* your upload is limited to 10M because your home can't upload to the speed-test service faster than that.

---

