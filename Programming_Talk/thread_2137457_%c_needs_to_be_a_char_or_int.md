---
title: "%c needs to be a char or int"
date: 2013-04-20
forum: Programming Talk
---

### Post by ki4jgt on 2013-04-20
Have a python cgi script in which I've placed 5 %s, these are where I'm going to display messages to the user if they make a mistake. My only problem is, when I run the script, I get %c needs to be a char or int. Here's my code: I've commented out the IP obtaining code and set it manually because it doesn't get it in the terminal. I've also printed out the values collected by the form so I can make sure they're being processed.

```

#!/usr/bin/env python

import cgi
import os

data = cgi.FieldStorage()

n = ""
p = ""
v = ""
b = ""
a = ""

#ip = cgi.escape(os.environ["REMOTE_ADDR"])
ip = "127.0.0.1"

print "Content-Type: text/html\n\n"
if ip != "127.0.0.1":
    print "<h1>THIS PAGE ISN'T FOR YOU!</h1>"
else:
    print data.getvalue("name")
    print data.getvalue("password")
    print data.getvalue("verify")
    print data.getvalue("start")
    print data.getvalue("ads")
    print """
<!DOCTYPE html>
<html>
    <head>
        <title>Smashnet Setup</title>
    </head>
    <body>
        <form name = "setup">
            <table width = 100% cellpadding = 20>
                <tr>
                    <td colspan = 3>Smashnet Setup
                    Welcome to the Smashnet setup wizard. Smashnet's goal is to maintain a self-supporting P2P network with virtually
                    100% uptime while remaining both secure and completely decentralized. To accomplish this goal, Smashnet needs to get
                    some basic information from it's users.
                    <p>THOUGH IT IS AN UNFORESEEN SIDE-EFFECT, THIS PROJECT DOES NOT FOCUS ON ANONYMITY. IN FACT, WE ARE WORKING HARD TO
                    CLOSE WHATEVER GAPS WE CAN IN WHICH INDIVIDUALS MAY HIDE. IF YOU HAVE SOMETHING TO SAY ONLINE, YOU SHOULD BE ADULT
                    ENOUGH TO STAND BEHIND IT!</p></td>
                </tr>
                <tr>
                    <td>Name:</td>
                    <td><input type = "text" name = "name"></td>
                    <td width = 500>In a P2P network, each individual gets their data from someone else on the network. Because there is NO
                    central authority upon which to authenticate that data, there needs to be another way of doing things. Enter,
                    data signing. Each status update is signed with a digital signature which only you can have. Everyone who wants to
                    subscribe to your status updates will ask the network for a special file which will tell them if a status was
                    signed by you or if it is a fake. If it's real, the status will be added to their time-line. If it's fake, the
                    status will be deleted and no one will see it. Each signature needs a name which is the name your friends will
                    see when your statuses display on their screens. <em>YOU CANNOT CHANGE THIS LATER</em><br /> %s <hr /></td>
                </tr>
                <tr>
                    <td>Password:</td>
                    <td><input type = "password" name = "password"></td>
                    <td>In case your digital signature is ever stolen by hackers or your angry ex, please provide a 10-20 character
                    alpha-numeric password which will be used to encrypt it.<br /> %s <hr /></td>
                </tr>
                <tr>
                    <td>Password:</td>
                    <td><input type = "password" name = "verify"></td>
                    <td>Please verify password.<hr /><br /> %s </td>
                </tr>
                <tr>
                    <td>Starting Node:</td>
                    <td><input type = "text" name = "start"></td>
                    <td>Since there aren't any official dedicated servers to tell your node where to join the network you will need
                    to enter a network starting point. Your node will connect to this other node and obtain connection information
                    for other nodes in the network.<br /> %s <hr /></td>
                </tr>
                <tr>
                    <td>Advertising:</td>
                    <td><input type = "radio" name = "ads" value = "yes">Yes<br />
                    <input type = "radio" name = "ads" value = "no">No</td>
                    <td>Smashnet is 100% sponsored by two small advertisements in the uppper-right corner of your time-line. To be
                    considerate to the users, Smashnet would like your permission to display these two ads. They're no larger than
                    two of Google's single ad blocks and there is no personal information submitted. Since you are getting this
                    service for FREE, we do think you should feel compelled to contribute a bit back to the community so we all may
                    enjoy future updates and services but the choice is completely up to you. We make a little less than 2 cents
                    (USD) every time you load your time-line. To all our fans, please do not abuse this system as though it makes
                    Smashnet more money, it goes against our values and cheats the only people who are actually willing to support
                    our project. Thanks.<br /> %s <hr /></td>
                </tr>
                <tr>
                    <td><button type = "submit" formmethod = "post" formaction = "setup.py">Configure Setup</button></td>
                    <td><button type = "reset">Reset</button></td>
                </tr>
            </table>
        </form>
    </body>
</html>
""" % (n, p, v, b, a)

```

I'm getting a %c needs to be an int or char from terminal.

I know it's probably something dumb but I've looked over and over for what's going on and cannot find it. :(

---

### Post by trent.josephsen on 2013-04-20
```
            <table width = 100% cellpadding = 20>
```
It's probably advisable to use the "new" formatting method (str.format()) as futureproofing.

---

### Post by ki4jgt on 2013-04-20
> **trent.josephsen said:**
> ```
            <table width = 100% cellpadding = 20>
```
It's probably advisable to use the "new" formatting method (str.format()) as futureproofing.

Thanks a lot :). Just read up on that. It's awesome! Have a nice day and I'm hoping to release an ALPHA of this to the community soon for anyone interested. It's going to be fully open sourced. I will probably be here again with some more questions like this (just a warning).

---

### Post by epicoder on 2013-04-23
I know this has technically been solved, but I'd like to point out an issue with your HTML before it becomes, well, an issue.
```

<table width = 100% cellpadding = 20>

```
There are two problems here. 1 is, your attributes are not quoted. While this is generally not an issue with numbers, it is technically against the standard. You should quote them.
2, there are spaces between your attribute names, equal signs, and values. While this does make the code look nice and most browsers can deal with it, going by the standards, here is how that code will be parsed:

```
<table width="" cellpadding="">
```
The problem with spaces in your tag attributes is that attributes are separated with them. So you are technically specifying 6 empty attributes, 4 of which are invalid.


```

<input type = "radio" name = "ads" value = "yes">

```
QUOTES YES GOOD.
However, see the spacing problem above. This snippet yields:

```
<input type="" radio="" name="" ads="" value="" yes="">
```

---

### Post by Carl H on 2013-04-23
A further small point...  if you want a % inside a string in Python, use %% for a single % - otherwise it's interpreted as a formatting instruction, as you found.

---

### Post by ki4jgt on 2013-04-25
Thank you all so much for your input. I will try to correct these. I don't don't if I can deal without the spaces as I've used them in every programming language I've ever learned and it annoys me on an odd level when other devs don't use them but anywho I will be placing the perenthesis and %% characters in. I am also going to be placing this into a Google Code project. If anyone is interested in downloading future updates of it. I'll also be marking this a solved.

---

