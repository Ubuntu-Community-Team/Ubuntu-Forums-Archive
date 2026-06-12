---
title: "Bash: Exit code in smbclient or ftp, or workaround?"
date: 2008-04-02
forum: Programming Talk
---

### Post by rockstar82 on 2008-04-02
I am scripting a backup-script that first compresses folders to .tar, and then transfer the files with smbclient or ftp. This works great.

However, I want to catch and log any error messages from the transfer and take appropiate actions, as I scheduled the backups with cron.

I could not find a way to do this with "$?". Is there a way to do this?

```
transfer_ftp ()
{
ftp -i -n -p -v $ip $port <<ENDFTP
user $user $pass
lcd $backuptofolder
bin
mkdir $path
cd $path
mput *$date*
close
bye
ENDFTP
}

transfer_samba()
{
smbclient //$ip -U $user $pass <<ENDSMB
prompt
lcd $backuptofolder
mkdir $path
cd $path
mput *$date*
exit
ENDSMB
}
```


Update! Exit code from smbclient solved, but no progress with ftp...

This worked, rather than putting the echo $? _inside_ the function. This gives me "1" if anything goes wrong.

```
transfer_samba
echo $?
```

Any ideas how to solve the exit code from ftp?

---

### Post by ghostdog74 on 2008-04-02
> **rockstar82 said:**
> 
However, I want to catch and log any error messages from the transfer and take appropiate actions, as I scheduled the backups with cron.


use the -d switch of ftp command , then pipe to output file
```

ftp ...-d server << EOF > output
...
..
EOF

```

---

### Post by mssever on 2008-04-02
$? only works for the last command executed (and only for a single command). In other words, you have to get its value immediately after executing a command. Maybe something like this:
 ```
ftp blah
status=$?
do_stuff
[[ $status -eq 0 ]] || handle_error
```

You can also use redirection and file descriptor manipulation to capture whatever output you might want.

---

