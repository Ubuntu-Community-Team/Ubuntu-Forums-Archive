---
title: "Need help with a simple bash script"
date: 2012-05-17
forum: Programming Talk
---

### Post by Nailox on 2012-05-17
Hi all. Some time ago a purchased a bash script for rotating IPs with postfix. Its a simple script that changes the inet_interfaces setting in the postfix config file and then restarts it. The person who sold me the script said it's limited to 10 IPs but from what I see in the script there is no such limitation, so Im not sure if he meant that the script is limited to rotating up to 10 IPs or the service he was providing is for setting up 10 IPs only. I lost the contact info of that person so I can't ask him. So if anyone here is willing to help me - please post in this thread and I will PM you the script (I can't post it in public) so you can take a look and tell me if it can work with more than 10 IPs. As I said the script is pretty simple (about 50 lines) and if you know bash it will take you 2-3 minutes to figure it out. Thanks!

---

### Post by Habitual on 2012-05-17
echo "$PMs"

---

### Post by hakermania on 2012-05-18
You shouldn't purchase such things :) We are all here willing to help :)

---

### Post by Vaphell on 2012-05-18
> You shouldn't purchase such things

why not? it all depends on how much one values one's time. If you need to invest hours upon hours to get some understanding of scripting only to attempt handmade solution it may be well worth it to drop in 50 bucks and just get it done. People go to mechanic to perform trivial maintenance of their cars, people go to restaurants despite having a kitchen at home. Yes, there is a drawback of being dependent on 3rd parties but that's how the world works and that's where the jobs for specialists come from.

---

### Post by Lars Noodén on 2012-05-18
If you can't post the script, how about posting the description of what it should do?

---

### Post by Habitual on 2012-05-18
It's a unrestricted .sh script that 
sed -i "new_ip_string" > {proc,send}mail.conf?
service restart
sleeps 520

---

