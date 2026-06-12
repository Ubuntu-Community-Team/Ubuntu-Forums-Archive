---
title: "adding ppa:dansmith/chirp-snapshots to your system's Software Sources."
date: 2020-04-07
forum: New to Ubuntu
---

### Post by jjconstru1 on 2020-04-07
Ubuntu 18.04 has been working well since installing it side by side Win7 on my Acer Aspire 5733Z-4851. Anyone know how Chirp ham radio programming PPA works with Ubuntu? Here's what was said to do;   

**Adding this PPA to your system**

                  You can update your system with unsupported packages from           this untrusted PPA by adding **ppa:dansmith/chirp-snapshots**           to your system's Software Sources.           ([Read about installing]("https://launchpad.net/+help-soyuz/ppa-sources-list.html"))         
          sudo add-apt-repository ppa:dansmith/chirp-snapshots
sudo apt-get update

Seemed to work from my point of view. Except for errors below;
Failed to connect to us.archive.ubuntu.com:80 followed by numbers in parenthesis for example (2001:67c:1562::18)
Then, some files failed to download. they have been ignored or old ones used instead.
What should be done? How do I close the terminal? 

jjconstr

r


Well, the PPA is installed. The commands were beyond me until I pulled out Rob's Linux book. And the last command needed was given me in Holger Gehrke's post. Thanks!  Where is the donate button? I searched to no avail.

---

### Post by Holger_Gehrke on 2020-04-07
The error you get seems to be unrelated to the ppa but rather seems to be one of the Ubuntu mirrors (us.archive.ubuntu.com, with ip6 address 2001:67c:1562:0:0:18) not responding. The files that were not downloaded are lists of packages stored on that mirror. 'apt update' or 'apt-get update' only updates the local list of packages available for installation. To actually install the package you want, you need to run 'sudo apt install **package-name**', in this case 'sudo apt install chirp-daily' which will download and install the package.

To close a terminal you can either enter 'exit' or just close the window.

Holger

---

### Post by Impavidus on 2020-04-07
Your error is indeed unrelated to the PPA you added. It could be a network problem, a server glitch, ... If the error is still there tomorrow, could you post the full output of```
sudo apt update
```
I'm not familiar with ham radio.

---

### Post by jjconstru1 on 2020-04-07
> **Holger_Gehrke said:**
> The error you get seems to be unrelated to the ppa but rather seems to be one of the Ubuntu mirrors (us.archive.ubuntu.com, with ip6 address 2001:67c:1562:0:0:18) not responding. The files that were not downloaded are lists of packages stored on that mirror. 'apt update' or 'apt-get update' only updates the local list of packages available for installation. To actually install the package you want, you need to run 'sudo apt install **package-name**', in this case 'sudo apt install chirp-daily' which will download and install the package.

To close a terminal you can either enter 'exit' or just close the window.

Holger

Thanks for the great reply. Does the output so far need to cleared before exiting(saw something like that in a terminal drop down menu) or before running 'sudo apt install chirp-daily'? 
Will this command correct the old files that were installed when the new ones were unavailable?

jjconstr

---

### Post by jjconstru1 on 2020-04-07
> **Impavidus said:**
> Your error is indeed unrelated to the PPA you added. It could be a network problem, a server glitch, ... If the error is still there tomorrow, could you post the full output of```
sudo apt update
```
I'm not familiar with ham radio.

Impavidus,

Is the code that is included in your post, the one I need to run to update the ppa? Ill wait for your response to do that.

