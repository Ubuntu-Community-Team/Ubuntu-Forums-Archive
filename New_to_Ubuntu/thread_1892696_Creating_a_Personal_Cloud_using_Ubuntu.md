---
title: "Creating a Personal Cloud using Ubuntu"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by HookAsnooK on 2011-12-08
Situation:
 I am getting my new Laptop in the mail next week and I have this idea that I could create my own personal "cloud" (or server) out of my old laptop.

Question:
 What are your suggestions for the best way of going about this?

What I have:

 Old Laptop Specs:
  Sony Vaio FZ
  -Intel Core 2 Duo 2.00 GHz
  -4.00 GB RAM
  -250 GB Hard Drive
  -Integrated Graphics

 New Laptop Specs:
  Sony Vaio SE
  -Intel i7 2.8 GHz (3.5 Turbo)
  -8.00 GB RAM
  -640 Hard Drive
  -AMD Radeon 6630m

 As an engineering student at a University I have access to some server software and other Microsoft software.

Additional Questions:
 Do you need to have a special program to boot Ubuntu at start instead of Windows 7?
 Are Microsoft software compatible with Ubuntu?

Right now I am just exploring Ubuntu through an external hard drive. I intended to follow this link: [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/]("http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/")
 
I guess that is a good place to start. Thanks for the help in advance.

---

### Post by philinux on 2011-12-08
[https://one.ubuntu.com/](https://one.ubuntu.com/)

Hope that is what you want.

---

### Post by lykwydchykyn on 2011-12-08
people use the term "cloud" to mean everything from webmail to file storage to virtualized server farms.

What precisely do you want to do with your old laptop?

---

### Post by HookAsnooK on 2011-12-08
I'd like to be able to access my old laptop from anywhere. Be able to download/upload whatever i'd like. Maybe use it to host my website. Run small video game servers. Remote access websites like pandora when Im not in the states. Etc.

---

### Post by bluexrider on 2011-12-08
this is the Ubuntu Server Guide in .pdf

 [https://help.ubuntu.com/10.04/serverguide/C/serverguide.pdf](https://help.ubuntu.com/10.04/serverguide/C/serverguide.pdf)

---

### Post by mastablasta on 2011-12-08
no there is a special Ubuntu cloud package (see this site, top right button for download). 

[http://www.ubuntu.com/business/cloud/overview](http://www.ubuntu.com/business/cloud/overview)

also having a notebook for server is a bit strange. unoless things changed the disks and all that in notebook are not really as durable and also notebooks are not really ment to run nonstop.

no, Windows software is not compatible with Linux. if it was, linux would probably be called windows. some software can be made to run via Wine.

the "special programme" to boot ubuntu is called boot manager (ubutnu uses GRUB). it's installed when you install Ubuntu.

---

### Post by HookAsnooK on 2011-12-08
Thanks for your responses. I'm going to keep exploring my options and see where it gets me. I like some of the suggestions made so far.

---

### Post by pierreyy on 2011-12-08
From what i know alot of engineering software runs exclusively on windows so im pretty sure that you wont be able to run your software...sorry

---

### Post by HookAsnooK on 2011-12-08
My intention isn't to use the computer on a day to day basis. It's turn it into a personal server.

---

### Post by lykwydchykyn on 2011-12-08
> **HookAsnooK said:**
> I'd like to be able to access my old laptop from anywhere. Be able to download/upload whatever i'd like. Maybe use it to host my website. Run small video game servers. Remote access websites like pandora when Im not in the states. Etc.

- First, (assuming you have a regular residential ISP with a non-static IP) register with a dynamic dns service like dyndns.org and set up the dyndns client on your server.  

- install openssh-server on the laptop

- Forward a port on your router to port 22 on the laptop.

Now you have shell access to your laptop from anywhere in the world, and can use sshfs (on *nix) or WinSCP (on windows) to access files.  You can [create an ssh]("http://www.revsys.com/writings/quicktips/ssh-tunnel.html") tunnel to pipe encrypted internet through your laptop from anywhere in the world.

You can also install [nxserver](http://www.nomachine.com) to have remote desktop over ssh.

For a website, install apache2 or lighttpd and forward port 80 on your router to port 80 on the laptop.

---

### Post by DapperMe17 on 2011-12-09
Nice post, or even easier than nxserver...X2Go.

:popcorn:

---

### Post by HookAsnooK on 2011-12-09
> **lykwydchykyn said:**
> - First, (assuming you have a regular residential ISP with a non-static IP) register with a dynamic dns service like dyndns.org and set up the dyndns client on your server.  

- install openssh-server on the laptop

- Forward a port on your router to port 22 on the laptop.

Now you have shell access to your laptop from anywhere in the world, and can use sshfs (on *nix) or WinSCP (on windows) to access files.  You can [create an ssh]("http://www.revsys.com/writings/quicktips/ssh-tunnel.html") tunnel to pipe encrypted internet through your laptop from anywhere in the world.

You can also install [nxserver](http://www.nomachine.com) to have remote desktop over ssh.

For a website, install apache2 or lighttpd and forward port 80 on your router to port 80 on the laptop.

I'm going to consider this. I'm not exactly the most knowledgeable on this matter, but reading and forums will get you a lot. 

Also, I've been exploring Ubuntu and it's simplicity is really nice and ideal for my taste. I like the minimalist feeling. The downfall is that I won't be able to run some of the windows programs or games. Is there a stream less method for running windows programs in Ubuntu?

Ideally I would like to maintain the simplicity and elegance of Ubuntu.

---

### Post by lykwydchykyn on 2011-12-09
> **HookAsnooK said:**
> I'm going to consider this. I'm not exactly the most knowledgeable on this matter, but reading and forums will get you a lot. 

Also, I've been exploring Ubuntu and it's simplicity is really nice and ideal for my taste. I like the minimalist feeling. The downfall is that I won't be able to run some of the windows programs or games. Is there a stream less method for running windows programs in Ubuntu?

Ideally I would like to maintain the simplicity and elegance of Ubuntu.

The most fool-proof way is to run them in a VM.  Some VM software (virtualbox, e.g.) has a "seamless mode" which allows programs to appear as if they were normal Ubuntu programs, but it's still a considerable resource overhead and complication.

You can sometimes run windows programs in Wine.  I've never managed to get a windows program running satisfactorily in Wine and stay running over the long-haul.

The best thing to retain simplicity and elegance is to find an alternative that runs natively in Ubuntu.

---

### Post by MyUserControl on 2012-02-07
Hello

I saw the name of the thread and I wanted to ask the participants something. I'm new with servers and cloud, but I want to learn.

Can you explain me (step by step, if someone has any time/nerves) how can you establish cloud with Ubuntu if you have 10-15 computers... we make those compures act like servers? how? on witch to instal Ubuntu cloud software? Pls tell me more :)

---

### Post by CharlesA on 2012-02-07
You could try Ubuntu Enterprise Cloud, but I don't have any experience with it.

I think you get get hosting on the Amazon EC2:
[http://aws.amazon.com/ec2/](http://aws.amazon.com/ec2/)

---

