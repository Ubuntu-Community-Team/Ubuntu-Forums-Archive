---
title: "First Step ... Crashed and Burned."
date: 2023-02-04
forum: New to Ubuntu
---

### Post by muzzmelbourne on 2023-02-04
Hi,

LINUX newbie here.

Just installed Ubuntu Server and everything seemed to go smoothly, no problems really.

First login attempt... "incorrect login"! Tried every conceivable combination of user name and password with no luck. Reinstalled the software twice paying particular attention to these items, still no luck.

Any ideas folks?

Cheers
Murray

---

### Post by TheFu on 2023-02-04
Well, since the installer has you enter the username and password, we can't possibly help if those are wrong.
If you think there's a default username/password combo, then you don't have an official Ubuntu Server install.

Are you doing something weird like running on Arm hardware, using Ubuntu Core or did you choose a non-English language/keyboard during install?


BTW, whenever posting any questions, we need the release number for the OS and if there's any desktop, the DE being used.

Someone new to Linux really shouldn't be using the text-only "Ubuntu Server" install.  Linux has a steep learning curve and most people new to it, even those planning to be Linux admins in the future, are better off starting with a GUI provided by a Desktop flavor install.  With Ubuntu Server, after you login, you are only going to see a plan black screen with 
```
~$
```
as the prompt. Do you know what to do with that?  Most admins don't admin their servers ON the machine. We connect over the network via ssh from a workstation with a GUI and use a terminal.  Ubuntu Server has NO GUI.

---

### Post by ajgreeny on 2023-02-04
You can try booting to recovery mode from the grub menu, assuming that you see that grub menu, and once into recovery mode you can check the username you will have chosen at installation simply with command ```
ls /home
```
If you do not normally see the grub menu keep repeatedly stabbing at Esc just after power-on if your machine uses UEFI, or hold shift if using legacy BIOS.

Can I also check that you used all lower case for the username when you set it up, as uppercase is not allowed, and that you're absolutely certain about your typing of your password?
If it becomes necessary you can reset the password again from recovery mode, but let's move one step at a time.

---

### Post by Impavidus on 2023-02-04
It's possible you ended up with the wrong keyboard layout, in particular if your keyboard isn't US-english. The layout used when entering the username will match the layout when entering the password, so you could check the keys used in the password when entering the username and make sure they give the intended characters.

---

### Post by muzzmelbourne on 2023-02-04
Sorry, v. 22.04.1 Ubuntu Server. Downloaded yesterday from this site. Flashed with balenaEtcher in (lastest)Ubuntu Desktop from the machine below.

MacBook Pro, Intel Core Duo i5 2.4Ghz, 16Gb RAM, 500 Gb SSD. Its old but I recently had it running Linux Mint Desk Top in Virtual Box 7.0 on MacOS Monterey via OCLP, so I'm sure it can run a text based server.

I chose an Australian keyboard layout, but as far as I'm aware, Aus and US are the same, but I'll do another full install and leave all the keyboard settings to default. Thanks.

Yup, fully aware of the CL environment. Spent years in MSDOS before Windows was even a thing. Command line's are my friend...

Yup, planning on admin remotely via my M2 MacBook Pro.

Cheers.

---

### Post by muzzmelbourne on 2023-02-04
> **ajgreeny said:**
> You can try booting to recovery mode from the grub menu, assuming that you see that grub menu, and once into recovery mode you can check the username you will have chosen at installation simply with command ```
ls /home
```
If you do not normally see the grub menu keep repeatedly stabbing at Esc just after power-on if your machine uses UEFI, or hold shift if using legacy BIOS.

Can I also check that you used all lower case for the username when you set it up, as uppercase is not allowed, and that you're absolutely certain about your typing of your password?
If it becomes necessary you can reset the password again from recovery mode, but let's move one step at a time.

Nah, no menus. Just the login prompt. I'll give Safe Mode a whirl though, thanks. I love 'stabbing' things...

