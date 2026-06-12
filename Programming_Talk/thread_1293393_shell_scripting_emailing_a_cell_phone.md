---
title: "shell scripting: emailing a cell phone"
date: 2009-10-17
forum: Programming Talk
---

### Post by Girya on 2009-10-17
I am trying to write a shell script that will email my cell phone.

the problem I'm having is when I run the script it exits with no error but I don't receive the text on my phone. the email address is [email]1234567890@vtext.com[/email] 

I can run the command from the terminal but it doesn't work from inside the script. 

the command I run in the script and command line is: 

> $msmtp [email]1234567890@vtext.com[/email] < some_file.txt

I think it has something to do with the number string in the email address.

any tips would be appreciated.

---

### Post by Seq on 2009-10-17
Could you post the contents of the script? I'd be curious to see.

Also, have you configured msmtp globally or just for your user?

---

### Post by Girya on 2009-10-17
> **Seq said:**
> Could you post the contents of the script? I'd be curious to see.

Also, have you configured msmtp globally or just for your user?

here is the script: 

> !/bin/bash

# curl script to retrieve acct bal
#and send it to a cell phone

#variables
cookie_jar=cookies.tmp
web_page=file.tmp
username=username
password=password 

#set cookies
curl --silent --cookie $cookie_jar \
        --output $web_page-1 \
        "https://loginpage"

#authenticate user  
curl --silent --cookie $cookie_jar --cookie-jar $cookie_jar \
        --location \
        --data "Action=LoginName&LoginName=$password&login=Continue"\
        --output $web_page-2 \
        "https://loginpage"

#authenticate password
curl --silent --cookie $cookie_jar --cookie-jar $cookie_jar \
        --location \
        --data "Action=Password&Password=$password" \
        --output $web_page-3 \
        "https://logininpage"

##find account bal
echo $(grep 'FREE' file.tmp-3|sed -e "s/'/ /g" -e 's/.*\([0-9][0-9].\.[0-9][0-9]*\).*/\1/g' -e '2,$d') >> test_msg.txt

#email bal to cellphone
msmtp '1234567890@vtext.com' < test_msg.txt


msmtp has a user config file. I'll look into that. 

also when script is complete I should be able to text my server and have server email me back

---

### Post by Girya on 2009-10-17
update:

I configured msmtp globally by adding a config file in /etc but that had no effect. 

I used to msmtp --debug see the output from smtp server:
```
msmtp --debug
```
It looks as though the server's spam filters were killing the message because there was no subject header. 

After I added "subject" to the echo line in the shell script the text message is received by my phone. 

There is so much to learn when you jump down the rabbit hole.  

Next I need to edit procmail to add a recipe to execute the script when I text my email address.

---

### Post by aesis05401 on 2009-10-17
Thank you for posting your solution.  I learned something.

---

### Post by Girya on 2009-10-18
**Update:**

So to recap, I wanted to be able to text my server and get texted back with a account bal. I wrote a shell script to accomplish this. The utilites used to accomplish this are (in the order they are called):

#crontab #to start fetchmail
fetchmail #to get my mail off a remote server
procmail # to filter emails and start the shell script
shell script
[INDENT]curl #to login and retrieve data from a remote server [/INDENT]
[INDENT]grep and sed # to filter data from file[/INDENT] 
[INDENT]msmtp #a simple sendmail substitute to send mail [/INDENT] 

the script/system is working as planned, now I need to use it for a few weeks to debug it and clean up the script (sed regex is pretty ugly)

here is the .procmailrc recipe that starts the shell script when I text my server. That was the easiest part. I need to figure out a way to differentiate between emails so I can use this technique to have my server text me different info depending on what I need. It'll probably involve using a specific word in the Subject header.  
> :0:
 10 * ^From.*1234567890.*   
 11 |/home/user/bin/script.sh


#line number 10: my cell phone number 
#line number 11 start shell script. used absolute path to shell script
#because procmail wasn't finding my bin directory 

I'm interested in how other people solve this type of challenge, if you have any suggestions please post your ideas.

---

### Post by ahmatti on 2009-10-19
I use SendEmail if I need to send e-mail from a shell script (its in the repos too): [http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)

---

### Post by Girya on 2009-10-20
> **ahmatti said:**
> I use SendEmail if I need to send e-mail from a shell script (its in the repos too): [http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)

It looks interesting, thanks. I'll rewrite my script using SendEmail to test it out. I used msmtp because I had it installed and configured for mutt.

---

