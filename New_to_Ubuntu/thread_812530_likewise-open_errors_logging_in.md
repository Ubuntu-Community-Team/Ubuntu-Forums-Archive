---
title: "likewise-open errors logging in"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by mohenjo on 2008-05-30
I've been playing with an Ubuntu 8.04 laptop, attempting to get it connected up and working on the Win2k3 domain I run at work.  I recently learned of the likewise-open package which, once installed, worked like a charm.

However when I took the laptop  home to play around with it, I noticed a few bizarre things happened.  When I logged in as my normal user account (the account I was using prior to installing likewise) I got a dialog box that just said "Error" with an OK box, and it let me in.

When I attempted to change my static IP address, it asked for my password like it always does, but at that point the whole system froze up on me.  I honestly thought I brought my Windows BSOD powers with me to my new ubuntu box!

I managed to get myself into the System Log Viewer to take a look and see if I could find any hint of errors (I'm very new to the linux world), and the only things I could find was this section under auth.log:
```

May 29 19:37:50 ulaptop gdm[5505]: pam_lwidentity(gdm:auth): PAM config: global:krb5_ccache_type 'FILE'
May 29 19:37:50 ulaptop gdm[5505]: pam_lwidentity(gdm:auth): failed to get GP info
May 29 19:37:50 ulaptop gdm[5505]: pam_lwidentity(gdm:auth): getting password (0x00000000)
May 29 19:37:59 ulaptop gdm[5505]: pam_lwidentity(gdm:account): PAM config: global:krb5_ccache_type 'FILE'
May 29 19:37:59 ulaptop gdm[5505]: pam_lwidentity(gdm:account): cannot contact daemon
May 29 19:37:59 ulaptop gdm[5505]: pam_lwidentity(gdm:account): PAM config: global:krb5_ccache_type 'FILE'
May 29 19:37:59 ulaptop gdm[5505]: pam_lwidentity(gdm:account): cannot contact daemon
May 29 19:37:59 ulaptop gdm[5505]: pam_lwidentity(gdm:setcred): PAM config: global:krb5_ccache_type 'FILE'
May 29 19:37:59 ulaptop gdm[5505]: pam_lwidentity(gdm:session): PAM config: global:krb5_ccache_type 'FILE'
May 29 19:37:59 ulaptop gdm[5505]: pam_lwidentity(gdm:session): could not create home directory
May 29 19:38:59 ulaptop polkit-grant-helper-pam[6195]: pam_lwidentity(polkit:auth): PAM config: global:krb5_ccache_type 'FILE'
May 29 19:38:59 ulaptop polkit-grant-helper-pam[6195]: pam_lwidentity(polkit:auth): failed to get GP info
May 29 19:38:59 ulaptop polkit-grant-helper-pam[6195]: pam_lwidentity(polkit:auth): getting password (0x00000000)
May 29 19:39:03 ulaptop polkit-grant-helper-pam[6195]: pam_lwidentity(polkit:account): PAM config: global:krb5_ccache_type 'FILE'
May 29 19:39:03 ulaptop polkit-grant-helper-pam[6195]: pam_lwidentity(polkit:account): cannot contact daemon
May 29 19:39:03 ulaptop polkit-grant-helper-pam[6195]: pam_lwidentity(polkit:account): PAM config: global:krb5_ccache_type 'FILE'
May 29 19:39:03 ulaptop polkit-grant-helper-pam[6195]: pam_lwidentity(polkit:account): cannot contact daemon

```

To get around this, I ended up turning off the laptop, bringing it back up and running the "sudo domainjoin-cli leave" command to remove the laptop from the domain.  This cleared evrything right up.

I may not even have the setup done correctly for how I got the laptop to log into the domain.  Might there be another way to set the computer up so that it can log into the domain when I need it to, but be able to log in "locally" (in windows terminology) when not at work?

---

### Post by elperrillo on 2008-06-03
I am having the same exact issue... have you or anybody found a solution to this?

---

### Post by tact on 2008-06-03
There are a couple of bug reports on launchpad against likewise-open and policy kit.  

Yes if you do not "leave" the domain somehow the notion its connected, or supposed to be connected, to a domain persists even after reboots....and so when you log in and do not get a domain controller to auth the login an error box is displayed and you log into the local machine.

---

### Post by elperrillo on 2008-06-03
I thought that if you left likewise-open opened when logging off it would reconnect when you reboot, because when I opened after reboot it it was showing as "connected". 
If that is the case, and it does not really reconnect, I will turn it off before rebooting. 

One final question... What does logging in to the active directory of your domain gives you? I did not notice absolutely any difference after logging in. I still have to enter user name and password when accessing shared drives (I go right in with a Windows machine) Am I doing something wrong?

---

### Post by tact on 2008-06-03
I have never tried it out, to see if after logging into a domain, shutting down, and restarting, whether automatically back in the domain. (I doubt it.  Maybe will test when at the office later today).


"What does logging in to the active directory of your domain gives you?"

Thats a multilevel question.  :)   Not sure what level of answer you want.