Yeah, lower case user name and careful input of password. Would have expected a mismatch warning at setup if I made a mistake.

---

### Post by muzzmelbourne on 2023-02-04
> **Impavidus said:**
> It's possible you ended up with the wrong keyboard layout, in particular if your keyboard isn't US-english. The layout used when entering the username will match the layout when entering the password, so you could check the keys used in the password when entering the username and make sure they give the intended characters.

I'm pretty sure Aus and US keyboard layouts enter the same values, but part of my password is $ so maybe Linux thinks we use the British Pounds symbol.

As I said, I'll do a full reinstall. Might steer clear of $ in my password too(just thought of that when I typed it, mmmm).

Cheers.

---

### Post by muzzmelbourne on 2023-02-04
Ok, quick update.

Managed to login ok after full reinstall. Left keyboard to US and used "abc" as initial password(don't panic, its different now).

Even managed to SSH in from my remote M2 MacBook Pro.

Now, I can't get the password correct for the remote server login. Tried the password for my modem! Tried the password for user, even tried the password for the M2.

Do I need to setup the M2 as a recognised, trusted, client of the Ubuntu Server or something before I can SSH in?

Tips very much appreciated thanks.

Oh, by the by, managed to boot into GRUB on the old install. Was presented with a static grub prompt which, on my reading of help guides(thanks for the links ajgreeny), means GRUB was having trouble with/finding boot records. Anyway, nice to know about keyboard stabbing tips... Cheers.

---

### Post by TheFu on 2023-02-04
> **muzzmelbourne said:**
> Nah, no menus. Just the login prompt. I'll give Safe Mode a whirl though, thanks. I love 'stabbing' things...

Yeah, lower case user name and careful input of password. Would have expected a mismatch warning at setup if I made a mistake.

Nope.  The warning is generic for incorrect username and/or incorrect password.  Part of UNIX security is not to state the specifics for incorrect login attempts.  Remember, these systems are meant to be remotely accessed over the internet by anyone in the world.

---

### Post by TheFu on 2023-02-04
> **muzzmelbourne said:**
> Ok, quick update.

Managed to login ok after full reinstall. Left keyboard to US and used "abc" as initial password(don't panic, its different now).

Even managed to SSH in from my remote M2 MacBook Pro.

Now, I can't get the password correct for the remote server login. Tried the password for my modem! Tried the password for user, even tried the password for the M2.

Do I need to setup the M2 as a recognised, trusted, client of the Ubuntu Server or something before I can SSH in?
 

So, as for getting ssh working from other systems, start with basic troubleshooting.  [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

a) you must install an ssh package that contains the server if you want one.  That can be "ssh", which is a meta-package that includes the client AND the server AND the openssh-sftp-server, or you can install "openssh-server".  I always install ssh and fail2ban on all my systems at the same time. No need to allow remote brute force attempts.
b) is the sshd running?
c) can the remote client ping the ssh server machine ... by name, by dns-name or by IP?  If name resolution isn't working or you've incorrectly setup the VM networking (host-only or NAT), then you won't connect.  Fortunately, a reinstall isn't needed, just tweak the VM settings to "bridged" networking.
d) If the client workstation can ping the ssh server, then you'll want to setup ssh-keys.  Assuming Linux -to- Linux, you'll need the openssh-client package installed, then from the client, run these 2 commands:
```
   $ ssh-keygen -t ed25519
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@server

```
Replace your username and server as needed.
Some non-UNIX/non-Linux OSes don't have the 2nd command.  Life is too short to deal with ****** ssh client packages that lack something that has been part of ssh for 20+ yrs.  Once those 2 commands are run, you'll not need to enter your server password for ssh, scp, sftp, rsync, sshfs, and most backup tools to work.  There must be 50 other things that use libssh and they all honor ssh-keys.  This step is 1-time per server.  BTW, the keygen part only needs to happen once per client, but if you are connecting to different paying clients, you probably want to use different key-pairs for each. They only get the public key, so it isn't the end of the world if you don't bother, but ... good security practice is not to overshare.  NEVER, EVER, share any private keys of the system that created them. 
e) check that any firewalls in the way allow ssh ... if you haven't changed it from the default port.  I leave the default port on my LAN, but have my WAN router perform port translation from some high ports into LAN ssh servers.  I never have port 22/tcp open on the internet.  That's asking for full logs.
f) There are lots of security techniques for sshd.  Firewalls, slow connection requests, only allow passwords from know subnets/IPs, force the use of ssh-keys for everywhere else.  There are a few other things too, but I don't bother - like port knocking.

