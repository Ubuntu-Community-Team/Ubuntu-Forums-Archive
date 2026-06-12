---
title: "New Internet provider, wireless printer will not print."
date: 2013-04-05
forum: New to Ubuntu
---

### Post by gordon33 on 2013-04-05
Hello All

New Internet provider, and now the  wireless printer will not print.  Started the trouble shoot process and got a box labelled: "Check Server Firewall".  The rest of the box said: 

"It is not possible to connect to the server.   

Please Check to see if a firewall or router configuration is blocking TCP port 631 on server 192.168.1.5."


Where should I look?  Will I have to go through the same process I went through when I first installed the printer?

I am running Ubuntu 10.4.  Its a HP Deskjet 6980


Gordon33

---

### Post by DuckHook on 2013-04-05
Hi gordon33,

Please appreciate that we have no idea what process you went through when you first installed the printer. Perhaps you could give us details so that we can comment.

There's a common set of procedures that one can always follow trying to pin down nasty network issues:

1. Try pinging your router.
2. Open your router and see what IP it has assigned your printer.
3. Print out a settings sheet on your printer and see if the IPs match.
4. Try pinging your printer.
5. Do you have a firewall configured on your own box?
6. Is the printer getting its IP address through DHCP or BootP?
7. Is the router assigning the printer its address dynamically or did you set it up with a static IP?
8. Do you have HPLIP installed?
9. If so, which version?

This should give enough to go on for now.

Jumping the gun a little, but you may also wish to start giving some thought to upgrading to 12.04. The upgrade process alone could solve a number of issues, and 10.04 only has about a month of life left before its die-date. If you intend on upgrading, then do a fresh install (not network upgrade) and the new drivers/configuration/apps could make wrestling with your balky configuration academic. If contemplating this option, MAKE SURE you run the whole thing as a LiveCD first. Otherwise, if you box is not sufficiently powerful, or if the new 12.04 drivers don't work, you could be left in worse shape than you are now.

---

### Post by gordon33 on 2013-04-05
Hello All and especially DuckHook

Thank you DuckHook  for all the suggestions.  I would have needed specific instruction for each of the suggestions.  I was going to try and reload or re-install the printer.  I got out the instructions book and found notes I had left the last time I had a similar problem.  Those notes follow.



I am not sure what went south but I did the following and it worked.  I called it "reload printer from list."
_System / Administration / Printing t_hen when the box comes up click on: _Server / New / Printer_  Then click on _Network Printer _ then I waited for my printer to show up on the list.  I clicked on my _[U]HP 6980 with all the associated numbers[ /U] _ After that I deleted the failed printer from the box mentioned above. Finally, I made the new printer my default printer.

All's well that ends well.

Gordon33

---

### Post by DuckHook on 2013-04-05
> **gordon33 said:**
> ...All's well that ends well.

I'd like to take some credit, but you solved this one all by your lonesome. ;)

Keep on Ubuntuing!

---

