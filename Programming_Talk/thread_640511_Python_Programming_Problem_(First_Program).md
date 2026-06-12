---
title: "Python Programming Problem (First Program)"
date: 2007-12-14
forum: Programming Talk
---

### Post by jseiser on 2007-12-14
I would like to write a program for  work to speed up a process i must do alot.  i think i could write the code in VB (had to learn it for school) but i want to try python.  This will be for a set of windows computers. 

IP = "111.111.111.111"
PW = "password"
number = raw_input(&#8220;What is the PVC?&#8221;) 
# Somehow connect to command promt and run
#telnet IP
#when telnet asks for password execute
# PW
#once connected run

sh int atm6/0.number
sh arp | in number

#display results of both commands on screen.
#exit telnet session

Any ideas on how to go about this in python. I think i need to load some telnet library?  This is all over my head, but i have to input this command over and over so i might as well automate the process.

---

### Post by dwblas on 2007-12-14
You want to use subprocess to execute telnet and retrieve any output/send input.  Take a looks at Doug Hellmann's module of the week examples.
 [http://blog.doughellmann.com/2007/07/pymotw-subprocess.html](http://blog.doughellmann.com/2007/07/pymotw-subprocess.html)

---

### Post by jseiser on 2007-12-14
Ok thanks, will look into this.
edit: thats all way over my head, i thought this was supposed to be an easy language to pick up.  Wow.  I guess i will have to write it in VB and that sucks :(

---

### Post by ghostdog74 on 2007-12-14
Python comes with telnet library you can use
check[ this]("http://docs.python.org/lib/module-telnetlib.html")

---

### Post by jseiser on 2007-12-14
ok ill try this, i had to do this by hand 3 times since ive posted lol, i need it programmed :)

---

### Post by dataw0lf on 2007-12-14
You could also use pexpect, the excellent Python API for Expect.  It's the preferred way of performing these sort of operations.

---

### Post by jseiser on 2007-12-14
pyexpect, is this a script or a library? Sorry im so dense, im trying to learn python by forcing myself into writing code.  This seems like the perfect project as well. lol, slow day :)

---

### Post by jseiser on 2007-12-14
alright, well google tells me its a module.  heh, but i also see where it is a download for linux, and that when its ran through windows it uses cygwin, i need something that will work on windows mainly, and i will more then likely then worry about it working from my home linux computer.

Im going to try and comment on the code, it would be great if someone could tell me if im reading it right or  not.

this is how i normally go about doing this manually.

open up cmd
telnet 111.111.111.111
then i get this prompt
#
#
# Enter Password
#

User Access Verification

password:_
i enter password and hit enter. which lets me into the router
router> enter command 1, then command 2, and look at their outputs.
_____________________________________________________________-

import getpass <--is this a module, if so do i need to set up the password in it?
import sys
import telnetlib

HOST = "111.111.111.111"
# user = username<--i shouldnt need this, since im only prompted for a password. correct?
vpc = raw_input("Enter The VPC Number: ") <--this is the only thing that changes, the customers pvc number, so its a variable i want to be prompted for before the program connects.
password = getpass.getpass() <--this is pulled from getpass(set this up?) and i need it ran when it says password:

tn = telnetlib.Telnet(HOST) <--connects to the variable in HOST, which is an IP

#tn.read_until("login: ") <--looking for a login in the line? which i wont ever see, so i dont need this correct?
#tn.write(user + "\n") <--would insert the string in variable 'user' which i dont need.
if password:                                   <--This is an if statement from the previous tn.read, which i commented out, so i would remove this and leave the line below to read untill a password: is found.
    tn.read_until("Password: ")    <--reading lines untill it sees string password.
    tn.write(password + "\n")        <--reads the getpass.getpass() for the password that was set up in it? and inserts it so i can log in. 

#tn.write("ls\n")   <--would execute a 'ls' so i would switch it to "sh int atm6/0.vpc   where vpc is the string i was prompted for. then it would execute that.
tn.write("sh int atm6/0.vpc\n") <--is that right, with the new line command entered after with no space?
tn.write("sh arp | in vpc\n") <- this would also run the second command after the first
tn.write("exit\n")<-- exit my telnet session

print tn.read_all()  <--display the output of both commands.?

---

### Post by jseiser on 2007-12-14
wow, i think im getting it  lol.

#import getpass <---just hardcoding the password seems to get me into the router.
import sys
import telnetlib

HOST = "111.111.111.111"
password = "password"
vpc = raw_input("Enter The VPC Number: ")
#password = getpass.getpass()

tn = telnetlib.Telnet(HOST) 

#tn.read_until("login: ")
#tn.write(user + "\n")
#if password:
tn.read_until("Password: ")  <--seems to work because i get into the router.
tn.write(password + "\n")

tn.write("sh int atm6/0.vpc\n") <--is my problem, it inputs "vlc" instead of the var in vlc.
tn.write("exit\n")

print tn.read_all()

----- here is what i see when i run the program.
>>> 
Enter The VPC Number: 240 <--prompted for, and i put it in.


pc-core-1>sh int atm6/0.vpc <--see it doesnt insert the variable i need, it puts in the literal "vpc"

                        ^

% Invalid input detected at '^' marker. <--good because its outputing what the router is saying.



pc-core-1>exit   <- its obviously putting 'exit' into the prompt, but it doesnt actually exit because i have to manually close telnet to be able to run my program again. 

just need it to get the variable saved in "vpc" instead of literally getting "vpc" wrote.


>>>

---

### Post by jseiser on 2007-12-14
tn.write("sh int atm6/0.vpc\n")

I know that line is wrong.  I need something like
tn.write("sh int atm6/0." + vpc "\n")  but that is obviously incorect sytax.  I need to insert a variable after a string literal and then put in the new line.

---

### Post by zero-9376 on 2007-12-14
this seems to do what you want?

>>> vpc='test'
>>> print("sh int atm6/0." + vpc + "\n")
sh int atm6/0.test

>>>

---

### Post by jseiser on 2007-12-14
thanks for everyones help its now working when ran from the interpreter. yet when i run it just from the icon it runs and closes automaticly.  How can i close it manually?
#import getpass
import sys
import telnetlib

HOST = "111.111.111.111"
password = "password"
vpc = raw_input("Enter The VPC Number: ")
#password = getpass.getpass()

tn = telnetlib.Telnet(HOST)

#tn.read_until("login: ")
#tn.write(user + "\n")
#if password:
tn.read_until("Password: ")
tn.write(password + "\n")

#tn.write("sh int atm6/0.vpc\n")
tn.write("sh int atm6/0." + str(vpc) + "\n")
tn.write("sh arp | in " + str(vpc) + "\n")
tn.write("exit\n")

print tn.read_all()
----
it would be nice to have it do some checking for me.
I actually get a vpc as 1/240, which is really 101240.
I would really need some sort of if statement that takes a substring of the first character and see if its nothing, 1, 2, 3, or 4.

If vpc.indexof("/") = -1 then 
vpc = vpc
else left = vpc.substring(0,1)
right = vpc.substring(2,3)
Else If left = 1 then
 left = 101                                       <--I think this code would work for VB, probably got some **** screwed up, but how would that translate to python?
Else if left = "2 "
then left = 102                                 <--- i want to take vpc apart, figure out the first number, then concatenate the 2 strings back into 1 number before i run the router commands.
Else if left =" 3"
then left = 103
vpc = left+right
End If

tn.write("sh int atm6/0." + str(vpc) + "\n")
tn.write("sh arp | in " + str(vpc) + "\n")
tn.write("exit\n")

print tn.read_all()

---

### Post by jseiser on 2007-12-14
n/m its working.

---

