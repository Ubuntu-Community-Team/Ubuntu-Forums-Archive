---
title: "Python Indentation /If statement Problem"
date: 2008-04-11
forum: Programming Talk
---

### Post by jseiser on 2008-04-11
With the help of these forums, a little while ago I wrote a small code snippet in python, that telnets to our company's router, and runs 2 commands, and then shows me the output.  This is fine, and program runs how I wanted.  The only thing is, when a customer calls, I need to check their 'vci' number ( 1/302, 2/250) in the router, and the way my program is set up, i have to transform 1/250, into 101250 myself, then run the command.  I wanted to set up the program to take a vci of 1/250 and have it check that the first part of the string is a 1, so take it, add a "01" to it, and then slap the rest of the vci back on the number, so the program will now convert for me.  To do this, I needed to set up some error checking, and check which number Im given, and then format it.  I tried to do this, and Im getting invalid syntax and indentation errors. I though that anything after the If statement just needs to be indented more then the if statement, I obviously have something wrong, here is the orginial code, then what i tried to add.

[PHP] import sys
import telnetlib
while True:
    HOST = "000.000.220.120"
    password = "password"
    vpc = raw_input("Enter The VPC Number: ")
    tn = telnetlib.Telnet(HOST)
    tn.read_until("Password: ")
    tn.write(password + "\n")
    tn.write("sh int atm6/0." + str(vpc) + "\n")
    tn.write("sh arp | in " + str(vpc) + "\n")
    tn.write("exit\n")
    print tn.read_all()
[/PHP]

Here is what i added, that doesnt work.

[PHP]import sys
import telnetlib
while True:
    HOST = 000.000.220.120"
    password = "password"
    vpc = raw_input("Enter The VPC Number: ")
    If vpc[:1] = '1':       # check first number
            vpc = vpc[:1] + '01' + vpc[3:]
    elif vpc[:1] = '2': # if its not a 1, check for a 2
            vpc = vpc[:1] + '01' + vpc[3:]
    elif vpc[:1] = '3': # if its neither 1 nor 2, check for 3, error if its 3
            vpc = vpc[:1] + '01' + vpc[3:]
            print ' Wrong Server ( 3/ VPI )'
            time.sleep(5)
            sys.exit(1)
     elif vpc[:1] = > 3 or < 0: # if the first num is neg, or >3, error
            print 'Invalid VPI'
            time.sleep(5)
            sys.exit(1)
    tn = telnetlib.Telnet(HOST)  # if its a 1 or 2, telnet & run cmd.
    tn.read_until("Password: ")
    tn.write(password + "\n")
    tn.write("sh int atm6/0." + str(vpc) + "\n")
    tn.write("sh arp | in " + str(vpc) + "\n")
    tn.write("exit\n")
    print tn.read_all()
 [/PHP]

Where am i going wrong? the code itself might be wrong (probably) but what is the proper 'setup' of that file?  I want to get this part working, so i can make a simple gui.  Thanks all

---

### Post by WW on 2008-04-11
There is an extra space in front of the third elif.

P.S. vpc[:1] is the same as vpc[0].  Also, don't you want vpc[2:] instead of vpc[3:]?  E.g.
```

>>> vpc = '1/250'
>>> print vpc[0] + '01' + vpc[2:]
101250
>>> 

```

---

### Post by WW on 2008-04-11
A few other problems:

When checking for equality, use ==, not =.

This line
[php]
    elif vpc[:1] = > 3 or < 0: 
[/php]
is not going to work.  First, the syntax for the comparisons is not correct, and second, vpc[:1] is a character, not an integer.  I think you mean something like this:
[php]
    elif vpc[0] >= '3' or vpc[0] < '0': 
[/php]
(but what is supposed to happen if vpc[0] is '0'?)

Actually, assuming I understand what you are trying to do, this elif clause appears to be unnecessary.  At this point, you already know that vpc[0] is not '1', '2' or '3'.  It looks like you could change the third elif to a simple **else:**.

---

### Post by jseiser on 2008-04-11
thanks for such quick answers, this forum rocks.  If the first part of the vci is a 0, then the user entered the info in wrong, and the script should kick out, that was this part, or tried to be this part 

