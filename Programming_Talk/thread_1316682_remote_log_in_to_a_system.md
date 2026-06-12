---
title: "remote log in to a system"
date: 2009-11-06
forum: Programming Talk
---

### Post by phillip_linux on 2009-11-06
Hi All
I need a script for remote login into a system . during run time it should ask Ip address login id and password of a system i need to login. I'm new bee to linux. Can any one help me.
i tried like

---

### Post by dwhitney67 on 2009-11-06
sshlogin:
```

#!/bin/bash

read -p "Enter the IP address of remote system: " IP
read -p "Enter the User Id: " UserID

ssh $UserID@$IP     # ssh will prompt for a password

```

To run the program:
```

$ chmod +x sshlogin

$ ./sshlogin

```

---

### Post by phillip_linux on 2009-11-06
> **dwhitney67 said:**
> sshlogin:
```

#!/bin/bash

read -p "Enter the IP address of remote system: " IP
read -p "Enter the User Id: " UserID

ssh $UserID@$IP     # ssh will prompt for a password

```To run the program:
```

$ chmod +x sshlogin

$ ./sshlogin

```

Thank u very much. :)

---

