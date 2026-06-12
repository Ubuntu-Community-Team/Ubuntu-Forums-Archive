---
title: "Live CD Issues"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by SirNobody on 2008-07-31
Hi.... I didn't know where else to ask... so I'm hoping this is the right place! OK so here's an issue I encountered today in the morning, I tried booting off an Ubuntu Hardy Heron Live CD, the bootup went perfectly...it worked fine too....I was playing around with the appearance settings and stuff....i wanted to get admin privileges so I made a new acccount with admin rights....but I was still using the Live User account!

In the Live User account the advanced effects were working nicely..all the window wobbles and stuff....however when i switched to the account I just created (the admin one)...the first thing I noticed was that the effects were gone...when I went in through Appearance settings and tried enabling the advanced effects...I was told "Effects could not be enabled!"

So wat gives? Any help? I liked those efects...:(...I know its probably summin utterly simple...so I'll be real grateful if somebody could walk methrough with what it is that I goofed up with!

Thanks!!

---

### Post by Tsarj on 2008-07-31
Well you could try going to Applications > Add/Remove... > Select Other > and you'll see Advanced Desktop Effects Settings. Install that and then under System > Preferences > Advanced Desktop Effects Settings, you can set all that up under there.

---

### Post by SirNobody on 2008-07-31
Thanx for the prompt response....but I'm a little confused...when you say INSTALLED..do u mean i need to download it first...because I'm using it on my laptop and I use a USB modem...and altho I saw some tutorials on how to use it with Linux (i have the drivers for Vista)..I havent yet managed to secure myself a connection!

---

### Post by bodhi.zazen on 2008-07-31
Ubuntu uses sudo and on the live CD the user is called "ubuntu" with a blank (empty) password.

So for admin access, just hit enter

sudo command

gksu nautilus

sudo -i

and on ....

[uhelp]community/RootSudo[/uhelp]

---

### Post by SirNobody on 2008-07-31
AHHH i get it now....no wonder i kept getting an Authorization Failed message when i tried running sudo with root... so silly of me! But wat about the accounts I create...im presuming they obviously dont count because once the CD is out...the system's back to normal right? So if i want admin access i need just use sudo wid a blank password?

Hmm...maybe now i'll get this modem working! Im working on something in Vista here so once I'm done with that I'll try going back into Ubuntu and I'll post my progress (and hopefully get some more help..)

Thanks a ton!

---

### Post by SirNobody on 2008-07-31
Ok back with some more wierd issues....like I said earlier, Im tryin to follow this little tutorial to get my USB modem working on Ubuntu...I'll copy past the instructions so its easier to understand my problem -

Open a terminal window.
Log in as root, i.e. type “su -” sans the quotes and enter the root password.
Then use vi to edit/create the following file “/etc/wvdial.conf”.
Enter the following text into it.
[Modem0]
Modem=/dev/ttyUSB0
Baud=115200
SetVolume=0
Dial Command = ATDT
init1=ATZ
init2=AT+CRM=1
FlowControl= Hardware (CRTSCTS)
[Dialer tata]
Username= internet
Password= internet
Phone=#777
Stupid Mode= 1
Inherits = Modem0

OK so i managed to get root on the terminal thanks to bodhi's comment earlier....now the thing with Vi...i know its a CLI text editor... i tried typing in vi followed by the name of the file....but nothing seemed to be happening....so i located the file using the file browser and opened it with the default text editor...i made the changes required therein but once I tried saving the file...i got an error message sayin..."You do not have the permission to change this file" and something else along with it about Correct Locations or something..... so im bak to square one....how am I supposed to convince that editor that I AM the administrator..... this is obviously very unlike the concept of admin in d Windows world... here u reach root in the terminal but are still denied permission to change a file!

Any help would be greatly appreciated as I really need to get that thing working on Ubuntu so i can access the 'net.

---

### Post by hyper_ch on 2008-07-31
if it works so wonderful why don't you just install it? ;)

---

### Post by SirNobody on 2008-07-31
All sarcasm aside...because I'm still apprehensive as to whether to commit myself full time to it....or just use it like i have in the past - as a means of taking backups when Windows decides to flip out on me, and i realize there is that ONE file i put in there right before disaster struck!

Sarcasm is a powerful tool...but dont go using it on every clueless guy just because you know something better then him...especially if the other guy is asking for help, not bragging about his own self proclaimed profficiency!

But thanx for reminding me every forum has its share of EXTREMELY HELPFUL people...pretty much like you!

---

### Post by hyper_ch on 2008-07-31
you can dual-boot... make 10gb available and have a go :)

