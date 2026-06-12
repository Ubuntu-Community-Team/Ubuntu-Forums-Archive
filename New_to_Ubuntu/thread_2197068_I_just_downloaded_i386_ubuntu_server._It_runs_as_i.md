---
title: "I just downloaded i386 ubuntu server. It runs as i686??"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by mruiz408 on 2014-01-02
[SIZE=3][FONT=arial]I just downloaded i386 ubuntu server. After I login to the install it says GNU/LINUX 3.8.0-29-generic i686. My machine is a Intel® Core™2 Quad processor with 2 gigs of ram 
[/FONT][/SIZE]http://acersupport.com/acerpanam/desktop/0000/Acer/AspireM5630/AspireM5630sp2.shtml[SIZE=3][FONT=arial]
actually just check out this link because it has everything. 
Is it safe for me to run i686? I would prefer something that uses the least amount of power if that makes any difference.  What is i686? 
[/FONT][/SIZE]

---

### Post by 3rdalbum on 2014-01-02
i686 is the i386 instruction set, plus a few instructions extra that make certain things faster.

Your CPU supports i686 so you have nothing to worry about.

---

### Post by deadflowr on 2014-01-02
i686 is a 32-bit version.
Same as i386.
the i386 designation on the disk is simply a legacy naming scheme, nothing more.
i386,486,586,686 are all the same on the Ubuntu disk, basically 32-bit version.

Edit: so yeah, perfectly safe.

---

### Post by mörgæs on 2014-01-02
Your CPU is 64 bit, so you will get better performance with the 64 bit ISO.

---

### Post by mruiz408 on 2014-01-02
You're right, I looked it up and the Intel Core2 Quad processor is 64 bit, which is weird to me since the computer shipped out with Windows Vista x32 bit.
I am trying to setup a home server that will be connected to my computer and PS3 so I can share files through Samba and uPNP(I think). Right now I need to decide if I should just go with the Desktop version or the Server version to run my home file server. I ran into a couple problems with Ubuntu server trying to setup Samba though and I'm not sure if I should even keep trying because it seems so difficult. Would you recommend Ubuntu Server for file sharing like this or just stick with the desktop version? Would Ubuntu Server use less power than the Desktop version? Thank you for your help guys

---

### Post by 3rdalbum on 2014-01-02
If you are new to Ubuntu, use the Desktop version (or install a desktop on top of Server).

You can set up your Samba with a GUI tool called System-Config-Samba. When it is set up, you can stop running the GUI environment to save power.

---

### Post by mruiz408 on 2014-01-02
I'm not too new to linux but when it comes to using a terminal only kind of thing I get uncomfortable even with a guide off google. & if I do install Server and install GUI ontop of it, I would be able to switch in-between interfaces? The GUI environment would use more power than the black terminal screen? I am going to try System-Config-Samba and post back. I followed a guide earlier and it told me to install something called Kerberos and I had no idea how to set up that program.

---

### Post by 3rdalbum on 2014-01-02
> **mruiz408 said:**
> I'm not too new to linux but when it comes to using a terminal only kind of thing I get uncomfortable even with a guide off google. & if I do install Server and install GUI ontop of it, I would be able to switch in-between interfaces? The GUI environment would use more power than the black terminal screen?

Correct and Correct. The desktop GUI is just a set of programs running on top of the command line. You can turn off those programs with one terminal command to get back to just the black terminal screen. Not that running a desktop, idle, will use much more power anyway.

I'll also point out that the Core 2 Quad Q6600 is not an ideal CPU for running a low-power server. My home server, which sadly my parents have commandeered, uses an Intel Atom CPU which is a lot less power-hungry. Even that's rather inefficient these days... but I digress.

> I am going to try System-Config-Samba and post back. I followed a guide earlier and it told me to install something called Kerberos and I had no idea how to set up that program.

If this is a home server, you DO NOT need Kerberos. Samba is made first-and-foremost for large enterprise networks, so be aware that any manuals or guides you see online might assume you're trying to set up a large network and advise you to install all sorts of additional things. Samba on its own (with something like System-Config-Samba to do the initial configuration) is perfectly fine for a home network.

---

