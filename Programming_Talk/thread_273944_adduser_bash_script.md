---
title: "adduser bash script"
date: 2006-10-09
forum: Programming Talk
---

### Post by chi_n_z on 2006-10-09
I am a newbee in linux and scripting in general. I am trying to add a user to my ubuntu box by running a script which provides username,  and other stuff. What i have managed to do is to execute the script and the user is added (writing stuff to /etc/password and /etc/shadow), at the end the script then tries to  initialise the password for the user (using : passwd $username). **** this is where my problem is ****.

The issue is i dont want to type the password. i just want to send it as a parameter.

Is there any way to add user and apply password by executing the script?

Is it possible to run this script say from a web interface (php etc) where an admin capture user details and by submitting the form the user is added?

---

### Post by Arndt on 2006-10-09
> **chi_n_z said:**
> I am a newbee in linux and scripting in general. I am trying to add a user to my ubuntu box by running a script which provides username,  and other stuff. What i have managed to do is to execute the script and the user is added (writing stuff to /etc/password and /etc/shadow), at the end the script then tries to  initialise the password for the user (using : passwd $username). **** this is where my problem is ****.

The issue is i dont want to type the password. i just want to send it as a parameter.

Is there any way to add user and apply password by executing the script?

Is it possible to run this script say from a web interface (php etc) where an admin capture user details and by submitting the form the user is added?

You can combine "mkpasswd -s" with "usermod -p". Look at their man pages.

---

### Post by chi_n_z on 2006-10-09
> **Arndt said:**
> You can combine "mkpasswd -s" with "usermod -p". Look at their man pages.

:confused: 

I have tried the options u gave me. But with no luck. I am not sure if i am doing it right.

As u suggested. [http://expect.nist.gov/example/mkpasswd.man.html#sect5](http://expect.nist.gov/example/mkpasswd.man.html#sect5)
mkpasswd generates passwords and can apply them automatically to users.

But i couldn't manage to solve the problem i am not exactly sure how shld i combine mkpasswd and usermod to achieve my goal:cry:

---

### Post by Arndt on 2006-10-10
> **chi_n_z said:**
> :confused: 

I have tried the options u gave me. But with no luck. I am not sure if i am doing it right.

As u suggested. [http://expect.nist.gov/example/mkpasswd.man.html#sect5](http://expect.nist.gov/example/mkpasswd.man.html#sect5)
mkpasswd generates passwords and can apply them automatically to users.

But i couldn't manage to solve the problem i am not exactly sure how shld i combine mkpasswd and usermod to achieve my goal:cry:

Your first problem was that 'passwd' reads from the terminal, not from standard input, so you can't easily send a password to it with a script (but the program 'expect' may help if you really need to use 'passwd'). "usermod -p" takes an encrypted password as argument, so that should solve that problem. But now you need to encrypt the password before giving it to 'usermod', and 'mkpasswd' does that.

I think this ought to work for you, but I haven't tried it:

> # Assuming $password and $username are available
tmpdir=/tmp/pwddir$$
chmod og-rx $tmpdir
echo $password > $tmpdir/pwd
encrypted=`mkpasswd -s < $tmpdir/pwd`
usermod -p $encrypted $user
rm -rf $tmpdir

This complexity is needed to ensure that the password is never visible in cleartext to anyone else. There may be an easier way to do it I have missed.

> encrypted=`echo $password | mkpasswd -s`

looks a lot simpler, but I'm not sure that this will not result in the 'echo' command being visible in the process listing.

---

### Post by chi_n_z on 2006-10-10
Thanx a lot man, your code did the magic! Just after adding 
mkdir /tmp/pwddir. At least I am sorted on this one, I now have to take care of adding the user from a web interface.


> **Arndt said:**
> 

password="my_simple password"
login="a_system_user created before"

mkdir /tmp/pwddir
tmpdir=/tmp/pwddir
chmod og-rx $tmpdir
echo $password > $tmpdir/pwd
encrypted=`mkpasswd -s < $tmpdir/pwd`
usermod -p $encrypted $login
rm -rf $tmpdir



---

