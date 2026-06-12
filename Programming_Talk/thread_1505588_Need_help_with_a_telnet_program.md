---
title: "Need help with a telnet program"
date: 2010-06-09
forum: Programming Talk
---

### Post by hellert88 on 2010-06-09
I need to telnet into a device and program something remotly.  Here is the peice of code that I am working with.  It gives me an error saying timeout in login or if i comment out the login line it says something similar but for the command line.  Any help is great!
 
use Net::Telnet;
print "What is the Trolley Number? ";
chomp($trolley);
$trolley = <stdin>;
@trolley = split('', $trolley);
$telnet = new Net::Telnet (Host=>'ip address');
    $telnet->login($login,$password);
    @line = $telnet->cmd("program tag = 10 00 10 00 10 00 1$trolley[0] $trolley$
    $telnet->close;

---

### Post by trent.josephsen on 2010-06-09
> **hellert88 said:**
> 
use Net::Telnet;
print "What is the Trolley Number? ";
chomp($trolley);
$trolley = <stdin>;
@trolley = split('', $trolley);
$telnet = new Net::Telnet (Host=>'ip address');
    $telnet->login($login,$password);
    @line = $telnet->cmd("program tag = 10 00 10 00 10 00 1$trolley[0] $trolley$
    $telnet->close;

To start with, you didn't put your code in [CODE] tags, you have an unclosed double-quoted string starting on line 8, you are chomping a scalar before you read anything into it, and you are not using strict or warnings.

The phrasing of your message makes me wonder if this code is yours or if you got it from somewhere else.  Care to share?

---

### Post by hellert88 on 2010-06-09
This is in perl, and sure I don't mind I don't know if you will be able to do the same thing that I am trying to do though.

---

### Post by hellert88 on 2010-06-09
New update.....
 
I am able to get the log in and everything but it ill not put my variables in at all.  If I print them after they will print out with what I put in them but for some reason it will not go into the program tag line.

---

### Post by trent.josephsen on 2010-06-09
I think I've misunderstood you somehow.  Can you post the *exact* code?

---

