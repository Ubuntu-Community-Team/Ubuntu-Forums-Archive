---
title: "Changing hostname"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by griffinmt on 2012-10-10
Just built a U12.04 system, now I want to permanently change the hostname I used, as well as the domain I selected. Using a terminal window, what commands would do this (via sudo).
 
Thanks,

---

### Post by DuckHook on 2012-10-10
You will have to edit the *hostname* file in */etc*

If you wish to use the command line editor, then:

```
sudo nano /etc/hostname
```If you wish to use the graphical editor, then:

```
 gksu gedit /etc/hostname
```Taking care (you are editing with root privileges), change the name in this file to the new name that you want.

If using nano, write the change to file. If using gedit, save. Make sure you exit either program cleanly (quit).

Repeat process with the file /etc/hosts 

Log out, then log in.

Check that the change has taken hold by starting terminal and typing:

```
hostname
```Not sure what you mean by the "domain you selected". Do you mean the workgroup name in a mixed Linux/Windows environment, or does your network run a DNS server?

---

### Post by critin on 2012-10-10
This is one of the helpful sites I've found, you should bookmark it.  lol

[http://www.liberiangeek.net/2012/04/common-tasks-to-perform-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/common-tasks-to-perform-in-ubuntu-12-04-precise-pangolin/)

There is also a page on changing workgroup name if that's what you meant.

I've found that reading tutorials like this helps me learn better than just blindly copy/pasting someone else's code.  Copying code is a great help, & I do it all the time, but learning where to go to learn how to do it yourself is more permanent.  IMO

---

### Post by bab1 on 2012-10-10
You also need to change the hostname in the */etc/hosts* file.

---

### Post by griffinmt on 2012-10-10
Thanks for the hostname change info.
The domain change in essence has nothing to do with any Windows systems, although the workgroup name used in windows systems would typacally be the same value in a local system. IE: host.sample.com belongs to domain sample.com and works with workgroup sample. 
My need is for the domain change as defined in my DNS system.

---

### Post by DuckHook on 2012-10-10
totally forgot about */etc/hosts*

Losing it in old age. Editing original post.

---

### Post by bab1 on 2012-10-11
> **griffinmt said:**
> Thanks for the hostname change info.
The domain change in essence has nothing to do with any Windows systems, although the workgroup name used in windows systems would typacally be the same value in a local system. IE: host.sample.com belongs to domain sample.com and works with workgroup sample. 
My need is for the domain change as defined in my DNS system.

Nope, the workgroup is a used to associate shares for easy browsing and could be: sales or engineering or accounting or legal or some such.  It has no security implications and is not really needed on a small network.  You can have as many workgroups as you like.  

On the other hand when it comes to the term **domain** we really need to define that.  An LDAP domain usually follows DNS naming conventions and is for security (e.g authentication, authorization and accounting).  

On the other hand you can have a domain that is only DNS related.  It would only be used to name DNS domains and the hosts in them.  It would be constructed like this: hostname.domain_name.tld (tld = top level domain (.com or .net, etc.))  No security implications at all.  A web site could use DNS domains in this manner.

---

### Post by DuckHook on 2012-10-11
This is not making much sense. Perhaps it is me, so I shall try to explain further.

If you are coming from Windows, the use of the term "Domain" is fraught with ambiguity and new users especially use the word in ways that it isn't intended. Rather than getting bogged down in semantics, let's just look at what you are trying to do:

1. If you want to assign a workgroup name to your machine either to make it recognizable to other windows machines or to allow it to recognize other Windows machines, then you need to change some settings in Samba, and this has nothing to do with domain names.

2. If you just want to connect over a home router to the internet, or if you are connecting your machine directly to your ISP's modem, then you do not need a domain name. Your internet connection will be fine and aren't really a member of any domain.

3. If, however, you have a sophisticated network with an actual physical computer of your own acting as a domain server, then your computer must be configured with a more complex series of steps to be part of this domain. This is a highly unlikely configuration in a home network environment and anyone who was running such an environment would already have the network administration skill to join any client computer to such a domain.

The reason that I am not giving further instructions is that it is likely to do more harm than good. I highly suspect that your situation is #2 above. If so, you don't need to define a domain name.

---

### Post by bab1 on 2012-10-11
> **DuckHook said:**
> This is not making much sense. Perhaps it is me, so I shall try to explain further.

If you are coming from Windows, the use of the term "Domain" is fraught with ambiguity and new users especially use the word in ways that it isn't intended. 
I agree!  That's why it is important to understand how the system really works.  I feel that it's helpful to understand how the various parts work together. > 

Rather than getting bogged down in semantics, let's just look at what you are trying to do:

1. If you want to assign a workgroup name to your machine either to make it recognizable to other windows machines or to allow it to recognize other Windows machines, then you need to change some settings in Samba, and this has nothing to do with domain names.
Assigning the host (a computer) to a specific workgroup neither makes it visable or invisable to others.  The name that you see is in fact the hostname is converted to a NetBIOS name via /etc/hosts or specifically stated in the smb.conf file as```
netbios name = COMPUTER_NAME
```
All Samba (Windows shares) are located by //NETBIOS_NAME/SHARE_NAME, not by workgroup.> 

2. If you just want to connect over a home router to the internet, or if you are connecting your machine directly to your ISP's modem, then you do not need a domain name. Your internet connection will be fine and aren't really a member of any domain.
Correct, The name resolution is only needed in this case if you want to connect to a host (computer) by name.  There is a notion of local DNS as well as external DNS.   You use local DNS so scripts are able to refer to a host by name.  My machines have the same name regardless of when I put them into service.  The router is always** bb-gw1**, the print server is always **bb-hp1** and my personal workstation is always **malibu**. Once again, you are correct using Domain Name Services (DNS) or its primative version (/etc/hosts) is valuable only to some folks. > 

3. If, however, you have a sophisticated network with an actual physical computer of your own acting as a domain server, then your computer must be configured with a more complex series of steps to be part of this domain. This is a highly unlikely configuration in a home network environment and anyone who was running such an environment would already have the network administration skill to join any client computer to such a domain.
The use of a DNS server only centralizes the configuration tasks.  You can achive the same thing with a simple /etc/hosts file on each machine in a simple LAN situation.> 

The reason that I am not giving further instructions is that it is likely to do more harm than good. I highly suspect that your situation is #2 above. If so, you don't need to define a domain name.

I assume that you are speaking to the OP here.

---

### Post by DuckHook on 2012-10-11
Apologies *bab1*. My entire post was a reply to the OP. Must have hit the wrong reply button (too easily done because I display threads in linear mode). Reference to "not making much sense" was with respect to this passage from the OP:

> **griffinmt said:**
> The domain change in essence has nothing to do with any Windows systems, although the workgroup name used in windows systems would typacally be the same value in a local system. IE: host.sample.com belongs to domain sample.com and works with workgroup sample.
My need is for the domain change as defined in my DNS system.

In fact, all of my comments were made in response to above, so please take no offence.

I have found that it is usually counterproductive to get into too much technical detail with new users. You and I may understand the workings of NetBIOS and how to configure smb.conf, but this is just confusing and intimidating to absolute beginners. Thus my attempt to avoid such detail--even avoiding the use of the word "domain"--and just getting him/her to the point where his/her system works.

Following comments directed to griffinmt:

Please don't pay too much attention to the technical discussion. Of course, if you like such stuff, then by all means. The *General Help* and *Networks* forums are especially helpful for exploring/configuring samba. You can also look at this:

[https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)

However, I think that both *bab1* and I agree that you don't need to define a domain name if you are just trying to connect to the Internet through a simple home router. If your system is more complex than this, then perhaps you may wish to post in the *Networks* forum for their expertise.

---

### Post by critin on 2012-10-11
> **griffinmt said:**
> Thanks for the hostname change info.
The domain change in essence has nothing to do with any Windows systems, although the workgroup name used in windows systems would typacally be the same value in a local system. IE: host.sample.com belongs to domain sample.com and works with workgroup sample. 
My need is for the domain change as defined in my DNS system.


[http://www.liberiangeek.net/2012/05/setup-static-dns-servers-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/05/setup-static-dns-servers-in-ubuntu-12-04-precise-pangolin/)

---

### Post by griffinmt on 2012-10-16
I appreciate you taking time to help me, and have since solved my issue.
I just wanted the system to append my local domain (sample.com) to all my requests to local systems so that an up front dns will resolve properly vs other non-local systems.
 
Anyway, I am not a newbie as I have worked with a variety of network based systems for 32 years (you do remember DECNET don't you?). It is just that ubuntu is new for me.

---

