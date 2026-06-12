---
title: "Can't set variables in bash script"
date: 2009-02-10
forum: Programming Talk
---

### Post by utnuc on 2009-02-10
I have a beginner's shell scripting question.  When this script is run, instead of allowing me to set the value of variables number_logons and number_logouts, it gives me a "number_logons: command not found" result.  Any thoughts?

BTW - this script attempts to parse my VirtualBox log file to tell me who is connected / disconnected.

Thanks
b

[PHP] 
#!/bin/bash
set `egrep -i 'logon|logoff' ~/.VirtualBox/Machines/Windows_XP/Logs/VBox.log | cut -d: -f5 | cut -d"(" -f1 | egrep -v 'NULL' | sort | uniq | wc -l`
echo "Connections to Windows XP Virtual Box"
echo "**********************************************"  
for (( c=1; c<="$1"; c++ ))
do
	number_logons = $(egrep -i 'logon' ~/.VirtualBox/Machines/Windows_XP/Logs/VBox.log | cut -d: -f5 | cut -d"(" -f1 | egrep -v 'NULL' | sort | uniq  -c | rev | cut -d" " -f4 | rev | sed -n "$c"p) 
	number_logouts = $(egrep -i 'logoff' ~/.VirtualBox/Machines/Windows_XP/Logs/VBox.log | cut -d: -f5 | cut -d"(" -f1 | egrep -v 'NULL' | sort | uniq  -c | rev | cut -d" " -f4 | rev | sed -n "$c"p)
	echo logons: $number_logons

	if [ $(( $number_logons > $number_logouts  )) ]; then

	echo -e `egrep -i 'logon|logoff' ~/.VirtualBox/Machines/Windows_XP/Logs/VBox.log | cut -d: -f5 | cut -d"(" -f1 | egrep -v 'NULL' | sort | uniq | sed -n "$c"p` "\t" `egrep -i 'logon|logoff' ~/.VirtualBox/Machines/Windows_XP/Logs/VBox.log | cut -d: -f5 | egrep -v 'NULL' | sort | uniq  | rev | cut -b 19- | rev| sed -n "$c"p | cut -d"(" -f2` "\t" Disconnected  

	else
	echo -e `egrep -i 'logon|logoff' ~/.VirtualBox/Machines/Windows_XP/Logs/VBox.log | cut -d: -f5 | cut -d"(" -f1 | egrep -v 'NULL' | sort | uniq | sed -n "$c"p` "\t" `egrep -i 'logon|logoff' ~/.VirtualBox/Machines/Windows_XP/Logs/VBox.log | cut -d: -f5 | egrep -v 'NULL' | sort | uniq  | rev | cut -b 19- | rev| sed -n "$c"p | cut -d"(" -f2` "\t" Connected 

	fi

done
echo "**********************************************" 
read [/PHP]

---

### Post by eightmillion on 2009-02-10
The problem is the spaces in your variable declarations. They need to look like this:

```

number_logons=$(egrep -i 'logon' ~/.Vir...
number_logouts=$(egrep -i 'logoff' ~/.Vir...

```

N.B. No whitespace around the equals sign.

---

### Post by geirha on 2009-02-10
> **utnuc said:**
> 
[PHP] 
	if [ $(( $number_logons > $number_logouts  )) ]; then
[/PHP]

Next, you'll probably get a problem with that line. You only need the [-command:
[php]
if [ $number_logons -gt $number_logouts ]; then
[/php]

---

### Post by utnuc on 2009-02-12
Perfect - thanks for the tips.  So annoying that whitespaces make a difference.  Also, I added code to handle the case of a null string (someone has connected, but not yet logged off).  The final, working code looks like this: 

[PHP]#!/bin/bash



num_users=$(egrep -i 'logon|logoff' ~/.VirtualBox/Machines/Windows_XP/Logs/VBox.log | cut -d: -f5 | cut -d"(" -f1 | egrep -v 'NULL' | sort | uniq | wc -l)

echo "Connections to Windows XP Virtual Box"
echo "**********************************************"  

for (( c=1; c<="$num_users"; c++ ))
do
	number_logons=$(egrep -i 'logon' ~/.VirtualBox/Machines/Windows_XP/Logs/VBox.log | cut -d: -f5 | cut -d"(" -f1 | egrep -v 'NULL' | sort | uniq  -c | rev | cut -d" " -f4 | rev | sed -n "$c"p) 
	number_logouts=$(egrep -i 'logoff' ~/.VirtualBox/Machines/Windows_XP/Logs/VBox.log | cut -d: -f5 | cut -d"(" -f1 | egrep -v 'NULL' | sort | uniq  -c | rev | cut -d" " -f4 | rev | sed -n "$c"p)
	computer=$(egrep -i 'logon|logoff' ~/.VirtualBox/Machines/Windows_XP/Logs/VBox.log | cut -d: -f5 | cut -d"(" -f1 | egrep -v 'NULL' | sort | uniq | sed -n "$c"p)
	ip_address=$(egrep -i 'logon|logoff' ~/.VirtualBox/Machines/Windows_XP/Logs/VBox.log | cut -d: -f5 | egrep -v 'NULL' | sort | uniq  | rev | cut -b 19- | rev| sed -n "$c"p | cut -d"(" -f2)


			#test for null string
if [ -z "$number_logons" ] ; then
number_logons="0" 
else
nothing=1
fi	

if [ -z "$number_logouts" ] ; then
number_logouts="0" 
else
nothing=1
fi					



	if  [ $number_logons -gt $number_logouts ]; then

	echo -e $computer "\t" $ip_address "\t" Connected  

	else

	echo -e $computer "\t" $ip_address "\t" Disconnected 

	fi

	#egrep -i 'logon|logoff' ~/.VirtualBox/Machines/Windows_XP/Logs/VBox.log | cut -d: -f5 | egrep -v 'NULL' | sort | uniq
done
echo "**********************************************" 
read[/PHP]

---

