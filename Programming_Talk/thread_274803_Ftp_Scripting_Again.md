---
title: "Ftp Scripting Again"
date: 2006-10-10
forum: Programming Talk
---

### Post by dyol on 2006-10-10
as a newbie ihave been helped out by amo-ej1 and  made the script that log into the server by adding username/paswwd and do the copying of files and it gives the time it takes.So now this script may u help again your newbie-i want it to run for say a day and take the output "time" for each transfer done and make a graph-iam testing file tranfer between Ethernet and PLC-so how will i make this run for day copying the same file and sending the stats to a file so that i can graph the output of how it behaved during the day.thx again

---

### Post by duff on 2006-10-10
[http://gnuplot.info](http://gnuplot.info)

Also, check out the man page for "time".  You can modify the output format so you can just have the number of seconds written to a file.

---

### Post by amo-ej1 on 2006-10-11
Why would you want to plot timings ? Wouldn't it make more sense to plot bandwidth usage ? You can get a wget in a loop for example and run a tool like mrtg on the interface. [http://oss.oetiker.ch/mrtg/](http://oss.oetiker.ch/mrtg/) that will present you with out of the box bandwidth usage statistics, all you need to do is generated the bandwidth. Bandwidth makes (imo) more sense than timings.

---

### Post by chi_n_z on 2006-10-11
> **amo-ej1 said:**
> Why would you want to plot timings ? Wouldn't it make more sense to plot bandwidth usage ? You can get a wget in a loop for example and run a tool like mrtg on the interface. [http://oss.oetiker.ch/mrtg/](http://oss.oetiker.ch/mrtg/) that will present you with out of the box bandwidth usage statistics, all you need to do is generated the bandwidth. Bandwidth makes (imo) more sense than timings.



But won't bandwidth usage also include other bandwidth usage info? this guy is only interested in ftp times for a specific file.

---

### Post by dyol on 2006-10-11
> **duff said:**
> [http://gnuplot.info](http://gnuplot.info)

Also, check out the man page for "time".  You can modify the output format so you can just have the number of seconds written to a file.

i have managed to direct the output to a file thanx-the output is like this
> --10:05:16--  [ftp://1.20.5.3/Hustling.doc](ftp://1.20.5.3/Hustling.doc)
           => `Hustling.doc.6'
Connecting to 1.20.5.3:21... connected.
Logging in as mrx ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD not needed.
==> PASV ... done.    ==> RETR Hustling.doc ... done.
Length: 69,120 (68K) (unauthoritative)

100%[===================================================>] 69,120        31.75K/s

10:05:19 (31.67 KB/s) - `Hustling.doc.6' saved [69120]
but it is leaving out the following > 
real    0m2.382s
user    0m0.008s
sys     0m0.008s

this stuff i can only see it on the terminal but not in the file.How can i correct this.thx

---

### Post by amo-ej1 on 2006-10-11
@chi_n_z: when you want to do load tests about something you will _always_ try to isolate what you are testing from the rest, so your test is worthless if you don't do it on a dedicated interface.

@dyol:

a) wget writes to standard output
b) time writes to standard error.

You can redirect all kinds of output like this:
```

i_am_a_command 1>/tmp/stdout.txt 2>/tmp/stderr.txt

```

1>/tmp/stdout means 'write the output of standard output to the file /tmp/stdout.txt'
2>/tmp/stderr means 'write the output of standard error to the file /tmp/stderr.txt'

and here you'll probably want to use 2>>/tmp/stderr.txt to append it (> creates/truncates a file, >> appends to a file or creates when it doesn't exit).

---

### Post by dyol on 2006-10-11
> **amo-ej1 said:**
> @chi_n_z: when you want to do load tests about something you will _always_ try to isolate what you are testing from the rest, so your test is worthless if you don't do it on a dedicated interface.


@amo-ej1:thanx again i managed to direct some of the output but failed  to send this part> 
real    0m2.397s
user    0m0.000s
sys     0m0.004s
[QUOTE]
yeh these are load tests-but i thot since iwas comparing file transfer in two different networks[PLC and ethernet]will it not make sense to also compare the time it takes to download file A in both both networks-having said that how would one isolate bandwith-how one include bandwith in the script-the other thing there is stuff iam failing understand in the output given by the script--the stuff in red
[QUOTE]
--22:08:21--  [ftp://1.2.5.1/Hustling.doc](ftp://1.2.5.1/Hustling.doc)
           => `Hustling.doc.5'
Connecting to 1.2.5.1:21... connected.
Logging in as xxxx ... Logged in![PHP][/PHP]
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD not needed.
==> PASV ... done.    ==> RETR Hustling.doc ... done.
Length: 69,120 (68K) (unauthoritative)

    0K .......... ..74%   [COLOR="Red"]31.19 KB/s[/COLOR]
   50K .......... ..100%   [COLOR="Red"]32.48 KB/s[/COLOR]

22:08:24 [COLOR="Red"](31.52 KB/s)[/COLOR] - `Hustling.doc.5' saved [69120]

---

