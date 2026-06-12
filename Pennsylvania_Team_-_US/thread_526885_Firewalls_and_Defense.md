---
title: "Firewalls and Defense"
date: 2007-08-16
forum: Pennsylvania Team - US
---

### Post by jpr13 on 2007-08-16
I just installed Ubuntu and it was totally painless. I had a bad feeling the bootloader and device detection was going to be hell, but i had zero problems.

So here is my first post-install questions:

1) What firewall should I use?

2) Antivirus. I am guessing that I should get it but I don't have to have it running in the background at all times like windows.
Is this the case?
I was going to use avast, since that is my solution on the windows side of things.


                                            Jason

---

### Post by eentonig on 2007-08-16
1. Assuming you're not running any public services on your computer, forget about a firewall. By default, ip-tables comes wit the kernel, but it's left unconfigured in Ubuntu. There's no need to activate it, as there are no open ports to connect to.

2. If you need it depends on how actively you want to protect the windows users you get into contact with. Virusses for Linux are practically non-existant for the moment. so even if a friend sends you an infected mail, it wont harm you. If you install a virusscanner, it's only goal will be to prevent to sent forward a virus to your windows friends.

---

### Post by misfitpierce on 2007-08-16
Firestarter is a great way to configure the ip-tables that come in ubuntu. Prob easiest firewall in world to setup and its very light. Wont even notice its running :)

---

### Post by elizabeth on 2007-08-16
First, I'd recommend that you look through all the things running on your machine and shut down what you're not using (feel free to ask here if you're not sure). The best way to protect yourself is to limit the services you're running that might someday be found to be exploitable. Other things are obvious, don't give accounts on your machine out to people you don't trust, only give administrator accounts to people you *really* trust, make sure your password is hard to guess, keep up with security updates (Ubuntu should tell you when your machine requires an update).

> **eentonig said:**
> If you install a virusscanner, it's only goal will be to prevent to sent forward a virus to your windows friends.

I just want to stress here that virus scanners in Linux (such as clamav, which is in Ubuntu) are designed for use on Linux mail servers to scan mails for viruses before sending them to the clients connecting with Windows.  If you're not running a mail server that's delivering outside mail to Windows PCs a virus scanner is not required for Linux itself and I'm not sure that good options exist at this time.

---

### Post by jpr13 on 2007-08-16
Thank you for all the answers.

As I understand it the firewall programs just control ip tables within the kernal itself and let you config them. I downloaded firestarter but did not set it to run at start, I just got it so I could modify the tales if I had to. 
I will download a virus scanner just to learn how to use it.
And I will shut down services I don't need, I already shut some stuff off by using a speed/mem tweak page from the net.

I know linux doesn't need active programs, but after years of M$, its weird to be online and not have all sorts of defense up!!!


                                        Jason

---

### Post by BraveSirRobin on 2007-08-17
Technocrat.net has [a node](http://technocrat.net/d/2007/8/16/25071) with a link to an article about running virus scanners on Postfix/Debian that you might find useful.

P.S. I'm fairly new to Ubuntu, so I can't tell you how much overlap there is[n't] between the instructions in that article and how you would go about the same task on Ubuntu.

---

### Post by ubuntu27 on 2007-08-17
> **jpr13 said:**
> I just installed Ubuntu and it was totally painless. I had a bad feeling the bootloader and device detection was going to be hell, but i had zero problems.

So here is my first post-install questions:

1) What firewall should I use?

2) Antivirus. I am guessing that I should get it but I don't have to have it running in the background at all times like windows.
Is this the case?
I was going to use avast, since that is my solution on the windows side of things.


                                            Jason

There are virus that are NOT in the wild, some people call them "Lab (Laboratory) Virus". 

Read ["Security on Ubuntu"]("http://www.psychocats.net/ubuntu/security")

---

