---
title: "Firewall"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by sanjeevpunj on 2008-05-13
[CLOSED]Looking for a easy to use Firewall for Ubuntu.

---

### Post by sy88 on 2008-05-13
Try Firestarter.

---

### Post by gn2 on 2008-05-13
Ubuntu has a firewall installed by default, it's called IP Tables.

Firestarter is a GUI configuration tool for IP Tables.

Unless you need to adjust the settings of the existing firewall, you don't need Firestarter.

---

### Post by sy88 on 2008-05-13
> **gn2 said:**
> Ubuntu has a firewall installed by default, it's called IP Tables.

Firestarter is a GUI configuration tool for IP Tables.

Unless you need to adjust the settings of the existing firewall, you don't need Firestarter.

I would hardly call iptables "easy to use."  Sanjeev, if you're willing to learn the nitty gritty details of using a CLI firewall, then you may do so as well.

---

### Post by gn2 on 2008-05-13
> **sy88 said:**
> I would hardly call iptables "easy to use."  

Neither would I.

But Firestarter isn't a firewall and it probably isn't required.

I was just trying to point out that unless you need to change the default firewall settings (for whatever reason) you do not need Firestarter.

Firestarter should not be left running.

---

### Post by bodhi.zazen on 2008-05-13
If you are new to linux you will likely find iptables a little overwhelming at first.

There is a "new" method of configuring your firewall, ufw

IMO ufw is superior to firestarter, but it is command line only ...

See there links :

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

[http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html](http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html)

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by spotteddog on 2008-05-13
IP Tables is disabled by default, right?

If so, do I need to enable it for protection. 

Or, do I only need to enable it if I need to set up firewall rules?

I'm not clear on this. I had enabled it, but got confused and now it is disabled. Which is right? 

Thanks

Spot

---

### Post by Monicker on 2008-05-13
iptables is enabled by default, but without any restrictions.
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Basically all incoming and outgoing traffic is allowed, without any filtering.

---

### Post by rockerphil on 2008-05-13
i like my IP tables myself, but i've found that adding a GUI firewall is nice, so i'd suggest either Firestarter or Gnome Lokkit, both are good, if you're really wantin one that's really customizable try Guarddog, just remember that Guarddog is a bit more difficult to set up

---

### Post by mister_pink on 2008-05-13
If you just want to turn the firewall on, and don't need to add any complex rules, then use ufw, eg:
```
sudo ufw enable
```
to turn it on and:
```
sudo ufw allow ssh
```
will allow incoming ssh connections for example. Its quite easy to set up.

Edit: also, you might want deny all by default:
```
sudo ufw default deny
```
Also useful is
```
sudo ufw status
```

---

### Post by sanjeevpunj on 2008-05-13
Thanks. I tried using sudo ufw enable and here is what I get:-

1.WARN: /usr/bin is group writable ( I did that earlier for some reason, this folder has permissions to my group to write and create files)
2.Error: uid is 0 but '/usr' is owned by 1000
 Who is 1000? I am perplexed!

---

### Post by rockerphil on 2008-05-13
try running this code, it's to install firestarter, one of my fave GUI firewlls

Code:
sudo apt-get install firestarter

---

### Post by bodhi.zazen on 2008-05-13
LOL

Your user is 1000 !!!

Looks like you changed the ownership of system files, not good. Often this leads to re-installing.

---

### Post by pearjam on 2008-05-13
I think learning iptables would be the way to go.

---

### Post by Flynsarmy on 2008-05-13
I've found the whole firewall thing so difficult to understand on linux. Why isn't there a simple 'allow/deny' popup when a program tries to make an outgoing connection like on Windows? I know about firestarter, i know about iptables (although i don't know how to use either of thme) but IMO having a popup with the programs name and allow or deny with a checkbox to remember it seems to nice and simple to me. Is there any firewall for ubuntu that has this kind of functionality?

---

### Post by zeronothing on 2008-05-14
well as mentioned before the new firewall with hardy heron (ufw) is great and the syntax is easy. you can now use PF style syntax to create your firewall rules. if you don't know what PF is; it is OpenBSD's replacement for IP tables. for example if you wanted to allow something you would input a rule like "ufw allow proto ssh from any-to-any port 22." if you think this is hard try looking at IP tables. to me I love the syntax of PF, thanks OpenBSD

also check out the ubuntu [wiki]("https://wiki.ubuntu.com/UbuntuFirewall") for ufc firewall

---

### Post by nxfs on 2008-05-14
what about if you've tried to step into the world of LAMP on ubuntu desktop, wouldn't running firestarter for apache be a good thing?


...downloaded firestarter, should i install?...

---

### Post by hyper_ch on 2008-05-14
> **Flynsarmy said:**
> Why isn't there a simple 'allow/deny' popup when a program tries to make an outgoing connection like on Windows?
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Besides firwalls in Windows and Linux have different base concepts... while on windows everything is wide open and nothing can be trusted it's different on linux.

As you are likely behind a router, I doubt that you actually need to configure/modify iptables at all.

---

### Post by takuhii on 2008-05-14
> **bodhi.zazen said:**
> If you are new to linux you will likely find iptables a little overwhelming at first.

There is a "new" method of configuring your firewall, ufw

IMO ufw is superior to firestarter, but it is command line only ...

See there links :

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

[http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html](http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html)

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

Firestarter is just a GUI to configure IPTables, UFW is just a python script to configure IPTables... UFW is classed as an easier option to maintaining IPTABLES, HOWEVER, I am from the Windows GUI generation, and find GUIs an easier method to updating my firewall settings...

---

### Post by hyper_ch on 2008-05-14
and I think you normally don't need either firestarter nor ufw ;)

---

### Post by takuhii on 2008-05-14
If you're new to CLI you do need some GUI help every now and then, but as you get used to it, neither FireStarter or UFW are required... There's enough documentation out there to allow you to configure IPTables quite easily these days...

---

### Post by nxfs on 2008-05-15
Firestarter not needed, thats what I'm hearing. Since also firestarter seems to setup the computer as a firewall router to let the other computer connect to internet via that computer. This seems unecessary since cable modem box & wireless netgear box is already firedwalled?

Thanks for the help.

---

### Post by hyper_ch on 2008-05-15
> **nxfs said:**
> This seems unecessary since cable modem box & wireless netgear box is already firedwalled?
This is one reason...

And the other reason is, that you don't have any services listening by default... if you install a ssh server, then you have that on listening on port 22... if you install apache, then you have listening on port 80... those two apps are pretty safe by themselves.... (for ssh server I'd recommend deny hosts or fail2ban)...

On windows however you have with a normal "enduser" install countless services listening and the firewall on windows is also there to prevent data for going out... as much software is obtained from dubious sources or as many companies include some back-phone service where data is sent back you also want to filter outgoing traffic on windows... in linux this is not so much the case - no adware, nor malware (when you compile from sources or use trusted repos), ...

---

### Post by gn2 on 2008-05-15
> **nxfs said:**
> 
...downloaded firestarter, should i install?...

No need to do it the Windows way, it's best to use the version of any software that's in the repositories and install it using apt-get or Synaptic Package Manager or Add/Remove.

[https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

---

### Post by mr-Kirch on 2008-05-15
Open terminal and type in sudo ufw enable

---

### Post by nxfs on 2008-05-19
thanks for all your help... just to be safe, I installed firestarter anyways.:)

---

### Post by hyper_ch on 2008-05-19
why?

---

