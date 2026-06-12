---
title: "What distro would you recomend?"
date: 2008-03-21
forum: Other OS Talk
---

### Post by patrickaupperle on 2008-03-21
I know you see a lot of these type of threads, but I can't find one with out special circumstances. I just want to try a distro that is different. I have tried Debian, (K)Ubuntu, Mint, and openSUSE KDE. openSUSE was quite a bit different, but the connection to microsoft and the inability for the installer to complete properly threw me off of it. I want to try something new. (Probably not debian based.)

---

### Post by freebios on 2008-03-21
try pc linux os it's a great windows like distro, its very popular has good community support and is easy to install.  I believe its based off mandrake.

---

### Post by patrickaupperle on 2008-03-21
Sounds good. I was thinking about freebsd, arch, and maybe slack or something. PCLOS sounds good too, though. I am downloading now. It does have a live environment, right? I would like to hear other suggestions, too.

---

### Post by mattk132 on 2008-03-21
Gentoo is good if you don't mind getting your hands a little dirty.  You have to configure a _lot_. But, it'll work great after that.:)

---

### Post by patrickaupperle on 2008-03-21
Gentoo? It looks pretty good, but it does not quite look like what I want, right now. Maybe some time in the future. :) Thanks for the suggestion, though.

---

### Post by OniLink on 2008-03-21
try Mandriva

---

### Post by patrickaupperle on 2008-03-21
I sm bit torenting mandriva and DLing FreeBSD. I decided against arch.

---

### Post by patrickaupperle on 2008-03-21
Just a couple more. I want 2 more or so, so when I get up tomorow I will have a lot to try.

---

### Post by patrickaupperle on 2008-03-21
I have now tried the PCLOS live cd. It is radically simple, almost too simple. It is a nice distro, but I won't be putting it on my HD. (it is only 60 GB)

---

### Post by ErusGuleilmus on 2008-03-21
I know that you mentioned that you decided against Arch, but I think that you should reconsider. Working with Arch has been a great learning experience for me. Once I got it configured to my preferences, I started to prefer it to Ubuntu.

---

### Post by RAV TUX on 2008-03-22
> **patrickaupperle said:**
> I know you see a lot of these type of threads, but I can't find one with out special circumstances. I just want to try a distro that is different. I have tried Debian, (K)Ubuntu, Mint, and openSUSE KDE. openSUSE was quite a bit different, but the connection to microsoft and the inability for the installer to complete properly threw me off of it. I want to try something new. (Probably not debian based.)Try Wolvix and PC-BSD (NOT Linux but BSD).

---

### Post by sujoy on 2008-03-22
well since you are wanting something different, try some rpm based ones.
arch is great though, i just love it

---

### Post by sandysandy on 2008-03-22
[SIZE="3"]Sabayon[/SIZE]

---

### Post by patrickaupperle on 2008-03-22
OK, I will try Arch. I will google Wolvix in a minute to see if I want to try it. PC-BSD? What about FreeBSD? I already have the ISO. What is the real difference?

Edit: Wolvix is downloading.
Edit2: Do you guys know how I can get openSUSE to install properly? I really like that distro.

---

### Post by patrickaupperle on 2008-03-22
I have arch installed now, but It just boots to a command line. What now? Please read above post also.

Edit: I found a guide. I typed:
```
pacman -S sudo
```
and got
```
warning: current locale is invalid; using default "C" locale
error: 'sudo' not found in sync db 
```

---

### Post by patrickaupperle on 2008-03-22
If I can not get this fixed, I might just remove Arch from my computer and use that partition for freebsd.

---

### Post by cardinals_fan on 2008-03-22
Try Zenwalk!  It is fast and well-designed.  I have not looked back since I started using it.  The new Live CD (coming out right about now) includes a gui installer.

---

### Post by patrickaupperle on 2008-03-22
Sweet. The Live CD on their homepage?

---

### Post by patrickaupperle on 2008-03-22
_**OH MY GOSH!**_

I just installed PClinuxOS in Virtual box and am updating. I used an outdated ISO.

---

### Post by DownTown22 on 2008-03-22
Give Fedora a go!

---

### Post by patrickaupperle on 2008-03-22
Ok, I was looking at that one for a while. I am DLing Zenwalk and upgrading PCLOS (see above post). I will probably wait till tomorow for that download.

---

### Post by fwojciec on 2008-03-22
> **patrickaupperle said:**
> If I can not get this fixed, I might just remove Arch from my computer and use that partition for freebsd.