---

### Post by ne29914 on 2023-02-04
> **muzzmelbourne said:**
> but part of my password is $ 

How on earth did you think that would work? Even in DOS, $ was a restricted character. Man! And it wanders all over the keyboard depending on English/US/etc. layout.

---

### Post by TheFu on 2023-02-04
> **ne29914 said:**
> How on earth did you think that would work? Even in DOS, $ was a restricted character. Man! And it wanders all over the keyboard depending on English/US/etc. layout.

Actually, '$' character is fine in passwords.   Any character that can be typed is fine ... unless the programmer failed.  For logins, it isn't an issue.

---

### Post by muzzmelbourne on 2023-02-04
> **TheFu said:**
> So, as for getting ssh working from other systems, start with basic troubleshooting.  [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)


Wow, thanks. Quite a bit to go through there, I'll get onto it directly.

However, I installed OpenSSH on the server when Ubuntu was installed and, as you watch the progress of the installation, you can see the system generate and record the keys, so i'm confident the server keygen part is working and done its job.

I'm using a M2 MacBook Pro with Ventura 13.2 as the remote client and ran the native SSH keygen package through terminal and that seemed to go ok. I left both file saving paths to system defaults, so I assume they know where to find them.

I can actually connect remotely to the server from the client, I got the IP address from the server using "IP a" command. I get the server prompt on the client screen no problems, so i think the SSH side of things is working ok.

Its, once again, logging in thats the problem, in particular the password. IFAIK, there is, one for the server user, one for the client user, one for the WiFi, one for the LAN, and one for modem admin. The server's login prompt on the client seems correct, the server name and user. Its the password I can't get to work. None of the one's I listed works.

Thanks for your help, any more is much appreciated.

I'll get there eventually no doubt...

Cheers.

Correction: The client prompt is server@IP not server name and user. My bad...

---

### Post by muzzmelbourne on 2023-02-04
> **TheFu said:**
> Actually, '$' character is fine in passwords.   Any character that can be typed is fine ... unless the programmer failed.  For logins, it isn't an issue.

Awesome, I can go back to my favourite, generic, one.

Cheers.

---

### Post by muzzmelbourne on 2023-02-04
> **ne29914 said:**
> How on earth did you think that would work? Even in DOS, $ was a restricted character. Man! And it wanders all over the keyboard depending on English/US/etc. layout.

Fair point. You're right, I wasn't thinking. However, during the setup of the system files on installation there is a warning about acceptable/unacceptable characters for the user name but no such warning for creating a password. So, figured it was ok.

$ was fine in DOS as long as it was used in the right way. Very hard to setup a payroll batch file without it. Fair point though.

As for keyboard variations, surely a $ symbol is a $ symbol regardless of its physical keyboard or geographic location.

Cheers.

---

### Post by muzzmelbourne on 2023-02-04
> **TheFu said:**
> Nope.  The warning is generic for incorrect username and/or incorrect password.  Part of UNIX security is not to state the specifics for incorrect login attempts.  Remember, these systems are meant to be remotely accessed over the internet by anyone in the world.

Fair enough and understood.

I meant a mismatch warning at the point of creation, rather than login attempts. Sort of defeats the purpose of entering the chosen password twice if it doesn't report a mismatch at that point. You would expect that post setup, you would get the password right at login, especially after about 10 attempts.

Cheers.