Full output in HTML
```
[COLOR=#8AE234]**jjconstr@Aspire-5733Z**[/COLOR]:[COLOR=#729FCF]**~**[/COLOR]$ sudo add-apt-repository ppa:dansmith/chirp-snapshots
[sudo] password for jjconstr: 
 
 More info: [https://launchpad.net/~dansmith/+archive/ubuntu/chirp-snapshots](https://launchpad.net/~dansmith/+archive/ubuntu/chirp-snapshots)
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Get:1 [http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu](http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu) bionic InRelease [15.4 kB]
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                     
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]    
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                     
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]   
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB] 
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages [680 kB]
Get:8 [http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu](http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu) bionic/main i386 Packages [488 B]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [909 kB]
Get:10 [http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu](http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu) bionic/main amd64 Packages [488 B]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main i386 Packages [456 kB]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main Translation-en [218 kB]
Get:13 [http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu](http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu) bionic/main Translation-en [232 B]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [38.5 kB]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main DEP-11 48x48 Icons [17.6 kB]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main DEP-11 64x64 Icons [41.5 kB]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted amd64 Packages [29.6 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted Translation-en [7,752 B]
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [666 kB]
Get:20 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 Packages [617 kB]
Get:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main Translation-en [313 kB]
Get:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [307 kB]
Get:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 48x48 Icons [73.8 kB]
Get:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 64x64 Icons [140 kB]
Get:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 Packages [42.8 kB]
Get:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/restricted Translation-en [10.8 kB]
Get:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [1,012 kB]
Get:28 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages [653 kB]
Get:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [1,062 kB]
Get:30 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe Translation-en [217 kB]
Get:31 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe Translation-en [330 kB]
Get:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [42.1 kB]
Get:33 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [273 kB]
Get:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 48x48 Icons [16.4 kB]
Get:35 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe DEP-11 64x64 Icons [116 kB]
Get:36 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 48x48 Icons [202 kB]
Get:37 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/universe DEP-11 64x64 Icons [477 kB]
Get:39 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 Packages [10.5 kB]
Get:40 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse Translation-en [4,696 B]
Get:41 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:42 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [7,980 B]
Fetched 9,266 kB in 9s (1,008 kB/s)                                            
Reading package lists... Done
[COLOR=#8AE234]**jjconstr@Aspire-5733Z**[/COLOR]:[COLOR=#729FCF]**~**[/COLOR]$ sudo apt-get update
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:2 [http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu](http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu) bionic InRelease
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                     
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                     
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::18). - connect (101: Network is unreachable) Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable) Could not connect to us.archive.ubuntu.com:80 (91.189.91.39), connection timed out Could not connect to us.archive.ubuntu.com:80 (91.189.91.38), connection timed out
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::18). - connect (101: Network is unreachable) Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable)
Err:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::18). - connect (101: Network is unreachable) Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable)
Reading package lists... Done                               
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/bionic/InRelease)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::18). - connect (101: Network is unreachable) Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable) Could not connect to us.archive.ubuntu.com:80 (91.189.91.39), connection timed out Could not connect to us.archive.ubuntu.com:80 (91.189.91.38), connection timed out
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::18). - connect (101: Network is unreachable) Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable)
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::18). - connect (101: Network is unreachable) Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::15). - connect (101: Network is unreachable)
W: Some index files failed to download. They have been ignored, or old ones used instead.
[COLOR=#8AE234]**jjconstr@Aspire-5733Z**[/COLOR]:[COLOR=#729FCF]**~**[/COLOR]$ ssh
usage: ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-E log_file] [-e escape_char]
           [-F configfile] [-I pkcs11] [-i identity_file]
           [-J [user@]host[:port]] [-L address] [-l login_name] [-m mac_spec]
           [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address]
           [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]
[COLOR=#8AE234]**jjconstr@Aspire-5733Z**[/COLOR]:[COLOR=#729FCF]**~**[/COLOR]$ ^C
[COLOR=#8AE234]**jjconstr@Aspire-5733Z**[/COLOR]:[COLOR=#729FCF]**~**[/COLOR]$ ^C
[COLOR=#8AE234]**jjconstr@Aspire-5733Z**[/COLOR]:[COLOR=#729FCF]**~**[/COLOR]$ ^C
[COLOR=#8AE234]**jjconstr@Aspire-5733Z**[/COLOR]:[COLOR=#729FCF]**~**[/COLOR]$ 
```

jjconstr

---

### Post by jjconstru1 on 2020-04-07
oh. Thanks for your reply!

jjconstr

---

