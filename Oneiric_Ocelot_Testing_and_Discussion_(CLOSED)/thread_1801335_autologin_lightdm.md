---
title: "autologin lightdm?"
date: 2011-07-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by loukingjr on 2011-07-10
was just curious if it's possible to autologin lightgm and what I have to change in /etc/lightdm/lightdm.conf to make it work.

---

### Post by Bowmore on 2011-07-10
Uncomment these two lines in /etc/lightdm/lightdm.conf
```
#default-user=bob
#default-user-timeout=5
```and replace *bob* with your user name and set timeout to 0

---

### Post by loukingjr on 2011-07-10
> **Bowmore said:**
> Uncomment these two lines in /etc/lightdm/lightdm.conf
```
#default-user=bob
#default-user-timeout=5
```and replace *bob* with your user name and set timeout to 0
okay, uncommenting just those two lines doesn't work for me. I don't know if it's because I have 11.10 installed as a guest in VirtualBox or not. everything in my lightdm.conf file is commented out except for the two you said to change. I assume that is part of the problem.

edit: btw, there are two different places in lightdm.conf with those lines. the seat configuration section and the seat-0 section

---

### Post by Xgen on 2011-07-10
The previous change works for me too, but you might try changing the pam service line to:
pam-service=lightdm-autologin

---

### Post by loukingjr on 2011-07-10
well, it's not working for me. in which section did you make the change? and is everything else commented out in your lightdm.conf file or not?

---

### Post by jerrylamos on 2011-07-10
I'm running Live right now which is different for logins, but try System Settings, User Accounts.  There's a line there that says Automatic Login On/Off.

I use the configuration files where the menu's don't work or are cumbersome, example "Update" has royally screwed me so I use either command line sudo aptitude update, sudo aptitude upgrade or else sudo apt-get update, sudo aptitude upgrade.  I do edit configuration files like /etc/samba/smb.conf.

Just when I get it figured out it will change....

Jerry

---

### Post by Bowmore on 2011-07-10
System Settings, User Accounts only works for GDM atm.

One has to edit lightdm.conf that way said by Robert Ancell and also done when selecting autologin at installation. So check that again.

---

### Post by Xgen on 2011-07-10
[http://paulscomputernotes.blogspot.com/2011/07/autologin-and-startup-apps-from-command.html]("http://paulscomputernotes.blogspot.com/2011/07/autologin-and-startup-apps-from-command.html")

...and no, I left everything else as default.

---

### Post by loukingjr on 2011-07-10
well, all I can say is, I actually had found all the info people have passed along before I ever wrote this post. it didn't work for me which is what motivated the post in the first place. all I can think of is, it doesn't work as expected because I have it installed in VirtualBox. plus as I keep saying, everything in my lightdm.conf is commented out including things that define the default session etc. maybe I will ask on the VB forum. 

thanks for trying to help all. I do appreciate it.

---

### Post by VinDSL on 2011-07-10
Hrm...

I was having the exact opposite problem.  LoL!

When I installed A1, I decided to try autologin.  Big mistake!

It took a long time to figure out that lightdm.conf was controlling it.

These are the entries that were responsible for autologin. i.e. created by the Live-CD installer:
```

default-user=vindsl
default-user-timeout=0
pam-service=lightdm-autologin

```

These are the entries that got rid of autologin, e.g. return to normal login: 
```

default-user=
default-user-timeout=5
pam-service=lightdm

```

Extrapolate backwards...  ;)

---

### Post by loukingjr on 2011-08-01
there no longer seems to be a /etc/lightdm/lightdm.conf (xubuntu daily build 7/31), so now how does one autologin?

---

### Post by sgage on 2011-08-01
> **loukingjr said:**
> there no longer seems to be a /etc/lightdm/lightdm.conf (xubuntu daily build 7/31), so now how does one autologin?
You can import the template from /usr/share/doc/lightdm and modify as needed (or you can just create one from scratch).

---

### Post by loukingjr on 2011-08-01
> **sgage said:**
> You can import the template from /usr/share/doc/lightdm and modify as needed (or you can just create one from scratch).
I tried copying the one from /usr/share/doc/lightgm. there was no "default user=" etc so I added the two lines that are suppose to work with no luck.