First up - I am very inexperienced with likewise-open and even less experienced at manually setting up gnu/linux to authenticate to a domain.

My company is fully microsoft Active Directory domains etc and the company issued laptops all windowsXP.  So when I was using the standard kit domain joining was transparent.    

One fine day my XP laptop decided the HDD was unreadable.  Booting ubuntu liveCD could read the supposedly corrupted NTFS partitions and copy the data off to the corporate windows fileservers...  I installed linux and stayed that way for the past almost 2yrs.

So back to your question  -  "What does logging in to the active directory of your domain gives you (me)?"

In the above instance - nothing.  :)   I was doing very well without it for so long.  I could access company fileservers and fileshares and the internet from the corporate LAN just like any of my XP bound colleagues.  

- My XP colleagues have certain fileshares mounted as drives at bootup
--By setting up /etc/fstab appropriately I could have the same shares auto mount at bootup

- My XP colleagues had their "My Documents" folder auto-sunchronised with a copy on a file server every time they connect to the corporate LAN
-- I use (g)rsync to do the same

- My XP colleagues sometimes get surprises as sysadmins occasionally push corporate changes down to their machines.  (Like new signature blocks on email, or new document templates as corporate image changes etc)
-- I never get those surprises, pick and choose what I want installed/changed on my corporate laptop.

There was one issue I had browsing network shares when NOT logged into the domain.  If I just used nautilus (Places>Network...) to browse the corporate LAN.  After maybe 5-10 minutes my access would fail.  Cannot even get to my email account.  My whole network account had been auto-locked out.  I suspect because not authenticated on the domain the authentication servers picked up my going in and out of network folders and thought I was an intruder.  A phone call needed to the sysadmins to reset my account in moments each time.

No such problem occurred if I mounted the share with CIFS and then browsed with nautilus.  Only when I was "freely" browsing non-mounted shares - a rare event.

So thats why I kept an interest in being able to join the domain properly.  I gave up attempts to configure it manually myself.  When likewise-open turned up I gave it a try and seems to work nicely.

So answer 2 to your question:"What does logging in to the active directory of your domain gives you?"
-  It permits me to free-browse across all machines and unmounted shares in nautilus without fear my account might get locked out.
-  it seems that when I browse the network while authenticated to the domain I see more machines than when I am not part of the domain.  This may be due to better access to browse lists from servers(????)

---

### Post by tact on 2008-06-03
> **elperrillo said:**
>  I did not notice absolutely any difference after logging in. I still have to enter user name and password when accessing shared drives (I go right in with a Windows machine) Am I doing something wrong?

When you log in to your linux machine you use something like:
username:    [email]user@domain.name.loca[/email]l
Password:     [your password]

Is that correct?

---

### Post by tact on 2008-06-04
I just did some testing on the apparent persistence of domain membership after PC shutdown/restart.

Here are the steps I performed.
-Boot my laptop
-CTRL-ALT-F1 join the domain from command prompt
-CTRL-ALT-F7 login at GDM using "user@domain.company.local" then password
-Succeeded

-Shutdown laptop
-boot laptop
-at the GDM login as a local user "user" then "password"
small "ERROR" message, dismissed, logged in as local user.
-check likewise-open gui and it thinks I am on the domain as the option is to "disconnect" from the domain.

-Actually I was not on the domain at all.  So any hint of persistence across re-boots is, as expected, not correct.

