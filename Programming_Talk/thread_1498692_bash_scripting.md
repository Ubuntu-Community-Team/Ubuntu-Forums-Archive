---
title: "bash scripting"
date: 2010-06-01
forum: Programming Talk
---

### Post by Drenriza on 2010-06-01
I'am bash newbie.

How can i get a bash script to look for an error, if it finds this error (that i have told it to look for) how do i get it to send me an e-mail to notify me on it.

Thanks on advance.

---

### Post by BoneKracker on 2010-06-01
What kind of error?  What is making the error?
Is it something that shows up in your logs?

---

### Post by Drenriza on 2010-06-01
An error in logs. An error a program will output to debug logs or something like that.

For example in df if a HDD reaches 80% HDD disk space usage can you then get a bash script to write an notification email?

or if CPU loads keep staying on 80-100% then you also get an notification email.

Im very new at this, and arnt quite sure what is possible and what aren't.

And im sorry if im not as detailed as i could be. Hope you all can bare with me :p

---

### Post by mickwombat on 2010-06-01
Hi there,

What you need is a cron job to do this for you.  I made a little script for my server that does something similar.  You just need to change it to suit your needs.

> #!/bin/bash
if [ -n "`cat /var/log/auth.log | grep sausage`" ]; then   # -n tests to see if the argument is non empty
        sed 's/sausage/replace/g' < /var/log/auth.log > /var/log/auth.log.kat

# Send a test mail to myself
	sendmail -v [email]name@yourdomain.co.uk[/email] < mick.mail &

# Replace the original auth file with the changed one
        cp /var/log/auth.log.kat /var/log/auth.log

# End of script

fi

What this does is it searches the auth.log if a user called sausage has logged in.  If they have, then the sed command will parse the file and replaces 'sausage' with 'replace' and save it to a new file.  It then sends a mail to myself using using the sendmail command and uses the mick.mail file as the input for the message.  The file for the mail is simply

> SUBJECT: <Subject>
Message body goes here.


It then replaces the original auth.log with the ammended file.  This is very important as you will continue to get an email every time the job runs.

Configuring Sendmail is difficult(ish) and somehow I did it after reading numerous posts.  Search on google for 'sendmail isp smtp'.  Have a look at this article though [http://cri.ch/linux/docs/sk0009.html]("http://cri.ch/linux/docs/sk0009.html")

To install the job, run (as root) #crontab -e

I have my job running every 5 mins and the crontab entry looks like this

*/5 * * * * sh /path/to/script

Good luck

---

### Post by BoneKracker on 2010-06-01
```
if grep sausage /var/log/auth.log; then
```

Also, you may have a "mail" command (or maybe "mailx") in ubuntu, which is useful for sending mail with dynamic content from scripts.

---

### Post by Drenriza on 2010-06-01
> **mickwombat said:**
> Hi there,

What you need is a cron job to do this for you.  I made a little script for my server that does something similar.  You just need to change it to suit your needs.



What this does is it searches the auth.log if a user called sausage has logged in.  If they have, then the sed command will parse the file and replaces 'sausage' with 'replace' and save it to a new file.  It then sends a mail to myself using using the sendmail command and uses the mick.mail file as the input for the message.  The file for the mail is simply



It then replaces the original auth.log with the ammended file.  This is very important as you will continue to get an email every time the job runs.

Configuring Sendmail is difficult(ish) and somehow I did it after reading numerous posts.  Search on google for 'sendmail isp smtp'.  Have a look at this article though [http://cri.ch/linux/docs/sk0009.html]("http://cri.ch/linux/docs/sk0009.html")

To install the job, run (as root) #crontab -e

I have my job running every 5 mins and the crontab entry looks like this

*/5 * * * * sh /path/to/script

Good luck

Thanks.

---

### Post by BoneKracker on 2010-06-01
If your needs are more substantial than just checking periodically for a single event, there a numerous packages available that are designed for parsing logs and initiating action, including logwatch, logsurfer, and logcheck, just to name a few.  If you're going to monitor your logs for a number of events, then it may be worth using one of those.  There are also purpose-specific log analysis programs for firewalls and web servers.

Also, if you're going to write your own, consider using perl, which is very well-suited to the task.

---

### Post by Drenriza on 2010-06-01
Unfurtiantly i want to do the bash script because it needs to go on a custom designed Linux kernel. That doesn't support much else then what it was designed for.

With customized hardware & drivers.

Also using as little resources as possible is critical.

This is why i wanted to do it in bash. Instead of a log monitoring  program solution.

---

### Post by BoneKracker on 2010-06-01
> **Drenriza said:**
> Also using as little resources as possible is critical.

If that's the case, then you should write it in C. :p

Seriously, I myself avoid perl like the plague.  But consider that a BASH script invoking both grep and sed could be gobbling up more ram than if you just wrote an awk script.

---

### Post by Drenriza on 2010-06-02
C could be a way to do it.

But im not 100% aware of what c can be used for.
Is it much more complicated to do it in c then in bash?
Can you do all the same things in C as in bash?

Thanks on advance.

---

### Post by BoneKracker on 2010-06-02
C can do much more than BASH; C can do anything.  What you create in C (if done properly) will run faster and use less memory than what you create in BASH.  With C you can interact directly with memory and hardware.  It is much, much more powerful than BASH.

C is _substantially_ more difficult to learn and use than BASH.  It will take you 10 times as long to master C.  It will take you 10 to 100 times longer to create something in C than in BASH.

In BASH you are working with bricks that have already been created and you are plastering them together with bits of simple code.
In C you are working with grains of sand to make your own bricks and mortar (or a concrete fountain, or a marble statue, and other things you can't make out of bricks).

You really don't want to write your own log parser in C, unless your requirements...
> With customized hardware & drivers.
Also using as little resources as possible is critical.
... really demand it.

---

### Post by Drenriza on 2010-06-02
If i would like to try C. Do you know some good guides, books, or toturials that i should take a look on.

Well making something in c from the start, would probably make life easier for me down the road. Since 90% of what is made here is done in c. And i think in c i would have better access to tweak it then in bash.

Based on what i have read.

---

### Post by BoneKracker on 2010-06-02
There are many good sites on the Internet about learning C programming.  Here is one, but you should also search for more:
[http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)

There are seven free books on C programming at the bottom of [this site]("http://www.intelligentedu.com/blogs/post/free_computer_books/287/35-free-c-and-c-programming-books-and-ebooks").

There is all kinds of information available; just look.  You might want to try looking specifically for information on C programming in Linux, such as this:
[http://aplawrence.com/Linux/c_compiling_linux.html](http://aplawrence.com/Linux/c_compiling_linux.html)
[http://www.linuxquestions.org/linux/answers/Programming/Building_C_programs_on_Linux](http://www.linuxquestions.org/linux/answers/Programming/Building_C_programs_on_Linux)

---

