---
title: "Ubuntu cloud 11.04 issue"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by sidsachdev on 2013-03-13
i am trying to install cloud  on private network

server1  - cc , walrus, sc
eth0 : 192.170.1.180

hostname: server1
dns: 192.170.1.1 , 8.8.8.8

gateaway 192.170.1.1

clustername - myueccluster
cloud controller address -blank

domain name: uec.com

http: blank
system mail name: server.uec.com
public ip -  192.170.1.1 -192.170.1.199

server2 - nc

etho - 192.170.1.111

hostname: nodeserver
dns : 192.170.1.1
gateway 192.170.1.1

domain name: nodeuec.com
cloud controller address: 192.170.1.180


--------------------------------------------------------

no dns server is established, i am just using these values , if incorrect please correct me

installed ntp server on both server 1 and server2 
modified ntp.conf

even made changes in eucalyptus.conf file on nc
 
------------------------------------------------------

ISSUE: from server 2  - temporary change of eucalyptus -  sudo passwd  eucalyptus
server 1 - sudo -u eucalyptus ssh-copy-if-i ~eucalyptus/.ssh/id_rsa.pub eucalyputs@192.170.1.111
server 2- sudo passwd -d  eucalyptus

sudo euca_conf --discover-nodes

how to remove this error, and please reply
[COLOR=#000000][FONT=Times New Roman][FONT=Ubuntubeta]
[/FONT][/FONT][/COLOR]
New node found on fe80::222:19ff:fe64:178f; add it? [Yn] Y

INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization.

Trying rsync to sync keys with "fe80::222:19ff:fe64:1639"...ssh: Could not resolve hostname fe80: Name or service not known
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
failed.


Trying scp to sync keys to: eucalyptus@fe80::222:19ff:fe64:1639://var/lib/eucalyptus/keys/...
ssh: Could not resolve hostname fe80: Name or service not known
lost connection
failed.

ERROR: could not synchronize keys with fe80::222:19ff:fe64:1639!
The configuration will not have this node.
Hint: to setup passwordless login to the nodes as user eucalyptus, you can
run the following commands on node fe80::222:19ff:fe64:1639:
sudo -u eucalyptus mkdir -p ~eucalyptus/.ssh
sudo -u eucalyptus tee ~eucalyptus/.ssh/authorized_keys > /dev/null <<EOT
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC3iDh4+58Eg2KTvKtVZwRA7CcW3UwlSfboR3BQQi9vc1v74cbDeW83s6l9yKuQRgH7Di+pB5dho4VbqilpycGTTlgq++HGZMKnSUUgaof7/LWS/StThUOMLyf5+9a8XMoBZFHnvje8vAx5aNaA4lvyAQN2JIujDJ4qhmImOyTm1wJ6FwxyWEhLJCLX3HUKlifnKwozkXpQcNJ59LRYk5kG1jSHMX7XRSVkwnEQW7DGD54dPcamW8WAgfwj8BrEV6EwRaEut5iqxo/xjRl/GnPGcmHUwFQiLNqhG3S93q0BF5DsUOD3MgCPWIzk1+YESAhgd/NePaXGiFYBKFq+zJE/ eucalyptus@chmurka
EOT

Be sure that authorized_keys is not group/world readable or writable

Trying rsync to sync keys with "fe80::222:19ff:fe64:178f"...ssh: Could not resolve hostname fe80: Name or service not known
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
failed.


Trying scp to sync keys to: eucalyptus@fe80::222:19ff:fe64:178f://var/lib/eucalyptus/keys/...
ssh: Could not resolve hostname fe80: Name or service not known
lost connection
failed.

ERROR: could not synchronize keys with fe80::222:19ff:fe64:178f!
The configuration will not have this node.
Hint: to setup passwordless login to the nodes as user eucalyptus, you can
run the following commands on node fe80::222:19ff:fe64:178f:
sudo -u eucalyptus mkdir -p ~eucalyptus/.ssh
sudo -u eucalyptus tee ~eucalyptus/.ssh/authorized_keys > /dev/null <<EOT
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC3iDh4+58Eg2KTvKtVZwRA7CcW3UwlSfboR3BQQi9vc1v74cbDeW83s6l9yKuQRgH7Di+pB5dho4VbqilpycGTTlgq++HGZMKnSUUgaof7/LWS/StThUOMLyf5+9a8XMoBZFHnvje8vAx5aNaA4lvyAQN2JIujDJ4qhmImOyTm1wJ6FwxyWEhLJCLX3HUKlifnKwozkXpQcNJ59LRYk5kG1jSHMX7XRSVkwnEQW7DGD54dPcamW8WAgfwj8BrEV6EwRaEut5iqxo/xjRl/GnPGcmHUwFQiLNqhG3S93q0BF5DsUOD3MgCPWIzk1+YESAhgd/NePaXGiFYBKFq+zJE/ eucalyptus@chmurka
EOT

Be sure that authorized_keys is not group/world readable or writable

---

