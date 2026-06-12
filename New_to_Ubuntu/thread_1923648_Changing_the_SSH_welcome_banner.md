---
title: "Changing the SSH welcome banner"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by camjulesjjhr on 2012-02-11
I'd like to change the banner to a custom message instead of the Ubuntu default. I'm using Ubuntu Server 11.10.

---

### Post by savanna on 2012-02-11
Edit the file **/etc/ssh/sshd_config**. 

Uncomment the line that says "**#Banner /etc/issue.net**". 

Put your greeting in the file **/etc/issue.net**. 

Get the ssh server to re-read it's config: **sudo service ssh reload**

---

### Post by ceerious on 2012-02-17
Thank you savanna,

That was exactly what i was looking for and worked perfectly.

kind regards,
cee

---

### Post by ceerious on 2012-02-17
I've got another question though. How (I know there must be a way) is it possible, to still display the last login like it used to?
Would it be a good idea to use update-motd?

I mixed something up there...
Your tip works great for the ssh login screen. I originally tried to change the motd (message of the day) message, that appears after the login.

---

### Post by kevdog on 2012-02-17
I believe the command lastlog is what you want.

If you type
lastlog -u $USER

You'll get what you want.
If you just want the information in column 4, it could be done by the following:

lastlog -u $USER | sed -n "2{p;q}" | tr -s ' ' | cut -d' ' -f4-9

That should give you what you want!!
(Basically it uses the lastlog command to lookup last login for current user, it gets the second line of the output (the first line are column headers, it squeezes all the extra space from multiple spaces to one space, and then takes fields 4-9 which is the last login time)

---

### Post by ceerious on 2012-02-17
Hi Kevdog

Thank you for your help. I did not know the lastlog command.
I would prefer to see the name and time of anyone who logged in at last, not only the $USER.

But that is already implemented in motd. So maybe it would be better to just alter this message.

---

