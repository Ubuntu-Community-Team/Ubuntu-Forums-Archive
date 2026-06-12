---
title: "Virtualbox and Windows network isues"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Joshoua on 2008-05-05
Hi.I am a beginner at linux and I am facing a few problems with Virtualbox.
I have managed to install it and I also managed to get windows to work as a virtual machine just fine.
Everything runs OK and the virtual machine even has internet.The guest additions are also installed succesfully.
The only problem is that I can't get the virtual maching to connect to our local windows network.
The computer that hosts the Virtualbox (which in turn hosts a Windows virtual machine) is connected to a network with Windows computers.
I want to be able to access shared folders on Windows computers on the network,through the Virtual machine on Virtualbox.
From what I have seen, the Virtualbox does not route data when they are heading for the local network.
Anyhow,I am really new at this..any help would be much appreciated.
Thanks in advance!!

---

### Post by bluefrog on 2008-05-05
explain the topology of your network.

linux host IP?
your windows network subnet?

Is your linux host able to connect to the windows shares?

---

### Post by Dougie187 on 2008-05-05
And how are you trying to connect to the windows shares?

---

### Post by Joshoua on 2008-05-06
Thanks for the replies!
My linux host IP is 192.168.0.37 and it's acquired by a Windows DHCP in my network. The Windows is network is on 192.168.0.* .
My Linux host can connect to the Windows shares just fine.
The Windows XP VM,gets an IP on 10.0.2.* network and a gateway of 10.0.2.2 (which supposedly is the Linux host Virtual adapter).
The strange thing is that, the VM acquires the DNS suffix of my Windows network.
When I try to ping any computer on my Windows network through the VM there is no reply.
I also tried to connect using Start->Run and by browsing the network through network places,nothing.
Any ideas?
I believe it should be a configuration issue with the Virtualbox. I think it acts like some kind of firewall and blocks requests or does not redirect requests to the Windows network.
I don't know I am just guessing,you see the VM can connect to the Internet just fine..

---

### Post by Dougie187 on 2008-05-06
I dont know if this will help, but it might.
[http://ubuntuforums.org/showthread.php?t=596912](http://ubuntuforums.org/showthread.php?t=596912)

---

### Post by Calash on 2008-05-06
It sounds like your Windows VM is set to use NAT for it's communication.  Can you browse the web with the VM? (Edit, you said it can in the post..sorry about that.)

I do not know if Virtualbox NAT can be configured to access the shares.  I was playing around with it last night and could not do it myself.

What does work, but requires a bit more configuration, is to create a bridge on your host that then can be used by the VM.  The end result is that your VM gets a real IP from your router and looks like a normal machine on the network.

What version of Virtualbox are you running?  The very latest, 1.6, has some issues with this type of configuration.  It works, but you have to take an extra step or two.

---

### Post by bodhi.zazen on 2008-05-06
You have several options for networking in Virtualbox. NAT or Brigdged.

It sounds like you are currently using NAT which allows "simple" networking, you need to use bridged.

You can see this : [http://ubuntuforums.org/showthread.php?t=346185](http://ubuntuforums.org/showthread.php?t=346185)

But actually the virtualbox Documentation has a very nice and easy to follow networking section as well :

[http://www.virtualbox.org/download/1.6.0/UserManual.pdf](http://www.virtualbox.org/download/1.6.0/UserManual.pdf)

---

### Post by Joshoua on 2008-05-06
Hmm..
It works now.
I played a bit around and It works ok.
The problem is I haven't noted what I did :-)
I mean,I searched around and tested various things..
Anyhow I wil try to find out and let you know,thanks for the replies though.
:-D

---

