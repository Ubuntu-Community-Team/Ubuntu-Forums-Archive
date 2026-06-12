---
title: "processing expect output"
date: 2008-02-17
forum: Programming Talk
---

### Post by Mba7eth on 2008-02-17
hi everyone.... I getting a big headache with expect command. 
I want to telnet to another device, actually a cisco switch, first i want to read some info then based on that info i'll make some output to be executed on the device. 

Unfortunately i'm very newbie to expect and bash scripting :( 
Please Help :confused::mad:

---

### Post by ghostdog74 on 2008-02-17
Have you done the necessary reading up , like maybe the expect manual? Also, show the code you used

---

### Post by Mba7eth on 2008-02-17
Yes ... 
here is my script 

```

#!/bin/bash/
expect << EOF
spawn telnet 10.1.1.1
expect "login:"
send "telnetC\r"
expect "Password:"
send "passPlease\r"
expect "*>"
send "en\r"
expect "Password:"
send "PleasePass\r"
EOF
exit


```

I just want to catch the output from the remote host. Do some processing locally, then send the result to the remote host.

---

### Post by ghostdog74 on 2008-02-17
have a try...not tested
```

expect << EOF > output
...
EOF

```

---

### Post by stroyan on 2008-02-17
The output of the remote host is available to your script using the 'expect_out()' variable.  Look at the 'expect_out' description and examples in "man expect".  You can also see more about expect_out and how it is used at [http://www.oreilly.com/catalog/expect/chapter/ch03.html](http://www.oreilly.com/catalog/expect/chapter/ch03.html)

---

### Post by Mba7eth on 2008-02-18
ghostdog74, stroyan thanks alot both of you. Your links are awesome

---

