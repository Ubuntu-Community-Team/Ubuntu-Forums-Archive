---
title: "SSH questions"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by P05TMAN on 2011-09-09
Hi there, everyone! 

I just installed Ubuntu 11.04 to dual boot with Win7 on my home PC. Ran into a few snags but go that all worked out! :) I'd like to pull away from Windows as much as possible, but I keep it around for certain programs that are mostly guilty pleasures. :oops:

My current goal for Ubuntu is to be able to access my desktop from anywhere, be it work, my cell phone (Android) or even from my school. I have a portable SSH client on my USB, but my challenge is seting up ssh correctly in Ubuntu. I've set up an SSH server once before, but that was on a Fedora VM. I found Mr. Bohi.zazen' s excellent guides via wiki, but I'm still unsure which authentication would be best for my desires. Obviously, I don't want to be open for attack, but I also am not entirely sure how SSH & RSA keys really would work for me if I want to truely access my PC from anywhere on any PC.
Could someone be so kind as to shed some of their own personal experience or insight? Even point me in the right direction?

Thanks in advance, everyone & I'm happy to be a part of this community!

---

### Post by Dangertux on 2011-09-09
Honestly if keys don't work for you a strong password that you change frequently would be the best bet. By strong password I mean AT LEAST 16 characters preferably more containing upper case , lower case, numbers, symbols and white space.

Additionally if you go that route make sure you are using something like denyhoste or fail2ban

---

### Post by heyandy889 on 2011-09-09
Hi, P05TMAN! Welcome to the forums! ):P

If you're accessing Ubuntu from Ubuntu, there's a built-in Remote Desktop application. I haven't used it successfully, but that might be somewhere to start.

As far as SSH, what I've found to work is "ssh-server," which is a subset of "openssh," which comes (partially?) pre-installed in Ubuntu. Try popping open Synaptic Package Manager and installing "openssh-server".

Agreed, I am also really trying to get away from Windows. At first, I used Ubuntu because it was convenient for my systems programming course. Then, after my operating systems course, I was hooked. Compiz, bash, and GUI connect to server are features that I really miss when I use Windows. Oh, and sudo!

Rock on, dude, and happy hacking!

---

### Post by P05TMAN on 2011-09-09
So once I set up the SSH server on my system, do I have to configure my router also since my IP is local to my home network?

---

### Post by Dangertux on 2011-09-09
If you want it to be accessible from outside you would have to forward port 22 (or whatever alternate port you assigned in your sshd config) to the internal machine in question.

---

### Post by P05TMAN on 2011-09-09
> **Dangertux said:**
> If you want it to be accessible from outside you would have to forward port 22 (or whatever alternate port you assigned in your sshd config) to the internal machine in question.
  
Sorry to be a fuss, but what do you mean by 'internal machine'? I would forward port "so & so" to the local machine with the SSH server?

---

### Post by Dangertux on 2011-09-09
> **P05TMAN said:**
> Sorry to be a fuss, but what do you mean by 'internal machine'? I would forward port "so & so" to the local machine with the SSH server?

Not a problem. Yes, you are correct. The machine with the SSH server.

---

### Post by rolandrock on 2011-09-09
Here is a guide that includes links to 'port forwarding' instructions amongst other things:
[http://ubuntuforums.org/archive/index.php/t-247563.html](http://ubuntuforums.org/archive/index.php/t-247563.html)

If dyndns is no longer free, try no-ip.com for a static address.

---

### Post by P05TMAN on 2011-09-09
> **Dangertux said:**
> Not a problem. Yes, you are correct. The machine with the SSH server.

Excellent! Thanks! 

So if I configure port forwarding, I can avoid having to configure my router, right? Then I could essentially set up like a VNCOverSSH as outlined here: [https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH](https://help.ubuntu.com/community/VNC?action=show&redirect=VNCOverSSH), correct? Or would VNCOverSSH be an unnecessary step?

---

### Post by wojox on 2011-09-09
You would have to configure port forwarding from the router if you want to connect from outside your LAN, ie work. The dameon will listen for incoming requests.

SSH uses default port 22.

---

### Post by madverb on 2011-09-09
I have my SSH set up with just password protection. Make sure you can't log on to SSH as root. I use denyhosts as well. It's amazing how often I have random people trying to log on. Have about 3 new IPs banned everyday.

Info for tunneling via putty in Windows as well: [http://simplexion.wordpress.com/2011/03/08/howto-tunnelling-connections-over-ssh/](http://simplexion.wordpress.com/2011/03/08/howto-tunnelling-connections-over-ssh/)

---

### Post by P05TMAN on 2011-09-11
> **madverb said:**
> I have my SSH set up with just password protection. Make sure you can't log on to SSH as root. I use denyhosts as well. It's amazing how often I have random people trying to log on. Have about 3 new IPs banned everyday.

Info for tunneling via putty in Windows as well: [http://simplexion.wordpress.com/2011/03/08/howto-tunnelling-connections-over-ssh/](http://simplexion.wordpress.com/2011/03/08/howto-tunnelling-connections-over-ssh/)

In your opinion, would it be best to use SSH or RSA keys then? I want to be able to have root access to my home PC. ON the other hand, I'm not entirely sure how I'd set up an SSH key from my work computer, for example. Would having a firewall be of any use?

---

### Post by SeijiSensei on 2011-09-11
If the server is running Ubuntu, then you'd achieve root access the same way you would if you were sitting at the console.  Log in with your normal account using SSH, then use sudo to perform root operations.

You might find it simpler to tunnel X over SSH and run just the programs you need rather than exporting your whole desktop.  Try, for instance, logging into the server using the command "ssh -X user@host", then, at the remote prompt, run a simple X application like xterm or xeyes.  You'll see the application pop up on the desktop of the client computer.

Setting up keys is the best approach.  If you configure the SSH server to only accept key-based authentication, you'll have both strong security and simplicity of use.

As for using your work computer, the procedure is the same.  The easiest solution is to copy the contents of your laptop's $HOME/.ssh to the identical directory on your work machine.  Easiest and safest way is to use a USB key drive or the equivalent.

---

### Post by P05TMAN on 2011-09-11
> **SeijiSensei said:**
> If the server is running Ubuntu, then you'd achieve root access the same way you would if you were sitting at the console.  Log in with your normal account using SSH, then use sudo to perform root operations.

You might find it simpler to tunnel X over SSH and run just the programs you need rather than exporting your whole desktop.  Try, for instance, logging into the server using the command "ssh -X user@host", then, at the remote prompt, run a simple X application like xterm or xeyes.  You'll see the application pop up on the desktop of the client computer.

Setting up keys is the best approach.  If you configure the SSH server to only accept key-based authentication, you'll have both strong security and simplicity of use.

Thanks! I'll try with the SSH keys & post my results and/or further questions

---

