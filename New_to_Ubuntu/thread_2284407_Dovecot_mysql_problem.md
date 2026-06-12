---
title: "Dovecot mysql problem"
date: 2015-06-29
forum: New to Ubuntu
---

### Post by Hamza_BEN_HAJ on 2015-06-29
[COLOR=#000000][FONT=Verdana]Hello, [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]This is my first time participation in this great forum.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I'm working on a new project : installing a mail server (ubuntu / postfix / postfixadmin / dovecot)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]the problem is when i run the commamd : apt-get install dovecot-mysql, i get the message below :[/FONT][/COLOR]

[B][COLOR=Red]The following packages have unmet dependencies:
dovecot-mysql : Depends: dovecot-core (= 1:2.2.9-1ubuntu2) but 1:2.2.9-1ubuntu2.1 is to be installed
E: Unable to correct problems, you have held broken packages.
[/COLOR]

Do you have any idea ? Thank you.[/B]

---

### Post by ajgreeny on 2015-06-29
Have you run ```
sudo apt-get update
sudo apt-get upgrade
``` before trying to install those packages?

---

