---
title: "Automating SSH scripts"
date: 2010-02-17
forum: Programming Talk
---

### Post by glubbdrubb on 2010-02-17
I would like to pass basic commands over SSH by scripting them. 

For example:

I need to pass 2 or 3 commands to multiple(70+) hosts over SSH. There is quite a lot of latency(up to 1 or 2 seconds) on the connections.

Each command can ake up to 10 seconds to complete before the following commands can be executed.

I have exported SSH keys to all the hosts so logging in is simple:
e.g ```
ssh user1@192.168.x.1
```

Replace x with IP address which increments per host.

I know I can pass 1 command simply by placing it at the end of the ssh statement.
But how do I do that for multiple commands?
e.g. ```
ssh user1@192.168.x.1 command1 command2 command3
```

---

### Post by capybara! on 2010-02-17
Hi, try this:

```
  
ssh user1@192.168.x.1 'command1; command2; command3'  
```it should work fine and execute all commands consecutively.

If you want to parse the output generated from whatever program you call on the remote host, you might want to look at 'expect', which is a scripting language designed for exactly this kind of things.

Hope this helps,,,

---

### Post by iponeverything on 2010-02-17
expect is perfect tool for this.

The expect cisco script can probably be modified to do what you want.

---

### Post by glubbdrubb on 2010-02-18
Sorry I have not responded yet, still testing it...

---

### Post by glubbdrubb on 2010-02-19
Well, I have tried that now. I get the error "standard in must be a tty" because my first command is to su to another user.

But I have found that this works:

```
ssh -t -t 192.168.x.1 <<EOF
Command1
command2
Command3
EOF
```

It is a little clunky but at least it works.

Thanks guys

---

