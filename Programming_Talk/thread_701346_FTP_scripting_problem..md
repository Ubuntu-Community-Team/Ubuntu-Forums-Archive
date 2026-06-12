---
title: "FTP scripting problem."
date: 2008-02-19
forum: Programming Talk
---

### Post by themajesticmoose on 2008-02-19
I'm writing a bash script to do FTP transfers as part of a small distributed-computing project, and I want to save the output so I can grep it to see if the files got transferred. A simple example of the code that I'm thinking SHOULD work is as follows:

pftp -ni mydomain.com <<EOF >logfile.txt
user myusername mypassword
binary
put myfile
bye
EOF
exit 0

The thing is that logfile.txt ends up empty. After a fair bit of experimenting, it's looking to me like maybe ftp doesn't produce output on stdout when its input has been redirected. So, is this a bug in ftp or what am I missing? (Since other people will be running this, I don't want to use another FTP program that is not present by default on all kinds of Unix-like systems.)

(BTW. The transfers are getting done fine, it's just that the output isn't there.)

Thanks in advance.

---

### Post by ghostdog74 on 2008-02-19
check the man page of ftp. there are 2 options which i can think of that you can use, -o and -d(ebugging) .eg
```

ftp -ni -d << EOF > logfile
...
EOF

```
I leave it to you to try the -o option.

---

### Post by themajesticmoose on 2008-02-19
> **ghostdog74 said:**
> check the man page of ftp. there are 2 options which i can think of that you can use, -o and -d(ebugging) .

Thanks. I'd read the man page already and it didn't help. There is no -o in the ftp that comes with 7.10, and -d is not really useful. But I did find the problem. The man page says "By default, verbose is on." **BZZT!** I checked the ftp source code, and it turns out verbose is on by default **if stdin is a tty.** So I just needed -v. I suppose there's no hope of getting the man page fixed? Anyone know?

---