[PHP]elif vpc[:1] = > 3 or < 0: # if the first num is neg, or >3, error
            print 'Invalid VPI'
            time.sleep(5)
            sys.exit(1) [/PHP]

Also, all my ide's tell me that syntax problem and indent problem is with the first "if" statement.  Which i cant fix, if I leave it even with everything, its wrong, if i ident it more, its wrong.  So they arent really allowing me any way to fix it.

---

### Post by WW on 2008-04-11
I was editing my previous response while you were responding, so you might not have seen the last sentence of my previous post.  Just change that third elif to **else:**.

---

### Post by jseiser on 2008-04-11
Alright, I tried your changes, still says my indentation is wrong.  I tried komodo, and PyScripter.  I also tried to rid myself of the extra elseif.  if the number is 3 I want it to error, if it isnt 3, its obviously not 1 or 2, so the number is invalid, i want it to throw an error message, and then exit.

[PHP]import sys
import telnetlib
while True:
    HOST = "000.000.220.120"
    password = "password"
    vpc = raw_input("Enter The VPC Number: ")
#this next line is where it shows error in the IDES
# does it need more indent, less indent, I cant seem to find a 
# correct place to stick it.
    If vpc[0] = '1': 
        vpc = vpc[0] + '01' + vpc[2:]
            elif vpc[0] = '2': # if its not a 1, check for a 2
                vpc = vpc[0] + '01' + vpc[2:]
                    else vpc[:0] = '3':
                        print ' Wrong Server ( 3/ VPI )'
                        time.sleep(5)
                        sys.exit(1)
# how can i make it error out if the number isnt 1 or 2?  but isnt a 3
# either?
    tn = telnetlib.Telnet(HOST)
    tn.read_until("Password: ")
    tn.write(password + "\n")
    tn.write("sh int atm6/0." + str(vpc) + "\n")
    tn.write("sh arp | in " + str(vpc) + "\n")
    tn.write("exit\n")
    print tn.read_all()[/PHP]

---

### Post by Can+~ on 2008-04-11
You just published your password? Edit your first message.

[PHP]If vpc[0] = '1': 
        vpc = vpc[0] + '01' + vpc[2:]
            elif vpc[0] = '2': # if its not a 1, check for a 2
                vpc = vpc[0] + '01' + vpc[2:]
                    else vpc[:0] = '3':
                        print ' Wrong Server ( 3/ VPI )'
                        time.sleep(5)
                        sys.exit(1)[/PHP]

could be:

[PHP]
if vpc[0] == '1' or vpc[0] == '2': 
        vpc = vpc[0] + '01' + vpc[2:]
else:
        print ' Wrong Server ( 3/ VPI )'
        time.sleep(5)
        sys.exit(1)[/PHP]

*edit* Another way, more pythonish:

[PHP]
if vpc[0] in ('1', '2'):
	vpc = vpc[0] + '01' + vpc[2:]
else:
	raise "Wrong Server ( 3/ VPI )"
	time.sleep(5)
	sys.exit(0)
[/PHP]

*another edit*

btw, you need to know that
a = b # Assignation, a contains the value of b now.
a == b #Comparison, return true if this are equal, false if different.

I gotta leave, got classes now :)

---

### Post by jseiser on 2008-04-11
whoa, thanks!  heh, good thing i was setting this up against the test server, or that would have a potentially have become a big problem, thanks again.

---

### Post by jseiser on 2008-04-11
it works now.

[PHP]import sys
import telnetlib
import time
while True:
    vpc = raw_input("Enter The VPI Number: ")
    if vpc[0] in ('1', '2'):
        vpc = vpc[0] + '01' + vpc[2:]
        HOST = "0.0.0.0"
        password = "password"
        tn = telnetlib.Telnet(HOST)
        tn.read_until("Password: ")
        tn.write(password + "\n")
        tn.write("sh int atm6/0." + str(vpc) + "\n")
        tn.write("sh arp | in " + str(vpc) + "\n")
        tn.write("exit\n")
        print tn.read_all()
        #time.sleep(10)
        #sys.exit(0)
    else:
        print "Wrong Server ( 3/ VPI ) or invalid VCI"
        time.sleep(1)[/PHP]

---

