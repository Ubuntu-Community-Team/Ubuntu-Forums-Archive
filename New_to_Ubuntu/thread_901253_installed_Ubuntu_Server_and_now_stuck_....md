---
title: "installed Ubuntu Server and now stuck ..."
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Low_E on 2008-08-26
I am working, as a volunteer, on a school-network. This network consist of about 100 pc's (running Win2K and WinXP) and a server.

The server we had, a home-made-linux-from-scratch-thing, gave us many problems. It was running a domain for our windows-clients but stalled frequently, making it impossible for all pc's to log in on the domain and run netwerk-shared-applications.
Also the person that made and configured this server, doesn't help us no longer.

I would like to switch to a new distro, where we can tune everything ourselves, based on a stable platform and that is why I installed Ubuntu Server on our server-pc. (I previously switched the hard drive, so that I can always return to the previous situation in case of disaster.

My problem is that I am only an amateur in IT, have some experience in WInows-networking, but am very noob in Linux ... and I'm stuck now.
The Ubuntu-server was installed, but only detected 1 networkadapter in stead of the two there are.
So I wanted to add this eth0 and runned "vi /../interfaces"
but wasn't able to.

I am NOT looking for exact answers. Just some good directions, so that I can find the solutions myselve are ok, + I learn most this way ... but unfortunatly Time is running short and I do not have the time to do extensive research.
SO please give me some tips:

first question: how can I override the read-only-settings of these conf-files?

second: can I ad this extra eth-card, just by adding the settings in de interfaces-file?
The two eth-cards are identical (offc not the MAC-address), so it should not be a problem about drivers.

third question: in the UBUNTU Server-edition, there is no Graphical interface installed.
I think working in the console is GREAT, ... but not so easy when you do not know the commands and where to look or search. This is kinda easier when running a graphical interface.

I tried startx and got a message to apt-get a xinit-thing, which I did, but the X is still not running

Alldough I selected the correct country and language-settings in teh installation-screens, the server now suddenly runs a different keyboard-layout.
I got used to typing QWERTY on an AZERTY-keyboard but it is not very easy .. AND .. I am now unable to log in on the root-account (it has a difficult password with é"#-@ things)
How can I correct this?

Any help will be GREATLY appreciated!


Ludo

ps: strange thing, alldough I encoutered many problems so far, I really like the no-nonsens way of functioning of Linux.
I really want to make this work and learn a lot from it.

---

### Post by billgoldberg on 2008-08-26
> **Low_E said:**
> I am working, as a volunteer, on a school-network. This network consist of about 100 pc's (running Win2K and WinXP) and a server.

The server we had, a home-made-linux-from-scratch-thing, gave us many problems. It was running a domain for our windows-clients but stalled frequently, making it impossible for all pc's to log in on the domain and run netwerk-shared-applications.
Also the person that made and configured this server, doesn't help us no longer.

I would like to switch to a new distro, where we can tune everything ourselves, based on a stable platform and that is why I installed Ubuntu Server on our server-pc. (I previously switched the hard drive, so that I can always return to the previous situation in case of disaster.

My problem is that I am only an amateur in IT, have some experience in WInows-networking, but am very noob in Linux ... and I'm stuck now.
The Ubuntu-server was installed, but only detected 1 networkadapter in stead of the two there are.
So I wanted to add this eth0 and runned "vi /../interfaces"
but wasn't able to.

I am NOT looking for exact answers. Just some good directions, so that I can find the solutions myselve are ok, + I learn most this way ... but unfortunatly Time is running short and I do not have the time to do extensive research.
SO please give me some tips:

first question: how can I override the read-only-settings of these conf-files?

second: can I ad this extra eth-card, just by adding the settings in de interfaces-file?
The two eth-cards are identical (offc not the MAC-address), so it should not be a problem about drivers.

third question: in the UBUNTU Server-edition, there is no Graphical interface installed.
I think working in the console is GREAT, ... but not so easy when you do not know the commands and where to look or search. This is kinda easier when running a graphical interface.

I tried startx and got a message to apt-get a xinit-thing, which I did, but the X is still not running

Alldough I selected the correct country and language-settings in teh installation-screens, the server now suddenly runs a different keyboard-layout.
I got used to typing QWERTY on an AZERTY-keyboard but it is not very easy .. AND .. I am now unable to log in on the root-account (it has a difficult password with é"#-@ things)
How can I correct this?

Any help will be GREATLY appreciated!


Ludo

ps: strange thing, alldough I encoutered many problems so far, I really like the no-nonsens way of functioning of Linux.
I really want to make this work and learn a lot from it.

About the no GUI thing.

Do

sudo apt-get install ubuntu-desktop

That will install gnome for you.

You can always remove it, or only use it by typing "startx".

I don't know if gnome will start by default or not, you can change that behaviour.

--

You should really ask this question [here]("http://ubuntuforums.org/forumdisplay.php?f=339"), you'll get better answers.

---

### Post by croniksoft on 2008-08-26
If you want gnome to start up once you boot up your server all you have to do is install ubuntu-desktop and the gdm package

ex:

sudo apt-get install ubuntu-desktop
sudo apt-get install gdm

---

### Post by gkestrel on 2008-08-30
hi there to help you in your research take a look at the following article it has lots of good advice and step by step info on setting up ubuntu server.

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

if your using a different version they probably have a tutorial for your version too.

The reason you cannot edit the interfaces file is because you need to do it as sudo to have the permission to edit and save any changes.

before you start to edit the interfaces file, it is best to make a backup just in case things go wrong.

so type 

sudo cp /etc/network/interfaces /etc/network/interfaces.backup

this makes a copy of the interfaces file and calls it interfaces.backup

it will ask for your login password - type it in you, will not see the password on screen for security reasons - press enter after you have typed it in and the file will backed up.

Now to edit the /etc/network/interfaces file you need to use sudo in front of the command, for example i use nano to edit  my files so i would use

sudo nano /etc/network/interfaces

it will ask for your login password - type it in you, will not see the password on screen for security reasons - press enter after you have typed it in and the file will open in nano ready for editing

here is an example of my interfaces file

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0

iface eth0 inet static
address my ip address here
netmask 255.255.255.0
gateway my routers ip address here

i am using a static ip address

provided you are correct about both cards being identical try adding this for the second network card, make shure the ip address is different from the first network cards.

# The secondary network interface
auto eth1

iface eth1 inet static
address second ip address here
netmask 255.255.255.0
gateway my routers ip address here

to save the changes hold down the ctrl key and press o at the bottom you will see filename to save to /etc/network/interfaces - press enter to save the file.  Next hold down ctrl and press x to exit nano.

now you will need to restart networking in order for the changes to take place, so type

sudo /etc/init.d/networking restart

to edit your keyboard layout
edit your /etc/defaults/console-setup file

Find the following lines and change them according to your preference.

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="pc105"
XKBLAYOUT="uk"
XKBVARIANT=""
XKBOPTIONS="lv3:ralt_switch"

you might have to change the uk to what ever layout you want depending on the language you are wanting.

Save and reboot.

try that out and if you need further help dont hesitate to ask.

---

