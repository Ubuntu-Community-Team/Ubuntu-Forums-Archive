---
title: "multiple words pattern matching in regex"
date: 2013-11-25
forum: Programming Talk
---

### Post by termvrl on 2013-11-25
Hi all,
im new to regex.
what im trying to do is to match a few keywords and take it as a variable.

For example:
i have a sample log:

```

192.168.0.13|<131>Nov 22 06:15:36 ubuntu apache-errors: [Fri Nov 22 06:15:33 2013] [error] [client 192.168.0.111] ModSecurity: Warning. Pattern match "\\\\balert\\\\b\\\\W*?\\\\(" at ARGS:name. [file "/etc/modsecurity/activated_rules/modsecurity_crs_41_xss_attacks.conf"] [line "148"] [id "958052"] [rev "2.2.5"] [msg "Cross-site Scripting (XSS) Attack"] [data "alert("] [severity "CRITICAL"] [tag "WEB_ATTACK/XSS"] [tag "WASCTC/WASC-8"] [tag "WASCTC/WASC-22"] [tag "OWASP_TOP_10/A2"] [tag "OWASP_AppSensor/IE1"] [tag "PCI/6.5.1"] [hostname "192.168.0.13"] [uri "/dvwa/vulnerabilities/xss_r/"] [unique_id "Uo9nBX8AAQEAAASiAh8AAAAA"]

```

is it possible to match a pattern [msg "Cross-site Scripting (XSS) Attack"] AND [severity "CRITICAL"] ?

And output a new line to the file - "Attack type - Cross-site Scripting, Severity - Critical."

Thanks
kindly share if u have a good regex tutorial for beginner.

---

### Post by sisco311 on 2013-11-26
You didn't specify what kind of regular expression would you like to use. With GNU/sed you can try something like:
 ```
sed  's/.*\[msg "\([^"]*\)"\].*\[severity "\([^"]*\)"\].*/Attack type - \1, Severity \2/' logfile.log
```

I'll let you try to figure it how it works. But, of course, if you have any questions, please feel free to ask.

---

### Post by termvrl on 2013-11-27
Hi,

I'm using a perl program call sec - simple event correlator.
It has a .conf file for pattern matching using regex. I dont know what kind of regex it use.
so, any way how i can find what kind of regex it use?

btw, i will try your regex first.
Thanks.

---

### Post by Lars Noodén on 2013-11-27
Perl uses its own [regular expression](http://perldoc.perl.org/perlre.html) syntax.  It's widely used outside of perl, too, where it is known as perl-compatible regular expresssion (PCRE).  

You can get a brief overview here:

[http://www.cs.tut.fi/~jkorpela/perl/regexp.html](http://www.cs.tut.fi/~jkorpela/perl/regexp.html)

but that is only touching the surface.

Can you show a line or two from the config file for that program so we can see what it is expecting?

---

### Post by termvrl on 2013-11-27
Hi all,

Thanks for the reply.

Here is the sample conf file(some called it rule file). In this file, it try to do a port knocking program. I will start the sshd if two condition fulfill, first if got attempted to connect on port 12345 and followed by the second attempted to port 54321 within the time window 30 seconds. 

```

#  portknock.conf
#  Portknocking example 2
#
#BSD Jun 27 15:02:58 foohost /kernel: Connection attempt to TCP 127.0.0.1:5555 from 127.0.0.1:4356 flags:0x02
#

type=Pair
ptype=RegExp
pattern=\S+\s+\d+\s+\S+\s+(\S+)\s+/kernel: Connection attempt to (\S+) (\S+):12345 from (\S+):(\S+).*
desc=$0
action=write - first half of key received....
ptype2=RegExp
pattern2=\S+\s+\d+\s+\S+\s+(\S+)\s+/kernel: Connection attempt to (\S+) (\S+):54321 from (\S+):(\S+).*
desc2=$0
action2=write - second half received! Starting sshd for 30 seconds...; shellcmd ./opensesame.sh;
window=30
```

"pattern' and "pattern2" are the sample regex to match with the syslog.

hope you understand, sorry for my Eng.
Thanks

---

### Post by Lars Noodén on 2013-11-27
The patterns look like they fit in substitutions (s///)

Here's a guess at one that does what you describe early on in this thread:

```

s/^.*\[msg "([^"]+)".*\[severity "([^"]+).*$/Attack type - $1, Severity - \u\F$2/

```

---

### Post by termvrl on 2013-11-27
Hi,

it seem that it not recognized the \u\F in the "Severity - \u\F$2/".
So this program use what type of regex? is it same as your link, perl based regex?

---

### Post by Lars Noodén on 2013-11-27
It might not want the leading s.  It is using the patterns differently.

```

^.*\[msg "([^"]+)".*\[severity "([^"]+).*$/Attack type - $1, Severity - \u\F$2

```

The proper format would use s/ / / but the pattern has to fit in to however they happen to have arranged the program.

---

### Post by termvrl on 2013-11-27
Hi Lars,
I managed to solve it by using only this part on "pattern",
 ```

pattern=^.*\[msg "([^"]+)".*\[severity "([^"]+).*$

```

and followed by "action",

```

action=write - Pattern matched, Possible $1 , Severity is $2 

```

So, the output is like this,

```

Pattern matched, Possible Cross-site Scripting (XSS) Attack , Severity is CRITICAL .

```

Thanks again.
=D

---

### Post by Lars Noodén on 2013-11-27
Cool.  

It look like it was using m/ / then and not s/ / /  It's hard to guess without seeing the internals.

---

### Post by termvrl on 2013-11-29
Hi, 
i have a problem to match a floating type number.
Let say, i want to match 20.0 in 20.0%us, 
My current code,
```

cpu=$(top -bn1 | grep -oP '\d\d.\d(?=%us)')

```

But it will prompt error when the cpu usage below 10.0%us, single floating number, 0.0 -> 9.9.

Thanks

---

### Post by Lars Noodén on 2013-11-29
The pattern needs to take into account a variable number of digits with a + or something like that.

```

cpu=$(top -bn1 | grep -oPm1 '\d+\.\d(?=\sus)')

```

The error is probably going to be there regardless of what it finds or doesn't find.  It looks like a bug with top.  You could redirect stderr to /dev/null for that one.

---

