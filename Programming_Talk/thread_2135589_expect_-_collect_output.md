---
title: "expect - collect output"
date: 2013-04-14
forum: Programming Talk
---

### Post by greenpanther on 2013-04-14
Hy!

I am new in programming but maybe there are some people here who can help me.

i bought a resol vbus/lan adapter. i have to communicate with this adapter trough telnet.

here is my script i have tried out.

```

#!/bin/bash
set timeout 20
expect -c "
spawn telnet 192.168.0.206 7053
expect "+HELLO"
send \"PASS vbus\r\"
expect \"+OK: Password accepted\"
send \"DATA\r\"
expect "+OK: Data incoming..."
expect "%"
set results $expect_out(buffer)
sleep 20
"
echo $results > text.txt

```

the login proces works fine. but i don't receive any data after "+OK. Data incoming...". there should be some bus conversation after this line.

thank you for your help in advance.

cu
green

---

### Post by nightahwk36 on 2013-06-28
Hi,

have you been able to sort this output thing out?

I am at the same point, where I can connect but output is blank.

Once I directly telnet to the box I can see some "data"

Cheers
Frank

---

