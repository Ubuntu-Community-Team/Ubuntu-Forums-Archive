---
title: "HOWTO: VNC over SSH using Public/Private keys From Windows"
date: 2007-03-12
forum: Outdated Tutorials &amp; Tips
---

### Post by gaten on 2007-03-12
[U][SIZE=4]HOWTO: VNC over SSH using Public/Private keys From Windows

Changelog:
[/SIZE][/U]
1/18/08
 - Condensed commands in step #3 to one line 
 - Fixed typo in step #6
 - Added howto link for Xubuntu users
Thanks to xunil76 for the above suggestions.  


[SIZE=3] [SIZE=4]_Contents_[/SIZE]
[/SIZE][LIST=1]
[*][SIZE=3]Overview[/SIZE]
[*][SIZE=3]Why?[/SIZE]
[*][SIZE=3]Install SSH[/SIZE]
[*][SIZE=3]Generate key pairs
[/SIZE]
[*][SIZE=3]Configure SSH[/SIZE]
[*][SIZE=3]Configure Remote Desktop[/SIZE]
[*][SIZE=3]Dealing with Dynamic IPs[/SIZE]
[*][SIZE=3]Portable Solutions[/SIZE]
[*][SIZE=3]Setup PortaPuTTY for port forwarding
[/SIZE]
[*][SIZE=3]Conclusion[/SIZE][/LIST][B][SIZE=3][COLOR=DarkRed] 1. _Overview:_[/COLOR]
[/SIZE][/B]
    You will learn how to set up a VNC sever using Ubuntu's built in "Remote Desktop" feature. You will also learn how to set up a SSH server using ONLY public/private keys, on a non standard port, and how to tunnel all of your VNC traffic over this SSH connection. Also, learn how to set up a permanent virtual domain name for your computer (ie **mycomputer.something.com**) so you don't have to remember your IP address (which usually changes).

By the end of this Howto, you should be able to connect to your home computer from almost any PC that allows outboud connections (yes, even Windows Boxes, if you have a USB key).

This guide assumes the following:[LIST]
[*]You have a router/firewall, and know how to open ports (for the ssh daemon)
[*]You can transport your private key with you (which means you have some sort of portable media, like a USB thumb drive or CD).[/LIST]These instructions were tested on Dapper, but the theory works on all Linux boxes (excluding specific commands, of course).
[B][SIZE=3]
[COLOR=DarkRed] 2. _Why?_[/COLOR]

