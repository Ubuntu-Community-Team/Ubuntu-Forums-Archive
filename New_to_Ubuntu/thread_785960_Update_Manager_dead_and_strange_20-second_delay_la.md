---
title: "Update Manager dead and strange 20-second delay launching apps"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by John Costella on 2008-05-07
Hi folks,

This morning, when my laptop was offline (on the train), launching various simple applications were taking a long time to launch. When I'm online again, they launch immediately. The CPUs and disk are doing absolutely nothing during the delay; top doesn't show anything strange. Here are some examples of the delay:

Terminal: 20 seconds exactly
Gedit: 20 seconds exactly
vim from within terminal: 20 seconds exactly
gvim from within terminal: 40 seconds exactly

The only thing that changed last night was that I ran Update Manager and it installed a chunk of Gnome and other updates.

I thought it may be a bug (waiting for some network thing) that may get fixed again with another update, but now I discover that Update Manager is dead. (When I press Check, it goes grey with the spinning disc and never comes back; been waiting a long time now.) (I'm doing it now, online, of course, not offline!)

I used to be on Gutsy and updated to Hardy a few days after it was released. Everything [else] has been excellently smooth (even the laptop microphone now works!).

Thanks in advance :)
John

john@john:~$ uname -a
Linux john 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux

Gnome desktop 2.22.1 build 07/05/08

---

### Post by Delever on 2008-05-07
Main server, selected in software sources, works for me. I don't know the reason for delays when launching applications though.

---

### Post by John Costella on 2008-05-07
Unfortunately, Software Sources seems to be dead. :(

When I select it from System/Administration I get a "Starting Administrative Application" minimised button on the lower system bar for about 13 seconds, which then disappears. No window appears.

:confused:
Thanks
John

---

### Post by Delever on 2008-05-07
Does sudo work? Try running

sudo gedit

in terminal and check if it starts.

---

### Post by John Costella on 2008-05-07
Hmm ... it threw up a strange (new) message: 

john@john:~$ sudo gedit
sudo: unable to resolve host john
[sudo] password for john: 

It *did* launch gedit after I entered the password. It also throws up the same message when I try it again (within the sudo timeout period):

john@john:~$ sudo gedit
sudo: unable to resolve host john
[sudo] password for john: 
john@john:~$ 
john@john:~$ sudo gedit
sudo: unable to resolve host john
john@john:~$ 

(and does launch gedit).

What is it trying to look up? ('john' is the local machine, as well as the username ... ambiguous, I know, but it worked ok until now.)

Thanks
John

---

### Post by VK7HSE on 2008-05-07
Hi to all...

It sounds like at some point you have changed your host name?

I managed this error a few weeks back as I had my local host called Ubuntu-710 then I upgraded to Ubuntu 8.04 b5 and I changed the host name to reflect the new version and the local host no longer resolved it's self!

I have no explanation for the application delays... Sorry :(

Scott

---

### Post by sickenmcsluggets on 2008-05-07
Yes, I had this problem as well, my /etc/hosts file had my username followed by a .domain, so like "username.domain". All I did was edit that file and delete the .domain from my username, and my update manager and all that began working again. Check out this thread...
[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by John Costella on 2008-05-08
AH! Yes, that has fixed the sudo / update manager problem! 

Many thanks, VK7HSE and sickenmcsluggets! :):)

I will check if it fixes the offline delay too -- makes sense, if it was looking elsewhere for something, and there is no elsewhere to check ...

Cheers
John

---

### Post by VK7HSE on 2008-05-09
How did you go ???

---

### Post by John Costella on 2008-05-09
Yes! That was it exactly. Many thanks.

(I don't know how to change the header of this thread to "solved"; have tried before but failed ...)

John

---

### Post by hyper_ch on 2008-05-09
what did now cause the application startup delay?

Btw, interesting homepage ;)

---

### Post by John Costella on 2008-05-09
>what did now cause the application startup delay?

Well, when I fixed the /etc/hosts file, the offline delay went away too.

I imagine that every time I launch terminal, vim, etc, it must look up something on the host 'john' (my machine). With the 127.0.1.1 entry in hosts changed to john.<domain>, it must have thought it needed to do a dns lookup somewhere else, because it could no longer find plain 'john' in /etc/hosts. Online it fails to find 'john' in the network dns server (hence the complaint); offline it times out after 20 seconds, I presume looking for a dns server. (gvim must look up two different things)

That's my best guess; I don't really know too much about networking. In any case, it's fixed. 

I've figured out that the /etc/hosts change was my stupid fault, when looking in System / Administration / Network / General / Host Settings. Being formerly addicted to Windows, I had a momentary regression to brain meltdown mode and put the Windows "domain" of my home network in there. I didn't realise that putting in a domain would wreck the machine (on Windoze, it never hurts, and sometimes helps). 

The ironic thing is that Ubuntu connects to my home Windows network more reliably than the machine did when it was actually running Windows! (Hence my obsession with always trying to "help" the machine recognise the Windows network ...)


>Btw, interesting homepage 

Thanks mate. :)

---

### Post by philinux on 2008-05-09
> **John Costella said:**
> Yes! That was it exactly. Many thanks.

(I don't know how to change the header of this thread to "solved"; have tried before but failed ...)

John

Another new feature.

If you edit your first post, go advanced you can pop solved at the beginning of the title. I hope they get this feature back.

---

### Post by John Costella on 2008-05-09
OK, I did that, and it changed the title of the first post, but not the title of the thread as shown in the forum itself.

Maybe I can't do that ...

Thanks 
John

---

