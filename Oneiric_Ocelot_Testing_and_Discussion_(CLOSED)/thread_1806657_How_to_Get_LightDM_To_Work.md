---
title: "How to Get LightDM To Work"
date: 2011-07-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cg2916 on 2011-07-18
I just upgraded my Lubuntu from 11.04 to 11.10. I decided to install LightDM. Now, when I log in, I just get a cursor and a desktop background, I'm guessing it didn't start correctly.

Someone told me that you are supposed to edit the lightdm.conf with the user-session and default-user or something like that. Can someone help me?

---

### Post by garvinrick4 on 2011-07-18
Install a theme I hope lubuntu uses this one if not find one. "aptitude show lightdm-greeter" a list should be shown.
```
sudo apt-get install lightdm-greeter-example-gtk
```#Use tty
Ctrl/alt/F1
login
install theme per code:
sudo stop gdm 
sudo start lightdm

---

### Post by rburkartjo on 2011-07-18
gar,tks for posting

---

### Post by cg2916 on 2011-07-18
It says lightdm-greeter-example-gtk is already installed.

---

### Post by garvinrick4 on 2011-07-18
So did you open a tty
Ctrl/alt/F1
login
sudo stop gdm
sudo start lightdm
should go to login screen

---

### Post by cg2916 on 2011-07-18
> **garvinrick4 said:**
> So did you open a tty
Ctrl/alt/F1
login
sudo stop gdm
sudo start lightdm
should go to login screen
I can get to the login screen and log in, but after that I get nothing.
It says there is no gdm and lightdm is already running.

---

### Post by garvinrick4 on 2011-07-18
what are you running in lubuntu, Unity interface maybe?
```
unity --reset
```Or you could try:
```
sudo session lightdm restart
``` does gdm work but not lightdm?
sudo stop lightdm
sudo start gdm

---

### Post by cg2916 on 2011-07-18
> **garvinrick4 said:**
> what are you running in lubuntu, Unity interface maybe?
```
unity --reset
```

Or you could try:
```
sudo session lightdm restart
```

If you are running a Classic Gnome does gdm work but not lightdm?
sudo stop lightdm
sudo start gdm

I was using whatever came with Lubuntu, I guess Openbox. I don't think I have Unity, my computer couldn't handle it. I don't have GNOME.

---

### Post by cg2916 on 2011-07-18
> **garvinrick4 said:**
> what are you running in lubuntu, Unity interface maybe?
```
unity --reset
```Or you could try:
```
sudo session lightdm restart
``` does gdm work but not lightdm?
sudo stop lightdm
sudo start gdm

I start lightdm, and it says Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions? Even though I'm in root and I'm using sudo.
I also used sudo start lxdm, and it starts, but nothing happens.

---

### Post by garvinrick4 on 2011-07-18
I just do not know enough about Lubuntu, lightdm is now the default in 11.10 ubuntu
and works mostly without a problem now. But seems there is more going on in Lubuntu 11.10
that I know nothing about. xldm I have never used so hopefully someone with Lubuntu
11.10 will jump in and help about installing lightdm on that system sorry I could not help
you with your Lubuntu install.
 > Even though I'm in root and I'm using sudo.
Do not use sudo if in root already.

---

### Post by garvinrick4 on 2011-07-18
There is a user named ranch hand that is online now lets see if he will help out I believe he
has lubuntu experience.

Have asked him to help out in this thread, I hope he can work it out for you.

---

### Post by cg2916 on 2011-07-18
Bump

---

### Post by Bowmore on 2011-07-18
Seems to be an undefined session issue.

So, try to login using option *Other...* and see to that you have the session *Lubuntu* selected.

---

### Post by terry_gardener on 2011-07-18
> **cg2916 said:**
> I just upgraded my Lubuntu from 11.04 to 11.10. I decided to install LightDM. Now, when I log in, I just get a cursor and a desktop background, I'm guessing it didn't start correctly.

Someone told me that you are supposed to edit the lightdm.conf with the user-session and default-user or something like that. Can someone help me?

i have recently installed the daily build and have the same problem as you. 

the way i am working around it at the moment is by autologon. 

edit the lightdm.conf file.

gksudo gedit /etc/lightdm/lightdm.conf 
find the lines 
default-user=bob
default-user-timeout=5 

uncomment out the 2 lines and then change the username bob to your username and change the timeout to 0 
 
save and exit. 

i just rebooted and then it was fine, you should be able to just restart lightdm using sudo session lightdm restart 

hope this helps.

---

### Post by ranch hand on 2011-07-18
I hate to be a disappointment but I know nothing at all about lightdm.  Seems to me to be another "fix" by Ubuntu for something that wasn't broken.

Lubuntu is a great OS and I hope it goes far.  It will be going there with out me though.  I have switched to Debian.

Thought I could use Stable for my secure use, Testing for my regular use and Ubuntu-testing for fun.  Debian Sid (unstable) and experimental are more fun.

Debian also does not assume that the "average" user must be protected from his/herself because he/she is an idiot.  They also actually work on outstanding bugs.

What this all boils down to is that I have not seen anything of lightdm except some screen shots.

I would, if having much trouble with it install Ldm or Gdm and use one of those.  Not sure how you make it the permanent choice but booting to recovery and the tty login and using "service ldm start"  or gdm3 (I think that is what is in the repo for Ubuntu) ought to work.

---

### Post by inportb on 2011-07-18
> **ranch hand said:**
> I would, if having much trouble with it install Ldm or Gdm and use one of those.  Not sure how you make it the permanent choice but booting to recovery and the tty login and using "service ldm start"  or gdm3 (I think that is what is in the repo for Ubuntu) ought to work.

*dpkg-reconfigure gdm* or *dpkg-reconfigure lxdm* should do the trick.

---

### Post by cg2916 on 2011-07-18
> **Bowmore said:**
> Seems to be an undefined session issue.

So, try to login using option *Other...* and see to that you have the session *Lubuntu* selected.

AHA! It works! Now, it gives me the option of Openbox session or Lubuntu. I thought Lubuntu was Openbox, which should I use?

---

### Post by inportb on 2011-07-18
Openbox is Openbox. Lubuntu is LXDE, which contains Openbox.

---

### Post by cg2916 on 2011-07-18
Can I just remove the Openbox session, since all it does is load up a black screen with a cursor?

---

### Post by inportb on 2011-07-18
It should not hurt either way.

---

### Post by Bowmore on 2011-07-18
Well, *openbox* session works too. That's what it is initially, a black screen with a cursor. What works is the right click menu. If you want a wallpaper you have to install such a manager, e.g *feh*. More to read [here]("https://help.ubuntu.com/community/Openbox"). But as said, openbox in not Lubuntu.

---

