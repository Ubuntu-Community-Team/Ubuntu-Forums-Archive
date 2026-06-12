---
title: "A couple of script questions"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by knottshawk on 2008-05-19
I'm trying to create a script to login to my proxy server. A couple of questions based on that... First of all, i use something like this to get to the proxy server:

ssh -D 1088 -p 80 [email]myname@myaddress.com[/email]

It then brings up a password prompt for me...this brings me to my question. **Is there a line I can put in the script to automatically fill in my password?**

The other question I have is this:
**How can I get my saved script to run by simply clicking the file (as opposed to going into the terminal and doing it). **My reason for this is that I've got several proxy servers to log into and a gui would be an easier way to do it. 

Right now if I click the file and select execute, nothing seems to happen.

---

### Post by sdennie on 2008-05-19
I don't know if you want to auto-fillin the password but, there is a way to allow public key authentication for ssh.  This tutorial looks correct: [http://ubuntu-tutorials.com/2007/02/05/unattended-ssh-login-public-key-ssh-authorization-ssh-automatic-login/](http://ubuntu-tutorials.com/2007/02/05/unattended-ssh-login-public-key-ssh-authorization-ssh-automatic-login/).

To make icons for you logins, just right click on the panel and select Add to Panel->Custom Laucher.  Type in the name of your script and change the Type from Application to Terminal Application.

---

### Post by brian_p on 2008-05-19
> **knottshawk said:**
> I'm trying to create a script to login to my proxy server. A couple of questions based on that... First of all, i use something like this to get to the proxy server:

ssh -D 1088 -p 80 [email]myname@myaddress.com[/email]

It then brings up a password prompt for me...this brings me to my question. **Is there a line I can put in the script to automatically fill in my password?**

```
apt-cache show expect
```

---

### Post by knottshawk on 2008-05-19
Vor, That doesn't look right... I don't have admin rights to the proxy servers. I just log into them. So I just need a way to automate the password I already have.

I don't know if there is a command I can put in the ssh line?

Brian, I don't know what you're saying to do... Sorry.... I'm a noob.

---

### Post by brian_p on 2008-05-19
> **knottshawk said:**
> Brian, I don't know what you're saying to do... 

I am pointing you at a program with does what you desire. Type the command I gave you in a terminal.

> Sorry.... I'm a noob.

In that case you may want to consider the security implications of putting passwords in a script.

---

### Post by knottshawk on 2008-05-19
I appreciate your concern... but I'm in a home office. My toddler has no interest in my passwords. And besides, if somebody gets my passwords, they have a proxy to the internet. Or they could just use an html proxy. There are no security implications. Believe me. Security is my job...

---

### Post by The Cog on 2008-05-19
You don't need admin rights to the proxy servers to set up key-based logins. You just put some files in the .ssh directory in the home directory of your login user.

---

### Post by brian_p on 2008-05-19
> **knottshawk said:**
> I appreciate your concern... but I'm in a home office. My toddler has no interest in my passwords. And besides, if somebody gets my passwords, they have a proxy to the internet. Or they could just use an html proxy. There are no security implications. Believe me. Security is my job...

You're underestimating the risk of subversion from inside. These toddlers will do anything for a bar of chocolate.

---

### Post by knottshawk on 2008-05-19
Anyone know how to use this expect command? I've seen it used about 10 different ways in different searches and I can't get any of them to work. It's still prompting me for my password.

---

### Post by brian_p on 2008-05-19
> **knottshawk said:**
> Anyone know how to use this expect command? I've seen it used about 10 different ways in different searches and I can't get any of them to work. It's still prompting me for my password.

This fragment works for me in a script I use:

```
#!/usr/bin/expect                                                                                        
                                                                                                         
# Run the telnet program and connect it to the router.                                           
spawn /usr/bin/telnet 192.168.7.1                                                                        
                                                                                                         
# Look for something in the prompt and send the password.                                                             
expect "password: "                                                                                      
send "1Pb(z7VG@*62cwlAkk9\r"
```

---

### Post by The Cog on 2008-05-20
I had a lot of trouble getting expect to work for me a few years ago. It seems that ssh could tell that it was running from a script and not a tty (this was on solaris if that makes a difference). I ended up making a telnet call to 127.0.0.1 and making the ongonig SSH call from the telnet login. Ugly but it got the job done.

---

