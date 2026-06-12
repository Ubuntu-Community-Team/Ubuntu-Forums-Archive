---
title: "simple pipe for ssmtp after grepping"
date: 2008-04-02
forum: Programming Talk
---

### Post by Rizla on 2008-04-02
I was hoping someone could help me figure out how to send an email to myself of some egrep output

here's what I wrote:

```

egrep '([[:digit:]]{1,3}\.){3}[[:digit:]]{1,3}' index.html | ssmtp myemailaddr@server.com

```

If you cant tell, it lists the IP's in the index.html page and then sends it to my email addr.  Problem is when i get the email, theres nothing in it.

Last bone of contention with ssmtp.  How come i cant specify a subject in the email?  i tried the -s <subject>  but nothing shows up.

Probably not the right forum, but wasnt sure where else to go..

---

### Post by ghostdog74 on 2008-04-02
i don't use ssmtp. I use mailx. and if your emailing envrionment is set up properly.
```

egrep '([[:digit:]]{1,3}\.){3}[[:digit:]]{1,3}' index.html | mailx -s "subject" myemailaddr@server.com

```

---

### Post by Rizla on 2008-04-03
> **ghostdog74 said:**
> i don't use ssmtp. I use mailx. and if your emailing envrionment is set up properly.
```

egrep '([[:digit:]]{1,3}\.){3}[[:digit:]]{1,3}' index.html | mailx -s "subject" myemailaddr@server.com

```


I just wanted a super barebones mailer to send out emails.  I can deal with the lack of a subject line for the time being.  I've actually found a way around that.

ssmtp [email]emaiaddr@server.com[/email] < header.txt

if in the header you have a line that says subject: <a subject>

it works.

BUT, the main issue i'm having is that the output of egrep is not showing up at all for some reason.

---

### Post by ghostdog74 on 2008-04-03
the only probable reason is the pattern is not found, either its really not there, or you have a buggy regular expression. you might want to describe what you want to find with a small sample of index.html.

---

### Post by Rizla on 2008-04-03
> **ghostdog74 said:**
> the only probable reason is the pattern is not found, either its really not there, or you have a buggy regular expression. you might want to describe what you want to find with a small sample of index.html.

here's what i'm trying to do, long story.  I'm using dsl at home which is gives my routher a DHCP address at random intervals.  It's a pain whenever the address changes and I cant ssh into my home pc.  I found a site that lists my router ip.  [www.canyouseeme.org](www.canyouseeme.org)

It lists your IP on the main index.html page. I wanted to create a script that woudl execute a few commands to email me my router ip daily.

start with:

wget [http://canyouseeme.org](http://canyouseeme.org)

-it downloads the index.html to my working dir (home dir)

next i use grep to grab the IP from the html page

grep returns the following output:

<input type="hidden" name="IP" value="xxx.xxx.xxx.xxx"/>
<td><b>xxx.xxx.xxx.xxx<b></td>

I wanted to take this output and pipe it into sendmail or ssmtp and email it to me.

The last bit was to create a daily cron job to do this.  I want to put all those commands into a shell script and have that script run daily.


I havent gotten to putting it in a script or creating the cron job yet becuase I cant get it to send me the output of egrep....

Any ideas?

---

### Post by Rizla on 2008-04-03
Well, quasi good news.  I've managed to put together a script that does what I need it to do.  The problem is that its a little quirky and not very clean.


```

#!/bin/sh
clear
#remove the old index file so that i dont get my old ip
rm index.html

wget http://canyouseeme.org

egrep '([[:digit:]]{1,3}\.){3}[[:digit:]]{1,3}' index.html  >> emailheader.txt

ssmtp myemailaddr@server.com < emailheader.txt



```

FYI, the email header is a simple text file that has
to: [email]myemailaddr@server.com[/email]
subject: My Daily IP email
body:
My Daily IP

This was the only way i could make it so that a subject line would contain info.  

Now the crap about this script.  The egrep command outputs html code and not purely the IP.

Everytime it runs its appending the new IP to the email header.  I can forsee overtime that it would become a long *** email.


I'm really new when it comes to shell scripting and the cli for that matter.  The next step is to have some sort of comparison check.  If the old ip is the same as the new IP, dont append.  If new, append, but remove the old ip.

In due time i will fine tune this.  Currently trying to figure out how to only ouput the ip address fro egrep..

---

### Post by WW on 2008-04-03
> **Rizla said:**
> 
In due time i will fine tune this.  Currently trying to figure out how to only ouput the ip address fro egrep..
Use the **--only-matching** (or **-o**) option in your egrep command.

---

### Post by Rizla on 2008-04-03
> **WW said:**
> Use the **--only-matching** (or **-o**) option in your egrep command.

Thanks a lot!  How would i limit it to only the first listing?  THe file i'm grepping has two entries that match the pattern, but i just want the first returned

---

### Post by WW on 2008-04-03
> **Rizla said:**
> Thanks a lot!  How would i limit it to only the first listing?  THe file i'm grepping has two entries that match the pattern, but i just want the first returned
Take a look at the egrep man page:
> 
$ man egrep

and check out the **--max-count** (or **-m**) option.

---

### Post by Rizla on 2008-04-03
> **WW said:**
> Take a look at the egrep man page:

and check out the **--max-count** (or **-m**) option.

and to think.. I've wasted your time so far becuase I didnt read the F'n man..  sorry.:)

---

### Post by WW on 2008-04-03
No worries.  If we all read all the manuals before asking a question, there would be no one here.  Not because we'd know all the answers, but because we'd all have been bored to death.

---

### Post by Rizla on 2008-04-04
> **WW said:**
> No worries.  If we all read all the manuals before asking a question, there would be no one here.  Not because we'd know all the answers, but because we'd all have been bored to death.

:lolflag:

---

