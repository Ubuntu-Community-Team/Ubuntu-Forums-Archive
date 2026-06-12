---
title: "Adding a line in the middle of a file?"
date: 2013-07-03
forum: Programming Talk
---

### Post by rondamato on 2013-07-03
Hello friends,

Just had a quick question for you all...not sure if this post belongs in this forum and if it does not I apologize. It involves BASH shell scripting.

At my company I am building a new template that is used to build Ubuntu VDIs. It is based on Xen.

The way that this works is...the creator of the VDI is allowed to pick a "template" that they then assign a name, ID, and overhead number to. There are many templates and each has different stuff installed...such as a 32-bit 10.04 template, a 64-bit 12.04 template, a 12.04 template with Hadoop...you get the idea.

Anyhow, when these machines are being built a shell script goes out to an FTP server where the name of the VDI (picked by the builder) is stored as a textfile. Each textfile is identified by a MAC address and each new machine is given a MAC one step up from the last. So...if I built a machine for myself my VDI name--let's say its "rdamato"--is stored as a one-line textfile. The file is named by whatever the VDIs MAC is going to be...so let's say mine is 00:00:00:00:00:23. One of the buildscripts gets the machine name by going to the FTP server that the textfile "00:00:00:00:00:23.txt" is stored on, then the variable $HOSTNAME is set to the contents of this file, which would be the single line "rdamato." Hey, I didn't come up with it! ; ')

Anyhow, my skills with *sed* are VERY rusty. What I am trying to do seems simple enough. One of the buildscripts uses the above information to generate an */etc/hosts* file. So...I have a file that contains something like:

```
127.0.0.1 localhost
127.0.1.1 rdamato.companydomain.com   company domain
#IPv6 stuff
fe00::0 ip6-localnet
ff00:0 ip6-mcastprefix
```
...and so on.

What I am trying to do is to insert the line "157.128.11.22 companydnsserver.domain.com" AFTER all of the 127.x.x.x lines, but BEFORE anything else.

Obviously I would use *sed *to do this, but the exact syntax is throwing me off big time.

So basically, *sed* would be running in a script, and it would be inserting the SAME line each and every time. Seems easy enough, right? Well...maybe for *you*it is!! I am having a bear of a time doing it.

Anyhow, if anybody has any tips or suggestions as to how to go about this chore, it would be greatly appreciated. Thank you!

Ron

---

### Post by VMC on 2013-07-03
```
sed 's/127/&\nTHIS GOES AFTER/' <file>
```
Will put lines after each occance. Something to work on.

---

### Post by Vaphell on 2013-07-04
> Obviously I would use sed to do this, but the exact syntax is throwing me off big time.

That's not so obvious because sed sucks in cases of selective transformations where you are interested only in one of many matches.
Why bother with sed outside of its mainstream scenarios, which is not intuitive at all with 2 data buffers total, when you have awk?

```
awk '/^127/{x=1} !/^127/ && x { x=0; print "157.128.11.22 companydnsserver.domain.com"; } { print $0; }'
```
awk can't modify source directly so you have to dump output to a temp file and mv it later.

---

### Post by varunendra on 2013-07-04
> **VMC said:**
> ```
sed 's/127/&\nTHIS GOES AFTER/' <file>
```
Will put lines **[COLOR="#FF0000"]after each occance[/COLOR]**. Something to work on.
As you pointed out, this will append the line after EACH instance of 127xxx line, while the OP seems to need it In-Between where such instances end, and different pattern starts -
> **rondamato said:**
> What I am trying to do is to insert the line "157.128.11.22 companydnsserver.domain.com" **[COLOR="#FF0000"]AFTER all of the 127.x.x.x lines[/COLOR]**, but BEFORE anything else.

@ Ron,

I'm not good with sed either, and while this may be possible within sed itself, I think this should work (assuming all the instances of 127xxx lines are together, without blank lines in-between, and start at the very first line or after a fixed number of lines in the source files) -

```
flag=`grep -c ^127 source_file`; sed "$flag a 157.128.11.22 companydnsserver.domain.com" source_file > target_file
```
Make sure to use double-quotes so that the variable can expand to its value.

If the "127xxx" lines begin after a fixed number of lines, say "N", you can use $flag+N instead.

However, if the "127xxx" pattern starts after undetermined number of lines, or may have blank lines in-between, you may have to use grep -n + some filter to determine the number of the last line that contains that pattern, then use that number in sed to append (a) your desired line.

I hope someone having actual experience of scripting could post a less insane solution. :P


**EDIT:**
Late again as usual :P.
I started when Vaphell's post wasn't there, and ended up 20 min. late ....
(oh, and while writing the last line "I hope someone....", I had these two words in mind - "Vaphell" and "awk" ;))

---

### Post by VMC on 2013-07-04
How about this:

cat X:
```
[SIZE=2]27.0.0.1 localhost
127.0.1.1 rdamato.companydomain.com   company domain
#IPv6 stuff
fe00::0 ip6-localnet
ff00:0 ip6-mcastprefix[/SIZE]
```

```
[SIZE=3]sed -i '/^127.0/{N;s/$/&\n157.128.11.22 companydnsserver.domain.com/}' x[/SIZE]
```

