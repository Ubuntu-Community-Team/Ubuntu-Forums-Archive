---
title: "[SOLVED] Need tips on bash script"
date: 2007-11-06
forum: Programming Talk
---

### Post by Tampio on 2007-11-06
I have this script that connect's to an ftp server, download's my irc logs, then generates statistics of the channel with pisg and uploads those to another ftp server. It works fine, but it leaves my passwords visible. If I give them as command line arguments they're left in the .bash_history, and the problem is that they're written in there only after I close the terminal window, so I can't add a part to the script that would get rid of them. 
The ideal way for me would be to give the passwords when the server asks for them, so they are not visible at any point. But if I make the code like this: 
```
echo "user $username" | ftp -n -v $server
```
it connects and asks for password, but right after I've typed it in the connection closes and I can't do anything.
Any way I could have the connection not close after typing the password, or if I give them as command line arguments could I have that line somehow not be written in the .bash_history? Or maybe there's some other nifty method I haven't thought of.

---

### Post by bfhicks on 2007-11-06
Encryption would probably be the way to go.

[http://www.math.ucdavis.edu/~zjohnson/doc/Adv-Bash-Scr-HOWTO/contributed-scripts.html#ENCRYPTEDPW]("http://www.math.ucdavis.edu/~zjohnson/doc/Adv-Bash-Scr-HOWTO/contributed-scripts.html#ENCRYPTEDPW")

You could easily incorporate this into your script, I believe.

---

### Post by ghostdog74 on 2007-11-06
> **Tampio said:**
> 
The ideal way for me would be to give the passwords when the server asks for them, so they are not visible at any point. But if I make the code like this: 
```
echo "user $username" | ftp -n -v $server
```
it connects and asks for password, but right after I've typed it in the connection closes and I can't do anything.
Any way I could have the connection not close after typing the password, or if I give them as command line arguments could I have that line somehow not be written in the .bash_history? Or maybe there's some other nifty method I haven't thought of.

```

 ftp -n server<<EOF
     user YourUserName
     pass YourPassword
     ls
     quit
 EOF

```

---

### Post by Tampio on 2007-11-07
Thanks ghostdog, that was just what I wanted :)

---

