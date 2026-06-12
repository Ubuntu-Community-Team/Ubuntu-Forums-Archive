---
title: "[SOLVED] I don't understand my ethertnet adapter"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by ricardo_sdl on 2008-11-06
I have a laptop with the sis 191 ethernet adapter. I've tried this with the auto configuration and setting the ip's and the dns ip's, but the only site that I can access is google. When I try to access reddit.com or uol.com.br the Firefox browser stays loading and never shows the website. I have windows xp running in dual boot and everything works fine in it. How can I access the internet beyond google (it's not so much but...)?
Thanks in advance.

---

### Post by nhasian on 2008-11-06
thats quite strange. can we get some more info on your setup?  are you behind a router?  are you getting your ip address automatically from the DHCP server?

can you post the output of *ifconfig*?

also what happens when you ping one of those sites you cant reach?

```
ping reddit.com
```

finally, please post the output of:

```
traceroute reddit.com
```

---

### Post by kernelhaxor on 2008-11-06
yeah try the ping and traceroute .. Make sure u dont hav any kinda blocker (like a Firefox addon) installed .. Contacting ur ISP is also a gud idea

---

### Post by ricardo_sdl on 2008-11-07
Here they are the screenshots of the commands nhasian:
the ping on the reddit.com:
[IMG]http://img47.imageshack.us/img47/8671/pingreddithb6.th.png[/IMG]

The ifconfig command:
[IMG]http://img384.imageshack.us/img384/1876/ifconfiglq8.th.png[/IMG]

I couldn't run the traceroute because I don't have the package installed and I couldn't use the "apt-get install" thing becase the problem of accessing the internet.
I don't think that the problem is the ISP kernelhaxor, because I use windows in the same computer and everything works fine.
Well, aparently the windows reconizes the ethernet adaptor as sis 191 and the ubuntu as sis 190, is this a problem?

---

### Post by nhasian on 2008-11-08
i cant enlarge those screenshots.  i think you just posted the thumbnails? screenshots are nice but you can just copy and paste the output right in the message.  if you use the Quote button to wrap the quote tags around the out it will be easier to read:

> here is some quoted text

i thought traceroute was part of tcp/ip.  what's it asking you to install when you run that in a terminal?

btw, apt-get is very easy to use.  just type

```
sudo apt-get install [package name]
```

"sudo" runs the apt-get command with administrative previliages.

"apt-get" is the name of the program we using

"install" is the variable we're giving the apt-get command.  there are other variables like remove, clean, purge, etc.

and the package name is ofcourse the name of the program you want to install.  for example if you want to install vlc (my favorite video player) you would just type:

```
sudo apt-get install vlc
```

I'll bet your wondering how to know what the correct package name is for a package you would like to install.  Use the *apt-cache search* command.

For example, lets say you want to install the Scumm emulator to play some of those classic point and click lucas arts games like *day of the tenticle* or *Secret of Monkey Island* but not sure what package to install?  just type:

```
apt-cache search scumm
```

then the output is:

> beneath-a-steel-sky - a science fiction adventure game
flight-of-the-amazon-queen - a fantasy adventure game
scummvm - free implementation of LucasArts' SCUMM interpreter

Great!  so we can see the third line down the package name is "scummvm"  Now you can install the package with the *apt-get install* :)

---

### Post by ricardo_sdl on 2008-11-08
Sorry for the thumbnails.
Here are the large images:
Ping Reddit.com
[IMG]http://img47.imageshack.us/img47/8671/pingreddithb6.png[/IMG]
the ifconfig command:
[IMG]http://img384.imageshack.us/img384/1876/ifconfiglq8.png[/IMG]

I'm not having problems with the apt-get command, this just doesn't work because the network problem.
I did some google search and I've found some issues of ubuntu with the sis191/190 ehternet adapter, like in this link:
[http://www.linuxquestions.org/questions/linux-networking-3/sis-191-adslpppoe-problem-631740/]("http://www.linuxquestions.org/questions/linux-networking-3/sis-191-adslpppoe-problem-631740/")
But it was in a previous version of the ubuntu(7.10).
Thanks!

---

### Post by ricardo_sdl on 2008-11-10
I don't know why, but it's just working now. Probably my mistake. Thanks for the answers!

---

