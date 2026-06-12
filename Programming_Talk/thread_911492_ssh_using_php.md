---
title: "ssh using php"
date: 2008-09-05
forum: Programming Talk
---

### Post by ub007 on 2008-09-05
Hi,

I'm trying to ssh using php on ubuntu.I have setup key based authentication on both the ubuntu machines and it works perfectly fine from the terminal command line .I then installed the following packages to get it working with php.

> php5-dev php5-cli php-pear build-essential openssl-dev zlib1g-dev

libssh2

pecl install -f ssh2

Edited php.ini file (for CLI utitilies: /etc/php5/cli/php.ini, for Apache utilities /etc/php5/apache2/php.ini)

extension=ssh2.so

This is the code,i'm using...//secret is my pass phrase,remote user id is david

> <?php
$connection = ssh2_connect('shell.example.com', 22, array('hostkey'=>'ssh-rsa'));
 
if (ssh2_auth_pubkey_file($connection, 'david',
                          '/home/david2/.ssh/id_rsa.pub',
                          '/home/david2/.ssh/id_rsa', 'secret')) {
  echo "Public Key Authentication Successful\n";
} else {
  die('Public Key Authentication Failed');
}
?>
It gives me 'Warning ssh2_auth,.......'Public Key Authentication Failed'

What am i missing here?I am using this script in conjunction with the Apache webserver...
to be more precise,i have a browser form,the user clicks on a 'Submit' button and this script gets called...

It worked fine prior to enabling key based logins.I used 'ssh2_auth_password'  method using root user.this was deemed very insecure,hence trying to use ket based logins.....Plz help me out

Cheers
David

---

