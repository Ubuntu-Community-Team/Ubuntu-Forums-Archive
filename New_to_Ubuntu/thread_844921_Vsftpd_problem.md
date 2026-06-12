---
title: "Vsftpd problem"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by robertmp on 2008-06-30
Hello Linux people

I recently jumped on the Linux boat to see what the fuzz is all about and so far I like what I see.

I do have a small problem which should be really easy for most of you.

I am trying to set up an vsftpd server on my Ubuntu server (no gui). So far I got it up and running and have managed to limit my 1 user from browsing the total content of the linux box. So I am actually ready to set it up as I intended.

I would like to have several accounts who all login to the same root and have the same folders available from here. These folders should be virtual/mapped folders. How would I go about making something like this?

---

### Post by .nedberg on 2008-06-30
vsftp can have virtual users. I set my ftp server up with three users, one for my self, one for guests and one for guests who need to write. They all logg in to the same folder and can't see the rest of the box.

Look into virtual users if that is what you want. If you want real users on the system I can't help you with that...

---

### Post by robertmp on 2008-06-30
I actually would like virtual users and did look into it, but I ran into problems using a guide which specifies that I had to specify a filename for the userlist in the vsftpd.conf. I have no idea how to specify the syntax in the userlist file.

Any help would be apriciated. If I get this part solved I am down to 1 problem, which is getting some content into the ftp server :P

---

### Post by .nedberg on 2008-06-30
I used [this guide]("http://gentoo-wiki.com/HOWTO_vsftpd#Virtual_Users") and [this]("ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.5/EXAMPLE/VIRTUAL_USERS") to set up virtual users on my system. That last one contains example configs and the README explains it relatively good.

---

### Post by .nedberg on 2008-06-30
In /etc/vsftpd.conf I have
```
user_config_dir=/etc/vsftpd_user_conf
```
and in that dir I have a file for every virtual user. The format of that file is equal to vsftpd.conf

For the "guest" user with write permission, but no listing of files I have
```
anon_world_readable_only=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
```

The reason for preventing listing of files is that I want to make this user less desireable for my friends to use. This keeps them logging in with my guest user who only have read access.

---

### Post by .nedberg on 2008-06-30
Also have a look [here]("ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.5/EXAMPLE/VIRTUAL_USERS_2/").

---

### Post by robertmp on 2008-06-30
Thanx a lot m8. I look forward to look into it when I get off work

---

### Post by robertmp on 2008-07-02
This stuff is confusing...

I seem to be stuck trying to create the logins.txt file. I created it and added a few users like the example stated:

user1
pass
user2
pass

I then went on to try to create the database with the berkeley db program using "db_load -T -t hash -f logins.txt /etc/vsftpd_login.db" but I didnt have the db_load and tried db3_load as suggested....

How do I get passed this problem?

---

### Post by .nedberg on 2008-07-03
Using db3_load is correct. I think your problem is that you don't execute the command as su.

Either try```
sudo db3_load -T -t hash -f logins.txt /etc/vsftpd_login.db
```
or
```
db3_load -T -t hash -f logins.txt vsftpd_login.db
sudo mv vsftpd_login.db /etc/vstfpd_login.db
```

Both will give the same result.

---

### Post by robertmp on 2008-07-03
I get:
sudo: db_load: command not found

Do you know the package name for it, so I can get it using apt-get?

---

### Post by .nedberg on 2008-07-03
Sorry, my mistake!

You should use db3_load...

---

### Post by .nedberg on 2008-07-03
Are you using Hardy? On my server I am using Dapper, and I installed libdb3-util.

On Hardy this package does not exist. Use db4.6-util instead, and load the package with db4.6_load
```
sudo apt-get install db4.6-util
sudo db4.6_load -T -t hash -f logins.txt /etc/vsftpd_login.db 
```

I hope they haven't changed the syntax (I don't have that package installed at my system to check).

---

### Post by robertmp on 2008-07-03
omg! No errors... Progress is made. Thx a lot .nedberg!

But still guessing you havn't heard the last from me yet. Thank you so much for you help so far!

---

### Post by robertmp on 2008-07-03
SOLVED!
Stuck at a new error which is puzzling to me (and my limited Linux knowledge)

When I try to login using username and passwrod specified in my ingins.txt file I get the following error from the ftp server:

500 OOPS: Missing value in config file for: <my password>

Have seen others with similar problem found some bugs in their vsftpd.conf file which contained whitespace and empty lines. I do not think that is the case for me.

---

