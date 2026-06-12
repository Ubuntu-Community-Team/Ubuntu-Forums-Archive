---
title: "Troubleshooting Lua SMTP date???"
date: 2009-08-19
forum: Programming Talk
---

### Post by FuRoSh on 2009-08-19
Sorry I had posted this under General Help and thought will maybe get a bit more help here. Original Post: [[COLOR=#282828]http://ubuntuforums.org/showthread.php?t=1243829&referrerid=896081[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1243829&referrerid=896081")
 
--------------------------------------------------
 
I've searched and searched with no luck so here I go...
 
I'm a sysadmin and trying to troubleshoot an emailing problem on a ubuntu box. A programmer has been writing Lua scripts and they all seem to work for the most part but I'm trying to troubleshoot an error of emails with Lua being sent with Date: 6/6/6 (all the time) even today on 8-18-09.
 
I have installed and configured exim4 and I have been able to send mail correctly from command line and using:
 
echo "Email Test" | exim4 [EMAIL="email@somedomain.com"][COLOR=#444444]email@somedomain.com[/COLOR][/EMAIL]
 
mail -S "Subject: La La La" [EMAIL="somone@domain.com"][COLOR=#444444]somone@domain.com[/COLOR][/EMAIL]
 
exim4 -d -bt [EMAIL="somone@domain.com"][COLOR=#444444]somone@domain.com[/COLOR][/EMAIL]
 
[FONT=Arial]All these work fine with correct date (8-18-09) being used. I can also debug with the last -d exim 4 command and all looks good![/FONT]
 
[FONT=Arial]However, anytime I use the Lua script it keeps doing the same thing. Now programmer claims all his stuff is good! :smile: Blame game is fun, but I just need to know how to troubleshoot this. The Lua scripts don't seem to use any of the syslogs that get written to for exim4, apache, or anything else. Is the Lua SMTP parameters configurable? Can you check any sort of log file, configuration file, etc to check where the issue may lie?[/FONT]
 
[FONT=Arial]Does anyone know how to troubleshoot this or what with Lua I can check/verify and fix this issue? [/FONT]
[FONT=Arial]I've checked the system's date, it's been updating with NTP, all other system mail related check seem fine.[/FONT]
[FONT=Arial]Please point me in the right direction....[/FONT]

---

### Post by FuRoSh on 2009-08-19
In addition I also would like to state that this ubuntu box is relaying to an MS Exchange 2003 server. The ubuntu IP address has been added to the "allowed" relay IPs. I thought this might be part of the problem, however anytime I use standard mail, exim4 commands from command line the emails are sent out the the public internet without the 6/6/6 date.
 
It only seems to be an issue when using the Lua script with the SMTP stuff. I can't find any logging, configuration, or other data I can use to determine where the issue lies. 
 
Any good Lua experts ever deal with something like this???
 
Anyway to debug the Lua while the scripts are sending emails???

---

