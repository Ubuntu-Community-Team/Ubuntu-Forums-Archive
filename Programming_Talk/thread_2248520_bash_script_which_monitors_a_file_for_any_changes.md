---
title: "bash script which monitors a file for any changes"
date: 2014-10-15
forum: Programming Talk
---

### Post by mitnix on 2014-10-15
[COLOR=#333333]I have a bash script which monitors a file for any changes. When the checksum of the file changes, it calls another bash script and prompts the user for reason_of_change , then takes a backup of the file with the reason entered, date stamp and loginID and then returns to monitoring the file again and the cycle continues.[/COLOR]

[COLOR=#333333]This is how the execution looks when run in the foreground:[/COLOR]

[I][COLOR=#333333][vmtest02 lab]# ./[/COLOR][COLOR=#333333]watchsession.sh[/COLOR][COLOR=#333333] test_file[/COLOR]
[COLOR=#333333]change detected,Changes not written yet[/COLOR]
[COLOR=#333333]Backing up...[/COLOR]

[COLOR=#333333]Enter the ticket number or reason: testing[/COLOR]
[COLOR=#333333]Backed up[/COLOR]
[COLOR=#333333]Changes written now[/COLOR]

[COLOR=#333333]--> resumed watching...[/COLOR][/I]

[COLOR=#333333]I want to be able to run this in the background and ONLY when the file is modified, come to the foreground and prompt the user for reason_for_change and take the backup and again go back to the background and continue monitoring.[/COLOR]

[COLOR=#333333]Here is how it looks when run from the background and notices file changes[/COLOR]

[I][COLOR=#333333][vmtest02 lab]# ./[/COLOR][COLOR=#333333]watchsession.sh[/COLOR][COLOR=#333333] test_file &[/COLOR]
[COLOR=#333333][1] 5253[/COLOR]
[COLOR=#333333][vmtest02 lab]# change detected,Changes not written yet[/COLOR]
[COLOR=#333333]Backing up...[/COLOR]

[COLOR=#333333]Enter the ticket number or reason: testing[/COLOR]

[COLOR=#333333]-bash: testing: command not found[/COLOR]

[COLOR=#333333][1]+ Stopped ./[/COLOR][COLOR=#333333]watchsession.sh[/COLOR][COLOR=#333333] test_file[/COLOR][/I]

[COLOR=#333333]Now on bringing this to fg it starts from where it left off and continues in the foreground.[/COLOR]

[I][COLOR=#333333][vmtest02 lab]# %%[/COLOR]
[COLOR=#333333]./[/COLOR][COLOR=#333333]watchsession.sh[/COLOR][COLOR=#333333] test_file[/COLOR]
[COLOR=#333333]testing[/COLOR]
[COLOR=#333333]Backed up[/COLOR]
[COLOR=#333333]Changes written now[/COLOR]

[COLOR=#333333]--> resumed watching.[/COLOR]
[/I]

[COLOR=#333333]The reason passed is hitting the terminal and is not getting read into the variable within the script. I guess this has to do with job control, using fg with the script doesnt work. I tried using set -m (as told in one of the posts) but it knocks me off the server when i try to enter the reason.[/COLOR]

[I][COLOR=#333333][vmtest02 lab]# ./[/COLOR][COLOR=#333333]watchsession.sh[/COLOR][COLOR=#333333] test_file &[/COLOR]
[COLOR=#333333][1] 10543[/COLOR]
[COLOR=#333333][vmtest02 lab]# change detected,./[/COLOR][COLOR=#333333]watchsession.sh:line[/COLOR][COLOR=#333333] 31: fg: %1: no such job[/COLOR]
[COLOR=#333333]Changes not written yet[/COLOR]
[COLOR=#333333]Backing up...[/COLOR]

[COLOR=#333333]Enter the ticket number or reason: testing[/COLOR]
[COLOR=#333333]testinglogout[/COLOR][/I]


[COLOR=#333333]Please let me know if anyone has any fix to this issue.[/COLOR]

---

### Post by Lars Noodén on 2014-10-15
You could use incron and then set up an incrontab to monitor the file and launch a script if the file is modified.

---

### Post by mitnix on 2014-10-15
After installing incron , i tried looks like it work only on directories and doesnt execute teh script.

Here is what i put in the incrontab
/nfs/home/kummit01/lab/test_file IN_MODIFY /nfs/home/kummit01/lab/bkup.sh

Please guide me

---

### Post by syadnom on 2014-11-18
I have a similar issue.

IN_MODIFY doesn't work stand alone, but if you do IN_MODIFY,IN_CLOSE_WRITE,IN_CLOSE_NOWRITE then it triggers 3 times.  I don't get it.

---