Then to see what is needed to get an actual domain logon:
- logged out as local user
-CTRL-ALT-F1 to command prompt.  "/etc/init.d/likewise-open status" reports that likewise-winbindd is not running.   
-"/etc/init.d/likewise-open start" to get likewise-winbindd up
-CTRL-ALT-F7 back to GDM and login using "user@domain.company.local" and "password"
-Succeeded..    actually on the domain.  Not a false indication.

This brings to mnd the bug report I contributed to in launchpad...  
When installing likewise-open a bunch of links are placed in the startup directories of your system (/etc/rcx.d/) so that likewise-winbindd will start at system start.

I (still) find that every time I "leave" a domain all those links are deleted by some unknown process.  Next restart likewise-winbindd will not be auto started.  Need to recreate the links ($ sudo update-rc.d likewise-open defaults)

---

### Post by elperrillo on 2008-06-04
TACT:

First of all let me thank you for that very detailed explanation. I am also very new to the Linux world and know a little about everting but I am an expert in nothing. 

When I log in to the Ubuntu server that I have, I log in as root, and then I open Likewise and connect to the Active Directory, however I do not get the shared drives that everybody gets automatically when they sign on using windows and I still need to enter a logging name and password to enter network drives. 

I am really blind since I read many terminologies but I do not really know what they do, all I know is that they are realated to comunicating with a Windows network. (Winbind, Samba, NTLM, Kerberos) I try to use WEBMIN to make it easy for me to modify those conf files, however the terms are not explained properly, like for example they give you a field somewhere that says "IP of Machine" well is it the server? is the the Client? should I put IP, sould I put DOMAIN? Should I put DOMAIN.LOCAL, Should I put .Domain.local? Should I put it in CAPS should I do lowercase? and my whole day goes by in trial and error.

---

### Post by mohenjo on 2008-06-04
Tact, thank you for that reply.  That's exactly what I've continued to experience.  As was mentioned, I think it's just a bug in likewise.  Or, perhaps it's just how it was intended to operate.  Usually desktop computers are either always in a domain or always not in a domain.  The problem for me lies in having a laptop that I want to take home and use off-site and away from the domain.  Maybe likewise is not the program I should be using to manage my rather dynamic domain membership needs.

Anyways....thanks to all for the replies.

---

### Post by tact on 2008-06-04
> **elperrillo said:**
> TACT:

First of all let me thank you for that very detailed explanation. I am also very new to the Linux world and know a little about everting but I am an expert in nothing. 

When I log in to the Ubuntu server that I have, I log in as root, and then I open Likewise and connect to the Active Directory, however I do not get the shared drives that everybody gets automatically when they sign on using windows and I still need to enter a logging name and password to enter network drives. 

Hi there, 

Is your server up and connected 24/7 to the LAN?  I presume so.  In that case what you need to do is just get connected to the Domain once (using likewise-open) and then just log in and out of the server as you need.  (You would need to repeat this process every time you reboot your server.)

1.  power on your server
2.  at a command prompt login as a local user (root??  perhaps a local user and use sudo better?)
3.  run this command to see if likewise-winbindd is running
```
(sudo) /etc/init.d/likewise-open status
```4.  If likewise-winbindd is not running then
```
(sudo) /etc/init.d/likewise-open start 
```5.  Then join your machine to the domain
```
(sudo) domainjoin-cli join domain.name.local username
(replace "domain.name.local" and "username" appropriately)
```6.  Now log out (when you logged in above it was as a local user not a domain authenticated user)
7.  Now log back in using this format  [EMAIL="user@domain.name.loca"]user@domain.name.loca[/EMAIL]l