---

### Post by muzzmelbourne on 2023-02-04
Ok, this is the error I'm getting when I enter the password.

[FONT=Menlo]Permission denied (publickey,password)[/FONT][COLOR=#000000][FONT=Menlo][FONT=arial]

[/FONT][/FONT][/COLOR] The client prompt, servername@IPaddress, seems to be ok.
[COLOR=#000000][FONT=Menlo][FONT=arial]
Cheers.
[/FONT]
[/FONT][/COLOR]

---

### Post by muzzmelbourne on 2023-02-05
Ok, final update. No progress. Access denied from client-server and server-client. Both display the remote system prompt and both deny access when their respective password's are entered.

VPN and A/V disabled, remote access and full disk access enabled and SSH module 'on' and running on the M2 MacBook Pro client and everything setup, including current SSH, on the x86 MacBook Pro server as per every bit of setup info and YouTube video I can find. The SSH fingerprints have been flagged and accepted in both directions. The IP addresses have been quadruple checked, and numerous reboots for both computers.

The server OS works fine, no problems scooting around directories and modifying config files.

As I said, I have a remote prompt in both directions, just can't get past the password stage.

Next step is to buy another ethernet cable and dongle for the M2(usb-c only standard) and connect them both to the modem directly rather than ethernet server and wifi client. Sorta defeats my objective though, not really 'remote' if they are wired to the same modem.

Anyway, thanks again folks.

I'll get there... eventually.

Cheers.

---

### Post by TheFu on 2023-02-05
> **muzzmelbourne said:**
> $ was fine in DOS as long as it was used in the right way. Very hard to setup a payroll batch file without it. Fair point though.

As for keyboard variations, surely a $ symbol is a $ symbol regardless of its physical keyboard or geographic location.

Unix isn't DOS.  They have very little in common.  Even the shells are different.  Don't make that mistake.  you'll do things the hard way if you do.  For example, MS-DOS/PC-DOS/DR-DOS used file extensions.  Linux/Unix doesn't.  They are handy for humans, but the OS doesn't care. Actually, the ".ext" doesn't have special meaning to the OS.  That's just for humans and some programs created by former MS-Widows people.  For example,
PDF files don't have to end in .pdf to work.  There's no ending required for executable programs ...  or we can make .pdf files executable and have programs.  The extension doesn't matter.
'ls *.*' isn't needed.
'ls *' means the same thing.
'evince *df' will open all files that end in df characters.    Or if you know the beginning character is an 'F' .... 'evince F*'  That's case sensitive, of course.

BTW, usernames should be lowercase - at least start with a lowercase 7-bit ASCII character, no spaces, "alpha-numeric" is the normal style.  We tend to use {initials}+{4 numbers} to randomize login names.  Those login names are never used in email correspondence, which gets [email]firstname.lastname@domain.com[/email] ... and {f-initial}{lastname}@domain.com aliases.  We don't want the usernames widely known outside the company.  Below are the "official" rules for usernames.  Just because a character can be created, that doesn't mean it won't have repercussions elsewhere.

Unix systems expect a smart admin.  The OS can't tell if things asked of it is genius or stupidity.  If you want to shoot yourself in the head and the OS can, then it will allow it. The user/admin is expected to be smart enough to not do bad things.  It isn't there to protect users.  If you want/need that, then you'll want a different OS.

Allowed passwords can be limited locally, but in general, anything a user can enter on a keyboard will be accepted.  The difficulty is in having the same keyboard on every system they may need to login from.  Limits on min/max length, words allowed, how often a password can be changed, etc. are all locally controlled. 

The useradd manpage says this:
```
CAVEATS
       You may not add a user to a NIS or LDAP group. This must be performed on the
       corresponding server.

       Similarly, if the username already exists in an external user database such as
       NIS or LDAP, useradd will deny the user account creation request.

       It is usually recommended to only use usernames that begin with a lower case
       letter or an underscore, followed by lower case letters, digits, underscores, or
       dashes. They can end with a dollar sign. In regular expression terms:
       [a-z_][a-z0-9_-]*[$]?

       On Debian, the only constraints are that usernames must neither start with a
       dash ('-') nor plus ('+') nor tilde ('~') nor contain a colon (':'), a comma
       (','), or a whitespace (space: ' ', end of line: '\n', tabulation: '\t', etc.).
       Note that using a slash ('/') may break the default algorithm for the definition
       of the user's home directory.

       Usernames may only be up to 32 characters long.

```

---

### Post by muzzmelbourne on 2023-02-05
> **TheFu said:**
> Unix isn't DOS.

Wonderful overview, thank you.

One of the things that has attracted me to Linux from day one is the 'maturity' it expects of its users and the flexibility it gives you to, as you say, "shoot yourself in the head" if so desired.

A good example of the 'great power = great responsibility' scenario, as I saw posted earlier.

Now, if I can resolve my remote login problem I can get down to some serious learning.

Do you think I should direct my questions/problems to a more specific forum sub-group or just keep posting here?

Thanks again for your help

Cheers

---

### Post by muzzmelbourne on 2023-02-05
[SIZE=3][FONT=lucida console][COLOR=#000000]Here is the [/COLOR][COLOR=#000000]screen image I am currently seeing... obviously redacted.[/COLOR]
[COLOR=#000000]
I have become aware of possible problems using SSH with MacOS Ventura 13.2. This feature is disabled by default for the first time in MacOS history for some reason. However, I have followed the procedure to enable it, and as you can see, I think the SS[/COLOR][COLOR=#000000]H is working, just not authorising access.[/COLOR][/FONT][/SIZE][COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Last login: Sun Feb  5 23:49:03 on console[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]murrayxxxxx@M2-MacBook-Pro-13 ~ % ssh esn/murray@xxx.xxx.x.xxx[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo](esn/murray@xxx.xxx.x.xxx) Password:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo](esn/murray@xxx.xxx.x.xxx) Password:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo](esn/murray@xxx.xxx.x.xxx) Password:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]esn/murray@xxx.xxx.x.xxx's password: [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Permission denied, please try again.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]esn/murray@xxx.xxx.x.xxx's password: [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Received disconnect from xxx.xxx.x.xxx port 22:2: Too many authentication failures[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disconnected from xxx.xxx.x.xxx port 22[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]murrayxxxxx@M2-MacBook-Pro-13 ~ % [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]

---

### Post by muzzmelbourne on 2023-02-05
Ok, this is getting ridiculous.

I now have 3 Mac computers setup. An x86 iMac 20(OSX 10.6.8), an M2 MacBook Pro(MacOS Ventura 13.2) and an x86 MacBook Pro(Ubuntu Server 22.04.1 LTS(?)). All running different OS's. All have fresh public and private SSH keys in the right directories. All SSH systems enabled.

All have problems connecting with each other. Various levels of progress with various combinations. All fail at password entry.

The only thing they have in common is the modem! TP Link Archer300. x86 MacBook Pro server is ethernet, others are WiFi.

Any chance this could be causing problems?

Slowly moving from an Ubuntu problem to a Mac vs. modem problem by the looks of it.

Any help greatly appreciated.

Cheers.

---

### Post by muzzmelbourne on 2023-02-05
_SOLVED_

UPDATE: Solved!

I have Tabby, a CLI app, that I played with 3 months ago but did nothing with really. 

Turns out, I setup a 'profile' in it for an old company I ran, that I was unaware of.  Seems this Tabby controls ALL command line interactions, including the system CLI, even when its not running. So, every time I went to SSH to my current setup Tabby was implementing an irrelevant set of login rules, which barred password logins. A quick 'profile' delete and a new one created and, bazinga, I was 'in'. Did a remote system reboot to check operations and all good. 

Totally stumbled across this problem/solution via accidental keystrokes at the command line.


Thanks for all your help folks.

Cheers

---

