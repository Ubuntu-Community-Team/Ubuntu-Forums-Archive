---
title: "bash script"
date: 2012-08-06
forum: Programming Talk
---

### Post by plecebo.mc on 2012-08-06
Hi guys I have been writing an autologin script for some friends at college so we can logon i finished the main program but now im working on adding some neat features to it. One of which is a preliminary check of the computers network connection and reliability.

Idea: The idea is to add a new section of code to my main script
the script will:
1) check to see that the network ssid matches one of the ones provided by the W# variables and also if 6 or more of 10 packs sent with ping are returned.
2) in the event that the first step fails the script will run a loop until the first step is true
3) when its done it will continue on with the rest of the script (not provided as this is a test script of these functions)

system: this code is written in bash and is used on osx (note: networkset and airport commands) even so it should not be an issue for you guys to check the script.

Problem: after countless trial and error and google and man pages i got every thing so far to work (as far as i know its correct) but the problem is the script seems to want to skip the whole entire ChangeNetwork function. Maybe im using the wrong syntax in my conditional's or maybe its something else either way i tried alot and now im having to resort to some outside help.

___
This is the script:

[http://pastebin.com/FCuQ6u6K](http://pastebin.com/FCuQ6u6K)

____
This is my output:

bash -x test.sh
++ ping -c10 [www.google.com](www.google.com)
++ grep received
++ awk -F, '{ print $2}'
++ awk '{ print $1}'
+ ping=10
++ airport -I
++ grep -w SSID:
++ awk -F, '{ print $1}'
++ awk '{ print $2}'
+ ssid=Motorola
+ declare -ir FALSE=1
+ declare -ir TRUE=0
+ W1=AUStudentOpen
+ W2=AURESNET
+ W3=AUGuest
+ echo 'Initiating preliminary checks NOW!'
Initiating preliminary checks NOW!
+ '[' CheckOnline == 1 ']'


((ends after that))

Thanks everyone I'm looking forward to some helpful insight.

---

### Post by anden.d on 2012-08-06
Could you post the actual code? might help shed some ligth on what's wrong
sorry didn't see the link

---

### Post by DarkAmbient on 2012-08-06
I don't have much experience with bash, I might point out.. but let's try...

On line 49, if you add an echo before "Script is changing networks NOW!" will that line be printed? It's inside the first until loop. 

Edit: didn't see your stop here comment.. 

And the `networksetup -setairportnetwork en1 $W1` lines, are you sure they works as they should, if at all?

---

### Post by plecebo.mc on 2012-08-06
writing the following test script:

------------
#!/bin/sh

W1="Motorola"
`networksetup -setairportnetwork en1 $W1`

-------------

I get the following results:

(when $W1 is set for AUStudentOpen *not present*)

SteelBeauty:~ matt$ bash -x test2.sh
+ W1=AUStudentOpen
++ networksetup -setairportnetwork en1 AUStudentOpen
+ Could not find network AUStudentOpen.
test2.sh: line 4: Could: command not found


(when $W1 is set the Motorola *which is avalible*)
SteelBeauty:~ matt$ bash -x test2.sh
+ W1=Motorola
++ networksetup -setairportnetwork en1 Motorola
SteelBeauty:~ matt$ 

____________

so it that code works correctly but maybe it exits because it cant connect using the command.

SideNote: i used have a function that scanned the wifi networks and would connect when the wifi ssid is present but i couldnt get grep and awk to grab the ssid by its self EX:

code: (example not original as i lost that revising)
------------------
scan=`airport -s`

function NetworkChange
{
      blah blah
      if [ $scan | grep '$W1' == '$W1'];then  ### note1
         `networksetup -setairportnetwork en1 $W1`
         return ${TRUE}
      elif blah blah

      else 
          return ${FALSE}
}
---------------------
note1: the command is a rough example i needed to learn how to make it grab only the ssid which after countless trys i could not do.

_________

as for line 49 the result dose not return further proving its skiping the whole until operation

---

### Post by spjackson on 2012-08-06
You say that this is bash, although I note that it has #!/bin/sh on line 1. 

The syntax of your while line does not cause the function to be executed. At a bash prompt if you type
```

while [ fubar == 1 ]; do echo looping; done

```
it does not complain that fubar is not found. [I think it is simply testing whether the word fubar (or CheckOnline) is lexically equivalent to the word 1.]

There may be a snazzier way to do it, but being old school, I would write your main loop like this.
```

CheckOnline
ONLINE_STATUS=$?

while [ ${ONLINE_STATUS} -eq ${FALSE} ]; do
    ChangeNetwork
    CheckOnline
    ONLINE_STATUS=$?
done

```
and similarly for your until loop within the ChangeNetwork function.

---

### Post by plecebo.mc on 2012-08-06
Thanks guys i figured it out now thanks for that piece of code spjackson you helped me find a few bugs too everything works now

---

