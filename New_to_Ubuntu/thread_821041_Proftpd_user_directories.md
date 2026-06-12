---
title: "Proftpd user directories"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Abadi176 on 2008-06-06
Hello,

I've got some problems with Proftpd. One of them is that I can't assign a directory to a user. For example we have user "test".

The home root of this user is: "/home/test".

When The user log in, he will only see what's inside "/home/test" directory.

What I want to do is assign a directory to the home folder, and give an alias.

For Example:

I assign the directory "/var/www" with alias "www". When the user will login, will he see this:

<directories and folders inside /home/test>
www

How can I create this ?

My second problem is that a user can go to his parent directory. I have used in proftpd.conf:

DefaultRoot ~

But it doesn't work well I think. When I'm on my server:  and type ../ after [ftp://srv1/](ftp://srv1/) ([ftp://srv1/../](ftp://srv1/../)) I can access the parent directory. And if I enter "ftp://srv1/../../" I've access to all directories.

Can Anyone help me with this problem?
Thank you all already

Greetz,

Abadi

---

### Post by superprash2003 on 2008-06-06
you need to use the "lock user in home directory" thingy..i suggest you try gproftpd , its a gui for proftpd and makes it easier for you to configure your ftp server.. to install type sudo apt-get install gproftpd .. or you could install via synaptic (System->administration->Synaptic)

---

### Post by Abadi176 on 2008-06-07
Hi superprash2003,

Thank you for your response.

I don't have the desktop version. I use the ubuntu server. So I don't have any GUI but the shell

---

### Post by Abadi176 on 2008-06-07
Anyone ?

---