---

### Post by SirNobody on 2008-07-31
Guess I will once i'm a lil bit more comfortable, but i want to figure out my initial problems with the live CD! Think you could help me with that?

---

### Post by hyper_ch on 2008-07-31
what initial problems?

---

### Post by SirNobody on 2008-07-31
Like why is it that I cant change a certain read-only file...i mean i know i have to be root...but i used sudo -i in the terminal and the prompt showed root...but obviously I'm not because I cant save dat file after making changes...says I dont have the permission to...and unless i change that file I cant get net connectivity on the laptop....its a USB modem that uses custom drivers in Vista...but apparently Linux handles it natively with a little bit of tinkering!

---

### Post by hyper_ch on 2008-07-31
well, as "normal" user you should not have rights to mess with the system. And as drivers are system-wide settings you normally don't have rights to mess with them. So you need root privileges.

---

### Post by SirNobody on 2008-07-31
Precisely. So how do i go about gaining root privileges? If i sign in with the default "ubuntu" user....im obviously a normal user....and if i create a new account with admin privileges through the Users And Groups panel, i still can't seem to have permissions to change that file...any help? Please!

---

### Post by hyper_ch on 2008-07-31
if you login as normal user (well, this does not count for the live cd) then you assume temporary root privileges by prepanding every command with
```

sudo

```
(or gksudo for graphical programs)
e.g.
```

gksudo gedit /etc/some_config_file.conf

```
You will be prompted for your USER password then.
For 15 or 20 minutes you can run another sudo/gksudo command in the same termianl and not be prompted again for the password.

OR

you could issue
```

sudo -i

```
that will take you into "root mode" and you can just execute all the commands then with root privileges. You leave that state by issuing
```

exit

```

On the live cd it's somewhat different.

---

### Post by SirNobody on 2008-07-31
So assuming i use sudo -i ....can i navigate to the .conf file with the file browser, double click on the file to open it, make changes and then be able to save it? And does it give me the authority to change the permissions on read-only files? Not that i'll be going messing with things i dont understand just so i know!

---

### Post by hyper_ch on 2008-07-31
sudo -i is for the terminal.... you can't navigate areound and click files ;) you'd need to start a file manager with gksudo

---

### Post by SirNobody on 2008-07-31
OK i kno im probably gettin irritating now, but how do i start a file manager with gksudo? N wat file manager do i usei mean..i dunno...wat is it called?

I'm sry if i'm pestering now....i jus really want to get this damn USB modem working with Linux... and then i'll install it on dual boot! I want to be able to learn to use Ubuntu on Ubuntu itself (dunno if that makes sense) i mean not restarting every thirty minutes to try out something because the net only works on Vista....and no right now I dont have any other comps around to be reading stuff on....dilemma!!

---

### Post by SirNobody on 2008-07-31
Alright thanks to all those who helped, I managed to get online....and yea thanx a ton hyper_ch.... and sorry for being slightly rude....i did finally figure out what you meant by running a file manager with gksudo....i thought i had heard of Nautilus before...so i just went ahead and typed it out and voila - root! Im typing this out on Linux....didn't think I'd get it working, but thanks to you guys i finally did!

Thank you soo much!!

Now to install it....a little scared about the partitions bit I dunno how Linux handles partitions....but I'll figure it out now!

You must've guessed...am quite happy I got it working, so thanks once again! :):):)

---

### Post by bodhi.zazen on 2008-07-31
Look at all the time and effort you are putting into maintaining Windows ....

If you put the same time an effort into maintaining Ubuntu I think it will pay of in spades, although there is an initial learning curve, in the long run many people find Ubuntu is more reliable and less vulnerable to viruses and other malware.

Obviously every OS has advantages and disadvantages and Ubuntu is not for everyone. If you decide Ubuntu is not for you, you will at least find it easier to maintain windows with Ubuntu.

Thanks [hyper_ch]("http://ubuntuforums.org/member.php?u=122588") for the time and effort you put into this thread.

---

### Post by SirNobody on 2008-08-01
Actually im finding Ubuntu good fun... plus I really wanna try out those fancy Compiz effects too..lol... but jokes aside....anything that feels zippy on a 5 year old laptop...IM SOLD! I saw it first on a friend's laptop...which is 5 years old and it runs pretty good...so i thought of trying it out on mine..and works like a charm! Thank u guys!

I might never completely switch because of all the gaming and 3D design work i do...but its a good experience nonetheless!

---

