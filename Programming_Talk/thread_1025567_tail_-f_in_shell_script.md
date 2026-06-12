---
title: "tail -f in shell script"
date: 2008-12-30
forum: Programming Talk
---

### Post by RobbieVeer on 2008-12-30
Hey 

I'd like to make a continouos shell script that runs a custom-made Nmap application if my dhcp server gives away an ip-adres

I was thinking about something like this:
This doesn't work, it's pseudocode 

```

#! /bin/sh
#
if [ sudo tail -f /var/log/syslog | grep "dhcpd: DHCPACK" ]
then

ip=sudo tail /var/log/syslog | grep "dhcpd: DHCPACK" | cut -d " " -f 9 
nmap $ip

fi
exit 0
```

The part of ip=blahblah and nmap $ip works but now i'd like to give it an continouos if statement

I don't have that much experience with shell scripts so I could use some help:P

---

### Post by laceration on 2008-12-30
I always do #!/bin/bash, so there is a slight possibility this won't work in
#!/bin/sh.  There is a concept in bash called *Command Substitution*.  Look into this.  It would work something like this:
```
if $( sudo tail -f /var/log/syslog | grep "dhcpd: DHCPACK" )
```
You might have to set it to a variable and then test it
```
somevariable=$( sudo tail -f /var/log/syslog | grep "dhcpd: DHCPACK" )
if test -z $somevariable
...
```
and doublecheck the conditional statements, it's so easy screw that up in shell/bash compared to other languages.

---

### Post by Cracauer on 2008-12-30
But the tail -f will never return.  This aint gonna work as-is.

If you want a trigger based on when a certain phrase first shows up in a file you either have to make a custom program or trust that `grep -q` aborts instantly and give the guy before it in the pipe the broken pipe treatment.  GNU grep happens to do that but it is not documented behavior in POSIX and I don't think the GNU grep documentation guarantees it either.

In addition, there is buffering in the pipe between tail and grep, and the buffers are not flushed when a newline shows up (like they are for interactive use).  This can backfire big time, there might be a large delay between a string being passed to syslog and a trigger like this going off.

Also, don't sudo this.  Edit syslogd.conf to give you the information you want in a new logfile and give that permissions that are available to the programs in question.

Anyway, to summarize, you might want to experiment with something like this:

```

if tail -f /var/log/foo | grep -q foobar ; then
   myvar=`grep foobar /var/log/foo | tail -1`
fi

```

I hope you understand why you can't combine the two greps.

There are obvious race conditions here, plus the buffering I mentioned. Doing a special program seems better.  At least you need to test this mechanism by artificially inserting statements into syslog and see what kind of delay you have.

---

### Post by laceration on 2008-12-30
if there are those buffering problems maybe something like this would work:
```

$(tail --bytes=256 /var/log/foo) > ~/mylog #writes to mylog file
somevariable=$( cat ~/mylog | grep something )
if test -z $somevariable
...

```
--bytes=256 is another way to try, man tail for ideas
you can't use sudo like that, because it requires input, it threw me off when you said it worked.
the backticks (``) are alternate syntax for Command Substitution. `foo` == $(foo)

---

### Post by RobbieVeer on 2008-12-31
Thanks guys..
I'll check it out in the weekend, because of new years eve and such
Happy New Year!!

---

