---
title: "PHP useradd"
date: 2006-10-11
forum: Programming Talk
---

### Post by chi_n_z on 2006-10-11
Hi Folks,

I am a new bee in scripting. I want to create a linux user programatically through php on my Ubuntu box.

I have managed to create the user using

```

echo "<pre>". shell_exec("/usr/bin/sudo /usr/sbin/useradd -d 
/home/".strtolower($_POST[login])." -p".crypt($_POST['pwd'])." -g test -s 
/bin/bash -m -c \"".$fullname."\" ".strtolower($_POST[login]))."</pre>";


```

where the given arguments are coming from the form.

my problem is to get the password working, i.e there is something wrong on my -p option. I have tried php crypt() but with no luck.

I am not really sure where am i getting it wrong. 

Help!

---

### Post by JonahRowley on 2006-10-11
First, what you're doing is exceptionally dangerous.  Calling shell programs from your PHP script alone is dangerous, doing so with superuser privs, that adds a user nonetheless, is asking for trouble.  It can be done safely though.

Validate all user input.  Twice, if possible.  Now, instead of using sudo, use a shell script to add the users.  This shell script should be owned by root and set suid (google for how to do that).  It should take very limited parameters (ideally, just username and password) and validate all user input (again, even though your PHP script already did it).  The script should be very specific, it should only add users to a certain group for example.  Just remember, be careful here.

---

### Post by chi_n_z on 2006-10-12
> **JonahRowley said:**
> (google for how to do that). 


:cry: I have been googling for this solution for a while now but with no luck. I think thats the bad part of being a new bee!. I have added my apache user to sudoers and gave it useradd previledges as suggested in other forums.

As for now i am not very much worried about the security, as long as I get something to work for now i will be fine. 

And will continue using that till i got something secure.

I'm tearing my hair out and wondering if anyone knows the answer to this.

---

### Post by JonahRowley on 2006-10-12
OK, to give apache full access to useradd, add a line like this:

```

apache ALL=(ALL) NOPASSWD: /usr/sbin/useradd

```

That should be it.  You *really* need to google for PHP input validation, because this is a HUGE, GAPING, absolutely unacceptable security hole.  I'm not responsible if someone finds this site and compromises your server!  I can't stress how dangerous this is, and I suggest that you not do it this way.

---

### Post by chi_n_z on 2006-10-12
> **JonahRowley said:**
>  You *really* need to google for PHP input validation, because this is a HUGE, GAPING, absolutely unacceptable security hole.  

Thanks. I had already given PHP the useradd previledge thru visudo, it was  adding the user the only prob was with the password.

I managed to get it working afterwards. I Will look into the security side as you adviced. Or one day the guruz out there will come with a more sure way of doing it!

Thanx

---

### Post by hobbestec on 2006-10-12
If this machine is accessible over the internet, at the very least you should add a .htaccess to limit access to the directory this script is in.  There are instructions to setup an htaccess file available all over the place online.  I've found one here: [http://www.debianhelp.co.uk/htaccess.htm](http://www.debianhelp.co.uk/htaccess.htm)

If your paranoid there are also a number of other issues that makes this a security nightmare, look into SSL certificates, even a self signed one would be fine if you are the only person who access this script over the internet. If the machine has multiple users on it you'll need to make sure nobody else can execute this script locally too.

---

### Post by JonahRowley on 2006-10-12
> **hobbestec said:**
> If this machine is accessible over the internet, at the very least you should add a .htaccess to limit access to the directory this script is in.  There are instructions to setup an htaccess file available all over the place online.  I've found one here: [http://www.debianhelp.co.uk/htaccess.htm](http://www.debianhelp.co.uk/htaccess.htm)

If your paranoid there are also a number of other issues that makes this a security nightmare, look into SSL certificates, even a self signed one would be fine if you are the only person who access this script over the internet. If the machine has multiple users on it you'll need to make sure nobody else can execute this script locally too.

Good advice, but if done through sudo, executing the script locally will not do anything.  The process must be running as apache.  However, if you give other people access to your webserver, they also have access to useradd.

---

### Post by chi_n_z on 2006-10-12
> **hobbestec said:**
> If this machine is accessible over the internet, at the very least you should add a .htaccess to limit access to the directory this script is in.  There are instructions to setup an htaccess file available all over the place online.  I've found one here: [http://www.debianhelp.co.uk/htaccess.htm](http://www.debianhelp.co.uk/htaccess.htm)

If your paranoid there are also a number of other issues that makes this a security nightmare, look into SSL certificates, even a self signed one would be fine if you are the only person who access this script over the internet. If the machine has multiple users on it you'll need to make sure nobody else can execute this script locally too.

Thank you so much. At least I know that I am a little bit safer now. The .htaccess link was so helpful. I had secured everything as suggested by the site and was working perfectly. But afterwards i decided to go to the Apache website. [http://httpd.apache.org/docs/2.0/howto/htaccess.html](http://httpd.apache.org/docs/2.0/howto/htaccess.html)
They heavily discourage the use of htaccess, instead the recommend the <Directory/>. And thats the way i have taken.

Thank you guys, "I think i am safe now." see that is in quotes. Someone might know a hole in this. who knows!

---

