---
title: "Re: /etc/apt/sources.list problem"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by tester100 on 2011-10-27
Hi guys

i got a similar error with my version

i will explain what i did..


had problems with sources.list before error -5 and -11 when i was trying to do apt-get udpate logged in with root account..

so i though well i will format it as i have just done alots of changes on the original services.list

so i formated installed fresh install of ubuntu server10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.2) with PTBR language support.

did all the updates with apt-get update and apt-get upgrade..


then changed dhcp to static and still worked fine..

shortly after it was time to install java 

so i added the following repository via cmd terminal

add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"

it showed up message to install firstly the apt-get phyton-software-properties, which i did great , then added new repositorey via terminal.

did afterwards apt-get update to update all new stuff, and downloaded java jre and jdk6 to install on machine..

all lovely and great.. shortly after it was time to reboot the machine and so i did it.

after reboot, i tried installing ISPconfig 3.0.33 via terminal and all its softwares related such as apach2, mysql etc..  and now i am getting all sorts of erros and i cannot download anything

tried to do apt-get update and i get wget error also

```
Err [http://archive.canonical.com]("http://archive.canonical.com/") lucid Release.gpg
  Algo estranho aconteceu 'archive.canonical.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Err [http://br.archive.ubuntu.com]("http://br.archive.ubuntu.com/") lucid Release.gpg
  Algo estranho aconteceu 'br.archive.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Err [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security Release.gpg
  Algo estranho aconteceu 'security.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-pt_BR
  Algo estranho aconteceu 'archive.canonical.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Err [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid/main Translation-pt_BR
  Algo estranho aconteceu 'br.archive.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-pt_BR
  Algo estranho aconteceu 'security.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Ign [http://archive.canonical.com]("http://archive.canonical.com/") lucid Release
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-pt_BR
  Algo estranho aconteceu 'security.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Err [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-pt_BR
  Algo estranho aconteceu 'br.archive.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Err [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid/universe Translation-pt_BR
  Algo estranho aconteceu 'br.archive.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Ign [http://archive.canonical.com]("http://archive.canonical.com/") lucid/partner Packages
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-pt_BR
  Algo estranho aconteceu 'security.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Err [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-pt_BR
  Algo estranho aconteceu 'br.archive.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Ign [http://archive.canonical.com]("http://archive.canonical.com/") lucid/partner Sources
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-pt_BR
  Algo estranho aconteceu 'security.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Err [http://br.archive.ubuntu.com]("http://br.archive.ubuntu.com/") lucid-updates Release.gpg
  Algo estranho aconteceu 'br.archive.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Ign [http://archive.canonical.com]("http://archive.canonical.com/") lucid/partner Packages
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security Release
Err [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-pt_BR
  Algo estranho aconteceu 'br.archive.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Ign [http://archive.canonical.com]("http://archive.canonical.com/") lucid/partner Sources
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/main Packages
Err [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-pt_BR
  Algo estranho aconteceu 'br.archive.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Err [http://archive.canonical.com]("http://archive.canonical.com/") lucid/partner Packages
  Algo estranho aconteceu 'archive.canonical.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/restricted Packages
Err [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-pt_BR
  Algo estranho aconteceu 'br.archive.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Err [http://archive.canonical.com]("http://archive.canonical.com/") lucid/partner Sources
  Algo estranho aconteceu 'archive.canonical.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/main Sources
Err [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-pt_BR
  Algo estranho aconteceu 'br.archive.ubuntu.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/restricted Sources
Ign [http://br.archive.ubuntu.com]("http://br.archive.ubuntu.com/") lucid Release
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/universe Packages
Ign [http://br.archive.ubuntu.com]("http://br.archive.ubuntu.com/") lucid-updates Release
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/universe Sources
Ign [http://br.archive.ubuntu.com]("http://br.archive.ubuntu.com/") lucid/main Packages
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/multiverse Packages
Ign [http://br.archive.ubuntu.com]("http://br.archive.ubuntu.com/") lucid/restricted Packages
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/multiverse Sources
Ign [http://br.archive.ubuntu.com]("http://br.archive.ubuntu.com/") lucid/main Sources
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/main Packages
Ign [http://br.archive.ubuntu.com]("http://br.archive.ubuntu.com/") lucid/restricted Sources
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/restricted Packages
Ign [http://br.archive.ubuntu.com]("http://br.archive.ubuntu.com/") lucid/universe Packages
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/main Sources
Ign [http://br.archive.ubuntu.com]("http://br.archive.ubuntu.com/") lucid/universe Sources
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/restricted Sources
Ign [http://br.archive.ubuntu.com]("http://br.archive.ubuntu.com/") lucid/multiverse Packages
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") lucid-security/universe Packages

```
strange..

