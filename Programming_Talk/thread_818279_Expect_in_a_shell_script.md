---
title: "Expect in a shell script"
date: 2008-06-04
forum: Programming Talk
---

### Post by rbhagwandin on 2008-06-04
First of all, hello!

I'm trying to create a line of code, using expect within a shell script, that will assign a variable the value of "grep -c "Hi" /home/myAccount/file
```


count=$(expect -c "spawn ssh root@127.0.0.1 \"grep -c \"Hi\" /home/myAccount/file\"
	expect \"*?assword*\"
	send \"supersecurepassword\r\"
        ")

```

I'm using a different IP address (obviously) and a different file, but the structure is more or less the name.

This is what I've got so far.  When run without the expect stuff as:
```
count=`ssh root@127.0.0.1 "grep -c Hi /home/myAccount/file"`
```
it works perfectly, setting count to the number of lines containing Hi, as it should.  

Any ideas?  With the expect code, $count ends up being the console output (the command run and the prompt for the password)

---

### Post by moot.xk on 2008-06-04
I used expect within bash scripts for a long time to do exactly what you are doing now. It works for most purposes I guess, but you'll get headaches when your passwords contain special characters. Expect likes to read them in as variables instead of chars.

Try doing a more "preferred" method of ssh keys and ssh commands.

[https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30]("https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30")

Once you have your keys setup properly, you'll be able to do something like:
```

$OUTPUT=`ssh remotehost 'whatever command'`

```

The output for "whatever command" is assigned to the OUTPUT variable.

For your script, it's easy enough to plug in the command you want:
```

$OUTPUT=`ssh remotehost 'grep -c "Hi" /home/myAccount/file'`

```

Be careful with your apostrophes, backticks and escapes. If you don't already understand explicit versus loose quoting, go read up on it ASAP. 
[http://www.gnu.org/software/bash/manual/bashref.html#Quoting]("http://www.gnu.org/software/bash/manual/bashref.html#Quoting")

---

### Post by geirha on 2008-06-04
Any reason why you're not using key-based or host-based authentication?

---

