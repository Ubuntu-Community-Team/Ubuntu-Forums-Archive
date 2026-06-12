---
title: "BASH - Nested IF statement not working correctly"
date: 2009-07-28
forum: Programming Talk
---

### Post by derelict888 on 2009-07-28
Here is part of a script that I'm stuck on;

```
while true; do

	echo -e "Which zone do you manually want to bring up? (type \"quit\" to exit)"
	read manual_up
	if (( $manual_up == "exit" || "quit" || "q" )) ; then break
	else
		echo "You have selected ${zones_array[$manual_up]}, is this correct? [y/n]"
		read confirm
		if (( $confirm == "y" || "yes" )) ; then
			echo -e "Moving ${zones_array[$manual_up]} to the manual folder"
			cp $mailing_zones/"${zones_array[$manual_up]}" $manual_zones/

		elif (( $confirm == "n" || "no" )) ; then
			echo -e "You did not confirm manual change.\n"

		else break
		fi
	fi
done
```
So at the "read confirm" part is where the script starts to work funny. Here is the results of running a test of the script;
```
[root@server ~]# /tools/DNS_manual.sh 
-----Tue 28 Jul 2009 01:58:09 PM MDT-----
Here are all the zones we current provide DNS for;

0: range1.in-addr.arpa
1: range2.in-addr.arpa
2: range3.in-addr.arpa

and here are the zone files already set up/down manually;

0: range4.in-addr.arpa
1: range5.in-addr.arpa
2: test.arpa

Which zone do you manually want to bring up? (type "quit" to exit)
1
You have selected range2.in-addr.arpa, is this correct? [y/n]
n
Moving range.in-addr.arpa to the manual folder

Which zone do you manually want to bring up? (type "quit" to exit)
q
[root@server ~]# 

```
Right where I input "n" or "no" the script does what "y" or "yes" input should do (which is first inline). I've tried re-writing some of that code to see if my syntax was bad but I've only got limited scripting knowledge. It could be my OR statements but idk. Any ideas? The variables I'm using check out (when I echo them for debug they output what I expect) :confused:

---

### Post by derelict888 on 2009-07-28
so my problem is whether the first input is an integer or a string, any ideas how to fix this easily? In the meantime I made two new variables $yes=y $no=n and then I do my if statements a bit different, but that feels kind of ghetto.

---

### Post by Eeqmcsq on 2009-07-28
At first glance, it looks like your || statements are written incorrectly. You need something like:

$confirm == "y" || $confirm == "yes" 

That goes for all of your || statements.

---

### Post by Eeqmcsq on 2009-07-28
Argh, goes to show how inexperienced I am with the nuances of bash syntax. This time, I tried out your code, and I THINK something like this is what you intended:

if [ $confirm == "y" ] || [ $confirm == "yes" ]

---

### Post by derelict888 on 2009-07-28
Thanks for responding. Whats weird is this line works;
```
if (( "$manual_up" == "exit" || "quit" || "q" )) ; then break
```
I have tried all those strings all they all send me out.

I could through in a simple echo line to see if the rest of that then statement would finish or if the program is simply breaking and exiting and looks like its exiting correctly.

---

### Post by derelict888 on 2009-07-28
> **derelict888 said:**
> 
I could through in a simple echo line to see if the rest of that then statement would finish or if the program is simply breaking and exiting and looks like its exiting correctly.

Hmm I tested this theory by typing a random string and the program still exited so my code isn't working, it just happens to have the desired result. :(

---

### Post by Eeqmcsq on 2009-07-28
I think you should change your syntax for all your || statements. I'm not sure what the (( )) syntax does, but I never use that in my || statements.

---

### Post by malagasmith on 2009-08-02
c

---