Now you are a domain authenticated user.  You can log out and in as much as you like (as domain authenticated user ("user@domain.name.local" then "password") or a local user ("user" then "password") so long as you do not explicitly run a command  "leave" the domain, or reboot the computer.

When you log in as a domain authenticated user ("user@domain.name.local") then you should have appropriate permissions everywhere as pas a windows user.   When you do a local logon ("user") even if that user is "root" - you do not have privs on the domain as you were not authenticated by the domain.

---

### Post by pwebster25 on 2008-06-05
This is starting to make sense to me.  I have been getting an error pop up every time I login to my ubuntu machine since I joined it to the domain with likewise.  I have just been putting in username and then password in the gui login screens.  I guess I need to put in [email]username@domain.msd.loca[/email]l

My domain is called MSD.  In likewise it says it is joined to MSD.domain

Do I need the local thing?

I also am on a laptop that goes back and forth.  On windows I just always log it in as into the domain and when I am at home it just doesn't find all the mapped drives it is looking for but does just fine.  Do I understand correctly from the other posts that this won't necessarily work?  I spend a significant amount of time working in both places.

After I get logged in with the error on login I have had problems authenticating my credentials when I want to change wireless settings (I have different wireless settings at home).  It freezes up when trying to authenticate in the network admin screen.

Thanks for your help.

---

### Post by pwebster25 on 2008-06-06
I am assuming that the case needs to be lower case when typing [email]username@domain.company.loca[/email]l

My domain name is called MSD.  It usually appear in a windows login as just MSD.

In likewise Open I had success joining it when I put MSD.domain

In my case I would put [email]username@domain.msd.loca[/email]l

What is the "local" for?  Thanks for your help.  I am a newbie.

---

### Post by elperrillo on 2008-06-06
Thank you, that is what I figured. I am more of a visual guy so I just placed an icon on the desktop to likewise and I enter all the loging info on its nice GUI, its easier for me. 


Once again thanks for the response.

---

### Post by mohenjo on 2008-06-06
Domains typically have .com, .org, .net, etc.  So to create a domain of just one name (as in your MSD domain), it may be adding that .local to the end of it.  I'm guessing .local is just the top-level portion that it's looking for, which also tells the computers that it is indeed a local domain and not a .com, .org, etc.

A workgroup is what typically has just one name, that could also be a way of differentiating between workgroup names and domains.

Either way, yea...you'll probably need to enter the .local after your domain name everytime you log in.

On the topic of freezing up when not connected to the domain, I believe this is still happening.  I haven't seen an update to likewise yet (but I also haven't taken my laptop home yet to test) so I think you'll need to leave the domain whenever you log in from home, then re-join the domain when you get back to the office.

---

### Post by tact on 2008-06-07
You may or may not need to the ".local" when you key in your domain.  That really depends on how your corporate LAN is set up.

There is some confusion around the use of the word "domain" so to avoid that I will use a specific name not the word "domain".

For example the corporate domain is "pqr".    Lets also assume its a dotcom and so we have "pqr.com".    My email address would be [EMAIL="username@pqr.com"]username@pqr.com[/EMAIL].  And quite possibly the public webserver is [www.pqr.com]("http://www.pqr.com").

[www.pqr.com]("http://www.pqr.com") would then be a fully qualified domain name (FQDN).   fully qualified meaning complete...nothing missing... pointing to a specific machine ... making it accessible, in this case, to the whole outside world.

Lets say the mailserver in my company is called "mailserver".   Lets say its also accessible to the outside world.   Its FQDN then is mailserver.pqr.com

When you log onto a domain using likewise-open you need to use a FQDN.  SO the form would be [EMAIL="username@fully.qualified.doma"]username@fully.qualified.doma[/EMAIL]inname

In this example:
-  (username@)***pqr***     is not a FQDN
-  ([EMAIL="username@pqr.com"]username@)***pqr.com***[/EMAIL]   is also not a FQDN on my company server.  Because of the way its configured I have to add a .local.   So on my corporate LAN I need to use 
- [EMAIL="username@pqr.com.loca"](username@)***pqr.com.local***[/EMAIL]

It is all about how the LAN is set up.  You may not need it.  And if you need something tacked onto the end there is no necessity for it to be ".local" - it could just as easily be ".snoopy" or ".wonderwoman" depending on how your admins set up the LAN.

So it boils down to you needing to know your company's FQDN.   Whatever you use if you get a "succeeded" at the end you got it right!  :)

Cheers.

---

### Post by leprox on 2008-06-19
I had the same problem i join the domain , but after reboot i cannot login.
but following a tutorial y get god results without problems after reboot..

1.	sudo apt-get install likewise-open
2.	sudo domainjoin-cli join yourdomain.com yourADusername 
3.	sudo update-rc.d likewise-open defaults
4.	sudo /etc/init.d/likewise-open start

i tried it with ubuntu 8.04 without any update..

---