[/SIZE][/B]Realistically, there really isn't a reason to encrypt VNC traffic. It's encoded, and many times encrypted anyway, and in order to sniff your traffic an attacker would have to have access to a machine in between the two connecting computers. So all in all, you probably DON'T need to encrypt VNC traffic (more), but there are a couple good selling points to this method:[LIST=1]
[*]Security in depth. An attacker has to peel away more layers of security to compromise your system (and SSH is one heck of a layer).
[*]Less ports open to the world. Using the method described in this guide, you don't have to leave your VNC server listening on your external ports, only your internal ones (in other words, your router can block port 5900 and you'll still be able to use it).
[*]The only service attackers can even attempt to exploit your system from is SSH, and with public/private keys, that becomes very difficult (without stealing your key anyway).
[*]Security is a mindset, not a bunch of protocols and programs. If you think about security from the get-go, you will be better off in the future.[/LIST]Generally speaking VNC is an unencrypted protocol (it can be encrypted, but that's not the focus of this article). That means that any information you send over the internet can possibly be read by someone running a packet sniffer. There is a software package written in Perl called **Chaosreader** ([COLOR=Blue][http://www.brendangregg.com/chaosreader.html](http://www.brendangregg.com/chaosreader.html)[/COLOR]) which allows you to sniff for VNC traffic (and almost everything else) and replay keystrokes in almost real time. A sample output from a test VNC session shows this:
```
**VNC: 192.168.1.102:1096 -> 192.168.1.100:5900**

 **File out_20070212-1601.log, Session 1**

 [COLOR=red]sudo cat /ectc/    oasshad    

password
exit
[/COLOR]
```The above looks kinda weird, due to the fact that I used tab completions. But in a nutshell, this is what I did in my VNC session:[LIST]
[*]Opened a terminal window
[*]typed in "sudo cat /etc/shadow"
[*]it asked for my password, and I typed it in. My real password was displayed where "password" is, unencrypted.
[*]I then exited the terminal and closed the VNC session[/LIST]**This** is why we are going to tunnel VNC over ssh. As a side note, I believe that if you **don't** encrypt your traffic, you deserve to get attacked. But that's just me *puts tinfoil hate back on*

[B][SIZE=3][COLOR=DarkRed][SIZE=2][SIZE=3]3. [/SIZE][/SIZE][/COLOR][/SIZE][U][SIZE=3][SIZE=2][SIZE=3][COLOR=DarkRed]Installing SSH[/COLOR][/SIZE]
[/SIZE][/SIZE][/U][/B]     First, we will need to install the OpenSSH ([COLOR=Blue][http://www.openssh.org](http://www.openssh.org)[/COLOR]) server and client. 
```

sudo apt-get install openssh-client openssh-server

```[B][SIZE=3]
[COLOR=DarkRed] 4. [/COLOR][/SIZE][/B][U][B][SIZE=3][COLOR=DarkRed]Generate Key Pairs[/COLOR][/SIZE]
[/B][/U]
Before we can set up SSH to use public/ private keys, we need to make them. 

_**Please take care when selecting your passphrase!** _
This key will literally be the key to your machine. And if you're foolish enough to use the same password as your sudo account, if you loose this key the person who finds it could have full unrestricted access to your machine. 

The **ssh-keygen **suggests a passphrase of at least 10 - 30 characters. A very simple but effective method for generating passphrases (one that I use) is to make up a very odd sentence, not something you would find in a book or movie. For example: > **S**ally **a**ttacked **N**ormon **w**ith **t**he **p**urple **f**ish, **b**ashing **h**im **a**bout **h**is **y**ellow **h**ead **w**ith **a**n **e**qually **y**ellow **d**og **i**n **a**n **a**ttempt **t**o **d**islodge **h**is **t**houghts. Yes, it makes no sense what-so-ever; thats ok. Now we're going to take the first letter of each word (which are in bold) and the punctuation and create a string of characters out of them:
> SaNwtpf,bhahyhwaeydiaatdht.Go ahead, guess that. I dare you. If you wanted to make it a little more secure, you could "leet speak it" (convert some letters to numbers and symbols) and add some capital letters in there. A final version of your password could look like:
> $4Nwtpf,bH4hyHw43yd144tdHt.Now that might be a little overkill for you, but you can make your sentence longer or shorter to your liking, just an idea. Anyway, on with the key generation.

Generating the keys is a very simple process. First create a directory to store them in, then start **ssh-keygen**. Note, this needs to be done by the user you want to login through SSH as, **not root!**
```
mkdir -p ~/.ssh
chmod 700 ~/.ssh
cd ~/.ssh
ssh-keygen -t rsa
```Something like the following should appear:
```

Generating public/private rsa key pair.
Enter file in which to save the key (/home/**USER**/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/**USER**/.ssh/id_rsa.
Your public key has been saved in /home/**USER**/.ssh/id_rsa.pub.
The key fingerprint is:

```Obviously, **USER  **will be replaced with your actual user name. Now your private key is called **id_rsa**, and your public key is **id_rsa.pub.** 

The key idea here is you need **both** of these keys to log in. Your public key will be kept on your machine in the .ssh directory. Your private key will (ideally) be on your person, kept safe from the evil doers (I keep mine on my USB keychain). 

In order to conform to a default ssh server configuration, we're going to append your public key to another file.

```
cat ~/.ssh/id_rsa.pub >> authorized_keys
chmod 600 authorized_keys
```Now we're ready to configure sshd

[COLOR=DarkRed]**[SIZE=3]5. [/SIZE]**[/COLOR][U][B][SIZE=3][COLOR=DarkRed]Configuring SSH[/COLOR][/SIZE]

[/B][/U]Before we configure the ssh server, we have a couple of things to think about. First is where you're going to be connected to your computer from. Work? School? The local Starbucks? Now ask yourself, do they allow outbound connections on any port? If you're at school or work, the answer is mostly likely no. My school blocks all outbound ports <1024 (except for DNS, HTTP and HTTPS of course), but the higher number unassigned ports they tend to leave open. For instance, they block port 5900 (VNC), but they do not block port 47000 (unassigned). 

This is important information because we need to know what port to set up our ssh server on so that we CAN connect to it, no matter what. Here are some good guidelines (they don't apply in all situations of course)[LIST]
[*]High numbered ports (>1024) are blocked less than low ports (privileged ports)
[*]Some ports will almost always be open, like HTTP (80) and HTTPS (443). If all else fails, try running your SSH server on one of those.
[*]Last but not least, port 53 (DNS) will always be open.[/LIST]I run a web server on port 80, with SSL on port 443, so those options are out for me. So i chose a high numbered port (specifically 47000), and I have not had problems connecting from anywhere *yet*.

Now we're going to set SSH up to be a little more secure, and possibly to help us bypass any filters your school/work has set up.

First, let's make a backup of our SSH configuration (which we're going to change), in case anything goes wrong.

```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.working
```Now, using your favorite text editor, open up **/etc/ssh/sshd_config**. A couple of changes are going to be made to this file. Find the line:
```
Port 22
```And change it to 
```
Port 47000
```Make sure there is no **# **in front of **Port. **You don't have to pick **47000**, but keep in mind what was said before.

Now we disable remote logins with the **root** account, find:

```
PermitRootLogin yes
``` and change **yes** to **no**. Even though the default Ubuntu install does not enable the root account, it is  a good idea to disable remote logins in case you decide to enable the root account at a later time (like I did).

Now we will disable password authentication **all together**. We do this for a couple of reasons:[LIST]
[*]You can't crack a password that doesn't exist.
[*]By doing this, we are **forcing** users to use public/private key authentication.[/LIST]Find ```
#PasswordAuthentication yes
``` and change it to```
PasswordAuthentication no
``` note that I removed the **#**.

That's it for ssh config, now restart the server daemon and onto the next step:
```
/etc/init.d/ssh restart
```[SIZE=3][COLOR=DarkRed]**6. **[/COLOR][/SIZE][U][SIZE=2][B][SIZE=3][COLOR=DarkRed]Configure Remote Desktop (VNC)[/COLOR][/SIZE]
[/B][/SIZE][/U][SIZE=2]
This is easy. Using the menus, goto System->Preferences->Remote Desktop. A dialog should pop up, select the following check boxes:
[/SIZE][LIST]
[*]Allow other users to _v_iew your desktop
[*]_A_llow other users to control your desktop
[*]_R_equire the user to enter this password[/LIST]Do **not **check "A_s_k for your confirmation", you won't be able to login remotely if you do that. Also, select a good password as always, even though VNC will only be accessible from inside your network.

Click close and you're set!

As Xubuntu doesn't come with the gnome vino-server installed by default, you'll have to install it or another VNC server. Check out this howto for instructions: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)


[COLOR=DarkRed]**[SIZE=3]7. [/SIZE]**[/COLOR][U][B][SIZE=3][COLOR=DarkRed]Dealing with Dynamic IPs[/COLOR][/SIZE]

[/B][/U]Unless you own a domain name and have set up your computer to respond to DNS queries for it, you probably have a dynamic IP address. Most cable and DSL subscribers do. You can pay extra to get a static line, but you can have your own hostname for free!

Go over to DynDNS ([COLOR=Blue][https://www.dyndns.com/services/dns/dyndns/](https://www.dyndns.com/services/dns/dyndns/)[/COLOR]) and sign up for a "Free Dynamic DNS account". What this will do is give you the option of selecting a virtual domain name from one of their domains (such as **mycomputer.linuxhome.net**). This way, when you want to connect to your computer from somewhere, you can simply type in that address rather than your confusing and changing IP!

There is a *nix client that is supposed to tell the DynDns server when your IP address changes at [COLOR=Blue][https://www.dyndns.com/support/clients/](https://www.dyndns.com/support/clients/)[/COLOR]. I don't use this, as my router has this functionality built in. There are plenty of howtos on their website, you should be able to figure it out.

[SIZE=2][COLOR=DarkRed]**[SIZE=3]8. [/SIZE]**[/COLOR][U][B][SIZE=3][COLOR=DarkRed]Portable Solutions[/COLOR][/SIZE]

[/B][/U]In order to connect to your machine, you're going to need to do a couple of things. 

First, you'll need to open the port on your firewall/router on which your ssh daemon is running (**47000** in the example). For examples on how to do this, see [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

Now you're going to need some portable software, which will be for windows computers (as *nix and macs have ssh built in). 

[B]Portaputty: [COLOR=Blue][http://socialistsushi.com/portaputty](http://socialistsushi.com/portaputty)[/COLOR]
   [/B]An awesome tool. The power of ssh on your thumb drive! This is a portable version of **PuTTY**, the infamous ssh client for windows. Stick this on your thumb drive.

[B]TightVNC Viewer: [COLOR=Blue][http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)[/COLOR]
   [/B]This is a VNC client for Windows (also a Linux version available). Get the "[/SIZE]tightvnc-1.2.9_x86_viewer.zip" version, as it does not require an installation and can sit on your thumb drive. There are alternatives, like UltraVNC and RealVNC, but I like this one the best.

**Your Private Key:** Located in ~/.ssh/
Remember the file from above, named **id_rsa**? You're going to put this file on your USB drive, and import the key into PuTTY. To do that:

  1) Run the file called "puttygen.exe" on the USB drive
  2) Goto Conversions | Import Key
  3) Click on your private key and enter your passphrase
  4) Update the key fingerprint, comment and passphrase as desired
  5) Save the keys using the "Save public key" and "Save private"

If you didn't notice, it generated another public key.This is the same key as is on your computer, as you can always generate your public key from your private key (but not the other way around).

OK, we're almost done, one more step!

[COLOR=DarkRed]**[SIZE=3]9. [/SIZE]**[/COLOR][U][B][SIZE=3][COLOR=DarkRed]Set up PortaPuTTY for port forwarding[/COLOR][/SIZE]

[/B][/U]On your USB drive, open up putty.exe and do the following:[LIST]
[*]On the left hand menu, select "Session". Fill in your brand spanking new dynamic hostname under "Host Name (or IP address)". **Note: **Do **not** use the URL here, instead use the hostname by itself. For instance, if your dynamic hostname's URL is **[http://mybox.home.com](http://mybox.home.com)**, put **mybox.home.com** in the "Host Name (or IP address)" box.
[*]Fill in the "Port"
[*]Now select "Connection->SSH->Auth" on the left menu.
[*]Under "Private key file for authentication:" browse for your private key ending in .ppk.
[*]Now select "Tunnels" on the left menu. Under "Source Port" pick a large number that isn't a service port (like **50000**).
[*]Under "Destination" type in "**127.0.0.1:5900**". That tells ssh to tunnel any service connected to port **50000** to port **5900** (VNC) on the local interface (and the local interface will be your home computer, once we connect to it),
[*]Now click the "Add" button.
[*]Go back to "Session", type in a name under "Saved Sessions" and click "Save". This way you can just load that profile and you don't have to type that all out again.[/LIST]OK, we're ready to connect. Drum roll please....

Click on the "Open" button, type in your private key passphrase when asked, You will see a normal looking shell prompt, that's ok. Now go back to the USB drive, and find your TightVNCviewer.exe. Open it, and under "VNC server:" type in "**127.0.0.1::50000**", note that there are 2 **::**. This will connect the view to the "proxy server" created by PuTTY, and then tunnel us home to our machine. If you set up the VNC server to use a password, it will ask you for it. Enter that, press enter and congrats! You should be looking at your own home desktop.

Don't expect it to be blazing fast, VNC is kinda slow. A faster solution would be FreeNX, perhaps I'll write a tutorial about that later if there is interest. 

[B][U][SIZE=3][COLOR=DarkRed]10. Conclusion

[/COLOR][/SIZE][/U][/B][SIZE=3][COLOR=DarkRed][SIZE=2][COLOR=Black]That was kinda long, I know. But you should have a good understanding on both services, and how to configure them. 

SSH provides to us a **great** resource for secure communications. Any TCP protocol can be forwarded in this way (FTP, POP, HTML). There are many uses for SSH tunneling, and this little HOWTO is just the tip of the iceburg. Using prublic and private keys provides us with increased security via two factor authentication (meaning that to access your system, you need to have your key, **and **know the passphrase to that key).

For some further reading, try:

[U]SSH
[/U][COLOR=Blue][http://www.securityfocus.com/infocus/1810](http://www.securityfocus.com/infocus/1810)
[http://www.openssh.org/faq.html](http://www.openssh.org/faq.html)
[http://www.rzg.mpg.de/networking/tunnelling.html](http://www.rzg.mpg.de/networking/tunnelling.html)
[http://johnny.chadda.se/2006/10/24/access-your-linux-computer-graphically-and-securely-using-ssh-and-vnc/](http://johnny.chadda.se/2006/10/24/access-your-linux-computer-graphically-and-securely-using-ssh-and-vnc/)[/COLOR]   
[/COLOR][/SIZE][/COLOR][/SIZE]   The above link is a MUCH better tutorial than this one :P Pictures and everything.

[U]VNC
[/U][COLOR=Blue][http://en.wikipedia.org/wiki/VNC](http://en.wikipedia.org/wiki/VNC)
[http://www.realvnc.com/](http://www.realvnc.com/)
[http://www.realvnc.com/](http://www.realvnc.com/)
[http://ultravnc.sourceforge.net/](http://ultravnc.sourceforge.net/)[/COLOR]   

Please let me know what you think about this how to. Is it confusing? Too much information? Too little? 

Any questions, comments or corrections you can either post here, send an email to **education.kills** [at] **gmail** dot **com** or find me on Freenode IRC (usually in #ubuntu-offtopic). Thanks.

---

### Post by wislon on 2007-03-14
Absolutely super HOWTO! I was been battling to get the SSH stuff working for myself, and putty made it a lot easier, but the explanation of the keys cleared up a few things for me. Well done! :)

---

### Post by DC@DR on 2007-03-14
Perfect! I'd like to THANK YOU for this howto. It's so helpful and well-organized :-)

---

### Post by gaten on 2007-03-14
DC@DR:
> Perfect! I'd like to THANK YOU for this howto. It's so helpful and well-organized 

wislon:
> Absolutely super HOWTO! I was been battling to get the SSH stuff working for myself, and putty made it a lot easier, but the explanation of the keys cleared up a few things for me. Well done! 

No problem, thanks for the feed back and I'm glad you liked it.

---

### Post by Paulo Wageck on 2007-03-17
server is refusing the keys... what can be wrong???
checked everything... its all like the tutorial... running edgy

---

### Post by Paulo Wageck on 2007-03-17
dunno what i did but now seens to be working.
thanks!

---

### Post by Webspot on 2007-03-27
Great tutorial! I'll try this as soon as I get home.

Finally I'll be able to access my machine from school!:)

---

### Post by Remthewanderer on 2007-03-27
> That's it for ssh config, now restart the server daemon and onto the next step:
Code:

/etc/init.d/sshd restartshouldn't it actually be 

```
 /etc/init.d/ssh reload
/etc/init.d/ssh restart
```Can you restart and not reload?  Does the order matter? (reload then restart)?  Also I do not think there should be a letter d after ssh.  My machine did not like that.

My other question is that once putty is running it asks for a login id and password.  Is this the ubuntu login id and password or something else?

I think I have everything running correctly but I have no idea what to use as a login.

Thanks so much for answering my original email so quickly!  My original problem was that I did not change the connection type in putty from RAW (which is the default) to SSH.  Once I made that change putty prompted me for login info.

---

### Post by Remthewanderer on 2007-03-30
So I think my assumption was correct, that the ssh username/passsword is whatever your ubuntu u/p is.

Now I think I ran into a bigger problem.  When on my home network putty does prompt me for login info ( I have not tried login in yet, no time lately) but at work it does not.  Putty just times out.

I was thinking that this was due to the port I was trying to use (port 47001) not open on my work network.  I used shieldsup at grc and noted that the port in quesiton is showing up as closed.

So the next step I am going to take is to try and use port 443 since I am not running a webserver at home.  

The weird thing is that the sheildsup scan also notes that port 443 along with other common ports (80 and 53) are closed.  This can not be since I can access http and HTTPS websites freely.  Is sheilds up confused?

thanks, REM

---

### Post by Chachee on 2007-04-11
I love your how to.  It was great and works, for the most part.

I can't get Putty to work with the web address though.  I can verify that my dyndns account is working.  When I go to the page forwarded by my router I get my login prompt.  I also verified the ports are forwarding correctly.

I can connect with putty through if I just use the ip as well.  So there's some setting in Putty that I don't have right just concerning the webpage.

Any clues?

JT

---

### Post by gaten on 2007-04-11
Sorry it took me so long to respond :(

Remthewanderer:
>           Quote:
                                                 That's it for ssh config, now restart the server daemon and onto the next step:
Code:

/etc/init.d/sshd restart                                 
shouldn't it actually be 

     Code:
      /etc/init.d/ssh reload
/etc/init.d/ssh restart 
Yes, you are correct, it should be **ssh**. Bad typo on my part, hopefully people figured it out. Thanks for the correction, it's fixed now.

However, **restart** simply restarts the daemon which causes the config file to be re-read. **Reload** just re-reads the config file without restarting the daemon. I always like to restart the daemon to ensure it starts like I want it to, but the choice is yours. Either
```
/etc/init.d/ssh reload
```or
```
/etc/init.d/ssh restart
```Will both accomplish the same thing. 

> Now I think I ran into a bigger problem. When on my home network putty does prompt me for login info ( I have not tried login in yet, no time lately) but at work it does not. Putty just times out.

I was thinking that this was due to the port I was trying to use (port 47001) not open on my work network. I used shieldsup at grc and noted that the port in quesiton is showing up as closed.The port will be closed unless there is a server running on it. If your home machine is behind a router, you will need to punch a hole through it in order to gain access to your machine. Also, if you are using a firewall such as iptables you will need to give access to your server through that. 

To see if that specific port is open, I like to use this tool: [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

Enter in the port that ssh is listening on, click **Check** and you should see something like this: > [COLOR=green]Success:[/COLOR] I can see your service on **IP_ADDRESS** on port (**Port #**)
Your ISP is not blocking port PORTIf you see something like: > [COLOR=red]Error:[/COLOR] I could **not** see your service on **IP_ADDRESS** on port (**PORT**)
Reason: Connection refusedIt means you either are not running the service or your firewall is blocking it. 

> So the next step I am going to take is to try and use port 443 since I am not running a webserver at home.  

The weird thing is that the sheildsup scan also notes that port 443 along with other common ports (80 and 53) are closed. This can not be since I can access http and HTTPS websites freely. Is sheilds up confused?Like I said above, unless you have a **server** running on those ports, ShieldsUP! will see the port as closed or "stealthed"., because they are only accepted connections initiated by **you**, not by other people.

---

### Post by gaten on 2007-04-11
**Chachee**:
>  I can't get Putty to work with the web address though. I can verify that my dyndns account is working. When I go to the page forwarded by my router I get my login prompt. I also verified the ports are forwarding correctly.

I can connect with putty through if I just use the ip as well. So there's some setting in Putty that I don't have right just concerning the webpage.Well, it's not a "webpage", it's simply a dynamic hostname. 

If you can connect through the IP address but not the hostname, make sure it's not an internal DNS problem. Try pinging your hostname and make sure it resolves to the same IP address as your actual machine. 

Also remember that you need to set up a DynDNS updater service so that when your IP address changes the hostname remains accurate. 

> When I go to the page forwarded by my router I get my login prompt. I don't understand what you are trying to say there, please explain some more for me. What "page" are you talking about? SSH isn't a webserver, remember.

---

### Post by Chachee on 2007-04-12
Ah.. I figured I wasn't being clear enough.  

I have my home router forwarding to dyndns through it's internal settings.  So when I go to the url that I choose I get the login prompt for my home router.  So I can confirm that the dynamic dns is working that way.

from putty whenever I try to connect through it to the url on the port I set (47000) it fails.  But if I use the IP that's currently assigned to my router it works.

The error screen pops up with - unable to open connection to http, host does not exist.

Please let me know if I am still not making sense.

JT

---

### Post by gaten on 2007-04-12
> 
I have my home router forwarding to dyndns through it's internal settings. So when I go to the url that I choose I get the login prompt for my home router. So I can confirm that the dynamic dns is working that way.
Make sure outsiders can't access your router. Even though they need to login, they can brute force it and you wouldn't know the difference. Use a port checker to see if 80 is open from the outside. 

> 
from putty whenever I try to connect through it to the url on the port I set (47000) it fails. But if I use the IP that's currently assigned to my router it works.

The error screen pops up with - unable to open connection to http, host does not exist.
I think I see the problem. In the address box in PuTTY you are putting "http://blah.blah.com", which like you said, is the **url** of your machine. You need to use the address of the machine, **not** the url.

Do **not** put the **http://** part, that really isn't part of the dynamic address, that's a protocol identifier (which means it tells what ever program you are using to use the **http** protocol). In summary:

If the url of your dynamic hostname is [B][http://chachee.mybox.com](http://chachee.mybox.com)

[/B]In the **address **box in PuTTY put: [B]chachee.mybox.com
[/B]In the **Port** box in PuTTY put: [B]47000

[/B]And I think that will do it, sorry I wasn't more clear in the HowTO, I'll update it to reflect this post.

As a side note FYI: in a web browser, you almost never have to put **[http://,](http://,)  **you can just put in "www.ubuntu.com" or whatever, as the web browser will assume the protocol is **HTTP**. This obviously doesn't apply when visiting **FTP**, **HTTPS** or any other type of server from a web browser, but at least you know what **xxx://** stands for in a URL now.

---

### Post by marv2097 on 2007-04-12
Gaten,

Thanks for the howto, it has cleared a lot of things up for me about SSH tunneling. 

I have also found I can use my ubuntu box to secure VNC sessions to my Windows box. I added another tunnel in Putty but instead of using 127.0.0.1:5900 i used the IP of the Windows machine running tightvnc server. eg. 192.168.0.7:5900 and listened on 50001. When I run the VNC client i enter 127.0.0.1::50001

//Marv

---

### Post by Chachee on 2007-04-13
Thanks for clearing that up.  I'll have to check about what you were saying in my router, have a quick link handy?

I left my mem stick at work so it's going to be a few days till I can check again.  I'll let you know.

JT

---

### Post by pirothezero on 2007-04-16
Thanks so much for this. 

I just reinstalled over the weekend and was looking for the tutorial on public keys and such and I came across this new thread and the moment I saw the intro I was like yes thats exactly what I wanted to do last time I wanted to do this.

Will run through it after update manager finishes and report back.

---

### Post by gaten on 2007-04-16
> Thanks for clearing that up.  I'll have to check about what you were saying in my router, have a quick link handy?

[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

Find your router on that page and it should tell you all you need to know.

---

### Post by Chachee on 2007-04-17
Thanks for the link, but I know how to forward ports.  I was more concerned with figuring out how to stop access to the router from the outside.  Right now I have it setup to only allow https access, but I can still get to it from the outside.

I need to know how to scan it and see what's open, and then how to close it.  I'll do some searching and see what I can come up with.

If you have anything on it please let me know.

Also, is it possible to use a port for ssh that you also use for web traffic?  At work to get to the proxy we use 8080 and I assume this is switched over to 80 at the firewall.  The port I chose is blocked.  Can I use 8080 and connect through?

JT

---

### Post by gaten on 2007-04-17
>      Thanks for the link, but I know how to forward ports. I was more concerned with figuring out how to stop access to the router from the outside. Right now I have it setup to only allow https access, but I can still get to it from the outside.GRC scan ([https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2))
SOS Scan ([http://scan.sygate.com/](http://scan.sygate.com/))

Also, if you can install **nmap** to a computer outside your network, you could scan it with that.

> 
I need to know how to scan it and see what's open, and then how to close it. I'll do some searching and see what I can come up with.As far as how to disable https access to your router, you'll have to read the documentation that came with it.

> 
Also, is it possible to use a port for ssh that you also use for web traffic? At work to get to the proxy we use 8080 and I assume this is switched over to 80 at the firewall. The port I chose is blocked. Can I use 8080 and connect through?Yes, you can use 8080 as long as you set up your home machine to forward 8080 to your ssh service.

---

### Post by Clamato on 2007-04-18
You're tutorial is awesome, very easy to get through, thank you.  I'm extremely new to Linux, so I've learned a ton just in this tutorial alone.  I had a few problems but worked them out, but I just wanted to say thanks for putting this together it's made me love linux that much more :D

---

### Post by Clamato on 2007-04-19
Well.....I guess I spoke too soon.  I do have a problem.  I have putty and my keys all saved on my thumb drive.  I'm able to load the profile that has the private key and tunneling setting saved, but when I move to another machine I have to load everything again...which isn't a big deal.  But, I can't get in to SSH or anything from outside my network.  I only tried it at school, so I'm not sure if they maybe have the port I used blocked or something.  Any idea's?  I get a network timed out message...... :( I have the port forwarded on my router, and I found out I can't even ping my external IP assigned by my ISP or my domain name setup through dyndns

---

### Post by gaten on 2007-04-20
> Well.....I guess I spoke too soon. I do have a problem. I have putty and my keys all saved on my thumb drive. I'm able to load the profile that has the private key and tunneling setting saved, but when I move to another machine I have to load everything again...which isn't a big deal. 

Are you using PortaPutty? If you are just using regular old Putty, it saves your configuration to the registry of the machine. 


> 
But, I can't get in to SSH or anything from outside my network. I only tried it at school, so I'm not sure if they maybe have the port I used blocked or something. Any idea's? I get a network timed out message...... :sad: I have the port forwarded on my router, and I found out I can't even ping my external IP assigned by my ISP or my domain name setup through dyndns

Not being able to ping is probably a result of your routers' firewall blocking pings, so that's no big deal. To check and make sure that you opened the right port, goto [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and put in whatever port you used (I mention this method in a reply somewhere on this post). Make sure it is open to that service. If not, check that a firewall on the machine itself is not blocking connections (like iptables or Firestarter). Also, make sure you are updating the DyDNS setting with a client or through your router. Hope that helps.

---

### Post by Clamato on 2007-04-21
> **gaten said:**
> Are you using PortaPutty? If you are just using regular old Putty, it saves your configuration to the registry of the machine. 

 Also, make sure you are updating the DyDNS setting with a client or through your router. Hope that helps.

Awesome, thank you. Yes, I am using regular putty.

I think I got this portion right, I'm able to nslookup my hostname and it posts as my ip address.  The port is showing open on canyouseeme, so I wonder if it's that my school is blocking that port.  I'm also able to get through using my hostname within my network, so the connection has to be going outside my router and back through?  Is that logic right?  I'll try and move the port higher and see if that works.  

I also had one more quick question, I'm wanting to add another user for one of my classmates so we can do labs on my machine at home but am having trouble setting his up.  He's setup as a user on the box, I went through the steps to create the private keys on the machine for that separate user, updated the sshd_config file to point to the authorized_keys, and set him up on putty.  Now when I try and ssh in I get "No supported authentication methods available".  I think it may have to do with the sshd_config file, this is what I have for the two users:


```
AuthorizedKeysFile /home/USER1/.ssh/authorized_keys 
```
```
AuthorizedKeysFile /home/USER2/.ssh/authorized_keys 
```

And it's the second user I'm having trouble getting into.  Sorry for all the questions, I appreciate it!

---

### Post by gaten on 2007-04-21
> I think I got this portion right, I'm able to nslookup my hostname and it posts as my ip address. The port is showing open on canyouseeme, so I wonder if it's that my school is blocking that port. I'm also able to get through using my hostname within my network, so the connection has to be going outside my router and back through? Is that logic right? I'll try and move the port higher and see if that works. 
Sounds like your school is blocking the port. Try something really high like 57000, or try something common like HTTP (80), HTTPS(443) or DNS(53). The last one should always work, but might be picked up by you school admins.

> 
I also had one more quick question, I'm wanting to add another user for one of my classmates so we can do labs on my machine at home but am having trouble setting his up. He's setup as a user on the box, I went through the steps to create the private keys on the machine for that separate user, updated the sshd_config file to point to the authorized_keys, and set him up on putty. Now when I try and ssh in I get "No supported authentication methods available". I think it may have to do with the sshd_config file, this is what I have for the two users:First off, let me say I'm very glad you brought this to my attention. I made a **huge** error when writing this howto. The line ```
#AuthorizedKeysFile    %h/.ssh/authorized_keys
```should **not** be changed, it is fine as is. The **%h** tells SSH to look in the connecting users home directory for **.ssh/authorized_keys**. That's the way it should be, so go ahead and find the line ```
AuthorizedKeysFile  /home/**USER**/.ssh/authorized_keys
```And replace it with the above (which is the default). My bad, I'm sorry, I don't know **what** I was thinking. 

Secondly, ensure that your friend has the following files in his ~/.ssh/ directory on your machine and his:

[U]His Machine
[/U]authorized_keys ==> His public key
id_dsa **OR** id_rsa ==> His private key

[U]Your Machine
[/U]authorized_keys ==> His public key

The basic theory is this: You friend will authenticate himself to your server using his private key (kinda) which is authenticated by his public key on your server. Without his public key on your machine, and his private key on his own machine, nothing can happen.

Thanks again for helping me find that error.

---

### Post by flope on 2007-05-15
Thanks a lot for the How To. It is working fine in a couple of computers inside the network.... now I should try this outside.

BTW, there is something that it is not clear to me. By default this line is commented.
```
#AuthorizedKeysFile    %h/.ssh/authorized_keys
```

Should it be uncommented? I created the file authorized_keys as it is indicated in the how to.

Ubuntu 7.04 64-bit.

---

### Post by gaten on 2007-05-15
It doesn't matter if it is commented or not. If, however, you change the default for some reason, uncomment it.

---

### Post by tehkain on 2007-05-15
What is the default port for the remote desktop included in ubuntu?

---

### Post by gaten on 2007-05-15
> What is the default port for the remote desktop included in ubuntu?

5900

---

### Post by DFreeze on 2007-08-09
Hey, thanks for your tutorial. Thanks to your info I got SSH working! But testing it from work today, I saw something distressing: the session prompts: " the server refused your password " or something similar. Yet I could login anyway (using PortaPuTTY)...

So I removed the key I generated from PortaPuTTY and tried again... AND I COULD LOGIN JUST FINE! So the SSH login is totally unprotected! How does this happen, and what do I do about it?

---

### Post by gaten on 2007-08-13
>  So I removed the key I generated from PortaPuTTY and tried again... AND I COULD LOGIN JUST FINE! So the SSH login is totally unprotected! How does this happen, and what do I do about it?

That is odd. Post the EXACT error message here and I can help you more. Also, check out **/var/log/auth.log **and see if there are any lines about ssh logins. 

Also, post your config, and we'll go from there. Try verbose logging in putty (its in the options somewhere, google for it), and check the error log from the client side.

---

### Post by DFreeze on 2007-08-14
Hey, thanks for listening. I&#8217;ve repeated the process just now, but first without the .ppk file (to ensure there&#8217;s not some password in the buffer the second time). The SSH login went just fine. Second time, with the .ppk file I made a while ago, the respone is the same login screen (I can type my username), then I&#8217;m prompted: &#8220;Server refused our key&#8221; and I&#8217;m asked for a password anyway. Using my password for the desktop at home (my sudo password) I&#8217;m in.

The second time /var/log/auth.log gives this
```

Aug 14 14:04:45 desktop sshd[133337]: Accepted password for $USER from ***.***.***.*** port 24257 ssh2
Aug 14 14:04:45 desktop sshd[133341]: (pam_unix) session opened for user $USER by (id=0)

```

My /etc/ssh/sshd.config is as follows:
```
 
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 47000
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

I hope you see something I overlooked or did wrong. If you need any more info I&#8217;m glad to give it to you.

---

### Post by gaten on 2007-08-14
Change this:

```
#PasswordAuthentication no
```

to this (removing #): 
```
PasswordAuthentication no
```

and restart the ssh server. I may have messed up with that section, I'll have to check (I wrote it so long ago), but unless the option is defined as the default, changing it without removing the **#** does nothing (it treats it like a comment). 

If **this** doesnt work, connect to your server using this command:
```
ssh -v server
``` and post the output here. 

Hope this helps.

---

### Post by DFreeze on 2007-08-15
Ha, I never noticed. That was an obvious flaw in the config. I edited the config file and restarted the ssh service. Now, when I connect from my other ubuntu-machine, I get the following:

```

goswin@c-maxx:~$ ssh -v 192.168.1.4 -p47000 -i ~/Desktop/id_rsa
OpenSSH_4.6p1 Debian-5, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.4 [192.168.1.4] port 47000.
debug1: Connection established.
debug1: identity file /home/goswin/Desktop/id_rsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[192.168.1.4]:47000' is known and matches the RSA host key.
debug1: Found key in /home/goswin/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/goswin/Desktop/id_rsa
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/home/goswin/Desktop/id_rsa': 
debug1: read PEM private key done: type RSA
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).

```

I'm not sure what that is. I created both keys just recently...

In Windows, using PortaPuTTY, I get the same "Server refused our key" message. Is there something I overlooked with the keys?

---

### Post by gaten on 2007-08-15
**On the client computer**
Check your permissions, and also put the key in ~/.ssh/, as this is the default place for ssh to look (unless you are in windows of course).

The perms for your private key should be set to 600, ie
```
chmod 600 ~/.ssh/id_rsa
```

and the directory **.ssh** should be 700 also.

**On the server computer**
Finally, make sure that your public key is on the server in the ~/.ssh/ directory and named **authorized_keys**. This is not **id_rsa**, that is your private key.

---

### Post by DFreeze on 2007-08-15
Hey gaten, thanks for helping me with this. I'm not there yet, but I appreciate your efforts! I set the permissions on the client side like you said. You debugged my server side once more, since authorized_keys wasn't in my .ssh folder. I put the id_rsa key in the .ssh folder of the client side and tried again. Still no luck...

```
OpenSSH_4.6p1 Debian-5, OpenSSL 0.9.8e 23 Feb 2007
Warning: Identity file id_rsa not accessible: No such file or directory.
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.4 [192.168.1.4] port 47000.
debug1: Connection established.
debug1: identity file /home/goswin/.ssh/identity type -1
debug1: identity file /home/goswin/.ssh/id_rsa type -1
debug1: identity file /home/goswin/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[192.168.1.4]:47000' is known and matches the RSA host key.
debug1: Found key in /home/goswin/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/goswin/.ssh/identity
debug1: Trying private key: /home/goswin/.ssh/id_rsa
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/home/goswin/.ssh/id_rsa': 
debug1: read PEM private key done: type RSA
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/goswin/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).

```

Can you identify if the problem lies on the server or the client? Or is a problem with the public key server-side per definition (I'm still trying to grok the whole keys thing).

::EDIT::
I read somewhere that this same type of error message is sometimes due to the fact that the ssh-program can't find out the type of key I'm using. I see the line "debug1: read PEM private key done: type <unknown>", so that might be a fix. Is the key an MD5 something (read that as well)?

---

### Post by gaten on 2007-08-15
> I read somewhere that this same type of error message is sometimes due to the fact that the ssh-program can't find out the type of key I'm using. I see the line "debug1: read PEM private key done: type <unknown>", so that might be a fix. Is the key an MD5 something (read that as well)?Possible, but I don't think so. That message is normal, as openssh tries to read your key unencrypted first (without a password), and fails because it does have a password (then it asks you for it). Here is the output on my machine:

```
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.101 [192.168.1.101] port 22.
debug1: Connection established.
debug1: identity file /home/gaten/.ssh/identity type -1
debug1: identity file /home/gaten/.ssh/id_rsa type -1
debug1: identity file /home/gaten/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-5ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.1.101' is known and matches the RSA host key.
debug1: Found key in /home/gaten/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/gaten/.ssh/identity
debug1: Trying private key: /home/gaten/.ssh/id_rsa
debug1: Trying private key: /home/gaten/.ssh/id_dsa
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/home/gaten/.ssh/id_dsa': 
debug1: read PEM private key done: type DSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Last login: Wed Aug 15 07:58:22 2007 from 192.168.1.100

```

You can see they are quite similar, except mine gets through ;)

You might try generating new keys, and trying those, remembering to upload only your public key to the server. I have to admit I'm stumped. Try a more verbose ssh output, via

```
ssh -vv host
```

---

### Post by nahham on 2007-09-30
Thank you very much for the tutorial.  I am using my server from half-away around the world with no problems.  I have a lame question though:

How can access the same setup through Linux?  I am running Ubuntu Feisty and was hoping there is a similarly easy way to access this setup.  I tried downloading Putty ssh client for Linux and configuring it accordingly but that didn't work. 

Any ideas??

EDIT: Don't worry about it, I got it to work.  Easier than I thought..

---

### Post by nisarg on 2007-10-22
A perfect HowTo... well done
Going to implement it soon and will post the results.
Thank you

---

### Post by bfdhud on 2007-10-30
Absolutely excellent HowTo.

Worked better than I ever would have hoped for. (Note: I have yet to try this outside of my network.)

---

### Post by 1feistymedic on 2008-01-11
Hello all.  I hate to rehash a seemingly closed post, but I have a few questions.  First of all I think the tutorial was great with just a few minor things I had to adjust with the help of some cross reference tutorials. I started remote desktop in ubuntu as directed and the vnc viewer in xp.

The biggest question is, when I connect to my Ubuntu Feisity box(server) via my XP box(client) using any client(ie..tightvnc and ultravnc) I can see an initial snapshot of the ubuntu screen but it stays frozen on the xp box.  While looking at my ubuntu screen I can see the mouse being moved by my xp box and can actually control the ubuntu desktop, but it does not show anything on the xp box as moving.

What I then tried was installing the tightvnc server on the ubuntu box, started it from the comand line and chose a password.  Only then could I actually see movement and screen changes on the xp box.  If I disabled the remote desktop on the ubuntu box, it killed access to the ubuntu tightvnc server.

Shouldn't the tightvnc server on the ubuntu box work without enabling the remote desktop feature?  Aren't they independent?  Apparently not.  Is there a fix for this problem so that I do not have to enable remote desktop on ubuntu **and** enable tighvnc server as well and still be able to see the changes I am effecting via my xp box(client)?

Thanks!

---

### Post by gaten on 2008-01-11
Do you have any desktop effects running (ie compiz)? On my desktop, I have to disable compiz effects in order to use remote desktop (tightvnc client). I usually just ssh in and run a 
```
pkill compiz.real
```
And that takes care of it, then I can run my vnc session without any problems.

As far as why it works with tightVNC server, my guess is that tight is a better server than vino (the gnome VNC server). In my opinion, Vino sucks but its easy to setup so I stick with it. 

And so far as using tight without remote desktop enabled, I'm not entirely sure why that is, I haven't used tight myself for quite some time.

In short, try disabling any kinds of desktop effects and see if that helps.

Oh, and would you mind telling me what adjustments you had to make? I'd like to make this tutorial as well rounded as possible. Thanks for reading it :)

---

### Post by Archmage on 2008-01-16
I only can thank for this wonderful turial. But is there anything called VNC over SSH using Public/Private keys from **Linux**? I seem not to get the tunneling over SSH to work and I all the Howtos that I check wont cover the problem with the firewall.

---

### Post by gaten on 2008-01-16
If I understand you correctly, you're trying to see a remote Linux desktop from another computer running linux? If that's the case, you have 2 options (well, a bunch more really, but I'll just cover 2).

1. Setup the server (the computer you are connecting to) exactly the same as described in the tutorial. Then from the local computer, ssh into the remote  using a command similar to this:
```
ssh -D 2000 remote.computer
``` 

This will create a dynamic forward from port 2000 on the local computer to port 22 (default ssh) on the remote computer.

Now, on the local computer simply use something like **rdesktop** (installed by default on Ubuntu) to connect to **127.0.0.1::2000 **using the VNC protocol, and everything should work as it does in Windows.

2. Use X forwarding in ssh
You'll have to change some settings on the server computer, and this tutorial I found on digg the other day does a great job explaining it:

[http://infectedproject.com/2007/07/09/forwarding-gnome-via-ssh/](http://infectedproject.com/2007/07/09/forwarding-gnome-via-ssh/)

Hope that helps.

---

### Post by xunil76 on 2008-01-16
i need some help with this.....i'm running Xubuntu instead of Ubuntu, and i obviously cannot complete step #6 as listed, as there is no "**_System->Preferences->Remote Desktop_**" in Xubuntu.

any ideas on how to enable remote desktop in Xubuntu?

---

### Post by xunil76 on 2008-01-18
i finally got this all figured out on Xubuntu....apparently, there is no VNC server installed by default in Xubuntu, so i ended up using [this article](https://help.ubuntu.com/community/VNC) to get tightvnc server set up on my system.  i only found this out after  multiple hours of searching & reading, so hopefully this will help someone else not have to waste as much time doing the same thing.....



also, a couple of other things to note....

in step #3, the commands could be shortened to a single command line:
```
sudo apt-get install openssh-client openssh-server
```



and in step #4, there is a typo.
```

mkdir -p ~/.ssh
chmod 700 **[COLOR="Red"]~./ssh[/COLOR]**
cd ~/.ssh
ssh-keygen -t rsa
```
should actually be:
```

mkdir -p ~/.ssh
chmod 700 **[COLOR="Red"]~/.ssh[/COLOR]**
cd ~/.ssh
ssh-keygen -t rsa
```

---

### Post by xunil76 on 2008-01-26
i also have another question about using SSH/VNC....how much bandwidth does SSH by itself use?  since it's only text-based, i'd assume that it isn't much, but i'm not quite sure how much the encryption uses on top of the text transfer.

is it less than a standard VNC connection that doesn't use an SSH tunnel?

---

### Post by gaten on 2008-01-26
> i also have another question about using SSH/VNC....how much bandwidth does SSH by itself use? since it's only text-based, i'd assume that it isn't much, but i'm not quite sure how much the encryption uses on top of the text transfer.

is it less than a standard VNC connection that doesn't use an SSH tunnel?

I'll just about guarantee that VNC uses more than SSH. This is because VNC basically sends screenshots of your desktop in rapid succession (compressed, of course). Like you said, SSH sends encrypted text. 

The point is security, not speed. Also, if you control both computers, you might want to look into FreeNX, its faster than VNC and has SSH already built in.

---

### Post by xunil76 on 2008-01-27
yeah, i'm not worried so much about the speed, the speed is fine....i was just curious as to how much actual bandwidth the SSH connection uses, since i don't want to use up too much and get in trouble at work.  i've used VNC for a while now, and have never really been griped at (although i've been griped at for other stuff and made to stop, like streaming audio at 16k/s :lolflag: )

---

### Post by gaten on 2008-01-27
Ahh I see. I don't think that will be a problem, ssh is pretty low on the bandwidth scale.

---

### Post by daflame on 2008-01-28
> **gaten said:**
> I'll just about guarantee that VNC uses more than SSH. This is because VNC basically sends screenshots of your desktop in rapid succession (compressed, of course). Like you said, SSH sends encrypted text. 

The point is security, not speed. Also, if you control both computers, you might want to look into FreeNX, its faster than VNC and has SSH already built in.

I am a programmer and I can bring some insight in these matters.  I have to say that your forum is impressive and I respect your high praises of FreeNX.  I use it for my employees to log into to do their work from home.  I have setup a forum on FreeNX here should you want to try it out:
[http://ubuntuforums.org/showthread.php?t=620057](http://ubuntuforums.org/showthread.php?t=620057)

As for the SSH tunnel and its bandwidth usage. An encryption protocol always adds transmission overhead, because in order to encrypt the data it adds noise using a very large prime number as the seed for that noise.  However, SSH also has a compression technique (if you enable it) that reduces the bandwidth loss to less than it would be normally.  My experiences have generally been about 4 times the bandwidth in cost maximum.

---

### Post by Kelogasi on 2008-01-31
Great HowTo! I added a couple of features from [Tichondrius's post]("http://ubuntuforums.org/showthread.php?t=122402") and [TwoWordz's post]("http://ubuntuforums.org/showthread.php?t=254149") to make a headless, multiuser, SSH only Gnome Ubuntu AMD64 machine. 

And in under 30 minutes no less!

Thanks!

---

### Post by philidox on 2008-01-31
I"m gonna try this out everyone is on ur nuts for this tutorial must be good

---

### Post by nisarg on 2008-02-28
great write up
finally got it working *i think*
port 53 seems to have done the trick. I was initially unable to connect via any other 'higher' ports.
One minor annoying thing - its seems i cannot connect from my local internal home network using the dyndns hostname. When I try I get a message stating - "Connection refused". I can however connect fine using the ip (local ip).
So i need to have two configurations one home network using the local ip and one external using the dyndns name; which isnt a major problem to be honest, i can live with it - just curious to learn what could the issue be? Are these dynamic hosts not designed to be seen from behind the router altogether or is this something i can configure?   
Any ideas? 
cheers

---

### Post by jonjonz on 2008-03-05
Another Thank You for taking the time to write a much needed recipe for aspiring new admins.  

I had set up my first ubuntu box two  years ago using a how to that has since vanished from the web, so when I was given a new server recently I have been looking high and lo for another guide on how to do this.  Most of what I could find now would have only part of the information, but never all of it in one place since it involves 3 components, ssh, the client, and some very specific settings.

Thanks again.

---

### Post by BlizzofOZ on 2008-03-18
I did the above... created a id_rsa, id_rsa.pub and authorized-keys and CAT id_rsa.pub to authorized_keys.

Next is where my confusion comes in... which file do I copy to my usb device? I think it is the private id_rsa file, correct? Can I connect my usb drive to the server? How do I see it and how do I copy the file to the drive?
Can I copy the file to my usb drive using Samba? I tried this but I get an error of:
"Cannot copy id_rsa: Access is denied Make sure the disk is not full or write-protected and that the file is not currently in use"
I am able to copy the id-rsa.pub file over, so my guess is a permissions problem on that file.

Next, once on the usb drive, I can connect to my Win XP computer and open the id_rsa file with puttygen?

---

### Post by heatpumpcontrol on 2008-04-04
First let me thank you for this howto. It is just what I was looking for. More of a GUI type.  

Oh, one thing which I think is an error and I had to correct is in step 4

```

Code:

cat ~/.ssh/[COLOR="Red"]id.pub[/COLOR] >> authorized_keys
chmod 600 authorized_keys


```


I had to change to [COLOR="Red"]id_rsa.pub[/COLOR]

I have some issues though... please help.

I have set it all up on two machines ,Ubuntu each and on Virtual XP from one of the machines. Each time I try to connect to either server, I'll get an Authentication failure message after I've entered the password. If I remove the password from the server.....whichever I select to be the server, I connect smoothly. 

Now, on my laptop, after I click on 'Open' on putty, the putty window disappears and I never get the black session window where I can enter my credentials. This happen no matter which server I select in putty.

I have set up two sessions in putty and each server has it's own port forwarded so the ssh keys work but the laptop will not start a session for me as the other two (ubuntu and virtual xp) will.

Thanks again.

---

### Post by heatpumpcontrol on 2008-04-05
After some more searching, I found:

After enabling the remote desktop password, enter your password and hit the return key.... this helped my situation with the system giving me an Authentication failure...


Still having the issue with the laptop not giving me the black putty window though. Will post anything I find.

---

### Post by gaten on 2008-04-07
BlizzofOZ:
>  Next is where my confusion comes in... which file do I copy to my usb device? I think it is the private id_rsa file, correct? 
That is correct. Make sure the permissions on the USB driver are 600 and try copying it again. If it doesn't work for some reason, just sudo copy it.

>  Next, once on the usb drive, I can connect to my Win XP computer and open the id_rsa file with puttygen?

I'm not sure I understand what you're asking. Are you connecting **from** or **to** your Win XP box? This tutorial teaches you how to connect **from** your Win XP box **to** your Linux box. 

heatpumpcontrol:
> Now, on my laptop, after I click on 'Open' on putty, the putty window disappears and I never get the black session window where I can enter my credentials. This happen no matter which server I select in putty.

You should enable logging in puTTY and see what it says. On the left hand side I believe there is a 'Logging' option, and you can select what type of logging you want. Use the most verbose and look in that file after the connection failed, and post what it says up here.

And thanks for the correction, **id_rsa.pub** is the default name for the public key file.

Sorry it took me so long to get back to you guys, I was on vacation ;)

---

### Post by a-converted-sparky on 2008-04-29
Many thanks, Im a total Newb and this was a walk in the park,
great guide!

---

### Post by vitalik on 2008-05-06
I keep getting this:

#ssh -v xxxxx.gotdns.org -p 47000
OpenSSH_4.7p1 Debian-8ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xxxxx.gotdns.org [69.2xx.49.1xx] port 47000.
debug1: connect to address 69.2xx.49.1xx port 47000: Connection refused
ssh: connect to host xxxxx.gotdns.org port 47000: Connection refused


I am not sure if this is the port problem, I have opened the port on machine from which I am trying to connect.
Was I supposed to do port forwarding on the machine to which I am trying to connect?

---

### Post by dynamethod on 2008-05-08
At home i have hardy with sshd running listening on port 55741(and port forwards etc etc etc)

and at work i use putty and tightvnc, i setup putty to tunnel vnc through port 55741

only thing is, could the guys in the IT department find out if im ssh'ing to my home pc?

if so, then could i tell my sshd server at home to listen on port 80, thus tunneling in port 80 at work? so that it looks like http traffic? is this a possibility or do i have my wires crossed?

---

### Post by nisarg on 2008-05-08
I do more or less the same kind of stuff. With difference that I connect over port 53, and just use SSH, no VNC. 
I would have thought, that they might be see some traffic  on an unusual port and block it if they like. On the other hand when you can use the port when its open? So probably its just not your company's IT department's policy to block everything. So, you should be fine. If it does stop working you can try connecting over port 80 or 53. 

> **dynamethod said:**
> At home i have hardy with sshd running listening on port 55741(and port forwards etc etc etc)

and at work i use putty and tightvnc, i setup putty to tunnel vnc through port 55741

only thing is, could the guys in the IT department find out if im ssh'ing to my home pc?

if so, then could i tell my sshd server at home to listen on port 80, thus tunneling in port 80 at work? so that it looks like http traffic? is this a possibility or do i have my wires crossed?

---

### Post by dynamethod on 2008-05-08
hehe, actually what ive done now, because i realised that because im using apache2 on my home machine i cant use port 80, so since i dont  use SSL on my webserver(no need for it, no sensitive info on there, basically there as an experiment) im going to ssh via port 443 mwuaahahahaha

---

### Post by VipX1 on 2009-09-22
I just like to add I found a lovely command that makes the key and then connects via ssh to the server and updates the authorized_keys2 file and sets permissions at the same time. If you had sshd working on the server and could log in with a standard user/password but want to upgrade it to a dsa key set up this is perfect.```
ssh-keygen -t dsa -f ~/.ssh/identity && cat ~/.ssh/identity.pub | ssh -vv user@host  'sh -c "cat - >>~/.ssh/authorized_keys2 && chmod 600 ~/.ssh/authorized_keys2"'
```
Now if I can switch off password access altogether and only allow clients that have a key in the host's Authorized_keys file to log in I'll be happy. "More reading to do!"..:)

---

### Post by SneakPeak on 2009-10-05
[Solved] Refer to the end part of this post.
Thanks for the Post

I am able to connect using PortaPutty.  I get a terminal login window it prompts:

login as:

I type in my user name for my remote machine

And then I have to enter the password that I created for the key generation process.

I then have what I think is a normal ssh terminal connection.  I can run normal linux terminal commands and I can see the directories on the host machine.

The problem I have is with VNC.  I am trying to use TightVNC viewer.  The version quoted in the orignal post doesn't seem to be available anymore.  I am using a java version.  I have to type

java VncViewer Host 127.0.0.1::50000 port 5900

Unfortunately this doesn't work.  I get the following error message:

```
Initializing...
Connecting to 127.0.0.1::50000, port 5900...
Network error: server name unknown: 127.0.0.1::50000
java.net.UnknownHostException: 127.0.0.1::50000
        at java.net.PlainSocketImpl.connect(Unknown Source)
        at java.net.SocksSocketImpl.connect(Unknown Source)
        at java.net.Socket.connect(Unknown Source)
        at java.net.Socket.connect(Unknown Source)
        at java.net.Socket.<init>(Unknown Source)
        at java.net.Socket.<init>(Unknown Source)
        at RfbProto.<init>(RfbProto.java:229)
        at VncViewer.connectAndAuthenticate(VncViewer.java:325)
        at VncViewer.run(VncViewer.java:158)
        at java.lang.Thread.run(Unknown Source)
```

Any ideas?

OK so I managed to solve this problem.  The first thing is that the Port used in this step:

> # Now select "Tunnels" on the left menu. Under "Source Port" pick a large number that isn't a service port (like 50000).
# Under "Destination" type in "127.0.0.1:5900". That tells ssh to tunnel any service connected to port 50000 to port 5900 (VNC) on the local interface (and the local interface will be your home computer, once we connect to it),

Must be the same as the port used in this step (as far as I can figure out):

> Now, using your favorite text editor, open up /etc/ssh/sshd_config. A couple of changes are going to be made to this file. Find the line:
Code:

Port 22

And change it to
Code:

Port 47000

Make sure there is no # in front of Port. You don't have to pick 47000, but keep in mind what was said before.

(So 47000 instead of 50000)

Then the java VncViewer command line must look like this:

```
java VncViewer HOST 127.0.0.1 Port 47000
```

I really am just about completely ignorant about how this stuff works but the above approach worked for me.

Thanks 

Sneaks

---

### Post by SneakPeak on 2009-10-06
[Solved] Another question

Before working through this Howto I was able to connect from my laptop to my desktop over the local network using the following command:

```
ssh username@192.168.1.102
```

Since applying the Howto I can no longer do this I get the following error message:

```
ssh: connect to host 192.168.1.102 port 22: Connection refused
```

Help please!

Ok I have figured out that if I reverse this step on the host machine:

Now, using your favorite text editor, open up /etc/ssh/sshd_config. A couple of changes are going to be made to this file. Find the line:

```
Port 22
```

And change it to

```
Port 47000

```

(So I change 47000 back to 22)  I can once again access my desktop from my laptop.  

So it seems if I use ssh on the client it automatically tries to access the host on port 22 but I can't figure out how to make it rather try to access on port 47000!

Help would be appreciated.

Ok solved the problem.  Really simple:

```
ssh -p 47000 username@192.168.1.102
```

Sorry for the dumb question.
 

Thanks

Sneaks:(

---

### Post by theDaveTheRave on 2009-11-02
Hello All.

I've got a question, with a problem.

I've got SSh working fine for 2 users, both are able to ssh (via putty from a vista system) into ubuntu.

Both are able to start up a vnc server session, independantly of one another.

so if I have 2 users, lets say identified with the following.

user: me           pwd: enter
user: notMe        pwd: LogIn

so both 'me' and 'notMe' can log in via ssh, and do everthing required (both are administrators), including starting the vnc server.

However only the user 'me' can log into a vnc session.

How do I add in the 'notMe' user to enable them to log in using thier password?

I would also like to know how to change passwords / remove user from being able to log in remotely etc.

I'm not worried about re-usable sessions. As access to this terminal isn't required that often.


Thanks in advance for you help  / assistance.

David

__more info ____

Ok so I've just chatted to my colleague who was trying to log into this terminal, and I've undestood his problem.

I recently changed the password for the user, staying with the above notation, I change the 'notMe' users password in the system from 'LogIn' to 'newLogIn' stupidly I never changed the password for vnc!

so I'm going to have a guess that all I need to do is run the command.

```

vncpasswd /root/.vncpasswd

```

However, and this is holding me back momentarily from acting on this. If I do does it change the password for ALL the users? or just for the user that runs the command?

Ok, I've tried changing the password, and no luck? Maybee I should re-boot the system, just to check....

back soon.

Ok suddenly I realised what the "proper" solution may be.

So you have multiple users on the system for people to log into.

for each user that you have created "access" for you should have a "hidden" .vnc directory change into this directory and then run the following command.

```

sudo vncpasswd

```
 
you will then requested for your "sudo" sign on, and then you will be asked for the new vncpassword (twice for confirmation). That should sort things out.

my error was running the vncpasswd command without sudo privileges. I (stupidly) made the assumption that if I ran it from the users directory sudo privileges wouldn't be required. In fact the command <vncpasswd> looked as though it had done the correct thing originally, but obviously the config file isn't writable by the user - obviously related to the instalation being done using sudo!

---

### Post by rileinc on 2010-01-17
I'm a little embarrassed to ask this, but how do you connect to the VNC server (set up as per OP's instructions) from an Ubuntu machine?

I got the server working fine and was able to tunnel from Windows, but I never learnt how to do the same from Ubuntu.

I tried following gaten's instructions in post #44 by doing "ssh -D 2000 [remote.computer]" then connect to 127.0.0.1::2000. That didn't work; all I get is a blank screen (compiz is disabled). 

Please note that I run x11vnc instead of vino on the remote machine.

Can anyone enlighten me? Thanks in advance.

---

### Post by krunge on 2010-01-17
> **rileinc said:**
> I tried following gaten's instructions in post #44 by doing "ssh -D 2000 [remote.computer]" then connect to 127.0.0.1::2000. That didn't work; all I get is a blank screen (compiz is disabled). 

The ssh -D option creates a SOCKS proxy. Run "man ssh" for the details on -D. This means the viewer connecting to it needs to know how to interact with a SOCKS proxy and probably be told it is using such a proxy.  Did you do something like that on Windows? (BTW which viewer did you use?)

From linux you might be better off not using -D and simply using the normal -L port redirection. Assuming x11vnc is listening on port 5900:
```

ssh -L 5900:localhost:5900 [remote.computer]

```
then point your vncviewer at 127.0.0.1:0  (which should be the same as localhost:0 or 127.0.0.1::5900)

OTOH, some linux vncviewers may support SOCKS proxies (I know my hack SSVNC does; I think it is in some of the repos), perhaps vinagre does too (haven't tried.)

---

### Post by rileinc on 2010-01-17
> **krunge said:**
> The ssh -D option creates a SOCKS proxy. Run "man ssh" for the details on -D. This means the viewer connecting to it needs to know how to interact with a SOCKS proxy and probably be told it is using such a proxy.  Did you do something like that on Windows? (BTW which viewer did you use?)
Nope I didn't do that on Windows; I followed OP's instruction (portaputty + tightvnc viewer) for Windows and it worked fine. On Ubuntu, I don't know the specific options to make SSH tunnel services, so I looked around and tried post #44's method with both remote desktop viewer and terminal server client, and that didn't work. I guess I should've read the manual first :/
> **krunge said:**
> From linux you might be better off not using -D and simply using the normal -L port redirection. Assuming x11vnc is listening on port 5900:
```

ssh -L 5900:localhost:5900 [remote.computer]

```
then point your vncviewer at 127.0.0.1:0  (which should be the same as localhost:0 or 127.0.0.1::5900)
That worked. Thank you very much :)

---

### Post by cbcb on 2010-10-22
Just another thank you for this! There is nothing better than learning something while creating something useful.

---