cat X:
```
127.0.0.1 localhost
127.0.1.1 rdamato.companydomain.com   company domain
**157.128.11.22 companydnsserver.domain.com**
#IPv6 stuff
fe00::0 ip6-localnet
ff00:0 ip6-mcastprefix
```

---

### Post by Vaphell on 2013-07-04
doesn't work too well as it assumes exactly 2 127.x.x.x lines
```
$ echo "127.0.0.1 localhost
127.0.0.1 localhost
127.0.0.1 localhost
127.0.1.1 rdamato.companydomain.com   company domain
#IPv6 stuff
fe00::0 ip6-localnet
ff00:0 ip6-mcastprefix" | sed '/^127.0/{N;s/$/&\n157.128.11.22 companydnsserver.domain.com/}'

127.0.0.1 localhost
127.0.0.1 localhost
**157.128.11.22 companydnsserver.domain.com**
127.0.0.1 localhost
127.0.1.1 rdamato.companydomain.com   company domain
**157.128.11.22 companydnsserver.domain.com**
#IPv6 stuff
fe00::0 ip6-localnet
ff00:0 ip6-mcastprefix
```

---

### Post by rondamato on 2013-07-04
Hey there,

THANKS!!! To all of you.

Vaphell, when you get the time can you tell me EXACTLY what this line does, piece by piece?

I last used *awk* around 1995 in FreeBSD so my *awk* skills are even MORE rusty...but it looks like this will work.

BTW, there will only be two 127.x.x.x lines in the auto-gen /etc/hosts...or rather, there SHOULD only be two.

Thank you!

---

### Post by rondamato on 2013-07-04
Hey, me again.

These are ALL great answers...thanks to all of you folks! Awesome!

I will try this code in my script tomorrow and see if all works as planned. It should by the looks of it.

One last thing, may or may not be related...I'm using Likewise Open for AD auth. I have PAM set up to authenticate to AD first, then to fall back to Linux. I am using an "AssumeDefaultDomain true" to eliminate entering DOMAIN/user name at the prompt.

I wonder....will the /opt/pbis/bin/domainjoin-cli *setname* command actually set the computer name CORRECTLY?? Like...actually set it in both /etc/hosts and /etc/hostfile? Some of these VDIs have the problem of *sudo* taking a LONG time, like 45 minutes or more, to run...even something like ```
sudo echo 'hi'
```
will take 25-45 minutes.

I was thinking this was from a mis-named machine in a host file but they are correct. If I understand correctly sudo will hang if it cannot get a route to host...and will then authenticate locally (after a LONG wait). Any other ideas?

Again, you guys are the best. Thank you!!

---

### Post by varunendra on 2013-07-04
> **rondamato said:**
> ....One last thing, may or may not be related...I'm using Likewise Open for AD auth. I have PAM set up to authenticate to AD first, then to fall back to Linux. I am using an "AssumeDefaultDomain true" to eliminate entering DOMAIN/user name at the prompt.

I wonder....will the /opt/pbis/bin/domainjoin-cli *setname* command actually set the computer name CORRECTLY?? Like...actually set it in both /etc/hosts and /etc/hostfile? Some of these VDIs have the problem of *sudo* taking a LONG time, like 45 minutes or more, to run...even something like ```
sudo echo 'hi'
```
will take 25-45 minutes.

I was thinking this was from a mis-named machine in a host file but they are correct. If I understand correctly sudo will hang if it cannot get a route to host...and will then authenticate locally (after a LONG wait). Any other ideas?

I believe this question above will get better answers in the Server Platform section of the forums : [http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)
Post a different thread with the question there, as it is not related to the topic here, so may not get attention of the people who may help with this.

---

### Post by SeijiSensei on 2013-07-04
Can I ask what might seem like a dumb question?

Since the order of entries in /etc/hosts is meaningless, why can't you just append the dnsserver line to the bottom of the file with "echo '157.128.11.22 companydnsserver.domain.com'  >>  /etc/hosts"?

Surely that is easier than any complicated sed or awk expression.

---

### Post by rondamato on 2013-07-05
Hey,

No, that's not a dumb question at all...

Here's the answer: that's what I THOUGHT but my boss, who I THOUGHT knew Ubuntu better than me, told me that it DID matter. Since it does not (I know now) I guess I'll just do what I was gonna do and stick a >> on the output of that echo...

So it really doesn't matter? I thought that the ipv4 stuff all had to be together...if this is the case I'm marking this solved and moving on--although I appreciate all of the sed/awk answers VERY much! Learned a lot!!!

Ron

---

### Post by Vaphell on 2013-07-06
explanation of awk code

for each line awk tries conditions of {} blocks to see which blocks should be executed
```
awk '       /^127/ { x=1; } <- this one sets marker to 1/true only when line is 127...
      !/^127/ && x { x=0; print "157.128.11.22 companydnsserver.domain.com"; } <- this one executes only once, in the line directly following last 127 line (not-127 AND x set to 1/true) because x gets reset to 0 and the condition can't be met anymore.
                   { print $0; }' <- print line unconditionally
```

in effect the first line after 127 block gets that additional code which injects 157.128.11.22 before printing the line itself.

---