The fix for this is easy: [http://wiki.archlinux.org/index.php/Locale]("http://wiki.archlinux.org/index.php/Locale")
The [Arch wiki](http://wiki.archlinux.org/index.php/Main_Page) is an indispensable resource for using Arch.

---

### Post by patrickaupperle on 2008-03-23
> **fwojciec said:**
> The fix for this is easy: [http://wiki.archlinux.org/index.php/Locale]("http://wiki.archlinux.org/index.php/Locale")
The [Arch wiki](http://wiki.archlinux.org/index.php/Main_Page) is an indispensable resource for using Arch.

Thank you, 
I already got rid of arch, though. I will reinstall when I get a chance.

---

### Post by rye_ on 2008-03-23
how about Ubuntu, I get the impression it's marginally popular, well suported etc :)

---

### Post by patrickaupperle on 2008-03-23
:) well I already tried ubuntu. I even have it installed right now. 
I reinstalled arch. Now part of the error was fixed. I still get 
```
error: 'sudo': not found in sync db
```

---

### Post by fwojciec on 2008-03-23
> **patrickaupperle said:**
> :) well I already tried ubuntu. I even have it installed right now. 
I reinstalled arch. Now part of the error was fixed. I still get 
```
error: 'sudo': not found in sync db
```

It should be in the core repo:
>  $ pacman -Ss ^sudo$
core/sudo 1.6.9p12-1
    Give certain users the ability to run some commands as root

Make sure that everything is correct in /etc/pacman.conf (consult [this wiki article](http://wiki.archlinux.org/index.php/Beginners_Guide#Package_Repositories_and_.2Fetc.2Fpacman.conf) if necessary) and sync pacman's database before trying to install anythin (pacman -Sy).

---

### Post by patrickaupperle on 2008-03-23
> **fwojciec said:**
> It should be in the core repo:


Make sure that everything is correct in /etc/pacman.conf (consult [this wiki article](http://wiki.archlinux.org/index.php/Beginners_Guide#Package_Repositories_and_.2Fetc.2Fpacman.conf) if necessary) and sync pacman's database before trying to install anythin (pacman -Sy).

pacman -Sy brings up errors.  My /etc/pacman.conf looks fine to me. I will install in VB so I can get  a screen. Maybe it will work from that install. If so I will correct my current install.

---

### Post by miggols99 on 2008-03-23
You might want to look at my installation guide if you are having errors with Arch Linux...

[http://archux.com/page/installation-guide](http://archux.com/page/installation-guide)

and see the rest of my website for other things like setting up sudo..also if you don't like using the command line too much there are two GUIs for pacman. Gtkpacman (Gnome, Xfce etc.) and Shaman (KDE), although Shaman is quite new which means it is a bit buggy.

---

### Post by fwojciec on 2008-03-23
> **patrickaupperle said:**
> pacman -Sy brings up errors.  My /etc/pacman.conf looks fine to me. I will install in VB so I can get  a screen. Maybe it will work from that install. If so I will correct my current install.

This, most likely, means that something is wrong with your network connection.  Try pinging google and see if it connects; if not: [http://wiki.archlinux.org/index.php/Beginners_Guide#Configuring_the_network_.28if_necessary.29]("http://wiki.archlinux.org/index.php/Beginners_Guide#Configuring_the_network_.28if_necessary.29")

---

### Post by rye_ on 2008-03-23
that reminds me.

how does pacman -Syu differ from pacman -Su

cheers

---

### Post by patrickaupperle on 2008-03-23
Sorry, I dont know how to ping. Do I just type ping [http://google.com/?](http://google.com/?) 

edit:What am I looking for after I ping google?

---

### Post by patrickaupperle on 2008-03-23
> **miggols99 said:**
> You might want to look at my installation guide if you are having errors with Arch Linux...

[http://archux.com/page/installation-guide](http://archux.com/page/installation-guide)

and see the rest of my website for other things like setting up sudo..also if you don't like using the command line too much there are two GUIs for pacman. Gtkpacman (Gnome, Xfce etc.) and Shaman (KDE), although Shaman is quite new which means it is a bit buggy.

I can't install a Gnome, because pacman won't work.:mad:. Once I get it working I will be getting a GUI for it though.:)

---

### Post by rye_ on 2008-03-23
> **patrickaupperle said:**
> Sorry, I dont know how to ping. Do I just type ping [http://google.com/?](http://google.com/?) 

edit:What am I looking for after I ping google?

you'll see something like this;
PING [www.google.com](www.google.com) (66.249.91.147) 56(84) bytes of data.
64 bytes from [www.l.google.com](www.l.google.com) (66.249.91.147): icmp_seq=1 ttl=243 time=48.9 ms

if not, you've got connection problems.

---

### Post by rye_ on 2008-03-23
you really ought to use 

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

as your reference guide.  it'll give all you need.

---

### Post by patrickaupperle on 2008-03-23
Ok. I put in 
```
 ping google.com 
``` 
and It told me 
```
 ping: unknown host google.com 
```

edit: I took a  look at the beginner guide and put in dhcpcd eth0 and then ping google.com and it gave me the first half of what you said it should. It has not returned me to a prompt yet, though.

---

### Post by miggols99 on 2008-03-23
Have you changed your /etc/rc.conf? Make sure it has
```

eth0="dhcp"

```
and not a static IP.

---

### Post by patrickaupperle on 2008-03-23
> **miggols99 said:**
> Have you changed your /etc/rc.conf? Make sure it has
```

eth0="dhcp"

```
and not a static IP.

I'll check, If I can figure how to stop the ping thing. :confused: Can you help there?

---

### Post by miggols99 on 2008-03-23
Just press Ctrl-C :)

---

### Post by patrickaupperle on 2008-03-23
Ok. It was not on DHCP, but I changed it. Unfortunantly it still does the same thing while pinging.

---

### Post by miggols99 on 2008-03-23
Try
```

/etc/rc.d/network restart
```

---

### Post by patrickaupperle on 2008-03-23
I did that and now I cant even get as far along with the pinging.
I got "unknown host google.com"

Edit: should I run dhcpcd eth0 again?

---

### Post by patrickaupperle on 2008-03-23
I ran dhcpcd eth0 again and it did not help at all.

edit: A reboot got me back to the half ping state.

---

### Post by miggols99 on 2008-03-23
That is strange...try this

Reboot

ifconfig
Is eth0 there? Any errors?

dhcpcd eth0
Any errors?

If that doesn't work, could you post the networking part of you /etc/rc.conf?
```
e.g.
HOSTNAME="michael-laptop"                                                

...
                                                                      
lo="lo 127.0.0.1"                                                        
wlan0="dhcp"                                                             
INTERFACES=(lo wlan0)                                                    

...
                                    
gateway="default gw 192.168.0.1"                      
ROUTES=(!gateway)
```

---

### Post by patrickaupperle on 2008-03-23
eth0 is there
No errors.

when I try the dhcpcd command this is what I get:
```
error,  eth0: dhcpcd already running on pid 2102
```

---

### Post by miggols99 on 2008-03-23
You need to kill dhcpcd. Do
```

killall dhcpcd
```
Then try again. If it works there should be no output...

---

### Post by patrickaupperle on 2008-03-23
It worked, the dhcpcd, but I still can't ping correctly. (half pinging)

edit rc.conf

```

----------------------------------------------------------------------------------------
Networking
----------------------------------------------------------------------------------------
HOSTNAME="myhost"
#A bunch of comments
 lo="lo 127.0.0.1"
eth0="dhcp"
INTERFACES=(lo eth0)
#more comments
gateway="default gw 192.168.0.1"
ROUTES=(!gateway)
#even more comments

```

---

### Post by LookTJ on 2008-03-23
> **patrickaupperle said:**
> I sm bit torenting mandriva and DLing FreeBSD. I decided against arch.
just so you know, FreeBSD is a lot harder and longer(post installation) to configure to where you would in Arch.

---

### Post by LookTJ on 2008-03-23
> **patrickaupperle said:**
> It worked, the dhcpcd, but I still can't ping correctly. (half pinging)

edit rc.conf

```

----------------------------------------------------------------------------------------
Networking
----------------------------------------------------------------------------------------
HOSTNAME="myhost"
#A bunch of comments
 lo="lo 127.0.0.1"
eth0="dhcp"
INTERFACES=(lo eth0)
#more comments
gateway="default gw 192.168.0.1"
ROUTES=(!gateway)
#even more comments

```Bah! Is net in your hooks?

edit  /etc/mkinitcpio.conf and see.

after you remove net from hooks

do mkinitcpio -p kernel26

---

### Post by patrickaupperle on 2008-03-23
> **Taylor said:**
> Bah! Is net in your hooks?

edit  /etc/mkinitcpio.conf and see.

after you remove net from hooks

do mkinitcpio -p kernel26

net is not in hooks. It says
```
Hooks="base udev autodetect pata scsi sata keymap filesystems"
```

---

### Post by LookTJ on 2008-03-23
> **patrickaupperle said:**
> net is not in hooks. It says
```
Hooks="base udev autodetect pata scsi sata keymap filesystems"
```mind to tell me? what's your gateway(router)? what's gateway the distro has set?

show output of "route" please.

---

### Post by patrickaupperle on 2008-03-25
> **Taylor said:**
> mind to tell me? what's your gateway(router)? what's gateway the distro has set?

show output of "route" please.

```

kernal IP routing table
Destination                 Gateway           Genmask                  Flags Metric Ref           Use         Iface
10.0.2.0                     *                   255.255.255.0         U        0         0             0         eth0
default                      10.0.2.2            0.0.0.0                 UG      0         0              0        eth0

```

---

### Post by patrickaupperle on 2008-03-26
Bump

---

### Post by patrickaupperle on 2008-03-27
Should I just get rid of arch and forget about it? Am I really just to stupid to get arch working?

---

