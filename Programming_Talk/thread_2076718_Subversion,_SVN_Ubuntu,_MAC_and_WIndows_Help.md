---
title: "Subversion, SVN Ubuntu, MAC and WIndows Help"
date: 2012-10-26
forum: Programming Talk
---

### Post by sunnychotai on 2012-10-26
Hi,

I'll try and keep this simple.

I am trying to:

1. Setup a Subversion SVN repository on my NAS drive
2. Use my Ubuntu box, MAC OS X and Windows machines as local DEV environments and synch up with this NAS drive

Is this possible?

Can I use different Subversion \ SVN clients against the same repository?  I am trying to just create a respository and not a Subversion\SVN server.

Make sense?

---

### Post by Bachstelze on 2012-10-26
Both Ubuntu and OS X use the standard command-line SVN client. I don't know what you can use in Windows, but I would be surprised if you couldn't use it on the same repository.

---

### Post by dwhitney67 on 2012-10-26
> **Bachstelze said:**
> Both Ubuntu and OS X use the standard command-line SVN client. I don't know what you can use in Windows, but I would be surprised if you couldn't use it on the same repository.
On Windoze, one will be able to.  There's Tortoise (sp?) and also Netbeans (which I use) that are able to interface with SVN.

---

### Post by steeldriver on 2012-10-27
+1 for the TortoiseSVN client - I've used it on both XP and Win7, with ssh+svn to a repository on a Fedora box. It also worked fine to a svn server on my Netgear NAS (Debian) which I set up just to try out.

---

### Post by spjackson on 2012-10-27
> **sunnychotai said:**
> 
Can I use different Subversion \ SVN clients against the same repository?  I am trying to just create a respository and not a Subversion\SVN server.

I have only used SVN a little, but I understood it to be inherently client-server. I didn't think you could also use it without a server. Am I wrong?

Edit: My mistake: I am wrong. I wan't aware of file:/// type access.

---

### Post by steeldriver on 2012-10-27
that is my understanding as well - I guess you *might* be able to run the server elsewhere and tell svnadmin to create the repo on a remote mounted location - I don't know

---

### Post by dazman19 on 2012-10-29
i would run svn-server on the ubuntu machine. i do this at home and use rapid svn for linux and tortoise svn client for windows.

i doubt your repository would be so huge that you would require a NAS. if it is i wouldnt trust samba/cifs with large amounts of data, i would just use a bigger hdd in the ubuntu box or if its a usb nas have it perminantly plugged into that but i still highly doubt you will need that much space.

a project i work on has 4800 revisions and takes up about 2-3gb max.

you can write your backups to a nas. not a silly idea.

---

