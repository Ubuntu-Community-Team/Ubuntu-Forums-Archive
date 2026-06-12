---
title: "Ubuntu 12.04 LTS Server Domain Problems"
date: 2014-08-17
forum: New to Ubuntu
---

### Post by Baldry on 2014-08-17
Hey,

i am pretty new to Linux stuff so am trying my best here :D

I installed some weeks ago Ubuntu Server on a machine and it did work perfect ([http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p3)) used this guide.
now i want to Install the same again on a VM on my Windows 7 Machine but i got the Problem that i cant reach my Domain name. I can open apache over the IP but not with the Domain name. Also php doesnt work if i open over the browser php file with phpinfo(); than there is only on the screen "php info();" so it doesnt work. if there is any questto the conf i used the guide again and i didnt see any mistake. 

if there is any questen i will answer as good as i can.

EDIT: ah jeah i want to use the Server for programming Php and HTML so i dont really need anything else.

EDIT2: I just saw the problem with the Php. I used for my first file a Samba folder and opend that over the browser that didnt work. this time i chanced the file index.html in the folder /var/www/ to index.html.php and wirth phpinfo(); and now it does show my php settings. so php is working but not over my samba folder and my domain name is still not working

---

### Post by Baldry on 2014-08-17
almost 4 hours withought any tipp. is it that i descripted it bad?or no one has any tipps? i would test anything i just have no idee what to do at this point.

---

### Post by Baldry on 2014-08-19
No one any idee why it doesnt work?

---

### Post by steeldriver on 2014-08-19
What are the VM network settings? (NAT? bridged?)

How exactly did you configure DNS? The page you linked to doesn't seem to mention it specifically

---

### Post by Baldry on 2014-08-19
bridged network, i didnt do anything special to DNS. the only thing i did was in /etc/network/interfaces 
nameserver mygateway 4.4.8.8
i tired  
nameserver 8.8.8.8 4.4.8.8 
too 
both didnt work

i installt the same thing on my PC (no VM) and it did work withought doing anything else than in the guide
so i thought this would work on a VM too

---

### Post by steeldriver on 2014-08-19
OK so those settings relate to how your server resolves hostnames to addresses in its **outgoing **connections - they don't affect whether you will be able to connect **in **to the server using its name instead of its numeric IP

---

### Post by Baldry on 2014-08-19
What do i do now? because i installt the same thing on my phys maschine and i can connect to it from another maschine with the domain name(same network)

---

### Post by steeldriver on 2014-08-19
Are you only concerned about connecting from inside your LAN, or is this for connections from the public network? What do you mean exactly by "domain name" - is it just the local  hostname (or zeroconf-style hostname.local) or do you have a real FQDN  that you want to point to the server?

---

### Post by Baldry on 2014-08-19
Only inside my LAN.
with domain name i mean for example info.example.loc
a friend of mine said i need to add this to my host (windows 7) too
C:\Windows\System32\drivers\etc\hosts
than i can connect to it from my host. i will try that after i get home.
so my problem is fixxed if this is enough.
i am sry my english just goes so far, i dont really use it very often(only know what i leared at school)

the questen is do i need to do that for every domain i create?because i will have more than 1.

---

### Post by nerdtron on 2014-08-19
Yes add entry for each domain on your windows machine.

---

### Post by Baldry on 2014-08-19
YES! it works :D it sucks that i need to do that every time but what ever.

now i want to know how to configure it for the i-net too :D i dont need it now but someday i will.

---

