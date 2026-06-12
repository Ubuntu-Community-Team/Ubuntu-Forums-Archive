---
title: "Samba PDC help"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by russd772 on 2013-04-15
hey all, 

  im having some trouble connecting my windows XP client to ubuntu 12.10 server running samba for PDC.  I think the issue lies somewhere between my ears and i just need some help locating it.  

in mock environments this setup worked fine, i connected to the PDC and logged on the client no problem.  now that i have a registered domain it doesnt seem to want to coperate with me at all.  I assume this is because my network is not able to communicate with my IP address that the domain is associated with?  the error that i get is "A domain controller for the domain "example.com" could not be contacted.  is this a DNS issue, do i need to set up bind to do DNS before i can start this project?  what about DHCP, do i need myself one of those also?  sorry if these are all noob questions. im a beginner here and trying to do this for some experience and to learn a little in the process.  any help would be great maybe just point me to the appropriate steps or a web guide, i have no issues with doing the reading i just cant find anything specific with the router issue.

basically what im trying to accomplish is setting up a domain at home with a PDC, web and e-mail server, and a windows client.  all of the machines are behind a router so i assume this is part of the issue as well.  I assume i am doing something completely wrong,  i need to make my domain point to my home IP then to the IP behind the firewall of the webserver.  on top of that i need to register all of these machines as part of the same domain.

---

