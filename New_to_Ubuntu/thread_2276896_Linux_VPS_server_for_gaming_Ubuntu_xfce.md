---
title: "Linux VPS server for gaming Ubuntu xfce ?"
date: 2015-05-05
forum: New to Ubuntu
---

### Post by abaki on 2015-05-05
Hi,

i have been dealing with linux server that i just bought. I have never used linux before but i learn fast.

I established to install ubuntu ,xcfe and different desktop enviroments.

I am planing to use my server as a gameserver and the game i want to install supports only windows. Thus, i will use wine.

I just couldnt understand which is good for my purpose. ubuntu xubuntu xcfe ?

i want to use xfce and ubuntu software center.

i tried and install the ubuntu 14.04 and xfce desktop with ubuntu apps. However, xfce version is 4.10 and i want latest.
i use those commands below but couldnt do it

[COLOR=#666666][FONT=Titillium]i:[/FONT][/COLOR]sudo add-apt-repository ppa:xubuntu-dev/xfce-4.12sudo add-apt-repository ppa:xubuntu-dev/extrassudo apt-get updatesudo apt-get dist-upgrade

i use those commands when i choose Ubuntu 12.04 x64 - Minimal from my VPS control panel:


1: apt-get update
2: apt-get upgrade
3:apt-get install xubuntu-desktop
4:apt-get install xfce4
5:apt-get install xrdp

---

### Post by sandyd on 2015-05-05
The PPA you tried to install from does not have XFCE 4.12 builds for precise.

Install 14.04 LTS instead, and use the PPA, and it should work.

Additional Suggestions:
- Best is to not have a GUI, and just use the CLI to manage the server for security and to keep the installation minimal.
- If you want a remote desktop, take a look at x2go, it is much faster and responsive than VNC

---

### Post by abaki on 2015-05-05
> **sandyd said:**
> The PPA you tried to install from does not have XFCE 4.12 builds for precise.

Install 14.04 LTS instead, and use the PPA, and it should work.


how i do that ? installing 14.04 LTS  using PPA ? i 'm new i follow instructions that i foun internet :(

---

### Post by sandyd on 2015-05-05
You have to install Ubuntu 14.04 from your VPS control panel, or upgrade to 14.04 from 12.04. If you have the option to install 14.04 in the control panel, use that, either try the following
```

sudo apt-get install upgrade-manager-core
sudo do-release-upgrade
```

---

### Post by abaki on 2015-05-05
> **sandyd said:**
> You have to install Ubuntu 14.04 from your VPS control panel, or upgrade to 14.04 from 12.04. If you have the option to install 14.04 in the control panel, use that, either try the following
```

sudo apt-get install upgrade-manager-core
sudo do-release-upgrade
```

There ara two option [COLOR=#000000][FONT=Verdana]Ubuntu 12.04 x64 - Minimal and  [/FONT][/COLOR][COLOR=#000000][FONT=Verdana]Ubuntu 14.04 x64 - Minimal in the [/FONT][/COLOR]VPS control panel.

i think the do not provide Ubuntu 14.04 LTS you mentioned. can i upgrade [COLOR=#000000][FONT=Verdana]12.04 x64 - Minimal to [/FONT][/COLOR]14.04 LTS  by the command that you wrote above ?

---

### Post by sandyd on 2015-05-05
Ubuntu 14.04 x64 - Minimal is the same as Ubuntu 14.04 LTS, you'll notice that a lot of VPS providers just omit the LTS part in the name

---

### Post by abaki on 2015-05-06
> **sandyd said:**
> Ubuntu 14.04 x64 - Minimal is the same as Ubuntu 14.04 LTS, you'll notice that a lot of VPS providers just omit the LTS part in the name


thanks a lot i made it :) 

right now i have to learn wine in order to start my game in it :)

---

### Post by abaki on 2015-05-06
do you think using root access better or should i added user for my linux server ?

---

### Post by mastablasta on 2015-05-07
you should use root on server. Once I got is sort of secured and opened it to internet I immediately got attacked by the Chinese. luckily they tried to break in as root and using brute force attacks to guess a password.

I would say do some reading, avoid the desktops, use a good webgui if you must (but I doubt you will need that just to run a game server)

---

### Post by abaki on 2015-05-07
> **mastablasta said:**
> you should use root on server. Once I got is sort of secured and opened it to internet I immediately got attacked by the Chinese. luckily they tried to break in as root and using brute force attacks to guess a password.

I would say do some reading, avoid the desktops, use a good webgui if you must (but I doubt you will need that just to run a game server)

thanks for advice. 

i manage to most of my goals but didnt manage to start the windows game in winehq. i couldnt find many tutorial and blog post just one or two. they give instructions for different games and its really to hard to understand. i start to read winehq documentations. 

but its really hard and i could stop using linux just for lack of information :( i found a guy who accomplished to start the game in linux but he didnt help me :( i really dont know what to do. i am tired.

i will try tomorrow too. i hope i can do this.

---

### Post by sandyd on 2015-05-07
What game are you attempting to run - Wine runs *some* windows programs, but not all.

---

### Post by mastablasta on 2015-05-08
> **abaki said:**
> thanks for advice. 

i manage to most of my goals but didnt manage to start the windows game in winehq. i couldnt find many tutorial and blog post just one or two. they give instructions for different games and its really to hard to understand. i start to read winehq documentations. 

but its really hard and i could stop using linux just for lack of information :( i found a guy who accomplished to start the game in linux but he didnt help me :( i really dont know what to do. i am tired.

i will try tomorrow too. i hope i can do this.


that should be "you should NOT use root on server". made a mistake.

not all games/programs work in wine. if you want help you do need to at least tell us what game it is. also sometimes windows games have "server version" that would work in Linux.

also for windows games windows is almost always the best option. i think no one here would think less of you if you decide to use it. many of us do.

---

### Post by abaki on 2015-05-08
the game is RUST
here is the steps to run a windows server : [https://developer.valvesoftware.com/wiki/Rust_Dedicated_Server](https://developer.valvesoftware.com/wiki/Rust_Dedicated_Server)

windows server are too much expensive :(

how can i run this ? on winehq ?

---

### Post by sandyd on 2015-05-08
Do the instructions on [http://murtal.no-ip.org/projects.html](http://murtal.no-ip.org/projects.html) help?

---

### Post by abaki on 2015-05-11
> **sandyd said:**
> Do the instructions on [http://murtal.no-ip.org/projects.html](http://murtal.no-ip.org/projects.html) help?

thanks a lot

i have been llearning and get stuck here : cant download monds in that site

i use : wget -x --load-cookies cookies.txt [http://oxidemod.org/downloads/oxide-for-rust-experimental.714/download?version=4894](http://oxidemod.org/downloads/oxide-for-rust-experimental.714/download?version=4894)

i get 403 forbidden error 

i search net try solutions nope didnt work
[http://kb.kristianreese.com/index.php?View=entry&EntryID=150](http://kb.kristianreese.com/index.php?View=entry&EntryID=150)

---

### Post by abaki on 2015-05-11
[http://superuser.com/questions/509753/how-to-get-past-the-login-page-with-wget](http://superuser.com/questions/509753/how-to-get-past-the-login-page-with-wget)

i tried too but nope :(

---

### Post by sandyd on 2015-05-12
> **abaki said:**
> thanks a lot

i have been llearning and get stuck here : cant download monds in that site

i use : wget -x --load-cookies cookies.txt [http://oxidemod.org/downloads/oxide-for-rust-experimental.714/download?version=4894](http://oxidemod.org/downloads/oxide-for-rust-experimental.714/download?version=4894)

i get 403 forbidden error 

i search net try solutions nope didnt work
[http://kb.kristianreese.com/index.php?View=entry&EntryID=150](http://kb.kristianreese.com/index.php?View=entry&EntryID=150)

Do you have a login/password for oxidemod.org - you apparently have to set that at the begining of the script.

---

### Post by mastablasta on 2015-05-12
yeah. I also get that when trying to access the link in windows: "You must be logged-in to do that." so somewhere oyu forgot to set up your password. if it's a one itme download you can download it on another PC and then move it to your server.

wget is a nice utility that connects to website & downloads files on it. you can use it on windows as well. wget gui for the gui version. just be reasonable when downloading larger files or websites :)

---

### Post by abaki on 2015-05-12
i found after 4 hours searching. i was skipping some lines :(

i really liked linux and i want to learn more and more

so i will look posdata for cURL

---

### Post by abaki on 2015-05-15
hi idk how i made this but i m getting an error :

Warning: running as root
Entering daemon mode; any further errors will be reported to:
  /home/oynadi/.xpra/:100.log
oynadi@oynadi:/home/steam/rust$ sudo xpra stop :100


Warning: running as root
connection failed: [Errno 2] No such file or directory
oynadi@oynadi:/home/steam/rust$

game doenst start

xpra doesnt stop or exit info etc nay commands doesnt work

---