here is my sources.list

```
#
#deb cdrom:[Ubuntu-Server 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.2)]/ lucid main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

```Any help will be appreciated..


ohh and yes i have killed all apt processes running before trying to run apt-get update again

by doing

ps -e | grep apt


kill -9  id process of apt running....


Any comments or ideas to fix solution are welcomed..

i have deleted the repository added for java and rebooted the server machine but i still get the same error.

Mod Note: The thread that he is referring to is [here]("http://ubuntuforums.org/showthread.php?t=1641542&page=2").

---

### Post by wolfen69 on 2011-10-27
Could you translate *Algo estranho aconteceu 'archive.canonical.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)*

---

### Post by tester100 on 2011-10-27
> **wolfen69 said:**
> Could you translate *Algo estranho aconteceu 'archive.canonical.com:http' resolvendo (-5 - NÃ£o hÃ¡ endereÃ§o associado com o nome)*


hi yes i forgot

Something strange happened 'archive.cannonica.comxxxxxxx resolve (-5 no address associated with name)

---

### Post by wolfen69 on 2011-10-27
The addresses of the sources list should match the addresses from **sudo apt-get update**.

---

### Post by 3rdalbum on 2011-10-28
In English, I think the error message would be "Something wicked happened resolving http://archive.canonical.com".

It means that the address is probably correct, but there might be something odd happening with your network. Are you still using a static IP and a static DNS, or have you switched back to DHCP?

---

### Post by tester100 on 2011-10-28
> **3rdalbum said:**
> In English, I think the error message would be "Something wicked happened resolving http://archive.canonical.com".

It means that the address is probably correct, but there might be something odd happening with your network. Are you still using a static IP and a static DNS, or have you switched back to DHCP?



Hi guys

yes indeed i made further testing today

if i put static ip i have internet access and everything

but cannot make updates or install anything

if i switch back to DHCP it updates new IP and it works great i can run apt-get update and upgrades and install further programs

any hints on how should i setup my static ip ::

i have checked ipcofig /all on my other windows machine and all i can see is 

address
netmask
gateway

i cannot see broacast or network ips 

as i have the following static

auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

i think the problem lies on the network and the broadcast ips...

i will try to delete them
and make static ip again to see if i can connect on apt-get update..



I will also check my PC router firewall as i am running a separate machine P4 1Gb Ram with Pfsense Router firewall FreeBSD linux system, perhaps its is blocking my fix ip..

as i have tested now i changed on to another static IP, and i have deleted the network and broadcast ips, just left the netmask, ipaddress, an gateway and now apt-get upgrade and update working again i can now install tools back on the ubuntu.

---

### Post by wolfen69 on 2011-10-28
Excuse my ignorance, but how come my sources list and update list match? Is it just a US thing? I thought the addresses were supposed to match perfectly?

---

### Post by tester100 on 2011-10-28
> **wolfen69 said:**
> Excuse my ignorance, but how come my sources list and update list match? Is it just a US thing? I thought the addresses were supposed to match perfectly?




well its working now..

i think the problem was on the dns nameserver on the resolve.conf .. something strange was happening anywys..

ohh by the way i don´t have sinaptics manager installed or ubuntu software as i am running ubuntu server no graphic GUI... as it is meant to run on low memory ram.

---

