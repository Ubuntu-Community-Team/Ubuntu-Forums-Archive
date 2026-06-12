---
title: "Safe way to store a password needed by a script on a server"
date: 2014-08-29
forum: Programming Talk
---

### Post by silentcreek on 2014-08-29
Hi,

I use a script to have my home server backup my imap email from external servers. I would like the script to be run by cron with with no user interaction required, which means I would need to put the password somewhere. I'd like to avoid putting it in plain text in my script, so I'm looking for a safer way to pass the password to my script without storing it in plain text and without me logging into the machine to type the password.

So, how would you do this? And how would you pass the password to the script while making sure the password is not printed to a shell (e.g. while somebody is logged in), visible in the console history or in any logs?


Thanks,

Timo

---

### Post by mejrum on 2014-08-29
If the cron job is run by root, I would put the password in root's home, eg, 
/root/secrets/mypassword
chmod -R 600 /root/secrets

This way only root can read the password, and if someone gains root access to your machine - you have more severe problems..

Dunno about hiding it from logs/stdout..

Maybe look into sftp with preshared keys?

---

### Post by silentcreek on 2014-08-29
Thanks.

That's where I am now. I have a configuration file for my script that holds the password and the file is set as read- and writable only to root (chmod 600, while root being the file owner). Edit: And yes, the script is executed as root by cron.

However, I thought there must be even a better way like encrypt the password and decrypt it with a passphrase file stored on the server only readable to root. I know it's just security by obscurity - but still better than storing the password in plain text. So something like:
> gpg -q --batch --no-tty --for-your-eyes-only --passphrase-file /path/to/passphrase -d /path/to/encrypted-imap-password.gpg
The problem here is one could basically monitor processes with their commandline options and would already know where the passphrase to the encrypted password is stored. I know, with some effort, this will always be possible if you want to provide the password without user interaction. But I'm wondering if there is a solution to make this less obvious.

Cheers,

Timo

Edit: I only have imap access to the external server, so sftp is not an option.

---

