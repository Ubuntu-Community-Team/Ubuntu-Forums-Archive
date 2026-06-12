---
title: "Bash script and encfs - except?"
date: 2008-07-28
forum: Programming Talk
---

### Post by Najkl on 2008-07-28
Hello,
I am creating a bash script, which I want to call from Revelation
```
sh DecodeDir.sh password
```
and script executes this command
```
encfs ~/.Dir ~/Dir
```
but this command write out
```
Heslo pro EncFS:
```
(that means 'Password for EncFS:' in English language) and I need send variable ```
$1
``` (it's string 'password' from sh DecodeDir.sh password. I tried 'expect' but I wasn't successfull. :(
I am still beginer in bash scripting.
Thanks.

---

### Post by ilrudie on 2008-07-28
expect will work well for this.  You should call the script from in and expect script like so
```

#!./expect -f 

spawn $argv 
while 1 {
expect "Password: $" {send "<your password>"}\
    "password: $" {send "<your password>"}\
    "(yes/no)? " {send "yes\r"}
}

```

this takes the script you want to run as an argument and runs it.  When it encounters password prompts is enters your password.  When it encounters a server you have not seen before it answers yes to the add this server to list of known hosts question.  You will need to modify for whatever language your system uses but it should give you a good starting point

also make sure the scripts you want to run this from have a shebang statement at the top so it knows which shell to use.

---

