---
title: "Help:Remote control via email"
date: 2011-06-10
forum: Programming Talk
---

### Post by n2o-Gr55 on 2011-06-10
Hey all, not sure if this would belong here, but I suddenly had inspiration for a project.

(Also, sorry if the title isn't very descriptive, hard putting it into words.)

Anyway, I had an idea for a project, and wanted to know if it was possible.

Basically, if a certain string is sent to my email address, I would like it to respond with a certain action.

For example, if I sent an email to this address containing the string string "time", How could I make it so that it replies to the message with the current time.

I was wondering if this is possible, and if so, how could I go about doing it?

I know I would have to
1.Detect email
2.Detect a specific string
3.Create the reply
4.Send the reply.

It would be preferable if it could all be done in a shell script, but I am open to other alternatives.

Thanks for the help,
n2o-Gr55

---

### Post by BkkBonanza on 2011-06-11
This would be quite easy to do in several languages. I would choose Python but it could be done in shell as well. You have the basic steps already so you just need to read up on the functions (or in shell, programs) for checking and sending mail. Detecting a string in the message is easy with string search/find/grep functions/tools. You can write a simple dedicated program or better yet make it more functional by having it read the match string and commands from file or config.

---

### Post by n2o-Gr55 on 2011-06-11
Thanks!

I wasn't aware that shell had email functions, I will have to read up on that, I thought I would have to leech information off of Evolution or something.

This will be one of my first real shell projects, wish me luck!

---

### Post by BkkBonanza on 2011-06-11
I don't think the shell has email functions built in. But you can use an email program in a command line mode to do what you need. I haven't done this but thinking about it suggests looking at the **mail** program and seeing how you can use it to retrieve mail and store it to be processed by the script.

For that you would start with **man mail** to see what commands are used and then do some experiments with running mail at the prompt with piping to file to see how you can control it in a script. What initailly comes to mind is that you could run mail and pipe the message headers to a "while read" loop which handles each message. I think by specifying the print option you could get the full message for each time thru the loop.

Not having tried it I'd guess something like this may work,

```

while read x; do
  # process msg here 
  # get msg by number
  # handle it as string to check for conditions
  # run command if conditions true
  # remove msg if desired
done < mail 

```

You may find exim more useful than mail. I haven't explored this but my impression is that exim has more support for pop/imap if you need that.

---

### Post by n2o-Gr55 on 2011-06-11
After many hours of googling (and headaches.) I finally got Exim4 configured. Shortly after this, I learn that exim is a mail sending client only.   Can you suggest a good IMAP daemon?

---

### Post by BkkBonanza on 2011-06-11
I did a short google for this and found **[fdm]("http://fdm.sourceforge.net/")** seems to have support for rules built in and filtering, so that may do a lot of what you want in one package.

Edit: upon reading the fdm manual a bit I think that gives you much of what you need because it allows defining actions on emails that match a ruleset. See the exec action as it allows running a command. So then you just put fdm in a cron to get regular mail checks.

I thought exim did mail retrieval as well as sending mail but I could be wrong there. I don't use it but I suggested it because it was supposed to be a default install on ubuntu.

---

### Post by n2o-Gr55 on 2011-06-11
FDM Sounded perfect, but when I tried to configure it for my email account... I found no conf file! The manpages told me the two places it stores it, and there was no file there, and the -f flag that allows you to specify a custom conf file didn't work, it displayed help (as if it were a syntax error) when I tried.

---

### Post by BkkBonanza on 2011-06-12
Tha's weird. What do you get with, 

fdm -nvv

---

### Post by n2o-Gr55 on 2011-06-14
(results of fdm -nvv) version is: fdm 1.6, started at: Tue Jun 14 03:28:46 2011 running on: Linux 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 host is: PC localhost.localdomain 127.0.0.1 home is: /home/me loading configuration from /home/me/.fdm.conf /home/justin/.fdm.conf: world readable or writable added account "me": fetch=imaps server "imap.gmail.com" port 993 user "usr@gmail.com" folders "INBOX" configuration loaded locking using: flock  options are: maximum-size=33554432, timeout=900, default-user="me", command-user="me", file-umask=077, queue-high=2, queue-low=1, strip-characters="\$%^&*|{}[]"'`;" using tmp directory: /tmp

---

### Post by n2o-Gr55 on 2011-06-19
Mutt has shown some promise, but I am having a bit of trouble configuring it for POP3/IMAP

---

### Post by n2o-Gr55 on 2011-06-24
Shameless bump...

---

### Post by aeiah on 2011-06-24
what email address are you using? if it doesnt matter, set up a gmail account and see what some of the many guides for gmail+mutt tell you.

---

### Post by n2o-Gr55 on 2011-06-25
Errrm, I am using gmail, thank you for reminding me to **Search before making a post, not just before making a thread.**

---

### Post by SeijiSensei on 2011-06-25
You want to learn about [procmail]("http://www.procmail.org/").  It's designed to grep messages for strings and take actions based on what it finds.

---

