---
title: "[SOLVED] Printer Sharing: I effed something up"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by ZOOstation on 2008-06-07
I'm running Ubuntu Hardy 8.04 and I was trying to set up my laptop to share a printer hooked up to a Windows XP machine. The whole house is networked wirelessly, but all the machines except mine are XP. The other ones can print from the shared printer without error.

When trying to set mine up, I messed something up majorly. Right now, I'd appreciate help getting back to square one. My Printer Configuration cannot connect. It gives me the error:
```
CUPS server error

There was an error during the CUPS operation: 'httpConnectionEncrypt failed'.
```

If nothing else, could you help me reset all the printer settings so I can start over?

---

### Post by avtolle on 2008-06-07
Not an expert here, but I'd suggest deleting the printer under Ubuntu. I'd then restart my system, and go through the Add Printer routine again, and see if this will work.

---

### Post by ZOOstation on 2008-06-07
Right. How? It appears as though I have no printers set up, and gives me no options under Printer Configuration except to (attempt to) connect to the print server.

---

### Post by avtolle on 2008-06-07
> **ZOOstation said:**
> Right. How? It appears as though I have no printers set up, and gives me no options under Printer Configuration except to (attempt to) connect to the print server.
I presume it is showing up as a Remote Printer under System>>Admistration>>Printing. If true, remove it (delete it, whatever it is called), so that no printer shows, remote or local (other than PDF). Then, I'd shut down the computer, Then, with the printer powered on at the XP machine, and enabled to share (I don't recall how this is done in XP), I'd click on Add a Printer, then after the search thing, select Windows Printer under Samba, and see if it is added correctly. HTH.

---

### Post by ZOOstation on 2008-06-07
You presumed wrong. What I was trying to say was there were no printers listed at all, and there wasn't even a "local printers" heading to be listed under. I had no access to anything but "Goto Server" which gave me the CUPS error I reported in my first post.

But the help menu was working, and told me to enable cupsys in System->Administrator->Services. It was already enabled, but I unchecked and checked it again and now it's working fine. Problem solved.

---

### Post by avtolle on 2008-06-07
> **ZOOstation said:**
> You presumed wrong. What I was trying to say was there were no printers listed at all, and there wasn't even a "local printers" heading to be listed under. I had no access to anything but "Goto Server" which gave me the CUPS error I reported in my first post.

But the help menu was working, and told me to enable cupsys in System->Administrator->Services. It was already enabled, but I unchecked and checked it again and now it's working fine. Problem solved.
Good to know the problem is solved.

---

### Post by dead_poet79 on 2010-06-12
I had the same problem and found this was the way to resolve the issue in prior versions of Ubuntu, but since they have changed things to upstart services, the Services app has been removed. To turn the cups service off now, open terminal and use:
sudo service cups stop

Once it stops, turn it back on by using:
sudo service cups start

This will do the same thing.

---

### Post by brawd on 2010-06-21
Thanks a lot for that. Every start of the computer meant that I lost all my printers. The only solution I knew of was to re-install cups from the repositories, a task that soon became tedious. Before that, on forum advice, I modified some file that I have long since forgotten. A mod that did no good at all.

This is a much better solution.

However the problem has only occured in the last few weeks. I originally did a clean install of 10.04 and had no problems with the printers. It seems when I accepted the updates the printing problems started.

 I really do hope a solution is found.

regards,

brawd

---

