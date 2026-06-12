---
title: "Ubuntu Firewall Project"
date: 2007-04-16
forum: Programming Talk
---

### Post by tomplast on 2007-04-16
Hi everyone.

Due to the lack in certain applications (*cough* Firestarter) and an eagerness to start learning some Python (and Glade) and trying to contribute to the community I have decided to work on a firewall for Ubuntu which will utilize iptables.

I'm very inexperienced and I'm starting from zero (I have a great deal of experience with Linux and some programming but nothing to brag with) so don't except it to be out soon (or ever) but I will try to put some time into it and hopefully there will be som result soon.


Suggestions and ideas are very welcome. Here comes a short explaination of the idea (not worked on that much). Sorry for the grammatic errors.

-----------------------------------------------------------------------------------------------------


[SIZE="4"][FONT="Verdana"]Ubuntu Firewall Project

Mission:
To create a firewall GUI which helps protects the computer
through the use of iptables.

Description:
Iptables may be a little hard for someones to learn and
implementing a simple (but not option-limited) GUI is a good
way to insure security through usabillity (if done correctly).

Focus should be on making new users (and people with no experience 
in firewalls and security) familliar with the settings and
how they do to get the desired effect.

Primary Goals:
* Implement a simple but functional GUI
	* Rules / Policies
		* Support for both TCP & UDP
		* Common Services list (HTTP, HTTPS, FTP etc)

	* Log viewer - An advanced log viewer that enabled the user to
	  search, view, backup & delete logs from the firewall. 

	* Settings
		* Log & Alert - Controls log-related settings and whether
		  the user should be contacted (and how) when something
                  (hacking attempt?) happends.

	* Firewall guide - Helps the user with getting the firewall
	  configured. A possible feature is detection of installed
	  software (like proftpd, apache) and asking the user
	  if he/she wants the service to be allowed/denied.

	* Attention alert - Tells the user when a service tries to open a
 	  connection and get's denied. Can be turned on/off in settings.[/FONT][/SIZE]

---

### Post by Quikee on 2007-04-16
Cool.. nice idea.

Maybe you should request for inclusion in "3rd party projects" subsection so everybody can participate in development. I would be glad to help if I can.

Python is a nice language and easy to learn. With glade and pygtk, GUI programming is almost trivial. =)

---

