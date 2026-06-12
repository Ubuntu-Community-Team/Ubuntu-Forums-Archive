---
title: "Install Spotify for Linux"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by Ulvdatter on 2012-09-14
Hi!

I've been running Spotify over Wine for some time, but it has proved to be very unstable, so I thought I might try Spotify for Linux.  The installation process seems to be quite complicated, though. Oh, and by the way, I'm running Xubuntu.
This is how far I got:

ulvdatter@ulvdatter-1000H:~$ echo "deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free" | sudo tee -a /etc/apt/sources.list
[sudo] password for ulvdatter: 
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
ulvdatter@ulvdatter-1000H:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 082CCEDF94558F59
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.Xk76amhzqT --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 082CCEDF94558F59
gpg: ber om nøkkelen 94558F59 fra hkp server keyserver.ubuntu.com
gpg: nøkkel 94558F59: «Spotify Public Repository Signing Key <operations@spotify.com>» ikke endret
gpg: Totalt antall behandlet: 1
gpg:              uendret: 1
ulvdatter@ulvdatter-1000H:~$ Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.FNqPtEHaQ4 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 082CCEDF94558F59
Executing:: command not found
ulvdatter@ulvdatter-1000H:~$ sudo aptitude update
sudo: aptitude: command not found
ulvdatter@ulvdatter-1000H:~$ sudo aptitude install spotify-client
sudo: aptitude: command not found

---

### Post by Ulvdatter on 2012-09-14
Well, that was a lot of norwegian, I just realised. Here's a translated version:

ulvdatter @ ulvdatter-1000H: ~ $ echo "deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free" | sudo tee-a / etc / apt / sources.list
 [sudo] password for ulvdatter:
 deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
 ulvdatter @ ulvdatter-1000H: ~ $ sudo apt-key adv - keyserver keyserver.ubuntu.com - recv-keys 082CCEDF94558F59
 Executing: gpg - ignore-time-conflict - no-options - no-default-keyring - secret-keyring / tmp/tmp.Xk76amhzqT - trustdb-name / etc / apt / trustdb.gpg - keyring / etc / apt / trusted.gpg - primary-keyring / etc / apt / trusted.gpg - keyserver keyserver.ubuntu.com - recv-keys 082CCEDF94558F59
 gpg: requesting key 94558F59 from HKP server keyserver.ubuntu.com
 gpg: key 94558F59: 'Spotify Public Repository Signing Key <operations@spotify.com> "not changed
 gpg: Total number processed: 1
 gpg: unchanged: 1
 ulvdatter @ ulvdatter-1000H: ~ $ Executing: gpg - ignore-time-conflict - no-options - no-default-keyring - secret-keyring / tmp/tmp.FNqPtEHaQ4 - trustdb-name / etc / apt / trustdb.gpg - keyring / etc / apt / trusted.gpg - primary-keyring / etc / apt / trusted.gpg - keyserver keyserver.ubuntu.com - recv-keys 082CCEDF94558F59
 Executing :: command not found
 ulvdatter @ ulvdatter-1000H: ~ $ sudo aptitude update
 sudo: aptitude: command not found
 ulvdatter @ ulvdatter-1000H: ~ $ sudo aptitude install spotify-client
 sudo: aptitude: command not found

---

### Post by Jakin on 2012-09-14
Here is what i just tried-

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
[sudo] password for joey: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.S26ABZUKal --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
gpg: requesting key 4E9CFF4E from hkp server keyserver.ubuntu.com
gpg: key 4E9CFF4E: public key "Spotify Public Repository Signing Key <operations@spotify.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
sudo sh -c 'echo "deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free" >> /etc/apt/sources.list'
sudo apt-get update
sudo apt-get install spotify-client

to which gave an error about the public key; so i typed

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59
sudo apt-get update
sudo apt-get install spotify-client


proceeded to install, i waited- and all was good :)

---

### Post by Ulvdatter on 2012-09-14
Oh, shoot. It just says "no such file or directory" : (

---

### Post by Jakin on 2012-09-14
let me simplify

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59
sudo sh -c 'echo "deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free" >> /etc/apt/sources.list'
sudo apt-get update
sudo apt-get install spotify-client

doesn't work?

Im on kubuntu, but it should be the exact same commands on xubuntu

---

### Post by Ulvdatter on 2012-09-14
Halelujah!!!

This got me as far as the "waiting" bit : )

Keeping my fingers crossed : )

---

### Post by Ulvdatter on 2012-09-14
Yes! I'm in!!!

Thank you Jakin, you have improved my life quality by 74% ; )

---

### Post by Jakin on 2012-09-14
Youre most welcome, and Rock On! :D

---

### Post by johsmic on 2012-10-20
And you improved mine by 78%! Works like a charm on Xubuntu 12.10. 
Thank you so much.

---

### Post by candtalan on 2013-01-09
> **Jakin said:**
> let me simplify

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59
sudo sh -c 'echo "deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free" >> /etc/apt/sources.list'
sudo apt-get update
sudo apt-get install spotify-client

doesn't work?

EDIT:
From the OMG Ubuntu site I followed stuff. Spotify appeared in the software centre as being installed, but still did not show in the opt directory, so I uninstalled via softwar centre, then reinstalled the spotify desktop client (only), and it worked
:-)

Im on kubuntu, but it should be the exact same commands on xubuntu

I have just tried this on Ubuntu 12.04.1 and it does not seem to work. 
I was running spotify via wine recently sometimes, and I have uninstalled it from Wine and believe I have removed all references to spotify before following the above commands.

Any ideas please?

---

### Post by Pyotrek on 2013-04-14
> **Jakin said:**
> let me simplify

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59
sudo sh -c 'echo "deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free" >> /etc/apt/sources.list'
sudo apt-get update
sudo apt-get install spotify-client

doesn't work?

Im on kubuntu, but it should be the exact same commands on xubuntu

Worked for me as well. Xubuntu 12.04.
                         P.S. I wasn't aware that each line needs to be launched separately ;)

---

