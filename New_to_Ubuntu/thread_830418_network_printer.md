---
title: "network printer"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by windows hater on 2008-06-15
i recently came into a printer and i have 5 computers and i want all of these to be able to connect to the printer and right now the only thing i have is a linksys router and i need help because i never setup a network printer before all the machines have ubuntu and the other is a vista 

thanks ahead

---

### Post by cmnorton on 2008-06-16
It seems like there are two pieces to this, connecting the printer to one of the computers, and then making connections from the other computers to the computer with the printer attached. I am making the assumption this printer is not a network printer. 

You will have to decide to which computer you wish to connect the printer, or whether or not you want it to be a network printer using a print server.  If I were doing this, I would purchase a cheap print server and let the printer stand alone, and then the Ubuntu systems could connect using AppJet direct, and the Windows systems could connect to the printer as a network printer.

To set the printer up in Ubuntu, Go to System -> Administration -> Printing, and set the printer up. Make sure you can print to it.

It would be helpful, but I am not sure it is required that all these computers, at least the computer to which the printer is connected and the Windows system be in the same Domain/Workgroup, unless you go the print server route.

I have not covered how the Ubuntu computers connect via SAMBA, but the connection string would be something like this:

DeviceURI smb://domain-name\username:password@domain-name/system-name/share-name

This is the connect string from my Kubuntu workstation to a Windows desktop to which a printer is connected.

You might do better taking this in pieces, and deciding first how you want to connect and configure this printer.

---