---

### Post by sgage on 2011-08-01
> **loukingjr said:**
> I tried copying the one from /usr/share/doc/lightgm. there was no "default user=" etc so I added the two lines that are suppose to work with no luck.

Try un-commenting these lines to [SeatDefaults] (or adding them if they're not there), and adapting as necessary. 

```
autologin-user=(your login name)
autologin-user-timeout=0
```

It worked for me. I had already made that edit, but then ran across the "default user", etc. tip so I made that edit as well. Bad troubleshooting - changed too many variables at once. :KS

Now I have commented out the "default user" stuff, and autologin still works.

---

### Post by loukingjr on 2011-08-01
I actually tried that first. it seemed the /etc/lightdm/lightdm.conf file was overwritten. I had uncommented the two autologin lines, added my user name, rebooted, got the login screen. when I looked at the lightdm.conf file the autologin lines were commented again.

---

### Post by sgage on 2011-08-01
> **loukingjr said:**
> I actually tried that first. it seemed the /etc/lightdm/lightdm.conf file was overwritten. I had uncommented the two autologin lines, added my user name, rebooted, got the login screen. when I looked at the lightdm.conf file the autologin lines were commented again.

That's odd... Did you purge/reinstall lightdm? Did you uncomment in the actual [SeatDefaults] section or in the description of SeatDefaults above it? 

I'd give it another try...

---

### Post by drs305 on 2011-08-01
Here are the steps I took, via the command line, to get oneiric to autologin:
Change the ***username***.
The sed commands could be shorter but for clarity I leave them as is and they work.
```
sudo -i
if [ -f /etc/lightdm/lightdm.conf ]; then cp /etc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf.orig; fi
if [ ! -f /etc/lightdm/lightdm.conf ]; then cp /usr/share/doc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf; fi

sed -e 's|#greeter-session=example-gtk-gnome|greeter-session=lightdm-gtk-greeter|' -i /etc/lightdm/lightdm.conf
sed -e 's|#autologin-user=|autologin-user=***[COLOR="Red"]username[/COLOR]***|g' -i /etc/lightdm/lightdm.conf
sed -e 's|#autologin-user-timeout=0|autologin-user-timeout=0|g' -i /etc/lightdm/lightdm.conf
exit

```
It's easy to make the above a script for the next time. ;-)

Notes Added: I'm using lightdm-gtk-greeter

---

### Post by loukingjr on 2011-08-01
well, nothing is working. my install is from the 7/31 daily build. everything in the lightdm.conf file is commented out except now...
autologin-user=louis
autologin-user-timeout=0

I noticed this right below the previous line. ..
#autologin-session=UNIMPLEMENTED

in the login screen I notice that there is no default session and I have to choose it every time I log in.

---

### Post by loukingjr on 2011-08-01
well, nothing is working. my install is from the 7/31 daily build. everything in the lightdm.conf file is commented out except now...
autologin-user=louis
autologin-user-timeout=0

I noticed this right below the previous line. ..
#autologin-session=UNIMPLEMENTED

in the login screen I there is no default session and I have to choose it every time I log in.

edit: could one of the moderators delete one of these? thanks

---

### Post by drs305 on 2011-08-01
> **loukingjr said:**
> well, nothing is working. my install is from the 7/31 daily build. everything in the lightdm.conf file is commented out except now...
autologin-user=louis
autologin-user-timeout=0

I noticed this right below the previous line. ..
#autologin-session=UNIMPLEMENTED

in the login screen I notice that there is no default session and I have to choose it every time I log in.

Did you also change/uncomment: 
> greeter-session=lightdm-gtk-greeter
You may need to check to make sure *lightdm-gtk-greeter* is installed. I think there was a short period where it was being dropped from the installation but I haven't had to manually add it lately.

Having those three lines uncommented, using Unity and lightdm, works for me. The "UNIMPLEMENTED" line remains commented in my conf file.

Note: Duplicate post deleted per your request.

---

### Post by loukingjr on 2011-08-01
here's my /etc/lightdm/lightdm.conf...
```
#
# General configuration
#
# start-default-seat = True to always start one seat if none are defined in the configuration
# greeter-user = User to run greeter as
# minimum-display-number = Minimum display number to use for X servers
# minimum-vt = First VT to run displays on
# user-authority-in-system-dir = True if session authority should be in the system location
# guest-account-script = Script to be run to setup guest account
# log-directory = Directory to log information to
# run-directory = Directory to put running state in
# cache-directory = Directory to cache to
#
[LightDM]
#start-default-seat=true
#greeter-user=lightdm
#minimum-display-number=0
#minimum-vt=7
#user-authority-in-system-dir=false
#guest-account-script=guest-account
#log-directory=/var/log/lightdm
#run-directory=/var/run/lightdm
#cache-directory=/var/cache/lightdm

#
# Seat defaults
#
# xserver-command = X server command to run
# xserver-layout = Layout to pass to X server
# xserver-config = Config file to pass to X server
# xdmcp-manager = XDMCP manager to connect to
# xdmcp-port = XDMCP UDP/IP port to communicate on
# xdmcp-key = Authentication key to use for XDM-AUTHENTICATION-1 (stored in keys.conf)
# xsessions-directory = Directory to find X sessions
# xgreeters-directory = Directory to find X greeters
greeter-session=lightdm-gtk-greeter 
# greeter-hide-users = True to hide the user list
# user-session = Session to load for users
# allow-guest = True if guest login is allowed
# guest-session = Session to load for guests (overrides user-session)
# session-wrapper = Wrapper script to run session with
# autologin-guest = True to log in as guest by default
# autologin-user = User to log in with by default (overrides autologin-guest)
# autologin-user-timeout = Number of seconds to wait before loading default user
# autologin-session = Session to load for automatic login (overrides user-session)
#
[SeatDefaults]
#xserver-command=X
#xserver-layout=
#xserver-config=
#xdmcp-manager=
#xdmcp-port=177
#xdmcp-key=
#xsessions-directory=/usr/share/xsessions
#xgreeters-directory=/usr/share/xgreeters
greeter-session=lightdm-gtk-greeter
#greeter-hide-users=false
#user-session=default
#allow-guest=true
#guest-session=UNIMPLEMENTED
#session-wrapper=lightdm-session
#autologin-guest=false
autologin-user=louis
autologin-user-timeout=0
#autologin-session=UNIMPLEMENTED

#
# Seat configuration
#
# Each seat must start with "Seat:".
# Uses settings from [SeatDefaults], any of these can be overriden by setting them in this section.
#
#[Seat:0]

#
# XDMCP Server configuration
#
# enabled = True if XDMCP connections should be allowed
# port = UDP/IP port to listen for connections on
# key = Authentication key to use for XDM-AUTHENTICATION-1 or blank to not use authentication (stored in keys.conf)
#
# The authentication key is a 56 bit DES key specified in hex as 0xnnnnnnnnnnnnnn.  Alternatively
# it can be a word and the first 7 characters are used as the key.
#
[XDMCPServer]
#enabled=false
#port=177
#key=

```doesn't work. and lightsm-gtk-greeter is installed

---

### Post by foxy123 on 2011-09-18
What about time-out. I've got three users on my laptop and I want make one of them auto login, but I need 10 sec time-out before that so if other users are using the laptop they could log in. I tried 
```
autologin-user-timeout=0
``` but it does not work and the laptop goes straight to the autologin account without a pause.

---

### Post by buntu63 on 2011-09-18
> **Xgen said:**
> [COLOR=Blue]*Ubuntu*[/COLOR]: [COLOR=Red]11.10 11.04 10.10[/COLOR]

wow dude! speechless...u should change to an advance distro like [COLOR=Blue]**Arch...**[/COLOR]

---

### Post by cariboo on 2011-09-18
> **buntu63 said:**
> wow dude! speechless...u should change to an advance distro like [COLOR=Blue]**Arch...**[/COLOR]

What does this comment have to do with autologin? There are many users that have multiple versions of Ubuntu running. Arch, although it is a good system doesn't fit everyones way of doing things and isn't relevant here.

---

